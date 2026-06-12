---
title: "Opensource on Windows"
date: 2009-02-05
forum: Programming Talk
---

### Post by oasmar1 on 2009-02-05
If I was to create an opensource program in WIndows, what would be the best language to use if I wanted to eventually port it to OS X or Linux. I am currently leaning towards C++ but if there is a better suggestion please tell me.
Also, what would the best IDE be?

---

### Post by japju on 2009-02-05
How's Java and Eclipse. Then there should be no need to port. Not wanted to start language wars, but it is a bit more difficult to write incomprehensible programs in Java than C++ :-)

---

### Post by nvteighen on 2009-02-05
Any interpreted language (Java, Python, Perl, Ruby, etc.) would work... that's one of the reasons these exist.

---

### Post by Martin Witte on 2009-02-05
If you choose C++ (or Python, or many other supported languages), and our program has a GUI it makes sense to use a cross platform available toolkit like [gtk]("http://www.gtk.org/index.php") or [wxwidgets]("http://www.wxwidgets.org/")

---

### Post by nebu on 2009-02-05
java + eclipse!

---

### Post by oasmar1 on 2009-02-05
Well, I really would like to go with C++, since that is the language that I am learning in college, which would be the best toolkit to go with. I want my programs to look native on Windows Vista and Seven, I want to use aero panels and have buttons, search bars etc which match the operating system (I want to use similar search bars to those used in Windows Explorer)

---

### Post by Simian Man on 2009-02-05
> **oasmar1 said:**
> Well, I really would like to go with C++, since that is the language that I am learning in college, which would be the best toolkit to go with. I want my programs to look native on Windows Vista and Seven, I want to use aero panels and have buttons, search bars etc which match the operating system (I want to use similar search bars to those used in Windows Explorer)

wxWidgets would be the best option.  It uses native widgets on Windows and Mac and Gtk on Linux.  I have found it to be really nice for C++ guis.

---

### Post by oasmar1 on 2009-02-05
Ok, thanks, I am looking into that toolkit now, I think, just to make sure, I will provide some more information (I should have done this at the start). Basically, I want to create a light Webbrowser using Webkit (I chose this for my coursework - i thought this would be easier than programming a game which most people seem to be doing). I created a mock up (this was part of the coursework - they compare what you create to the original mock up), this mock up is attached. Now will C++ and Wxwidgets allow me to produce this kind of thing?

[[IMG]http://img87.imageshack.us/img87/7575/browsermockupip5.th.jpg[/IMG]](http://img87.imageshack.us/my.php?image=browsermockupip5.jpg)

Thanks for all the input.
I wont be able to release the source code, until I hand it in and prove that I am the one who is uploading this program - basically, a teacher must see that it is me that is uploading the work and not me just copying someone (one of the conditions I had to agree to so they would let me opensource this.)

---

### Post by nvteighen on 2009-02-06
> **oasmar1 said:**
> Ok, thanks, I am looking into that toolkit now, I think, just to make sure, I will provide some more information (I should have done this at the start). Basically, I want to create a light Webbrowser using Webkit (I chose this for my coursework - i thought this would be easier than programming a game which most people seem to be doing). I created a mock up (this was part of the coursework - they compare what you create to the original mock up), this mock up is attached. Now will C++ and Wxwidgets allow me to produce this kind of thing?

If you refer to the Aero stuff, then don't worry as that is managed by the OS no matter what toolkit you use.

Anyway, if you want Windows's native toolkit, look at their API.

---

