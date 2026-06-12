---
title: "Python code smaller than c"
date: 2009-07-22
forum: Programming Talk
---

### Post by nipunreddevil on 2009-07-22
I just read somewhere that for the same purpose Python code is about  2 to 10 times smaller than the corresponding c code.
How true is that?
And if true,why still majority of programmers are c programmers?
Why Python and Perl have a small share in projects on sourceforge.net

---

### Post by Cyanidepoison on 2009-07-22
There are programmers who value speed of execution more than their time spent developing the software.

There are also many programs that just cannot be written in Python because they are interacting directly with hardware resources and the like.

To your last question, I have no answer.

---

### Post by Darkhack on 2009-07-23
Python code is likely shorter than C because of the additional language features.  But those who say 2-10x shorter are over embellishing things.

I should admit that I am a C programmer and my Python experience is limited, but of the Python code I've seen, it wasn't significantly shorter than what I could do in C.  In most cases it's about the same when you consider that a lot of Python programmers are using libraries that exist in C, like GTK+.

The key to getting code 2-10x shorter is APIs.  Usually when you see side by side comparisons of C and Python that embellishes Python, the person who wrote the test cases is ignoring many of the quality APIs that exist for C and is choosing to only use the standard library which will be 2-10x larger.  But that's to be expected.  No programmer would only use the C standard library in a real project.  To use that as a basis for comparison is misleading.

Python code is likely shorter because memory management, strings, bounds checking, hash tables, etc are built in, and C doesn't have the syntactical shortcuts for these features.  But APIs do exist for them, and I can't imagine a situation where the lack of expressive syntax bloats the code to 2-10x of the Python equivalent.

---

### Post by rkirk on 2009-07-23
> **nipunreddevil said:**
> Why Python and Perl have a small share in projects on sourceforge.net

Assuming this is true, it may be that the public's perception of Python and Perl is more as scripting languages rather than languages for "serious" application development which merits official or semi-official distribution. There's probably a lot of very informal projects and scripts floating around on the web that are written in these sorts of languages that aren't really available on repositories such as SourceForge. I may, of course, be wrong in my thinking, but that's how it seems to me, more or less.

---

### Post by CptPicard on 2009-07-23
Another thing that shortens Python code are things like list comprehensions and higher-order functions with closures, that then can lead to more concise API definitions. I also don't quite believe in these 10x improvements except very locally, but also, that kind of code size metric is misleading as to what is actually meaningful ... this was flamewarred a lot over a while ago. :)

---

### Post by nipunreddevil on 2009-07-23
So,
it means that python should be more in use,especially with the rapid pace of development wrt c/cpp.
Is it just that people refuse to leave their fave language c

---

### Post by Sockerdrickan on 2009-07-23
> **CptPicard said:**
> Another thing that shortens Python code are things like list comprehensions and higher-order functions with closures, that then can lead to more concise API definitions. I also don't quite believe in these 10x improvements except very locally, but also, that kind of code size metric is misleading as to what is actually meaningful ... this was flamewarred a lot over a while ago. :)
By script kiddies? :D

---

### Post by CptPicard on 2009-07-23
> **Tux0r said:**
> By script kiddies? :D

By C++ fanatics who do not seem to appreciate language design elegance much as long as fighting their tool makes them feel all manly and the end result is faster ;)

---

### Post by benj1 on 2009-07-23
python is smaller im not sure by how much

the question is how do you measure
C
```

char foo[11] = "hello world";
for (int i = 0; i < sizeof(foo); i++)
{
    printf("%d",foo[i]);
}

```

python
```
for i in "hello world"; print i
```
python is 1/5 the length of C going by lines, but then i could squash up the C example in to two lines, and if i declared the string as a variable i could stretch the python example to 3 lines. 
it also depends on what youre writing, if its low level stuff python loses its advantage but for higher level stuff python tends to be shorter

i think overall python code is more compact, although most of the difference is brackets, but i find it much quicker and easier to write code in python and its more readable afterwards, which i suppose is more important than size, but thats just me.

---

