---
title: "Black screen w/error message when installing ubuntu from USB drive"
date: 2013-12-14
forum: New to Ubuntu
---

### Post by alelliot on 2013-12-14
I am currently running ubuntu off a USB drive-- the desktop edition-- which I installed with UNetbootIn. I want to install ubuntu within windows 7, or make a partition, so that I can continue running Windows 7 as well as ubuntu. Upon startup, I can only select "Try ubuntu without installing it" option. When I run the "install ubuntu" wizard program on my desktop, and select the "run ubuntu inside windows 7" option, a black screen with what I assume is an  error message appears. It flashes by so fast I can't read it and then  restarts. I've tried taking a screenshot and taking a picture with my  phone but it's simply too fast. The same thing happens when I select "Install Ubuntu" from the boot menu upon startup.

I decided to try to create a hard drive partition on my own instead of letting the wizard do it for me using [this guide.]("https://help.ubuntu.com/community/HowtoPartition/CreatingPartitions") The first attatchment to this post is what Gparted looks like right now. I selected "information" for /dev/sda2, only to receive several error messages: "Cluster 14524911 is referenced multiple times! Cluster 14524912 is referenced multiple times! Cluster 14524913 is referenced multiple times!..." etc., etc. You can see the full error message in the second attachment here.

I am very much a noob to ubuntu/linux, especially with installing it-- this is my first time. I'm not really sure where to start with this. Obviously I tried googling it, but the error is so specific I couldn't get much. I think something might be wrong with my memory? Is that what the message means by referencing clusters?

Any help would be greatly appreciated. Let me know if you need any more hardware information.

---

### Post by sandyd on 2013-12-14
> **alelliot said:**
> I am currently running ubuntu off a USB drive-- the desktop edition-- which I installed with UNetbootIn. I want to install ubuntu within windows 7, or make a partition, so that I can continue running Windows 7 as well as ubuntu. Upon startup, I can only select "Try ubuntu without installing it" option. When I run the "install ubuntu" wizard program on my desktop, and select the "run ubuntu inside windows 7" option, a black screen with what I assume is an  error message appears. It flashes by so fast I can't read it and then  restarts. I've tried taking a screenshot and taking a picture with my  phone but it's simply too fast. The same thing happens when I select "Install Ubuntu" from the boot menu upon startup.

I decided to try to create a hard drive partition on my own instead of letting the wizard do it for me using [this guide.]("https://help.ubuntu.com/community/HowtoPartition/CreatingPartitions") The first attatchment to this post is what Gparted looks like right now. I selected "information" for /dev/sda2, only to receive several error messages: "Cluster 14524911 is referenced multiple times! Cluster 14524912 is referenced multiple times! Cluster 14524913 is referenced multiple times!..." etc., etc. You can see the full error message in the second attachment here.

I am very much a noob to ubuntu/linux, especially with installing it-- this is my first time. I'm not really sure where to start with this. Obviously I tried googling it, but the error is so specific I couldn't get much. I think something might be wrong with my memory? Is that what the message means by referencing clusters?

Any help would be greatly appreciated. Let me know if you need any more hardware information.

Have you tried scanning your disk in windows?
In Windows, right click the drive, select properties, and go to the tools tab where you can scan your drive
[IMG]http://gyazo.com/7200b850df2af3b5d6f4a24200ac2b43.png[/IMG]

---

### Post by Gone fishing on 2013-12-14
I would suggest first checking and defraging Windows as in the post above, then resizing the Windows ntfs partition from Windows. Windows 7 can do this then install into the freespace created [http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

