---
title: "[SOLVED] Re-install"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by tnewt on 2008-11-08
How do I re-install Ubuntu 8.10? I installed it, played around with it, put some things on and took some things off and generally messed it up. I want to start over with a clean install without messing up my home directory (which, fortunately, is on a separate partition).

When I put in the installation disk, it seems to recognize that it is already on the hard drive and boots up from that. This is not what I want. I want it to start over and install it cleanly. I want my messed up but working install on the hard drive to be a forgotten memory.

How do I do this?

---

### Post by phidia on 2008-11-08
Do you have the cdrom/optical drive selected in bios to boot before the hard drive?

If you put the disc in the drive it should boot from that if bios is set up correctly.

---

### Post by akiratheoni on 2008-11-08
You'll have to change your BIOS to boot from the CD. Right now it checks the hard drive before checking the CD drive for an operating system. Restart your computer and when the computer manufacturer's logo appears, there should be an option that says something like <F10> Boot Menu or <F2> BIOS.

Hit that key (which could be F1, F2, Del, F10, F12, etc) and you'll get into the BIOS or boot menu. If you're in the boot menu, just select the CD drive. If you're in the BIOS, you'll have to look around for a category called "Boot" or something similar.

---

### Post by Elfy on 2008-11-08
You have to boot from the livecd - if it isn't then make sure that bios is set to boot from cd first - or if you have newish hardware you might have a boot option - either way theree should be a way to access them - esc, delete, F keys 

Once it's booted - choose manual partitioning option - pick the drive it's installed on and edit partition to be used as ext3, mountpoint of / - format drive

Pick your home - edit partiton - use as ext3 mountpoint /home - do not format

---

### Post by tnewt on 2008-11-08
Man, those are fast replies! I'll try it out and let you know how it goes.

---

### Post by tnewt on 2008-11-11
Well, it doesn't work. It doesn't matter if I tell the BIOS that the CDROM is the only boot device that exists. It goes to the hard drive and boots up and I get my old desktop.

Is this some 'feature'? Is Ubuntu checking the hard drive and saying "he's already got this installed, I'll just jump to the hard drive." ??

The CDROM works--it is what was used to put Ubuntu (8.10 RC) on it in the first place. In fact my original 8.10 RC disk does the same thing even though when the hard drive was blank it could install Ubuntu okay.

What do I have to do? Do I have to wipe out my hard drive to get Ubuntu to re-install?

---

### Post by tahitiwibble on 2008-11-11
Are you sure that you hit "Quit and **Save**" when you exited the BIOS?

---

### Post by Tatty on 2008-11-11
No you wont have to wipe your hard disk.  Booting from the live CD has nothing to do with what you already have installed on your hard drive, as this all happens before any data is read from the HDD.

You simply need to do what you did when you installed it first time.  Perhaps you have overlooked something, its easy to do. Carefully check each step in getting the CD to boot.

Perhaps the CD has gotten damaged somehow?  You may need to burn a new CD.

---

### Post by Shwefty on 2008-11-11
I also had a problem that my Live CD didn't spin up in time to be recognized by my BIOS (so then it just assumed there was no disc and went to hd).  If you can rig it up so that the cd is spinning whenever you select the boot from CD/DVD, that may help you too.

---

### Post by tnewt on 2008-11-12
I just did it!

I had changed the disk mode to something like AHCI which somehow made it unable to boot from the CDROM. When I remembered this change, I changed it back, then it was able to boot from the CDROM.

I've re-installed, and I still have my home directory. Cool!

Thanks for the replies!

---

