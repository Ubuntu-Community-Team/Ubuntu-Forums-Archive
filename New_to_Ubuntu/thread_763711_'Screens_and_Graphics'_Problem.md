---
title: "'Screens and Graphics' Problem"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by vkennedy85 on 2008-04-23
Hey all, I just recently (3 weeks ago) installed Gutsy to dual boot on my laptop.  Yesterday I had played around a little with my screens and graphics options to try and increase the resolution so that things didn't appear so big on my desktop.

Long story short I totally snockered it and now I see about 8 desktops overlapping and it's all messed up.  How can I change these settings in recovery mode?

Also, what is the best way to find out exactly which drivers I should be using for my monitor(s)? I'm running a Dell Inspiron 1300 17" standard Laptop Display and I like to hook it up to my Sony Bravia 32" LCD TV.

---

### Post by PmDematagoda on 2008-04-23
You should be able to restore the X-Server settings by executing:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by hermes0710 on 2008-04-23
> ...8 desktops overlapping...

What do you mean?

You can manually edit ```
 sudo /etc/X11/xorg.conf 
``` and fix the changes made to resolution.

---

### Post by vkennedy85 on 2008-04-23
> **hermes0710 said:**
> What do you mean?

You can manually edit ```
 sudo /etc/X11/xorg.conf 
``` and fix the changes made to resolution.

I'm a relative n00b at Linux systems, so manually editing the xorg seemed risky to me (that and I coudln't find it).

It is kind of tough to describe, but you know how the old premium channels would look really wavy and distorted?  That's kind of what my screen looked like, except I could 10 different pointers, like the screen was fuzzed out and then shifted over an inch 10 times.  Imagine copy and pasting it with 50% opacity and shifting an inch 10 times.

I'll try the xserver command, thanks.

---

### Post by hermes0710 on 2008-04-23
Ok, I understand.
  If trying out the command doesn't work , most probably, in /etc/X11/ folder a backup of xorg.conf logically exists... You can save your current configuration to a temporary file and rename the backup file to "xorg.conf" in order to roll back to your previous settings. (With the xserver not running: "sudo /etc/init.d/gdm stop")

---

### Post by cstyve on 2008-04-23
> **vkennedy85 said:**
> I'm a relative n00b at Linux systems, so manually editing the xorg seemed risky to me (that and I coudln't find it).

It is kind of tough to describe, but you know how the old premium channels would look really wavy and distorted?  That's kind of what my screen looked like, except I could 10 different pointers, like the screen was fuzzed out and then shifted over an inch 10 times.  Imagine copy and pasting it with 50% opacity and shifting an inch 10 times.

I'll try the xserver command, thanks.
I've done this many times to my macine trying to get optimum resolution with  video card and screen.

The problem is that xserver - which handles all screen/mouse/keyboard related stuff is initializing your monitor to an incorrect refresh rate.  Like I said...been there - done that.  So how do you reset....

Restart ubuntu and when the boot manager, called Grub, starts select the option that says safe mode. Once you log in start a terminal window (from the Accessories menu option) and type in the following command then restart ubuntu.

sudo dpkg-reconfigure -phigh xserver-xorg

xserver reads all its configuration information from a file called xorg.conf and is located in the /etc/X11 folder.  It's a text file so you can review it.  Take a look at it and get familiar with it as you may need to manually changes settings at some point.

If you complete mess up settings the xorg.conf xserver will warn you and ask if you want to start with a "low resolution" safe mode.   Unfortunately, setting the monitor to an invalid horizontal refresh rate doesn't seem to qualify as a situation that's messed up from xserver's point of view.

---

### Post by vkennedy85 on 2008-04-23
Thanks for all the help.  I don't have safe mode I can boot to, just normal and recovery, but recovery still gives me the command line so I can I do most things.

I'll let you all know how it goes, thanks again.

---

### Post by vkennedy85 on 2008-04-24
That fixed it for me, thanks (resetting my xserver)

---

### Post by Can+~ on 2008-04-24
Please add tags to this subject!

---

