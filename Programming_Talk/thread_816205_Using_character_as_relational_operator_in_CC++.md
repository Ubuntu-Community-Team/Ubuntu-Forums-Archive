---
title: "Using character as relational operator in C/C++"
date: 2008-06-02
forum: Programming Talk
---

### Post by control_guy on 2008-06-02
Hello there

How can I use a character entered by the user as a relational operator. Something like: 

```
int var1 = 30;
int var2 = 20;
char op_char = cin.get();         // User enters '<'

if (var1 op_char var)
{
Do something...
}

```
I want to avoid a lot of switch case statements.
Any help?

Thanks.

---

### Post by slavik on 2008-06-02
> **control_guy said:**
> Hello there

How can I use a character entered by the user as a relational operator. Something like: 

```
int var1 = 30;
int var2 = 20;
char op_char = cin.get();         // User enters '<'

if (var1 op_char var)
{
Do something...
}

```
I want to avoid a lot of switch case statements.
Any help?

Thanks.
you really can't ...

---

### Post by Bichromat on 2008-06-02
You'd need an equivalent of the "eval" function found in some languages...

Edit : or map the chars to the desired functions ?

---

### Post by control_guy on 2008-06-02
> **Bichromat said:**
> You'd need an equivalent of the "eval" function found in some languages...

Yes thats what I am looking for in C/C++. It is in Matlab.

---

### Post by CptPicard on 2008-06-02
Eval is a very high-level language feature... you just don't have it in statically compiled languages like C or C++. You'd have to essentially run some kind of interpreter on top of your own code.

---

### Post by dempl_dempl on 2008-06-02
No, a hash map + pointers to functions  will do the trick :)  .

Aspect-oriented programming exists because of situations like that .

---

### Post by control_guy on 2008-06-02
> **dempl_dempl said:**
> No, a hash map + pointers to functions  will do the trick :)  .

Could you kindly post some example code?

---

### Post by CptPicard on 2008-06-02
> **dempl_dempl said:**
> No, a hash map + pointers to functions  will do the trick :)  .

It's still a glorified switch/case statement :)

---

### Post by dempl_dempl on 2008-06-02
This is aspect-oriented example.


Create a factory.h file : 

```

/*This is a file factory.h  */



typedef bool (*funcPtr)(int , int);


#include <map>

class OperatorsFactory
{
 private:
 	
 	//Did not have time for generic singleton :)
 	/ nor generic factory :)
 	OperatorsFactory() {}
 	~OperatorsFactory() {} 
 	
 	
 	std::map< char, funcPtr >   operationsMap;
  public:
  	OperatorsFactory& getInstance()   	
  	{ 
  		static OperatorsFactory of;
  		return of
  	}
  	
  	
  	void register(  char op , funcPtr   fp )  	
  	{
  		operationsMap.insert (  make_pair( op , fp )  );
  	}
  	
  	
  	
  	funcPtr getByOperator( char op )  	
  	{
  		return operationsMap.find( op.second );
  	}
}

//--------------End of Factory.h -----------------------------------///



```




Next , create a  file  called less_than.cpp and add it to project

```


/*This is less_than.cpp */

#include "factory.h"


//Anonymous namespace , common practise , for this things , I'll explain why some other time :)
namespace 
{
	bool less_than_function( int a , int b )
	{
		return a < b;
	}
	
	
	OperatorsFactory::getInstance().register( '<' , less_than_function);	
}


```


Create main.cpp , and add it to project :


```

/*This is less_than.cpp */



//Note the fact I did NOT use  #include less_than.h or anything !
#include "factory.h"

int main()
{
	char c;
	cin >>c ;
	
	
	OperatorsFactory& opFactory = OperatorsFactory::getInstance().
	
	funcPtr fp = opFactory.getByOperator(c);
	
	if(fp(2,3))
		cout << "Yes! it\'s alive! " << endl;
	
}

//--------------End of main.cpp -----------------------------------///


```
 Now here's  the interesting part 
If you wany yo create another operator, create a file called   , for example , equals.cpp  
 and add it to project



```


/*This is l equals.cpp  */

#include "factory.h"


//Anonymous namespace , common practise , for this things , I'll explain why some other time :)
namespace 
{
	bool equals( int a , int b )
	{
		return a < b;
	}
	
	
	OperatorsFactory::getInstance().register( '==' , equals);	
}


//--------------End of equals.cpp -----------------------------------///


```

Now, if you want to use   operator '==' , you don't have to change main.cpp file,
just add equals.cpp to project, and it'll self-register the   '==' operator  to main.cpp 

You can do this for as many operators as you would like. 

Of course, you can put as many operators as you want in one cpp file.

Of course, this aspect-oriented example is used for some larger projects , which need this plugin-based architecture,
this is a little bit of over-kill :D .

The whole strength in this example is that you don't change your main.cpp code.

When you want a new operator , you **add** a new module ( you add the code , you don't change it )

It also has an advantage of code being a lot less coupled, unlike switch statement, which has to #include all 
the code in one file. Less external depencies makes program a lot easier to maintain .


Btw, did I've scared you with this code ?  You've asked for  dynamic operators , and I've thrown you the aspect-oriented programming :) 

Sorry if I did :)

Cheers!

---

### Post by Can+~ on 2008-06-02
If this is just a simple "a ? b" kind of program, yes you could use a hash or a simple switch case if you just use 4 operations.

If you eventually want to do a parse an expression, you could use a tree:

```

            *
           / \
          +   *
        / |   | \
       3  |   5  14
          -
         / \
        x   3

innode: 3 + (x - 3) * (5 * 14) 
```

