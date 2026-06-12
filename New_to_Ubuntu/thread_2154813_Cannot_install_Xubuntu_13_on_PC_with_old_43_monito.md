---
title: "Cannot install Xubuntu 13 on PC with old 4:3 monitor.  Screen just goes blank."
date: 2013-06-16
forum: New to Ubuntu
---

### Post by queazy03 on 2013-06-16
Hi.

Help!  I can't install Xubuntu 13 onto an older PC with an old 4:3  monitor.  The computer boots up into its old BIOS start up thing like it  did for Windows XP, then it says it is booting off the CD, then does  the Xubuntu Install image of keyboard + man in a circle icon, then I get  a blinking cursor in upper left corner, then I get the error "OverSize  Recommand Mode 1280 x 1024", then the screen goes blank.  

"[http://imgur.com/fMe1yKW](http://imgur.com/fMe1yKW)" has a picture example of what is going on.


The monitor is an old 
"Kogi L7EH-TA" monitor with Model "L7EH-TA_QD63V-2000-KG2".  
It is roughly a 17 inches across from opposing corners (roughly 13.5 inches wide & 10.5 inches tall).
It appears to be a 4:3 ratio monitor, but it seems to want a recommended  resolution of "1280 x 1024", which I guess would really make it that  oddball 5:4 ratio.

What can I do to install Xubuntu on this PC / Monitor?  Thank you.

---

### Post by mörgæs on 2013-06-16
How does it work with the alternate ISO (Lubuntu)?

---

### Post by queazy03 on 2013-06-16
> **mörgæs said:**
> How does it work with the alternate ISO (Lubuntu)?

I don't even know what that is.

---

### Post by user_of_gnomes on 2013-06-16
> **queazy03 said:**
> I don't even know what that is.

They're Ubuntu editions with a less fancy installer and a higher chance of working on older machines. Unfortunately, they are very well hidden and I can't find 'm at the moment ...

Oh, actually I found out why: [http://www.phoronix.com/scan.php?page=news_item&px=MTE2OTk](http://www.phoronix.com/scan.php?page=news_item&px=MTE2OTk)

In their infinite wisdom, canonical decided to drop Alternate installers?

You can still get one for Lubuntu, though: [https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO)

---

### Post by snowpine on 2013-06-16
Have you considered throwing money at the problem and simply upgrading to a computer on this list (and a new monitor)?

[http://www.ubuntu.com/certification/](http://www.ubuntu.com/certification/)

Or purchase a machine with Ubuntu preinstalled such as System 76?

[https://www.system76.com/](https://www.system76.com/)

---

### Post by mörgæs on 2013-06-16
That would not be my advice.
Plenty of tests and workarounds to try before giving up on the hardware.

---

### Post by queazy03 on 2013-06-17
---IGNORE---[strike]Well...there is one thing I can try.  I can borrow a monitor that is more modern and not  4:3, install it on with that monitor, and then change it later.  I was able to do this on another machine, so I think I will try that.  I'd rather avoid this, because the person whose monitor I'm borrowing this from does not like to lend it, so I will try to make it quick.  Will update thread with results later.[/strike]---IGNORE---
Woops...I just remembered, this MIGHT not work.  Doing this allows Xubuntu to change the resolution to a resolution low enough for this old monitor to handle, but only after you have logged in.  The Login screen isn't visible at this time if I remember right.  I'll try this though, maybe even using two monitors connected to the PC (with old monitor as main screen and a newer monitor as secondary screen).  Hopefully it works.  Thank you all, I greatly appreciate your advice.

---

### Post by queazy03 on 2013-06-17
What can I do now that I am getting the error "error:  attempt to read or write outside of disk 'hd0'"?

Ok, I tried plugging in another monitor temporarily, and before it finished installing I plugged in the older 4:3 monitor and it worked.  However I'm getting this error now 
"error:  attempt to read or write outside of disk 'hd0'"
and I have no idea what it is or how to fix it.  A google search has somewhat confused me, having something to do with something called "Grub" (no clue what that is), and the Xubuntu OS trying to install itself on the hard drive but leaving too little space left over for the BIOS to work properly... well that is what it seems with my limited grasp of the subject.  

Here is a picture at "http://imgur.com/kgTG6FR".  

What can I do now that I am getting the error "error:  attempt to read or write outside of disk 'hd0'"?
Thank you.

---

### Post by mörgæs on 2013-06-18
This is old gear. Please post a complete hardware description.

---

### Post by user_of_gnomes on 2013-06-18
> and I have no idea what it is or how to fix it. A google search has somewhat confused me, having something to do with something called "Grub" (no clue what that is), and the Xubuntu OS trying to install itself on the hard drive but leaving too little space left over for the BIOS to work properly... well that is what it seems with my limited grasp of the subject.


The BIOS is not situated on the hard drive. (Although parts of the user interface might be on certain Compaq/HP systems but that is most likely not applicable here and even if it was and you'd wipe the hard drive, it would function regardless.)

Also, you might want to diagnose that hard drive to make sure it's O.K.

I've only skimmed over this thread and it seems to me that your combination of monitor and videocard might not be optimal. You could try a different videocard or use some of the boot options as discussed here: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Ubuntu has no problem working with 1280x1024. I installed it on 15" monitors with 8MB videocards and although you can get some funky results, it pans out right most of the time.
Why don't you try Lubuntu with the alternate installer like you were recommended to do earlier?

---

### Post by momist on 2013-06-23
OK, it's been a while (5 days) and I may get some flames from this, BUT:

Have you considered an operating system perhaps a little more suited to your old hardware?  I'd recommend Puppy Linux.  I had success with this on a very, very old Toshiba laptop of the sort that Ubuntu would not even fit on the HD, and memory measured in megabytes.  Ran beautifully, and really easy to use.

Nothing wrong with Lubuntu either, and once you're up and running with that you can easily add any of the heavier software you desire that doesn't come in the standard install.  My current Dell D360 could run full blown Ubuntu or Xubuntu, but Lubuntu _really_ flies on that, and for what I use it for it's great.

---

