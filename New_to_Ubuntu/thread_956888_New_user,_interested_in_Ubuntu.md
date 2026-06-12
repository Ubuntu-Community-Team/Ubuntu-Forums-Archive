---
title: "New user, interested in Ubuntu"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by CoreyB. on 2008-10-23
I've been looking at Ubuntu for a while now and when 8.10 is released I'm going to download it and run the Live CD for a while, make sure everything works fine, then install.

I have a Dell Inspiron 1525 laptop and have many questions:

1. Vista is preinstalled and I need to keep that intact.  I have one hard drive, so I am going to have to repartition it.  How large should I make the partition for Ubuntu, I was thinking 40-50 GB.

    1.a.  I would also like to keep the Windows bootloader, what is the safest/best way to go about this?

    1.b.  Is dual booting safe?  It won't cause a problem when Windows or Ubuntu has to restart to update itself right?

    1.c.  Is there a way to keep Vista as a 'default' OS, so I don't have to choose the OS every time, or is there a timeout in the Windows bootloader?

    1.d.  If I want to uninstall Ubuntu later, can I reclaim the partition I used for Ubuntu back to my Windows partition?

2. Does Ubuntu do a good job of cleaning up after itself when there are updates to it?  I read that Ubuntu updates itself more frequently and I don't want it to consume a lot of space on my hard drive.

3.  Is the Live CD the best way to test hardware compatibility?

4.  What is the best way to learn Ubuntu?  I saw a book on Amazon.com that was "The Official Ubuntu Book" for $30-$40.  And on Lulu.com the book by Canonicol was $60, do I have to pay that much to learn Ubuntu?

Ok, that is all I can think of for now.  I have never used any other OS than Windows, so bear with me.  Thanks in advance for any and all help in advance, can't wait only 7 days...

---

### Post by beno1990 on 2008-10-23
> **CoreyB. said:**
> I've been looking at Ubuntu for a while now and when 8.10 is released I'm going to download it and run the Live CD for a while, make sure everything works fine, then install.

I have a Dell Inspiron 1525 laptop and have many questions:

1. Vista is preinstalled and I need to keep that intact.  I have one hard drive, so I am going to have to repartition it.  How large should I make the partition for Ubuntu, I was thinking 40-50 GB.


40-50 GB should be enough to give the OS a test drive.

> 
    1.a.  I would also like to keep the Windows bootloader, what is the safest/best way to go about this?


I'm pretty sure the Windows bootloader refuses to acknowledge the presence of a non-Windows OS.

> 
    1.b.  Is dual booting safe?  It won't cause a problem when Windows or Ubuntu has to restart to update itself right?


It won't cause a problem as long as you don't mount your Windows partition in Linux and mess around with it that way.

> 
    1.c.  Is there a way to keep Vista as a 'default' OS, so I don't have to choose the OS every time, or is there a timeout in the Windows bootloader?


GRUB bootloader is very configurable, it'll timeout after a few seconds if you want it to.

> 
    1.d.  If I want to uninstall Ubuntu later, can I reclaim the partition I used for Ubuntu back to my Windows partition?


Yes, there's a way of doing that, and you'd have to recreate the Windows bootloader from inside Windows before reformatting that partition or you'd have no bootloader to boot from afterwards.

> 
2. Does Ubuntu do a good job of cleaning up after itself when there are updates to it?  I read that Ubuntu updates itself more frequently and I don't want it to consume a lot of space on my hard drive.


It often caches the packages it downloads in case you reinstall them, but it only keeps the current version of most packages so that's not much of an issue.

> 
3.  Is the Live CD the best way to test hardware compatibility?


No, you might not be able to install all of the possible kernel modules which you would if the OS were installed. The Inspiron 1525 (which is the laptop I have) requires additional kernel modules for the WiFi and webcam to work, which have to be downloaded from the repositories. But I can tell you that all Inspiron 1525 hardware is Linux compatible, Dell ship the laptop with Ubuntu installed if you choose for a Linux OS.

