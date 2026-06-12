---
title: "Starting a new project, what language should I use?"
date: 2009-01-16
forum: Programming Talk
---

### Post by lamalex on 2009-01-16
I'm debating between C#/Mono and python. What do you all think?

---

### Post by Kilon on 2009-01-16
> **Iamalex said:**
> I'm debating between C#/Mono and python. What do you all think?

Well .Net is not very liked around this place cause is considered a Microsoft product. But I say "nonsense"

.NET framework is by far the best framework out there, and by far the most useful product of Microsoft. I like it ! Mono project tried its best to port all this beautiful .NET code to other OSes . They are not there yet, some libraries are missing and I have heard several complains about the GUI ( especially in MACOS) , but I am sure there are easy ways to work around these problems. 

What I love about .NET C# , is that it takes out alot of complexity associated with C++ and implements a more clean process than java. But it does not dare to go as far as python. Mainly because it tries to keep a lot of its C++ heritage and look like its competitor JAVA.  

Python really implements what we call here at Greece "Spartan behaviour (lakonizein esti filosofein)" which basically  means "talking/doing less is wisdom" or as they tell here in the english speaking world "Less is more". It is a philosophy thousands years old applied in a modern language .   

In the end it is extremely difficult to say NO to a language that can do the sames thing in up to 5 times less code than the alternatives. The trade off is a slower execution, but with dual cores and quad cores it becomes almost impossible to experience slowness and for those CPU-Hungry tasks you can always implement part of the code that consumes the most in C++ and the rest that is regular programming stuff in tidy python syntax with no performance penalty. 

Of course personal taste always plays a major role. Afterall you cannot be highly productive in language that you don't like.

---

### Post by jimi_hendrix on 2009-01-16
im a C# fan and i dont like python so ill be biased...C#

---

### Post by slavik on 2009-01-16
the one that fits the problem you are trying to solve

---

### Post by Wybiral on 2009-01-16
It *might* help for you to explain the project some...

---

