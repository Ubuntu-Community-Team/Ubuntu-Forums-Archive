---
title: "video is a scrambled mess"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Linux Kelley on 2008-04-30
Hey Folks,

I would like to switch over to Ubuntu from XP but I cannot get the Display to work correctly.

When I use a live CD the video is a scrambled mess.
When the CD Starts I can see all the options and when I select Live CD I can see the Unbuntu name and logo as it is booting up.
However when it gets to what s/b the login in screen the video is totally scrambled.

I have tried 7.04 and 7.10 amd 8.04.

I am using an NVIDIA FX 5500 and an ACER WXGA 22" flat screen.

Thanks!

Kelley

---

### Post by it.henrik on 2008-04-30
I dont have your graphics card so I dont have the same problem, but have you had a look in this thread?

[http://ubuntuforums.org/showthread.php?t=767854&highlight=NVIDIA+FX+5500](http://ubuntuforums.org/showthread.php?t=767854&highlight=NVIDIA+FX+5500)

---

### Post by Linux Kelley on 2008-04-30
> **it.henrik said:**
> I dont have your graphics card so I dont have the same problem, but have you had a look in this thread?

[http://ubuntuforums.org/showthread.php?t=767854&highlight=NVIDIA+FX+5500](http://ubuntuforums.org/showthread.php?t=767854&highlight=NVIDIA+FX+5500)

Thanks for pointing that thread out, but I'm afraid his problem is not the same as mine. On my screen there is nothing recognizable. I don't even get as far as the other poster did.

---

### Post by it.henrik on 2008-05-01
When you get as far as what should be the login screen try to press

CTRL+ALT+F1

This will give you a login prompt to the shell, from here you can run commands to configure the x-server etc.

---

### Post by anewguy on 2008-05-01
Okay, I'm going to suggest something here, but someone else who actually knows this will have to provide the details IF it is something that might work.

Your problem is that the resolution and the refresh rates don't match up, hence the scramble.  There is a way at boot (maybe F6, but I don't know if this works off the livecd) where you are allowed to edit the boot line, and I think it is something like VGA=774 or something like that that you have to add to get it to boot.  I could be wrong about that.

It's funny to me, previously in the forum the suggestions from everyone was to get an nVidia based card, not ATI, because the ATI's are difficult to get working.  For me, it's been the opposite.  I've run into the same problem you talk about with 2 separate nVidia based cards.  I put in an ATI 9250 and it worked right away.  Go figure.

BTW - the link given to go into terminal and get envy is not invalid.  The black screen mentioned in that post is just another symptom of driver problems.

I would tell you to boot to a terminal session and then download and run envy and even xserver-xorg reconfigure, but since you are having problems on the LiveCD at boot, those options don't really mean much.  If you really want to install, I would:

(1) download, burn and install the alternate cd (it's just a checkmark on the regular download page)

(2) boot the new install.  If the screen is still messed up, do ctrl-alt-F1 to get to a terminal window login.  Once in that terminal window, start up the network (post back if you need instructions), download and install envy, then run envy. (You might consider downloading the package for Envy in Windows first and putting it on a CD or other medium [can include your hard disk] so you have access to it in Ubuntu).

I strongly recommend trying that.  All the other suggestions really don't matter until you actually get Ubuntu installed.  The alternate CD doesn't use "graphics" mode - it uses the old "terminal" graphics in text mode.

Let us know how it goes! :)

---