### Post by Sockerdrickan on 2009-07-23
> **CptPicard said:**
> By C++ fanatics who do not seem to appreciate language design elegance much as long as fighting their tool makes them feel all manly and the end result is faster ;)
Well Python speed is more like O(rows) ;) A good thing it doesn't need so many of them after all, although I agree 10x shorter is a bit of an overkill statement.

---

### Post by nipunreddevil on 2009-07-23
> **benj1 said:**
> 

i think overall python code is more compact, although most of the difference is brackets, but i find it much quicker and easier to write code in python and its more readable afterwards, which i suppose is more important than size, but thats just me.
That is what a programmer usually looks for.Especially if his code will be used by others

---

### Post by Sockerdrickan on 2009-07-23
> **benj1 said:**
> python is smaller im not sure by how much

the question is how do you measure
C
```

char foo[11] = "hello world";
for (int i = 0; i < sizeof(foo); i++)
{
    printf("%d",foo[i]);
}

```python
```
for i in "hello world"; print i
```python is 1/5 the length of C going by lines, but then i could squash up the C example in to two lines, and if i declared the string as a variable i could stretch the python example to 3 lines. 
it also depends on what youre writing, if its low level stuff python loses its advantage but for higher level stuff python tends to be shorter

i think overall python code is more compact, although most of the difference is brackets, but i find it much quicker and easier to write code in python and its more readable afterwards, which i suppose is more important than size, but thats just me.
C++0x
[php]for(char c: "hello world")
    std::cout<<c;
[/php]By the way you output your characters as integers was that on purpose or was it an example of how things can go when you don't C your C code? ;)

---

### Post by nipunreddevil on 2009-07-23
How can we make our application use the advantages of both.
like for low level work use c and for high level in python ..both languages in one application.

---

### Post by Sockerdrickan on 2009-07-23
> **nipunreddevil said:**
> How can we make our application use the advantages of both.
like for low level work use c and for high level in python ..both languages in one application.
You can have PYObjects or what they are called in C, or you can write functions in C and use them in Python (the other way around) :popcorn:

---

### Post by nipunreddevil on 2009-07-23
> **Tux0r said:**
> You can have PYObjects or what they are called in C, or you can write functions in C and use them in Python (the other way around) :popcorn:

How often is this approach used in software development especially GUI's .
There is a similar feature in Java called JNI ,have not heard anyone using it.

---

### Post by Sockerdrickan on 2009-07-23
> **nipunreddevil said:**
> How often is this approach used in software development especially GUI's .
There is a similar feature in Java called JNI ,have not heard anyone using it.
If you are going to write a GUI app I would recommend choosing one path, python ;) (depending on what GUI app of course, if it's a game level editor then you should blend both)

---

### Post by benj1 on 2009-07-23
> **Tux0r said:**
> C++0x
[php]for(char c: "hello world")
    std::cout<<c;
[/php]By the way you output your characters as integers was that on purpose or was it an example of how things can go when you don't C your C code? ;)

it was a test, you passed :)

it also handily illustrates that with python you tend to make less of the silly little mistakes

---

### Post by Sockerdrickan on 2009-07-23
> **benj1 said:**
> it also handily illustrates that with python you tend to make less of the silly little mistakes
Yeah well I prefer C++0x for loop in this particular case, because I get awesome speed as well :popcorn:

---

### Post by CptPicard on 2009-07-23
> **Tux0r said:**
> A good thing it doesn't need so many of them after all, although I agree 10x shorter is a bit of an overkill statement.

And even when it is 10x shorter we may approach the limit at unreadability... python does stress the ability to actually comprehend what was written, which means it's not geared towards one-liners.

In general I tend to feel that brevity and hopefully clarity are just side-effects of correctly chosen language primitives. What some for loop exactly looks like, for example, is somewhat beside the point. The interesting stuff in python are, IMO, the type system and object model plus the limited functional-programming support, and the fact that all of it has been put together rather orthogonally -- stuff fits logically together and there are no annoying rough spots or excessive exceptions to the rule of how things are done.

---

