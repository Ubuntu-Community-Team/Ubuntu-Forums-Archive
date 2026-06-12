---
title: "HOWTO:  Return multiple values from a C/C++ function."
date: 2010-04-22
forum: Programming Talk
---

### Post by stchman on 2010-04-22
I was reading about this on other sites and there seens to be a lot of confusion about this.  It is actually pretty easy.

Normally a function returns just one value.  C/C++ has pointers which simply point to an address.

Here is an example of code used to return multiple values from a function.

[php]
/*
Return multiple values from a function
*/

#include <stdio.h>
#include <math.h>
#include <string.h>
#include <stdlib.h>

// prototype function
void tester( double *xx, double *yy );

// main function
int main( int argc, char *argv[] )
{
    double x = 0.0, y = 0.0;
    
    // init variables
    x = 4.8;
    y = 95.26;
    
    // print original values
    printf( "%10.4f           %10.4f\n", x, y );
    
    // call tester passing the address rather than the values
    tester( &x, &y );
    
    // print new values gotten from function
    printf( "%10.4f           %10.4f\n", x, y );
    
    return 0;
        
} // end of main

// notice the function is void as it returns nothing
// you passed in the address of the variables
void tester( double *xx, double *yy )
{
    // pointers are a pointer to an address
    // these statements are basically saying that the address contains the following values
    *xx = 900.23;
    *yy = *xx * 56.3 + 85.147;
}
[/php]This is a simple example, but as you can see with pointers you can return as many values as you wish from a function.

---

### Post by Cracauer on 2010-04-22
I would not use the phrase "return value" for this.

Passing in things via non-const references or pointers always allows you to transport state back to the caller.

The term "return value" should be used for something that has about the same semantics as the function return value, which is that it can be ignored (without cooperation from the function on the ignore part) and that it doesn't involve mutation of anything.

---

### Post by tookyourtime on 2010-04-22
Or even better you can pass by reference, and not have to worry about lots of &s and *s.

```

void function(float & x, double & y)
{
[INDENT]x = 900;
y = x * 56 + 85;
[/INDENT]}

int main(void)
{[INDENT]float x = 10;
float y = 20;

function(x, y);
[/INDENT]}
```

---

### Post by Aped on 2010-04-22
OR you could just always use global variables, hurr!

---

### Post by stchman on 2010-04-22
> **Cracauer said:**
> I would not use the phrase "return value" for this.

Passing in things via non-const references or pointers always allows you to transport state back to the caller.

The term "return value" should be used for something that has about the same semantics as the function return value, which is that it can be ignored (without cooperation from the function on the ignore part) and that it doesn't involve mutation of anything.

Does the program indeed return multiple values from one C function to another?  Yes it does.

---

### Post by tookyourtime on 2010-04-22
But it doesn't really return anything, it just changes things that were already there.

Your not wrong, he's just saying that 'technically' you used the wrong word.

---

### Post by lisati on 2010-04-22
> **tookyourtime said:**
> Or even better you can pass by reference, and not have to worry about lots of &s and *s.

```

void function(float & x, double & y)
{
[INDENT]x = 900;
y = x * 56 + 85;
[/INDENT]}

int main(void)
{[INDENT]float x = 10;
float y = 20;

function(x, y);
[/INDENT]}
```
This is the C equivalent of what I was taught, and is what I'd recommend that you use if possible.
> **Aped said:**
> OR you could just always use global variables, hurr!
:) You need to be aware of possibility unintended side effects if you choose this approach.

---

### Post by stchman on 2010-04-22
> **tookyourtime said:**
> But it doesn't really return anything, it just changes things that were already there.

Your not wrong, he's just saying that 'technically' you used the wrong word.

I see what you mean.  Since I passed the function the address it is changing what is at the address.

What I have in essence is given you the illusion of returning multiple values.

---

### Post by Letrazzrot on 2010-04-22
> **tookyourtime said:**
> Or even better you can pass by reference, and not have to worry about lots of &s and *s.

```

void function(float & x, double & y)
{[INDENT]x = 900;
y = x * 56 + 85;
[/INDENT]}

int main(void)
{[INDENT]float x = 10;
float y = 20;

function(x, y);
[/INDENT]}
```

