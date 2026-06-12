---
title: "Complete Lock Up, where to start?"
date: 2012-03-04
forum: New to Ubuntu
---

### Post by DGINSD on 2012-03-04
I had something odd happen yesterday and its the second time its happened to me, I figured the first time was a fluke, both times it's occurred I was using Gnome shell. Basically the system completely freezes up no keyboard to touch pad no nothing, basically I end up having to force a power down and restart by holding down the power key.

Where do I begin to trouble shoot this issue, what log files should I take a peek at? I really don't even know where to begin with this one. 

I feel I should mention this as it could be related every once in a while I'll get a blank screen, or my open windows will reload, again this only seems to happen while using Gnome shell. It's as if it gets confused as to what it supposed to be displaying but then quickly figures it out puts everything right.

---

### Post by 2F4U on 2012-03-04
Here is a list of the available log files:

[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

You should start with systemlog, Xorg.0.log.

---

### Post by DGINSD on 2012-03-07
Ok I dug through the logs a bit but didn't find anything, I need a little more help on what to look for? I've been using unity lately and it's been flawless so I think the issue has something to do with gnome shell. 

I doing a thread in desktop environments that seemed like a similar issue, without the screen blanking and window reloading. Their issue was solved by turning off "disable touch pad while typing", I'll give that a whirl tonight, but that is a feature I actually use so it's not really a great fix for me.

Any help with this is appreciated.

---

### Post by Tony Flury on 2012-03-07
The "disable touchpad when typing" setting is not as bad as you think - you can still use the touch pad - it just stops you inadvertantly "tap clicking" or "cursor moving" while you are actually typing on the keyboard. Stop typing for a second (well less than that), and you can use the touchpad.

---

### Post by jerrrys on 2012-03-07
I wonder if the package "lightdm" is giving you trouble.

 [https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

---

### Post by DGINSD on 2012-03-07
> **Tony Flury said:**
> The "disable touchpad when typing" setting is not as bad as you think - you can still use the touch pad - it just stops you inadvertantly "tap clicking" or "cursor moving" while you are actually typing on the keyboard. Stop typing for a second (well less than that), and you can use the touchpad.

Sorry I may not have explained myself right. I'm a chronic tap clicker/courser mover so I need to use the disable touchpad. The other thread suggested disabling it as a fix to a similar issue.

---

### Post by DGINSD on 2012-03-08
> **jerrrys said:**
> I wonder if the package "lightdm" is giving you trouble.

 [https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

So how can or should I trouble shoot it? I read the wiki but there's no info on common issues. I could switch back to gdm but what issues will that cause.

Being a rather random problem makes it hard to track down.

---

### Post by bronquel on 2012-03-08
You might try the skinny elephant trick.  It is a way to regain control of a frozen system.

look at step 5 of this post:
[http://lxtips.posterous.com/recover-an-unresponsive-linux-system-with-alt](http://lxtips.posterous.com/recover-an-unresponsive-linux-system-with-alt)


Sometimes you can also get to a virtual terminal by pressing ctrl-alt-F1 and then using ps or top to kill the offending process(es), and then pressing ctrl-alt-F7 to get back to your desktop.  maybe this trick will let you see what process is causing the problem.

---

### Post by Immolatus on 2012-03-08
Are any of the lights flashing on the machine? This usually indicates "kernel panic". The most common cause I've seen with Linux is graphics driver issues. try turning of the desktop effects.
Also if you can do: Ctrl+Alt+F1 
and it drops to tty1 then that means X is crashing (also gpu related) not kernel panic.
What is the make and model??

---

### Post by theducksfan2010 on 2012-03-08
> **bronquel said:**
> You might try the skinny elephant trick.  It is a way to regain control of a frozen system.

look at step 5 of this post:
[http://lxtips.posterous.com/recover-an-unresponsive-linux-system-with-alt](http://lxtips.posterous.com/recover-an-unresponsive-linux-system-with-alt)


Sometimes you can also get to a virtual terminal by pressing ctrl-alt-F1 and then using ps or top to kill the offending process(es), and then pressing ctrl-alt-F7 to get back to your desktop.  maybe this trick will let you see what process is causing the problem.

I wish I would have seen this a while ago, I was having this issue recurring on a old load of Ubuntu 11.10. Eventually I have had to reload (due to other reasons) and it has not resurfaced yet. This will be very useful if I run into it again.

---

### Post by theducksfan2010 on 2012-03-12
> **bronquel said:**
> You might try the skinny elephant trick.  It is a way to regain control of a frozen system.

look at step 5 of this post:
[http://lxtips.posterous.com/recover-an-unresponsive-linux-system-with-alt](http://lxtips.posterous.com/recover-an-unresponsive-linux-system-with-alt)


Sometimes you can also get to a virtual terminal by pressing ctrl-alt-F1 and then using ps or top to kill the offending process(es), and then pressing ctrl-alt-F7 to get back to your desktop.  maybe this trick will let you see what process is causing the problem.


So when I left for Fresno today to go hook up the in-laws computers I just rebuilt (XP) my laptop was doing a update - upgrade in the terminal in Bodhi Linux (Ubuntu based, and had been doing this for quite a while. I just got back to find it all locked up and did the skinny elephant trick from your link to no success, I tried twice. Left wherith no choice but to do a hard kill, and now when try trying to boot it up it starts the load process and then just stays on a blank screen. Am I hosed, or is there anything I can do to try and get this up and running again. No luck in the Graphics Failsafe mode either, although it does progress further with the last 2 lines showing being:

[   2.779366] scsi 2:0:0:0: Direct-Access    Ut165    USB2FlashStoragen0.00 PQ: 0 ANSI:2
[   2.782181] sd 2:0:0:0: Attached scsi generic sg0 type 0


I had an update crash in the terminal in Lubuntu  11.10 before and know that there was a command I had to run int the terminal before I was able to use the Synaptic Package Manager again, but I can't get to the Synaptic Package Manager, let alone the terminal if I can't get a desktop (workspace) to load on this again.

The version of Bodhi Linux I am running is built on Ubuntu 10.04.4 LTS

Linux Bodhi 2.6.35-28-generic #49-Uuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686 GNU/Linux
Ubuntu 10.04.4 LTS

Welcome to Ubuntu!
 *Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

bodhi@bodhi:~$

---

### Post by bronquel on 2012-03-15
> **theducksfan2010 said:**
> So when I left for Fresno today to go hook up the in-laws computers I just rebuilt (XP) my laptop was doing a update - upgrade in the terminal in Bodhi Linux (Ubuntu based, and had been doing this for quite a while. I just got back to find it all locked up and did the skinny elephant trick from your link to no success, I tried twice. Left wherith no choice but to do a hard kill, and now when try trying to boot it up it starts the load process and then just stays on a blank screen. Am I hosed, or is there anything I can do to try and get this up and running again. No luck in the Graphics Failsafe mode either, although it does progress further with the last 2 lines showing being:

[   2.779366] scsi 2:0:0:0: Direct-Access    Ut165    USB2FlashStoragen0.00 PQ: 0 ANSI:2
[   2.782181] sd 2:0:0:0: Attached scsi generic sg0 type 0


I had an update crash in the terminal in Lubuntu  11.10 before and know that there was a command I had to run int the terminal before I was able to use the Synaptic Package Manager again, but I can't get to the Synaptic Package Manager, let alone the terminal if I can't get a desktop (workspace) to load on this again.

The version of Bodhi Linux I am running is built on Ubuntu 10.04.4 LTS

bodhi@bodhi:~$



I have two guesses as to why your system is hosed, the first being that the grub loader is messed up (grub doesn't mount the hard drive and point to the kernal), and the second being that your linux install is messed up (kernal or some configuration tied to it).  It maybe something else, if the below two things don't work, I'd do a fresh install.

to repair grub do something like this: [http://ubuntuforums.org/showthread.php?t=1485445](http://ubuntuforums.org/showthread.php?t=1485445)  (you maybe able to find a better post than this)  and see if that does the trick.

If that does not work, you can try using a live cd to repair the install:  [http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

If that doesn't work, I'd probably start dumping what ever files you need onto an external hard drive and then do a fresh install.  Hope that helps!

---

### Post by bronquel on 2012-03-15
Found another link that explains more about the "Magic SysRq Key" from which came the skinny elephant trick:  [http://www.makeuseof.com/tag/fix-unresponsive-or-frozen-computers-with-keyboard-shortcuts/](http://www.makeuseof.com/tag/fix-unresponsive-or-frozen-computers-with-keyboard-shortcuts/)

I'm going to play around with this more, but it looks like you maybe able to gain control of your system with out a reboot(alt-sysrq-f), or at the very least dump some information to tell you what process(s) locked up your machine(alt-sysrq-w).

---

### Post by DGINSD on 2012-04-01
> **bronquel said:**
> You might try the skinny elephant trick.  It is a way to regain control of a frozen system.

look at step 5 of this post:
[http://lxtips.posterous.com/recover-an-unresponsive-linux-system-with-alt](http://lxtips.posterous.com/recover-an-unresponsive-linux-system-with-alt)


Sometimes you can also get to a virtual terminal by pressing ctrl-alt-F1 and then using ps or top to kill the offending process(es), and then pressing ctrl-alt-F7 to get back to your desktop.  maybe this trick will let you see what process is causing the problem.

I ran into a freeze up of my HP laptop both touchpad and keyboard totally usless. So on my other computer I pulled up this thread and read through, I got to your post and followed the link to  the skinny elephant trick. One problem my computer doesn't have a SysRq key so I searched around a bit and found that on some computers it's not printed on the keyboard but the print screen in conjunction with the Alt still functions as the SysRq key.

Went through the process;
```

Alt-SysRq-R   (Puts keyboard in raw mode so kernel can receive commands)
Alt-SysRq-S   (Puts the hard drive in sync)
Alt-SysRq-E   (Stops all running processes)
Alt-SysRq-I   (Kills all remaining processes)
Alt-SysRq-U   (Unmounts the file system and mounts it in read-only mode)
Alt-SysRq-B   (Reboots the system)

```

Worked like a charm, thank you for that.

This freeze up occurred using Unity not Gnome shell, so that leads me to believe the issue lies with the base of the system not with a particular desktop environment. How can I troubleshoot this issue to eliminate it?

---