### Post by eye208 on 2009-01-16
> **Kilon said:**
> In the end it is extremely difficult to say NO to a language that can do the sames thing in up to 5 times less code than the alternatives.
The last time someone made that claim, it [didn't work out so well](http://ubuntuforums.org/showthread.php?p=6528556#post6528556) for him.

---

### Post by Kilon on 2009-01-17
> **eye208 said:**
> The last time someone made that claim, it [didn't work out so well](http://ubuntuforums.org/showthread.php?p=6528556#post6528556) for him.

Too bad they are not many like you to disagree with this claims. 

> Python allows us to tackle the complexity of programs like the WAS without getting bogged down in the language

[http://articles.techrepublic.com.com/5100-10878_11-1045764.html](http://articles.techrepublic.com.com/5100-10878_11-1045764.html)

> A couple of hours into the project, I noticed (allowing for pauses needed to look up new features in Programming Python) I was generating working code nearly as fast as I could type. ... This was my first clue that, in Python, I was actually dealing with an exceptionally good design. Most languages have so much friction and awkwardness built into their design that you learn most of their feature set long before your misstep rate drops anywhere near zero. Python was the first general-purpose language I'd ever used that reversed this process.

[http://www.computerworld.com.au/index.php/id;826423396;fp;2;fpid;568176992](http://www.computerworld.com.au/index.php/id;826423396;fp;2;fpid;568176992)

The simplicity of python is what sells it. Other than that there is nor real reason why someone should abandon his favorite language for python. But if you ask all the people that use python why they use it you will get the same answer. 

It is pretty thin to believe that you can get 1.000.000 python developers to lie at the same time.

---

### Post by eye208 on 2009-01-17
> **Kilon said:**
> It is pretty thin to believe that you can get 1.000.000 python developers to lie at the same time.
If one million Python developers claimed that there is a 5:1 SLOC ratio between C++ and Python, I would probably believe them.

But in fact I've seen only three fanboys making that claim. And each of them failed to prove it. ;)

---

### Post by ushimitsudoki on 2009-01-17
You don't give any details, so to deal in only general terms, here is my opinion:

Python. It has lots of advantages:
- Active development community
- Lots of good online references
- Lots of good books
- Good GUI bindings (PyQt)
- Elegant, well-designed language
- Good libraries to draw from
- Pure FLOSS - doesn't spread Microsoft mindshare

The only thing that threw me off when I first started learning python was that whitespace matters. This is pretty strange if you come from a C background. However, it began to make a lot of sense to me later, and now I actually prefer it for both readability and practicality.

The feeling you get when python concepts like list comprehensions begin to click is very exciting.

---

### Post by pp. on 2009-01-17
> **Kilon said:**
> It is pretty thin to believe that you can get 1.000.000 python developers to lie at the same time.

That's scarcely a useful argument. By that token, Windows would be vastly superior to all other OSs combined.

> **eye208 said:**
> If one million Python developers claimed that there is a 5:1 SLOC ratio between C++ and Python, I would probably believe them.

But in fact I've seen only three fanboys making that claim. And each of them failed to prove it. ;)

Calling people names does not answer the question. Comparing non-trivial software systems does. Take, for example, two applications covering General Ledger. Count the LOC for each. Divide. Tell.

---

### Post by nvteighen on 2009-01-17
It depends on the project... and this also implies that you should also think of other alternatives outside C# or Python. I mean: use the language that fits better to the task.

Of course, without any further details, we'll never be able to give you any helpful advice beyond this ;)

---

### Post by pp. on 2009-01-17
> **nvteighen said:**
> language that fits better to the task.

OTOH, you might want to consider a language you already know, unless you expect the project to become so large that thoroughly learning another language just to do that project becomes attractive.

Also, if you think other people might join the project now or at a later time, you'd consider a language you can expect a reasonable number of people to be proficient in.

---

### Post by eye208 on 2009-01-17
> **pp. said:**
> Calling people names does not answer the question. Comparing non-trivial software systems does. Take, for example, two applications covering General Ledger. Count the LOC for each. Divide. Tell.
I know how to count. Show me the code.

If the fanboys are telling the truth, why is it so hard for them to come up with, say, 20 lines of Python code that translates to 100 lines of C++? I mean, 5 to 1 is a pretty bold statement, don't you agree?

Convince me!

---

### Post by scourge on 2009-01-17
> **eye208 said:**
> If one million Python developers claimed that there is a 5:1 SLOC ratio between C++ and Python, I would probably believe them.

But in fact I've seen only three fanboys making that claim. And each of them failed to prove it. ;)

The 5:1 SLOC ratio could be true if we compare decent Python code with badly written or C-like C++ code. When I started to learn C++ my code was pretty much C with classes, and the SLOC count was huge compared to my Python code. Later I learned to use STL, Boost, Qt, better OOP, idioms like RAII, resulting in a lot less code.

---

### Post by ushimitsudoki on 2009-01-17
If you really care about SLOC as a measurement then why not look at [Project Euler]("http://projecteuler.net/") solutions? These are short, largely mathematical problems that participants solve using a language and technique of their choosing. 

For example, take problem #3, What is the largest prime factor of the number 317584931803 ? 

One C++ approach:
> int ProjectEuler::problemThree(double num) {
double limit = num/2;
for (int i = 0; i < limit; i++) {
if(isPrime(i)) {
while( !fmod(num,(double)i) ) {
num /= i;
}
}
if (num == 1) {
return i;
}
}
return -1;
}

bool isPrime(int num) {
if (num < 2) return 0;

for (int i = 2; i < num/2; i++) {
if (!(num&i)) {
return 0;
}
}
return 1;
}

One Python approach:
> d, n = 3, 317584931803
while (d * d < n):
if n % d == 0: n /= d
else: d += 2
print n 

I chose the problems and solutions at random. You can check for yourself and draw your own conclusions.

I don't think SLOC really matters as a comparison, and I'm not asserting a x:y ratio for any two languages - I think that is foolish.

I like Python because I'm more productive when I use it. This isn't me just talking out my butt (like most of my posts :) ). I have a pet project that I implement (or try to implement) every time I have to learn a new language. I've written it "from scratch" at least 6 times (perl, C++, VBA, C#, ruby, python). 

In python I was able to put out a [public release]("https://launchpad.net/scalculator") in about a week of coding (part-time) - that includes the "engine" and the GUI. I never got that sort of production out of any other language. That's just one person's experience of course; but at least I can say I have implemented the exact same project in multiple languages and have some actual reasons for holding the position I do concerning Python. It's not "fanboyism".

---

### Post by eye208 on 2009-01-17
> **ushimitsudoki said:**
> d, n = 3, 317584931803
while (d * d < n):
if n % d == 0: n /= d
else: d += 2
print n
This happens when I run your program:
```
./euler.py: line 1: d,: command not found
./euler.py: line 2: syntax error near unexpected token `:'
./euler.py: line 2: `while (d * d < n):'
```
Try again? ;)

---

### Post by ushimitsudoki on 2009-01-17
The spaces/tabs didn't come over. 

This is with spacing:
```
d, n = 3, 317584931803
while (d * d < n):
    if n % d == 0: n /= d
else: d += 2
print n
```

Also, to ward off future snark - I truly did grab the problems/solutions at random and assumed they were valid solutions. The above python doesn't qualify because Project Euler solutions are supposed to run in about one minute or less.

So, here is one I did **not** pick at random and actually tested:
```
x = 317584931803
i = 2
f = 1
 
while x > 1:
    if not x % i:
        x /= i
        f = i
    i += 1
 
print f
```

---

### Post by dwhitney67 on 2009-01-17
> **eye208 said:**
> This happens when I run your program:
```
./euler.py: line 1: d,: command not found
./euler.py: line 2: syntax error near unexpected token `:'
./euler.py: line 2: `while (d * d < n):'
```
Try again? ;)

+1.  Btw, that Python code translates into C++ as follows:
[php]
#include <iostream>

int main()
{
  unsigned long long d = 3, n = 317584931803LL;
  while (d * d < n)
    if (n % d == 0) n /= d;
    else d += 2;
  std::cout << n << std::endl;
  return 0;
}
[/php]

---

### Post by dwhitney67 on 2009-01-17
> **ushimitsudoki said:**
> ...

So, here is one I did **not** pick at random and actually tested:
```
x = 317584931803
i = 2
f = 1
 
while x > 1:
    if not x % i:
        x /= i
        f = i
    i += 1
 
print f
```

In C++:
[php]
#include <iostream>

int main()
{
  unsigned long long i = 2, f = 1, x = 317584931803LL;
  while (x > 1)
  {
    if (!(x % i))
    {
      x /= i;
      f = i;
    }
    ++i;
  }
  std::cout << f << std::endl;
  return 0;
}
[/php]

---

### Post by ushimitsudoki on 2009-01-17
Hooray. 

Anyway, I don't know why I got off on this C++ SLOC thing. I've never asserted there is some magical ratio, nor have I ever asserted that SLOC is an important measurement. 

C++ is a fine language. I use it and have no particular problem with it. Stroustrup himself was kind enough many years ago to answer an email I sent him on a point that I misunderstood in _The C++ Programming Language_ and not even make fun of my ignorance.

My **side** point was if **you** care about SLOC, then check Project Euler -- or something like it -- because it has a lot of solutions to the same problem in many languages from many people.

My **main** point is that in Python vs. C# - I prefer Python for the reasons I listed.

---

### Post by Kilon on 2009-01-17
> **eye208 said:**
> I know how to count. Show me the code.

If the fanboys are telling the truth, why is it so hard for them to come up with, say, 20 lines of Python code that translates to 100 lines of C++? I mean, 5 to 1 is a pretty bold statement, don't you agree?

Convince me!

Actually I did not claim that python produces **always **5 times less code.  I have seen some proof that python can produce 5 times less , but you will have to google it, cause I do not remember the link.  

My experience with jython helped me reduce my java code to 70%-50%.

But of course my Jython code does not use any python libraries , only JAVA . But even so , reduce to half is enormous advantage. Reducing a project that would take a year to mere 6 months , is extremely important to most people.    

And of course I do not include the time you save , using a language that it does not do its own memory management or force you to Object Orientation.  The proof is in front of your nose, open your eyes and see it. C++ is  dinosaur , walking slowly towards extinction. The days that was considered the De Facto language for most tasks are well over.   

C++ is still a highly useful language , its problem is that it is stuck in the past.

---

### Post by Zugzwang on 2009-01-17
> **Kilon said:**
> And of course I do not include the time you save , using a language that it does not do its own memory management or force you to Object Orientation.  The proof is in front of your nose, open your eyes and see it. C++ is  dinosaur , walking slowly towards extinction. The days that was considered the De Facto language for most tasks are well over.   


Uuuh, when doing language-wars, please be precise. C++ does *not* force you to do OOP, by no means! That's Java, but even there you can simply put all your functions statically into a class and do functional programming as before.

Also, when using C++ correctly, you don't *have* to do the memory management on your own. Just put everything into "auto_ptr"s and you are done (except for circular references but I've not seen a situation where there can occur so far).

