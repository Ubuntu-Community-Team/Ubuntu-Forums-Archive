---
title: "Dual Boot XP/Ubuntu--Loading Grub, Error 5"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by enon8727 on 2008-09-30
Hello, I'm pretty noobish so I wanted to dual boot XP with Hardy Heron and I already had XP on my PC so I set up the partitioning and dual boot properties in the install of Ubuntu and everything worked awesome for a couple weeks, then all of a sudden, on boot up before it would show the OS's to choose from, it said something like, "Loading Grub 1.5...Error 5".

So I read that's got something to do with a bad partition table and that all my info and stuff should be fine, I just need to fix the table.  So I've tried a few things to no avail.  It seems the biggest issue is that I can't even mount my HD to do some fixing with the live CD :(

For instance I tried this
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
and after "find /boot/grub/stage1" I got something basically saying it couldn't find that.  So I went down the page a bit to try mounting my drive and it said "special device /dev/sda6 does not exist"

I don't know what to do next...Please help!

Thanks,
Ian

---

### Post by caljohnsmith on 2008-09-30
How about first posting:
```
sudo fdisk -lu
```
If that shows your linux partition (should be type "linux" under "system"), then run an fsck on it:
```
sudo fsck -y /dev/sdaX
```
Where sdaX is the linux partition. Let me know what the output of that command is, and we can work from there.

---

### Post by enon8727 on 2008-09-30
When I run sudo fdisk -lu nothing happens.  It just goes straight back to the prompt, "ubuntu@ubuntu:~$"

---

### Post by prshah on 2008-09-30
> **caljohnsmith said:**
> How about first posting:
```
sudo fdisk -lu
```
If that shows your linux partition (should be type "linux" under "system"), then run an fsck on it:
```
sudo fsck -y /dev/sdaX
```
Where sdaX is the linux partition. Let me know what the output of that command is, and we can work from there.

You should do this from the live CD, since you can't boot into Ubuntu.

---

### Post by enon8727 on 2008-09-30
Yea, I'm in the live CD...

---

### Post by caljohnsmith on 2008-10-01
If "sudo fdisk -lu" doesn't even see your HDD, that's not a good sign. When you try and boot from it on start up, are you still getting a Grub error, or does BIOS complain there is not bootable device present? 

How old is your HDD? Can you check the cables/connections to make sure the HDD is connected OK? Do you have any HDD diagnostic software that came with your HDD, like on a CD? If so, I would suggest running that and seeing what it reports. But if fdisk doesn't even see that HDD, I'm doubtful that any HDD diagnostic software would see your drive either.

---

### Post by enon8727 on 2008-10-08
Yea, I thought that might be the case.  I did some HD diagnostics and one reported an error once, but I did about four others that said it was fine.  

After the tests it booted up perfectly normal somehow too!  So I went into XP since I was doing a few things in there before hand, but now I'm back to square one.  Sometimes I get "GRUB loading, please wait... Error 5" and sometimes I get the same thing only Error 18.  I'm guessing because of the sparatic-ness of the errors and the inconsistency that I have a bad drive :(

What do you guys think?  Any hope?

---

### Post by bumanie on 2008-10-08
Grub error 5 is an indication of a corrupted partition table. You can recover and re-write the partition table with testdisk.>  sudo apt-get install testdisk To run > sudo testdisk You can also get a stand-alone live cd .iso from [here]("http://www.cgsecurity.org/wiki/TestDisk"). Also, read the tutorial on that site and also look [here]("http://www.users.bigpond.net.au/hermanzone/p21.html")

---

### Post by crispy_420 on 2008-10-09
[http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html)

---

