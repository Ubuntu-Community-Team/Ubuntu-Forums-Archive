---
title: "Clojure"
date: 2008-10-18
forum: Programming Talk
---

### Post by Shin_Gouki2501 on 2008-10-18
Hello there ubuntu programming forum!

Today i want to introduce to some very nice stuff:
[http://en.wikipedia.org/wiki/Clojure](http://en.wikipedia.org/wiki/Clojure)

"Clojure is a dialect of Lisp that runs on the Java Virtual Machine."
And it brings some very nice Ideas with it :)

[http://blog.thinkrelevance.com/2008/9/24/java-next-overview](http://blog.thinkrelevance.com/2008/9/24/java-next-overview)
So this first link is a overview from Stuart Halloway on "java.next" languages, the interestign thing there is that it show some common problems and hwo those are solved with Clojure and others in comparison.

[http://groups.google.com/group/clojure/msg/16fec21eb1fff8aa?pli=1](http://groups.google.com/group/clojure/msg/16fec21eb1fff8aa?pli=1)
An overview from Rich Hickey since Clojure is already 1 year old, it gives somes nices infos!

[http://robert.zubek.net/blog/2008/04/26/clojure-web-server/](http://robert.zubek.net/blog/2008/04/26/clojure-web-server/)
An Example of how to code an webserver in clojure.

[http://rpdillon.googlepages.com/creatingexecutablejarswithclojure](http://rpdillon.googlepages.com/creatingexecutablejarswithclojure)
An Example of how to create a jar from clojure.

[http://enclojure.net/Index.html](http://enclojure.net/Index.html)
CLI Intefaces like REPL are nice. But sometimes you want IDE support too.

[http://blog.thinkrelevance.com/2008/09/16/pcl-clojure](http://blog.thinkrelevance.com/2008/09/16/pcl-clojure)
So if you come from LISP or want to see how some problems are solved with Clojure besure to check this out!


So that's it!If you like check it out : [http://clojure.org/](http://clojure.org/)

---

### Post by nvteighen on 2008-10-18
It's definitely on my Wishlist since some time ago (Wybiral's fault :)), but I don't have enough time... :(

Anyway, according to your links, I see some stuff that seems like Scheme but automated (the "loop" procedure... in Scheme we have the "named let" idiom and usually recursions are "named lets" named "loop").

---

### Post by Shin_Gouki2501 on 2008-10-18
the data structes are incredible!

Check these Videos out where Rich Hickey explain those himself:
[http://blip.tv/file/get/Richhickey-ClojureForLispProgrammersPart1997.mov](http://blip.tv/file/get/Richhickey-ClojureForLispProgrammersPart1997.mov)

[http://blip.tv/file/get/Richhickey-ClojureForJavaProgrammers2Of2680.mov](http://blip.tv/file/get/Richhickey-ClojureForJavaProgrammers2Of2680.mov)

---

### Post by nvteighen on 2008-10-18
I've downloaded the Clojure interpreter and looked at the official documentation... Man, even though the language is still in a embryonic phase, it's impressive!

And I love that's pure-functional... assignment in Lisp is somewhat a weird thing, IMO.

---

### Post by Shin_Gouki2501 on 2008-10-18
Yes its "still" growing have a look at the examples made by stu!
He will also relase soon a Book!

---

### Post by rye_ on 2008-10-18
Something I'm sure you guys will know (and yes I've looked at wikipedia!!).

I assume the name clojure is an amalgamation of closure and java?
Am I correct in thinking the definition of a closure is just a block of functionality which makes of variables from its defining space?
(freezing the value of those values inputted when block first defined)

Cheers,

---

### Post by Shin_Gouki2501 on 2008-10-18
I think i read somewhere where the name comes from.. In some blog comments i don't remember exatcly where or what it does stand for.

Or are you like one of those here:
[http://www.reddit.com/r/programming/comments/77jx4/clojures_first_year/.mobile](http://www.reddit.com/r/programming/comments/77jx4/clojures_first_year/.mobile)

who can'T get over the name ? ;)

---

### Post by nvteighen on 2008-10-19
> **rye_ said:**
> Something I'm sure you guys will know (and yes I've looked at wikipedia!!).

I assume the name clojure is an amalgamation of closure and java?
Am I correct in thinking the definition of a closure is just a block of functionality which makes of variables from its defining space?
(freezing the value of those values inputted when block first defined)

Cheers,

You're right about closures. But more technically put, a closure is a function that is created in some place (the "defining environment") and when called, is able to refer to variables/bindings back from the "defining environment", even when that environment isn't being executed.

It's not just a Clojure propierty, not even just Lisp dialects', but you can do it in Javascript by making a function return another function that refers to variable or also in Python. Closures are there in any programming language where functions are "first-class citizens" (i.e. objects you can manipulate like any other built-in object).

---

### Post by CptPicard on 2008-10-19
Even more technically put, IIRC the closure is exactly the set of bindings that are associated with the anonymous function, and these bindings are in force even after the lambda is returned.

I am not sure if you can have closures outside of the discussion of lambdas though... but the lambda "has a closure".

---

### Post by Shin_Gouki2501 on 2008-10-19
Another nice example:
[http://netzhansa.blogspot.com/2008/10/trying-clojure.html](http://netzhansa.blogspot.com/2008/10/trying-clojure.html)
(source code example link in comments)

---

### Post by mssever on 2008-10-19
> **nvteighen said:**
> It's not just a Clojure propierty, not even just Lisp dialects', but you can do it in Javascript by making a function return another function that refers to variable or also in Python. Closures are there in any programming language where functions are "first-class citizens" (i.e. objects you can manipulate like any other built-in object).
How do you do closures in Python? As far as I know, you might be able to call inner functions and lambdas closures, but they're quite limited compared to, say, Ruby's blocks and procs.

---

### Post by nvteighen on 2008-10-19
> **mssever said:**
> How do you do closures in Python? As far as I know, you might be able to call inner functions and lambdas closures, but they're quite limited compared to, say, Ruby's blocks and procs.
Check the ErrMsg code in Sysres! ;)

But yeah, Python lambdas are pretty limited and maybe they aren't even closures: 

1. They seem to substitute free variables instead of building a pointer to a frame... so, if you try to do some assignment inside the lambda, Python yields a (IMO) absurd SyntaxError, as Python is a mostly imperative language.

2. The lambda statement in Python doesn't accept more than one-liners... That's pretty annoying. I hope they change that in the future.

---

### Post by mssever on 2008-10-19
> **nvteighen said:**
> Check the ErrMsg code in Sysres! ;)
That's only a closure on a technicality. :) And Guido considered removing lambdas from Python 3.0 (don't have the link anymore). Fortunately, lambdas are staying. But that's nothing like Ruby, which uses closures all over the place. For example, the usual iteration method, each, does its own iteration internally (instead of returning an iterable), and calls a closure for each element.

---

### Post by CptPicard on 2008-10-19
Guys... you do not "call a closure" :) The lambda has an associated closure, because the function *closes over* the environment it is defined in.

(I know I'm nitpicking, but...)

EDIT: and oh yeah, to the OP, Clojure really is nice. It's my favourite Lisp...

---

### Post by nvteighen on 2008-10-20
> **CptPicard said:**
> Guys... you do not "call a closure" :) The lambda has an associated closure, because the function *closes over* the environment it is defined in.

(I know I'm nitpicking, but...)


Anyway, thanks for nitpicking! :) You're always enlightening!

---

### Post by Shin_Gouki2501 on 2009-06-12
[http://developers.sun.com/learning/javaoneonline/j1sessn.jsp?sessn=TS-4164&yr=2009&track=javase](http://developers.sun.com/learning/javaoneonline/j1sessn.jsp?sessn=TS-4164&yr=2009&track=javase)

When the netbeans plugin gets updated i need to check it again STM and other stuff looks so nice!

---

