---
title: "Perl6 is going to be more awesome than ..."
date: 2008-09-24
forum: Programming Talk
---

### Post by slavik on 2008-09-24
Firefox3 awesome bar! :)

Some features to note:
Regular Expressions have been overhauled from ground up, they are now first class citizens in Perl6 (not a module like Java/Python/C++/etc.), in Perl5 they were just strings. There is also something called "rules" that expands on regular expressions. Rules allow you to create grammar objects, so that you can easily define your own language. Perl6 will ship with 1 language already defined and that will be the Perl6 language.

here's a grammar sample of what it would look like (I couldn't get grammars to work in pugs or in rakudo ... :(), if you've ever looked at a language syntax specification, this should look very familiar. :) (there is an actual name for the notation of language syntax)
```

grammar URL {
        token TOP {
            <schema> '://' 
            [<hostname> | <ip> ]
            [ ':' <port>]?
            '/' <path>?
        }
        token byte {
            (\d**{1..3}) <?{ $0 < 256 }>

        }
        token ip {
            <byte> [\. <byte> ] ** 3
        }
        token schema {
            \w+
        }
        token host {
            (\w+) ( \. \w+ )*
        }
        token port {
            \d+
        }
        token path {
            <[a..zA..Z0..9-_.!~*'():@&=+$,/]>+

        }
    }

```

and since grammars are objects, you can do something similar to the following:
```

grammar URL:HTTP is URL {
    token schema { 'http' }
}

```

use strict; use bignum; are default, bignum kicks in just like in Python/Haskell (when needed).

sigils are for life:
perl5: my @array; $array[1]=5;
perl6: my @array; @array[1]=5;

for loops will be automatically parallelized (that's what the language spec says but there is a debate as to what model to use) this is similar to using OpenMP, except that it would be automatic. :)

---

### Post by ankursethi on 2008-09-24
I tried Perl5 once. It was pretty nice and got the work done quite quickly. Then I just moved to Python instead, expecting to learn Perl properly once Perl 6 was released. This was 2 years ago, and we still haven't seen a production quality Perl6 release.

I think this is exactly what is hindering this otherwise awesome language. People look around the web, realize that Perl6 is in development and decide they'll learn it when the new version comes out.

@slavik
You're the Perl guy around here. Any speculations on when Perl6 is going to come out? I'm also looking forward to Parrot. If Parrot sees wide adoption, we'll probably see people writing Python or Ruby interpreters for it. Which would be uber-awesome. Any news about Parrot?

---

### Post by pmasiar on 2008-09-24
> **ankursethi said:**
> If Parrot sees wide adoption, we'll probably see people writing Python or Ruby interpreters for it. Which would be uber-awesome. Any news about Parrot?

I cannot claim than nobody will ever write Python on Parrot, but **my** first priority (if I was smart enough to be Python core hacker) would be PyPy: Python compiler in Python, which has engine 
- (1) optimized for Python (instead of generic engine with more special cases not for Python)
- (2) coded in Python, not in whatever implementation language of Parrot is: C? Haskell?

Of course there might be people who like Parrot and I might be wrong (and definitely not smart enough to hack on Python core) but that is my gut feeling from following Python devel list on occasions.

---

### Post by slavik on 2008-09-24
well, at the moment, pugs (Perl6 interpreter written in haskell) has more features, but I already have tried rakudo (perl6 on parrot). so far, parrot is missing bignum.

from what I read, there is a project kp6 (kinda perl6) that is going to be used to bootstrap perl6 to create a minimal perl6 compiler that will compile perl6.

right now, if you want to try perl6, lookup cabal (because compiling pugs didn't work for me). cabal is like apt for haskell stuff. :)

I would say that anything close to production level perl6 should be almost ready in a year ...

I have to note that I tried some more or less process intensive code (translated from perl5) and so far pugs is much slower (but it's only a prototype)

---

### Post by ankursethi on 2008-09-24
> **pmasiar said:**
> I cannot claim than nobody will ever write Python on Parrot, but **my** first priority (if I was smart enough to be Python core hacker) would be PyPy: Python compiler in Python, which has engine 
- (1) optimized for Python (instead of generic engine with more special cases not for Python)
- (2) coded in Python, not in whatever implementation language of Parrot is: C? Haskell?
My first choice for writing Python would always be the standard CPython. Parrot would be interesting because it would compete head-on with Sun's JVM and Microsoft's .NET.

---

### Post by slavik on 2008-09-25
> **ankursethi said:**
> My first choice for writing Python would always be the standard CPython. Parrot would be interesting because it would compete head-on with Sun's JVM and Microsoft's .NET.
actually, the point of something like PyPy or KP6 is that once you have the minimal implementation of the language (that you need to implement everything else), you can use that to create an interpreter that is platform independent.

for example: you have python2.5 for windows, now you can write a python 3.0 interpreter in python 2.5 (all an interpreter/compiler is/does: parse the code into a tree, translate it to some kind of byte code, optimize the stuff somewhere along the way)

a real world example: linux kernel is developed on systems running the linux kernel, gcc is written in C which gcc compiles. :)

come to think of it, this bootstrapping things and "lang A in lang A" is some pretty neat stuff.

EDIT: KP6 page: [http://moritz.faui2k3.org/pugs/v6/docs/kp6-roadmap.pod.html](http://moritz.faui2k3.org/pugs/v6/docs/kp6-roadmap.pod.html)
the minimal perl6 interpreter is written in Perl5, pretty much the same as pypy

---

### Post by kavon89 on 2008-09-25
I love how a thread about Perl6 turns into python discussion. :popcorn:

---

### Post by slavik on 2008-09-25
it's still about perl6 ... nobody got anything on grammars. :)

makes implementing a parser for your language that much simpler. :)

not only that, but there is automatic parallelization (OpenMP style). :)

---

### Post by LaRoza on 2008-09-25
> **slavik said:**
> Firefox3 awesome bar! :)

