---
title: "How to install themes for GRUB2?"
date: 2011-11-29
forum: New to Ubuntu
---

### Post by longcheeze on 2011-11-29
Can anyone show me how to install the themes from this site,
[http://grub.gibibit.com/](http://grub.gibibit.com/).  Was unable to find instructions on site.

Will installing the themes make my GRUB2 fonts bigger when choosing which OS to login to?

Thanks.

---

### Post by jjex22 on 2011-11-29
Hi there, okay gonna warn you from the off this is pretty much the most complicated thing you're gonna do with linux short of writing programs. That website is actually a guide on how to do it - in documentation, that massive blue section of commands is the winter theme. This was a summer of code project to see what was possible.

Grub, like everything in linux is a program reading a text document to tell it what to do - so you have to edit those documents with text commands for EVERYTHING you want it to do - which is why people were so happy when we got grub 2 and got sudo update-grub.This is a massive pain and short of just copying that winter theme, is going to take forever if you don't know what you're doing - hexadecimal colors etc.

For most of us (including the guys that make the distro's) it's enough to change the splash image (and if you want to resize things, follow [this]("http://linuxconfig.org/change-tty-font-size-with-grub-2-boot-console-resolution"))

To get more info on how grub is configured and ho to personalise it, please see this [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) - be sure to make a copy of any text document you edit before you edit it - that way if you stuff up you can just copy it back! But yes the section about splash images is about 3/4 of the way down.

Sorry I couldn't be more help, but I hope you can see why.

---

### Post by grahammechanical on 2011-11-29
If you want to put a background image behind the Grub menu and/or change the font size as well as change the menu order, then do these two things:

1) Install Grub customizer.

2) Install grub2-splashimages from the Ubuntu Software Centre.

Here is the link to Grub customizer:

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

I keep that link bookmarked. I use this utility. Another utility you might want to look into is Simple LightDM Manager

[http://www.ubuntugeek.com/simple-lightdm-manager.html]("http://www.ubuntugeek.com/simple-lightdm-manager.html")

I have used this to change the LightDM greeter background to one of the desktop background images. The latest version helps you edit the greeter logo. It puts the logo image (logo.png) into its .simpleLigtDMManger folder (yes that is the folder name and not my spelling mistake). By editing logo.png or creating you own logo.png and putting it in that Simple LightDM Manager folder you change the logo in the greeter.

I like it.

Regards.

---

### Post by Frogs Hair on 2011-11-29
Here is a link , but it is dated like the one in the original post . I too would leave well enough alone . A nice view in grub is not worth breaking a system for , but that's up to you . [http://www.webupd8.org/2009/11/customizing-grub2-ubuntu-linux.html](http://www.webupd8.org/2009/11/customizing-grub2-ubuntu-linux.html)

---

### Post by drs305 on 2011-11-29
As has been mentioned, theming is still not the easiest thing to do with Grub 2. 

If you are using Grub 2 version 1.99 (Natty and later) then adding a background image is very easy. Changing font colors is a bit trickier but still not too difficult. Here is a link to a guide to accomplish these tasks:
[Grub 2 Drop-In Backgrounds & Font Selection]("http://ubuntuforums.org/showthread.php?t=1739412")

---

### Post by fleamour on 2011-11-29
You may want to consider Burg which is a graphical overlay atop Grub:

[http://www.ubuntugeek.com/super-boot-manger-make-easier-and-intuitive-configuration-of-grub-burg-and-plymouth.html](http://www.ubuntugeek.com/super-boot-manger-make-easier-and-intuitive-configuration-of-grub-burg-and-plymouth.html)

---

### Post by cortman on 2011-11-29
Go with Burg. It'll get you just what you're after (from looking at the linked site) and it's very simple. It was one of the first things I did in Ubuntu, just for fun, and it worked quite well.

---

### Post by Cavsfan on 2011-11-29
There is a link in my signature for making a background picture and changing the colors as well as the font size.

It is good for dual booting and I don't have to do anything when a new kernel is installed.

It's pretty straight forward but, a lot of detail.

---