> 
4.  What is the best way to learn Ubuntu?  I saw a book on Amazon.com that was "The Official Ubuntu Book" for $30-$40.  And on Lulu.com the book by Canonicol was $60, do I have to pay that much to learn Ubuntu?


No, the people on the forums will help you a lot of the way. Not to mention the hundreds of Linux sites on the internet which are free of charge.

---

### Post by HittingSmoke on 2008-10-23
> **beno1990 said:**
> No, the people on the forums will help you a lot of the way. Not to mention the hundreds of Linux sites on the internet which are free of charge.

I agree, don't spend your money on a book unless that's really the easiest way for you to learn something.

I've been using Ubuntu exclusively for a few months now and everything I've learned, I learned from screwing something up and coming here for help fixing it. Its much cheaper and more fun. Everyone here is really great.

---

### Post by Paqman on 2008-10-23
> **CoreyB. said:**
> 
3.  Is the Live CD the best way to test hardware compatibility?


Absolutely, although you should have very few problems. Dell actually sells the Inspiron 1525 with Ubuntu on it, so it's fully supported. 

Check out [this thread](http://ubuntuforums.org/showthread.php?t=762770) for links to the Dell Linux wiki and links to custom LiveDVD images for your laptop. Note that these images are for the 1525N model that comes with Ubuntu, but it should be fine with the Windows version 1525, since the hardware is probably very similar (or indeed identical).

---

### Post by OutOfReach on 2008-10-23
> 
1. Vista is preinstalled and I need to keep that intact.  I have one hard drive, so I am going to have to repartition it.  How large should I make the partition for Ubuntu, I was thinking 40-50 GB.
Usually Ubuntu doesn't take up as much disk space as Windows, 40 GB is perfect but you can go lower (just make sure to not go too low).

> 
    1.a.  I would also like to keep the Windows bootloader, what is the safest/best way to go about this?
As far as I know, the Windows bootloader can only boot iteself and no other OS, you need to install GRUB (bootloader) (which will be installed when you install Ubuntu).

> 
    1.b.  Is dual booting safe?  It won't cause a problem when Windows or Ubuntu has to restart to update itself right?
Dual-Booting is perfectly safe, as long as you know what you are doing.

> 
    1.c.  Is there a way to keep Vista as a 'default' OS, so I don't have to choose the OS every time, or is there a timeout in the Windows bootloader?
You can set Vista to be the first entry in GRUB so it will boot to it when the timeout ends. 

> 
    1.d.  If I want to uninstall Ubuntu later, can I reclaim the partition I used for Ubuntu back to my Windows partition?
Sure, but defragment your Windows partition first! And you will also have to restore the Windows bootloader.

> 
2. Does Ubuntu do a good job of cleaning up after itself when there are updates to it?  I read that Ubuntu updates itself more frequently and I don't want it to consume a lot of space on my hard drive.
Yes Ubuntu does clean up after itself after an update.

> 
3.  Is the Live CD the best way to test hardware compatibility?
Sorry, I don't have an answer to this...

> 
4.  What is the best way to learn Ubuntu?  I saw a book on Amazon.com that was "The Official Ubuntu Book" for $30-$40.  And on Lulu.com the book by Canonicol was $60, do I have to pay that much to learn Ubuntu?

No! Of course not. There are plenty of online (free, of course) guides to learning/installing/using Ubuntu and Linux in general.

Hope that helped. :)

---

### Post by GuitarRocker2562 on 2008-10-23
> **CoreyB. said:**
> I've been looking at Ubuntu for a while now and when 8.10 is released I'm going to download it and run the Live CD for a while, make sure everything works fine, then install.

I have a Dell Inspiron 1525 laptop and have many questions:

1. Vista is preinstalled and I need to keep that intact.  I have one hard drive, so I am going to have to repartition it.  How large should I make the partition for Ubuntu, I was thinking 40-50 GB.

Really, anything over 10 GB would work.

    1.a.  I would also like to keep the Windows bootloader, what is the safest/best way to go about this?

