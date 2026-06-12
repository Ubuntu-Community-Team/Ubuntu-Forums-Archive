---
title: "Forth ..."
date: 2008-07-03
forum: Programming Talk
---

### Post by slavik on 2008-07-03
I took a look at Forth the other day and to me it seemed to be like brainfuck.

Is there anything special about Forth that I am missing?

---

### Post by pmasiar on 2008-07-03
[Forth](http://en.wikipedia.org/wiki/Forth_%28programming_language%29) is real programming language for experienced programmers who can handle total control over the CPU, and want to build sophisticated systems running in extreme limited environments. It was between first languages directly implemented in CPU.

[Brainfuck](http://en.wikipedia.org/wiki/Brainfuck) is esoteric language never used for anything in real life.

Maybe what confuses you is its reverse Polish notation and direct manipulation of stack, and even higher level of compactness than Perl has, with even higher use of ascii special characters, where every punctuation symbol is an operation, mostly on stack, right? That's one of the interesting features - and surely it adds to the compactness of the code :-) Even Perl cannot compete with Forth's one-liners :-)

Another difference is simplicity how in Forth you can define new "words", and total lack of syntax which allows join defined words using intended semantics. Forth is language to quickly and simple develop problem-oriented mini-languages - more than any other language I ever encountered.

Forth is the only "real" language intended to really smart programmers only - Smart can increase productivity 10 times, average programmer will struggle of fail. It was designed to be polarizing.  And that possibly was one of the reasons why it did not become success: after Forth started (end of '70), IBM PC revolution changed IT, and wave of inexperienced MS BASIC programmers on PC washed over IT, and Forth was definitely beyond the grasp of most of them ([by design](http://dobbscodetalk.com/index.php?show=In-this-1980-article-from-Byte-Charles-Moore-recounts-the-creation-of-Forth..html))

You possibly cannot imagine how it was being programmer before PC. It was serious job for professionals in glass rooms, requiring education and dedication. 

I would encourage curious programmers to take a look - it will change your perception what is possible to do, and how little resources you really need to do that.

[A Beginner's Guide to Forth](http://galileo.phys.virginia.edu/classes/551.jvn.fall01/primer.htm)

---

### Post by slavik on 2008-07-04
right, it has direct stack manipulation and the syntax are very simple.

when I was reading about the stack manipulation, it reminded me of brainfuck.

"defining new words" ... a word is a function IMO. :)

it seems to me that forth is to assembly is what functional languages are to declarative languages (haskel to C for example). Would this be a fair comparison?

---

### Post by pmasiar on 2008-07-04
> **slavik said:**
> "defining new words" ... a word is a function IMO. :)

not necessary. Most words manipulate stack, but not all.

see [above mentioned intro](http://galileo.phys.virginia.edu/classes/551.jvn.fall01/primer.htm), chapter 11, d.

```

: jtab:  ( Nmax --)      \ starts compilation
    CREATE              \ make a new dictionary entry
    1-  ,               \ store Nmax-1 in its body
;                        \ for bounds clipping

: get_xt    ( n base_adr -- xt_addr)
    DUP  @      ( -- n base_adr Nmax-1)
    ROT         ( -- base_adr Nmax-1 n)
    MIN  0  MAX    \ bounds-clip for safety
    1+  CELLS+  ( -- xt_addr = base + 1_cell + offset)
;

: |   '  ,   ;     \ get an xt and store it in next cell

: ;jtab   DOES>  ( n base_adr --)   \ ends compilation
    get_xt  @  EXECUTE        \ get token and execute it
;    \ appends table lookup & execute code

\ Example:
: Snickers   ." It's a Snickers Bar!"   ;   \ stub for test

\ more stubs

5 jtab:  CandyMachine
         | Snickers
         | Payday
         | M&Ms
         | Hershey
         | AlmondJoy
;jtab

3 CandyMachine  It's a Hershey Bar!   ok
1 CandyMachine  It's a Payday!   ok
7 CandyMachine  It's an Almond Joy!   ok
0 CandyMachine  It's a Snickers Bar!   ok
-1 CandyMachine  It's a Snickers Bar!   o

```


Word 'jtab:' starts definition of your little compiler (of your custom structure), '|' adds item, and ';jtab' defines how to use defined structure.

They are not functions: they define custom compiler, allocate memory, and compile addresses of previously defined function to the new code.

> it seems to me that forth is to assembly is what functional languages are to declarative languages (haskel to C for example). Would this be a fair comparison?

Even if  you can define functionality of any Forth word in assembly, it's not the focus: focus is to define custom structures and operators for your custom minilanguage specialized exactly as you want it. The moment you defined your minicompiler, you can forget about low level and solve problems in words you just defined.

---

### Post by slavik on 2008-07-04
interesting ...

---

