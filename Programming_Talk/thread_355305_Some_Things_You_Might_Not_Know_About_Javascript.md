---
title: "Some Things You Might Not Know About Javascript"
date: 2007-02-07
forum: Programming Talk
---

### Post by SuperMike on 2007-02-07
Here's some things you might not know about Javascript.

* It used to be called Livescript at Netscape, eons ago.

* Yes, you can start your variables with a dollar sign like you do in Perl or PHP. $Kewl.

* On Ubuntu, ngs-js is a Javascript interpreter that is "good enough" and has a lot of functionality for all kinds of uses, including the same kinds of things you might use Perl on a server, and it has a very tiny footprint. It also can be used as a CGI language in your web server. Javascript doesn't have to be solely a web thing, though -- you can use it for monitoring servers, for instance.

* Some people don't know that when you don't use 'var' in a function, it becomes a variable in the global scope instead of the local scope, and that's "expensive" (consumes resources).

* I like how Javascript isn't that hokey. I mean, Perl's interesting here or there, but it has some oddball things in it like the 'else if' being called 'elsif' and so on.

---

### Post by runningwithscissors on 2007-02-07
And here's something that everyone knows about Javascript

* It is a pain in the arse
* It is ugly
* Abused beyond belief (even more now that AJAX is here) as people think they can have truely dynamic apps
* Every browser has a different implementation (nobody cares about the W3C)
* Used to make those annoying pop ups and alert boxes


Bring it some sanity! Please! Or kill it!

---

### Post by Wybiral on 2007-02-07
Javascript isn't THAT bad if used responsibly... It's kind-of like alcohol!

---

### Post by SuperMike on 2007-02-07
Scissors: perhaps your real pain with Javascript is not with Javascript at all but is, instead, a dislike of the browser-specific versions of it and the DHTML linkage and/or AJAX. So, take all that away and imagine it being used as a language to interface with just console or file I/O, for instance, such as what you might see with ngs-js. When you begin to look at it from that perspective, it sure does look like a beautiful language. Sure, it has its quirks here or there, but much of any quirks you have with it can be undone by creating some functions.

---

### Post by dannyboy79 on 2007-02-07
javascript IS awesome because it's OS independent. You can write a script and use it on your pda, windows, linux, or wherever.

---

### Post by lloyd mcclendon on 2007-02-07
the awesomeness of javascript has really remained a secret to most developers. 

[http://www.crockford.com/javascript/javascript.html](http://www.crockford.com/javascript/javascript.html)

---

### Post by SuperMike on 2007-02-07
> **lloyd mcclendon said:**
> the awesomeness of javascript has really remained a secret to most developers. 

[http://www.crockford.com/javascript/javascript.html](http://www.crockford.com/javascript/javascript.html)

Exactly.

When used via ngs-js, my opinion of Javascript turned around. Sure, ngs-js could stand some improvement, but it's "good enough" as is. Moreover, the developer left the doorway open for me to write a C library and link it in via the Javascript, giving it a way to do even more.

As for the other quirks I dislike about Javascript, I can easily overcome them with some functions.

Another cool thing about Javascript is that I can remember it fairly easy once I get going. I don't have to keep looking junk up.

Now, granted, when you have to do browser-exception type work, or mess with DHTML or XPCOM, yeah, Javascript gets hairy, but it's not Javascript's fault -- it's the fault of the way DHTML and XPCOM were implemented in a klunky interface, and the fault of all these programmers thinking that the w3c.org is just a jumble of letters.

---

