---
title: "&quot;bootmgr missing&quot; help"
date: 2012-07-30
forum: New to Ubuntu
---

### Post by hillaryshaffer on 2012-07-30
I am an absolute beginner. Today I installed Ubuntu from Windows 7, then deleted Windows 7 using OS Uninstaller. I ran updates and restarted and got a "bootmgr missing" error. I can't get past it. How can I fix this? I've read about boot installer but wondering how I run it if I can't get to anything. Will burning it to a CD make it autostart? Sorry I'm so new to this. Any help is appreciated. Thanks.

---

### Post by electricmaster on 2012-07-30
I've had a lot of problems with this. If you *just* install Ubuntu, the easiest thing to do would be to start over and it'll install GRUB instead. If not, boot into a live CD via CD-ROM or flash drive and run grub-install. I'm not too good with GRUB though and GRUB2 (latest) is pretty finicky.

---

### Post by levlaz on 2012-07-30
+1 on starting over.. installing grub from the live CD may be more trouble than its worth - especially since the install only takes about 15-20 minutes these days.

---

### Post by oldfred on 2012-07-30
Sometimes a full reinstall is the easiest for new users.

But we often like to try to fix things, sometimes it takes days, when a reinstall may be an hour. :)

You can see if this installs grub, if not run the BootInfo report and post link.
Bootmgr is Windows boot loader, so it still has Windows in the MBR and is trying to boot Windows.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by audiomick on 2012-07-31
> **hillaryshaffer said:**
> ...Today I installed Ubuntu from Windows 7, ...

I can't help but wonder if it might have been a Wubi install. In this case, as far as I know, it will have been removed along with the Windows.

If the Ubuntu install is really fresh, I would also suggest doing it again. 

Well done, by the way, on getting rid of Windows in one fell swoop. ;)

---

### Post by Mark Phelps on 2012-08-01
> **hillaryshaffer said:**
> I am an absolute beginner. Today I installed Ubuntu from Windows 7, then deleted Windows 7 using OS Uninstaller. I ran updates and restarted and got a "bootmgr missing" error. 

That's because (1) you installed Ubuntu from INSIDE Windows, so when you removed Windows, you removed Ubuntu as well, and (2) the Wubi install relies on the Windows boot loader to produce the OS Selection menu -- which you removed when you removed Windows.

You should boot from CD or USB and install Ubuntu that way.

---

