---
title: "manually changing screen dimension in pixels"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by hill0093 on 2008-07-08
I have searched about this, but I can't understand it.

When the amd64 8.04 installation procedure doesn’t set correctly the dimensions of the screen in pixels, what is a simple way to set the dimensions when the correct size does not appear in choices for 
System > Preferences > Screen Resolution 
after installation? 

On another computer, the recommended resolution appears,
but I can’t see the bottom banner unless I change the resolution to another one that appears on the choice list.

I know there are man pages for the commands used on the terminal,
but where is a list of the available commands with short explanations like what is the subject matter of the command?

---

### Post by ZabiGG on 2008-07-08
OK. We need more details. For starters, what kind of monitor (HDTV, flat panel, crt...), and what graphics card are you using. What driver are you using?

This will help us help you better.

Z.

P.S. -- My crystal ball tells me it might be an overscan issue. Are you using an Nvidia 8800 card with a HDTV connected via DVI-to-HDMI by any chance? If so, please click this [link]("http://ubuntuforums.org/showthread.php?t=848822&highlight=dvi-to-hdmi").

---

### Post by hill0093 on 2008-07-10
The video is on the mainboard. 
How do I find out what it is?
There must be a command.
The monitor is an LCD Samsung 17 inch.

---

### Post by ZabiGG on 2008-07-11
Did you try

System > Preferences > Screen Resolution?

It's a standard monitor. It should work. If not, please post the result of the two following commands you need to enter in a terminal (one by one)

glxinfo
lspci | grep VGA

---

