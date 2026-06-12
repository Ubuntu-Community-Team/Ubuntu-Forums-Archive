---
title: "Restart/suspend problem, mounting Vista partition"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by hobs on 2008-08-08
I've installed Kubuntu Hardy on a Vostro 1000 with KDE 4 and I usually run the gdm session. In gnome, the computer is not able to restart.  It seems like it is going to restart itself and turns off all of the network connections, etc. and then hangs with a blank black screen.  At that point I manually turn it off and back on again with no problems, but I would like it to be able to restart normally.  

I also, like other people, get an annoying error after a successful suspend and I would also like to have my computer suspend when I close the lid, instead of just locking the session now.

This may sound stupid, but in KDE 4, how do I suspend the computer?

I also want to mount my Vista partition and I know that I should edit /etc/fstab for that, but I'm not really sure what to do.  

Thanks for the help!

---

### Post by bobnutfield on 2008-08-08
The restarting problem in Gnome is more than likely a problem with ACPI.  Do you have it turned off for any reason?  Suspend problems with Ubuntu (or most Linux distros for that matter) are well known.  I can't really help you with that, other than to say to search the forum using "suspend" in the search bar.  I gave up on it long ago on my laptop.

You should not have to edit your fstab file to mount your Vista partition unless you want it to automatically mount at boot time.  If you just want to mount, you should be able to do it in Places>Removable Media>.  This is how I mount my Windows partion.  It usually shows up as "31.1GB Media" (or similar on your machine.  If you want to mount it from the command line, you can do it with:

> sudo mount -t ntfs /dev/sda1 /mnt/Vista

This is assuming you Vista is located on the first partition of the first disk and you want to mount it to the created directory of /mnt/Vista.

---

### Post by hobs on 2008-08-08
Thanks for the reply.  

I don't know if this helps, but in acpi-support I have:

ACPI_SLEEP=true
ACPI_HIBERNATE=true
ACPI_SLEEP_MODE=mem
HIBERNATE_MODE=shutdown

I ideally want to automatically mount my vista partition at boot time.  Right now, to load it I open the /media/OS file and all of the files from my vista partition that I need are available.  I'm guessing the mount point is /media/OS, but I don't know what the file system is for /etc/fstab.

---

### Post by bobnutfield on 2008-08-08
I haven't used Vista in a loooong time, but I believe it is still NTFS that it uses.  If that is the case, an edit in your fstab file similar to this would mount it at boot:

> /dev/sda1   /media/OS   ntfs   defaults,umask=002,uid=500,gid=500  0  0

I don't automatically mount my Windows partition now, but in the past when I did this is what I used.

The ACPI config you have should be ample to control the suspends function but many are still having trouble with it, even though it is configured in the kernel correctly.  There a bug called the "8254 Timer Not Connected" bug.  You may or may not see this come up immediately after grub starts loading the system.  I cannot confirm that it has anything to do with the suspend problem, but I suspect it does.  This bug does not have any other ill effect on my machine, but I cannot properly suspend either.

---

### Post by hobs on 2008-08-08
Thanks for the fstab help.  Is there a way to test it before I restart with the new file?

So the ACPI looks ok for suspend? What about restart?

---

### Post by bobnutfield on 2008-08-08
> **hobs said:**
> Thanks for the fstab help.  Is there a way to test it before I restart with the new file?

So the ACPI looks ok for suspend? What about restart?

Fstab is there to mount files systems at boot, so I do not believe it is testable outside of rebooting.  But the sample I gave is just a sample and may not represent which partition your Vista is installed to.  But, I am sure you know where that is.  If you used that example and it is in fact on /dev/sda1, then when you reboot you should find Vista already mounted on /mnt/OS, which you could place on your desktop if you wanted.

After spending literally weeks trying to get suspend to work, I doubt if I could help you with that one, but hopefully someone else will chime in.

---

