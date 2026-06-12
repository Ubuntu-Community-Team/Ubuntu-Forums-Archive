---
title: "first boot problem"
date: 2013-04-04
forum: New to Ubuntu
---

### Post by mrrog on 2013-04-04
Just installed lubuntu on a 32 bit netbook using the bootable usb installer, now to boot up I have to have the boot usb inserted, but when its booted it appears to be on the hard disk and I can use the software thereafter without the usb in?

I've messed about with the boot order and changed it from 'dos/unix/novell' to 'other', but I still need to have the usb in to boot up?

any ideas on what's happening would be most appreciated,

thanks

---

### Post by r.stiltskin on 2013-04-04
Not only do you not need it, after completing the installation you _should not_ boot with the usb drive.

If you can't boot without the usb drive there's something wrong with your installation.

---

### Post by Rex Bouwense on 2013-04-04
+1.  Unmount the flash drive and boot normally.  If it will not boot, then as has already been stated you have a problem with the installation.  Did the md5sum come out correct.  What program did you use to burn it to your flash drive?

---

### Post by black veils on 2013-04-05
try running this command ```
sudo grub-install sda
``` while in the hard drive system. after it has finished, reboot without the usb plugged in.

---

### Post by mrrog on 2013-04-08
The command did not run, something about not finding SDA, still the command line sent me searching and I eventually downloaded band run something called boot-repair, seems to have done the trick, or have I done something awful?

---

### Post by Bashing-om on 2013-04-08
Nope, not a thing in-correct in running boot-repair; see:
[http://ubuntuforums.org/showthread.php?t=1769482&page=2&highlight=boot-repair](http://ubuntuforums.org/showthread.php?t=1769482&page=2&highlight=boot-repair) for full documentation/usage .

Pleased you are up and going ![INDENT=4]
welcome to ubuntu

[/INDENT]

---