Also, there are some situations in which you do not want to have this memory management stuff. A typical example are Binary decision diagram data structures (BDD) which normally use a cache with explicit reference counts. Consequently in C and Java you have to dereference them explicitly. Not so in C++, where the guaranteed destruction when going out-of-scope can be used. Here, C++ saves a lot of programming time.

Just my 2 Cents.

---

### Post by eye208 on 2009-01-17
> **ushimitsudoki said:**
> So, here is one I did **not** pick at random and actually tested:
```
x = 317584931803
i = 2
f = 1
 
while x > 1:
    if not x % i:
        x /= i
        f = i
    i += 1
 
print f
```
For the sake of completeness, here's the C version:
```
#include <stdio.h>

int main() {
    long long x = 317584931803, i = 2, f = 1;
    while (x > 1) {
        if (!(x % i)) x /= (f = i);
        i++;
    }
    printf("%lld\n", f);
}
```
;)

---

### Post by Kilon on 2009-01-17
> **Zugzwang said:**
> Uuuh, when doing language-wars, please be precise. C++ does *not* force you to do OOP, by no means! That's Java, but even there you can simply put all your functions statically into a class and do functional programming as before.

Also, when using C++ correctly, you don't *have* to do the memory management on your own. Just put everything into "auto_ptr"s and you are done (except for circular references but I've not seen a situation where there can occur so far).



In theory what you say is true , in practice is considered a very bad idea.

Also I do not do language wars. I love C++, and have no problem programming with it if I must.

---