This is useful when you need to store a formula for later, depends on what you're trying to accomplish.

Also, here is the python "one-liner"

> [FONT="Courier New"][COLOR="#0081FF"]print[/COLOR] input("command:")[/FONT]

---

### Post by dempl_dempl on 2008-06-02
Sorry, accidentally duped the post ( it's browser fault , as usual :) )

---

### Post by Can+~ on 2008-06-02
> **dempl_dempl said:**
> lots of code, obligatory "Cheers!"

Oh man, If I were the OP that would kill any desire to program. Also, could you add "CODE" or "PHP".

---

### Post by dempl_dempl on 2008-06-02
Yeah, Well I've tried ... but this is actually nice aspect-oriented example and shows how to implement modularity... if you have someone to explain it to you  nicely :) ...

Oh well.. I hate teaching anyway .. :) 

Cheers!

---

### Post by Can+~ on 2008-06-02
> **dempl_dempl said:**
> Yeah, Well I've tried ... but this is actually nice aspect-oriented example and shows how to implement modularity... if you have someone to explain it to you  nicely :) ...

Oh well.. I hate teaching anyway .. :) 

Cheers!

And have you invested in other paradigms? Even if you won't use other language, you'll learn a new point of view. For example, kinda-functional with py:

[PHP]#Define some example functions
def opSum(a, b):
	return a+b

def opSub(a, b):
	return a-b

#Dictionary that stores the functions (or lambda function in case of "*").
table = {"+" : opSum,
         "-" : opSub,
         "*" : lambda a,b : a * b}

def operation(character, a, b):
	#Get function from dict, call with (a,b)
	return table[character](a, b)

#Try them (7 - (5 + 3))
print operation("-", 7, operation("+", 5, 3))

#Append new one, using lambda!
table["=="] = lambda a,b : a == b

#Try the new operation
print operation("==", 6, 6)[/PHP]

To the OP, if this is a task for school, just do a switch-case or a short hash; google for Hash and C++.

---

### Post by dempl_dempl on 2008-06-02
Aaargghh ,  you python fanatics...

What I've presented is Aspect-oriented programming ... 
It was over-kill for this topic.. ok.. I know... 

What you've just shown can be done in C++ just as easy..
But I'm bit tired of typing...

The whole thing is that my over-kill was modular,
that operations can be added/removed by adding/removing
file from a project .. and I've made it for simple school project :) .. which is crazy .. but let it be :) 

to OP:

I agree with Can~+ , simply searching  a **hash table** +  **C++** + **pointers to functions** is what you need.


and to make it up, and to show that I can write simple code too :) ( to believe it or not ! :D )


Here's a C++ **simple** example :

```


#include <map>
#include <iostream>

using namespace std;
typedef  bool (*FuncPtr)(int,int);

bool moreThan(int a,int b)
{
 return a > b;
}

bool lessThan(int a,int b)
{
 return a > b;
}


map<char,FuncPtr> opMap;

opMap.insert( make_pair( '<', lessThan);
opMap.insert( make_pair( '>', moreThan);

int main()
{
 char c;
 cin >> c;

 int a =4,b =5;
 FuncPtr fp = opMap->find(c).second;
 cout <<   (*fp)(a,b);

}


```
Cheers!

---

### Post by Quikee on 2008-06-02
> **dempl_dempl said:**
> This is aspect-oriented example.

...

Btw, did I've scared you with this code ?  You've asked for  dynamic operators , and I've thrown you the aspect-oriented programming :) 

...



Sorry I don't want to sound rude but this example has nothing to do with aspect-oriented programming. This is only a registry for operators which has some touches from functional programming.


Aspect oriented programming has to do with applying aspects to the code without actually modifying the code - it would be totally transparent for the code. For example logging is a typical thing you can do with aspects - you don't change the actual code to do logging but you register a pointcut to execute a logging method on all methods which name starts with "get" and "set". 

Another example is to automatically start a transaction before and commit/rollback a transaction after all methods that are annotated @Transactional" (Java example).

---

### Post by control_guy on 2008-06-02
dempl_dempl:

Thanks for both pieces of code. I am going to use the second, hash and function pointer based version. On the other hand, the first was a good introduction to the aspect-based programming.

Can+~:
Thanks. The Python example is good, but I am writing a C/C++ only windows-based code. It is actually not a school project. I am implementing a Matlab-like "find" function to search arrays/matrices and the user could enter any condition to be matched for the elements, the indices of which are to be found. My colleague suggested to use lex/yacc but I think for such simple parsing, it is really over-kill.

---

### Post by dempl_dempl on 2008-06-03
> **Quikee said:**
> Sorry I don't want to sound rude but this example has nothing to do with aspect-oriented programming. This is only a registry for operators which has some touches from functional programming.


Aspect oriented programming has to do with applying aspects to the code without actually modifying the code - it would be totally transparent for the code. For example logging is a typical thing you can do with aspects - you don't change the actual code to do logging but you register a pointcut to execute a logging method on all methods which name starts with "get" and "set". 

Another example is to automatically start a transaction before and commit/rollback a transaction after all methods that are annotated @Transactional" (Java example).


Actually, I am applying aspects to the code, without modifying it.
If you want to add a new method, you don't change the main() code, you just 
add the new Unit to the project!  You don't change the code, you add the new code! This could be just as easy exported to DLLs and stuff.

I know this was not a typical example of aspect , but if you look carefully, I did not included operators themself in the main.cpp unit.
They're uncoupled with the rest of the code.

Thus we conclude, I was right all along , and that is what truly matters
:p:p:p

