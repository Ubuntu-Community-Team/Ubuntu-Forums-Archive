---
title: "Linux --&gt; Windows"
date: 2006-11-05
forum: Programming Talk
---

### Post by hamil on 2006-11-05
Hello!

I have been helping out on translating different projects to my native spoken language for some time now.
One of the project managers, asked me, since I also had Windows on one of my machines, if I maybe would be interested in making a Windows port of his application.
I am very interested in helping out in any way I can, and maybe also learn something new while I do the work. I said that I would look into it, and maybe find some howtos etc to read and learn from. 

Well, now my problem seems to be that I do not find the howtos I had hoped existed.. :) This is where I hope some of you can help...

The application I am trying to compile for Windows and make a simple exe file from (so that I could double click to install it completely on my Windows machine), depends on two other programs/libraries. It has ./configure and make scripts included in a tarball, and there is also .deb versions available for all the necessary applications.

How do I do this? I have read the howto [wiki.njh.eu](http://wiki.njh.eu/Cross_Compiling_for_Win32), but did not understand what I was supposed to do...

If someone would have mercy, and guide me through this, preferably in a step by step guide, it would be highly appreciated.. Links to other howtos etc is also welcom! ;)

---

### Post by Houman on 2006-11-06
hi there,

I am not sure exactly what is the solution to your problem, but if you want to know how to compile and create windows programs you need to install mingw cross compiler on your ubuntu machine (assuming thats the distro that  you have) using :

```

sudo aptitude install mingw32

```

afterwards you can easily compile win32 code and create windows executables, but instead of using gcc, you got to use  "i586-mingw32msvc-gcc" as your compiler.

Also install [wine]("https://help.ubuntu.com/community/Wine") to run those executables if you dont have windows.

However, I think best thing would be to try to follow the tutorial and then ask specific questions about where you had difficulties, that way it will be much easier for forum members to help you.

regards

Houman

---