Personally, I think GRUB is a much better boot loader, and you can configure it to boot Vista by default. However, if you do wish to use Vista's bootloader, see [this]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1") guide.

    1.b.  Is dual booting safe?  It won't cause a problem when Windows or Ubuntu has to restart to update itself right?

Yes, the only thing that can really mess up is user error with partitoning, just use the guide above and you will be fine.

    1.c.  Is there a way to keep Vista as a 'default' OS, so I don't have to choose the OS every time, or is there a timeout in the Windows bootloader?

    1.d.  If I want to uninstall Ubuntu later, can I reclaim the partition I used for Ubuntu back to my Windows partition?

Yes, but if you ever want to uninstall, ask here or look for a guide, just to make sure you do it right.

2. Does Ubuntu do a good job of cleaning up after itself when there are updates to it?  I read that Ubuntu updates itself more frequently and I don't want it to consume a lot of space on my hard drive.

Yes, and if you aren't satisfied with it's job, the command below will totally clean any leftover files.

```
sudo apt-get clean
```

3.  Is the Live CD the best way to test hardware compatibility?

Installing is the best, but if it works with the LiveCD it will work with the install.

4.  What is the best way to learn Ubuntu?  I saw a book on Amazon.com that was "The Official Ubuntu Book" for $30-$40.  And on Lulu.com the book by Canonicol was $60, do I have to pay that much to learn Ubuntu?

Google, and these forums. The Ubuntu Wiki is also pretty good.

Ok, that is all I can think of for now.  I have never used any other OS than Windows, so bear with me.  Thanks in advance for any and all help in advance, can't wait only 7 days...

And for all those people telling you that your wireless won't work, it's not true, the new kernel that will be included with Ubuntu 8.10 adds support, so just use Intrepid.

Have fun!

---

### Post by mkvnmtr on 2008-10-23
Dual boot is the best way. You will always have system to use if one has a problem. Don't be afraid of the grub boot loader it has more options than windows boot loader. You will like it. I agree buying a book is not money well spent while Google works. Welcome

---

### Post by Zimmer on 2008-10-23
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)
I used EasyBCD to manipulate the  bootloader.
You need to install GRUB to the partition you install Ubuntu on, NOT to the MBR or Vista partition.
You will need to read up about how best to use Vista's disk management software to make room for an Ubuntu partition. I will try and find the link for you later...
Regards

---

### Post by CoreyB. on 2008-10-23
Wow, thanks for the super fast responses, I love the speed of this forum!  Thanks all of you for your help, all of my answers were answered completely!!  One more question, will I be able to retreive data from within Ubuntu on my Windows partition and vice versa?

---

### Post by OutOfReach on 2008-10-23
You will be able to get files/etc from your Windows partition in Ubuntu. But Windows cannot see any other filesystem other than NTFS and FAT. You will need to install third party tools in Windows to see your Ubuntu files.

---

### Post by Zimmer on 2008-10-23
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)
The link I promised you...

EDIT
Two things that happened for me that you have to do, one is defragment and the other is clear the page file, vista doesnt let you partition if there is a page file or something (you can see that in a little note when using the included partitioner, its even in the picture in the instructions actually)

---

### Post by CoreyB. on 2008-10-23
> **OutOfReach said:**
> You will be able to get files/etc from your Windows partition in Ubuntu. But Windows cannot see any other filesystem other than NTFS and FAT. You will need to install third party tools in Windows to see your Ubuntu files.

What filesystem does Ubuntu use?  Should I let Ubuntu create the partition during installation (if that is possible?) or should I let Vista create the partition.
Any recommendations on program to view the files in Ubuntu?

Thanks for the info Zimmer

---

### Post by anti-node on 2008-10-23
I would say that the Live CD is the way to go about testing Ubuntu, after a while you will probably stop using Vista as the open source alternatives work just as well or better that the microsoft ones

---

### Post by mc4100 on 2008-10-23
> **CoreyB. said:**
> What filesystem does Ubuntu use?  Should I let Ubuntu create the partition during installation (if that is possible?) or should I let Vista create the partition.
Any recommendations on program to view the files in Ubuntu?

