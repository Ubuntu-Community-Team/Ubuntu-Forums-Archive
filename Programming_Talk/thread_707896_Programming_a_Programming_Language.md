---
title: "Programming a Programming Language"
date: 2008-02-25
forum: Programming Talk
---

### Post by coolkid5 on 2008-02-25
How would one go about creating a programming language.  I'm trying to make a simple one to learn more about computers and computer languages.  
I know that flex and bison are available for making compilers.  What exactly are they?
Am I right that C is turned into assembler which is turned into machine code, where as a language like java is turned into a special bytecode for the jvm?  What are the advantages to these two different methods?

Thank you in advance!

---

### Post by Wybiral on 2008-02-25
Do you know a lot about assembly language or virtual machine design? If not, you'll probably want to start there. For a simple start, try writing a program that will parse an infix-notation expression and output the assembly code to evaluate it (you could also write a simple virtual machine to evaluate it).

---

### Post by CptPicard on 2008-02-25
> **coolkid5 said:**
> How would one go about creating a programming language.

1. Specify the grammar
2. Create parser for the grammar
3. Use parser to parse source into an internal representation, a syntax tree
4. If you want a compiled language, walk the tree and output assembly, if you want an interpreted language, walk the tree and evaluate the expressions as you go.

> I'm trying to make a simple one to learn more about computers and computer languages.

Probably not a good idea for a learning project, but good luck :)

> I know that flex and bison are available for making compilers.  What exactly are they?

Flex is a lexical analyzer, bison is a parser generator. Flex reads the source and recognizes the really simple structures and produces tokens out of them. Tokens are the low-level building blocks of your source, like in typical C we might have tokens "if" "(" "x" "<=" "1" ")" "{" ...

Bison is a parser generator. It takes the tokens produced by flex and does the higher-level analysis and generation of the code you need to actually do something to the recognized structures of your language.

> Am I right that C is turned into assembler which is turned into machine code, where as a language like java is turned into a special bytecode for the jvm?

Yes, you are.

> 
  What are the advantages to these two different methods?


The assembly you get from C is turned into CPU-specific machine code. Running this is obviously very efficient. The reason to use bytecode is usually crossplatform compatibility -- you run a virtual machine, versions of which can be compiled for all sorts of platforms in the aforementioned way, and then *that* reads your bytecode which can be the same for all platforms. The efficiency implications are that you're running on top of a kind of emulation layer, which of course is slower. There are nice things like just-in-time compilation that compiles bytecode into native code just before running, and that ameliorates this performance problem.

---

### Post by coolkid5 on 2008-02-25
Thanks, I guess I'll try and do that first.  I've been learning nasm assembler so I'm good there, but I'm still not exactly clear on flex and bison.  They are tools to help me make an infix notation parser... do they also deal with outputting assembler?

---

### Post by kaens on 2008-02-25
This is a very complicated topic. 

[This book]("http://http://www.cs.brown.edu/~sk/Publications/Books/ProgLangs/2007-04-26/") could be very useful if you really want to delve into making programming languages.

Bison is used to take a set of rules and make parsers, flex is used to make lexical analyzers.

The advantage of using something like java's bytecode is that it (arguably) makes it easier to write cross-platform applications.

There are also interpreted languages, like python, perl, and ruby which get run through an interpreter instead of compiled. The book linked above focuses on scheme, which is an interpreted language.

[This book]("http://www.cs.indiana.edu/eopl/") is also very good, but I am not aware of a free version available.

Implementing a language is not easy work, by the way.

---

### Post by CptPicard on 2008-02-25
I have to disagree with Wyb here and advice you to create an interpreter and not bother with the assembler. Your first task here is to just get something running, and to get your grammar parsed etc... just read in your source and evaluate it in your interpreter, instead of outputting anything compiled.

---

### Post by LaRoza on 2008-02-25
> **kaens said:**
> 
There are also interpreted languages, like python, perl, and ruby which get run through an interpreter instead of compiled. The book linked above focuses on scheme, which is an interpreted language.


Python and Perl are compiled to byte code before execution. And both can be compiled to byte code which will run on any platform with the interpreter.

---

