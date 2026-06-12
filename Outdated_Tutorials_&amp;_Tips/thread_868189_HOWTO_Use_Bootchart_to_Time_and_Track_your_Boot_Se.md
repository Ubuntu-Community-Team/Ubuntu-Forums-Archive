---
title: "HOWTO: Use Bootchart to Time and Track your Boot Sequence"
date: 2008-07-23
forum: Outdated Tutorials &amp; Tips
---

### Post by mbsullivan on 2008-07-23
**HOWTO: Use Bootchart to Time and Track your Boot Sequence**

This simple tutorial will describe how to use bootchart in order to get a graphical representation of the processes which run during your boot process. You will also be able to view the CPU and disk usage during your boot sequence, and will get an exact time (in seconds) of how long it takes for you to boot up.

Using bootchart is in no way difficult (and I present no new knowledge here), but it is my hope that this will introduce some in the Ubuntu community to bootcharting and give them an easy introduction to the topic.

**Motivation:**

There are various reasons that you may want to see what processes start along with your computer. Apart from satisfying your curiosity, getting a visual representation of your boot sequence may help you to fine tune your computer startup, or to diagnose why your computer may not be starting as quickly as you may like. Furthermore, getting a quantitative value for the time it takes to boot your computer will allow you to analyze how much of an improvement you make in the future :)

**Installing Bootchart**

In order to track the boot sequence, we will use a program called bootchart. Installing it from the repositories is dead simple:

```
sudo aptitude install bootchart
```

... And it's installed! No further configuration is necessary. 

**Using Bootchart**

Using bootchart may be even easier than installing it... Just reboot! After your machine starts up next time, bootchart will create a graphical representation of the boot sequence (as a .png file), and place it in **/var/log/bootchart**.

An example bootchart is attached. It was taken from an unoptimized boot sequence on my Thinkpad x61 running Hardy. You can see at the top that it took 30 seconds to boot completely, and there seem to be some places where optimizing the boot sequence (through parallelism) could possibly lead to a speedier bootup. But, such a thing is best left for another tutorial...

**Disable Bootchart**

Bootchart will, unless disabled, chart every boot process after you've installed it. This may be overkill for most users, who only want to track their boot sequence occasionally. In order to stop bootchart from charting your boot sequence, simply remove its SysV script from executing after startup:

```
cd /etc/init.d
sudo update-rc.d -f stop-bootchart remove
 Removing any system startup links for /etc/init.d/stop-bootchart ...
   /etc/rc2.d/S99stop-bootchart
   /etc/rc3.d/S99stop-bootchart
   /etc/rc4.d/S99stop-bootchart
   /etc/rc5.d/S99stop-bootchart

```

**Enable Bootchart**

Re-enabling bootchart is as simple as disabling it. You may either reinstall it (through the repositories), or add it back to runlevels 2345:

```
cd /etc/init.d
sudo update-rc.d stop-bootchart start 99 2 3 4 5 .
 Adding system startup for /etc/init.d/stop-bootchart ...
   /etc/rc2.d/S99stop-bootchart -> ../init.d/stop-bootchart
   /etc/rc3.d/S99stop-bootchart -> ../init.d/stop-bootchart
   /etc/rc4.d/S99stop-bootchart -> ../init.d/stop-bootchart
   /etc/rc5.d/S99stop-bootchart -> ../init.d/stop-bootchart

```

That's it! It's so easy! I hope that this tutorial helps some of you to chart your boot process. Let me know if anybody runs into any issues.

Mike

---

### Post by erwall on 2008-07-28
Didn't work for me, installed, rebooted, and nothing in /var/log/bootchart

Then tried this:

```
sudo update-rc.d stop-bootchart start 99 2 3 4 5 .
```

And got this:

```
System startup links for /etc/init.d/stop-bootchart already exist.
```

---

### Post by mbsullivan on 2008-07-28
> Didn't work for me, installed, rebooted, and nothing in /var/log/bootchart


For most people, bootchart should work "out of the box". Otherwise, troubleshooting seems a bit ambiguous.

What distro are you running? Also, did you do something non-standard to your java installation? Bootchart depends on java, so if you have weirdness going on with your JRE then it might make something break. What's the output of 'which java' and 'which rsvg'?

A quick look around and I came up with [this thread]("http://ubuntuforums.org/showthread.php?t=319962"). Turns out that bootchart doesn't run when FSCK checks the disc, and certain boot options can stop it from working, too.