Thanks for the info Zimmer
Ubiquity, the Ubuntu installer, will create the partition during installation. By default, Ubuntu uses the [ext3]("http://en.wikipedia.org/wiki/Ext3") file system.

---

### Post by drakeman007 on 2008-10-23
> **CoreyB. said:**
> I've been looking at Ubuntu for a while now and when 8.10 is released I'm going to download it and run the Live CD for a while, make sure everything works fine, then install.

I have a Dell Inspiron 1525 laptop and have many questions:

1. Vista is preinstalled and I need to keep that intact.  I have one hard drive, so I am going to have to repartition it.  How large should I make the partition for Ubuntu, I was thinking 40-50 GB.

    1.a.  I would also like to keep the Windows bootloader, what is the safest/best way to go about this?

    1.b.  Is dual booting safe?  It won't cause a problem when Windows or Ubuntu has to restart to update itself right?

    1.c.  Is there a way to keep Vista as a 'default' OS, so I don't have to choose the OS every time, or is there a timeout in the Windows bootloader?

    1.d.  If I want to uninstall Ubuntu later, can I reclaim the partition I used for Ubuntu back to my Windows partition?

2. Does Ubuntu do a good job of cleaning up after itself when there are updates to it?  I read that Ubuntu updates itself more frequently and I don't want it to consume a lot of space on my hard drive.

3.  Is the Live CD the best way to test hardware compatibility?

4.  What is the best way to learn Ubuntu?  I saw a book on Amazon.com that was "The Official Ubuntu Book" for $30-$40.  And on Lulu.com the book by Canonicol was $60, do I have to pay that much to learn Ubuntu?

Ok, that is all I can think of for now.  I have never used any other OS than Windows, so bear with me.  Thanks in advance for any and all help in advance, can't wait only 7 days...

Hello corey b, you are newbie like me, if you want send me a private message, i can give you some good material to learn ubuntu!!!

---

### Post by d_skillz on 2008-10-23
Good luck on your Ubuntu experience just remember you have the community in case anything doesn't work as you expect and wait the seven days to download intrepid. Remember though your gonna have to read a little more material and troubleshoot with an open mind.

---

### Post by jrecortel on 2008-10-23
just an information.in hardy, i use the vista program to shrink my vista partition.
[http://test.ubuntuforums.org/showthread.php?p=5932429](http://test.ubuntuforums.org/showthread.php?p=5932429)

---

### Post by eternalnewbee on 2008-10-23
You've had a lot of good advice already. I've skimmed through, so I'm not sure whether it is mentioned, but as you are a new user I'd recommend not messing with the Grub. If you have Ubuntu installed and rebooted, you'll have Ubuntu as first boot choice, and if you go down with the down arrow you can boot windoze. As for if you decide to uninstall Ubuntu and you want to reclaim the partition, then you should reformat it again.
Hope this helps.
Good luck.

---

### Post by em4r1z on 2008-10-24
SPACE: A typical Ubuntu installation uses less than 2 GB, thus 5-8 GB for the system should be enough (all my system partitions are 5 Gb in size.)

FILE SYSTEM: I'd use JFS for a laptop for its lower CPU usage. Mount your partitions with the 'noatime' attribute.

REFERENCE: Ubuntu is such an easy-to-use system that you can use it without knowing the basics, but this shouldn't stop you from learning about GNU/Linux. Buy books, read, check essays and researches online, read, visit forums and mailing lists, read.

---

### Post by CoreyB. on 2008-10-24
[QUOTE=eternalnewbee;6022787]As for if you decide to uninstall Ubuntu and you want to reclaim the partition, then you should reformat it again.
QUOTE]

Do you mean I can expand the Windows partition (C:) to the space I had previously dedicated to Ubuntu without losing all of my Windows information and without having to reinstall Windows?

---

### Post by random turnip on 2008-10-24
Yes, use "Gnome Partition Editor".
Search for it on google, it is the easiest and safest way of changing partittion sizes in a graphical manner (i.e. not using terminal code) and it's free to download.

---