### Post by benj1 on 2009-07-23
> **CptPicard said:**
> 
In general I tend to feel that brevity and hopefully clarity are just side-effects of correctly chosen language primitives. What some for loop exactly looks like, for example, is somewhat beside the point. The interesting stuff in python are, IMO, the type system and object model plus the limited functional-programming support, and the fact that all of it has been put together rather orthogonally -- stuff fits logically together and there are no annoying rough spots or excessive exceptions to the rule of how things are done.

+1
(the for loops were meant to illustrate the difficulty in measuring code length though)

---

### Post by CptPicard on 2009-07-23
To continue on that idea from the perspective of the for loop... the meaningful idea right there is not syntactical, but the point that the for loop works right for any sequence-like object: iterables and generators. It's things like that that reduce the actual code size, not necessarily the length of the for-expression alone... the need not to explicitly declare the exact type system related to what the for will take, makes things even easier and shorter.

---

### Post by nipunreddevil on 2009-07-23
> **CptPicard said:**
> To continue on that idea from the perspective of the for loop... the meaningful idea right there is not syntactical, but the point that the for loop works right for any sequence-like object: iterables and generators. It's things like that that reduce the actual code size, not necessarily the length of the for-expression alone... the need not to explicitly declare the exact type system related to what the for will take, makes things even easier and shorter.
So it is similar to Matlab,although a lot quicker

---

### Post by mmix on 2009-07-23
After all, there is no os written in python, unununium os is between abandonware and deadware.

---

### Post by nipunreddevil on 2009-07-23
> **mmix said:**
> After all, there is no os written in python, unununium os is between abandonware and deadware.
So what is an OS written in.
it has to be c/c++.
Is Java not used and what about VB and .net .
Why is Python not used??

---

### Post by Darkhack on 2009-07-23
You could in write parts of an OS in interpreted languages.  Microsoft is doing just that with Singularity in C#.  You could do the same with Python, but in both cases, it wouldn't be pure.  You'd have to write a microkernel in C that includes an interpreter.  You may also have to modify the language to control lower level parts of the system.  Microsoft has something called Sing# which is an extended version of C# that allows for these low level capabilities needed in OS development.  Granted, you can't even write a OS entirely in C either.  Some assembly is needed.

---

### Post by Sockerdrickan on 2009-07-23
C++0x
[php]for(auto c: "hello world") 
    std::cout<<c;[/php]

no types here? ;)

---

### Post by CptPicard on 2009-07-23
> **Tux0r said:**
> 
no types here? ;)

It's still just a tag that tells the compiler to just "figure it out", right?

---

### Post by Sockerdrickan on 2009-07-23
> **CptPicard said:**
> It's still just a tag that tells the compiler to just "figure it out", right?
Indeed but I'm just the end-user I don't have to know about that ;) And it might interpret it as a const char* hehe :P

---

### Post by Reiger on 2009-07-23
Something not mentioned, or probably implied rather than explicitly mentioned is that Python gives you "for free" a lot of things you have to do manually in C/C++. This isn't obvious from any trivial example like the for loop, it only becomes apparent when you are doing more complex tasks like building a parse-tree out of some plain text file; manipulate the parse tree via GUI controls... possibly flushing it to a file.

However, for a trivial example of how certain language features can make code short:

```

primes [] = []
primes (x:xs) = x: (primes [y | y<-xs, y `mod` x /= 0 ])

```

Don't expect it to run very fast though.

---

### Post by JordyD on 2009-07-23
> **Tux0r said:**
> C++0x
[php]for(auto c: "hello world") 
    std::cout<<c;[/php]

no types here? ;)

I've never had issues with types. I don't really mind them, so I'l probably not be using this feature if it makes it to C++. In fact, I like declaring variables. I always hated doing this in python:
```
list = []
```
It just looks like useless static to me. I'd rather do this:
```
list alacabam
```
'list' being the type. or:
```
list alacabam = ['al', 'a', 'ca', 'bam']
```

---

### Post by CptPicard on 2009-07-23
> **JordyD said:**
> I've never had issues with types. I don't really mind them, so I'l probably not be using this feature if it makes it to C++.