---

### Post by Wybiral on 2008-06-03
> **dempl_dempl said:**
> Aaargghh ,  you python fanatics...
...

What you've just shown can be done in C++ just as easy..


But can C++ do this? :p

```
def make(op, a):
    ops = {'+': (lambda b: b + a),
           '-': (lambda b: b - a),
           '*': (lambda b: b * a)}
    return ops[op]

plus2 = make('+', 2)
minus1 = make('-', 1)
times10 = make('*', 10)

print minus1(times10(plus2(10)))
```

---

### Post by dempl_dempl on 2008-06-03
Can Google engine be written in Python and to actually work?
Can Neural Network Image recognition be written in Python and to search something in less than month?
Linux is written in Pyhton I suppose?

...
bla bla bla 
...
..
My language is better than yours... bla bla bla 
..
[let's flood the Internet with those discussions]
..

```

def make(op, a):
    ops = {'+': (lambda b: b + a),
           '-': (lambda b: b - a),
           '*': (lambda b: b * a)}
    return ops[op]

```

They will add lambdas in next standard. While at it, can you do the template-meta programming in Python?


Cheers!

---

### Post by Wybiral on 2008-06-03
> **dempl_dempl said:**
> Can Google engine be written in Python and to actually work?
Can Neural Network Image recognition be written in Python and to search something in less than month?
Linux is written in Pyhton I suppose?


You're a bit defensive, lol. I never said that C wasn't needed for certain things, but only for those certain things. Are you writing Linux and image recognition software all day? If so, maybe you should use C, otherwise you're probably wasting your time.

And my argument wasn't with Python, it was higher level languages in general. I could have said
```

(define (make op a)
 (cond ((eq? op +) (lambda (b) (+ b a)))
       ((eq? op -) (lambda (b) (- b a)))
       ((eq? op *) (lambda (b) (* b a)))))

```


> **dempl_dempl said:**
> They will add lambdas in next standard. While at it, can you do the template-meta programming in Python?

Cheers!

You do realize that lambdas aren't nearly as useful in a statically typed language, right? And that template-meta-programming is a mere joke compared to Lisps macro system...

---

### Post by Lster on 2008-06-03
Things like that can be done in C too. You can do many things to achieve that kind of functionality.

I mean, it's not like there is *anything* Python can do that C can't. But it's not true the other way round. Python's strength lies in ease of use (it's between C and pseudocode perhaps). :)

---

### Post by Wybiral on 2008-06-03
> **Lster said:**
> ...

Well, without some kind of JIT library (or actually implementing Lisp in C) you couldn't do the lambda example I showed in Python and Lisp. C isn't capable of the closure that lambdas provide.

BTW, what about generators?

```

def fibs():
    a, b = 1, 1
    while True:
        yield a
        a, b = b, a + b

```

Or introspection (you can fake genericness in C, but there's no way to determine the original type or what attributes it has at runtime).

---

### Post by Lster on 2008-06-03
[QUOTE=Wybiral]BTW, what about generators?[/QUOTE]

Return the values to a list? That might even be how Python does it - but of course it hides things like that away. The benefit being elegance with the expense being a slight loss of control.

[QUOTE=Wybiral]Or introspection (you can fake genericness in C, but there's no way to determine the original type or what attributes it has at runtime).[/QUOTE]

How about having all structures have the first 4/ 8 bytes reversed for identification? Even if you don't know what you are pointing to, you can work it out then (so long as you know it's a structure)!

But really that is it. Python gives one the ability do a lot in a very little time so long as development time is dominant over run time. Often I know I can implement something very simply with Python but it would take a bit longer in C. If run time is not an issue then I usually choose Python.

However I have certain problems (Project Euler comes to mind) for which finding an efficient solution for which Python would be feasible would take too long. I usually brute-force it in C then. :)

---

### Post by Wybiral on 2008-06-03
> **Lster said:**
> Return the values to a list? That might even be how Python does it - but of course it hides things like that away. The benefit being elegance with the expense being a slight loss of control.
Absolutely not. That's the power of generators, the state is preserved in the function and resumed each call to "next" (which is handled during iteration or can be used explicitly).

This is exactly why you use generators instead of full-on list building. Consider the following:

```

def gmap(f, seq):
    for i in seq:
        yield f(i)

def gfilter(f, seq):
    for i in seq:
        if f(i):
            yield i

def take(n, seq):
    return [x for x, y in zip(seq, xrange(n))]

```

Those two functions are lazily evaluated over the list, the list is NOT built all at once. This allows you to sort-of plug them together and pull some sequence through them instead of building them all... Passing them... Building them... Etc.

BTW, you don't have to write these in Python, they already exist in the "itertools" module.

```

print take(20, gmap(lambda x: x * 2, gfilter(is_odd, fibs())))

```

(take the first twenty odd fibonacci numbers, where each is multiplied by two)

The above doesn't create a list of all the fibs (which is impossible, because it's an infinite generator, I posted the code for it before), instead "gfilter" pulls them out one-by-one. And it also doesn't create the entire filtered list before passing to the map, the "gmap" pulls them one-by-one. It's only when it gets to the "take" that it's accumulating them into a list, but I didn't have to do that either... I could have implemented a generator form of "take" and iterated them (and this would never build any lists, purely pulling values when needed in the iteration).

This is the power of generators/streams and it's VERY difficult to do in a statically typed language, especially ones that don't have any true concept of "lambda". I suggest you read some [SICP]("http://mitpress.mit.edu/sicp/") (lecture videos can be found [here]("http://swiss.csail.mit.edu/classes/6.001/abelson-sussman-lectures/")), they talk about streams and the power of lambdas a lot.

> **Lster said:**
> How about having all structures have the first 4/ 8 bytes reversed for identification? Even if you don't know what you are pointing to, you can work it out then (so long as you know it's a structure)!

