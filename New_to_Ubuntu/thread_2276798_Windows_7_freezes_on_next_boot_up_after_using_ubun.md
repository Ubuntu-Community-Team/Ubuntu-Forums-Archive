---
title: "Windows 7 freezes on next boot up after using ubuntu live cd"
date: 2015-05-05
forum: New to Ubuntu
---

### Post by sikofwin7 on 2015-05-05
As question says, windows 7 freezes on next boot up after using ubuntu live cd. Only way to fix it that i have found is to turn of power supply before booting up after using the live cd.

Anyone else have this happen to them? Any idea on how to fix it?

Thank you in advance, much appreciated!

---

### Post by Bucky Ball on 2015-05-05
Welcome. Have you tried shutting down the machine (not rebooting)? Same thing? Are you booting up with the disk still in? Have you changed the BIOS back to boot from the hard drive and not the optical drive? Is this the ONLY time this happens, when you boot the Ubuntu disk then restart? Are you shutting down the disk properly (log out or restart) or just switching the machine off?

Some might appear to be silly questions but best to ask. ;)

---

### Post by sikofwin7 on 2015-05-05
I have been shutting it down completely. Nope i take the disk out when it tells me too upon it shutting down. Yup BIOS is set to boot up from hard drive. Yea only time it happens, i can shut down the PC and than boot it up all day and it won't freeze except after using Ubuntu live cd. I shut down properly always.

---

### Post by Bucky Ball on 2015-05-05
Hmm, very strange. Booting from live media shouldn't interfere with or alter your hardware in any way. What are you doing when you boot from the install media? Just 'Try Ubuntu' and going to the desktop and looking about? Are you mounting any Win drives that are not unmounting properly, or something obscure, which brings me to ...

Is Win7 booting in UEFI? Are you booting the install media the same way? Is the Win7 partition in hibernate when you boot Ubuntu and not completely shut/unmounted? (Are you shutting down Win completely, not using 'fast boot/start' or whatever it's called)?

If Win is hibernating when you shutdown/reboot and launch from the install media, rather than off/shutdown, that means the disk is still open and mounted according to Win. Perhaps it's getting confused by something in that case when you boot from the install media then back to the disk. Just a guess ...

Have a check to make sure when you shutdown Windows it is shutdown totally, not in hibernate.

---

### Post by Mark Phelps on 2015-05-05
Couple of questions ...

1) shutdown: When you exit from Ubuntu to reboot into Win7, are you selecting Restart? Or are you selecting Shut Down?

2) Win7 freezinfg: how far are you getting into Win7 before it freezes?  Do you get the animated Windows logo?  Do you get to the login screen?  Do you get to the desktop?

---

### Post by sikofwin7 on 2015-05-06
@Bucky Ball

Yea i just click on try Ubuntu and look around. I do mount a usb but  unless it doesn't unmount it properly when i tell it to, than it  shouldn't be a problem as i do unmount it as well a remove it after  unmounting it.

This i am not sure.  How would i go about finding out? I completely shutdown Win 7 before  booting from Ubuntu CD. 

Nope i completely shutdown Win 7

Like i said, completely shutdown Win 7



[URL="http://ubuntuforums.org/member.php?u=311399"][B][COLOR=#000000]

[/COLOR][/B][/URL]@Mark Phelps

Shut down completely.

I get all the way to the desktop. I can  even see my Antivirus and firewall working. Thing is that my mouse  cursor won't move and my keyboard won't work either.


Edit: Sorry had to post it like this instead of replying with quote function. Some reason it wouldn't let me do it that way. I kept getting message was to short and to at least use 1 character or something to that effect.

---

### Post by Bucky Ball on 2015-05-07
So, in other words, your problem is that your mouse and keyboard don't work in Windows? And you're saying this ONLY started happening after you tried Ubuntu from live media (USB or disk)?

---

### Post by sikofwin7 on 2015-05-08
> **Bucky Ball said:**
> So, in other words, your problem is that your mouse and keyboard don't work in Windows? And you're saying this ONLY started happening after you tried Ubuntu from live media (USB or disk)?Yup that is what i am saying. It only happens if i have just finished using Ubuntu live CD. Not sure what is going on or why this happens.

---

### Post by sammiev on 2015-05-08
Since you are set to boot from the hard drive, why not leave the live cd in for a few boots.

I just wonder if it's not totally shutting down.

---

### Post by sikofwin7 on 2015-05-08
> **sammiev said:**
> Since you are set to boot from the hard drive, why not leave the live cd in for a few boots.

I just wonder if it's not totally shutting down.

I guess i could go ahead and try that and see if that works.

---

