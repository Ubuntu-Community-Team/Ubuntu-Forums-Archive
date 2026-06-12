---
title: "Drive mount/unmount"
date: 2012-03-02
forum: New to Ubuntu
---

### Post by Zaxaramas on 2012-03-02
Hey, I am new to Linux and i have put the Ubuntu 12 OS on my usb drive, i was wondering if, when i boot up for the usb, if i could unmount my 'C' drive from windows, or 'OS' as Linux calls it. 

I dont see why this would be a problem, but i dont want it to be a perma-dismount because that would kinda suck when i wanted to use windows again. Thanks in advance.

Zack

---

### Post by winh8r on 2012-03-02
You can run 12.04 in "live" mode without installing it to your hard disk.

 However please be aware that 12,04 is still in the pre-release testing stages and is not due for official "stable" release until April.

It is fairly stable at the moment but be aware that you may experience some issues which have still to be worked out by the development teams.

If you have any questions or issues you should raise them in the Ubuntu +1 Precise Pangolin section of the forum.

Hope this helps you.

---

### Post by audiomick on 2012-03-02
going by your post, I assume you are talking about being in the live environment, i.e. the "try without changing" option.

Just out of curiosity, why do you want to unmount the drive that has your windows on it?

Either way, if, as I believe, your are working in the live environment, unmounting is and action that only relates to that current live session. If you unmount a drive there, it wont make any difference at all to what the computer sees when you boot without your USB drive connected.

If you have actually installed onto your USB drive, unmounting the windows partition still wont have any effect when you boot into windows.

If it is a real install of Linux, or even a live environment with persistance, I still don't belive unmounting the drive will last beyond a reboot into Linux. As far as I know, drives that are listed in the fstab file (I think it is /etc/fstab ... ) are always mounted at boot. If you unmount them, I believe it is only for the current session, as long as the fstab file isn't changed.

---

### Post by Miljet on 2012-03-02
Hi, and welcome to Ubuntu. I suspect that your definition of unmount is quite different from the way it is used in Linux/Ubuntu. The mount command attaches another partition, filesystem, or parts of another system so that it becomes a part of the file system you are currently using. The unmount (actually umount) just releases it from your current operating system.

---

### Post by critin on 2012-03-03
> Hey, I am new to Linux and i have put the Ubuntu 12 OS on my usb drive, i  was wondering if, when i boot up for the usb, if i could unmount my 'C'  drive from windows, or 'OS' as Linux calls it. Do you see the drive icon on the screen?  That just allows you to use it if you need too.  You  booted into the usb, yes?  So windows isn't mounted unless you clicked on it; in that case the icon will remain on the screen until you right click and unmount.  Yes, you can unmount IF this is the situation.  

Don't mess with the main C drive is my advice if you don't know how.  lol  There's no reason to.

---

### Post by Zaxaramas on 2012-03-03
OK, from your combined answer you have answered my question, Thanks :)

The reason i wanted to unmount my windows drive was because i thought it might get corrupt for whatever reason.

So thanks all :)

Zack

---

