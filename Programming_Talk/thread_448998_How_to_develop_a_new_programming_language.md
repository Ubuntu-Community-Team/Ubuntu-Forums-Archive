---
title: "How to develop a new programming language??"
date: 2007-05-19
forum: Programming Talk
---

### Post by palestal on 2007-05-19
Hi, i'm a c programmer. i teach c programming for univ. students. i'm 14 years old. I want to develop a new programming language. Can anyone tell me how can i do this?
Thanks...

---

### Post by MRiGnS on 2007-05-19
> **palestal said:**
> Hi, i'm a c programmer. i teach c programming for univ. students. i'm 14 years old..

oO

---

### Post by palestal on 2007-05-19
i heard yacc and lex, but i didn't use them

---

### Post by loell on 2007-05-19
you must have good understanding on languages and automata theory :popcorn:

---

### Post by palestal on 2007-05-19
i know them very well, object based and functional programming languages. I worked on visual basic 6.0 too.

---

### Post by loell on 2007-05-19
i see, i guess your all set, define your language syntax:mrgreen:
then develop your lexical analyzer. :guitar:

---

### Post by palestal on 2007-05-19
i heard yacc and lex, but i don't know how about using them...

---

### Post by muaddib on 2007-05-19
palestal,
A few years ago, I decided to try my hand at writing my own programming language in my spare time. Believe me, it is very difficult, and very complex.
If you are really interested in this, I suggest that you become proficient at coding in multiple different languages. Also, you should have some basic understanding of certain aspects of computer science - things like object-oriented programming and recursion.
If you just can't wait, there are several programs out there that can help you develop your language. I have learned to use Flex and Bison (aka Lex and Yacc).
Essentially, the way they work is like this:
Flex is a lexical analyzer, which outputs tokens.
Bison is a parser generator, which takes tokens, and outputs C code.
I think you will find there is a lot of learning you need to do before you will be able to generate a real programming language. If you are satisfied with a simple calculator, though, there are tutorials on the web (search google) to help you do that.
- Muad'dib

---

### Post by diatribe on 2007-05-19
a 14yo teaching college students doesnt smell like bull to anyone else here?

---

### Post by samjh on 2007-05-19
> **diatribe said:**
> a 14yo teaching college students doesnt smell like bull to anyone else here?

Best to ignore that sort of thing, and focus on the question at hand.  It's not relevant whether it's true or not (probably the latter).

In any case, if he is smart enough to teach university students at age of 14, then he should be smart enough to figure out how to use Yacc and Lex.  So no help forthcoming from me. :p

---

### Post by Ptero-4 on 2007-05-19
lol. the bane of forum users, being underage.

---

### Post by pmasiar on 2007-05-20
> **Ptero-4 said:**
> lol. the bane of forum users, being underage.

It is NOT about underage. It is about asking a question without making initial research which would gave him a clue about amount of work which it will take to solve it. Designing a language is so obviously beyond OP capabilities so it does not make sense to answer. Better question will be: what I need to learn to be able to do it - but did he asked it? No.

Another question is, why would anyone wasted time on using this new language? What problem is solves better? Again, not asked.

If you need to ask how to design the language, you don't have enough experience to do it. :-)

---

### Post by JT673 on 2007-05-20
:shock: :shock: :shock:

Lex, Yacc, Flex, Bison are all good contenders.  I used JavaCC once, and it's pretty good.  Take baby steps, start with a small arithmetic calculator.

---

### Post by slavik on 2007-05-20
> **pmasiar said:**
> It is NOT about underage. It is about asking a question without making initial research which would gave him a clue about amount of work which it will take to solve it. Designing a language is so obviously beyond OP capabilities so it does not make sense to answer. Better question will be: what I need to learn to be able to do it - but did he asked it? No.

Another question is, why would anyone wasted time on using this new language? What problem is solves better? Again, not asked.

