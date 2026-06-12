---
title: "Have need for function passing in C++"
date: 2008-11-06
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-11-06
I have a C++ program that is about 2000 lines long.  Issue is that there are around 15 functions that are copy and paste exactly the same except for one line.  Problem is that the one line that differs is a function call.  So I could take 15 functions and make them 1 if only I had a way to pass a function as an argument as other languages like Javascript and ML allow.  The other complication is that the one line that differs is called several times inside a for-loop, so I can't simply split all the functions into 2 parts, part before the call and part after the call, making the special call in between.

The best idea that I can think of is to replace each line that differs with another function call to a more generic function and then pass some argument token so that the generic function knows which call to make.  Something like this:

void A()
{
   Object myobj;
   //bunch of code
   myobj->call1();
   //more code
}


void B()
{
   Object myobj;
   //bunch of code
   myobj->call2();
   //more code
}

Replace with:

void A()
{
   Object myobj;
   genericFunc(myobj, "CALL1");
   //more code
}

void B()
{
   Object myobj;
   //bunch of code
   genericFunc(myobj, "CALL2");
   //more code
}

void genericFunc(Object myobj, String callid)
{
    if(callid == "CALL1")
    {
          myobj->call1();
    }
    else if(callid == "CALL2")
    {
          myobj->call2();
    }
}

Can anyone think of a better approach?

---

### Post by dwhitney67 on 2008-11-06
How about:
[php]
class BaseClass
{
  public:
    ...

    void doSomething()
    {
      // do generic stuff

      doSomethingSpecial();

      // do more generic stuff
    }

    virtual void doSomethingSpecial() = 0;
};
[/php]

Then each of your specialized "actions" can inherit this base-class and implement their specialty within doSomethingSpecial().

A program could then be:
[php]
void doIt( BaseClass* bc)
{
  bc->doSomething();
}

int main()
{
  std::vector<BaseClass*> lotsToDo;

  lotsToDo.push_back(new SpecialA);
  lotsToDo.push_back(new SpecialB);
  ...
  lotsToDo.push_back(new SpecialK);

  std::for_each(lotsToDo.begin(), lotsToDo.end(), doIt);

  return 0;
}
[/php]

---

### Post by SNYP40A1 on 2008-11-06
> **dwhitney67 said:**
> How about:
[php]
class BaseClass
{
  public:
    ...

    void doSomething()
    {
      // do generic stuff

      doSomethingSpecial();

      // do more generic stuff
    }

    virtual void doSomethingSpecial() = 0;
};
[/php]

Then each of your specialized "actions" can inherit this base-class and implement their specialty within doSomethingSpecial().

A program could then be:
[php]
void doIt( BaseClass* bc)
{
  bc->doSomething();
}

int main()
{
  std::vector<BaseClass*> lotsToDo;

  lotsToDo.push_back(new SpecialA);
  lotsToDo.push_back(new SpecialB);
  ...
  lotsToDo.push_back(new SpecialK);

  std::for_each(lotsToDo.begin(), lotsToDo.end(), doIt);

  return 0;
}
[/php]

I could make that work.  But I am not sure it is the best way.  Actually, the Object myobj is the exact same type of object in each of my 2 A and B examples.  Each function really only needs to execute in a static context.  So using inheritance to define the special action to execute and then having to create an instance for every function call seems like a lot of overhead.  But let me think about it some more, what's the advantage of doing that over the generic if-statement approach that I mentioned?  Efficiency does kind of matter in what I am trying to do and I think the object allocation might slow things down a bit.  I will keep thinking about this approach.

---

### Post by slavik on 2008-11-06
have you tried passing a reference to a void?

int function() { code }
int function2(void &func) { int a = func(); }
function2(&function);

I haven't tested the code, but you get the idea. Failing that, you can do it the C way and pass a pointer to a function.

---

### Post by karpati on 2008-11-06
I think that you can try this if the functions have the same prototypes (not sure about the syntax. You may need to fix it to get it to work):

define a function pointer in class object:
class Object {
// some code

// declare a pointer to function:
void (*p_call)(args...);
 // some more code
}

