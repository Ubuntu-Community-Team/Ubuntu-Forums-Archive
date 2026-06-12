---
title: "[SOLVED] 16meg laptop swap floppy/non bootable CD"
date: 2008-05-12
forum: Other OS Talk
---

### Post by volkswagner on 2008-05-12
I want to mess with a minimal install.  I have a Toshiba 420CDS laptop.  It has a CDrom which is not able to boot according to bios.  I can get another laptop with a floppy drive.  This will give me two machines.  The drives are swap drives.  I can't have both in at the same time.

What would be my best solution to get a HD install for DSL, or puppy?  The HD is only 1gig and empty.  Shall I install one of the floppy based linux to HD small partition?  Then boot that to get CD rom support?  Can I boot a small floppy linux to ram, then swap out the drive for the CDrom install?

The laptop is without USB, modem, ethernet.  You may ask what the heck is it good for.  I am wondering myself.  I would like maybe some kids games/applications. Or I may try to get an inexpensive PCMIA soulution.  Either ethernet, or usb.

---

### Post by darrelljon on 2008-05-12
What you want to do, is install a floppy Linux distro to the HDD. Installing it to RAM then attempting to swap drives probably won't work. Once you've installed a floppy distro to the HDD you could consider installing a CD distro.

Some distros to consider include;
[BasicLinux]("http://distro.ibiblio.org/pub/linux/distributions/baslinux/")
Mungkie
Blueflops
and
Grey Cat

Let us know how you get on.

---

### Post by volkswagner on 2008-06-05
OK.  I need some help.  I can boot with basic Linux.  I don't know how to install to HD.  I tried smart boot manager.  This would be best if I could install to HD.  I don't know how to get around no boot from CD.  Even if I get a floppy distro on the, how will this help me get a CD distro?

---

### Post by tgalati4 on 2008-06-05
I had an old omnibook with a 4 gb drive.  I took the drive out and using an IDE-to-notebook-drive adapter ($6) put it an a desktop machine and loaded DSL.  Put the drive back in and it booted.  Of course this machine had 32 MB so it can run DSL OK.  16 MB will only get you a command line.  I think 24 MB is the minimum to get a graphical environment.

---

### Post by volkswagner on 2008-06-05
> **tgalati4 said:**
> I had an old omnibook with a 4 gb drive.  I took the drive out and using an IDE-to-notebook-drive adapter ($6) put it an a desktop machine and loaded DSL.  Put the drive back in and it booted.  Of course this machine had 32 MB so it can run DSL OK.  16 MB will only get you a command line.  I think 24 MB is the minimum to get a graphical environment.

I was afraid that would be my only way out.  I considered dismantling a pocket USB for that.  Did you just copy the CD contents?  What distro would be best?  Basic Linux GUI runs well.  I gather it's because it is loaded to RAM.

---

### Post by jariku on 2008-06-05
I recently installed DeLi Linux 0.7.2 on a Pentium 133 with 1,6 gigabyte HDD and 16 megabyte RAM using boot floppies and a CD. It runs IceWM quite all right, but I made a 150 megabyte swap partition just to be sure. Also, I turned the swap on before I started the install process. The newest version of DeLi Linux (0.8.0) needs 32 megabytes of RAM, so it was out of the question.

What comes to your problem with the floppy or cd situation, you could try installing via null modem connection from another computer. I haven't tried it myself but I think you should be able to install DeLi with it. Another possibility might be having the CD ISO image on the HDD and booting to it with boot floppies (DeLi Linux boot floppy images are included in the 0.7.2 CD).

Here are links to the DeLi Linux website and a mirror where I downloaded the 0.7.2-big ISO image, which contains IceWM and Fluxbox (I couldn't find a download link for it from the official website). The smaller ISO is for a command line system only. I hope this helps.

[http://www.delilinux.org/](http://www.delilinux.org/)
[http://darksnow.radiolivre.org/deli/](http://darksnow.radiolivre.org/deli/)

EDIT: I forgot to mention that I used the boot floppies because I couldn't boot from the CD even with a sbootmgr floppy.

---

### Post by volkswagner on 2008-06-05
I connected a null modem cable to my ubuntu box and the laptop.  I don't know how to get ubuntu to recognize the connection.  Where to look?  While I am running basic linux, bash does not recognize sudo.  I tried to mount the cdrom in basic linux.  It warned cdrom was not in /etc/fstab.  I do not know how to edit files in basic linux.  I may need to join the mailing list unless someone is familiar here.  Is there a service I can restart to get the kernel to see the cdrom?

---

### Post by volkswagner on 2008-06-05
I found the editor.  vi=e3vi.
I added the following to /etc/fstab
```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

When I try to mount it it get

```
mounting /dev/hdc on /media/cdrom0 failed: no such device
```

I checked dmesg after swapping the drives, last line read.

```
VFS: Disk change detected on device fd(2,0)
```

---

### Post by volkswagner on 2008-06-06
I copied the DSL files to the HD with my usb drive.  I removed the existing 2.5" drive and installed the laptop drive.  It seemed odd there were just a boot, knoppix and lost&found folders.  Plus there was an .html file.  The laptop would not boot.  It said missing OS.  I think there may be permissions problems.  I had to run nautilus as root to change the drive permissions when adding the DSL files.  I tried the DSL boot floppy and failed.  I also tried smart boot manager and it showed a zero for HD.  It should have showed two drives as I made another small linux partition.  Is it possible the machine can't utilize ext3 file system?

I even used a win 98 boot disk to run fdisk.  My installed boot partition was listed as non dos and active.  I thought I may need to set it as active.  :(

After the no boot, I reconnected the drive via usb.  The drives are locked.  

Is there a good distro to allow this type of install directly to the HD, located outside the pc.

---

### Post by volkswagner on 2008-06-07
Here is what I learned.

zmjjmz said:
> Google Smart Boot Manager, you'll appreciate it.
Also, DSL seems like a but much for that, how Linux savvy do you think you are?
If you think you'd be comfortable with some pretty hard stuff you can try [http://www.basiclinux.com.ru](http://www.basiclinux.com.ru)
It fits on two floppies, runs well with 12MB RAM, and those computers will run it pretty well.

The ram seemed to be an issue.  I swapped a 42meg module from another laptop.  This eliminated kernel panic.

Using the USB route to load the os failed.  The installer would not load bootloader to the usb drive.

I was able to install the drive into another laptop.  I booted with DSL in CDrom.  Used the installer.  The key was when the installer finished, not to let the system reboot in the host machine.  I had to swap the drive to the old laptop and finish the installer (passwords, vesa, etc.)

I just need to find the correct pcmcia card to get lan or wlan.  It is the old style, new cards have a differen interlock and are not recognized by the system.  :(

The idea of swapping the drive came as a side note from earlier poster suggesting the drive adapter.

I think DSL is a good choice for this type of hacked install since when installed to the HD, it still scans hardware on each boot and loads appropriate drivers.

EDIT:  I forgot to mention.  I did not realize how light weight windows 95 is.  4meg ram min, 8meg recommended.  It runs well with the 16meg module.  It also states 70meg hard disk space.

---

