---
title: "Opinions on Ruby?"
date: 2008-04-22
forum: Programming Talk
---

### Post by danbuter on 2008-04-22
I've been programming for a year or so in Python, upon recommendation from other programmers. I learned a heck of a lot in that time, and I do agree Python is great for beginners. However, I don't really like the "feel" of Python. Not really sure what it is. I've considered a number of other languages. Ruby seems like it could be really interesting (and I've seen it described as Lisp with C syntax). I was just wondering what those of you who have experience with Ruby and a few other languages think of it. I don't really want to jump in and spend a bunch of time on it without at least some comments from experienced programmers. I really only program as a hobby, this is not a career path for me. Thanks!

---

### Post by stevescripts on 2008-04-22
I only have tinkered with Ruby, but find it interesting.

Why not give it a try?

I sorta like this link: [http://www.ruby-lang.org/en/documentation/quickstart/](http://www.ruby-lang.org/en/documentation/quickstart/)

I have also done a little RubyTk, and thats not bad either

Just my $.02

Steve
PS - You could also have a look at that tired dead old language Tcl ... ;)
see the links below

---

### Post by ghostdog74 on 2008-04-22
> **danbuter said:**
>  However, I don't really like the "feel" of Python. Not really sure what it is. 

that's weird.

---

### Post by ihavenoname on 2008-04-22
> **danbuter said:**
> I've been programming for a year or so in Python, upon recommendation from other programmers. I learned a heck of a lot in that time, and I do agree Python is great for beginners. However, I don't really like the "feel" of Python. Not really sure what it is. I've considered a number of other languages. Ruby seems like it could be really interesting (and I've seen it described as Lisp with C syntax). I was just wondering what those of you who have experience with Ruby and a few other languages think of it. I don't really want to jump in and spend a bunch of time on it without at least some comments from experienced programmers. I really only program as a hobby, this is not a career path for me. Thanks!
Ruby is "currently" slower than python. But it has a lot of really really nice features. If your scripting speed probably won't matter anyways. The ruby website has an online interactive terminal/tutorial that shouldn't take 20minutes  to do. If you like it then look more into it otherwise there are plenty of other languages to try. You might be interested in javafx (not java, but part of the java platform).  They have some very nice features ( for example to run something on a different thread you use do{ "things to do in another thread"} I haven't looked into it too much but it seems very nice.

As for ruby having C syntax, I don't know about that, they are different. Ruby has very simple syntax though.

---

### Post by lnostdal on 2008-04-22
> **danbuter said:**
> ..(and I've seen it described as Lisp with C syntax)..

..and Lisp itself has both. Isn't that great? It has Lisp with Lisp syntax (that is; no syntax really) and a real "C compiler" (instead of C syntax, which ofc. sucks).

Here: 
* [http://common-lisp.net/~lnostdal/writings/sbcl.html](http://common-lisp.net/~lnostdal/writings/sbcl.html)
* [http://gigamonkeys.com/book/](http://gigamonkeys.com/book/)
* [http://www.paulgraham.com/onlisptext.html](http://www.paulgraham.com/onlisptext.html)

---

### Post by danbuter on 2008-04-22
I've looked into Lisp. I really don't understand it. That's kind of why I was thinking of learning Ruby. It seems like it's a step in that direction, but with a style I understand. (I knew I shouldn't have written syntax in my OP).

---

### Post by danbuter on 2008-04-22
> **ghostdog74 said:**
> that's weird.

Um, not really helpful. I guess, with Python, I don't like the Only One Way To Do It philosophy. I've been doing some minor tinkering with Perl and other languages, and they just seem more free-form. Since I don't have to code for another person to maintain, this may suit me more. I really like Perl's philosophy, but it just looks unreadable to me.

---

### Post by ghostdog74 on 2008-04-22
> **danbuter said:**
> Um, not really helpful. I guess, with Python, I don't like the Only One Way To Do It philosophy. 

so now you have a reason. If this is the case, just go ahead and give Ruby a shot. Since you are only progam as a hobby anyway. If you want to , maybe you can post this question to  comp.lang.ruby and comp.lang.python.

---

### Post by pmasiar on 2008-04-22
@OP: Why Ruby? Compared to Python, Ruby does not have much new to teach you. So what is your learning goal?

More educational would be some statically typed language, like C or C++, or more useful for career, like Java or even C#. Or more different, like Lisp, Prolog, Erlang, Forth.

(I cannot believe me promoting Java! Hell froze over :-) )

It is very hard to give you any advice where to go without any information about your goals.

Another suggestion would be to pick a Free software project you want to contribute to (best is: you want a feature added), and learn its language.

Ruby is OK language, I just do not see reason to switch to 99% language if you already know 100%. They are almost identical (Ruby being little slower, little less widely used, with less libraries).

---

### Post by mssever on 2008-04-23
I like Ruby. It's my language of choice much of the time, and it "feels" right to me; more so than Python (of course, that's my subjective opinion).

What I like about Ruby:

[LIST]
[*]Variable names show scope
[*]Awesome method naming conventions: names ending in ? return a boolean; names ending in ! are dangerous/modify the receiver in place; instead of def __add__(other), Ruby does def +(other)
[*]Blocks
[*]Auto closing files
[*]Awesome, flexible syntax
[*]The syntax reflects the fact that Ruby is 100% OO. You'd never know that Python is fully OO without being told.
[*]Ruby's web-based API docs (Ruby's doc style takes some getting used to, but IMHO it's easier than Python's docs once you get used to it)
[/LIST]
What I dislike about Ruby:

[LIST]
[*]Dumb names for many settings: $/, $\, $-, etc. Some are easy enough to remember, though, it you're familiar with Bash scripting, such  as $:, $0, and $?. Workaround: require 'English'
[*]Ruby isn't necessarily very fast, although the next release is supposed to address it, if they ever decide to release it.
[*]Rails. Its documentation is poor. Once you learn your way around, I hear that it isn't too bad, but there's no good beginners documentation. Plus, rails is difficult to host because it doesn't run well on Apache.
[/LIST]
Areas where Python is superior to Ruby:

[LIST]
[*]Namespaces. Namespaces. Namespaces.
[*]Better library coverage. I've had to switch part of one of my projects to Python because I need TLS authentication for SMTP and Ruby's net/smtp isn't up to the task, as far as I can tell. Also, Ruby's sqlite3 library is really buggy.
[/LIST]
I don't know much about lisp (though I want to learn it sometime), but I think that Ruby is quite different from it.

By the way, being too free-form is a Bad Thing because it tends to make code look like line noise. Python attempts to prevent that problem, and goes a bit overboard in that respect (IMHO), but Ruby gives you enough rope to hang yourself. Don't take all that rope, even though it's there.

---

### Post by ZuLuuuuuu on 2008-04-23
When I was at the step of choosing Python and Ruby I gave both a try. I gave try to Ruby first. Ruby seemed that it is really beautiful. But after a while 4758473589437604 ways to write a syntax began to annoy me. Because every programmer will write the syntax as "he like" and this will certainly reduce the maintainability of the program. Also to have more then 1 functions to do the same thing... What is it for? I will have to learn all of them to be able to read anyone's code.

I like that Python tries to bring some new philosophy like "Nobody uses switch statement so throw it away." or "Everybody is doing indenting to show the blocks so why not give them a real meaning?". I am now investigating whether the statement that "Python is not as much object-oriented as Ruby is." is true. 

All I can say is these for now because I am still at the beginning of learning Python. I am reading the free "Byte of Python" book to get more about Python "feel".

---

### Post by jespdj on 2008-04-23
I have some experience with Ruby and only did very little with Python (my main programming language is Java).

However, I do think I like Ruby better than Python. Ruby seems more clean than Python. I don't like the significant whitespace idea of Python, and some things are strangely inconsistent. For example, why are there built-in functions like len(s) to get the length of a string? It would have been much cleaner if the String class had a length() method instead.

I did notice however that Ruby is quite slow. I wrote some small programs that process XML files, and for example using XPath (with Ruby's REXML) is very slow.

---

### Post by CptPicard on 2008-04-23
> **jespdj said:**
> For example, why are there built-in functions like len(s) to get the length of a string? It would have been much cleaner if the String class had a length() method instead.

Duck typing. "len" is not only the length of a string, it is the length of any object that implements __len__() which gets called by the global len().

(Now, don't ask me why they didn't just make it so that anything that has a length just implements object.len() ;) -- probably has something to do with the fact of not "having" to use objects...)

---

### Post by CaptainLinux94 on 2008-04-23
> **danbuter said:**
>  However, I don't really like the "feel" of Python.

Yeah, I think I understand what you're trying to say.  Are you feeling like you're ready for less noodly-code and less beginner syntax to take advantage of programming as much as you can?

I'm still working with Python, but then again...  I have this giant book by O'Reilly on Python; I swear you can do everything in Python...  Just not as fast as something like C.

If you're comfortable with Python why not give C a try.

---

### Post by mssever on 2008-04-23
> **ZuLuuuuuu said:**
> I like that Python tries to bring some new philosophy like "Nobody uses switch statement so throw it away."That's one of the things I miss in Python. I think that the switch/case statement is cleaner than a series of elsif statements. Ruby's case statement doesn't fall through, but I think that that is even useful sometimes.

> **CptPicard said:**
> Duck typing. "len" is not only the length of a string, it is the length of any object that implements __len__() which gets called by the global len().

(Now, don't ask me why they didn't just make it so that anything that has a length just implements object.len() ;) -- probably has something to do with the fact of not "having" to use objects...)In Ruby, everything that has a length implements a length method. ("some string".length) This makes for greater consistency. I believe that the term duck typing was coined by the Ruby community. Whether or not that's the case, Rubyists certainly use duck typing a lot. Also, since enumerable objects implement the each method, Ruby programmers rarely use for loops. They call some_object.each instead.

---

### Post by pmasiar on 2008-04-23
> **mssever said:**
> I believe that the term duck typing was coined by the Ruby community.

[http://en.wikipedia.org/wiki/Dynamic_typing#Duck_typing](http://en.wikipedia.org/wiki/Dynamic_typing#Duck_typing) assign coining to Python's Alex Martelli.

---

### Post by lnostdal on 2008-04-23
> **danbuter said:**
> I've looked into Lisp. I really don't understand it.
yeah, figures .. "so let's go shopping!" .. it would be a crying shame actually learning something truly new, wouldn't it

anyway .. no matter; more for me, as always

---