But really that is it. Python gives one the ability do a lot in a very little time so long as development time is dominant over run time. Often I know I can implement something very simply with Python but it would take a bit longer in C. If run time is not an issue then I usually choose Python.

However I have certain problems (Project Euler comes to mind) for which finding an efficient solution for which Python would be feasible would take too long. I usually brute-force it in C then. :)

Right, you can jump through hoops trying to implement a universal type system in C and essentially end up recoding Pythons object system, lol. But this is a waste of precious time...

And I'm not saying that C is useless, not at all, but I am saying that its use should be limited to situations where it's an absolute must. And one piece of a project requiring a C component doesn't mean that the entire project should be written in C :)

---

### Post by Lster on 2008-06-03
[QUOTE=Wybiral]Absolutely not. That's the power of generators, the state is preserved in the function and resumed each call to "next" (which is handled during iteration or can be used explicitly).[/QUOTE]

Wow. I never realized that and I've been using generators quite a bit! I guess the C equivalent would use global variables and return for each iteration. The function would get called again and the variables would be unchanged from the last call.

Am I understanding correctly?

---

### Post by Wybiral on 2008-06-03
> **Lster said:**
> Wow. I never realized that and I've been using generators quite a bit! I guess the C equivalent would use global variables and return for each iteration. The function would get called again and the variables would be unchanged from the last call.

Am I understanding correctly?

Global variables wouldn't work, because each instance of the generator has its own state, so you can say:

```

a = fibs()
b = fibs()

```

And you can iterate/pull values from them separately.

You would basically need some sort of structure to hold all local variables and pass that to the function or something... But, I'm sure you can imagine how much more complex that would eventually get as you're passing them down streams and handling the memory management for it, etc.

---

### Post by Lster on 2008-06-03
You are right. :) By using global variables I simplified it to the point where I lost some generality. It would also make multithreading extremely hard.

---

### Post by CptPicard on 2008-06-03
And the "yield" statement really "freezes" execution state at the point in code, and when you next() again, you resume from that point. Return would always start at the top of the function.

---

### Post by Wybiral on 2008-06-03
> **CptPicard said:**
> And the "yield" statement really "freezes" execution state at the point in code, and when you next() again, you resume from that point. Return would always start at the top of the function.

Yeah, I forgot to mention that :)

```

def primes():
    yield 2
    yield 3
    # Start real prime generation here

```

You can yield anywhere you want, it doesn't have to be in a loop or anything.

---

### Post by Lster on 2008-06-03
Part of the data structure could define the position within the function. Or you could start using assembly. That can do these types of things very easily. :)

---

### Post by Wybiral on 2008-06-03
> **Lster said:**
> Part of the data structure could define the position within the function. Or you could start using assembly. That can do these types of things very easily. :)

Yeah :)

But at the end of the day...

Was it worth it?

---

### Post by Lster on 2008-06-03
Possibly... :)

I'd be interested if you can think of a situation where generators are necessary, though. I can't think of any really...

---

### Post by CptPicard on 2008-06-03
> **Lster said:**
> 
I'd be interested if you can think of a situation where generators are necessary, though. I can't think of any really...

Generators and streams and lazy-lists and such are very very handy in functional programming. Strictly no high level structure is ever *necessary*, you can always code it all in Assembly, but... read the linguistics thread, it's all about how structures map to problems and your brain.

---

### Post by Lster on 2008-06-03
[QUOTE=CptPicard]Generators and streams and lazy-lists and such are very very handy in functional programming. Strictly no high level structure is ever necessary, you can always code it all in Assembly, but... read the linguistics thread, it's all about how structures map to problems and your brain.[/QUOTE]

That thread looked interesting, if a little over my head. :confused:

---

### Post by Wybiral on 2008-06-03
> **Lster said:**
> I'd be interested if you can think of a situation where generators are necessary, though. I can't think of any really...

It's useful when you create functions that take in generators, or in Pythons case, generic sequences. Take the sum function for instance... When you say
```

print sum(2 ** x for x in xrange(5))

```
You're sending a generator to "sum" which iteratively pulls the values from the generator. Without this functionality, you would have to build the entire list, pass it, then sum would iterate over it... What a waste...

And when you start to compound these, they become even more powerful, capable of efficiently and cleanly representing massive transformations on lists.

```

fibs = gen_fibs()
odd_fibs = ifilter(is_even, fibs)
sqr_odd_fibs = imap(lambda x: x * x, odd_fibs)
print sum(itake(1000, sqr_odd_fibs))

```

It's like you've constructed this pipe at runtime for which the values will flow through. No longer do you have to think in terms of iterations, and applying more and more maps and filters to the sequence is just a matter of adding another small pipe to the end. You simply don't have that kind of power with iterations, you can't dynamically construct them in this manor. And you also don't have the efficiency if you're constantly building new lists with each iteration.

I mean this in a constructive way, but when you can't see a situation that a higher-level functionality is useful for, chances are you're stuck in a form of [blub]("http://www.paulgraham.com/avg.html").

---

### Post by Lster on 2008-06-03
[QUOTE=Wybiral]You're sending a generator to "sum" which iteratively pulls the values from the generator. Without this functionality, you would have to build the entire list, pass it, then sum would iterate over it... What a waste...[/QUOTE]