If you need to ask how to design the language, you don't have enough experience to do it. :-)
designing a language doesn't have to be about solving some problem. remember why linux started, it is because someone wanted to "learn about the 386." and unix started "because there was a pdp-7 and running the space sim on the mainframe was expensive." (quotes are paraphrazed)

---

### Post by ankursethi on 2007-05-20
I decided to try and develop an interpreter for good ol' BASIC once (in C, of course). I'll be 17 this year, I know Python, Perl, C, bit of C++ and PHP, although I haven't done large projects with anything except PHP. Yet I couldn't get to grips with this project of mine. So I decided to do just what the guys here are saying, i.e., develop a simple calculator instead :-). And believe me, once you start even that turns out to be pretty hard. It goes without saying that I gave up on my interpreter.

I suggest you look at the source for something like uBasic (search Freshmeat.net), read up on programming language design (there's even a book on that, look on Amazon), do your research. Once you're comfortable with some more programming languages as well as these design concepts, then look at "designing" your own language.

GM

---

### Post by coder_ on 2007-05-20
[_Compilers: Principles, Techniques, and Tools_]("http://www.amazon.ca/Compilers-Alfred-V-Aho/dp/0201100886") is a good read on it.  It isn't an easy read by any means, and doesn't focus on lex (or flex) or yacc (or bison) in any means, but it would certainly help you, if you can grasp the ideas.  Also, note that it is a college level textbook.

Keep in mind that this can be a very complex thing, depending on what kind of language you are writing.  Don't go trying to write the next Python or Perl, unless you have *a lot* of experience.

---

### Post by loell on 2007-05-20
:D even guido of python and larry of perl , developed their languages for years and its still evolving not to mention bjarne of c++, and these brilliant individuals developed thier languages when they are a bit more older.

life is kinda short ya know, enjoy it ;)

and perhaps try to consider this project later in life. :p

---

### Post by pmasiar on 2007-05-20
> **slavik said:**
> designing a language doesn't have to be about solving some problem. remember why linux started, it is because someone wanted to "learn about the 386." and unix started "because there was a pdp-7 and running the space sim on the mainframe was expensive." (quotes are paraphrazed)

Exactly. Both projects (and BTW neither Linux or Unix are languages, but anyway)  were started to solve some concrete problem and by experienced developer, not as an ego-trip by some wannabe so obviously without basic knowledge.

Let me tell you that when Linus started writing his own kernel (which was to become Linux), he knew a lot about design of operating systems, and he also read  and digested source code of Minix. He did not need to ask which tools are needed.

---

### Post by russell.h on 2007-05-20
If you want to write a compiled language you are going to need a compiler. Which means you are going to need to know assembly not only well enough to write it, but well enough to write a computer program to write it.

Or, if you are looking for something similar but that won't involve learning assembly write a high level language that "compiles" to C.

---

### Post by slavik on 2007-05-20
> **pmasiar said:**
> Exactly. Both projects (and BTW neither Linux or Unix are languages, but anyway)  were started to solve some concrete problem and by experienced developer, not as an ego-trip by some wannabe so obviously without basic knowledge.

Let me tell you that when Linus started writing his own kernel (which was to become Linux), he knew a lot about design of operating systems, and he also read  and digested source code of Minix. He did not need to ask which tools are needed.
at the time he was writing linux, he didn't even take an OS class (he says it himself in the argument he and tenembaum have).

you best learn by actually trying to do something, maybe OP will eventually create a very nice language.

@OP, try writing an interpreter for brainfuck (very simple language, with only 8 commands), then try to tackle something a bit more complex (maybe even something that has C-like syntax).

Also, remember, the first C++ compiler was only a translator (to C) :)

---

### Post by wmcbrine on 2007-05-20
I would say... Learn all the languages that exist first... Then, if you still think a new one is needed, you'll have a better idea of where to go with it. More likely, you'll find one or more existing languages to your liking along the way.

---

### Post by rekahsoft on 2007-05-20
> **diatribe said:**
> a 14yo teaching college students doesnt smell like bull to anyone else here?

yes it did...i almost clicked back right away

---

