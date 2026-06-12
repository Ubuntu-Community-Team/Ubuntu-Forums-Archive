---
title: "Creating a duel boot question"
date: 2013-01-22
forum: New to Ubuntu
---

### Post by waltd on 2013-01-22
Hi all,  
I've very new to Linux and Ubuntu.   I'm running LiveUSB with   Ubuntu Desktop, version 12.10, 64bit on a flash drive with persistent  memory set to maximum. (4Gig).   I used LiLi Creator to create the LIveUSB.  All is looking great!  Everything is working fine.  
   
Now I'm interested in creating a duel boot with Windows 7 (which is already installed) and Ubuntu Desk Top, 12.10, 64bit.  But I don't want to touch my PC's hard disk drive that I have Windows 7 on.  I have two USB hard disk drives connected to my laptop by USB.  Can I use one of these USB HDD to install Ubuntu into?  Is there a problem installing Ubuntu into a USB HDD rather than my PC's HDD?  Is there any danger to corrupt Windows 7 if I use a separate HDD than Windows is on?  Any problems, concerns, helpful tips?  Thanks all.  :D

---

### Post by sudodus on 2013-01-22
Welcome to the Ubuntu Forums :-)

This is possible, and should work quite well. But there are a few things to discuss.

Do you have USB 2 or USB 3? USB 2 is much slower than running from an internal drive.

Do you have a

1. desktop, workstation or
2. laptop, netbook?

If you have desktop or workstation you can install a second internal HDD (or SSD) for Ubuntu.

Do you have an eSATA or eSATA/USB port? Then you can connect an eSATA external drive, which is as fast as a SATA 3 Gb/s internal drive.

---

### Post by waltd on 2013-01-22
Thank you sudodus for your kind welcome and answer.  I'm glad to be here.  I'm enjoying using LiveUSB Ubuntu with persistent memory.  That's why I want to migrate to Unbuntu, but slowly, step by step.       
I have a three old HP laptop with USB 2.  (No USB 3).    
I'm not sure about eSATA or eSTAT/USB but I can get the answer and post it.  Using eSATA would be a good way to go, but I need to see if I have it.  I'll post my findings soon.

---

### Post by sudodus on 2013-01-22
If you are stuck with USB 2, I suggest that you test both to clone your live flash drive to one of the USB HDDs. And make a standard installation to the other USB HDD.

It works, but writing a lot of small files via USB is very slow, so updating will be extremely slow, and if you disconnect it before it has finished writing, the file system might be (probably will be) corrupted. So be patient!

You can run the command ```
sync
``` in a terminal window and wait until it returns to prompt. This is a way to see when the writing has finished.

In any case, it is good to take frequent backups of the USB systems. Then you can easily restore it, if the file system is corrupted.

By the way, it is possible to have a casper-rw partition instead of a casper-rw file for live persistence. Then there is no size limit (4 GB).

---

### Post by waltd on 2013-01-22
Good news.  I have an eSATA/USB external port.  I'll buy an external eSATA drive for this port to install Ubuntu on.  Also, creating a casper-rw partition is a good idea.  I'll do that next I'm waiting for my  eSATA drive to arrive.  Can you suggest a document that's easy to follow for a newbie, on how to create a casper-rw partition?  Again thanks sudodus.  I truly appreciate your help.

---

### Post by sudodus on 2013-01-22
> **waltd said:**
> Good news.  I have an eSATA/USB external port.  I'll buy an external eSATA drive for this port to install Ubuntu on.  Also, creating a casper-rw partition is a good idea.  I'll do that next I'm waiting for my  eSATA drive to arrive.  Can you suggest a document that's easy to follow for a newbie, on how to create a casper-rw partition?  Again thanks sudodus.  I truly appreciate your help.

+1
Yes good news :-)

I recommend using ***gparted***, which is available on the live Ubuntu drive. See this link
[[COLOR="Red"]http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/[/COLOR]]("http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/")

---

### Post by waltd on 2013-01-22
I read the document.  It looks easy.  I found the GParted program.  But I have a question.  Please let me know if I am right or please correct me if I'm wrong on this point.      
                                     
I am to have  *Two*  LiveUSB flash drives for Ubuntu.  One LiveUSB flash drive I use to boot up Ubuntu and I do not modify this flash drive, but I leave it alone.    The second flash drive I connect to my PC and do the modifications on.  Then I do future bootups on the second flash drive.

---

### Post by waltd on 2013-01-22
Also one more question.  The document says to delete the existing casper-rw file.  I did a search for the casper-rw file on my current LiveUSB and could not find the file.  How do I delete the file?  Thanks.

---

### Post by sudodus on 2013-01-22
> **waltd said:**
> I read the document.  It looks easy.  I found the GParted program.  But I have a question.  Please let me know if I am right or please correct me if I'm wrong on this point.      
                                     
I am to have  *Two*  LiveUSB flash drives for Ubuntu.  One LiveUSB flash drive I use to boot up Ubuntu and I do not modify this flash drive, but I leave it alone.    The second flash drive I connect to my PC and do the modifications on.  Then I do future bootups on the second flash drive.
Well yes, this is possible and safer than to tamper with the first one.

But you wrote, that you want to use a USB hard disk drive, and later on that you have eSATA. Then you don't need a new USB pendrive.

You can make a persistent system directly on an external eSATA hard disk drive, or make it on a second pendrive, and later clone it to the hard disk. ***With the high speed of eSATA it is even better to put a regular installed system onto it.***
--
I have an Ubuntu system in an eSATA box with an SSD drive. It works very well.

If you want it portable between computers, you should not install any proprietary drivers. Otherwise, if you intend to use it for only one computer, you can install anything, that would work with an internal drive (including proprietary drivers).

---

### Post by sudodus on 2013-01-22
> **waltd said:**
> Also one more question.  The document says to delete the existing casper-rw file.  I did a search for the casper-rw file on my current LiveUSB and could not find the file.  How do I delete the file?  Thanks.

Don't delete it! You are not supposed to delete it when booted from the pendrive itself, it's like cutting the tree you are sitting on.

At least not now (unless you want to test with this only(?) pendrive. Then you can do anything with it, wipe it, repartition and reformat ...)

If Ubuntu, it should be a (max) 4 GB file with the name casper-rw in the root directory of the boot partition of the pendrive.

---

### Post by waltd on 2013-01-23
Hi Sudodus,  thanks for all your help.  I truly appreciate it.  I like Ubuntu a great deal and I'm greatly enjoying working with it and the Linux world.  I'm looking forward to other projects with Ubuntu such as getting OpenVPN to work.  That's my next project.  Have a good day.

---

### Post by sudodus on 2013-01-23
You are welcome and good luck :-)

---