I agree with this.  The generally accepted rule seems to be to use pointers only if you *have* too.  Also remember, that when using the pointer version, you should check for NULL pointers before using them -- something you typically don't have to do with references.

---

### Post by pokebirdd on 2010-04-23
> **tookyourtime said:**
> Or even better you can pass by reference, and not have to worry about lots of &s and *s.

```

void function(float & x, double & y)
{[INDENT]x = 900;
y = x * 56 + 85;
[/INDENT]}

int main(void)
{[INDENT]float x = 10;
float y = 20;

function(x, y);
[/INDENT]}
```

How does that work exactly? You call it pass by reference but isn't that just passing the values of x and y to the function? I'm guessing it has something to do with the &'s in the function definition?

---

### Post by lisati on 2010-04-23
> **pokebirdd said:**
> How does that work exactly? You call it pass by reference but isn't that just passing the values of x and y to the function? I'm guessing it has something to do with the &'s in the function definition?

There is an important difference between calling-by-reference and calling-by-value. When you call by reference, you are able to modify the variables, but with call by value, a copy of the variable's value is provided to the function and not the variable itself.

[http://en.wikipedia.org/wiki/Evaluation_strategy#Call_by_value](http://en.wikipedia.org/wiki/Evaluation_strategy#Call_by_value)

---

### Post by LKjell on 2010-04-23
> **stchman said:**
> I see what you mean.  Since I passed the function the address it is changing what is at the address.

What I have in essence is given you the illusion of returning multiple values.

A function can only return one type or nothing. The only way to return multiple values is to encapsulate the values into a data structure. What it means by return is that you can assign a variable to the function. But to do that you need to know the type it returns.

There is no difference with the code below.
```

int two() {
        return 2 + 2;
}

int x = two();
int x = 2 + 2;
```

With your function it modifies existing variables. You cannot assign a variable to the function and thus you have no idea what the function do.

An issue you might want to look at is square root of a positive number.
If b = a^2 then b can be

(-a)^2 and a^2.

Now you make a function of square root of a value. It can either return the negative or the positive of that number. And you have no control what it might return. But since some math people are smart they made the definition that all square root function will return the positive value and you have no more problems.

---

### Post by MadCow108 on 2010-04-23
return the results in a structure if they are related:
```

typedef struct Vector2 {
  double x;
  double y;
} Vector2;

Vector2 MakeVector(double x, double y)
{
  Vector2 vec;
  vec.x = x;
  vec.y = y;
  return vec;
}

int main(...)
{
  Vector2 = MakeVector(1,5. 6);
}

```

return type optimization of the compiler will remove the temporary in the function, so no performance hit compared to the pointer/reference version in most cases.

The pass by reference/pointer or global variable makes more sense when the results are not related (like result and errorcode)

---

### Post by slooksterpsv on 2010-04-23
[PHP]

#include <iostream>

using namespace std;

struct mStruct
{
 double x;
 double y;
};

void modify(mStruct *v)
{
 v->x += 10;
 v->y = v->x * 25.5;
}

int main()
{
 mStruct tv;
 cout << "X = 5 and Y = 0" << endl;
 tv.x = 5;
 tv.y = 0;
 modify(&tv);
 cout << "X = " << tv.x << " and Y = " << tv.y << endl;
 cin.get();
 return 0;
}

//This returns the following:
//X = 5 and Y = 0
//X = 15 and Y = 382.5

[/PHP]

=P

---

### Post by LKjell on 2010-04-23
@slooksterpsv even if you modify the struct with function you do want to return a pointer of the modified stucture and not void.

---

### Post by Compyx on 2010-04-23
> **LKjell said:**
> @slooksterpsv even if you modify the struct with function you do want to return a pointer of the modified stucture and not void.

Why? Since we're passing a pointer to the structure, the structure itself gets modified in the function, so there's no need to return a pointer to the structure since we already have that information (the structure `tv' itself).

---

### Post by pokebirdd on 2010-04-23
> **Compyx said:**
> Why? Since we're passing a pointer to the structure, the structure itself gets modified in the function, so there's no need to return a pointer to the structure since we already have that information (the structure `tv' itself).

Well, it would be slightly more convenient to write:
```
cout << modify(&tv)->x;
```instead of:
```
modify(&tv);
cout << tv.x
```

---

### Post by dragos2 on 2010-04-23
Don't do that, its poor design. Make a class object and return that.
C# uses tuples and it can return up to two values from a method which is handy but poor design.

---

### Post by LKjell on 2010-04-23
> **Compyx said:**
> Why? Since we're passing a pointer to the structure, the structure itself gets modified in the function, so there's no need to return a pointer to the structure since we already have that information (the structure `tv' itself).

I guess I just love the toString() method in Java. I found something similiar with C++; Another reason why you want to return the class is to chain modify it if you want.

```


#include <iostream>

using namespace std;

class mStruct {
public:
	int x;
	int y;

	mStruct (int x, int y) {
		this->x = x;
		this->y = y;
	}
};

std::ostream& operator<<(std::ostream &strm, const mStruct &a) {
	return strm << "x = " << a.x << " y = " << a.y;
}

mStruct &modify(mStruct &v) {
	v.x += 10;
	v.y = v.x * 25.5;

	return v;
}

int main()
{
	mStruct tv(5,0);

	cout << tv << endl;
	cout << modify(tv) << endl;
}

```

---

### Post by phrostbyte on 2010-04-23
Of course you can also use a struct, but I guess you could consider a struct "one value".

Some languages (ex: Python) let your return multiple values (via a tuple).

```

def somefunc():
   return 5, 7

a, b = somefunc()

```

a is 5, b is 7

---

### Post by phrostbyte on 2010-04-23
There is also the yield construct in Python (and other languages), which is a bit difficult to explain, but it basically turns any function into a state machine which syntactically looks as if it's returning many values.

---

### Post by soltanis on 2010-04-23
> **lisati said:**
> This is the C equivalent of what I was taught, and is what I'd recommend that you use if possible.

That is C++ code. The C equivalent involves pass-by-pointer:

```

/* sum acc with x and return it in acc */

int sum(int *acc, int x)
{
    return (*acc = *acc + x);
}

```

There is nothing particularly "wrong" or "dangerous" about returning information about a function call in a buffer. read(2) returns its data in the buffer, the pointer to which is passed as its second argument.

Of course, memory is unchecked in C (and C++ too, but C++ has other constructs which I guess are supposed to make things safer) so any bounds-checking/buffer non-overflowing/stack-smashing avoidance needs to be done at the application level.

If you simply want to return information in a complex datatype but don't want to clobber your input values (or use pointers), simply define a struct:

```

struct retval {
   int a;
   float b;
};

```

And return it in your function call.

---

### Post by azagaros on 2010-04-23
a reference usually means I use the variable where it originally started.  

```

int x;
int y;

FunctionXY(&x, &y);


void functionXY(int inX, int inY)
{
    inX++;  // will add 1 to X from the above function call.
    inY++;  // will add 1 to y from the above function call.
}

```

I am a person who doesn't use globals so passing by reference is how I pass a lot of things...

```


std::string aString;
ASrtingWorkFunction(&aString);  // I do work on the string...
// when I got back here the string is modified...
// this is great if I have to strip stuff from the string that the normal parsing functions don't do.


```

Another way to pass multiple values back is use a structure or class.

---

### Post by slooksterpsv on 2010-04-24
Or you could do VB:
[php]
'... not all code is shown

Dim alpha As Double
Dim beta As Double

Property pAlpha as Double
 Set(ByVal value As Double)
  alpha = value
 End Set
 Get
  Return alpha
 End Get
End Property

'Add property for beta
'run like so

Public Sub ChangeAlphaBeta(ByVal x As Double, ByVal y As Double)
 pAlpha.Set(x)
 pBeta.Set(y + pAlpha * 5)
End Sub

Public Sub Test()
 ChangeAlphaBeta(5, 5)
 MsgBox(pAlpha.ToString + " = alpha" + vbCrLf + pBeta.ToString + " = beta")
 'Outputs 
 '5 = alpha
 '30 = beta
End Sub
[/php]

I know it's not C or C++, but just an example of VB

---

### Post by slooksterpsv on 2010-04-24
Isn't there a language that can do something like this:
[php]

int, int alpha(int x, int y)
{
 return x*y, y+x;
}

void main()
{
 int x, y;
 {x, y} = alpha(5, 5);
}

[/php]

Not sure if you guys get what I'm showing there, but its something like that that you can do in a language to return multiple variables from single function.

---

### Post by nikstard on 2010-04-24
> **phrostbyte said:**
> Of course you can also use a struct, but I guess you could consider a struct "one value".

Some languages (ex: Python) let your return multiple values (via a tuple).

```

def somefunc():
   return 5, 7

a, b = somefunc()

```

a is 5, b is 7

Uh, no, it returns exactly one value, the tuple. The caller just happens to destructure it. If the caller didn't destructure it, it would receive and use the tuple itself. 

The only language I know of that can return multiple values is Common Lisp, maybe some other Lisps have it too.

---

### Post by nvteighen on 2010-04-24
Ok, let's see...

Return means the function comes to an end and there's a value passed to the address the return pointer points to. Popping the call stack of the returning function is then performed.

Using pointers may be seen as a by-hand implementation of the principle above. I mean, by making your function return void and modify variables via pointers, one could say those pointer arguments are multiple "return pointers".

I know it's not an accurate description, but for the programmer both effects seems to be very similar.

---

### Post by Aped on 2010-04-24
Guys let's all just use global variables for everything okay

---

### Post by heikaman on 2010-04-24
> **Cracauer said:**
> The term "return value" should be used for something that has about the same semantics as the function return value, which is that it can be ignored (without cooperation from the function on the ignore part) **and that it doesn't involve mutation of anything**.

actually when you 'return val;' you **mutate** %eax:

ret.c:
[PHP]
int func(){ return 5; }
int main(){ return func();}
[/PHP]

[PHP]gcc ret.c -o ret && objdump --disassemble --section=".text" ret[/PHP]

[PHP]
00000000004004c4 <func>:
4004c8:	b8 05 00 00 00       	mov    $0x5,%eax
[/PHP]

---

### Post by Lux Perpetua on 2010-04-24
> **slooksterpsv said:**
> Isn't there a language that can do something like this:
[php]

int, int alpha(int x, int y)
{
 return x*y, y+x;
}

void main()
{
 int x, y;
 {x, y} = alpha(5, 5);
}

[/php]

Not sure if you guys get what I'm showing there, but its something like that that you can do in a language to return multiple variables from single function.

Of course, lots of higher level languages have this. For example, in Python: ```

def divmod(a, b):
    return a/b, a%b

q,r = divmod(15,4)

```

---

### Post by schauerlich on 2010-04-24
> **Lux Perpetua said:**
> Of course, lots of higher level languages have this. For example, in Python:

Although you could argue that only one value is really being returned - the tuple object. Python's syntax just allows you to drop the parentheses under certain circumstances (such as on the left side of the assignment operator), so it's a little harder to see. But, in effect, you're able to return multiple values - they're just packed into a container.

---

### Post by Lux Perpetua on 2010-04-24
> **schauerlich said:**
> Although you could argue that only one value is really being returned - the tuple object. The distinction is not useful or interesting.

---

### Post by slooksterpsv on 2010-04-24
Javascript is the one I was thinking of it does this:
```

<!--incomplete code--//>
var a, b;

function yay(aa, bb)
{
 return aa/2,bb*2;
}

function woohoo()
{
 {a, b} = yay(10, 5);
}

```

Tuples, I've heard of them, but never knew what they were. I'd rather setup classes for needed objects, create global objects, and modify/pull data via the classes.

---

### Post by phrostbyte on 2010-04-24
> **Lux Perpetua said:**
> The distinction is not useful or interesting.

It's not even a real distinction. A tuple just a fancy way to say "a representation of zero or more values". Abstractly, *all* functions accept a tuple and return a tuple. Python just lets to return n-tuples ("multiple values"). :)

---

### Post by LKjell on 2010-04-25
A tuple or vector is just another data structure. Which means it can be a linked list, array or some other fancy structure. So in reality python is returning a pointer and then interpret that.

---

### Post by Cracauer on 2010-04-25
If it mutates anything existing, whether it is on the stack of the calling function, global or whereever, it doesn't count as a return value.

Returning structure instances would kind of count, but the price is pretty hefty, many language implementations will do heap allocation for this. And if the structure implementation is based on pointers to fields you can easily nail down another CPU cache line. Returning two 32-bit integers that way will in most languages in a 64 bit environment account for at least 192 bits of basic structure overhead (a header and two pointers), not to mention the structure might only be able to point to composite objects with presumably one more word each. And if it is heap allocated the heap now tracks this object, involving at least two more pointers, and then of course there is the work for GC later.

And all of that for nothing if the caller opts to ignore the return value.

---

### Post by nvteighen on 2010-04-25
> **Cracauer said:**
> If it mutates anything existing, whether it is on the stack of the calling function, global or whereever, it doesn't count as a return value.

Returning structure instances would kind of count, but the price is pretty hefty, many language implementations will do heap allocation for this. And if the structure implementation is based on pointers to fields you can easily nail down another CPU cache line. Returning two 32-bit integers that way will in most languages in a 64 bit environment account for at least 192 bits of basic structure overhead (a header and two pointers), not to mention the structure might only be able to point to composite objects with presumably one more word each. And if it is heap allocated the heap now tracks this object, involving at least two more pointers, and then of course there is the work for GC later.

And all of that for nothing if the caller opts to ignore the return value.

It's a fair argument, in my opinion (I've been following this thread silently :)).

I guess the thing boils down to the perspective one takes. I know that may sound like the "easy way out" in any discussion, but I truly believe it applies in this case.

Ok, technically speaking you only return a value when the address at the return pointer is accessed and set with the value asked. That's how it works at low-level and why stack overflow attacks exist. We also know that a return address can only set one single thing at a time (as an address will hold the location of one single object or instruction) and that's why it's actually impossible to return two values so that Python has to use a hidden anonymous tuple to make it work.

Maybe we should call it another way, but the Python way or the call-by-reference tricks can be considered ways to "return" a value from an upper call stack to a lower one. From a conceptual point of view, the difference of letting a value "pop out" from the "interior" of a procedure by accessing the return pointer or by using pointers or a hidden tuple is zero.

---

### Post by phrostbyte on 2010-04-25
> **LKjell said:**
> A tuple or vector is just another data structure. Which means it can be a linked list, array or some other fancy structure. So in reality python is returning a pointer and then interpret that.

A tuple as much a data structure as a "set" or a "scalar" is. IE. not much of a data structure at all, it's actually a mathematical formalisation for a category (which is what a set or a scalar is in math as well). The actual data structure that represents a tuple (which can be as simple as setting a few registers) is irrelevant to its definition.

A tuple is a category that represents a "non-unique finite set of ordered values". You could say Python returns a "non-unique finite set of ordered values" instead. But the term tuple can extend to other languages.

For instance in C:  

```
int foo(int blah, int monkey);
```

This is a function that takes in a 2-tuple and returns a 1-tuple.


```
void foo(void);
```

This is a function that takes in a 0-tuple and returns a 0-tuple.

I'm sure you can see that all functions accept a n-tuple and return a n-tuple.

You don't see C programmers throwing the word tuple around very often though. Functional programmers on the other hand, they like to talk in terms of tuples because functional programming is heavily influenced by mathematics, and uses mathematical terminology much more liberally. Python was influenced by this.

I also don't like the categorisation of vector as a *data structure*. Vector is a type of category in mathematics, again where the underlying "data structure" is irrelevant. 

If you are referring to the C++ implementation, what you are talking about is an extendible array. When I talk about data structures I talk about "linked list" or "array" or "binary search tree", not vector<T> or list<T> or map<T, S>.

That's why some books like to separate the idea of data structure and "abstract data type". IE: Stack is an ADT that can be implemented using the array or linked list structures. You can view and ADT is a kind of contract or interface that can be wrapped around one more concrete data structures. That's actually the approach Java takes in its collections library.

---

### Post by LKjell on 2010-04-25
Well it is just two words which means the same. As I said the underlying structure can be anything. But what I am pointing at is that function in a computer only return a memory location. If you know how to return two memory locations without returning one then shed some light on it.

---