Hmm... I hope you understand the question of static vs. dynamic typing and genericity really is of a deeper quality than whether someone "has issues" with types or not (it would like a rather n00bish excuse to use a dynamically-typed language...)

Try designing a really large type collection in a complex program in an object-obsessed language, and then try adding some exceptional objects to that... chances are it totally breaks the type design. The proliferation of "design patterns" in languages like Java seem like a symptom of this.

The good part in duck typing is that you can always assume something will behave in some given fashion if you're willing to use it in some fashion, without explicitly saying so elsewhere (the idea that static typing saves the programmer from himself seems to me to be overblown...)

> 
```
list = []
```
It just looks like useless static to me.

Would you suggest that

```

X = 0

```

Looks like that as well? There is a value literal, which contains the type information already...

---

### Post by Reiger on 2009-07-23
Altough to be fair if you have seen "cannot construct the infinite type [a]" in a Haskell compiler error message (or something similar to that effect) you haven't experienced the wonderful feature of certain static type systems that detect things like... infinite loops.

Mind you: that doesn't 100% certain prevent you from fouling up, but Strict Static Type systems can have meaning beyond a mechanism for mere compile-time earmarks.

---

### Post by Sockerdrickan on 2009-07-23
> **JordyD said:**
> I've never had issues with types. I don't really mind them, so I'l probably not be using this feature if it makes it to C++. In fact, I like declaring variables. I always hated doing this in python:
```
list = []
```It just looks like useless static to me. I'd rather do this:
```
list alacabam
```'list' being the type. or:
```
list alacabam = ['al', 'a', 'ca', 'bam']
```
I agree, but:
std::map<std::vector<std::string>,std::vector<std::vector<std::string>>::const_iterator i=bloat.begin();
vs
auto i{nice.begin()};

---

### Post by JordyD on 2009-07-23
> **CptPicard said:**
> Would you suggest that

```

X = 0

```

Looks like that as well? There is a value literal, which contains the type information already...

Honestly, I see no issue with that. It does explicitly say what kind of variable it is, simply by value. But my issue is more with how Python will let me do this:
```
X = 0
```
at any time. But not this:
```
X = X + 1
```

This makes sense because I never assigned a value to X. But I'd rather it required me to tell it what it was so that I could use it later on. I guess my issue is not with static declaration, but with default values. I would rather have the language assume that if I'm treating an undeclared variable as a integer, it's value is 0 by default. The next best thing is being able to say 'int X = 0' or 'X = 0' at the beginning of a function and have it assumed 0. But since lists look so ugly to declare 'alist = []', I'd rather be able to 'list alist'. It's really just aesthetics. Regardless, I don't think it a major issue. I still love Python overall.

---

### Post by monraaf on 2009-07-23
> **JordyD said:**
> But since lists look so ugly to declare 'alist = []', I'd rather be able to 'list alist'. It's really just aesthetics. Regardless, I don't think it a major issue. I still love Python overall.

You can also use.

```

alist = list()

```

---

### Post by NathanB on 2009-07-23
> **nipunreddevil said:**
> 
And if true,why still majority of programmers are c programmers?
Why Python and Perl have a small share in projects on sourceforge.net

A programmer never has the luxury of choosing what language to use.  The employer/client always sets this requirement based on the demands of the task.

Every year or two someone champions a new "fad language" to replace C, but, fortunately, the industry doesn't listen.  "If its not broke, don't fix it!" as the saying goes.  The C language will always be the most popular language because it is the easiest language for beginners to learn, it is the first (and often only) language ported to new architectures, it is available on all older platforms (important to big enterprise), and it doesn't require tons of money to re-train your staff.

---

### Post by nipunreddevil on 2009-07-23
> **NathanB said:**
> 
Every year or two someone champions a new "fad language" to replace C, but, fortunately, the industry doesn't listen.  "If its not broke, don't fix it!" as the saying goes.  
We can look at the positive impact of these so called fad languages,since they are easier for newbies especially scripting tools,it promotes more competition which is always good.

---

### Post by soltanis on 2009-07-23
> **NathanB said:**
> The C language will always be the most popular language because it is the easiest language for beginners to learn,

