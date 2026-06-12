---
title: "Re-install 12.04 question"
date: 2014-04-11
forum: New to Ubuntu
---

### Post by riverguy99 on 2014-04-11
Dell D620 with 12.04 installed side-by-side with XP. I'm having all sorts of issues with this installation that remain unresolved and are getting worse, so I would like to re-install Ubuntu.  I did another laptop with dual-boot, but the other one I did using the "other" install option, the one in which I had to create a partition for Ubuntu.  That one works flawlessly.  So my question is, is there a way to remove Ubuntu from this machine completely and then start all over with a clean, fresh install?  I want nothing left of the old installation to muck up the new one!

This will take hours, as I have spent much time getting this installation and all my apps running sweetly, but I'm game to do it if it is possible.  I did this and the other (successful) installs from a downloaded ISO file on a USB stick.  I'd like to do this one the same way.

Willl this work, or am I asking for even more issues?

---

### Post by nerdtron on 2014-04-11
It will work. If you want a fresh install of ubuntu on that laptop, create a bootable USB stick, boot from it and then install Ubuntu by choosing the "Erase everything and install Ubuntu" option on the installer.

---

### Post by riverguy99 on 2014-04-11
OK, but what I want to accomplish is to still have a dual boot, so I don't want to wipe the drive for an Ubuntu-only install.  If I use the same ISO USB I did last time and for my other laptop, will it overwrite the old install, or leave some of the stuff behind that is causing me all these problems?

---

### Post by nerdtron on 2014-04-11
> **riverguy99 said:**
> OK, but what I want to accomplish is to still have a dual boot, so I don't want to wipe the drive for an Ubuntu-only install.  If I use the same ISO USB I did last time and for my other laptop, will it overwrite the old install, or leave some of the stuff behind that is causing me all these problems?

You still want to dual-boot. That is a bit more complicated. But since you are familiar with the "Other" method or the manual partitioning method, you'll be fine.
1. Boot in the live usb.
2. Choose "Other" on the installation option.
3. You'll see that you ubuntu partitions there are already created from your previous install. 
4. Just do what you want here, like what you did on the other laptop. Delete the ubuntu and recreate a partition for root and swap.
5. Continue with the installation.
Upon reboot, it will be a fresh ubuntu with dual boot.

---

### Post by riverguy99 on 2014-04-11
OK, I'll do it.  It will end the pain, and hopefully, it will work right this time.  One more question, kinda not related but maybe, when I get on the forum and try a dozen different suggested  terminal entries to fix a problem and none of them work, is it likely that those entries make changes that then become problems of their own?  I've always been curious about that, kinda like making arbitrary changes in the Windows Registry?

---

### Post by nerdtron on 2014-04-12
Yes they do so be sure that you always try your best to understand what the commands do before you run them. And also, try to remember the error so that you can post them here and hopefully we can revert back or post possible solutions.

---

### Post by riverguy99 on 2014-04-12
> **nerdtron said:**
> You still want to dual-boot. That is a bit more complicated. But since you are familiar with the "Other" method or the manual partitioning method, you'll be fine.
1. Boot in the live usb.
2. Choose "Other" on the installation option.
3. You'll see that you ubuntu partitions there are already created from your previous install. 
4. Just do what you want here, like what you did on the other laptop. Delete the ubuntu and recreate a partition for root and swap.
5. Continue with the installation.
Upon reboot, it will be a fresh ubuntu with dual boot.

Thank you for the feedback on the terminal command thing.  Si if I do a terminal command to fix a problem and the command does not fix it, shouldn't I then UNDO whatever changes I made that didn't work?  My concern, and maybe this is what has happened to this machine, is that if I try a dozen suggested changes and none works, I have more than likely caused some other problems with all the changes.  

Back to the original question, it just occurred to me that you said, "You'll see the partitions your ubuntu partitions there already . . ."  The thing is, I did a side-by-side install on this one so no partition was created for ubuntu.  I want to do the new install so that no trace of the original install remain, but this time I will choose the "Other" method.  So if I just do another "boot from the usb ISO," will that remove the installed ubuntu before installing the new one?  If not, is there a way I can accomplish this without formatting my hard drive?

Thank you for your patience!

---

### Post by nerdtron on 2014-04-12
> My concern, and maybe this is what has happened to this machine, is  that if I try a dozen suggested changes and none works, I have more than  likely caused some other problems with all the changes.
Some commands need to be undo like installing something something or changing some system files, some don't do anything if they don't work at all. It depends on the commands.

> The thing is, I did a side-by-side install on this one so no partition  was created for ubuntu.  I want to do the new install so that no trace  of the original install remain, but this time I will choose the "Other"  method.  So if I just do another "boot from the usb ISO," will that  remove the installed ubuntu before installing the new one?  If not, is  there a way I can accomplish this without formatting my hard drive?

Install side-by-side is the same thing as using the "Other" method, it's just that the installer creates the partitions for you (and you don't see it in the background)
When you boot from USB and then choose "Other" and then see the Ubuntu partitions, select it and delete/format that partition. Then recreate that partition and then install Ubuntu again. This is technically a fresh install.

---

### Post by riverguy99 on 2014-04-12
OK, I'll give it a try.  The reason I was apprehensive about it is that in the "other" install that I did in which I actively created a partition for Ubuntu, the whole file system appears differently.  I can see the Ubuntu partition when I boot into Windows and I can see the Windows files when I've booted into Ubuntu.  On this machine (with which I took the side-by-side option), I can't see the Windows files from inside Ubuntu and Ubuntu partitions do not show up in Windows.  

I'll give it a try later this evening.  Thank you for your patience.  I'm trying really hard to get this all down!  :)

---

### Post by nerdtron on 2014-04-12
Well that is weird. Is that a wubi install?

---

### Post by riverguy99 on 2014-04-12
No, It was installed from the downloaded ISO for 12.04.  I'm downloading again right now just to make sure I have a clean copy and will give it a try straight away,

---

### Post by riverguy99 on 2014-04-12
OK, the beat goes on.  I tried to boot from the usb just as I had done before.  I get this: " No DEFAULT or UI configuration directive found." I tried the usb with the fresh downloaded ISO from Ubuntu in another identical laptop and got the same response, so it must have something to do with the download?  As I remember, this is the same way I've installed 12.04 on four other machines now so what am I doing wrong?

(On each computer, I changed the boot sequence to usb first.)  I tried it both with the "change boot order" F12 option and also from F2 setup. Same results.)

---

### Post by nerdtron on 2014-04-13
What did you use to create a bootable USB from the ISO? And be sure to format the flash drive with FAT32

---

### Post by riverguy99 on 2014-04-13
> **nerdtron said:**
> What did you use to create a bootable USB from the ISO? And be sure to format the flash drive with FAT32

I downloaded "Ubuntu-12.04-desktop-amd64.iso" from the Ubuntu download site, copied it from my "downloads" folder to a freshly formatted (FAT32) 4GB USB stick, and used that to try booting the computer.  That's the same process I used on several other computers and it worked fine, so what the heck am I doing wrong this time??

Before when I tried booting from the USB it gave me the "No DEFAULT or UI configuration directive found" message,  This morning, and another newly formatted USB stick, all I get is a flashing "_" in the upper left corner of the screen.

Something so simple . . .

---

### Post by riverguy99 on 2014-04-13
EUREKA!  It worked!  I googled this issue and came up with the suggested to use Ubuntu's Startup Disk Creator.  Like that should have been somewhat obvious except that I had never heard of it before.  Anyway, I did that and I now have a fresh install on my machine.

Thank you for your patient assistance, all who replied!

---

