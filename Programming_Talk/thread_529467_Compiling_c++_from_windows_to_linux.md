---
title: "Compiling c++ from windows to linux?"
date: 2007-08-19
forum: Programming Talk
---

### Post by Hopeless on 2007-08-19
Hi,

I'm trying to compile a windows c++ program  from  

[http://opensvn.csie.org/s1mp3/s1fwx/](http://opensvn.csie.org/s1mp3/s1fwx/)

its for all S1mp3 players (the chinese ones on ebay - mp3 players) is it possible to do?

i downloaded g++ and mingw32..

Can anyone suggest how this application be ported to linux? it dosent work under wine...

thanks...

---

### Post by badactress on 2007-08-19
'fraid it's not just a case of compiling it under Linux. It uses the Windows  GUI library for it's front end for a start, so you're going to need to re-write that part of the code to use the Gnome GTK instead. Chances are there is more Windows-only code in there that would need converted too.

It can be done! It's just not quite as simple as running it through a compiler in Linux and a Linux application appearing!

:(

---

### Post by Hopeless on 2007-08-19
Any good web sites for converting windows gui to linux?

---

### Post by rbprogrammer on 2007-08-20
i'm not an expert in windows programming or gtk+ programming, but i'm sure your probably just going to have to learn how your that program works, and then learn gtk+.  then you would have to go through that code line by line and make the necessary modifications.

i'm not an expert, but i know there it's not going to be as easy as a simple converter.  sometimes you cant just convert a line from windows API to gtk+.  example: a few lines of windows API might convert to one line of GTK+ and vice versa.

:( sorry its not as easy as it first might of seemed

---

