---
title: "trying to save info on hard drive using live cd"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by gregorio on 2008-10-06
Hello,

I think I have a dying windows hard drive.  It just keeps rebooting.  There is some files on it that I need to get.  Can I use an Ubuntu live cd to not only access the files on the drive, but also burn them to a cd-r?  How would one do that?

Thanks

---

### Post by philinux on 2008-10-06
Easiest way would be to use the livecd to copy the files to a usb stick.

---

### Post by gregorio on 2008-10-06
unfortunately, my usb drive is full, and only 1gb.  I know I can do a shuffle of copy on it, boot to Ubuntu, copy there and so on.  I was hoping to burn to cd.

---

### Post by bwang on 2008-10-06
If you have two CD drives, you can. Otherwise, the Ubuntu LiveCD will use your CD drive, preventing you from burning anything. However, if you have enough RAM, you can use Knoppix with the toram option.

Get Knoppix at: [http://www.knoppix.net/](http://www.knoppix.net/)

Read about the toram "cheat code" here: [http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)

---

### Post by egalvan on 2008-10-06
Patrted Magic LiveCD is also very useful, it will automatically load into RAM and eject the LiveCD, if you have enough RAM.

I find it easier to use than either Knoppix or Ubuntu as a LiveCD.
It's much smaller, yet still has a large number of packages, including CD and ISO burning tools.

Personally, I like it and use it, so I donated to the authors.


homepage:
[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

list of programs:
[http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Programs](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Programs)

---

### Post by anewguy on 2008-10-06
I'm not saying it's not your disk drive, but does it do anything besides just reboot?  Ever get to any operating system?  I ask this because this could also be related to other problems - heat, power supply problems, motherboard problems, memory problems, etc..

If you can boot from CD all the way to Linux, then I would suspect you are correct.

Dave :)

---

### Post by gregorio on 2008-10-06
I dual boot from another hard drive to Ubuntu.  It runs fine.  It could be the hard drive.  It could be software, who knows with windows!

---

### Post by philinux on 2008-10-06
In that case use your ubuntu OS to copy the windows files to a cdr. No need for livecd at all.

---

### Post by gregorio on 2008-10-07
Well, I wish it was that easy.  I would need to tear into the computer to do so, and I guess it wouldn't be that big of deal to do.  I have my hard drives on a dpdt switch connected to the jumpers on the drives.  By flipping that switch before powering up the computer, I select which drive to boot from.  I can "see" the windows drive, but cannot access it.  What I think I would need to do is to go in and make the windows drive a slave and hopefully not have any boot issues then.  I'm really not sure.

thanks

---

### Post by philinux on 2008-10-07
When you say you can "see" the windows drive do you mean in nautilus/places. If so it can be made accessible.

---

### Post by gregorio on 2008-10-07
I'm going off of memory right now, for my computer is at home.  But when I try to access the windows drive, I can see folders and files, but to try to copy them it tells me something to the effect of having no permission (I think, wish I was in front of it right now, perhaps I should wait till I get home).

---

### Post by philinux on 2008-10-07
ntfs-3g comes preinstalled in Hardy. All you need to do is use the configure app and you're good to go.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by gregorio on 2008-10-25
ok, so now I finally have time to tear into my system.  I made my windows drive a slave and now I see it listed on the left side of the file browser.  I have NTFS3G installed and configured it.  However, when I try to mount the windows drive, it says:

Cannot mount volume.
You are not privileged to mount this volume.

Any ideas?

thanks

---

### Post by gregorio on 2008-10-26
well, I did a bunch of reading and found a way to force mount the drive, so now I do have access to it.  So, I guess I will continue with my problems with that drive (in other words probably more threads or research)

---