### Post by CptPicard on 2008-02-25
Scheme actually even has a native-code compiler... [http://www-sop.inria.fr/mimosa/fp/Bigloo/](http://www-sop.inria.fr/mimosa/fp/Bigloo/)

They "discourage" the use of call/cc though which to me seems like means "we have bad support for it"... :p

---

### Post by kaens on 2008-02-25
> Python and Perl are compiled to byte code before execution. And both can be compiled to byte code which will run on any platform with the interpreter.

True. I was using them as an example, as the compilation is not (normally) done by you.

---

### Post by LaRoza on 2008-02-25
> **kaens said:**
> True. I was using them as an example, as the compilation is not (normally) done by you.

On that note, I advise the OP to look at tcc. [http://en.wikipedia.org/wiki/Tcc](http://en.wikipedia.org/wiki/Tcc)

Perhaps its source might be enlightening.

---

### Post by coolkid5 on 2008-02-25
So, if I were to make an interpreter do just use a language like C or Java, or are Bison and Flex used for interpreters as well?

---

### Post by pmasiar on 2008-02-25
You did not mentioned your experience level.... But from the questions you asked, it is IMHO not at the level where someone can think about designing a language. You need to be comfortable it at least half a dozen languages of different kinds to be ready to design one. Including different non-C non-Python languages, like Lisp, Forth, Erlang, Haskel.

That said, the simplest way to define a (simple) language is Forth, IMHO. It is very easy to develop a language specialized in solving some specific class of problems, and you will see all levels from HLL down to ASM, what exactly is going on. Warning: it is not for easy to get scared people! Lisp might be another way.

---

### Post by Acapulco on 2008-02-26
Wow. First of all, it's good that you have that kind of drive. :)

Second, I would really think that before getting into any actual *program* be it Flex, Bison or whatever, I think you should first get some knowledge on formal languages.

I got to develop my own "programming language" in college, in my compilers class, and let me tell you it's not an easy task (although a very rewarding one).

Like CptPicard posted here, you first need to understand what a formal grammar is, in math terms.

Then you have to practice (with good ol' pen and paper) building grammars for different "languages". 

For example, try to build a grammar that will accept any string of "1" and "0" that's a pallindrome (i.e. 10011001), and keep going with harder excercises.

When you have this step "mastered", then you have to design the state-machine to parse it.

What that means is, you basically have a matrix, where the first row is a list of all the recognized symbols, and each subsequent row is a particular state. 

So you basically say that when you are at location (X,Y) of your array, the value Y is the one you are "reading" right now, and you are at state X, so the location (X,Y) in the array will let you know what's the next state.

Example:

    A B C D
0  1 3 0 2
1  1 3 2 1
2  3 0 0 1
3  - - - -

Means that, you start at state 0 always, and when the state-machine is in that state, and you read an "A" you go to state 1.
If you read a "B" you go to state 3, etc.

The point is, to see if a particular string of symbols gets the state-machine into the "final state", which means that the process ended successfully, and then you say that string if part of the grammar, or part of the language you are designing. 

So, say state 3 is your final one in the above example, then an "accepted string" would be "AB". You start at state 0, and read the "A", then you go to state 1. Then you read the "B", and go to state 3 and you are finished, meaning that "AB" is a valid TOKEN.

So, once you have this done, you have a list of valid tokens, and then you can proceed accordingly, because now you know that the first "instruction" is "AB" (whatever that means in your language).

As you can see, it's no easy task. Designing a grammar just to accept some particular "1" and "0" strings is not easy, let alone a full-blown working language.

So, my advice: Go learn some formal languages, some grammar design, etc. Then you can think of building a proper language. Although I would think that needs at *least* four months of a college course to *understand* how a compiler works.

Then some more time to master it.

I hope that helped a bit, and if you need further help, I can provide my final semester project, so you can see the innerworkings of a very simple "language".

The beauty of using an array to determine your state-machine is that you just need to build a program that "follows" the array like the above example, and so you can build lots of different "arrays" (actually, state-machines) and only ONE "state-machine" reader.

It won't be the fastes compiler around (ehem :] ) but it will work.

Then you can have some fun writing state-machines for different purposes. 

Like I said, start by doing some basic grammars.

1.- A state machine that accepts only "1"'s and no zeros.
2.- A SM that accepts 3 "1"'s and a "0" at the end (and nothing else)
3.- SM that accepts the string "100101010111110" but no other.

Etc.

(Sorry for the long and confusing post, but this is no easy subject)

---

### Post by lnostdal on 2008-02-26
doing this in lisp is very easy btw.

you transform the code (text/string) into lisp forms .. then pass that to `compile' which generates machine language from the intermediate lisp code

here's a very silly example:

```

(defun my-compiler (program-code)
  "my-language --> lisp --> machine language"
  (with-input-from-string (ss program-code)
    (let ((lisp-code))
      (let ((a1 (read ss))
            (op (read ss))
            (a2 (read ss)))
        (push (list op a1 a2) lisp-code))
      (compile nil `(lambda () ,@lisp-code)))))


CL-USER> (funcall (my-compiler "4 + 2"))
6
CL-USER> (funcall (my-compiler "4 - 2"))
2
CL-USER> (funcall (my-compiler "4 * 2"))
8
CL-USER> (funcall (my-compiler "4 / 2"))
2
CL-USER> (defun ^ (a b)
           (expt a b))
^
CL-USER> (funcall (my-compiler "4 ^ 2"))
16

```


..but generally, in lisp, i instead create new languages with new constructs directly using "lisp syntax" ..   say, for instance - i miss the `for' construct in lisp .. then i just add it directly into lisp, like this:

```

(defmacro for ((var initial-value pred &optional update-value) &body body)
  (if update-value
      `(do ((,var ,initial-value ,update-value)) ((not ,pred))
        ,@body)
      `(do ((,var, initial-value)) ((not ,pred))
         ,@body)))

CL-USER> (for (i 0 (< i 10) (+ i 1))
           (format t "`i' is: ~A~%" i))
`i' is: 0
`i' is: 1
`i' is: 2
`i' is: 3
`i' is: 4
`i' is: 5
`i' is: 6
`i' is: 7
`i' is: 8
`i' is: 9
NIL

```

.. and i have in a way created a new programming language by extending lisp .. lisp is a programmable programming language

---

### Post by Acapulco on 2008-02-26
> **lnostdal said:**
> 
..but generally, in lisp, i instead create new languages with new constructs directly using "lisp syntax" ..   say, for instance - i miss the `for' construct in lisp .. then i just add it directly into lisp, like this:

```

(defmacro for ((var initial-value pred &optional update-value) &body body)
  (if update-value
      `(do ((,var ,initial-value ,update-value)) ((not ,pred))
        ,@body)
      `(do ((,var, initial-value)) ((not ,pred))
         ,@body)))

CL-USER> (for (i 0 (< i 10) (+ i 1))
           (format t "`i' is: ~A~%" i))
`i' is: 0
`i' is: 1
`i' is: 2
`i' is: 3
`i' is: 4
`i' is: 5
`i' is: 6
`i' is: 7
`i' is: 8
`i' is: 9
NIL

```

.. and i have in a way created a new programming language by extending lisp .. lisp is a programmable programming language

The problem I see with that is when you receive a "faulty" for construct. You might have everything else working, but say you do

CL-USER> (for (i 0 (i < 10) (++ i 1)

Then you get an error but won't know what happened, and in a way, you won't be creating a new language, just defining a lisp function for every function of "MyLanguage".

If you go the long and hard way, you get to know exactly where the error was, why was it an error, etc. I.e. a full fledged compiler

BTW, @OP: I forgot to say that you need 3 things to get a compiler:

1.- Lexical analyzer: Checks whether the symbols you are trying to "compile" actually exist in the grammar. (That's the state machine i talked about in my prev. post). It outputs tokens to the next step.

2.- Sintactic analyzer: Checks whether (sp?) the tokens received are correctly forming an instruction. I.e. the symbols might be correct,  but in bad shape (e.g. "( ( ) " - there's one missing ")" )

3.- Semantic analyzer: Checks whether (sp?) the "commands" received from step 2, actually make sense.

"for (i=1; a<0; var++)" for example. All symbols exist, they are in "good shape" but  it doesn't make any sense to start a for loop with i=1, and continue the loop until "a<0"...you get the idea.

I don't have to tell you that the last step is the hardest one :)

---

### Post by lnostdal on 2008-02-26
> **Acapulco said:**
> The problem I see with that is when you receive a "faulty" for construct. You might have everything else working, but say you do

CL-USER> (for (i 0 (i < 10) (++ i 1)

Then you get an error but won't know what happened, and in a way, you won't be creating a new language, just defining a lisp function for every function of "MyLanguage".

If you go the long and hard way, you get to know exactly where the error was, why was it an error, etc. I.e. a full fledged compiler

huh? i don't understand .. if i where to do something wrong i know exactly where it happens

the stuff that is wrong is cleary marked by a different (red) color in my environment and lisp reports a backtrace with pointers to where in the code it happened and i can navigate there directly by pressing a key:

```

(defun test ()
  (for (i 0 [COLOR="Red"](i < 10)[/COLOR] [COLOR="Red"](++ i 1)[/COLOR]) 
    (format t "i: ~A~%" i)))

```

edit:
like this:
[IMG]http://common-lisp.net/~lnostdal/images/lisp-for.png[/IMG]

---

### Post by Acapulco on 2008-02-26
One last post: [http://www.cs.nuim.ie/~jpower/Courses/parsing/]("http://www.cs.nuim.ie/~jpower/Courses/parsing/")

Check this out. I really haven't read all the pages, but it seems to have the basic stuff explained, so you might want to start there to look for pointers, then start a search of your own.

Sorry for all the posts, but I really love this subject (although I'm no expert at it)

---

### Post by Zwack on 2008-02-26
Lex and Yacc (or Flex and Bison) can be used to create interpreters as well as compilers.  

In fact I'd say that if you are serious about this then you might want to take a small subset of some language and implement that as a learning exercise.

But what do I know.

You're not likely to be writing the new killer language that everyone wants to learn but Lex and Yacc are useful for more than just writing compilers or interpreters.

Z.

---

### Post by CptPicard on 2008-02-26
> **coolkid5 said:**
> So, if I were to make an interpreter do just use a language like C or Java, or are Bison and Flex used for interpreters as well?

Of course you need to parse your grammar first to produce your internal abstract syntax tree... this is the so called "front end" of your compiler. The "back end" part produces the compiled code, and this is what I suggest you leave out for the time being, and just evaluate your AST in memory, thus creating an interpreter.

---

### Post by HuBaghdadi on 2008-02-26
ANTLR is an outstanding software for parser generation.

---

### Post by aks44 on 2008-02-26
> **Wybiral said:**
> Do you know a lot about assembly language or virtual machine design? If not, you'll probably want to start there
> **CptPicard said:**
> 4. If you want a compiled language, walk the tree and output assembly,
> **CptPicard said:**
> Of course you need to parse your grammar first to produce your internal abstract syntax tree... this is the so called "front end" of your compiler. The "back end" part produces the compiled code

I'd tend to disagree on the "back-end" part: a compiler does not *necessarily* produce binaries / machine code.

There are numerous examples out there of compilers that actually do their "compiler" job (ie. parsing, syntax checking, AST, ... even optimize) then output some intermediary code in another language.

The example that comes to mind is the Comeau C++ compiler, which outputs... C code. For convenience of the programmer, the C compiler is then automatically called, but that's another matter. :)

---

### Post by Wybiral on 2008-02-26
> **CptPicard said:**
> I have to disagree with Wyb here and advice you to create an interpreter and not bother with the assembler. Your first task here is to just get something running, and to get your grammar parsed etc... just read in your source and evaluate it in your interpreter, instead of outputting anything compiled.

That's why I said they either have to know assembly OR how to write a virtual machine. But you're right, if your language generates tokens close enough to "byte code" (such as Lisp or Forth) or your AST is efficient enough to walk as-is then you can interpret it directly. But you still have to know how to write a machine that will interpret the AST (a virtual machine of sorts, it doesn't have to mimic normal processors with registers and stacks, but IMO it's still a virtual machine).

---

### Post by pmasiar on 2008-02-26
As usually, Python has some neat library/framework to do 60% of the job in a realy simple way. This one, surprised me. It should not be that simple! :-)

[ Programmable Python Syntax](http://benjiyork.com/blog/2008/02/programmable-python-syntax-via-source.html)

Enjoy!

---

### Post by Wybiral on 2008-02-26
> **pmasiar said:**
> As usually, Python has some neat library/framework to do 60% of the job in a realy simple way. This one, surprised me. It should not be that simple! :-)

[ Programmable Python Syntax](http://benjiyork.com/blog/2008/02/programmable-python-syntax-via-source.html)

Enjoy!

That's an amusing little hack!

---

### Post by moma on 2008-02-26
Hello,

You can with moderate efforts create your own programming language. People has traditionally used Lex/Flex and Yacc/Bison for lexical and syntax analyzes of code.  But these tools are outdated. Forget them. 

[COLOR="DarkRed"]Parrot and PGE rules ![/COLOR]
Start with the Parrot virtual machine. Parrot also provides an excellent grammar engine (PGE, Parser Grammar Engine) that lets you define gramma for your programming language.

Study: [http://parrotcode.org](http://parrotcode.org)
+
[http://en.wikipedia.org/wiki/Parser_Grammar_Engine](http://en.wikipedia.org/wiki/Parser_Grammar_Engine)

I wrote a longer rant about Parrot and PGE in my blog (norwegian language).  Link: [http://linux1.no/blogg/moma/3231/perl6-boken-ankom-i-dag-holder-meg-opptatt]("http://linux1.no/blogg/moma/3231/perl6-boken-ankom-i-dag-holder-meg-opptatt")

At the bottom of the blog page you'll find instructions how to install Parrot on Ubuntu Gutsy and Hardy.  It also shows how to compile the samples in the parrot/examples/tutorial/ directory.
----

As said, Parrot has a powerful grammar engine.
Take a look at the "abc" calculator project in the parrot/languages/abc/ folder.

The clue is to create grammar.pg and grammar-actions.pl files. Study:
/parrot/languages/abc/src/grammar.pg
/parrot/languages/abc/src/grammar-actions.pl

There are also other good programming language projects in the languages/ directory. Study them all and stay Parrot VM compatible.

---

### Post by coolkid5 on 2008-02-26
Thanks for all of the responses.
Does anyone know of a tutorial on parsers, grammars, compilers etc like making an infix notation calculator or something like that?
I think that would be a good way for me to start learning.

---

### Post by Limvot on 2008-02-26
I tried to do this once before also.
First, i belive GNU has an example of doing this, but i don't know where it is.

Also you can do this.
 1. Go here and look at the code i once made. (sorry bout spelling)  [http://limvot.x10hosting.com/Links/codeprogects.htm](http://limvot.x10hosting.com/Links/codeprogects.htm)
(yes i know it just makes c++ code out of the input)
2. i once had code that compiled it's output when it was done interpting, but i lost it and never put it on my web site. (which is going to get a makeover soon. :popcorn:) but you can replicate what i did by looking at my code, and then calling a system() call on the code like so. (example program calling compiler)

#include <iostream>

main(void) {
system("g++ yoursourcehere.cpp -o yourprogramname");
return 0;
}

And yes, i do know the disadvantages of using system(). It is because it is nessary for the OS to be looking for such a call. But most do by defult, (including windows and Ubuntu)  so you are in the clear.

My program is like Comeau! A big name compiler! Yay!

---

### Post by Zwack on 2008-02-26
If I remember correctly one of the Flex or Bison manuals covers most of what you will want to know to start with decent examples...

Z.

---

### Post by coolkid5 on 2008-02-26
Yes, I believe I saw a tutorial in the flex and/or bison manuals.

> **Limvot said:**
> I tried to do this once before also.
First, i belive GNU has an example of doing this, but i don't know where it is.

Does any one know about this?

Any other tutorials?

---

### Post by kaens on 2008-02-26
Well, there's [this]("http://http://compilers.iecc.com/crenshaw/"). . . 

I don't think it's a topic that gets tutorialed very often, probably because few programmers have a need for writing such things until they've been at it long enough to be able to just read references and manuals to find out what they need to do.

---

### Post by Zwack on 2008-02-26
As I said earlier the [Bison manual]("http://www.gnu.org/software/bison/manual/") has a fairly extensive example...  But you will also want the [Flex manual]("http://www.gnu.org/software/flex/manual/") as they interface together.

The Bison manual takes you through a reverse polish calculator as an example...  I've used them for non compiler purposes before and they're fairly straightforward to use once you get into it.  That's not to say that writing a Compiler is easy, but that using Flex and Bison isn't particularly complicated.

I hope that this helps,

Z.

---

### Post by pmasiar on 2008-02-26
> **coolkid5 said:**
> Does anyone know of a tutorial on parsers, grammars, compilers etc like making an infix notation calculator or something like that?
I think that would be a good way for me to start learning.

As I said before: If you cannot find decent tutorial in all what Google knows, you are not ready yet.

---

### Post by stratavarious on 2008-02-27
.

---

