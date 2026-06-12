---
title: "There has to be a way..."
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Dionikon on 2008-05-13
Ok, I've been playing around with Ubuntu and MythTV with limited success.

I have now got to a point where I'd like to wipe it clean and start anew.

Now for the silly part.  I can't figure out how to do that.  I try booting from the CD and it boots directly into my current build without giving me any options.  I'm positive I've just missed something but can someone help me out here?

I have searched the forums but can't find any mention of how to do this.

Cheers,

:)

---

### Post by kesman on 2008-05-13
Is the CD burned correct? Is your BIOS set to boot from cd first and HDD second?

---

### Post by Dionikon on 2008-05-13
It's the same CD that I installed from originally so I'm pretty sure it's correct.

I have actually set the BIOS to only boot from the CD and not the HDD at all.  I can hear the CD spin up as it boots, then the HDD lights flicker during the boot process, then shows my login screen as if the CD doesn't exist.

---

### Post by smoker on 2008-05-13
sounds like a faulty or dirty cd or drive, try giving both a clean, and maybe try the disk on another pc if you can and see if it starts ok there.

---

### Post by Dionikon on 2008-05-13
I don't have another PC that I can try but I have tested the CD using a parallels install on my Mac laptop and it works perfectly.

Kind of glad about that, would have been very embarrassing otherwise. :)

---

### Post by Dionikon on 2008-05-13
Is there a way to force the HDD to be unbootable?  It is definitely booting from CD to start and then switching to the HDD as it starts.

I have noticed a menu while booting, I see message saying:
```
 
Loading GRUB
Press Esc for menu: 

```

When I hit Esc I get 5 boot options:
```

Ubuntu 8.04, kernel 2.6.24-16-generic
Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
Ubuntu 8.04, kernel 2.6.24-14-generic
Ubuntu 8.04, kernel 2.6.24-14-generic (recovery mode)
Ubuntu 8.04, memtest86+

```

With some more options regarding editing commands or using a command line.

Whichever option I choose the system still starts using the HDD.

If I choose 'e' in this menu to edit the commands I think I can see why, the first line reads: 
```

root  (hd0,0)

```
which would suggest to me that the CD is forcing the system to switch to the HDD, unless this menu is on the HDD rather than the CD.

I'm going around in circles now, best stop and wait for advice.....

:)

---

### Post by raydeen on 2008-05-13
I would suspect a faulty CD drive or cable. I had a laptop I was trying to fix up for a customer and couldn't get the CD to boot. Turns out the drive was bad. (the laptop had taken a fall at some point and when I pulled the drive out, it was bent up like you wouldn't believe.) Maybe it's time to upgrade to a nice DVD+/-RW. :)

---

### Post by Dionikon on 2008-05-13
That would make sense, except it's a brand new Sony Blue Ray drive.

Once I've booted into the current install I can read from the drive with no problems, although I can't seem to get it to play DVD's correctly, I assume this is something to do with my tinkering, not a problem with the drive.

To be sure though I'll dig up a known working drive and test it out.

---

### Post by Dionikon on 2008-05-14
I found a way, although it's probably not recommended procedure. ;)

What I did was:
- I disconnected the SATA cable from the HDD.
- Boot the machine from the CD and wait for the OS to boot from the CD.
- Then plug the HDD back in and tell the CD to install from scratch.

Problem solved.

Like I said, probably not the best way to do it, but hey... it worked. :)

---

