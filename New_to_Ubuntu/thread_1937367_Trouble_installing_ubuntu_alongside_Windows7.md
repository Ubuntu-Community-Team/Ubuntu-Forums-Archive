---
title: "Trouble installing ubuntu alongside Windows7"
date: 2012-03-07
forum: New to Ubuntu
---

### Post by SandiB on 2012-03-07
After successfully installing ubuntu on an old thinkpad using a usb, I'm trying to install it on a aspireoneD255 netbook.

The problem is in the Installation Type menu, there is no choice to Install Ubuntu alongside Windows7, I have took a screen-shot of the page when i select Something Else. I have no idea what any this means, so do not know how I can install ubuntu. I do want to keep windows 7, just so its still there.
[ATTACH]213883[/ATTACH]

[ATTACH]213884[/ATTACH]

Any advice would be appreciated.

---

### Post by HeroOfCanton on 2012-03-07
Before anything else, backup anything you may need from that system. This is very important!

You are on the right track, but please explain your setup a little more so we can provide accurate help without overwriting anything you may need... What is on those individual partitions? Have you already created one for use with linux or are those all related to your current windows setup?

---

### Post by NikTh on 2012-03-07
> **SandiB said:**
> 
The problem is in the Installation Type menu, there is no choice to Install Ubuntu alongside Windows7


Are you sure that you have enough space to install ubuntu alongside windows ?

---

### Post by SandiB on 2012-03-07
I have not created any of those partitions, wouldn't know how, have done nothing to the original windows set-up. I really don't know what other information I can give you sorry.

---

### Post by Karlchen on 2012-03-07
Hello, SandiB.

In addition to what was said / advised by HeroOfCanton, let me give a first diagnosis:

Telling from **[the second screenshot]("http://ubuntuforums.org/attachment.php?attachmentid=213884")**, it seems to be pretty obvious that currently the complete disk has been assigned to Windows filesystems, either FAT32 or NTFS. No unallocated disk space seems to be available. This is why the Ubuntu installer does not offer to install Ubuntu in addition to Windows.

Very likely you will have to free up disk space by reducing the size of /dev/sda5 maybe if this should be feasible in order to get unallocated disk space which the Ubuntu installer can use for installing Ubuntu.

So the option to choose in **[the first screenshot]("http://ubuntuforums.org/attachment.php?attachmentid=213883")** whould be **Something else** which will allow you to free up currently used disk space by resizing an existing partition.

*Yet, before you simply start doing so following HeroOfCanton's advice would be really wise: please, give us details about what the existing devices /dev/sda1 through to /dev/sda5 are currently used for. In particular /dev/sda5 looks a bit confusing because GParted is unable to determine how much of this partition is in use.*
[I]But simply because it is the largest partition /dev/sda5 is the most likely candidate for reducing its size and giving away the freed disk space to Ubuntu.
[/I]
> I have not created any of those partitions Well, nevertheless you should be able to inspect the content of those partitions either from inside Windows or with the help of the Ubuntu USB live system.

Kind regards,
Karl

---

### Post by Karlchen on 2012-03-07
> **NikTh said:**
> Are you sure that you have enough space to install ubuntu alongside windows ?Currently SandiB does not have any available disk space which the Ubuntu installer could use. :(

This is why we need exact details about the nature and content of each existing partition (sda1 .. sda5) in order to be able to tell whether one of the existing partitions can be reduced thus getting free disk space for the Ubuntu filesystem and the swap space device.

Karl

---

### Post by Gremlinzzz on 2012-03-07
Windows7 doesn't give up space/ you have to make room/ does it run using live CD? don't install.see if it runs OK using live CD,Then install it using wubi so it will be easy to remove if you change your mind:popcorn:

---

### Post by oldfred on 2012-03-07
Almost all Windows 7 systems use all 4 primary partitions that MBR allows. You will have a hidden Windows boot of 100MB, your main install, then a vendor reocovery (which is just an image of drive as purchased not an installer), and then a vendor utilities partition.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by SandiB on 2012-03-07
[ATTACH]213890[/ATTACH]

I hope this is the information needed. 

> Besure to create recovery DVD(s) first. And a Windows repair CD.
I am using netbook with no dvd drive, can an external hard drive be used? 


thanks guys for the replies

---

### Post by Miljet on 2012-03-07
It appears that you are lucky. It looks like Windows is installed on a logical partition that is located inside an extended partition. So follow these steps.

1. Back up any important data. Yes, you can use an external hard drive.

2. Start Windows and run defrag. Wouldn't hurt to run it twice.

3. Use the Windows disk tools to shrink C: drive. The space you free up will be unallocated.

4. Restart Windows. It will probably want to fun chkdsk. Let it.

5. Restart Windows again just to make sure it is still working.

6. Now try again to install Ubuntu. The installer should now give you the option of installing to unallocated space. If not, select "something else", select the unallocated space and install Ubuntu to it.

---

### Post by SandiB on 2012-03-08
Thanks everyone for the response, much appreciated.

I have now successfully installed ubuntu on my netbook after following Miljet's instructions, thanks, you're a :KS

---

### Post by Mark Phelps on 2012-03-09
Glad to see you got it working.  Would you please now use the Thread Tools at the top of this thread to mark this as SOLVED.  thanks

---