You could simply sum up as you went along, couldn't you? Fastest still, in this case, would be to use "print 2**x - 1" (if x &#8805; 0 and x is whole).

---

### Post by Wybiral on 2008-06-03
> **Lster said:**
> You could simply sum up as you went along, couldn't you? Fastest still, in this case, would be to use "print 2**x - 1" (if x &#8805; 0 and x is whole).

What about my second example? It's not so easy... Especially since the "pipes" you're adding can be conditional. I might want to include the even numbers in some cases, so I wouldn't apply the "ifilter(is_even, fibs)" part (I just realized I meant to put "is_odd", but you get the point).

You can stack this pipeline up as you go, passing it to functions and returning new pipes... Then you just have to start pulling the values out. There is no simple iterative approach to something like this, it's just not nearly as flexible.

---

### Post by Lster on 2008-06-03
How about this?

[PHP]
t = 0

a = 1
b = 2
c = 2
while c < 1000:
	t += c * c
	
	i = 0
	while i < 3:
		c = a + b
		a = b
		b = c
		
		i += 1

print t

[/PHP]

It sums up the square of all even Fibonacci numbers smaller than 1000. No needs for "pipes" here! :)

---

### Post by Wybiral on 2008-06-03
> **Lster said:**
> It sums up the square of all even Fibonacci numbers smaller than 1000. No needs for "pipes" here! :)

Great, you can solve ONE problem. My example is meant to highlight the ability to solve lots of problems, in a dynamic and modular way.

What if you need to be able to switch out the even for odd? What if you want them to all be scaled by some value before being summed? What if you don't want to sum them at all, but instead you want to find the product...

You can keep rewriting the same crap for each new use, or using strange workarounds to accomplish this, but there are better ways, and the stream-based map-filter-reduce is one of the most efficient ways to do this.

---

### Post by Quikee on 2008-06-03
[PHP]
t = 0

a = 1
b = 2
c = 2
while c < 1000:
	t += c * c
	
	i = 0
	while i < 3:
		c = a + b
		a = b
		b = c
		
		i += 1

print t

[/PHP]

Aaaa.. don't write C in python... it hurts my eyes and my brain raised a RuntimeError! 








Just kidding.. 


..about the brain and RuntimeError.

---

### Post by Lster on 2008-06-03
[QUOTE=Wybiral]Great, you can solve ONE problem. My example is meant to highlight the ability to solve lots of problems, in a dynamic and modular way.

What if you need to be able to switch out the even for odd? What if you want them to all be scaled by some value before being summed? What if you don't want to sum them at all, but instead you want to find the product...

You can keep rewriting the same crap for each new use, or using strange workarounds to accomplish this, but there are better ways, and the stream-based map-filter-reduce is one of the most efficient ways to do this.[/QUOTE]

If it was odd would be harder as that was specifically written for even numbers. However I could have used a method for which I would only have to swap a bit of code for "== 1" to work for odd values.

Scaling is trivial by just multiplying at the end.

To find the product requires changing just one character...

I truly don't see how the method you propose is superior. This way is really quite easy and efficient.

---

### Post by Lster on 2008-06-03
[QUOTE=Quikee]Aaaa.. don't write C in python... it hurts my eyes and my brain raised a RuntimeError![/QUOTE]