### Post by MadMan2k on 2009-01-17
> **eye208 said:**
> The last time someone made that claim, it [didn't work out so well](http://ubuntuforums.org/showthread.php?p=6528556#post6528556) for him.
I wanted to show that OOP does not work out so well in C (not C++) and you gave me a C++ version, so well...

if you so desperately want a python example you cant beat:

assume you have an array of Nx6 with points in array[i][0..3] and you want to save the normalized version in array[i][3..6]

```

from numpy import *

a = ones((10, 6)) # generate some data

a[:,3:6] = [v/linalg.norm(v) for v in a[:,0:3]]

```

you might look up boost.math for this...

---

### Post by eye208 on 2009-01-17
> **MadMan2k said:**
> if you so desperately want a python example you cant beat:

assume you have an array of Nx6 with points in array[i][0..3] and you want to save the normalized version in array[i][3..6]
```
#include <boost/numeric/ublas/matrix.hpp>
#include <boost/numeric/ublas/matrix_proxy.hpp>
#include <boost/numeric/ublas/vector_proxy.hpp>
using namespace boost::numeric::ublas;

int main() {
    matrix<double> a(10, 6);
    vector<double> v(3);

    for (int i = 0; i < a.size1(); i++)
        matrix_vector_slice<matrix<double> >(a, slice(i, 0, 3), slice(3, 1, 3))
            = (v = subrange(row(a, i), 0, 3), v / norm_1(v));
}
```
:P

---

### Post by spupy on 2009-01-17
Judging by the way this thread is heading, I'd say OP trolled you guys pretty hard...

---

### Post by slavik on 2009-01-17
> **spupy said:**
> Judging by the way this thread is heading, I'd say OP trolled you guys pretty hard...
Agreed. Even though the discussion has been good, the OP hasn't come back. Either the OP has more to say or this thread has become a recurring discussion.

---

### Post by nvteighen on 2009-01-18
> **slavik said:**
> Agreed. Even though the discussion has been good, the OP hasn't come back. Either the OP has more to say or this thread has become a recurring discussion.
Close the thread, then? It seems reasonable.

---

### Post by spupy on 2009-01-18
> **nvteighen said:**
> Close the thread, then? It seems reasonable.

Don't we need a Recurring Discussions thread about programming languages? That seems reasonable to me. (Not this thread particularly though)

---

### Post by nvteighen on 2009-01-18
> **spupy said:**
> Don't we need a Recurring Discussions thread about programming languages? That seems reasonable to me. (Not this thread particularly though)
There's the Recurring Discussions section, but it's devoted to the whole of UF. I guess that due the special character the PT has, having our own Recurring Discussions section would be very handy...

---

### Post by MadMan2k on 2009-01-18
> **eye208 said:**
> ```
#include <boost/numeric/ublas/matrix.hpp>
#include <boost/numeric/ublas/matrix_proxy.hpp>
#include <boost/numeric/ublas/vector_proxy.hpp>
using namespace boost::numeric::ublas;

int main() {
    matrix<double> a(10, 6);
    vector<double> v(3);

    for (int i = 0; i < a.size1(); i++)
        matrix_vector_slice<matrix<double> >(a, slice(i, 0, 3), slice(3, 1, 3))
            = (v = subrange(row(a, i), 0, 3), v / norm_1(v));
}
```
:P
quite impressive - altough it took me quite some time to figure out what exactly you code does.

I think I will benchmark this, since I was always curious, whether pure numpy is as fast as C++ or not...

and please dont close the thread - yes it is off topic, but it does not hurt anyone...

---

### Post by module0000 on 2009-01-18
Definately go with Python.  No headaches to go cross-platform with your apps, giant community, and more functionality in less lines of code.

---

### Post by HotCupOfJava on 2009-01-18
I've noticed that pretty much any thread that starts with "what language should I use...." devolves into a language war. 

My opinion: depends on what you are trying to do. Different languages were created with different purposes in mind. Most posters will jump to the defense of whatever language they prefer using, though.

---

### Post by Wybiral on 2009-01-19
> **eye208 said:**
> If one million Python developers claimed that there is a 5:1 SLOC ratio between C++ and Python, I would probably believe them.

But in fact I've seen only three fanboys making that claim. And each of them failed to prove it. ;)

Well, one obvious blessing is in the dynamic typing. You can write a few small generic functions instead of writing a ton of type-specific functions.

This is where the OO programmer might step in and say "but, we have polymorphism for that", which is true, but it requires extra coding to set up an interface/base class whereas it's implicit in the dynamic language (all objects in Python, for instance, are instances of the base type "object" and I need not worry about it).

And of course, the generics/template/macro programmers might step in and throw a mess of compile-time code at me... To which I will vomit and leave. Having true runtime dynamicness really does make your code shorter and more expressive, but it's not going to be as obvious in small test cases like that, it will shine in any non-trivial application.

As an added note, just having dynamic types doesn't help much, but having a clean duck-type standard and introspection go a long way.

---

### Post by MadMan2k on 2009-01-19
> **MadMan2k said:**
> 
I think I will benchmark this, since I was always curious, whether pure numpy is as fast as C++ or not...
ok, just did the test with N=10000
Python: 0.27s
C++: 0.04s

so python is about 10x slower. Not quite fast, but not too bad either...

---

### Post by slavik on 2009-01-19
> **MadMan2k said:**
> ok, just did the test with N=10000
Python: 0.27s
C++: 0.04s

so python is about 10x slower. Not quite fast, but not too bad either...
I think you need a bigger test set. ;)

---

### Post by eye208 on 2009-01-19
> **Wybiral said:**
> Having true runtime dynamicness really does make your code shorter and more expressive, but it's not going to be as obvious in small test cases like that, it will shine in any non-trivial application.
I have worked on non-trivial applications for a decade, in teams of 20+ developers. When you do something like this, you learn to appreciate strong typing.

In strongly typed languages you can tell which data types a function will accept simply by looking at the function declaration. In Python this isn't possible. You have to look at the actual code instead. Imagine the following function:
```
def func1(data):
    (100 lines of code)
    data.func2()
    (another 100 lines of code)
```
If you pass an object to func1() that doesn't have a func2() method, the code will obviously throw an exception at runtime. And here's the problem: To find out that your object needs to have a func2() method to work with func1(), you'll have to look through the code of func1(). Now imagine that func1() looks like this:
```
def func1(data):
    (100 lines of code)
    func3(data)
    (another 100 lines of code)
```
Now it's not sufficient to look at func1(). You also have to look at func3()! What if both func1() and func3() have been written by someone else? What if they are poorly documented? What if you don't have the source but only a binary module/library?

When you work in a large team on a large project, you don't want to read each other's code. You don't even care about it. What you care about is the interface between your code and the other guy's code. If the other guy passes the wrong type of object to your function, you don't want to discuss who's at fault. You want these things rejected by the compiler, at compile time, before any damage is done.

---

### Post by Wybiral on 2009-01-19
> **eye208 said:**
> I have worked on non-trivial applications for a decade, in teams of 20+ developers. When you do something like this, you learn to appreciate strong typing.

In strongly typed languages you can tell which data types a function will accept simply by looking at the function declaration. In Python this isn't possible. You have to look at the actual code instead. Imagine the following function:
```
def func1(data):
    (100 lines of code)
    data.func2()
    (another 100 lines of code)
```
If you pass an object to func1() that doesn't have a func2() method, the code will obviously throw an exception at runtime. And here's the problem: To find out that your object needs to have a func2() method to work with func1(), you'll have to look through the code of func1(). Now imagine that func1() looks like this:
```
def func1(data):
    (100 lines of code)
    func3(data)
    (another 100 lines of code)
```
Now it's not sufficient to look at func1(). You also have to look at func3()! What if both func1() and func3() have been written by someone else? What if they are poorly documented? What if you don't have the source but only a binary module/library?

When you work in a large team on a large project, you don't want to read each other's code. You don't even care about it. What you care about is the interface between your code and the other guy's code. If the other guy passes the wrong type of object to your function, you don't want to discuss who's at fault. You want these things rejected by the compiler, at compile time, before any damage is done.

Firstly, you have static types mistaken for strong types. Python is a STRONG (albeit, dynamically) typed language.

And anyway, you're digressing from the point, which is that it requires less code (nice dodge though). I never said "it's more/equally suited for large development teams" I said that it typically requires less code to do similar tasks (and dynamic typing plays a part in this).