// Function A
//Declare the function prototype as an argument to A().
void A(... , void (*call) (args...))
{
Object myobj;
myobj->p_call = call; // assign the pointer to the class variable

// some code
myobj->p_call(args); // call the function
//more code
}

You can call A() like:
A(call1);
or
A(call2);

---

### Post by SNYP40A1 on 2008-11-07
(deleted)

---

### Post by dribeas on 2008-11-07
> **SNYP40A1 said:**
> I have a C++ program that is about 2000 lines long.  Issue is that there are around 15 functions that are copy and paste exactly the same except for one line.  Problem is that the one line that differs is a function call.  So I could take 15 functions and make them 1 if only I had a way to pass a function as an argument as other languages like Javascript and ML allow.  The other complication is that the one line that differs is called several times inside a for-loop, so I can't simply split all the functions into 2 parts, part before the call and part after the call, making the special call in between.

Assuming that A(), B()... Z() are exact same copies of the function with the difference that A calls obj->a(), B calls obj->b()... and that a(), b()... share the same signature you can rewrite the A to Z functions into just one generic function that takes a method pointer as argument (if instead of methods it was functions, you can use function pointers):

```

typedef void (TheClass::*)() signature; // so changing signature is easier
void Generic( signature method )
{
   TheClass obj;
   // all code before method call
   obj.*method(); // Call through a method pointer
   // all other similar code.
}

```

Then if you can change the caller code you can replace:

```

class TheClass
{
public:
   void a();
   void b();
   //...
   void z();
};
int main()
{
   Generic( &TheClass::a ); // A()
   Generic( &TheClass::b ); // B()
}

```

That solution can evolve. You can store method pointers in a map indexed by name of function and pass around a string instead of the method pointer. Generic would receive a function method and internally translate through the map into the appropriate method pointer.

There are more generic solutions. If you do care to learn take a look at boost::function and boost::bind. Boost Function allows you to define a generic function interface (signature) for functors (functor defined as anything to which you can apply parenthesis () and gets executed) The result is a functor in itself that can be passed around as any other regular object. Boost bind allows you to adapt method/function signatures by moving around, inserting or removing arguments.

---

### Post by lisati on 2008-11-07
I've seen it done in C, where a pointer to the function was passed as an argument. I've lost track of the magazine I saw it in, but if memory serves correctly, it was similar to the approach suggested by slavik here: [http://ubuntuforums.org/showpost.php?p=6121774&postcount=4](http://ubuntuforums.org/showpost.php?p=6121774&postcount=4)

---

### Post by slavik on 2008-11-07
atexit() takes a function pointer, so does signal(); :)

---

### Post by Npl on 2008-11-07
Barring syntactical errors this should work with using member-pointers:
```
typedef void (Object::*PFMV)() // Pointer to a void () method of Object

void foo(PFMV mf)
{
Object myobj;
//bunch of code
(myobj.*mf)(); // call function of instance myobj
//more code
}

void A()
{
  foo(&Object::call1);
}

void B()
{
  foo(&Object::call2);
}
```
It could work without the typdef aswell, but I always mess it up if I dont use typedefs.

---

### Post by dwhitney67 on 2008-11-07
Here's yet another way; it's not very C++ with all of the "floating" functions.  It would be better if the functions were encapsulated in a class.
[php]
#include <algorithm>
#include <vector>
#include <iostream>


typedef void (*PF)(void);


void commonBegin(void)
{
  std::cout << "commonBegin(),\t";
}

void commonEnd(void)
{
  std::cout << "\tcommonEnd()" << std::endl;
}

void functionOne(void)
{
  std::cout << "functionOne(), ";
}

void functionTwo(void)
{
  std::cout << "functionTwo(), ";
}

void functionN(void)
{
  std::cout << "functionN(), ";
}

void Process(PF f)
{
  commonBegin();

  f();

  commonEnd();
}


int main()
{
  std::vector<PF> vec;

  vec.push_back(functionOne);
  vec.push_back(functionTwo);
  // ...
  vec.push_back(functionN);

  std::for_each(vec.begin(), vec.end(), Process);

  return 0;
}
[/php]

---

