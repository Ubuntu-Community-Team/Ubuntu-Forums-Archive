---
title: "Programming Language for ubuntu"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by Manish555 on 2013-04-28
Hi There,

i need your input on which out of these two is a  better programming language to develop apps for Ubuntu platform? (JAVA  vs Python).I have knowledge of java,but i am a completely newbie to python programming language.Also i was thinking on porting the same app to the mobile(ubuntu) platform too.which language would be better?



-Regards

---

### Post by deadflowr on 2013-04-28
You should installl quickly.
I think it uses python though. Not sure, don't care.

Looky here:
[https://wiki.ubuntu.com/Quickly](https://wiki.ubuntu.com/Quickly)

---

### Post by johncroc on 2013-04-28
I am both a Java and Python programmer (30+ yrs app dev exp, on many, many platforms and languages).  I haven't used Java for a number of years though and have spent the last four learning Python.  I should mention that I'm no longer a full-time programmer so when I say, "spent the last four learning Python," that's been at the rate of 5-10 hours per week.

I am beginning to like Python, although that has been a LONG time coming.  First Python is not a "strongly typed" language and I'm old school so that took a lot of getting used to.  Also, if you start down the Python road you'll see that there is something called the "pythonic" way of doing things.  This comes from the idea that Python is a pretty radical departure from the programming norms any of us old-timers are used to.  I did some projects in Python and after having used it for about a year I decided to go back to basics and watch some tutorials on YouTube (check out "thenewboston"), so I could try to understand this "pythonic" thinking.  Things have been MUCH easier since then, so I suggest starting there.

Also, get the Eclipse IDE, you can find it in the Ubuntu software center.  It will make your life tons easier, as it enables you to set breakpoints, step through your code, etc.

Hope this helps.  I probably have more to say, so I'll keep an eye on this thread and add to it if I think of anything else.

---

### Post by johncroc on 2013-04-28
I thought of another couple of things that might not be obvious:  Python's interpreter is pretty bare bones so your code will be heavily reliant on Python modules such as numpy, scipy, etc.  I use matplotlib for plotting.  My point is that at least a summary understanding of some of the basic modules ("os" comes to mind) will go a long way.  Be sure you spend some time learning about the available modules before you get frustrated trying to figure Python out.

Also, all my machines are fully 64-bit; primarily so I can address a lot of RAM and hard drive space.  So when I installed Python I went out and found 64-bit versions of everything.  Then about a month later I realized there was a module that I had not gotten and went out to find a 64-bit version, but couldn't...which basically meant I had to uninstall EVERYTHING Python 64-bit-related and install all the 32-bit versions.  Took me a few hours, no big deal, but you can save the hassle by just going 32-bit in the first place.

I might also recommend going with Python 2.7 (not 3.x).  2.7 seems to be more stable and better supported in terms of forums and literature (if you end up buying a reference book).

---

### Post by Manish555 on 2013-04-29
Look,i am always ready to learn a new programming languaguage such as python,IF apps written in them(python) run better on ubuntu platform.At the first place i am really sorry for not being clear about what i am trying to achieve here.I am planning to build a voice recognistion app for the ubuntu platform which makes use of google voice server.what language according to you is a better way to go about? Which is a BETTER programming language(JAVA  vs Py) to develop apps like voice recognistion on ubuntu platform and by the way the apps is GUI based!

---

### Post by Manish555 on 2013-04-29
Thank you so much for the reply.

Look,i am always ready to learn a new programming languaguage such as  python,IF apps written in them(python) run better on ubuntu platform.At  the first place i am really sorry for not being clear about what i am  trying to achieve here.I am planning to build a voice recognistion app  for the ubuntu platform which makes use of google voice server.what  language according to you is a better way to go about? Which is a BETTER  programming language(JAVA  vs Py) to develop apps like voice  recognistion on ubuntu platform and by the way the apps is GUI based!

---

### Post by Cheesemill on 2013-04-29
The official Ubuntu SDK for mobile apps is based on QT5 and QML.

All the resources you need to start with can be found on the Ubuntu developer site...
[http://developer.ubuntu.com/get-started/gomobile/](http://developer.ubuntu.com/get-started/gomobile/)

---

### Post by Manish555 on 2013-04-29
> **Cheesemill said:**
> The official Ubuntu SDK for mobile apps is based on QT5 and QML.



Thank you for the reply.Okay so if i start writing programs on python,would it be possible to make QML language talk to programming language such as python? i.e i would design the app using QML and process the data/request using language such as Python

---