The key to not relying on compiler-generate errors/warnings, is properly testing the code before deployment. This has a similar functionality as the compiler throwing an error. Even with compiled languages, if you're not unit testing, you're doing something wrong.

But, in reality, introspection and established duck-type themes (Python's standard, and almost all third-party libraries, are very good about this) are the key here. In Python you can say "hasattr(obj, 'func2')" and find out if it's there. Perhaps you'd like to do something else with it at that point if it isn't.

Maybe I'm biased though, I haven't worked on many projects using undocumented, closed-source, scheme-ignoring code. To be honest, I don't really want to.

---

### Post by slavik on 2009-01-19
> **eye208 said:**
> I have worked on non-trivial applications for a decade, in teams of 20+ developers. When you do something like this, you learn to appreciate strong typing.

In strongly typed languages you can tell which data types a function will accept simply by looking at the function declaration. In Python this isn't possible. You have to look at the actual code instead. Imagine the following function:
```
def func1(data):
    (100 lines of code)
    data.func2()
    (another 100 lines of code)
```
If you pass an object to func1() that doesn't have a func2() method, the code will obviously throw an exception at runtime. And here's the problem: To find out that your object needs to have a func2() method to work with func1(), you'll have to look through the code of func1(). Now imagine that func1() looks like this:
```
def func1(data):
    (100 lines of code)
    func3(data)
    (another 100 lines of code)
```
Now it's not sufficient to look at func1(). You also have to look at func3()! What if both func1() and func3() have been written by someone else? What if they are poorly documented? What if you don't have the source but only a binary module/library?

When you work in a large team on a large project, you don't want to read each other's code. You don't even care about it. What you care about is the interface between your code and the other guy's code. If the other guy passes the wrong type of object to your function, you don't want to discuss who's at fault. You want these things rejected by the compiler, at compile time, before any damage is done.
AFAIK, Python will throw an exception saying that data does not have a member called func2, not only that, but it should tell you where this error was caught (in what function).

One nice case where static typing is definately useful is when you tell the compiler/interpreter that a certain variable will never be bigger than a certain size. Imagine a loop counter that is never bigger than an unsigned int (< 2^32), in this case, nobody has to watch the variable when it needs to be turned to a bignum. Python does bignum when needed, which means it has to check for a variable's value.

This is actually another thing that Perl6 is introducing, static typing when you want it. So you can declare a function to accept a variable of a specific type.

Here's an example of bignum when needed in Perl6 (Haskell and Python do the same afaik):
```

slavik@slavik-desktop:~$ perl6 -e 'my $a = 5; say $a.WHAT'
Int
slavik@slavik-desktop:~$ perl6 -e 'my $a = 5**65; say $a.WHAT'
Num
slavik@slavik-desktop:~$ perl6 -e 'my Int $a = 5; say $a.WHAT; $a = 5 ** 65;'
Int
Type mismatch in assignment.
... many errors caused by the mismatch

```

---

### Post by eye208 on 2009-01-20
> **Wybiral said:**
> Firstly, you have static types mistaken for strong types. Python is a STRONG (albeit, dynamically) typed language.
English is not my first language. But I think you got the point of what I said.

> And anyway, you're digressing from the point, which is that it requires less code (nice dodge though).
I'm still waiting for evidence that Python code is significantly shorter than C++ code. You guys keep talking about a 5:1 ratio, but you seem unable to prove it.

> I never said "it's more/equally suited for large development teams" I said that it typically requires less code to do similar tasks (and dynamic typing plays a part in this).
You were talking about "non-trivial" applications. A problem is non-trivial if it takes a large team to solve it.

> The key to not relying on compiler-generate errors/warnings, is properly testing the code before deployment. This has a similar functionality as the compiler throwing an error. Even with compiled languages, if you're not unit testing, you're doing something wrong.
You are obviously referring to Bruce Eckel's blog post. I have read it. However, Bruce doesn't answer the question how to avoid the requirement to read other people's code. He just says: Test more, and all will be fine. Frankly, I think he has no clue. I'd rather trust Linus Torvalds than him. And as you probably know, Linus even considers C++ too high-level.

The whole point of OOP is to get rid of the requirement that each developer in a large project team needs to look at the whole picture. OOP is about encapsulation. It's about making things invisible to others so they stop worrying about it. I want to test my own code, not someone else's. Static typing helps me narrow down the things my function has to test for. It shortens both my code and my testing cycles.

> In Python you can say "hasattr(obj, 'func2')" and find out if it's there.
How does this keep others from passing wrong data to my function?

---

### Post by Wybiral on 2009-01-20
> **eye208 said:**
> I'm still waiting for evidence that Python code is significantly shorter than C++ code. You guys keep talking about a 5:1 ratio, but you seem unable to prove it.
You say "you guys" as though we are one mind. I never said anything about a 5:1 ratio. But if you think idiomatic C++ or Java code for some non-trivial task is going to be less verbose than the equivalent in Perl/Ruby/Python/Lisp, you're kidding yourself.

> **eye208 said:**
> You were talking about "non-trivial" applications. A problem is non-trivial if it takes a large team to solve it.
I meant that those tiny snippets of code you claimed as proof that C/C++ are as compact/terse as Python are too trivial to matter. It only starts to show when area for generalization and refactoring is made. It should be intuitive to realize that generalizing and refactoring code is going to be easier in a dynamically typed language.

> **eye208 said:**
> You are obviously referring to Bruce Eckel's blog post. I have read it. However, Bruce doesn't answer the question how to avoid the requirement to read other people's code. He just says: Test more, and all will be fine. Frankly, I think he has no clue. I'd rather trust Linus Torvalds than him. And as you probably know, Linus even considers C++ too high-level.
I wasn't referring to Bruce, most large projects these days revolve around unit testing. I was saying that unit testing is a viable means of finding would-be bugs due to something like dynamic typing (just like a compiler would give you errors in a compiled language).

> **eye208 said:**
> The whole point of OOP is to get rid of the requirement that each developer in a large project team needs to look at the whole picture. OOP is about encapsulation. It's about making things invisible to others so they stop worrying about it. I want to test my own code, not someone else's. Static typing helps me narrow down the things my function has to test for. It shortens both my code and my testing cycles.
You can have OOP without static typing. What's important is that there's a defined interface. Yes... Most OO-capable HLLs support inheritance. You can still write out your base classes as a way of documenting the type's required methods.


> **eye208 said:**
> How does this keep others from passing wrong data to my function?
It doesn't but it lets you decide what to do at that point if that method doesn't exist. And, when you run your automated unit tests, the exception thrown from trying to access that attribute will report back to you what error occurred and where :) (very similar to how the compiler would whine about the types)

