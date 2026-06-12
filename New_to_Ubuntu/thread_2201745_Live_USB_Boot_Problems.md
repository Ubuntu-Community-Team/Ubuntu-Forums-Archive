---
title: "Live USB Boot Problems"
date: 2014-01-25
forum: New to Ubuntu
---

### Post by Nick_Smith on 2014-01-25
I have a Live USB running Ubuntu for a class on Software Radio.  The Live USB shows up in Windows as "Ettus Research LiveUSB SDR Env"  The day I got it, it worked fine but lately it has been having trouble trying to boot.  At some point in the boot process, it encounters an error and goes to the command line.  This is what it displays:
```
(initramfs) umount: can't umount /cdrom: Device or resource busy
mount: mounting /dev/sdd2 on /cow failed: invalid argument
can not mount /dev/sdd2 on /cow
```

Can anyone help me solve this or at least tell me what is causing it?

---

### Post by sudodus on 2014-01-26
Welcome to the Ubuntu Forums :-)

Did you get the live USB running Ubuntu (instead of making it yourself)?

I think it is damaged (the file system or some file in the file system). This can happen if it is a 'persistent live' or 'installed system' in a USB drive, and you unplug it before it has finished writing buffered data to disk. It can take minutes to finish if it is a slow pendrive, so this is a common cause of damaged systems.

If there is a 'light' damage of the file system you might be able to repair it, but not from Windows. You need to boot a computer from another linux system to do it. If this is not feasible for you, you'd better get a new pendrive (with that system installed).

The problem might also be that the pendrive works well in some computers, but not in some other computers depending on the hardware and firmware of the computer.

As you notice, I'm only guessing. It will be easier to give relevant advice, when you describe the problem with more details, and also what you can do with linux.

---

### Post by Nick_Smith on 2014-01-27
I did receive the drive with Ubuntu pre-installed (I paid $20 for it because my college's IEEE Club was able to get us a discount as it would normally cost closer to $50).  I do have another system running linux (Lubuntu, i don't remember which version) and would be very appreciative of receiving a step-by-step walkthrough of how to fix the file system

EDIT: I just tried a few things in the command line it goes into and confirmed that "/etc/fstab" is MISSING.  I found [a page on the official Ubuntu site]("https://help.ubuntu.com/community/Fstab") that explains the syntax for fstab but the command line does not appear to have any kind of text editor and I'm not 100% sure how to set up the fstab file

---

### Post by sudodus on 2014-01-28
I think the easiest solution might be that you ask the vendor of the pendrive with the preinstalled system of the web address to an iso file or other image file containing the system. Then you can download that file and install it (overwriting the present and damaged system). If you show some evidence of buying it (receipt, internet bank transfer number ...) the vendor should help you with that. And I can help you flashing it to the pendrive.

But it might also be possible to try to repair the file system or /etc/fstab from Lubuntu.

When booted into Lubuntu, connect the pendrive. Unmount it without ejecting it.

Run ```
parted -l
``` to identify its root partition. Let us say it is **/dev/sdxy** (x=b or x=c ..., and y=1, y=2 ...), typically /dev/sdb1

Unmount with ```
sudo umount /dev/sdxy
```

Then run ```
df 
```to see that it is no longer mounted, and then try to repair the file system with
```

sudo -f e2fsck /dev/sdxy
```

---

### Post by sudodus on 2014-01-28
/etc/fstab can be created with that of Lubuntu as a template, but you need to edit the UUIDs to match those of the partitions on your pendrive (the root partition and the swap partition).

---

### Post by Nick_Smith on 2014-01-28
just did all of that and then (after the command line returned to normal input where it shows the username and working directory) shutdown the system and booted from the LiveUSB and it worked! thank you so much for your help :)

---

### Post by mörgæs on 2014-01-28
Good, please mark the thread 'solved'.

---

