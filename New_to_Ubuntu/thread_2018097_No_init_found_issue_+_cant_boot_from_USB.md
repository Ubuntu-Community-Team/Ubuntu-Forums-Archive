---
title: "No init found issue + cant boot from USB"
date: 2012-07-05
forum: New to Ubuntu
---

### Post by morano on 2012-07-05
A while back i installed Jolicloud 1.2 on my hp mini netbook.
It worked fine for about a month, but now it gives me the no init found error.
I'm trying to re-install windows.
I've seen the fixes for the issue, which involves a live cd or usb. My netbook doesnt come with a disc drive, so my only option is the USB.

The thing is that i can't boot from my USB at all.
I've set my USB as the default boot device but when i boot it up, it continues on to boot jolicloud. Also, when i press f9 to manually choose the boot device, the only device in the boot options is "notebook hard drive"
Also, when i chose the recovery option on startup, it goes on to boot into jolicloud and give me the error again.

How can i fix this?
the netbook came with a recovery partition but im not sure how to access it.


It is worth noting that my netbook gives me a hard disk error prompt, but it has been that way since a month or so after i got it. The netbook works fine despite this prompt.

---

### Post by anewguy on 2012-07-06
Chances are very high that unless you created installation disks, or you have installation media, you won't be able to recover Windows.  Normally the recovery partition is used in conjunction with installation media.

Also, if you need to boot a Windows install disk but from USB, you may want to check for win32diskimage-creator (or some such name).  It will take an ISO and burn it to a USB flash drive.  I believe this tool was based on tools for Linux, but this one runs in Windows.  Take a Windows install disk, make an ISO image file of it on a Windows pc, and use win32disk-image to burn it to a flash drive.  Take the flash drive to your netbook, check the BIOS boot order - you may have to move the USB device to be the first boot device first.

If you are having problems booting from a flash drive, just be sure your BIOS has the USB boot option higher in the boot order than the hard drive.


Also, remember you can't just copy files to the USB media and boot - you actually have to use software - like win32disk-image or unetbootin to burn the IMAGE to the media.

---

### Post by critin on 2012-07-06
> How can i fix this?
the netbook came with a recovery partition but im not sure how to access it.


It is worth noting that my netbook gives me a hard disk error prompt,  but it has been that way since a month or so after i got it. The netbook  works fine despite this prompt.With a hdd error on a brand new machine, I would have contacted the seller for a replacement, but that's just me.

Why don't you go to the computer's site and search for the manual if you don't have one.   Or ask there.  There should be a 'restore' or 'recovery key' on the bios page to hit.  Don't mess too much with it or you might lose the option.  On my HP, there is info in the Programs list for recovery, but that's unique I think, my other machines don't have it there.

---

### Post by critin on 2012-07-06
> I'm trying to re-install windows.Are you dual booting or did Joli take the whole disk?  Unless you're dual booting, the recovery partition is gone.


 > Also, when i press f9 to manually choose the boot device, the only device in the boot options is "notebook hard drive"

When mine couldn't see the usb, it was because that usb port was faulty.  Try another.

---