You aren't responsible for your end-users not properly testing their code. Even in C++ they could cast some pointer and make the compiler believe something that isn't true and blow the whole thing to smithereens... It's not your fault, just document your code the best you can and make your requirements clear.

---

### Post by CptPicard on 2009-01-20
Yay, I have missed these threads much... and now I miss pmasiar a lot too :(


> **eye208 said:**
> English is not my first language. But I think you got the point of what I said.

Those are technical definitions of typing disciplines, not intricacies of English. Look static/strong/weak/dynamic typing up on Wikipedia, it's all there ;)

> 
I'm still waiting for evidence that Python code is significantly shorter than C++ code. You guys keep talking about a 5:1 ratio, but you seem unable to prove it.

Just read some decent Python code and think about how you would go about doing it in C++. When you do not need to declare a lot of stuff, plus when you have some of the functional-style "declarativeness" (different from declaring types etc in advance), you save in code... but it's not the lines-sense saving that I most like, it's the certain cleanliness of what you're seeing that is even better.

Of course Python can't escape the fact that it's still an imperative language and also discourages extreme one-liners (which is good) so it's not quite as short as I guess it could be... but I really don't understand how someone could claim that Python and C++ would not have a significant difference.

> 
You were talking about "non-trivial" applications. A problem is non-trivial if it takes a large team to solve it.

Any problem takes a huge team to solve if you give them bad enough tools! Good tools and good people make a harder problems solvable with less people.


> Bruce doesn't answer the question how to avoid the requirement to read other people's code.

Wrong problem statement.

First, you define and document your interfaces well. Second, because the interfaces tend to be far more generic in HLLs, they are much smaller and have less constituent parts that are there only because of, say, requirements of the static type system (see below). So there is much less to actually understand in those other people's code as there is less crud mandated in the design by language. Third and last, if the code is syntactically not mostly "noise" and the language is orthogonal in design (easy to distinguish what does what in any given situation), other people's code is shorter and easier to read and understand to begin with, so reading it is less of a problem.

> 
I'd rather trust Linus Torvalds than him. And as you probably know, Linus even considers C++ too high-level.

Out of accomplished hackers, when it comes to general-purpose programming, I would trust anyone else except Linus any day. Linus is a kernel hacker and as such he has a kernel hacker's perspective which is by practical necessity twisted towards C. For everyone else, semantically the language constructs of C are trivially contained in higher-level languages or a large part of them are ignored completely, if the language is not imperative (think Haskell).

> 
The whole point of OOP is to get rid of the requirement that each developer in a large project team needs to look at the whole picture. OOP is about encapsulation. It's about making things invisible to others so they stop worrying about it. I want to test my own code, not someone else's. Static typing helps me narrow down the things my function has to test for.

IMO *static-typed* OOP does not quite work as the marketers and PHBs would like... it tends to just produce an explosion of types and all kinds of weird helper classes that have meaning only on the GoF sense. A really over-engineered static-typed OOP design has more static-typed OOP architecture in it than actual code that solves the actual problem -- the simple fact that there are so many "patterns" to get around problems it introduces is food for thought :)

The worst offenders in this "architectural explosion" are indeed encapsulation (need to expose again what was encapsulated so it can be used, in particular if design changes), and then the single dispatch model of a typical OOP language where for some really odd reason the function to be invoked on the data is selected only on the basis of the type of the first argument (there is always the implicit "this" argument to method calls that is used to resolve the virtual function at runtime).

Compare this to the Common Lisp object system model which is able to do pretty much anything in comparison -- inheritance hierarchies are on data only, functions are separate from data, and function calls are dispatched based on types of *all* arguments (and even runtime values), calls can be chained to form multimethods... CLOS is probably the most expressive way to do OOP I've seen so far, and I can't see how it would not work for a large team. And oh yeah, you can assert types in Lisp if you want to, but you don't have to. :)

Being able to question the OOP orthodoxy has really been the most liberating thing that has happened to me during my career so far... programming became fun again after I could ditch the UML and do things in a more natural, flexible way...

---

### Post by Kilon on 2009-01-20
> **wybiral said:**
> you say "you guys" as though we are one mind. I never said anything about a 5:1 ratio.

we are the python !!!!
Prepared to be assimilated!!!
You knowledge and culture will be added to our own!!!

Resistance is futile!!!

---

### Post by nvteighen on 2009-01-20
> **Kilon said:**
> we are the python !!!!
Prepared to be assimilated!!!
You knowledge and culture will be added to our own!!!

