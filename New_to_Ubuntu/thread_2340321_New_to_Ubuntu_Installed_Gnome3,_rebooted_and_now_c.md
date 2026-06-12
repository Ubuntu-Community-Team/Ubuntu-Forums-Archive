---
title: "New to Ubuntu: Installed Gnome3, rebooted and now computer doesnt boot?"
date: 2016-10-17
forum: New to Ubuntu
---

### Post by SnazzleLabsYT on 2016-10-17
Title. It comes up with the message:     A start job is running for Hold until boot process finishes up (time since message here/no limit)

---

### Post by oldrocker99 on 2016-10-17
Did you install Gnome 3 from an existing Ubuntu installation, or did you install Ubuntu Gnome?

---

### Post by T.J. on 2016-10-17
I need to ask, what kind of video hardware and driver are you using?  It is important, because Gnome is very sensitive.

---

### Post by SnazzleLabsYT on 2016-10-17
I installed on top of an existing vanilla Ubuntu install.

The graphics card is a GeForce 840M, with propiatary drivers from Additional Drivers.

Forgot to mention; I cant even get to Unity.

EDIT: its still showing the message, not booting and it stayed like this for 40 mins

EDIT 2: before rebooting, Gnome worked perfectly.

---

### Post by T.J. on 2016-10-17
Thank you.  Before we begin, I feel compelled to mention a couple of caveats to this process.  Please do not think I am rude, sometimes I am simply blunt. This is not a reflection on you or your abilities.  I don't know what they are.  

I'll try to keep straight to the point, so that you get a solution without the fan-girl/boy commentary.

1.If you are upgrading to 16.10, 16.10 is intended as an enthusiast/developer version, and there are bugs.  This is a given. For best results, non-programmers should stick to LTS versions of Ubuntu.  They have better support and fewer bugs over time.  

2.&#8220;In place&#8221; upgrades of Ubuntu versions have been known to create unforeseen bugs, especially while booting up.  It is recommended that you reinstall rather than upgrade, especially if it is not an LTS version.  



Okay, that said, I need you to edit your boot lines.  You can do this on the menu when Grub starts up usually.  By pressing E, you can usually edit the lines.  In your boot entry, try looking for a line that has the word&#8220;splash.&#8221;  (If you don't find it, try to post what you have and I'll tell you what you need to do next.)

Add &#8220;nomodeset vga=0x318&#8221; to that line and then boot the machine.  This will force the system to boot into low resolution VGA mode.  If Gnome starts,then that means we need to fix your video setup.  If not, the boot process may be stalled on something else.  


We will try this first.  If that works, let me know and we then will work on repairing your video driver.

---

### Post by SnazzleLabsYT on 2016-10-17
My problem is that at boot, the system bypasses GRUB and goes straight to the splash screen.

Also, dont worry about trying to/not trying to be rude :)

Also, the machine is a laptop. Don't know if that makes a difference though.

---

### Post by monkeybrain20122 on 2016-10-17
You can get to grub by quickly press than hold the shift key.

---

### Post by Geoffrey_Arndt on 2016-10-18
Did you ever get to the standard Unity desktop before you decided to "overlay" (and what does that mean really - - did you just install the gnome3 desktop? ).   How did you do that?   (what source and what packages?).    BTW, saying "Laptop" is as meaningless as saying "Desktop" . . . . what make and what specific model?    Do you have any other OS's on the PC?

---

### Post by SnazzleLabsYT on 2016-10-18
Yeah, I could get to Unity, and Gnome3 was installed by the command <CODE/> sudo apt install gnome <CODE/> and this was from the 'universe' repository. The laptop is a Lenovo Z50-70 (the model with an i7-4510U, 8gb RAM and a GeForce 840M.) This came with Win8.1 and I installed Ubuntu recently.

Ubuntu was clean installed over a current (yet broken) Kubuntu 16.04 install with no other OSs.

---

### Post by Geoffrey_Arndt on 2016-10-18
That's good news . . . that this isn't a dual-boot scenario, as dual-boot seems to add a lot more "instability" to the overall machine than Linux or Windows only (more so than in the past where Windows updates would not overwrite boot-loaders, partition tables etc.).

So, my suggestion is to start off with a "STABLE" version of standard Ubuntu - - that is, Ubuntu LTS with the Unity Desktop.   Then run only that for daily for  6 months until you build some actual expertise.   I also run Xubuntu for example, but do it on a separate usb_v3 SSD as a complete installed system (not a live or persistent live system).

Finally, set up a _Test PC or Test Partitions_ to do any future experimenting with other distros or other desktops.    Just like running a dual-boot, have multiple DE's on the same partition is just opening the door for "complications" and extra work (imho).

---

### Post by SnazzleLabsYT on 2016-10-19
Yeah, alright! I'll take your advice and reinstall. I'll install Ubuntu 16.04 LTS and run that so I gain a lot more expertise.

Thanks for you help!

---

### Post by mastablasta on 2016-10-20
if you would like to experiment and have the ram to do it (4 Gb would be good) then use this: [SIZE=2]http://www.psychocats.net/ubuntu/virtualbox
[/SIZE]

install procedure is nearly is the same in Linux or Windows. 



you install Linux in virtualbox, make a snapshot of the OS, mess it up completelly. then just click restore snapshot and in a few seconds you are back to where you started. i do it all the time when i need to test some new progs or something.

---

### Post by SnazzleLabsYT on 2016-10-20
I've used VBox before, and am used to it. Thanks for the suggestion though.

---

