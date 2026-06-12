---
title: "Unable to Install linux"
date: 2011-10-02
forum: New to Ubuntu
---

### Post by Kushagra.19 on 2011-10-02
I have tried many times to install linux but all the time i ge disappointed ..

Plese help me out

i m running windows 7 and i have created a partition of 17 gb
but when i boot with the linux cd and at the last step when i choose that 17 gb partition it says "Insufficient memory to install" .

It is showing the same message when i created the 50 gb partition ..

Please help me out ..

---

### Post by chong601 on 2011-10-02
What is the size of the RAM?

---

### Post by fantab on 2011-10-02
I am afraid that you may have NOT created a Linux SWAP Partition. Have you? If possible please post some details about your system configuration and Partition scheme.

---

### Post by Kushagra.19 on 2011-10-02
4 gb of RAM

---

### Post by Kushagra.19 on 2011-10-02
> **fantab said:**
> I am afraid that you may have NOT created a Linux SWAP Partition. Have you? If possible please post some details about your system configuration and Partition scheme.

when i m installing it didn't ask me whwther you want to ctreate swap or not .. 

i m enclosing my drive partitions in a picture

---

### Post by fantab on 2011-10-02
I am assuming that you are installing Ubuntu Linux. 

Yes, you will have to create a Linux SWAP partition and it should be at least twice the size of your RAM, in your case it should be **8GB**.

**Create it and Format it as SWAP. **

My advice to you is please read some Installation documentation, which is freely available if you care to search... to get you started try this [LINK]("http://neosmart.net/wiki/display/EBCD/Ubuntu") and [LINK2]("http://members.iinet.net.au/%7Eherman546/p23.html")

Have fun with Linux.

---