Resistance is futile!!!
That reminds me of someone exiled from here... :(

---

### Post by eye208 on 2009-01-20
> **CptPicard said:**
> Just read some decent Python code and think about how you would go about doing it in C++.
I did that several times right here in this forum. And I always came up with something equally short (and magnitudes faster) in C/C++. And then the next fanboy comes along, completely ignores all the previous discussion and makes the same claims about "shorter code" again. Rinse, repeat.

Now you're telling me something like "Linus can't be trusted because he's a *kernel hacker*". Well, in my world it makes no difference whether you hack the Linux kernel, the Mozilla kernel or the OpenOffice kernel. We all have the same goal: to move data from A to B as efficiently as possible. Because at the end of the day, when you use a word processor to write your thesis about obscure high level languages, you want a word processor that doesn't suck. And when you post in this forum, you want a web browser that doesn't suck. And when you edit movies or render a 3D model, you want tools that don't suck. And these tools are written in C/C++. All of them.

> Any problem takes a huge team to solve if you give them bad enough tools! Good tools and good people make a harder problems solvable with less people.
My suggestion is: Start solving these problems, instead of talking about them. Then show me your solution. At least then we have *something* to talk about.

---

### Post by scourge on 2009-01-20
> **CptPicard said:**
> Out of accomplished hackers, when it comes to general-purpose programming, I would trust anyone else except Linus any day. Linus is a kernel hacker and as such he has a kernel hacker's perspective which is by practical necessity twisted towards C.

I don't think Linus has anything against high level languages in general, or else he wouldn't have written parts of Git with shell scripts. He seems to be more against OOP, and has actually said that even Visual Basic was a more important innovation than OOP.

---

### Post by directhex on 2009-01-20
How about both - IronPython :p

---

### Post by Kilon on 2009-01-20
> **eye208 said:**
> I did that several times right here in this forum. And I always came up with something equally short (and magnitudes faster) in C/C++. And then the next fanboy comes along, completely ignores all the previous discussion and makes the same claims about "shorter code" again. Rinse, repeat. 

You must have a very abstract definition in your vocabulary of the word "shorter".
 
> 
 We all have the same goal: to move data from A to B as efficiently as possible. Because at the end of the day, when you use a word processor to write your thesis about obscure high level languages, you want a word processor that doesn't suck. And when you post in this forum, you want a web browser that doesn't suck. And when you edit movies or render a 3D model, you want tools that don't suck. And these tools are written in C/C++. All of them.


You understand that most software sucks ? Of course it may not suck to some people like you with very low demands like "i use my super popular language" "look mom I can do this faster than superman" . 

I see a pattern to most C++ programms, they seem to ignore the term "ease of use". Any time I come in front of a software review there no mention of "Speed" or "intelligent software architecture" actually most time is spend on GUI and the ease of use. And C++ software suck at this. And the reason it sucks is because there so many problemes to solve inside a c/C++ programm that GUI and ease of use are always forced in the of end of the list of priorities.   

> My suggestion is: Start solving these problems, instead of talking about them. Then show me your solution. At least then we have *something* to talk about.


My suggestion is choose the right tools especially when you make a big software involving many people and probably will span to many releases and versions. 

One of the big problems of software today , the "serious" software as you call it is that is a Dinosaur. Big, slow and can create quite mess. By slow I mean not the actually speed but the speed of improvement. Companies keep producing updates but those updates are mere bug fixes which should not even been there in the first place and a limited amount of features. Once a while  really revolutionary software comes along and it is like a huge party. This is the problem with todays software and languages like C/C++ are part of that problem. 

An intelligent programmer should ask himself what are the right tools for the job. If he uses C++ all the time , python all the time or just a single tool and single approach then I do not consider him as an intelligent programmer.

---

### Post by wmcbrine on 2009-01-20
> **eye208 said:**
> ```
#include <boost/numeric/ublas/matrix.hpp>
#include <boost/numeric/ublas/matrix_proxy.hpp>
#include <boost/numeric/ublas/vector_proxy.hpp>
using namespace boost::numeric::ublas;

int main() {
    matrix<double> a(10, 6);
    vector<double> v(3);

    for (int i = 0; i < a.size1(); i++)
        matrix_vector_slice<matrix<double> >(a, slice(i, 0, 3), slice(3, 1, 3))
            = (v = subrange(row(a, i), 0, 3), v / norm_1(v));
}
```
:P

This is *hideous* compared to the Python version. I wasn't going to bring that up, but then you had to say "And I always came up with something equally short (and magnitudes faster) in C/C++." No. Wrong. Fail.

---

### Post by eye208 on 2009-01-20
> **wmcbrine said:**
> This is *hideous* compared to the Python version.
I consider encoding programs in punctuation and whitespace (!) to be more hideous. I guess it's a matter of taste. You either have it or you don't. ;)

> I wasn't going to bring that up, but then you had to say "And I always came up with something equally short (and magnitudes faster) in C/C++." No. Wrong. Fail.
It's one statement. And it executes several times faster than the Python one. Mission accomplished. Who cares if you like it? You're not important.

---

### Post by Kilon on 2009-01-20
> **eye208 said:**
> I consider encoding programs in punctuation and whitespace (!) to be more hideous. I guess it's a matter of taste. You either have it or you don't. ;)

No you don't. You just are addicted to disagreeing. I bet 1.000.000 $ that you use python most of the time and then say it is C++. You fool none . 

> It's one statement. And it executes several times faster than the Python one. Mission accomplished. Who cares if you like it? You're not important.


You can do it with Delphi . Same executed speed , much less code, far more readable. Pretty much the same as python but with no speed loss. No reason to use C++.

---

### Post by eye208 on 2009-01-20
> **Kilon said:**
> You can do it with Delphi . Same executed speed , much less code, far more readable. Pretty much the same as python but with no speed loss.
Show me the code.

---

### Post by Kilon on 2009-01-20
> **eye208 said:**
> Show me the code.

Why ?

Should I show you where the sun rises and where the sun sets as well ? Learn to program and then make claims. You have a very distorted view of how things work, which is based on your ignorance and lack of will to learn.

---

