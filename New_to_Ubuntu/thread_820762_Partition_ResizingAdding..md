---
title: "Partition: Resizing/Adding."
date: 2008-06-06
forum: New to Ubuntu
---

### Post by Freyja on 2008-06-06
Hi there.

Well I got a few doubts about my partition(s) and thought about changing it.
Telling about the search results this is a common question at the first look, I apologise for this.

Here are the primary guides I read:```

http://ubuntuforums.org/showthread.php?t=282018
http://linuxplanet.com/linuxplanet/tutorials/3174/1/
http://www.overclock.net/linux-unix/11208-linux-partitioning-guide.html
http://gparted.sourceforge.net/larry/resize/resizing.htm
```

Current partition (fdisk -l):```

Device Boot      Start         End      Blocks   Id  System
[color=red]/dev/sda1[/color]   *           1       60044   482303398+  83  Linux [color=green]Primary partition?[/color]
[color=red]/dev/sda2[/color]           60045       60801     6080602+   5  Extended [color=green]Primary partition?[/color]
[color=red]/dev/sda5[/color]           60045       60801     6080571   82  Linux swap / Solaris [color=green]Logical partition?[/color]
```

So looks fine but I would like to add those '/home', '/www' partitions and one with ww.
This is where my questions start actually:```

[color=red]sda1[/color] *Root partition: Was told to be 5GB at least but I thought about 50GB.
[color=blue]sda3[/color] *WW system partition: 50GB for the system.
[color=red]sda2[/color] Extended partition: Guess this is the primary for the swap 300GB.
[color=red]sda5[/color] Swap partition: Read that 2GB would be alright for this.
[color=blue]sda6[/color] /Home partition: 100GB, should store the home/ files **(does this auto copy the current ones?)**
[color=blue]sda7[/color] /www partition: 100GB, should store the www/ files **(is that possible?)**
[color=blue]sda8[/color] WW file partition: 80GB for the files.
```
[FONT="Monospace 10"]```

--------------------------------------------------------------------------
¦########¦########¦###################################¦##################¦
¦#  WW  #¦# Ubun #¦################ Extended #########¦##################¦
¦########¦########¦------------------------------------#####  Free  #####¦
¦#System#¦# Root #¦# Ubun #¦# Ubun #¦# Ubun #¦#  WW  #¦##################¦
¦########¦########¦# Swap #¦# Home #¦# www  #¦# File #¦###### 100 #######¦
¦## 50 ##¦## 50 ##¦#  20  #¦# 100  #¦# 100  #¦#  80  #¦##################¦
-------------------------------------------------------------------------¦

```[/font]
[color=red]Problems:[/color]```

 - I installed Ubuntu already on the whole diskspace.
 - Is that even possible that way without deleting the data?
 - GParted live CD crashes after botting, can I do this with the Ubuntu install CD without reinstalling?.
```

Thank you for your help and time.

---

### Post by Duck2006 on 2008-06-06
You can use parted magic or gparted to resize your drive.

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

The have good guides on there sites.

---

### Post by Inxsible on 2008-06-06
I am not sure what www or WW is, unless you have just named them to explain your issue. but you can create partitions and resize them using Gparted on the Live CD. Its under System>>Administration>>GParted. It could also be named Partition Editor under the same menu. I forget if they changed it in Ubuntu as well.

and no you don't need a 50 GB root. I have a 9 GB root and I still havent filled half of it. I keep the rest of the space for my personal files like music movies etc. And if you are going to have a separate partition for such files, you probably don't even need a very huge /home drive. I have 20GB of home drive and I have ended up using about 300 MB of it since I have a different partition for my files.

And I think anything above 1GB for swap is a waste of space.

---

### Post by Hospadar on 2008-06-06
You can use gparted off the ubuntu livecd just fine.  I think that's the best way to handle partitions and formatting in linux.  I've always had good results
After formatting those drives, you'll want to copy the contents from your main partition to the new partition, (i.e. "sudo cp -rf /home/* /media/<wherever your new partition got mounted to by default>) then edit your /etc/fstab to correct the mountpoints. just look for the /media/<wherever your new partition got mounted to by default> and change it to the location you want (following our examples it would change to /home

And yeah, as inxsible says, you don't need a big root partition.  I have a 5GB partition for root on my lappy that I will probably never fill even with all the crap I install in it.  If you play a ton of linux video games, that might not be the case though, but you can always resize it later if you find you really need it.  I think you would be totally fine with something between 5-10Gb even for games and whatnot.

---

### Post by Freyja on 2008-06-06
Yay, thank you guys so far.

GParted:
 - Well yeah I know/read about this but just wanted to ask about the partition table schema first, so I do not have to change that twice.

Schema:
 - So I will cut the /root to 20GB instead of 50GB (or currently 482GB), if the /www partition works.
 - I will leave the Swap since 1GB does not bother me and I have to change less.
 - /www, I meant like the /home direcoty, where webpages are stored in an own partition (could not find out if this is possible).
 - WW is an old windows version (Windows for Workgroups 3.11).

---

### Post by Inxsible on 2008-06-06
You might find this guide helpful to change your home drive.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Freyja on 2008-06-06
Alright, thank you for this guide (or better the whole linked site).

I decided to do the changes one by one so I will not get lost too easily.
Guess I will add the windows partitions tomorrow.

Here is my current status:```

/dev/sda1   *           1        2611    20972826   83  Linux
/dev/sda2           46991       60801   110936857+   5  Extended
/dev/sda5           60045       60801     6080571   82  Linux swap / Solaris
/dev/sda6           46991       53517    52428064+  83  Linux
```

 - How can I check that the /home really is in the new partition, except relying on the mount entry?
 -> Guess it worked since my Postfix testmails are gone.

[size=1]**A total different question (do not want to open a new thread for it, just curious):**
 - I had to restore my password three times now after setting it to (i.e. 'x.%%%%5mypassword6&&&&&.y.???????-a'.
 - When I reboot in the terminal I can not login with this everytime. What am I doing wrong?[/size]

---

### Post by Duck2006 on 2008-06-06
> Guess I will add the windows partitions tomorrow.

If your going to make one a win partition, it has to be a primary partition.

---

### Post by Freyja on 2008-06-07
[size=1]@Duck2006: I will keep that in mind, thanks.[/size]

Well nothing works anymore, what a shock:(

Tried to login as normal user today and got such line after 'startx'.
 - xauth: timeout in locking authority file in home/.../'a filename I could not write down'
 -> I read this is because I copied the /home folders as root, is that right?

After nothing worked, it hang up so I rebooted and tried to login as root:
 - .... login: root
 - Password: ****************************
 - mail: /tmp/mail.RsXXXXhubKhN: Read-only file system.
 -> And it logs me out right away.
 -> Now I got this message on each user.
 ->> Did not find any information about this.

[color=red]//Edit
Just for your information:
 - I solved this part and my users can login now again. (Phew)
 - I will post later about the other partitions if it worked (or not).
[/color]

---

### Post by Freyja on 2008-06-08
Oh my...
Made a new partition for the future windows and now all my partitions are gone (can not even boot anymore): (

---

