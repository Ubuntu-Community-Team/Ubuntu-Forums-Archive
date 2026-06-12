---
title: "Partition help!"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by John Futter on 2012-01-29
Hello
I am running Ubuntu 11:10 dual booted with Windows 7 on the other partition.  I am, to say the least, a noob at partitioning. I managed to dual boot it with help, but recently occasionally either when the battery runs out on my laptop, or at just (seemingly) random times, it will come up with a black screen saying not enough free swap.

This is what my GParted screen looks like. (attached) 

As you can see I have 1000mb unallocated space, I was hoping I could move that to my swap space? Or is there something else I should do? I would just remove Windows, but I still need it at the moment.

Thanks to anyone who helps!

First thread made on these forums!:D

---

### Post by ajgreeny on 2012-01-29
No, you can't add that space to your current small swap as the two are not side by side and moving partitions of win7 is both extremely dangerous and would also take a very, very long time.  The swap size you currently have is probably causing your problems when the machine tries to suspend on loss of battery power, as it is too small to allow that to happen.

I presume the unallocated 1000MB is a relic of the original setup of Win7 by the OEM, and I would forget about that at the moment.  I can not see what sda3 is doing at the moment either;  there is nothing using space, but it appears to be the win7 OS, unless that is sda1, but I know nothing of win7 so may have that totally wrong.  For safety, I suggest you leave all the ntfs partitions untouched and deal with the ubuntu partitions only.

I suggest you boot to a live CD/USB of ubuntu and run gparted, then right click on the swap partition and choose "swapoff".  Now you can shrink sda6 by 1.5GB and enlarge sda5 to give you 2GB for swap and the remainder for the ubuntu OS.

Backup everything before you do anything to partitions, just in case something goes wrong.

---

### Post by Fernhill Linux Project on 2012-01-29
Assuming the unallocated space is really unallocated space, then you could format that as swap from gparted and your ubuntu install should just pick it up and use it.
I run several distro's from usb devices and they all pick up and use the swap partition on the internal drive without problem or being told to.
Hope that helps.

---

### Post by ajgreeny on 2012-01-29
> **Fernhill Linux Project said:**
> Assuming the unallocated space is really unallocated space, then you could format that as swap from gparted and your ubuntu install should just pick it up and use it.
I run several distro's from usb devices and they all pick up and use the swap partition on the internal drive without problem or being told to.
Hope that helps.
Too many partitions already to do that, unfortunately.

---

### Post by BC59 on 2012-01-29
You can give some space (maybe 1 GB) from Ubuntu sda6 to swap. You don't need all this space for Ubuntu, you can store your data to the ntfs partition sda3 instead.

---

### Post by Fernhill Linux Project on 2012-01-29
> **ajgreeny said:**
> Too many partitions already to do that, unfortunately.

Just looked at the picture again and I agree.
The solution in the first post by ajgreeny would be the best option.

---

### Post by Bartender on 2012-01-29
I've got another suggestion.  I don't know if Acers still do this, but with my 5 year old Acer 5920, I made the recovery discs, then ran them.  That wasn't exactly the original intent, but I screwed things up trying to dual boot.

After reinstalling from the recovery discs, the extra Acer partitions that clog everything up were gone.  There was just one big ntfs partition.  That made installing Linux much easier.

---

### Post by oscarivera9 on 2012-01-30
> **Bartender said:**
> I've got another suggestion.  I don't know if Acers still do this, but with my 5 year old Acer 5920, I made the recovery discs, then ran them.  That wasn't exactly the original intent, but I screwed things up trying to dual boot.

After reinstalling from the recovery discs, the extra Acer partitions that clog everything up were gone.  There was just one big ntfs partition.  That made installing Linux much easier.

If your Acer is still under warranty and you would like to keep your warranty intact, I suggest you DO NOT do what is suggested above.  It will void your warranty.

However, if your Acer is no longer covered by the warranty (if you bought it over a year ago, for example), then the above is actually not a bad idea.

Better yet, try this:
Shutdown Ubuntu and boot into Windows 7.  Then Shutdown Windows 7 and boot into Ubuntu.  The reason for this is that you might have been on Hibernate or Sleep in Windows when you took the screenshot you attached, which would explain the red exclamation sign at the sda3 NTFS partition which is most definitely your Windows 7 partition.  Leave all partitions alone and then post another screenshot like you did the first time; hopefully the red exclamation will be gone.  Depending on how much free space you have in that NTFS partition, you might be able to shrink that partition and then re-size the extended partition sda4 to enlarge the Swap Logical Partition(sda5).  Otherwise, you can just go ahead and do what was suggested earlier about making the Ubuntu partition(sda6) a little smaller to make room for the bigger Swap area.   
Whichever way you look at it, your  problem is definitely being caused by the Swap not being big enough.

---

