---
title: "Multiple Instances.."
date: 2008-08-11
forum: New to Ubuntu
---

### Post by wannapiece on 2008-08-11
Hello all, I am a new user to Ubuntu Hardy via Wubi and so far I love it.  I just get everything updated and wifi working on my laptop which I thought wouldn't be able to happen, so now I want to "make the switch"

I do however have one very important question...  **How do I allow multiple instance of a program?**

I am running SecondLife and usually run 2 clients simultaniously for beta testing, in windows to allow multiple instances of a program you add "-multiple" on the end of the target path, however I do not know how to do that yet in Ubuntu.

I would greatly appreciate anyone that could help me on this matter, thank you!

---

### Post by loboc on 2008-08-11
stupid question:
have you tried just running it twice

secondlife&

secondlife&

---

### Post by wannapiece on 2008-08-11
This is what I get when I attempt to run the program twice

> Second Life is already running.

Check your task bar for a minimized copy of the program.
If this message persists, restart your computer.

---

### Post by wannapiece on 2008-08-11
Okay I found on support wiki on Secondlife to do this...

>   Linux

   1. Find the file gridargs.dat in the Second Life installation directory
   2. Edit the file and add '-multiple' 

I can't open the .dat file because it is set to a group and owner of 1052 in my usr/share/games/SecondLife

I've tried copying the file to desktop to try and replace it, but I'm going to try to uninstall (originally installed with .deb) and reinstall in another location...

---

### Post by Dylock on 2008-08-11
Woah there dont reinstall. You just need to use sudo when you edit the file.

Open up a terminal and type ```
 gksudo gedit /usr/share/games/SecondLife/gridargs.dat 
```

Make your changes and then save.

---

### Post by wannapiece on 2008-08-11
Awesome, Thank you Dylock

I was sketchy about what to do because the file specified was blank, I wasn't sure if it was a read error or something else.

I just typed in -multiple in the empty .dat file and now I have multiple client goodness!

Thx so much for your help

---

