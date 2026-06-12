---
title: "What features of javascript make it powerless?"
date: 2010-12-11
forum: Programming Talk
---

### Post by vim_lover on 2010-12-11
I have read so many articles about using javascript as a general purpose programming language.  But practically I see it is not widely adopted as a general purpose language.  Nowadays python and ruby are successful general purpose languages.  Why could javascript not get the place of python and ruby?  The simple answer is python and ruby are powerful.  Javascript is powerless (compared to python and ruby).

**My question is:**
What language features of javascript (either presense of or absense of) make it less powerful than python and ruby?

---

### Post by dv3500ea on 2010-12-11
Javascript is not powerless, and comparing the 'power' of [turing complete]("http://en.wikipedia.org/wiki/Turing_completeness") programming languages is just silly. Javascript is being widely adopted, not just in browsers but [on the desktop]("http://live.gnome.org/Seed"), [on servers]("http://nodejs.org/") and [in databases]("http://couchdb.apache.org/").

---

### Post by Arndt on 2010-12-11
> **dv3500ea said:**
> Javascript is not powerless, and comparing the 'power' of [turing complete]("http://en.wikipedia.org/wiki/Turing_completeness") programming languages is just silly. Javascript is being widely adopted, not just in browsers but [on the desktop]("http://live.gnome.org/Seed"), [on servers]("http://nodejs.org/") and [in databases]("http://couchdb.apache.org/").

I'll just add the note that we used Javascript as embedded script language in an application, which worked well enough overall, but we discontinued this practice (offering the users a socket interface with C instead) because the implementation of Javascript (Spidermonkey, I believe) had some bugs which made the execution unreliable. This was three years ago, and they may have fixed them, or there may be other freestanding implementations of Javascript.

---

### Post by nvteighen on 2010-12-11
Javascript coders were powerless and that brought very bad popularity to the language. Until people started to realize Javascript is useful... and AJAX-based technology was born :) Nowadays, all the nice web apps you probably use more or less wouldn't be possible if Javascript didn't exist.

But Javascript is impressively good: it's dynamic, it's got a good OOP system that borrowed some concepts from Functional Programming, it's client- and server-side (Python, Ruby and Perl are only server-side), and now it's becoming faster than anyone ever imagined thanks to Google's (GPLed) V8 engine.

---

### Post by vim_lover on 2010-12-11
Two more questions.

1) Python and ruby are strongly typed.  Javascript is weakly typed.  Does it make javascript a powerless language?

2) Python and ruby have standard libraries.  Is it possible to write a javascript standard library?  Why are developers hesitating to write a javascript standard library?

---

### Post by dv3500ea on 2010-12-11
> **vim_lover said:**
> Two more questions.

1) Python and ruby are strongly typed.  Javascript is weakly typed.  Does it make javascript a powerless language?

2) Python and ruby have standard libraries.  Is it possible to write a javascript standard library?  Why are developers hesitating to write a javascript standard library?

1) No

2) There is no standard library but the environment in which javascript is embedded may have a standard library for that particular environment. Seed, for example, has an imports object which allows importing of libraries or file I/O, Gtk etc. The approach in javascript is different - instead of having a core language and having extra libraries for each problem domain, the interpreter is embedded separately for each problem domain and the appropriate functionality is exposed to the language. The HTML DOM, for example, is not part of javascript but it is an API exposed by the web browser environment in which javascript is embedded.

---

### Post by CptPicard on 2010-12-11
I would suggest you read Douglas Crockford's *Javascript: The Good Parts* to get an understanding of why Javascript is both flawed and inspired, and thus salvageable to a degree. There are also videos of Crockford giving talks on the subject.

Javascript has, unfortunately, its fair share of really bad design decisions, and the fact that until recently it was strictly restricted to running within the browser's environment as a sort of browser extension -- married to the DOM, which is an awful API on its own -- did not help.

However, if you know how to avoid the pitfalls in Javascript and make full use of the really good features that fortunately made into the language -- the prototype-based object system, and first-class functions and closures, you can leverage *those* features as they are very strong indeed. They can be used to build a lot of other stuff (see *Structure and Interpretation of Computer Programs* -- Javascript can be  close to Lisp, although using C-style syntax).

> **vim_lover said:**
> 
1) Python and ruby are strongly typed.  Javascript is weakly typed.  Does it make javascript a powerless language?

IMO weak typing is a dangerous feature that can result in very "surprising" behaviour. Javascript's tendency to "help" by converting things magically to strings and then operating with them as such is one of the worst features of the whole language. The type system has other oddities, such as the ability to define "undefined"... try

```

undefined = 3

```

and then see what "undefined" is...

> 
2) Python and ruby have standard libraries.  Is it possible to write a javascript standard library?  Why are developers hesitating to write a javascript standard library?

Javascript doesn't really have a decent modularization system... everything is just loaded into one single global scope to begin with, because the language used to be so tightly coupled to the browser.

But, as I said before, closures help here as well. There is a "module pattern" you can make use of. But as far as a "standard library" goes, that will have to come from some sort of standardisation efforts of the browser authors.

---

### Post by trent.josephsen on 2010-12-11
Why would you want to use Javascript as a GP language when you have languages that are already well-suited to a wide variety of tasks, have extensive standard libraries and healthy communities, are well-respected in the software industry, and don't behave weirdly or crash suddenly when run with a different browser?

I don't know a whole lot of Javascript, but I am somewhat familiar with it, and I can't imagine what it has to offer as a general-purpose language.  For Web site scripting, sure, it's really the only option, and I'm kind of okay with that.  But with Perl, Python, Ruby, C, C++, Java, bash, assembly, and who-knows-what-else at my fingertips, I just don't see a compelling reason to make Javascript an acceptable general-purpose alternative.  That would involve a lot of work for very little return.

---

### Post by saulgoode on 2010-12-11
```
alert(.1 + .2)
```

---

### Post by shadylookin on 2010-12-11
Javascript is used a lot. It's the only option for client side scripting without using flash/java applets

I would say it's biggest problem the browsers that support DOM manipulation differently. Libraries like JQuery extract that out and make it decent to use. 

I'm not a big fan of weak typing either. A typo that would have thrown a compiler error is instead now part of your object or global scope.

---

### Post by dv3500ea on 2010-12-11
> **saulgoode said:**
> ```
alert(.1 + .2)
```

This is not just a problem in javascript - it is a problem with floating point arithmetic in general. You will get the same problem in other languages.

---

### Post by CptPicard on 2010-12-11
> **shadylookin said:**
>  A typo that would have thrown a compiler error is instead now part of your object or global scope.

Or, a runtime error. That's more important, taking proper TDD practices into account.

---

### Post by saulgoode on 2010-12-11
> **dv3500ea said:**
> This is not just a problem in javascript - it is a problem with floating point arithmetic in general. You will get the same problem in other languages.
You are correct, however, other languages don't mandate that all numerical operations be done in floating point. Nonetheless, my point was made tongue-in-cheek -- Javascript is a decent language (though mostly just syntactic sugar for Scheme).

---