I would be interested in seeing a pythonic way of writing code. I too find it a little ugly. :(

---

### Post by Wybiral on 2008-06-03
> **Quikee said:**
> Aaaa.. don't write C in python...

EXACTLY! A lot of C programmers learn the minimal Python, or some other high-level language, only learning about the features they were comfortable with and then wonder why they didn't find the higher level language more useful.

To program in a higher level language, you have to think different than you do in C. The thing that makes Python what it is isn't the new syntax, that's all meaningless garbage, what makes it special is the dynamicness and new features, and if you aren't going to learn them and use them... Using the higher level language is pointless.

---

### Post by Wybiral on 2008-06-03
> **Lster said:**
> If it was odd would be harder as that was specifically written for even numbers. However I could have used a method for which I would only have to swap a bit of code for "== 1" to work for odd values.

Scaling is trivial by just multiplying at the end.

To find the product requires changing just one character...

I truly don't see how the method you propose is superior. This way is really quite easy and efficient.

You don't get it...

The same pieces from my method could be interchanged, reordered, replaced, etc. I don't have to keep writing these new implementations, I just stack these little generators up. It can be constructed dynamically, at runtime. You just keep recoding it... That's the whole point. Stop. You should be able to use the same code, you're repeating WAY too many patterns.

What if you wanted users to pass the "source" sequence to the function, instead of just fibonacci numbers? What if you want to conditionally (AT RUNTIME) determine which values to filter and how to transform the values?

---

### Post by Lster on 2008-06-03
[QUOTE=Wybiral]To program in a higher level language, you have to think different than you do in C. The thing that makes Python what it is isn't the new syntax, that's all meaningless garbage, what makes it special is the dynamicness and new features, and if you aren't going to learn them and use them... Using the higher level language is pointless.[/QUOTE]

Yes, I've kind of felt that I haven't gone deep enough into Python. Maybe you could advise me some tutorials for enlightenment. I quite often see Python code exploiting new features I have barely any knowledge of.

---

### Post by Wybiral on 2008-06-03
> **Lster said:**
> Yes, I've kind of felt that I haven't gone deep enough into Python. Maybe you could advise me some tutorials for enlightenment. I quite often see Python code exploiting new features I have barely any knowledge of.

Yeah, I know what you mean, especially coming from C. I wrote C in Python for a long time before finally starting to ease into the Python idiom. One thing that helped me a lot was reading Python code wherever I could... The standard library, for instance, and other modules are great to read. Also the Python docs on the website are amazing (the tutorial, the language reference, and the library reference are all a must-have).

And if you're really comfortable with C, you can go straight to the source code for Python, which helped me a lot with learning what was efficient and how things really were underneath it all.

Another thing that's been even further broadening my concept of lambdas, streams, and functional programming in general has been learning Lisp, and as I mentioned before SICP (both the book and the lectures).

---

### Post by Can+~ on 2008-06-04
```
t = 0

a = 1
b = 2
c = 2
while c < 1000:
    t += c * c
    
    i = 0
    while i < 3:
        c = a + b
        a = b
        b = c
        
        i += 1

print t
```

That would be the procedural approach, one solution, one strict case that solves the issue. The way Wybrial approaches (besides looking not like C), tries to be more flexible, which leads to a better future-proof design:

So to get a modular approach, you need each block to do a task right. In fact, you don't even have to care about what he does inside, it's just a black box that gets a value and returns another (or modifies in place), but you know what that box will do, and whatever you need to change, it can be changed via parameters, not having to copy-paste and edit. I essence, the real definition of a function in Math:

```
     Black box function
x, y--> [f (x, y)] --> usable value
```

This is one of the basis of (but not limited to) object oriented programming. Having blocks that do the tasks well is also the principle that Bash uses, it leads to chain them:

```

x, y --> [f (x, y)] --> z --> [g(z)] --> usable value

```

It all looks very simple, but to accomplish that level of modularity takes some time, and reset your way of thinking. Think outside of the box, the box can do whatever it wants inside it, you just use it.

The relation programmer and the language is as the relation between the painter and the canvas, the tool and the canvas are just following orders, the painter is who makes all the work. You can code on binary on in the best language, it doesn't matter, your brain is what does the real job, the computer just follows you.

---

### Post by CptPicard on 2008-06-04
> **Can+~ said:**
> You can code on binary on in the best language, it doesn't matter, your brain is what does the real job, the computer just follows you.

+1... and to think of it, wybiral's version is so much more readable. It expresses the concept of what is being done nicely (once you get used to reading the primitives)... while in a procedural/imperative solution, you really need to trace the execution's parts and construe in your mind what the original problem was that we're solving here.. :)

---

### Post by Lster on 2008-06-04
Can+~, thanks for that post - you've cleared up quite a few things for me. I think I understand what Wybiral and you are saying. By using that method, Wybiral's trying to remove the staticness of the implementation by defining blocks that can be "pick and mixed" so to speak.

That way of programming may be conceptually simple but I don't think it gives the programmer the option to use clever algorithms. For example, if I understood Wybiral's code, it generates all the needed Fibonacci numbers, testing them (and dismissing some), and then squaring them.

My method on the other hand uses the fact that every third Fibonacci number is even. With this knowledge I need not even check which numbers are even - they all are!

I do know that computational complexity wise they are equal, but I would guess my code is marginally faster. For other cases, I would expect taking Wybiral's approach could even lead to a far less efficient algorithm (computational complexity wise).

[QUOTE=Wybiral]What if you want to conditionally (AT RUNTIME) determine which values to filter and how to transform the values? [/QUOTE]

Not everything needs to be dynamic all the time. But when they do, you could just use "if"s with several different functions. There are quite easy ways to achieve dynamics like that. :)

---

### Post by Wybiral on 2008-06-04
> **Lster said:**
> Can+~, thanks for that post - you've cleared up quite a few things for me. I think I understand what Wybiral and you are saying. By using that method, Wybiral's trying to remove the staticness of the implementation by defining blocks that can be "pick and mixed" so to speak.


It's not just a matter of dynamicness, it's also about less rewriting of the same crap. When you write everything out procedurally, you often end up reimplementing the same things because they aren't as easy to interchange... Which leads to lots of copy&paste code and bloat. Streams allow you to abstract away some of your reoccurring patterns.

> **Lster said:**
> 
For example, if I understood Wybiral's code, it generates all the needed Fibonacci numbers, testing them (and dismissing some), and then squaring them.


If I were to use "map(add1, filter(is_even, fibs()))" what's really going on is this...

map says "pull a value from filter and do add1(i)"
filter says "pull a value from fibs() and return it if is_even(i)"
fibs simple spits out values when asked

This is repeated until "map" isn't able to pull a value, in this case, it's infinite, but if I said:

take(20, map(add1, filter(is_even, fibs())))

Then the "take" is what starts the "pulling" and it will stop after pulling 20 values through. It doesn't generate all of the fibonacci numbers necessary, it only pulls them out when needed as it goes. If you would be more satisfied, you could write a even_fibs generator instead of doing the filter so you can use your optimization... But the rest is exactly the same thing that would happen in an iteration, just more modular.

> **Lster said:**
> 
My method on the other hand uses the fact that every third Fibonacci number is even. With this knowledge I need not even check which numbers are even - they all are!


This is under the assumption that you can't just write an "every_third_fib" generator :) You can use those optimizations when needed, but piece it all together as a stream of generators.

> **Lster said:**
> 
For other cases, I would expect taking Wybiral's approach could even lead to a far less efficient algorithm (computational complexity wise).

Not necessarily...
In this case, with just streams, so it's not as interesting, it's just another way of abstractly handling the iterations. But the map/filter/reduce concept is VERY powerful when it comes to reducing complexity and especially paralleling the execution.

