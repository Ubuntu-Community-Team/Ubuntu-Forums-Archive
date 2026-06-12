---
title: "wanting to expand 12.04 partition"
date: 2014-05-07
forum: New to Ubuntu
---

### Post by bstanfordb on 2014-05-07
Hi... I created a dual boot with Umbuntu 12.04 and Windows 7 and now I would like to allocate more space to Umbuntu

I used Gparted and cut off an addition 10 GB that is adjacent to my Linux partition

I followed the instructions about how to make a bootable USB out of a .iso but when I tried to boot it said something about an unkown character or word or something and didn't boot.

Does anybody know the best Iso to use?  I may have used the wrong one since I have 12.4 and the iso was for 12.4.4


Or even better, is there a way to allocate the 10Gb in limbo to Umbuntu through Windows7?



Havin a heck of a time over here, would really appreciate any input.  Thanks

---

### Post by deadflowr on 2014-05-07
Two things:

Firstly, If you're trying to move some space from the Windows partition, then it is HIGHLY recommended to use Windows disk management tool.
Gparted is good, but it can still wreck the windows side, where as the windows utility won't (or at least shouldn't).

Secondly, 12.04.4 is 12.04, so don't worry.
The .4 is it's point release.
It's kind of like a service pack.

Aside from that, the iso on usb problem is hard for me to understand, without more to go on.
Like, what it actually stated during the boot failure.

---

### Post by Dreamer Fithp Apprentice on 2014-05-07
> **bstanfordb said:**
> Hi... I created a dual boot with Umbuntu 12.04 and Windows 7 and now I would like to allocate more space to Umbuntu

I used Gparted and cut off an addition 10 GB that is adjacent to my Linux partition

I followed the instructions about how to make a bootable USB out of a .iso but when I tried to boot it said something about an unkown character or word or something and didn't boot.

Does anybody know the best Iso to use?  I may have used the wrong one since I have 12.4 and the iso was for 12.4.4


Or even better, is there a way to allocate the 10Gb in limbo to Umbuntu through Windows7?



Havin a heck of a time over here, would really appreciate any input.  ThanksIt took me a while to figure this out and I wrote a whole page before I realised I'd mistaken your meaning. So, if I got this right, you successfully created a dual-boot Windows/Ubuntu system and then, using gparted you shrunk the Windows partition by 10 giB and now you want to grow the Ubuntu partition into that space. And you tried to make a bootable USB stick to boot from and use gparted to do the growing. If that's right:

Yes to the last question, you can do it from Windows. I haven't used partitioning software from Windows in a long time but it exists, it works fine and you shouldn't have to buy anything. I'm pretty sure it used to ship with Windows but if not I'm sure you can find some shareware or downright freeware Windows partitioning programs. Just use a search engine. I'd try searching "windows partitioning shareware" at startpage.com ('cause Google is evil, lol) for starters. And yes that would be the easiest way to do it.

If you want to do the other way with live media, whatever you installed the Ubuntu with should work fine. Version wouldn't really matter unless it is REALLY old. Speaking of which, you didn't just install 12.04 did you? You know that's 2 years old? You may have good reasons to not upgrade, I don't know. But, although I'm not a fan of the way the standard Ubuntu DE has evolved since 10.04, I do think the underlying stuff in 14.04 seems pretty good and has given me less problems that any version since 10.04. Part of that may be that I've explored more alternative desktops and finally gotten things tweaked the way I like them, but partly I think it HAS gotten better. Your call though.
==============
Added by edit:
I see Deadflower answered while I was typing slowly. Such is the price of prolixity. Anyway since my answer appears after his I was concerned it might  seem like I was dissing his answer about the greater safety of the Windows partitioner by saying either way is fine. Actually he is probably right. Using the Windows partitioning software probably is at least a wee bit safer in addition to being substantially easier since you'll be working from a hard drive partition that you already have installed. At least I've seen the claim fairly often. And if nothing else, it does preclude the most obvious possible mistake of getting confused about which partition is which. In practice I'm pretty sure I've used gparted to manipulate Windows 2000 partitions, and I think Windows 7 partitions, in the past with no problem. But I had legitimate installation disks and clonezilla backups so I wasn't being quite as paranoid-careful as I might have been in other circumstances.

---

### Post by squakie on 2014-05-07
Shrinking a Windows partition is always best done with the Windows tools.  There is actually a little more to it than just shrinking the partition, though:

- defrag the disk in Windows - twice doesn't hurt.  This is important to avoid potential data loss.
- shrink the partition using the Windows tools (like disk management)
- reboot Windows and let it get everything straightened out from the partition shrinkage.  Sometimes Windows needs to boot a couple of times to "adjust" itself (non-technical expanation), as it may give you errors about the file system having changed the first time.  You always want to be sure Windows will boot cleanly and operate cleanly prior to starting the install of Linux/Ubuntu.

Prior to attempting to install a newer release from 12.xx, you may want to check the minimum hardware specs and also your video support.  Backups are always a prerequisite prior to any changing being done on your PC.

Since you have already created the space, I wrote the above for others who may read this post looking for advice.  For you, the best bet (to me anyway) is to indeed boot from a live media - be it a USB flash or a live DVD.  When you boot the live media and use the "Try Ubuntu" option, you will probably need to install gparted first - as I remember I don't think it was included in the 12.xx "Try Ubuntu" option.  Simply open a terminal and do:  sudo apt-get install gparted   .  When that completes you should be able to run gparted and expand your partition into the free space.

---

### Post by bstanfordb on 2014-05-07
Thank you for the responses.  

The message I'm seeing when it tries to boot from USB is:  

Unknown keyworkd in configuration file

Boot:

and then it's unresponsive to any button press, but after a few it will make the loudest beep sound I've heard from this machine.




I'll look into upgrading from 12.04, this was just what was available to me at the time where I looked I guess.

---

### Post by squakie on 2014-05-07
That is, well, odd!  I'll see if I can find anything on that and I'm sure others with more knowledge will be helping here as well - perhaps one of them has the answer. 

How did you create the USB flash?  I would recommend unetbootin to do so.  It runs in Linux and Windows both.  You may want to retry creating the flash with that.  If you have a network connection while doing so, you can select the version you want.

---

### Post by bstanfordb on 2014-05-07
I used Startup Disk Creator to make the bootable USB

---

### Post by squakie on 2014-05-07
Try unetbootin and see if you have better luck.

---

### Post by squakie on 2014-05-09
While it's old, perhaps this will help:  [http://askubuntu.com/questions/141311/unknown-keyword-in-configuration-file-boot-error-when-booting-off-a-live-usb](http://askubuntu.com/questions/141311/unknown-keyword-in-configuration-file-boot-error-when-booting-off-a-live-usb)

---