Perhaps one of these things applies to you? You could also try a good old reinstall:

```
sudo aptitude reinstall bootchart
```

Let me know if the problem resolves itself.
Mike

---

### Post by erwall on 2008-07-28
I have what I consider a pretty vanilla install of Hardy.  The output of which java and which rsvg show them both in /usr/bin

After reading the other post you provided I'm wondering if my having 'startup-manager' installed has anything to do w/it...

Thanks for the help so far!

---

### Post by mbsullivan on 2008-07-29
```
After reading the other post you provided I'm wondering if my having 'startup-manager' installed has anything to do w/it...
```

You mean [this one]("http://packages.ubuntu.com/hardy/startupmanager")? It doesn't sound far-fetched to me that it might interfere with bootchart. I know that it has issues out-of-the-box dealing with display managers other than XDM/KDM/GDM, and there are probably other programs that might interfere with its performance, as well.

Let me know if you figure anything out!
Mike

---

### Post by erwall on 2008-07-29
> **mbsullivan said:**
> ```
After reading the other post you provided I'm wondering if my having 'startup-manager' installed has anything to do w/it...
```

You mean [this one]("http://packages.ubuntu.com/hardy/startupmanager")? It doesn't sound far-fetched to me that it might interfere with bootchart. I know that it has issues out-of-the-box dealing with display managers other than XDM/KDM/GDM, and there are probably other programs that might interfere with its performance, as well.

Let me know if you figure anything out!
Mike
Yep, that's it.  I'll report back if I figure anything out.

---