Some features to note:
Regular Expressions have been overhauled from ground up, they are now first class citizens in Perl6 (not a module like Java/Python/C++/etc.), in Perl5 they were just strings. There is also something called "rules" that expands on regular expressions. Rules allow you to create grammar objects, so that you can easily define your own language. Perl6 will ship with 1 language already defined and that will be the Perl6 language.

Interesting, however, why is having them built into the language better than a module? Now you have to update the entire language to update regular expressions.

---

### Post by slavik on 2008-09-25
because this allows faster text processing. :)

and no, you don't have to update the language to update regular expressions. there is still notation for regular expressions, except that in perl5 $var = "/regex/"; would make $var be a string. in perl6 $var will be a regular expression (as an object).

regex is a built in type, much like int or float or string. it's the same as Integer in java. what's the point of having an Integer class? and int is an int is an int ... but in reality, it's not.

I mean, why would you have two list generating functions and then change one of them to act as the other one (range() and xrange()).

---

### Post by LaRoza on 2008-09-25
> **slavik said:**
> because this allows faster text processing. :)

Is that usually a bottleneck?

> 
I mean, why would you have two list generating functions and then change one of them to act as the other one (range() and xrange()).
Perl has functions like that? This thread is about Perl, is it not ;)

---

### Post by loell on 2008-09-25
> **LaRoza said:**
> Is that usually a bottleneck?

the web has lots of texts, we need more text processing power than ever before. :D

---

### Post by slavik on 2008-09-25
> **loell said:**
> the web has lots of texts, we need more text processing power than ever before. :D
not only that, but it makes building your own language much much simpler.

you just define the different tokens, and then you build and NFA out of the tokens and you're good. :)

then it becomes parsing the individual tokens and replacing it with other code. :)

---

### Post by LaRoza on 2008-09-25
> **loell said:**
> the web has lots of texts, we need more text processing power than ever before. :D

And the network is usually the bottleneck, or disk access.

---

### Post by slavik on 2008-09-25
which is why Perl6 will have kernel threads and be able to parallelize things like:

for @list -> $val {
#do something with $val
}

---

