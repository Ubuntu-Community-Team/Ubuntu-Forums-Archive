---
title: "Mount Point On Newly Installed Internal HD"
date: 2013-10-08
forum: New to Ubuntu
---

### Post by Steve_Campisano on 2013-10-08
Sorry for being so long winded here .....

I'm new to Linux / Ubuntu but have been coding for over 37 years so I'm not a complete moron (I think)

&#8230;.. so please cut this old timer someslack.

Anyway, my Windows 7 HD crashed and I tried cloning it to another HD but there was an issue with the bad HD so I couldn't complete the clone successfully.

So I thought this was the perfect time for me to get a new internal HD and try out Ubuntu.

I installed the new HD, cut an Ubuntu ISO disk and ran the install flawlessly.

Ubuntu is a sweet OS for sure.

So I bought another secondary internal HD, installed it, created a couple of partitions using GParted to hold my database and my images.  Piece of cake &#8230;.. so far.  

The next step, &#8220;Create A Mount Point&#8221; in the instructions I am using [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)  state, &#8220;you need to choose a mount point" ,,,, blah, blah, blah &#8221; and this is where I get lost.

I have a terminal session open and I executed the SUDO MKDIR command to create the mount point as indicated.

The new directory however is being created on /dev/sda1 (my boot drive).

I think about it and this does make sense. I mean in my terminal session I'm not positioned at my/dev/sdb1 or /dev/sdb2 drive.

So the questions I have are &#8230;..

First, are these instruction incorrect? I mean, are they missing a step that states I should issue a command to move to the the either of the new drives? In Windows I would enter the drive letter like &#8220;d:&#8221; and press enter to move to the new drive and then issue my command on that drive. Or did I miss some part of these instructions?

How do I change from my /dev/sda1 driveto another drive?  Or should I be doing this?

Currently I can see the two new drives represented on the launch bar. And I can mount and unmount them.  The names for the both of them show up as &#8220;1.0 TB Volume&#8221;.

---

### Post by heir4c on 2013-10-08
Normally, when you plup in a HD then Ubuntu recognise direct the HD and you must see it in Nautilus and on the Desktop or now with Unity in the Launcher-bar on the left.
Can't you see the HD there?
I have here plug in a second HD and it's mounted on /media/.... automatic. No configuration at all.

---

### Post by apmcd47 on 2013-10-08
Okay, assuming you have a new disk at /dev/sdb, and you have created two primary partitions sdb1 and sdb2 as ext3 filesystems, which you want mounted at /data and /images respectively:

Open two terminal windows. In one type:```
blkid
```
and in the other type```
cd /etc
sudo cp -p fstab fstab-orig
sudo vim fstab
```
Now add something like this to your fstab
```

UUID=xxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /data         ext3    defaults 0 2
UUID=xxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /images         ext3    defaults 0 2

```
replacing the strings of x with the actual UUID for /dev/sdb1 and /dev/sdb2 respectively, as found in the first terminal.
Now type ```
sudo mount -a
``` after saving the file and it should mount those file systems. Obviously, change the mount points and file systems for the ones you used.

Andrew

---

### Post by apmcd47 on 2013-10-08
> **heir4c said:**
> Normally, when you plup in a HD then Ubuntu recognise direct the HD and you must see it in Nautilus and on the Desktop or now with Unity in the Launcher-bar on the left.
Can't you see the HD there?
I have here plug in a second HD and it's mounted on /media/.... automatic. No configuration at all.

This is true for external disks. This, however, is an internal disk. Also Steve_Campisano mentions having a database on this disk. It probably needs a permannent mount point which is guaranteed not to change when rebooted when more disks are attached.

Andrew

---

### Post by Steve_Campisano on 2013-10-08
Andrew, Thanks for the quick response to my issue.

I performed the blkid which returned the following related to my two new partitions:

/dev/sdb1: UUID="1d11019b-b1c5-4e8a-b60f-89fd94906f31" TYPE="ext4" 
/dev/sdb2: UUID="daf46f14-fb9b-4970-830c-db992ce42685" TYPE="ext4" 

Are you saying that I need to input the complete UUID for these partitions in your above example (mine are ext4 by the way and I hope this is not an issue):

UUID=[FONT=Verdana]1d11019b-b1c5-4e8a-b60f-89fd94906f31[/FONT] /data         ext4    defaults 0 2
UUID=[FONT=Verdana]daf46f14-fb9b-4970-830c-db992ce42685[/FONT] /images         ext4    defaults 0 2

I just want to make certain of this before I proceeed.

Thanks.

---

### Post by Elfy on 2013-10-08
Make sure the mountpoints have been created before you run sudo mount -a or it will fail.

```
sudo mkdir /data /images
```

Personally I mount my data inside /mnt - /mnt/music for instance.

---

### Post by Steve_Campisano on 2013-10-08
Okay, now I'm glad I asked .....

Once I open a terminal session and issue the sudo mkdir commands where will these directories be created?  This is what I'm trying to understand.

I'm assuming that these mount points directories need to be created on each of these new partitions I have created using GParted (correct)? If this is true will this mkdir command put these on /dev/sdb1 and /dev/sdb2.

---

### Post by Elfy on 2013-10-08
No  you need to put the mountpoints in the installed system folder system.

