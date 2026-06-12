---
title: "Dual_boot with a fat32 partition"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by hellarough on 2008-05-29
Okay so i have just installed ubuntu on my dell laptop and I created this partition when I installed it...

80g HDD

50gb ntfs primary (windows)
5gb fat32 primary 
22 ext3 primary (linux)
2gb swap primary (linux)

the dual boot works great and linux even recognizes the other partitions that I have access to (after typing my admin password). My problem is that I would like to be able to access the fat32 partition in windows (which i can't right now) so that I can transfer files between linux and windows easily.

I did some research and found that other dual boot guides instruct users to make the fat32 and swap partitions logical instead of primary. if this is the case will i encounter problems if i use gparted to just edit the existing partitions?

also i think there is an issue with my network adapter (its a dell laptop with a broadcom adapter: dell inspiron e1505). any suggestions with that so i can access the internet through linux would help a lot...

---

### Post by forestpixie on 2008-05-29
The reason behind the logical and primary partitions is that you can only have 4 primary partitions, means you can't add any later.

You need to add the drives which you can't access to the fstab file - this is a good tutorial
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Can't help with the broadcom I'm afraid - it might be better to start a new thread for that, check on the forum first as there will be plenty of previous threads, instead of using the forum search try these

[http://www.googlubuntu.com/](http://www.googlubuntu.com/)
[http://www.uboontu.com/](http://www.uboontu.com/)

---

### Post by live2learn on 2008-05-29
thats weird, it should work straight away.if its version 8.04
I recommend you fix the fat32 partition.
put your fat32 partition to a logical instead.
You don't even have to use fat32, it works with
ntfs now. I believe its windows that did not reconize 
your fat32 partition because its primary and in linux 
it should work.

---

### Post by hellarough on 2008-05-30
problem solved....I totally f**ked up the xp partition (i guess it was installed to two partitions and absolutely needed both of them) so now I am just using linux. I guess there is nothing like diving right in, right? So I have a wired internet connection but I just have to figure out a way to get this broad com working...wish me luck!

---

### Post by forestpixie on 2008-05-30
Good luck :D

As I said there are is a lot here about broadcom - I've seen them, just neverread any of them.

---

### Post by forestpixie on 2008-05-30
This might help you - but I don't know which wireless adapter you have -

[Dell Inspiron E1505 Wireless (Broadcom 1390 WLAN)]("http://ubuntuforums.org/showthread.php?t=297092")

Also have a look through the network forum - [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

Finally of course you search for your adapter - these 2 search the forums, easier than the forum search.

[http://www.uboontu.com/](http://www.uboontu.com/)
[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

If you do need help it will be better to start a new thread

---

### Post by doctored on 2008-05-30
This thread
[http://ubuntuforums.org/showthread.php?t=769990]("http://ubuntuforums.org/showthread.php?t=769990")
got me going with my Broadcom wireless network. And I really have no idea what I'm doing most of the time.

---