When I do "map(f1, filter(f2, items))" there's nothing holding this back from doing the filter test on each item in parallel, likewise with the map (after the filtered objects have been collected). Scalability then starts to come naturally. This is a powerful edge over constantly thinking in terms of iteration (where you're explicitly expressing the problem in a sequential nature), I don't care what order they happen in... Do it all at once, then collect them... Do them backwards... Whatever...

> **Lster said:**
> Not everything needs to be dynamic all the time. But when they do, you could just use "if"s with several different functions. There are quite easy ways to achieve dynamics like that. :)

Then you end up having to code those parts into the loops, and doing the conditions each loop. It's not as easy to write modularly where you can interchange pieces and reuse everything. It's not just about runtime dynamicness, it's about reusable, modular, scalable ways of dealing with large sets of data.

---

### Post by Lster on 2008-06-04
[QUOTE=Wybiral]This is under the assumption that you can't just write an "every_third_fib" generator  You can use those optimizations when needed, but piece it all together as a stream of generators.
[/QUOTE]

But then you would, effectively, be using my method... and perhaps adding streams on the end, which in this case would be useless...

[QUOTE=Wybiral]Not necessarily...
In this case, with just streams, so it's not as interesting, it's just another way of abstractly handling the iterations. But the map/filter/reduce concept is VERY powerful when it comes to reducing complexity and especially paralleling the execution.[/QUOTE]

How can they reduce complexity? I would love to see an example. :)

[QUOTE=Wybiral]When I do "map(f1, filter(f2, items))" there's nothing holding this back from doing the filter test on each item in parallel, likewise with the map (after the filtered objects have been collected). Scalability then starts to come naturally. This is a powerful edge over constantly thinking in terms of iteration (where you're explicitly expressing the problem in a sequential nature), I don't care what order they happen in... Do it all at once, then collect them... Do them backwards... Whatever...
[/QUOTE]

That's really looking to the future. I doubt many people have lots of cores on their computers. However it's an interesting point considering multicores look like they're here to stay. It definitely isn't impossible in C with multithreading - or hard for that matter.

In fact, I've been doing a lot recently with multithreading. My game engine, for example, is fully written in C and can support any number of processors (theoretically). For that I have a tasking system. A stack of tasks are stored and each one has dependencies. Each thread keeps checking the stack to see if a task is accessible; when one is, it runs it marking it done.

---

### Post by Wybiral on 2008-06-04
> **Lster said:**
> But then you would, effectively, be using my method... and perhaps adding streams on the end, which in this case would be useless...

Yes, Lster, in this EXACT, simplified, one-time-only case you can argue that none of this matters. But think bigger than this... Once you write that generator, you can use it anywhere you want! You can iterate over it with a for loop... You can pass it through filters, maps, reduces... You can take the nth element, the first n elements... Etc. It's modular. Reusable. Simple.

You keep referring to this exact example, stop. I'm talking about an entire concept, I don't care how easy it is to write this problem in C, the CONCEPT is what's important. Not this simple example.

> **Lster said:**
> 
How can they reduce complexity? I would love to see an example. :)


OK, perhaps I worded that incorrectly. Using streams, for instance, can increase the memory efficiency by not having to rebuild lists over-and-over (think about the spacial efficiency). And, using a parallel map/reduce you can scale the algorithms to as many processors or servers as you'd like. I know... You can do these things procedurally. It's just harder and more work that way. Spend the rest of your life writing millions of "for" loops if you want... But there ARE better ways.

This conversation has broken into two topics now, streams and functional map/reduce. I want to make it clear that we're talking about two things now. Streams go beyond map/reduce, you can do lots of things with them. Map/reduce is just a common use for them, and it's also an elegant and simple way to massively parallel various algorithms.

> **Lster said:**
> That's really looking to the future. I doubt many people have lots of cores on their computers. However it's an interesting point considering multicores look like they're here to stay. It definitely isn't impossible in C with multithreading - or hard for that matter.

WRT map/filter/reduce (not streams anymore):
This goes FAR beyond simple multithreading... This scales to entire server farms with little effort on the user. Google, for instance, has employed [mapreduce]("http://labs.google.com/papers/mapreduce.html") for many of their applications. It's simply the most natural way to deal with large sets of data. Constantly thinking sequentially in "for" loops just isn't going to cut it, it's a broken concept when you're trying to parallel your code, in its essence it is explicitly saying "I'm sequential".

Map and filter are much different... The order of execution doesn't matter, and that's the beauty of it, and functional programming in-general!

---

### Post by Lster on 2008-06-04
[QUOTE=Wybiral]Yes, Lster, in this EXACT, simplified, one-time-only case you can argue that none of this matters. But think bigger than this... Once you write that generator, you can use it anywhere you want! You can iterate over it with a for loop... You can pass it through filters, maps, reduces... You can take the nth element, the first n elements... Etc. It's modular. Reusable. Simple.

You keep referring to this exact example, stop. I'm talking about an entire concept, I don't care how easy it is to write this problem in C, the CONCEPT is what's important. Not this simple example.[/QUOTE]

I get your point but I don't think the situation you describe arises much. I guess all of this comes down to mindset. I have never had a problem in which I would use your techniques over my own. I can always find a way around the solution and usually very efficiently without using such constructs. I guess it really does come down to ease.

Really, I doubt there are any problems you can give me which require those kinds of methods. Or even any where I would have to go through a very long winded method.

[QUOTE=Wybiral]Using streams, for instance, can increase the memory efficiency by not having to rebuild lists over-and-over (think about the spacial efficiency).[/QUOTE]

Actually, my proposed way would not need to store a list.

---