So - open a terminal then do sudo mkdir /*whatever* or if you want to put them inside /media or /mnt then it's

sudo mkdir /*mnt*/data or /*media*/data

Whatever the case - create them BEFORE you run the mount command.

some examples in /
```

hob@hob:~/Desktop$ cd /
hob@hob:/$ ls
bin    dev   initrd.img      lib64       mnt   root  srv  usr      vmlinuz.old
boot   etc   initrd.img.old  lost+found  opt   run   sys  var
cdrom  home  lib             media       proc  sbin  tmp  vmlinuz
hob@hob:/$ sudo mkdir /anything
[sudo] password for hob: 
hob@hob:/$ ls
anything  dev         initrd.img.old  media  root  sys  vmlinuz
bin       etc         lib             mnt    run   tmp  vmlinuz.old
boot      home        lib64           opt    sbin  usr
cdrom     initrd.img  lost+found      proc   srv   var
hob@hob:/$ sudo mkdir /anythingIwant
hob@hob:/$ ls
anything       cdrom  initrd.img      lost+found  proc  srv  var
anythingIwant  dev    initrd.img.old  media       root  sys  vmlinuz
bin            etc    lib             mnt         run   tmp  vmlinuz.old
boot           home   lib64           opt         sbin  usr
hob@hob:/$ cd anything
hob@hob:/anything$ sudo mkdir Iwant
hob@hob:/anything$ ls
Iwant
hob@hob:/anything$
```

---

### Post by Morbius1 on 2013-10-08
Your mixing up physical devices and their partitions with mount points.

Your operating system ( which may be located in something like /dev/sda1 ) is mounted to "/".

All other mount points that the system will ever use is mounted within that main mount point. So when you use something like this:
>  UUID=[FONT=Verdana]1d11019b-b1c5-4e8a-b60f-89fd94906f31[/FONT] [COLOR=#0000cd]**/data**[/COLOR]         ext4    defaults 0 2
You are telling the OS that there is a partition with that UUID ( aka /dev/sdb1 ) and that you want it mounted within the main OS mount point ( the "/" part ) with this name: data

---

### Post by heir4c on 2013-10-08
> **apmcd47 said:**
> This is true for external disks. This, however, is an internal disk. Also Steve_Campisano mentions having a database on this disk. It probably needs a permannent mount point which is guaranteed not to change when rebooted when more disks are attached.

Andrew

With the database: Ok I understand that. (and specially when it is with a shell and without a gui.)
But it's a internal disk here, I plug it in inside my case so it mount directly via /media. (a old laptop sata disk 5400rpm with 3 distro's on it)

---

### Post by Steve_Campisano on 2013-10-08
Thanks a lot guys for this information it helps tremendously in my understanding of this issue.

I did the following:

1. created two directories under /mnt .... one was /data the other was /images

   As I originally stated I plan on using /data for my mySQL database(s) and /images for my photography (one of my many hobbies).

2. copied my fstab to back it up and then updated fstab and added the following lines atthe end of the file:

# new /dev/sdb1
UUID=1d11019b-b1c5-4e8a-b60f-89fd94906f31 /mnt/data       ext4    defaults 0 2
# new /dev/sdb2
UUID=daf46f14-fb9b-4970-830c-db992ce42685 /mnt/images         ext4    defaults 0 2

Then I rebooted.

I tried to copy a document into the /mnt/data folder by it returned a "Permission Denide" error.

I assume I need to change the permission on these partitions.  And I need to know how to do that so I can get access to them.

Also, I was "assuming" that these partitions (drives) would appear when I launched Files.  They do not.

I checked them in GParted and they both are listed with the correct mount points.

Any info on what I should do to get access to these drives?

---

### Post by Morbius1 on 2013-10-08
Because ownership and permissions on a Linux filesystem are contained within the filesystem itself. By default a newly created ext4 partition will mount with owner = root and permissions of 755. Root can write to the partition ( the "7" part ) and everyone else can only read ( the "5" part ).

There are a hundred ways to enable you to write to the partition. One of them is to take possession of the mounted partition:
```
sudo chown steve /mnt/data
```

---

### Post by Elfy on 2013-10-08
You want to use chown and chmod to set up ownership and permissions. 

I like this page to explain chmod - you can see what and how different numbers for permisssion works - [http://www.ss64.com/bash/chmod.html](http://www.ss64.com/bash/chmod.html)

[http://www.ss64.com/bash/chown.html](http://www.ss64.com/bash/chown.html)

You can also get man pages in a terminal 

```
man *command*
```

You can also do the same with a root filemanager. 

I used to use 

```
sudo chown *user*.*user* /mnt/*partitionname*
sudo chmod 770 /mnt/*partitionname*
```

those permissions suited me

---

### Post by Steve_Campisano on 2013-10-08
I used the chown command for both and things appear to be working fine now.

It's a learning curve moving from Windows to Ubuntu but I'll get it.  But that's that fun part, I'll be learning something new.

I took a UNIX course way back in the 80's when I was working with AT&T in Florida so it's been a while since I've played around with this OS.

But I have a LAMP installed and i'm running Netbeans developing some PHP stuff (again another learning experience).

Again, thanks for all the help. 

I'm sure I'll be back asking more questions.

---

