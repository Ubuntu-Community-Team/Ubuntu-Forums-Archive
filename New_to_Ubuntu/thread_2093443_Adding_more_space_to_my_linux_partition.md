---
title: "Adding more space to my linux partition"
date: 2012-12-10
forum: New to Ubuntu
---

### Post by SimplySerenity on 2012-12-10
Hello, I'm running Ubuntu 12.10 as a dual boot, and when I originally installed I figured 10 gigabytes would be enough space as I didn't plan on doing a whole lot with the OS. Well now I've run out of space, and I was wondering how I could add more space to my Ubuntu partition?  I still have around 800 gigabytes left on my hard-drive so I don't think I really need to clean anything up. ^^

---

### Post by papibe on 2012-12-10
Hi SimplySerenity.

Boot into the same Ubuntu installation CD/USB. Use it a as 'Live CD' by selection 'Try Ubuntu'.

Once on the desktop, use 'gparted' to increase or move your partitions. Take a look at this tutorial: [How to Partition]("https://help.ubuntu.com/community/HowtoPartition"), specially to the section on how to increase an existing one:  [HowtoPartition/ResizingPartition]("https://help.ubuntu.com/community/HowtoPartition/ResizingPartition").

Let us known how it goes.
Regards.

---

### Post by SimplySerenity on 2012-12-10
But I didn't use a cd or usb drive to install?

---

### Post by oldfred on 2012-12-10
Is this then a wubi install that is just a file inside the NTFS partition and uses the Windows boot loader?

       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

    
       From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

    
Post this from terminal:

sudo fdisk -lu

---

### Post by papibe on 2012-12-10
Did you use Wubi?

I so, take a look at this tutorial: [Resize and Duplicate WubiDisk]("https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk").

Let us know how it goes.
Regards.

---