No, it really isn't.

---

### Post by Cyanidepoison on 2009-07-24
> **soltanis said:**
> No, it really isn't.
This is quite true.  In order to learn C, you need some pretty heavy understanding of some CS principles and knowledge of how a computer works.

While C is SIMPLE, it isn't EASY.

---

### Post by CptPicard on 2009-07-24
Hmmh... C is "simple", but it's not "efficiently pedagogical" especially when considering beginners.

I mean, the point is that it is a small language. Just control constructs, functions, and a handful of data types. In this sense, rather trivial.

However, a learner really needs in particular better error feedback than "segmentation fault", and built-ins in terms of "what sorts of things programs typically contain"...

I guess someone could claim that anything new that comes about is a "fad", but IMO it really represents the fact that we're trying to make languages "better" for the programmer. Progress. And besides, Lisp comes from 1958 and everything after that has been just a rehash of ideas contained within it or easily implementable on top of it... hardly a fad language ;)

---

### Post by nvteighen on 2009-07-24
> **NathanB said:**
> A programmer never has the luxury of choosing what language to use.  The employer/client always sets this requirement based on the demands of the task.

"Never x" means that in no situation x is true, right?

Ok, I have always chosen the languages I use... Of course, all are personal projects, but that doesn't make me less programmer than a hired professional ;)

> 
Every year or two someone champions a new "fad language" to replace C, but, fortunately, the industry doesn't listen. 

Hm... No, it's not that often, fortunately. And unfortunately, the industry sometimes happens to listen to the wrong ideas. Part of C++'s design is meant to replace C... and it did in some places (look at KDE, e.g.)... and it's a language with lots of issues. But then, Objective-C appears and nobody save the Mac OS X programmers use it and it's a really interesting language...

If you mean Python, Perl, Java, C#, Ruby, etc. are meant to replace C, you're wrong. Maybe some people think like that, but they surely don't know that high level languages are for high-level tasks and low level languages are for low-level tasks. Maybe in some contexts those languages may have replaced C in niches where C was used because of the lack of any better alternative. Nobody seriously enough could consider those languages intended to replace C.

But nobody is serious about those langauges that could replace C... Objective-C, D, Forth...

> 
"If its not broke, don't fix it!" as the saying goes.  The C language will always be the most popular language because it is the easiest language for beginners to learn, it is the first (and often only) language ported to new architectures, it is available on all older platforms (important to big enterprise), and it doesn't require tons of money to re-train your staff.

C is not the most popular language. Sadly, the most popular languages currently are C++ and Java (where it should be Lisp!). It's not the easiest language to begin with, as it makes you learn how to program along to how to deal with a lot of computer-specific stuff that's unrelated to programming. Programming is about modelling reality on a formal language... The computer just speaks binary, so it doesn't care what you write in which language; but we humans do care what language we're using because we are "symbolic beings" always heading for better expression of concepts.

> **Cyanidepoison said:**
> This is quite true.  In order to learn C, you need some pretty heavy understanding of some CS principles and knowledge of how a computer works.

While C is SIMPLE, it isn't EASY.

No. No CS principle is needed to learn C. CS is about algorithms and formal languages.

[QUOTE=Edsger W. Dijkstra]
Computer Science is no more about computers than astronomy is about telescopes.
[/QUOTE]

---

### Post by raf_kig on 2009-07-24
> **nvteighen said:**
> 
No. No CS principle is needed to learn C. CS is about algorithms and formal languages.
Algorithm and formal languages are only parts of CS. If you want to program C you'll have to have an understanding of a lot of basic concepts, execution model, os interfaces, memory management etc. Those are aspects of CS as well (not their implementation specific details ofc, but the concepts nevertheless).

---

### Post by Cyanidepoison on 2009-07-24
> **nvteighen said:**
> No. No CS principle is needed to learn C. CS is about algorithms and formal languages.

You're trolling.

---

### Post by unknownPoster on 2009-07-24
> **Cyanidepoison said:**
> You're trolling.

