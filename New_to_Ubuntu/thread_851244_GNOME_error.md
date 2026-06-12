---
title: "GNOME error"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by like2program on 2008-07-06
I get this error message whenever I start up:

> There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

Does anyone know what to do?
Sorry for not being very specific but I am kinda a Linux noob.

---

### Post by bumanie on 2008-07-06
Go to terminal (Applications --> Accessories --> terminal) input code > sudo apt-get install ubuntu-desktop hit enter. Type in password, hit enter. Close terminal when install finished. Reboot and see if a reinstallation of the desktop environment worked.

---

### Post by like2program on 2008-07-06
I am assuming you want me to run
> sudo apt-get remove ubuntu-desktop
first because it claims that mine is just fine and doesn't need a reinstall.

---

### Post by like2program on 2008-07-06
Also, though this is irrelivant, why does it want to install tomboy along with ubuntu-desktop?

---

### Post by Troll_the_Great on 2008-07-06
Remove it and then install it again:
```
sudo apt-get remove ubuntu-desktop
```
and
```
sudo aptitude install ubuntu-desktop
```.
It is better to use "aptitude" instead of "apt-get" because you can remove it easier if you want.
Hope this helps.
Cheers!

---

### Post by like2program on 2008-07-06
Nope still get the standard error message.
Any more ideas?

---

### Post by like2program on 2008-07-06
If it helps, my boot up sound plays 1+ minutes after I am logged in.

---

### Post by Troll_the_Great on 2008-07-06
You could try to reinstall the display manager:
```
sudo apt-get remove gdm
```
and
```
sudo apt-get install gdm
```
See if that works.
Cheers!

---

### Post by like2program on 2008-07-06
it did not and firefox just lost all of my settings (wtf?)
Anyways, I need more sugestions.

---

### Post by like2program on 2008-07-06
FYI the firefox thing doesn't have to do with my problem.
Please post an more suggestions.
I will be trying other window managers to see if they work.

---