### Post by westie457 on 2011-10-02
Looking at the picture your hard drive has been converted to dynamic. This is something that is not easy to sort. Go to here for advice on what to do. [http://ubuntuforums.org/showthread.php?t=1853007](http://ubuntuforums.org/showthread.php?t=1853007)

---

### Post by fantab on 2011-10-02
> **westie457 said:**
> Looking at the picture your hard drive has been converted to dynamic. This is something that is not easy to sort. Go to here for advice on what to do. [http://ubuntuforums.org/showthread.php?t=1853007](http://ubuntuforums.org/showthread.php?t=1853007)

westie457 is right... 

if its a HP Laptop or a branded HP Desktop call help. If not back up your all your important data and start fresh with [GParted]("http://gparted.sourceforge.net/livecd.php")

---

### Post by sanderj on 2011-10-02
> **westie457 said:**
> Looking at the picture your hard drive has been converted to dynamic. This is something that is not easy to sort. Go to here for advice on what to do. [http://ubuntuforums.org/showthread.php?t=1853007](http://ubuntuforums.org/showthread.php?t=1853007)

@westie457,

So Ubuntu can't create a partition on such a dynamic disk and that's the reason of the OP's ""Insufficient memory to install""? 
If so, wouldn't it be clearer if the Ubuntu install would say "sorry, I couldn't create a partition (because you have a dynamic disk)"?

---

### Post by ajgreeny on 2011-10-02
> **fantab said:**
> I am assuming that you are installing Ubuntu Linux. 

Yes, you will have to create a Linux SWAP partition and it should be at least twice the size of your RAM, in your case it should be **8GB**.

**Create it and Format it as SWAP. **

My advice to you is please read some Installation documentation, which is freely available if you care to search... to get you started try this [LINK]("http://neosmart.net/wiki/display/EBCD/Ubuntu") and [LINK2]("http://members.iinet.net.au/%7Eherman546/p23.html")

Have fun with Linux.
This is old advice, and no longer holds true.

You can install with no swap if you have 4GB ram, but I would not advise that you do so.

However, there is no point in having 2X ram size for swap these days if you have a newish machine with plenty of ram, and with your 4GB ram I suggest a max of 2GB swap, and I doubt that will ever be used in normal system use or running.

---

### Post by Kushagra.19 on 2011-10-02
> **westie457 said:**
> Looking at the picture your hard drive has been converted to dynamic. This is something that is not easy to sort. Go to here for advice on what to do. [http://ubuntuforums.org/showthread.php?t=1853007](http://ubuntuforums.org/showthread.php?t=1853007)

Actually for the first time when i created the partition mu disk was 'primary' but now, as u can show in the picture it has converted into 'basic volume'..
During that time (when i created the partition for the first time)
windows 7 shows me a message something like "u won;t be able to install operating system in the future". But then in a hurry i created it ..

So please give me suggestions ...

Will the re installing windows sort out the problem ??

---

### Post by d4m1r on 2011-10-02
What exactly does SWAP do? I assumed it was like the windows paging file (using HDD for ram) so I disabled it and a warning appearing during install but I ignored it...I have 8GB of ram so don't want to use my slow HDD for that if that is what it is..

---

### Post by Kushagra.19 on 2011-10-03
> **sanderj said:**
> @westie457,

So Ubuntu can't create a partition on such a dynamic disk and that's the reason of the OP's ""Insufficient memory to install""? 
If so, wouldn't it be clearer if the Ubuntu install would say "sorry, I couldn't create a partition (because you have a dynamic disk)"?

But my drive shows that it is basic volume only ....

---

### Post by sanderj on 2011-10-03
> **Kushagra.19 said:**
> But my drive shows that it is basic volume only ....

Basic? Can you then post a new screenshot?

---

### Post by Redblade20XX on 2011-10-03
> **d4m1r said:**
> What exactly does SWAP do? I assumed it was like the windows paging file (using HDD for ram) so I disabled it and a warning appearing during install but I ignored it...I have 8GB of ram so don't want to use my slow HDD for that if that is what it is..

Swap is used in case you run out of memory space during an event(s) and the cpu needs more storage to perform the operation(s), It uses your hdd space as the alternative in case that happens. So unless your compiling something heavy as a kernel or using several heavy programs at once, you should be alright.

---

### Post by mastablasta on 2011-10-03
> **Kushagra.19 said:**
> But my drive shows that it is basic volume only ....
 
 
Basic is a bit vague. Need more info on that. The issue here is that  you can't install any OS on dynamic partition. you need primary or extended to do so. primary are limited i think to max 4.
 
often the preformated and partitioned disks will have them all occupied already (i am not sure why they od this. i think it's very rude). hence the advice to back up data on one of those partition, remove it and create empty disk space on that area. use windows disk manager to do this.
 
> **d4m1r said:**
> What exactly does SWAP do? I assumed it was like the windows paging file (using HDD for ram) so I disabled it and a warning appearing during install but I ignored it...I have 8GB of ram so don't want to use my slow HDD for that if that is what it is..
 
Swap also stores system data when computer goes into hibernation. i guess oyu canget away with turning it off.
 
now to end all this swap talk --- > the installer creates swap partition automaticly unless you choose the advanced manual parititoning in which case you need to tell him to do it. So clearly swap doesn't have anything with OP problem and it would be best to leave it alone for now.

---

### Post by Kushagra.19 on 2011-10-03
> **westie457 said:**
> Looking at the picture your hard drive has been converted to dynamic. This is something that is not easy to sort. Go to here for advice on what to do. [http://ubuntuforums.org/showthread.php?t=1853007](http://ubuntuforums.org/showthread.php?t=1853007)

Now i m enclosing a second image of my disk drive ..
it is the basic volume only , not the dynamic on as you have said ..

---

### Post by westie457 on 2011-10-03
Sorry to say this. It is still dynamic as the attached picture shows. Go to the thread I linked to earlier and refer to the post by 'oldfred' for guidance on how to convert the drive back to basic.

Back up everything you want to keep just in case it does not work properly.

Until the hard drive is converted back to 'Basic' Ubuntu will not install properly or not at all.

@ sanderj  Why the out of memory error message was thrown up instead of the one you suggested I have no idea. However I am not a code writer.

---

### Post by fantab on 2011-10-03
> **Kushagra.19 said:**
> So please give me suggestions ...

Will the re installing windows sort out the problem ??

Yes it will, but first:


[LIST=1]
[*]Back up all your important Data.
[*]Download and burn[COLOR=Blue] [COLOR=Red]**[GPARTED [link]]("http://gparted.sourceforge.net/livecd.php")**[/COLOR][/COLOR] to a CD and boot.
[*]Delete all the partitions and **change the Partition Table to DOS**.
[*]CREATE PARTITIONS
[*]Format Windows Specific Partitions with NTFS file system and for LINUX use EXT4 file system, also don't forget to create a SWAP partition of 4GB (you have a 500GB HDD so keep it 4 to 8 GB).
[*]Then go ahead and reinstall Windows and then Linux. For more info use the links I have provided in my previous posts here.
[/LIST]

Keep it simple.
Good Luck.

---

### Post by philinux on 2011-10-03
Please see this regarding swap.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by xaris on 2011-10-03
If you are new to linux maybe it would be better to use wubi for installing Ubuntu through 
Windows7. With this way you will be sure that nothing wrong is going to happen while trying to learn using gparted. 
For a start try reinstalling windows7 and from disk management delete and reformat the unused partition. I think that windows7 disk management gives you the same functionality as gparted. Afterwards just let wubi do the rest
[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer).

---

### Post by Kushagra.19 on 2011-10-05
@ westie457 and @ fantab
 with all the pain i have formatted my laptop(after creating backup) and the biggest thing is that linux (fedora 14) is now installed .
but now i m facing the problems regarding the connectivity.
linux is not recognizing my wireless networks but amazingly bluetooth is working..
what can i do now ???
 
> **westie457 said:**
> Sorry to say this. It is still dynamic as the attached picture shows. Go to the thread I linked to earlier and refer to the post by 'oldfred' for guidance on how to convert the drive back to basic.

Back up everything you want to keep just in case it does not work properly.

Until the hard drive is converted back to 'Basic' Ubuntu will not install properly or not at all.

@ sanderj  Why the out of memory error message was thrown up instead of the one you suggested I have no idea. However I am not a code writer.

> **fantab said:**
> Yes it will, but first:


[LIST=1]
[*]Back up all your important Data.
[*]Download and burn[COLOR=Blue] [COLOR=Red]**[GPARTED [link]]("http://gparted.sourceforge.net/livecd.php")**[/COLOR][/COLOR] to a CD and boot.
[*]Delete all the partitions and **change the Partition Table to DOS**.
[*]CREATE PARTITIONS
[*]Format Windows Specific Partitions with NTFS file system and for LINUX use EXT4 file system, also don't forget to create a SWAP partition of 4GB (you have a 500GB HDD so keep it 4 to 8 GB).
[*]Then go ahead and reinstall Windows and then Linux. For more info use the links I have provided in my previous posts here.
[/LIST]

Keep it simple.
Good Luck.

---

### Post by d4m1r on 2011-10-05
> **philinux said:**
> Please see this regarding swap.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)


Thanks....Seems like Swap is like the Windows paging file, but with 8GB of ram I'd much rather use physical ram that my 7200PM SATA II harddrive. I did manually install this partition and it did prompt a message about Swap, but I ignored it and have no space for it configured so I guess I can't use sleep mode but I never do anyway :D

---

### Post by fantab on 2011-10-06
> **Kushagra.19 said:**
> @ westie457 and @ fantab
 with all the pain i have formatted my laptop(after creating backup) and the biggest thing is that linux (fedora 14) is now installed .
but [B]now i m facing the problems regarding the connectivity.
linux is not recognizing my wireless networks[/B] but amazingly bluetooth is working..
what can i do now ???

First of all, why did you not install Fedora 15, which is their latest release? For me, on Fedora 15 my wireless broadband modem connects out of the box, all I had to do was configure the connection.

In your case too I think its the configuration, try disabling CHAP, MSCHAP & MSCHAPv2 in ppp configuration settings and try....

If it is not solved Post this issue in [**Fedora Forums**]("http://forums.fedoraforum.org/index.php")

---