I disagree. For one, [nvteighen]("http://ubuntuforums.org/member.php?u=273037") is one of the most respected posters here. Secondly, tell me one Computer Science principle that is required to learn C. 

I'm pretty sure that you could teach a person how to program in C, just like you could teach someone how to bake a cake.

And obviously, you have no respect for one of the most well known Computer Scientists ever, Dijkstra.

---

### Post by CptPicard on 2009-07-24
Well, it just depends on how much weight you're willing to give the engineering side of understanding computation. I'm certainly more of an "abstract CS" purist in nvteighen's vein, but on the other hand certainly C exposes the inner working of the machine more, which is, in practical terms, important to understand for anyone in the field.

Now, whether I am actually willing to elevate that stuff to the level of "CS principle" is debatable... for me, CS principles always had more to do with things like the halting problem, NP-completeness, big-Oh analysis and such.

---

### Post by unknownPoster on 2009-07-24
> **CptPicard said:**
> 
Now, whether I am actually willing to elevate that stuff to the level of "CS principle" is debatable... for me, CS principles always had more to do with things like the halting problem, NP-completeness, big-Oh analysis and such.

I agree. Granted I'm only an undergraduate student, in my last Data Structures and Algorithms class, we rarely wrote code. Most of the work we did was "pen and paper." We were trying to actually understand the concepts instead of memorizing them in some particular language. 

I honestly enjoy the classes that are more theoretical than the "mindless coding" classes.

---

### Post by matthew.ball on 2009-07-25
There should be a distinction between Computer Science and Computer Engineering, though the two certainly over-lap at a point..

I find the Computer Science more engaging.

---

### Post by nipunreddevil on 2009-07-25
> **matthew.ball said:**
> There should be a distinction between Computer Science and Computer Engineering, though the two certainly over-lap at a point..

I find the Computer Science more engaging.
Even i have heard so
Could you highlight the differences

---

### Post by matthew.ball on 2009-07-25
Well, exactly as CptPicard and co have pointed out, Computer Science is more about the algorithms, the data structures and the core concepts, none of which is really confined to a limited domain; it's usually fairly mathematical (purely for the reason it is abstract and technically doesn't exist outside of theory!).

While engineering is the more physical aspect of things I guess, the differences between an x86 and a SPARc architecture or something. This is domain specific.

---

### Post by CptPicard on 2009-07-25
The funny thing about Computer Science is that it is essentially a very broadly applicable study of *problems* and their efficiently computable solutions. The study of what kind of a machine you exactly need to run those algorithms is peripheral -- all you need to do is to fundamentally prove that one can physically exist, and after that, you can just assume its existence... :)

I can't stress it enough that most of the interesting stuff in CS actually comes from understanding *problem structure* and having insight about ***_that_***, not about the computer. The computer is completely exchangeable underneath and can be abstracted as a very high-level symbolic computable description (programming language) if you please.

This means that after you've got your basic algorithmics education, you can move into pretty much any application domain and see what kind of solutions would fit. At that point, you can offload as much work as you can (the boring parts) to a computer so you can focus your own mind on the parts that require more human intervention. 

There are also really intriguing implications of computability theory to the workings of the so-called real world out there -- Stephen Wolfram has gone crazy about this. I have an interest in economics, for example, and algorithmic computability theory has interesting corollaries to that field -- namely, if you can prove that some game theoretic mechanism, say, some market or auction rule system or whatever, is not computable, then it is by definition also not realistic, as a group of actors *could never "compute" the result through their own action!*

I really didn't appreciate CS for what it was while I still was an undergrad, but the older I get, the happier I am that there is this higher understanding of things to be gleamed from it... it's not just about learning to write code ;)

EDIT: Mind you, this is not to diss Computer Engineering or Electrical Engineering, they are very tough and math-heavy majors. I suck royally at integrals compared to your typical EE guy. In addition, most Computer-Engineering types also need to be well versed in the CS computability theory side, and probably will not find it difficult to tackle it. There is, however, a very distinct *difference* between the fields. CS guys don't really need to care much about the machine underneath, as long as the Engineers provide the Analytical Engine with enough steam pressure...

---

