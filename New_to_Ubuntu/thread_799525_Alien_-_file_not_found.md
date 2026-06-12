---
title: "Alien - file not found"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by 2CV67 on 2008-05-19
Hi guys!

Trying to get my Epson scanner to work in Gutsy, I am following a thread on that subject, which tells me to download RPM files (done OK & checked md5 OK).

It then tells me to convert to deb package using alien (installed OK) using:
sudo alien iscan-2.8.0-1.c2.i386.rpm

When I do this, I get:
chris@DESKTOP:~$ sudo alien iscan-2.8.0-1.c2.i386.rpm
File "iscan-2.8.0-1.c2.i386.rpm" not found.
chris@DESKTOP:~$ 

I originally had the rpm file in a folder on the desk, then tried putting the file directly on the desk, then tried copying the file name directly from file properties (looked the same, but...) but always same result.

I guess I missed something.

A little advice would be greatly appreciated!

Thanks!

---

### Post by HotShotDJ on 2008-05-19
If the file is still on your desktop, then simply execute the command ```
cd Desktop
``` then run the other commands.

---

### Post by 2CV67 on 2008-05-19
Thanks! :oops:

I promise to do Terminal 101 again immediately!

Actually, I hate terminal (as you can tell by my signature).
Your "cd desktop" gave :
chris@DESKTOP:~$ cd desktop
bash: cd: desktop: No such file or directory
chris@DESKTOP:~$

so I needed "cd Desktop"....

I look forward to a GUI Ubuntu!

Thanks again :)

---

### Post by angry_johnnie on 2008-05-19
Hi there.

It's cd **D**esktop. :-) Linux is case-sensitive.

A few weeks ago, I found [this]("http://ubuntuforums.org/showthread.php?t=311255").

It will take some terminal commands to get it done, but after that you'll be able to right-click-convert rpms much easier. :-)

And, don't hate the terminal... she's your friend :-)

P.S.  In that how-to I linked to, they tell you to

```
~/.gnome2/nautilus-scripts/alien-this
```

but it should be

```
gedit ~/.gnome2/nautilus-scripts/alien-this
```

Good luck.

---

### Post by HotShotDJ on 2008-05-19
> **2CV67 said:**
> Actually, I hate terminal (as you can tell by my signature)...

...I look forward to a GUI Ubuntu!Remember, the command line will ALWAYS be more powerful than the GUI.  In a GUI, you only get to do what the programmers think you ought to be doing.  In the command line, you get to be the programmer. :)

---

### Post by 2CV67 on 2008-05-19
Oh yes, of course I realize that command line is infinitely more powerful and efficient for full-time professionals, alert nerds and other smarties ;) but it is an ergonomic disaster for the other 99% of the population, especialy retired old geezers like me! (And I have been a programmer...)

I don't need to be able to get the exact pared-down result in nanoseconds; I need to be able to click steadily through to where I want to be without having to wade through a thick manual first and without risk of destroying everything by one false keystroke.

I would like to see an independent check on "efficiency" comparing random "dummies" like me (not experts) trying to use command line vs GUI.

I am happy to let you guys use command line, but I badly need GUI.

So does Ubuntu.

...and no - I don't want to stick with Microsoft!

Sorry if this is now a bit off-subject!

Thanks for being a great bunch of helpful guys!

---

