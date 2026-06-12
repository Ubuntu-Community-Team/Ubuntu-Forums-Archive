---
title: "C/C++ parser for a basic language"
date: 2011-12-04
forum: Programming Talk
---

### Post by rbaleksandar on 2011-12-04
Hi, guys.

  I'm doing a project for school - create a very basic compiler for a specified language using C/C++. The scanner-part is ready and fully funcional. It creates Tokens from a given source code. I use Eclipse with CDT.
  Now this might be obvious for the masters here, but hopefully you will give a suggestion how to solve the following problem:
  Let's say I have following files:
[b]a.cpp, a.h
b.cpp, b.h[/b]
  And now let's say I have the following code in them:
```

**a.h:**
#ifndef A_H_
#define A_H_

void fooA(void);

#endif /* A_H_ */

```

```

**a.cpp:**
#include "a.h"
#include "b.h"

void fooA(void){
   //Do something
   fooB();
}

```

```

**b.h:**
#ifndef B_H_
#define B_H_

void fooB(void);

#endif /* B_H_ */

```

```

**b.cpp:**
#include "b.h"
#include "a.h"

void fooB(void){
   //Do something
   fooA);
}

```

Now as you can see both sources call each other. In order to use a function defined in another source, I have to call the HEADER. That's how the world works. But obviously this results in a problem **fooA()/fooB was not declared in this scope** although I have all the headers packed in.
If I delete one of the includes (for example in b.cpp delete the #include "a.h"), I won't be able to use either fooA() or fooB() depending on the source file in which I call it because the compiler wouldn't now where to look for the declaration and body of the function.

Any ideas? This is quite essential, because the grammar, that represents the language (for which I make this compiler) is defined in such a way that there is some recursion here and there and I also have to jump back to the rule, which lead me to the sub-rule.
  A little bit explanation with an example (don't want to give the exact grammar of the language because than I won't learn anything by just copying; but if I have to, I can provide it):

We have a language L with the following grammar (S,A,B,C - non-terminals, q - terminal):
```

S ::= A B
A ::= C
B ::= B A | A
C ::= q

```

This is roughly represented by the following abstract code:
```

void S(void){
  A();
  B();
}

```
```

void A(void){
  C();
}

```
```

void B(void){
  B();
  A();
}

```
```

void C(void){
  nextToken();
  if(token == q){
    A();
  }
}

```
  I can put all that in one single file, but then it will be difficult if a college of mine wants to work on a single rule to add additional error-handling for example. So imagine that each method is in a separate CPP-file with the H-file that goes along. In the main-function we call only the S();
  
  I still have plenty to work on (for example the fact that everything is done sequentially from top to bottom -> every time I call foo(), I start from the beginning of the function :P) but for now this is what is really bothering me. Is it possible to use such function-calls without this annoying HEADER-problem? If you have any question, I'll gladly answer them.

Many, many thanks in advance,
RB

---

### Post by 11jmb on 2011-12-04
At the risk of being pedantic, you probably shouldn't open up a post with "I'm doing a project for school" because of the homework policy on this board. Because you are asking a general question about concepts, I'll gladly help, but I recommend keeping it to yourself that it is homework in the future.

In C, you should not have a problem writing mutually recursive functions in separate header files, it gets a little funny when you have circular class dependencies, though. This can be solved with a forward declaration.

Example here: [http://en.wikipedia.org/wiki/Circular_dependency](http://en.wikipedia.org/wiki/Circular_dependency)

Are you getting compiler errors? One thing that you need to be sure of here is that all of your header files are wrapped with preprocessor macros, which it looks like you did in your example.

---

### Post by rbaleksandar on 2011-12-04
Thanks for the reply. As for the school-thing: my question is pretty general so I might as well say that it's not a school-project. :P I think the school-thing applies to those threads where you can read something like "I have this and this. Can someone give me the answer with code?". :lolflag: I gave the abstract part and what I'm actually doing.

As for the errors - as mentioned I get "out of scope"-error, which is quite a surprise and I just can't explain it. :confused: I also have to use self-reference.

---

### Post by 11jmb on 2011-12-04
Are you getting the out of scope error when you include both header files as explained in your previous post?

I put together a quick project based on your code (fooA and fooB don't do anything other than print a number, decrement, and call each other) to show the mutual recursion at work, even if it is doing nothing useful.

Tell me if the simple code makes anything more clear.

---

### Post by rbaleksandar on 2011-12-04
Thanks. Will look at it. The out of scope is always in one of the two files.
If I remove the #include "b.h" in a.cpp, the out-of-scope-error disappears from b.cpp but appears in a.cpp when I call fooB().
If I remove the #include "a.h" in b.cpp, the out-of-scope-error disappears from a.cpp but appears in b.cpp when I call fooA().

That's weird, isn't it? :D As for the recursion - my methods don't have any parameters or return-values (part of the rules I guess). It's just jumping from one method in another or itself (depending on the rule I implement), taking tokens and again jumping here and there.

---

### Post by 11jmb on 2011-12-04
I just wanted to show a VERY simple example of how you can implement mutual recursion in C.

As for your out of scope error, I have never seen that before. You don't have any includes in your header files do you?

The only other culprit I can think of from the top of my head would be circular makefile dependencies. How are you compiling this project?

---

### Post by rbaleksandar on 2011-12-04
Not in these two. I have only one case of an include file that contains another include where I declare some global variables, that need other HEADER-files. I'll keep looking for a solution. Your project compiles without a problem. So obviously it's not something general and I've made some stupid mistake somewhere. Right now I have more than 40 header and source files and the number keeps growing. :D But at least it's easier to find your mistakes. Worst case scenario is that I'll have to reimplement the whole parser-part. That'll be fun...

I compile your project using gcc from the terminal or make. In Eclipse I compile it using the interface. I also have a make file, but it's only for the Scanner-part and I have to put some more code in order to compile the parser with it too. Still I doubt it's Eclipse's false in this case. But who know - maybe it is. :D

---

