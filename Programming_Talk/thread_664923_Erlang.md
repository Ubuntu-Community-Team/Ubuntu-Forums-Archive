---
title: "Erlang"
date: 2008-01-11
forum: Programming Talk
---

### Post by YourSurrogateGod on 2008-01-11
A few days ago I learned about Erlang. I looked at [www.erlang.org](www.erlang.org) and on wikipedia to learn more. I installed the interpreter and ran a few simple programs. Does anyone have advice about this particular programming language? Is it any similar to Lisp (if so how)? What are your experiences?

The whole thing about putting a period at the end of a line and then whitespace was a little odd at first.

---

### Post by angustia on 2008-01-11
i'm practicing programming in erlang too

what i can say:
- it's becoming my language of choice for anything network oriented, it's a pleasure to create state machines.
- it's good for creating systems, attending many clients at time or controlling many external processes (see the port system). it's not good for creating small scripts.
- you're going to have some patience getting used to the functional style and using read only variables

---

### Post by YourSurrogateGod on 2008-01-11
> **angustia said:**
> i'm practicing programming in erlang too

what i can say:
- it's becoming my language of choice for anything network oriented, it's a pleasure to create state machines.
- it's good for creating systems, attending many clients at time or controlling many external processes (see the port system). it's not good for creating small scripts.
What about neural networks?
> **angustia said:**
> - you're going to have some patience getting used to the functional style and using read only variables

Yes, I noticed that. But there are other things that can functionally replace variables (as we're used to them in other languages), I think they're called modules, but can't recall.

---

### Post by YourSurrogateGod on 2008-01-12
Angustia, how do you get out of the emulator once you're in it?

I get to this point:
```
$ erl
Erlang (BEAM) emulator version 5.5.2 [source] [async-threads:0] [hipe] [kernel-poll:false]

Eshell V5.5.2  (abort with ^G)
1>
```
The only way that I can get out is do Ctrl + C. Ctrl + G doesn't really work very well.

I know that lisp's emulator has (bye), (quit) and (exit) commands.

---

### Post by angustia on 2008-01-12
> **YourSurrogateGod said:**
> Angustia, how do you get out of the emulator once you're in it?

I get to this point:
```
$ erl
Erlang (BEAM) emulator version 5.5.2 [source] [async-threads:0] [hipe] [kernel-poll:false]

Eshell V5.5.2  (abort with ^G)
1>
```
The only way that I can get out is do Ctrl + C. Ctrl + G doesn't really work very well.

I know that lisp's emulator has (bye), (quit) and (exit) commands.



q().

---

### Post by angustia on 2008-01-12
> **YourSurrogateGod said:**
> What about neural networks?


Yes, I noticed that. But there are other things that can functionally replace variables (as we're used to them in other languages), I think they're called modules, but can't recall.

i don't know so much about neural networks, but i could guess:

- each neuron it's a very simple state machine
- you want to have the maximum number of neurons

you could program some neural networks using erlang processes, but if you need to make the maximum performance you will be force to use a compiled language.



P.S. if you have a smp machine, run erlang this way:

erl -smp
excuse my english

---

### Post by YourSurrogateGod on 2008-01-13
> **angustia said:**
> i don't know so much about neural networks, but i could guess:

- each neuron it's a very simple state machine
- you want to have the maximum number of neurons

you could program some neural networks using erlang processes, but if you need to make the maximum performance you will be force to use a compiled language.



P.S. if you have a smp machine, run erlang this way:

erl -smp
excuse my english

Silly question, but what's SMP. I looked in the man page and this is what I got:
```
         -smp [enable|auto|disable]:

             -smp enable and -smp starts the Erlang runtime system with SMP support enabled. This may fail if no runtime  system  with  SMP  support  is
             available.  -smp  auto starts the Erlang runtime system with SMP support enabled if it is available and more than one logical processor are
             detected. -smp disable starts a runtime system without SMP support. This is currently the default behavior. -smp auto will probably be  the
             default behavior some time in the future.

             NOTE: The runtime system with SMP support will not be available on all supported platforms. See also the +S flag.
```
It tells me how to activate it, but it forgets to tell me what it is :) .

---

### Post by popch on 2008-01-13
Symmetrical Multi Processing?

---

### Post by angustia on 2008-01-13
[http://en.wikipedia.org/wiki/Symmetric_multiprocessing](http://en.wikipedia.org/wiki/Symmetric_multiprocessing)

like this:

> Gazelle laptop.
Dual-core, 2 gigs of ram.

---

### Post by YourSurrogateGod on 2008-01-13
Cool thanks guys :) .

One other thing that I picked up. It seems that Erlang is really good at running many processes at the same time. So good, that the web servers written in erlang out-performed Apache by a very large margin.

[http://en.wikipedia.org/wiki/Yaws_%28web_server%29](http://en.wikipedia.org/wiki/Yaws_%28web_server%29)

That's pretty cool.

---

### Post by efittery on 2008-02-21
> **YourSurrogateGod said:**
> A few days ago I learned about Erlang. I looked at [www.erlang.org](www.erlang.org) and on wikipedia to learn more. I installed the interpreter and ran a few simple programs. Does anyone have advice about this particular programming language? Is it any similar to Lisp (if so how)? What are your experiences?

The whole thing about putting a period at the end of a line and then whitespace was a little odd at first.

You have to put a period "." at the end of a line but you don't have to put any white space.

Just tried:

1+1.

with no white space and it returned

3

:KS

---

### Post by HuBaghdadi on 2008-02-24
I highly recommend Erlang, it is a powerful, robust programming language.
Even if you don't use it in your work, it will teach you new ways in programming as it is a Functional programming language.
It has a web framework too:
[http://erlyweb.org/](http://erlyweb.org/)

---

### Post by YourSurrogateGod on 2008-02-26
> **efittery said:**
> You have to put a period "." at the end of a line but you don't have to put any white space.

Just tried:

1+1.

with no white space and it returned

3

:KS

I'd love to know how you got that. I did the same thing in a shell and in a file and got 2.

---

### Post by a9bejo on 2008-02-27
> **HuBaghdadi said:**
> I highly recommend Erlang, it is a powerful, robust programming language.


I read a book and implemented a project in Erlang last year, but I found the language not as interesting as the hype indicated: Or, more precisely, the official implementation of the language: It has some really dirty designed APIs, and some awful implemented modules. Stuff like IO and Regular Expression parsing is extremely slow in the official Erlang implementation.  And eager evaluation is really not that 	fascinating if you learn a functional programming language.

I think the acteur model, the lightweight process model and the syntactic sugar for process invocation are great.  But as a  functional programming language, haskell and ocaml have a more beautiful design in my opinion.

I still recommend the book by Joe Armstrong to get familiar with the concurrent concepts.

---

### Post by HuBaghdadi on 2008-02-27
> **a9bejo said:**
> I read a book and implemented a project in Erlang last year, but I found the language not as interesting as the hype indicated: Or, more precisely, the official implementation of the language: It has some really dirty designed APIs, and some awful implemented modules. Stuff like IO and Regular Expression parsing is extremely slow in the official Erlang implementation.  And eager evaluation is really not that 	fascinating if you learn a functional programming language.

Maybe because the language was created to be used in only Ericsson, no thoughts to make it available to the public (so the APIs aren't polished)?
For Java folks, Scala promise is to bring Erlang concurrency model to the Java platform.

---

