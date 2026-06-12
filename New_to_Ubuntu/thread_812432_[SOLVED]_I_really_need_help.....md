---
title: "[SOLVED] I really need help...."
date: 2008-05-29
forum: New to Ubuntu
---

### Post by jjblackfox on 2008-05-29
Hi, I am a brand new linux user and I desperately need help.
I installed Linux and broke it about 4 times and I had to re install it all over (Messed up in the terminal trying to install themes and compiz).
I finally got it to work the way I want it to (with Compiz and AMV) and I mess it up again. Without thinking, I blindly followed this tutorial:

{Now comes the tricky part, because the remaining panel can't be deleted. So, go to System -> Preferences -> Sessions and click the second tab, "Current Session". Click once on the gnome-panel entry in that list and then hit the 'Remove' button to delete the last remaining panel. Then, click on the "Session Options" tab and check the 'Automatically remember running applications when logging out' option and hit the 'Remember currently running applications' button. Close the Sessions window and reboot the computer.}

So I pretty much just deleted my toolbar that lets me run stuff. The only way that I could even get on here to ask this question is by creating an empty html document that I open in firefox so I could get on the internet.
My toolbar on the top is gone and I don't know how to get it back and I really don't want to have to re install linux, what should I do? I didn't back it up yet and I am running Ubuntu Hardy Heron 8.04

---

### Post by quelx on 2008-05-29
can you do **ALT-F2** then type **gnome-panel**?

---

### Post by jjblackfox on 2008-05-29
> **quelx said:**
> can you do **ALT-F2** then type **gnome-panel**?
I tried that, but Alt+F2 doesn't do anything. 
Thanks for the quick response though.

---

### Post by quelx on 2008-05-29
**CTRL-ALT-F1** then login and type **export DISPLAY=:0** then **gnome-panel** then **ALT-F7** to get back to Gnome

---

### Post by jjblackfox on 2008-05-29
> **quelx said:**
> **CTRL-ALT-F1** then login and type **export DISPLAY=:0** then **gnome-panel** then **ALT-F7** to get back to Gnome

When I hit Ctrl alt F1, my screen goes blank and I can't see anything,including my text. I remembered that I put in a shortcut to get to the terminal and I typed:

 sudo dpkg-reconfigure gnome-desktop-environment


It gave me the following error:
Package `gnome-desktop-environment' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: gnome-desktop-environment is not installed

---

### Post by tamoneya on 2008-05-29
i believe you are thinking of ubuntu-desktop.  It however is already installed.  Hit ctrl-alt-F7 to get back to it.

---

### Post by jjblackfox on 2008-05-29
> **tamoneya said:**
> i believe you are thinking of ubuntu-desktop.  It however is already installed.  Hit ctrl-alt-F7 to get back to it.

Hitting ctrl alt F7 doesn't do anything for me. 
[http://tinypic.com/view.php?pic=1247j4j&s=3](http://tinypic.com/view.php?pic=1247j4j&s=3)
That is a picture of my desktop. I am missing the toolbar that is at the top.

---

### Post by quelx on 2008-05-29
in the terminal run **gnome-panel**

to reconfig **sudo dpkg-reconfigure ubuntu-desktop** is what tamoneya was saying

---

### Post by jjblackfox on 2008-05-29
> **quelx said:**
> in the terminal run **gnome-panel**

to reconfig **sudo dpkg-reconfigure ubuntu-desktop** is what tamoneya was saying

Oh, it works now! Thanks everyone for your patience. I really appreciate the help.

---

### Post by jjblackfox on 2008-05-29
How do I mark the problem as solved?
[edit] got it. Thanks again everyone.

---