### Post by SNYP40A1 on 2008-11-07
I think it's basically this example here:
[PHP]
Now suppose we would like to create a list consisting of twice the corresponding values in the original list:
[1, 12, 3] ==> [2, 24, 6]

Rather than rewriting code very similar to what we have written already, we can reuse the old code, by adding a function argument:

List<int> map(const List<int> L, int (*f)(int))
{
  ListIter<int> iter(L);
  List<int> newList;

  for(; !iter.isEnd(); iter.advance())
    newList.append(f(iter.current()));

  return newList;
}

and then writing two trivial functions:

  int square(int i) { return(i*i); }
  int dbl(int i) { return(2*i); }

We can now write:

  map(L, square);
  map(L, double);
[/PHP]

from here:

[http://pages.cs.wisc.edu/~siff/CS367/Notes/fp.html](http://pages.cs.wisc.edu/~siff/CS367/Notes/fp.html)

However, I forgot to mention that some of the special functions take function arguments.  And the function arguments are not all of the same type...makes things more complicated.

---

### Post by dribeas on 2008-11-08
> **SNYP40A1 said:**
> However, I forgot to mention that some of the special functions take function arguments.  And the function arguments are not all of the same type...makes things more complicated.

You should be more clear on the interfaces you want to use, solutions may be different depending on whether the signatures of the copied functions are the same or not, if they are different if they take the same arguments that need to be passed to the member method, whether the common code provides data to be used as arguments to the method call...

---

### Post by SNYP40A1 on 2008-11-10
I have been thinking about this problem over the past three days.  I am thinking of doing what I described earlier with the generic if-statement list.  The variable type / number argument passing really makes things complicated.

---

### Post by dwhitney67 on 2008-11-10
> **SNYP40A1 said:**
> I have been thinking about this problem over the past three days.  I am thinking of doing what I described earlier with the generic if-statement list.  The variable type / number argument passing really makes things complicated.
It would not be complicated if you use Boost's "bind".

Here's a trivial example:
[php]
#include <boost/bind.hpp>
#include <iostream>

int functionOne(int i)
{
  return i;
}


int functionTwo(int i, int j)
{
  return i + j;
}

template<class F> void doSomething(F f)
{
  std::cout << "result = " << f() << std::endl;
}


int main()
{
  doSomething( boost::bind(&functionOne, 5) );
  doSomething( boost::bind(&functionTwo, 4, 5) );

  return 0;
}
[/php]

---

### Post by dribeas on 2008-11-10
> **SNYP40A1 said:**
> I have been thinking about this problem over the past three days.  I am thinking of doing what I described earlier with the generic if-statement list.  The variable type / number argument passing really makes things complicated.

Without further explaining your requirements, we cannot assist you. 

Anyway I can give you examples of use from the STL that might (or might not) be close to what you need. Note that I am posting usage, not implementation, that is your question. It does not really make sense going into details when it may as well not be what you want.

The tranformation you provided in the sample code is similar to what std::transform does -well, std::transform is more generic, but the idea is similar.

```

int square_function( int x )
{
   return x*x;
}

int main()
{
   std::vector<int> input; // fill in data
   std::vector<int> result;
   
   std::transform( input.begin(), input.end(), std::back_inserter( result ), &square_function );
}

```

Now, transform (as many other algorithms in STL) allow the use of function objects. With function objects you can add some more info into the mix:

```

class multiply_int // easy to templatize for any type, but for the sake of simplicity
{
public:
   multiply_int( int factor = 1 ) : factor_( factor ) {}
   int operator()( int x )
   {
      return x * factor_;
   }
private:
   int factor_;
};
int main()
{
   std::vector<int> input; // fill in data
   std::vector<int> times2;
   std::transform( input.begin(), input.end(), std::back_inserter(times2), multiply_int( 2 ) );

   std::vector<int> times5;
   std::transform( input.begin(), input.end(), std::back_inserter(times5), multiply_int( 5 ) );
}

```

@dwitney67 solution of using boost::bind is a good suggestion that comes into the line of function objects with the extra ease of use of the library that allows you to adapt function/method signatures by creating anonymous function objects.

It all depends on your requirements, that are not clear yet.

---

