---
title: "Slo-o-o-w start up of 11.10"
date: 2011-12-06
forum: New to Ubuntu
---

### Post by ronmlinux on 2011-12-06
I am a newbie to Linux and not much of a computer person.  I started with 10.10 and then 11.04.  For various reasons I wiped my HD clean and reloaded a dual boot of 11.10 and Win Vista.  Now my start up time for 11.10 is like 10 minutes.  If I select "older version of Ubuntu" it will boot up faster but still slow.  Windows boots up fast with a clean new reload, by the way.  One of the good things about Linux is supposed to be faster boots.  Aside from this little glitch, I am a confirmed Linux convert.

---

### Post by LinuxFan999 on 2011-12-06
What are the specifications of your computer?

---

### Post by ronmlinux on 2011-12-06
Pretty new machine - 2.4 GHz Core2 Quad processor, 8GB Ram, 300 GB Hard drive partitions each for Linux and Windoze.  Both earlier version with out dual boot were fast boot-ups.

---

### Post by lolpenguin on 2011-12-07
When you see "Ubuntu" and the Ubuntu logo in the center of a purple background, press an arrow key, then tell us if anything suspicious is happening. Also, try booting into recovery mode.

---

### Post by ronmlinux on 2011-12-07
I tried booting from the recovery mode and got a screen full of 25 lines of text and no further response to the mouse or keyboard.  I had to turn the machine off manually and reboot.
I do not get the ubuntu logo while it is booting up, just the purple screen and then the little login box.:confused::confused:

---

### Post by editheraven on 2011-12-07
What the last line is telling?

Do : ctrl+alt+f1 and login. After that 
xinit and start gdm/kdm and post the output.

le : also do

```
glxinfo|grep render
glxinfo|grep render
ls /etc/X11/xorg.conf
lspci | grep VGA
lspci -nnk | grep -i VGA -A2
```[FONT=Verdana]

and post the output.



[/FONT]> **ronmlinux said:**
> I ...... just the purple screen and then the little login box.
This would mean that your graphical manager runs fine. Anyway, do as i said.

---

### Post by ronmlinux on 2011-12-07
OK - so help me a little bit more here.  As I said, I am a dumb newbie - when DOS lost to windoze I just went along.  But I finally got the guts to say enough of microsoft and now I'm going to be a Linux user and try to learn the basics.

---

### Post by Lamukra on 2011-12-08
I also have the problem with long startup but already on the login screen. When I type in my password and press enter in takes ages to load or it is not loading at all. Using Unity 3D With Xpress 1250(RS600), Gallium 0.4, direct rendering enabled and KMS working properly...

What to do?

---

### Post by ronmlinux on 2011-12-09
OK - I tried as best I could the suggestions of EDITHERAVEN.  No improvement, still takes 9 minutes to boot.  I got responses that the code was not recognized.:confused:

---

### Post by wildmanne39 on 2011-12-09
Hi, editheraven was asking you to run each of those commands one at a time and post the output here so we can have a look at it, it was not commands that would fix the problem but give us information that might help fix it.
Thank you

---

### Post by ronmlinux on 2011-12-11
Thanks, I will try that this evening.:confused:

---

### Post by ronmlinux on 2011-12-15
I finally got around to some of edithravens help.
When I do ctrl-alt-F1, login and type xinit response is:
Fatal server error:  and other text.
I tried Ctrl-alt-t while in 11.10 and typed xinit  response is:
X: user not authorized to run the X server, aborting.
After in between text both said:
XIO: fatal IO error 11 (resource temporarily unavailable) on X server ":0" after 7 requests (7 known processed) with 0 events remaining.

tried start gdm - response
start: Rejected send message,/matched rules; type "method_call" and more text
glxinfo | grep render
Error: unable to open display
ls /etc/X11/xorg.conf
ls: cannot access /etc/X11/x.org.conf: No such file or directory
lspci | grep VGA
01:00.0 VGA compatible controller: ATI RV770 (Radeon HD4850)
lspci -nnk | grep -i VGA -A2
01:00.0 VGA compatible controller[0300]: ATI RV770 (Radeon HD4850)[1002:9442]
Subsustem: Dell Device [1028:0502]
Kernel driver in use: radeon:confused::confused:

---

