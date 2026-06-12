---
title: "need help for c++ programming."
date: 2010-11-21
forum: Programming Talk
---

### Post by chinmay3 on 2010-11-21
I am trying to learn c++. I installed build-essential. I have read some documentations about it. i tried the same way as mentioned in documentation but when i save gedit file of source code i get following error....... (gedit:3838: GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed Is there anyone who know how to resolve this problem? Thanks in advance.

---

### Post by GregBrannon on 2010-11-21
There is an excellent area, a sub forum, for help with these kind of problems called Programming Talk.  Maybe a nice mod will move this post there.

In the meantime, please provide more info about your development environment and your error message.  Have you had success doing any coding?  Did the typical first program, "Hello, World" work?  Show us the code that's not working - post code in code tags - and copy exactly the commands you're using to compile and run the code and the error messages you're getting.

Good luck, and keep coding!

---

### Post by lisati on 2010-11-21
*Thread moved to **Programming Talk**.*

---

### Post by spjackson on 2010-11-21
> **chinmay3 said:**
> I am trying to learn c++. I installed build-essential. I have read some documentations about it. i tried the same way as mentioned in documentation but when i save gedit file of source code i get following error....... (gedit:3838: GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed Is there anyone who know how to resolve this problem? Thanks in advance.
I don't really see why reports of bugs in gedit/glib need to be moved to Programming Talk, unless you are wanting help in fixing gedit/glib, and as you are just learning that would be somewhat ambitious!

From reading the many similar posts in other forums, these messages are due to relatively unimportant bugs in gedit/glib. Here's one of many [http://ubuntuforums.org/showthread.php?t=1264420](http://ubuntuforums.org/showthread.php?t=1264420)

Does your file save? If so, don't worry about it, or run gedit from the menu rather than the command line when you won't see the message.

If these messages are a a real problem for you, then simply switch to one of the many many alternatives to gedit: vim, emacs, Geany etc.

---

### Post by lucasart on 2010-11-21
> **chinmay3 said:**
> I am trying to learn c++. I installed build-essential. I have read some documentations about it. i tried the same way as mentioned in documentation but when i save gedit file of source code i get following error....... (gedit:3838: GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed Is there anyone who know how to resolve this problem? Thanks in advance.

Can you please show us your source code ?

Also, to begin you should use an IDE. I suggest you install CodeLite from Synaptic. It's much easier than writing text files, because:
* when compiling and linking with g++, it outputs errors so you can click on them and it will point you to the corresponding line of code
* you can then run your program in debug, doing a step by step execution (using F5, F9, F10, F11 keys, just like in MSVC)

I strongly suggest you start coding in plain C. Only when you fully grasp the subtilties of C should you attempt to learn C++.

---

### Post by santosh83 on 2010-11-21
> **chinmay3 said:**
> I am trying to learn c++. I installed build-essential. I have read some documentations about it. i tried the same way as mentioned in documentation but when i save gedit file of source code i get following error....... (gedit:3838: GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed Is there anyone who know how to resolve this problem? Thanks in advance.

Build essential shouldn't be necessary for taking your first steps with C++. Just g++ and gdb should be sufficient, and maybe boost as well. Which documentation did you read. I think if you're really serious about this, getting an hardcopy book should prove very useful. Two of the best are 'C++ Primer' and 'The C++ Programming Language.'

As for your gedit assertion, it seems to be a bug in your version gedit/glib. One way is to try compiling and installing gedit from source. Also ensure that you've applied all the latest updates offered by the update manager. Does this happen when saving any file, or only under some circumstances?

Anyway, in the interim, to get work done, use another editor like GVim or Kate.

---

### Post by wojox on 2010-11-21
How are you calling it?

```
g++ test.cpp -o test
```

---

### Post by nvteighen on 2010-11-21
That error message is completely irrelevant... You're free to report that bug in Gedit, but chances are high that it already was :P


> **lucasart said:**
> 
Also, to begin you should use an IDE. I suggest you install CodeLite from Synaptic. It's much easier than writing text files, because:
* when compiling and linking with g++, it outputs errors so you can click on them and it will point you to the corresponding line of code
* you can then run your program in debug, doing a step by step execution (using F5, F9, F10, F11 keys, just like in MSVC)


No, please... The sole fact that you describe the use of keys as an advantage of IDEs reflects my opinion on them: they're not for beginners who still don't know the concepts behind the programming process, but for people that already know them and need an environment that displays all sort of needed tools in a single place (but knowing how to fix stuff manually when something fails).

> 
I strongly suggest you start coding in plain C. Only when you fully grasp the subtilties of C should you attempt to learn C++.

Well, I'd suggest Python before C or C++, but that's another discussion. So, if the alternatives are C and C++, well, I'd go for C, then some unrelated OOP language (whatever: Python, Ruby, Common Lisp, even Smalltalk-80!) and then C++, so that you appreciate the STL (but so that you also don't adore it neither consider it the best thing in the programming universe...).

---

### Post by GregBrannon on 2010-11-21
chinmay3,

See what you've started?  Not your fault, obviously.

Please post your code and the tutorial(s) or book(s) you're using to start your C++ journey, and let's get you on your way, out of the middle of this argument.  If you need a learning resource, check out the stickies.

---

### Post by chinmay3 on 2010-11-21
this is why i am in love with Ubuntu. The community, lots of helping hands to pull you out of trouble , whoever you are, wherever you are.  Thanks everybody. lets come to the point.  here is link of page what i have followed.:  [http://www.ubuntugeek.com/how-to-install-c-and-c-compilers-in-ubuntu-and-testing-your-first-c-and-c-program.html](http://www.ubuntugeek.com/how-to-install-c-and-c-compilers-in-ubuntu-and-testing-your-first-c-and-c-program.html)  I done exactly same as there written. I have little experience with 'c' programming but its with turbo c compiler on windows xp. Yes the file get saved even after error. I regularly update my system.

---

### Post by GregBrannon on 2010-11-21
I suppose that's as good a place to start as any, except for the gedit part because of the apparently known gedit bug that others have reported.

Do you know how to use any other command line editor?  An editor that you're comfortable with already would be best.  If there is none or you have no preference, then I'll ask someone else to recommend an editor that is already installed or can be easily installed in your current OS setup.

Have you mentioned that?  Which OS are you using?  Which desktop environment?

---

### Post by trent.josephsen on 2010-11-21
I'll echo nvteighen:  IDEs are not good for beginners, and I'd choose C before C++ (but Python before either).  C and C++, but especially C++, suffer from lots of outdated and inaccurate resources that a lot of people still follow and gather bad habits from.  (Notably, the tutorial you linked should use int main(void) in the C example, and the first example on [this page](http://www.cprogramming.com/tutorial/lesson1.html) both pollutes the main namespace and uses an ugly hack to work around poorly written IDEs.

As for an editor, I'll recommend both Vim and jEdit.  Vim has a much steeper learning curve, but in the long run has made me a much more productive coder.  jEdit is easier to get started with.  There's also nothing wrong with continuing to use gedit; lots of people do.

---

### Post by nvteighen on 2010-11-21
> **chinmay3 said:**
> this is why i am in love with Ubuntu. The community, lots of helping hands to pull you out of trouble , whoever you are, wherever you are.  Thanks everybody. lets come to the point.  here is link of page what i have followed...

It's interesting you say that being myself a Debian user... :D

> **trent.josephsen said:**
> I'll echo nvteighen:  IDEs are not good for beginners, and I'd choose C before C++ (but Python before either).  C and C++, but especially C++, suffer from lots of outdated and inaccurate resources that a lot of people still follow and gather bad habits from.  (Notably, the tutorial you linked should use int main(void) in the C example, and the first example on [this page](http://www.cprogramming.com/tutorial/lesson1.html) both pollutes the main namespace and uses an ugly hack to work around poorly written IDEs.


Yes, one of the biggest issues of C++ tutorials is that they assume that to learn C++ you need to learn C, which is completely false. The way of doing things in C++ is completely different and translating C into C++ is the path to disastrous code that uses hacks instead of the C++ STL. Moreover, if I really had to, I'd teach C++ starting with the STL and highest-level constructs and only climb down to the C-inherited bits when strictly needed. STL-style C++ isn't a great thing, but isn't as bad as C-like C++.

IMO, this is the best C++ resource, updated and reasonably sane: [http://cplusplus.com/](http://cplusplus.com/)

---

### Post by trent.josephsen on 2010-11-21
> **nvteighen said:**
> It's interesting you say that being myself a Debian user... :D
My PC, an Arch machine, hasn't run Ubuntu since Intrepid Ibex.

> **me said:**
> Notably, the tutorial you linked should use int main(void) in the C example, and the first example on this page both pollutes the main namespace and uses an ugly hack to work around poorly written IDEs.

I forgot to say that I picked that page because it was one of the first hits on a Google search for "learn C++".  Just one example of how pervasive bad habits can be.

---

### Post by chinmay3 on 2010-11-22
sorry if anybody get hurt as I considered all community members uses ubuntu. I am grateful to all community members whatever os they are using. I am thinking to use _'vim'_ . I believe in
 [COLOR=Magenta]" JUST BECAUSE SOMETHING IS DIFFICULT DOESN'T MEAN YOU SHOULDN'T TRY, IT MEANS YOU SHOULD JUST TRY HARDER "
[COLOR=Black]
So i will try harder to learn it.:D
[/COLOR][/COLOR]

---

### Post by trent.josephsen on 2010-11-22
I don't think anyone was offended; for my part, it was just an interesting observation.

Good luck with Vim!  You should probably start by running "vimtutor".  Afterwards, from within Vim, type ":help" to start reading through the manual, which is quite extensive, but will make you more productive.

---

