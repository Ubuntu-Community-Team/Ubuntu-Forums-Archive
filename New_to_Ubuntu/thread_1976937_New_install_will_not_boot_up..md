---
title: "New install will not boot up."
date: 2012-05-09
forum: New to Ubuntu
---

### Post by Bigjack08 on 2012-05-09
Hello all; I decided to ditch windows from my desktop as well as my laptop and loaded ubuntu 11.10 some time ago; the computer is a Compaque Presario.  It worked fine and today I decided to try it as a dual boot PC with windows 7.  I tried to load the Windows 7 ISO disc and it wouldn't load, and the computer would not shut down.  I switched the computer off and it would not boot up again.  I had decided to upgrade to ubuntu 12.04 anyway so downloaded the ISO file; I chose the option to upgrade from 11.10 to 12.04 and at the end of the process a message reported that not all of my previous files had been successfully copied.  Now the computer gets as far as the black screen with flashing cursor at the top left corner and stops.  
Any ideas for getting ubuntu up and running again.....sod windows.

---

### Post by iMurshaq on 2012-05-09
You might have corrupted your BIOS, if not try a Bios update.

---

### Post by oldfred on 2012-05-09
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

Windows cannot see Linux partitions, but knows it is in use. Windows needs a primary NTFS formated partition with the boot flag to install or unallocated space with a primary partition available.

---

### Post by Mark Phelps on 2012-05-09
I don't think Windows, even Win7, will allow you to install to a drive that is fully-formatted with a Linux Filesystem -- because Windows simply does not understand non-Windows filesystems.  That might halt the installer part way through.

Another possibility, as evidenced by the Ubuntu installer being unable to copy all the files, is impending hard drive failure.

If this latter problem is the case, you could try ruling out other hardware problems by booting from a LiveCD -- which will not use the hard drive.  If that works fine. albeit slowly, then the only hardware problems left are hard drive related.

And, BTW, I had a very similar problem with 12.04 -- it appeared to install OK, but would not boot -- even after a bunch of reinstalls and GRUB repairs.  I tried a different hard drive, and 12.04 installed and is now working fine.  So. it appears that 12.04 might be especially sensitive to hard drive problems, moreso than earlier releases (since this drive had 11.04 on it working just fine).

---

### Post by Bigjack08 on 2012-05-09
Thanks for the advice so far guys, but the boot repair programme would not work (I did get it loaded).
I am now trying a clean install of ubuntu 11.10 to see if that helps following the last input.
Will let you know what happens; incidentally if I am succsessful with the 11.10 I will attempt an upgrade and see if the problem returns.
Can't wait until I know how to work this properly!!
I am leaving windows off ...... full stop.

---

### Post by Mark Phelps on 2012-05-09
> **Bigjack08 said:**
> Thanks for the advice so far guys, but the boot repair programme would not work (I did get it loaded).
..

Ironically, this same thing happened in the case I cited above.  Boot-Repair would load, I would select the option to repair ... and it would just cycle and cycle and cycle ...

I let it go one time for over an HOUR, and it still did not finish.

The only thing that "fixed" it was replacing the drive.

---

### Post by Bigjack08 on 2012-05-10
Well a result sort of! I have successfully clean installed ubuntu 11.10 and all seems well. It is currently downloading all of the updates (quite a lot) and then I will attempt to upgrade to 12.04. Will keep you informed.

---

### Post by Bigjack08 on 2012-05-10
Have now upgraded to ubuntu 12.04 via internet and all except my printer Brother DCP 385C is working. Thanks guys.

---

