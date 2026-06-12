---
title: "xorg.conf - missing?"
date: 2012-12-15
forum: New to Ubuntu
---

### Post by Awalrath on 2012-12-15
I understand this thread is closed. 

However I also have a missing /etc/x11/xorg.conf missing
I completed the first step however after typing 
sudo mv xorg.conf.new /etc/x11/xorg.conf

it tells me there is no file to move.
I know I have typed the step before correctly as I have done it many times now.

Also the computer was working just fine, xorg.conf and all until two days ago, now when booting I get that message and it cycles back to grub menu.

Any help at all would be nice as I am afraid with ubuntu I am in over my head.

Annie

---

### Post by cariboo on 2012-12-15
I'm not sure what it is you are trying to do, but the original thread this post was in is closed. It would help if you explained the problem again.

BTW, /etc/X11/xorg.conf is generally not needed any more, and should be used only in really special cases.

---

### Post by Awalrath on 2012-12-15
I do realise it was closed, however since I was following those steps I assumed it would be easier for all involved to post the question here.

The computer is an hp mini 210 1040 nr which is a netbook. (or rather laptop with no cd drive)
Running ubuntu 11 (? I believe, could be 11.4) 

Its been running ubuntu since maybe 2010 (possibly later), not to sure.  It is my brothers computer and he doesnt want/ feel the need to give me any real information about it.  I mostly work with windows so I am unsure how to really read what ubuntu is telling me.

In order to start the ubuntu on his computer you have to go to use recovery mode from the grub menu then scroll down to failsafe graphic then it scrolls some text and finally you get to the desktop. (I assume thats a driver problem with the graphic card but, have never used the computer so I am unsure)

Well yesterday it started just scrolling through text and coming back to the options 
(root, graphics mode thing, that whole menu)
the only error I have managed to catch is it saying /etc/X11/xorg.conf is not there.
I assumed that would have to be the problem so I have attempted to fix it the way it states above.  However I cant get it to generate a new file for me to move.

Again I know this is closed but, I figured instead of coping and pasting the full sets above in a new thread it would be better posted here.

---

### Post by Awalrath on 2012-12-16
Any ideas at all would be helpful.

---

### Post by Paqman on 2012-12-16
You should be able to get booted into a command line, and we can do some diagnosis from there.

[LIST]
[*]At the boot menu select the option called "recovery mode", "advanced" or similar (it depends what version you're on)
[*]At the next menu select the option "drop to a root shell prompt", or words to that effect
[/LIST]

While your there, enter:
```
lsb_release -a
```
and it will tell you which exact version you've got.

---

### Post by 3rdalbum on 2012-12-16
Two things:

It's /etc/X11/xorg.conf, not /etc/x11/xorg.conf.

Xorg can start with no conf file. If you need one to edit, make sure X is not running and type:

sudo X --configure

A new xorg.conf file will bee created in the current directory.

---

### Post by grahammechanical on 2012-12-16
Hi, might I ask what you see if you try to load Ubuntu from the usual way and not with Recovery Mode? That might give some information as to what is wrong in the first place.

I find that I can sometimes get to a desktop (Ubuntu loaded) by selecting Recovery mode and then Resume. This loads Ubuntu without using a proprietary video driver. It uses the Open source (Nouveau) driver instead.

You then might look for the Additional Drivers Utility. You might need to install or re-install the proprietary driver. I have not used 11.04 for a year so I cannot give you directions. The way things are done have changed since 11.04 was released. Sorry.

The one and only time my computer went into failsafe - low graphic mode was because the graphic adapter/card was overheating and so breaking. You might want to make sure there is plenty of ventilation getting inside this Netbook.

Regards.

---