### Post by Wybiral on 2008-06-04
> **Lster said:**
> I get your point but I don't think the situation you describe arises much. I guess all of this comes down to mindset. I have never had a problem in which I would use your techniques over my own. I can always find a way around the solution and usually very efficiently without using such constructs. I guess it really does come down to ease.

Of course, because you've never used it before :)

> As long as our hypothetical Blub programmer is looking down the power continuum, he knows he's looking down. Languages less powerful than Blub are obviously less powerful, because they're missing some feature he's used to. But when our hypothetical Blub programmer looks in the other direction, up the power continuum, he doesn't realize he's looking up. What he sees are merely weird languages. He probably considers them about equivalent in power to Blub, but with all this other hairy stuff thrown in as well. Blub is good enough for him, because he thinks in Blub.

"[Beating the Average]("http://www.paulgraham.com/avg.html")", Paul Graham

---

### Post by Lster on 2008-06-04
Yeah, but I get along fine. I never find the *need* for Python, but it's often desirable.

It's not that I'm closed to new languages, it's not that I don't try to explore them, it's just I don't see the need. The term "blub" programmer is really quite useless - by its loose definition almost every programmer is one. It would also appear Paul Graham is talking more about the business side of programming which is by no means the whole of it, nor the part I care for.

---

### Post by CptPicard on 2008-06-04
As I said before, functional-programming concepts can reduce "complexity" simply by revealing useful problem structure, which yields a better algorithm. A lot of stuff is just very naturally expressed functionally, simply because mathematics tends to already provide a good description. Imperative programming has the added problem of actually describing the "how", while functionally, you just tell the computer "what". And such abstract descriptions tend to be very very general and can be very elegant.

Pure-functional programming's ability to scale and to have all sorts of other fancy transformations applied to it shouldn't be underestimated either, parallelization is the future... and you should also remember that parallelization has a close cousin, distributed computing, which derives similar benefits.

You *can* get hidden complexity from things like generating your entire list in RAM etc... but you're not supposed to be stupid using any programming paradigm...

> **Lster said:**
> 
It's not that I'm closed to new languages, it's not that I don't try to explore them, it's just I don't see the need. The term "blub" programmer is really quite useless - by its loose definition almost every programmer is one.

Everyone is in some ways always a beginner... but blubness is a whole mindset of its own really. :) For example I have done enough to never underestimate some concept that I don't "feel the need for" because it tends to usually just mean that I haven't looked into it enough.

> It would also appear Paul Graham is talking more about the business side of programming which is by no means the whole of it, nor the part I care for.

Actually, he is pointing out that "surprisingly" Lisp is a business-capable language *too*. Lisp was supposedly the Holy Grail of AI back in the day in the 1960s... it wasn't, of course, but it got a lot, lot of stuff right.

Your last sentence really is the core reason why you *should* look into all of this. Just because you theoretically can do it all in C, doesn't mean there aren't extremely insightful and cool things out there in higher-level languages. You're starting to sound like Shining Arcanine ... read SICP and then come tell Wybiral and I that you don't need to know Scheme because you're interested in the non-business-side of programming ;)

---

### Post by Bichromat on 2008-06-04
> **CptPicard said:**
> As I said before, functional-programming concepts can reduce "complexity" simply by revealing useful problem structure, which yields a better algorithm. A lot of stuff is just very naturally expressed functionally, simply because mathematics tends to already provide a good description. Imperative programming has the added problem of actually describing the "how", while functionally, you just tell the computer "what". And such abstract descriptions tend to be very very general and can be very elegant.

But it can be very hard to wrap your mind around these concepts. I'm trying to learn Haskell and I just don't see how I could do e.g. a physics simulation, because a loop over a certain number of time steps just seems the "right" way to do it... Sometimes, the "how" is the natural way to describe a problem.

---

### Post by CptPicard on 2008-06-04
> **Bichromat said:**
> But it can be very hard to wrap your mind around these concepts. I'm trying to learn Haskell and I just don't see how I could do e.g. a physics simulation, because a loop over a certain number of time steps just seems the "right" way to do it...

True... well, pure-functional languages like Haskell are a bit strange in that sense. That's why I am a lisper and not a haskeller, lisp lets me have my mutable state when I must (although Clojure is trying hard to get rid of it).

I never understood how monads work, but I suppose one day I will... and usually when I have understood stuff like that, it really is a revelation that gives me ideas not only for that specific language, but other languages as well.

But, of course, I am not advocating functional programming for everything ;)

How you'd model that particular issue typically is btw an infinite list of states and associated "time-indexes". Then you just need to have some kind of state-transformation function that gets a state and returns a new state. Monads (somehow) encapsulate this sort of stuff. But yes, I have always felt like Haskell is too computer-sciencey to be really practicable for other scientists as a coding language.

---

### Post by pmasiar on 2008-06-06
> **dempl_dempl said:**
> My language is better than yours... bla bla bla 

I think that discussion about generators in Python nicely underscored the point we were trying to make: speed of execution is not the only measure to judge a language, and Python has  different ways to conquer complexity - which you, as a blub programmer, cannot see, and do not consider when judging the language. Which is your right of course.

To answer your question: No, Google does not run queries in Python, they are in C++, and some less time-critical are in Java. But majority of Google code is not to run queries, but to manage deployment of  hundreds of thousands of servers - and that is written in Python. As Alex Martelli (head of production/deployment and one of top Python gurus) said: "we program in Python if we can get away with it, in C++ if we must".

Python is not the best tool for every job under the sun - but neither is C++. But Python **is** best tool for about 80% of the jobs, that's why it is always my first choice. :-)

---