### Post by run1206 on 2008-08-01
sorry to ask but does anyone know where the config files are for bootchart
i'm trying to put the patch in that does bootchart after the GNOME startup 
[http://www.gnome.org/~lcolitti/gnome-startup/analysis/](http://www.gnome.org/~lcolitti/gnome-startup/analysis/)

(i've checked /etc and i don't have bootchartd.conf like the patch says)

any help is appreciated, thanks a bunch.

---

### Post by mbsullivan on 2008-11-13
> (i've checked /etc and i don't have bootchartd.conf like the patch says)

You're right, the Ubuntu packages do not install a configuration file for bootchart. I'm not sure of any fix (there may be one) other than going and installing it some other way.

The Debian packages are more updated, and might (note: I don't know) work out for you. I've attached the current version from Debian to this post. You can try it out by downloading it and installing it:

```
sudo dpkg -i [name].deb
```

Uninstall the Ubuntu package first, if you want to try it.

Mike

---

### Post by jmckean on 2009-01-31
OK, I have bootchart running under eeeUbuntu (8.04 with netremix and a few hardware tweaks).  But it reports much faster boot than I actually experience.  It says 22 seconds, I say 45 seconds to login prompt (gdm).

I thought is was measuring to login prompt.  Am I wrong?

---

### Post by run1206 on 2009-01-31
nope, bootchart only checks up to where you finish with the startup processes.  There is a patch where you can have bootchart check up to the login promapt and including the gdm login process up to where your main screen comes up.  Look up boootchart patch either here or in Google

---

### Post by mariner09 on 2009-02-12
I installed bootchart on Jaunty and it works great...

I installed bootchart on Intrepid to compare and it doesn't generate anything.

I removed startupmanager and no go..

Does it require a specific java to function?

---

### Post by run1206 on 2009-02-13
> **mariner09 said:**
> I installed bootchart on Intrepid to compare and it doesn't generate anything.

odd, works for my Intrepid partition :?

did you check the right folder? (/var/log/bootchart/)
right code?  ```
sudo apt-get install bootchart
```

also, what's your hardware specs?  maybe it might be a hardware problem...

---

### Post by EzarKun on 2009-09-11
Hi,

Thanks for the tutorial OP. 

Newb here, and having some problem in boot somewhere, but don't understand what is causing it.
Also sorry for bring out old thread, it's what I found in search.

Anyways, I used bootchart, and there is an unusually long wait period from GRUB to activity, around 15-20 seconds.

I have attached the pic. Hope someone can figure out the problem.

```
Hardware spec:
-Computer-
Processor		: Genuine Intel(R) CPU           U2700  @ 1.30GHz
Memory		: 3917MB (529MB used)
Operating System		: Ubuntu 9.04
User Name		: newblet
Date/Time		: Fri 11 Sep 2009 12:42:46 PM EDT
-Display-
Resolution		: 1366x768 pixels
OpenGL Renderer		: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20090326 2009Q1 RC2
X11 Vendor		: The X.Org Foundation
-Multimedia-
Audio Adapter		: HDA-Intel - HDA Intel
-Input Devices-
 Power Button (FF)
 Lid Switch
 Sleep Button (CM)
 Macintosh mouse button emulation
 AT Translated Set 2 keyboard
 Video Bus
 PC Speaker
 HD Video WebCam
 SynPS/2 Synaptics TouchPad
-Printers-
No printers found
-IDE Disks-
-SCSI Disks-
ATA WDC WD3200BEVT-2
TSSTcorp CDDVDW TS-U633A
```


Thank you

---

### Post by mbsullivan on 2009-09-15
> Anyways, I used bootchart, and there is an unusually long wait period from GRUB to activity, around 15-20 seconds.

Weird! Is it on the GRUB screen (with the list of available kernels and a countdown)?

Mike

---

### Post by EzarKun on 2009-09-16
> **mbsullivan said:**
> Weird! Is it on the GRUB screen (with the list of available kernels and a countdown)?

Mike

Hi,
Thanks for the reply.

To answer: its right after the grub screen, and right before the Ubuntu loading screen. 

It says: 
> Starting up...
at the top of the screen after selecting Ubuntu in GRUB, thats when there is that 15-20 second wait.

I have attached the bootchart PNG in my previous post. I think USplash is the Ubuntu loading thing? it starts 20 seconds after first init process for some reason.

Thanks

---

### Post by felipe-fruwacz on 2009-11-29
Hi,
hope here some can answer my question:
my boottime is prolonged by high usage of CPU when it's mounting nfts file (over 10 sec), What can I do to shorten the time?

---

### Post by mbsullivan on 2009-12-01
> my boottime is prolonged by high usage of CPU when it's mounting nfts file (over 10 sec), What can I do to shorten the time?

NFTS? I'm not quite sure what you mean. 

Do you mean that you're mounting an NTFS drive (shared with a Windows computer), or an NFS drive (network file system), or something else?

Mike

---

### Post by frogotronic on 2010-04-29
Hello,

 I get 1 minute 21 seconds.  My wife has the same machine running winXP and its about 5+ minutes.

  WooHoo!!!

- CH

---

### Post by kamatschka on 2010-04-29
With 10.04 i get about 28 - 30 seconds

I was really impressed after I installed Lucid and have seen the time it needs to boot to the desktop.

Soo.. a SSD would get 5 Secs or what?! :D

EDIT: Daaaamn the Boardsoftware is resizing the picture from bootchart automatically and after that nothing can be recognised from the picture... I upped it on imageshack.

[[IMG]http://img249.imageshack.us/img249/8898/ronubuntulaptoplucid201.th.png[/IMG]](http://img249.imageshack.us/i/ronubuntulaptoplucid201.png/)

---

### Post by Oliv' on 2010-06-15
Hello,

&#304; use Lucid.

&#304;'m trying to deactivate bootchart but for some reason &#304; cannot find where or how it's called ?

And there's nothing about bootchart in etc/rcX.d ...

Thanks,

Oliv'

---

### Post by Oliv' on 2010-06-18
I looked further at what's going on, and found some bootchart script here and there :

1)
/usr/share/initramfs-tools/hooks/bootchart
/usr/share/initramfs-tools/scripts/init-top/bootchart

So &#304; guess here I can delete the bootchart scripts. I tried but as I inferred from the the man page I have to create a new initramfs image to be effective.
I hope there's a more user-friendly way to desactivate bootchart !
And I don't know if it will be enough because of 2) 

2)

/etc/init/bootchart.conf
/etc/init.d/bootchart

Here some others bootchart scripts. Who does what is still a mystery for me, but at least &#304; learn things about the booting process ;-)
So in /etc/init/bootchart.conf  there's this line with "bootchart=disable" where it should exit the script and stop bootchart if &#304; understand correctly... but the question is where or how do &#304; tell this script that I want to disable it ???

&#304;f somebody can help me on this one &#304;'ll be very glad !

Regards,

Oliv'

---

### Post by cheaka on 2010-07-31
Assuming you installed from a package:
```
sudo apt-get remove bootchart
```
should update all the boot stuff correctly.

---

