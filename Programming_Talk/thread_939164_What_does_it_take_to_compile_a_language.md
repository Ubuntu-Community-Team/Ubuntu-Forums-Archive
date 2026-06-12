---
title: "What does it take to compile a language?"
date: 2008-10-05
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-10-05
so ive made my own language that is very simple but is basically translated from its state to C and then compiled with gcc

so my question is: what does it take to turn my psudo-C into a compiled program without gcc?

---

### Post by snova on 2008-10-05
[LIST]
  [*] A tokenizer
  [*] A syntactic analyzer
  [*] A lexical analyzer
  [*] A backend
[/LIST]

First, the tokenizer. This is what splits "thing[a+2]" into "Name: variable", "Open bracket", "Name: a", "Operator: Plus sign", "Constant: 2", "Close bracket".

Then there's the syntactic portion. It takes the above input and decides what it means.

After that, there's lexical things to consider. What does the above statement mean in context?

Finally, there's the backend, which takes everything generated so far and spits out something else, which is the output of the compiler.

Naturally, I've probably missed a few important components, but compilers are complex things. You could probably simplify it a lot if the syntax isn't drastically different from C, but then it wouldn't be much more than a preprocessor.

A full compiler would also include an intermediate "bytecode", optimizers to work on the bytecode (the "middle end"), and a completely different kind of backend that generates assembly code (usually).

So, quite a lot. Have fun.

---

### Post by jimi_hendrix on 2008-10-05
*decides to keep the interperater*

---

### Post by snova on 2008-10-05
Before this thread disappears, I want to know a little more about the language.

It might not be as hard as I described. I think the only really hard bit is the tokenizer, because it's *very* context-sensitive. Take strings for example- normally you ignore whitespace, but in a string, they are as important as everything else. The tokenization process is about splitting the input into atomic pieces.

Then there's the syntactic part, which might actually be harder. Look at the first token, and if it's a string and matches "if", look for a '('. Then read tokens into an expression buffer until you meet a matching ')'. Feed the expression into another parser that checks for validity. Then look for a '{', but if one can't be found, a statement will do instead, so look for a ';'. This probably is the hard part, actually... Anyway, this stage is about reversing what the tokenizer did- take the atoms and decide how they fit together, while making sure nothing is missing.

Then you have to decide whether some of them make sense. Statements don't make sense outside of functions. If 'scalar' is accessed as an array but was declared as an integer, that's an error. And so on. You take the statements that the syntax parser put together and combine them into higher level components, like "function body", "class declaration", and so on.

Then you just take all of that and dump it to a C file.

So it's a tough job, but don't lose heart, or you'll miss a really fun project. And think carefully about what I call "fun".

If you ever decide to continue with this, I might like to help a little.

Edit: If you've already got an interpreter, you can skip the first three sections and go right to the C backend. Silly me. You've already done most of the work!

---

### Post by jimi_hendrix on 2008-10-05
meh i was bored one day and decided to make a "1337 C" language...the translator is written in C# and can easily be hacked to turn any of my keywords to C keywords...but ive been considering writing a simple real language (as in not 1337 speak and it compiles...) even though its way over my head it would be a cool hobby

---

### Post by snova on 2008-10-05
Well, post the interpreter source, I'd like to take a look. Unfortunately, I know very little about C#, but I should be able to make some sense of it.

I've been thinking about language design myself recently. I think an easy place to start would be to combine the indentation-based syntax of Python with C, so that you get all the niceties of Python with the low-level stuff of C. (It would also require that statements be put on their own line, just as in Python.) It wouldn't be much more than a preprocessor, and you wouldn't even have to touch the indivual statements.

---

### Post by hac13 on 2008-10-05
> **jimi_hendrix said:**
> meh i was bored one day and decided to make a "1337 C" language...the translator is written in C# and can easily be hacked to turn any of my keywords to C keywords...but ive been considering writing a simple real language (as in not 1337 speak and it compiles...) even though its way over my head it would be a cool hobby

Another way to do it would be to define your 1337 language as macros for the C preprocessor, like: #define pr1n7f() printf()

---

### Post by jimi_hendrix on 2008-10-05
acually my language would use something more like this for printf():

|>?|~-|-|=("|-||=-||[], \^/[]?||)"); (prints hello, world)

these might not have been the exact characters i used because the program is not right in front of me but you get the idea

---

### Post by snova on 2008-10-05
Oh, dear me... No thank you, I don't think I'm interested anymore. :)

---

### Post by jimi_hendrix on 2008-10-05
> **snova said:**
> Oh, dear me... No thank you, I don't think I'm interested anymore. :)
well that can all be changed very easily...its ment to be an interchangeable translator and the 1337 part was ment to be a useless language anyway

---

### Post by mssever on 2008-10-05
Flex and Bison are designed for part of the process. I've never messed with either, though, so I can't help you beyond telling you to read the documentation.

---

### Post by jimi_hendrix on 2008-10-05
thank you

---

### Post by snova on 2008-10-05
Well, I was looking at it with the assumption that you would write your own parser, but if you want to learn how to use these tools, I guess that works too. :)

---

### Post by jimi_hendrix on 2008-10-05
id do whatever...i could probably make a pretty decent parser for a whitespace language if i could figure out how to deal with nested loops

or i could just make a GOTO language :D

---

### Post by pmasiar on 2008-10-05
> **snova said:**
> I've been thinking about language design myself recently. I think an easy place to start would be to combine the indentation-based syntax of Python with C, so that you get all the niceties of Python with the low-level stuff of C.

There are Cython (which compiles to C) and rPython (restricted Pyrhon used to write Python system in Python).

Another language you may want to look into is Forth: it's trivial to extend/specialize basic constructs of Forth language in any direction. One of the reson is total lack of any syntax (space is token delimiter, rest is semantics) and direct access to both argument and call stacks. I've seen tinyPascal (simplified Pascal) implemented in 11 pages of Forth code, including parser, compiler, and interpreter of P-code. Extremely impressive!

---