### Post by ajackson on 2009-01-20
I really don't understand why these language wars keep rehashing all the old stuff over and over again. Most languages come about because there is a need, if there wasn't the language would quickly die as no one would use it.

Some languages are better suited to different tasks, for example for rapid development of a GUI based app high level languages are a good bet, while languages like C can be used only the better C programmers could match the speed of development that the higher level languages give. With stuff requiring a greater element of control (kernels, drivers, etc), lower level languages really come to the front because of the power and control they give.

On the whole "fan boy" nonsense, can we leave name calling to the kids in the playground, remember eye208 by your own definition (ie a fan boy is someone who proclaims language *X* is the best using blinkered vision to all arguments), you also are a fan boy, just of C rather than Python. But also to the fans (note not fan boys) of Python, Python isn't the answer to everything, I don't think any language truly is.

---

### Post by Kilon on 2009-01-20
> **ajackson said:**
> Python isn't the answer to everything, I don't think any language truly is.

no it is not and probably will never be. But real fanatics do not think like this , they think  that their tools are the best all the time. But it is not thinking actually only pure reactive emotion.

---

### Post by wmcbrine on 2009-01-20
> **eye208 said:**
> I consider encoding programs in punctuation and whitespace (!) to be more hideous.Generally (albeit not in this case) there's a lot less punctuation in a Python program, so that's a point for Python rather than against it. As for indentation, it's the same indentation you'd use anyway in a C-like language, 99.99% of the time.

> *It's one statement. And it executes several times faster than the Python one. Mission accomplished.*It's 13 lines, 430 characters vs. 3 lines, 109 characters. It's not shorter, it's not as short, it's not nearly as short. Mission failed.

---

### Post by Kilon on 2009-01-20
> **wmcbrine said:**
> 
It's 13 lines, 430 characters vs. 3 lines, 109 characters. It's not shorter, it's not as short, it's not nearly as short. Mission failed.

maybe it is shorter in the "look mom I can use C/C++, I am hacker!" kind of way. :D


Also i have to say initially i did not found whitespace any strange , afterall i use whitespace from my old C++ dos days . However I did found the lack of "{" "}" abit annoying . Even when I was programming for many years with delphi , i found it annoying . 

But I saw early in the process that most IDES and editors that respect their selves show the scope in one way on the other (can fold the scope, etc etc) so "{" "}" symbols are really not that necessary. 

It is one of the things people think that they matter to them but in practice it does not.

---

### Post by eye208 on 2009-01-20
> **wmcbrine said:**
> It's 13 lines, 430 characters vs. 3 lines, 109 characters. It's not shorter, it's not as short, it's not nearly as short. Mission failed.
LOL

You're counting #includes, function headers etc. as executable code. And you're counting function/class name lengths. That's nonsense of course. If matrix_vector_slice was named "mvs", you would complain about code obfuscation.

The actual code is one for() statement, up to the terminating semicolon. And it runs circles around Python. I could have written an even faster version in C using pointers on an array of doubles, but then you would complain even more.

---

### Post by ajackson on 2009-01-20
> **eye208 said:**
> And you're counting function/class name lengths. That's nonsense of course. If matrix_vector_slice was named "mvs", you would complain about code obfuscation.
I agree, meaningful names are an indication of good programming practice.

---

### Post by Kilon on 2009-01-20
> **eye208 said:**
> LOL

You're counting #includes, function headers etc. as executable code. And you're counting function/class name lengths. That's nonsense of course. If matrix_vector_slice was named "mvs", you would complain about code obfuscation.

The actual code is one for() statement, up to the terminating semicolon. And it runs circles around Python. I could have written an even faster version in C using pointers on an array of doubles, but then you would complain even more.


Ahhh he is referring to "EXECUTABLE CODE" of course.... DOH!!! because the rest of the code is written by itself . WOW pure C++ magic!!!!

---

### Post by Wybiral on 2009-01-20
> **eye208 said:**
> And when you post in this forum, you want a web browser that doesn't suck.

And when your post hits the forum, you want the server-side code not to suck, which was written in PHP. I don't see your point here, bud. I think we're all aware that LL has its place in the world (especially for things like kernels).

But, you make strange arguments to defend your claims... CptPicard was saying that kernel hackers are likely to take the LL side because that's where they're minds are invested, so you defend by saying "we need kernels"? Yes... But that doesn't make kernel hacking design strategies useful in areas other than kernel hacking.

And once again, I'm telling you, you being able to rewrite a few lines of Python code semi-compactly in C/C++ does not prove anything. There's no room for generalizing and reducing redundant patterns in such a small example. This can only really be proved by experience...

---

### Post by wmcbrine on 2009-01-20
> **eye208 said:**
> You're counting #includes, function headers etc.Of course I am. That's the whole point -- all the crap you have to type in C++, that Python strips away.

---

### Post by eye208 on 2009-01-20
> **Kilon said:**
> Why ?
Because it would establish credibility. You can talk the talk, but can you walk the walk? I don't think so. :p

---

### Post by Kilon on 2009-01-20
> **eye208 said:**
> Because it would establish credibility. You can talk the talk, but can you walk the walk? I don't think so. :p

why would i need to establish credibility to something that is so obvious ?

---

### Post by eye208 on 2009-01-20
> **Kilon said:**
> why would i need to establish credibility to something that is so obvious ?
Why would anyone listen to your advice regarding programming languages if you can't even write a one-liner in Delphi? ;)

---

### Post by Kilon on 2009-01-20
> **eye208 said:**
> Why would anyone listen to your advice regarding programming languages if you can't even write a one-liner in Delphi? ;)
 who said i cant't ?

---

### Post by Rocket2DMn on 2009-01-20
Once again another PT thread degrading into bashing and mudslinging.  Smiley faces do not make it ok.  Thread closed.

---

