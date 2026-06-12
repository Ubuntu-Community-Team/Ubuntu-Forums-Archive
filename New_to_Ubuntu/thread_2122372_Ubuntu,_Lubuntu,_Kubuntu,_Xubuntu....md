---
title: "Ubuntu, Lubuntu, Kubuntu, Xubuntu..."
date: 2013-03-04
forum: New to Ubuntu
---

### Post by Tuexnovia on 2013-03-04
hi guys I'd like to ask you something, when I'm looking for something in internet I find so many places where they are talking about XUBUNTU, KUBUNTU, and different distros that makes me feel completly lost...

I'd like to read a usefull guide to start with.


For example today I learner for what is it use.

Synaptic, GDBI, Lubuntu software center... (At the beggining you had to put a code in the terminat to update it right? why and where does it come from that?)

I mean you had to put apt- get update

I'm just asking stupid questions that I always try to type one google, but now I'll really need a guide to know the basic controls easy comands. AND SO ON...


Thanks guys. I hope you understand me xD

---

### Post by Tuexnovia on 2013-03-05
I'd like to know for example what should be learning... thanks

Ubuntu or lubuntu?

sorry for this little misunderstanding of concepts, my problem is that I don't think that I'd be able to learn a new language...

---

### Post by slooksterpsv on 2013-03-05
Ubuntu is the main distro, Lubuntu, Xubuntu, Kubuntu (well it's not anymore for Kubuntu) are all recognized distrobutions via Canonical. They all base their packages and code off of Ubuntu's base which is Ubuntu is a derivative of Debian - but since has branched off.

If you're using Lubuntu you're using what's called LXDE - Lightweight X11 Desktop Environment.
If you're using Ubuntu you're using what's called Unity - it's a dashboard based Desktop Environment that left behind the old Gnome2 packages - instead of going with Gnome 3 they made their own variant for a more polished version of Linux.

If you want a starter guide you can try this site it looks like it has good information on what's what - more geared for Ubuntu: [http://ubuntuguide.org/wiki/Ubuntu_Quantal](http://ubuntuguide.org/wiki/Ubuntu_Quantal)

If you're a real beginner and don't want much hassle of trying to figure out how to install this or that, you can use Linux Mint. Don't use Debian Edition as that's what they call a "rolling release" which means that as soon as packages are updated, they are pushed to your system. Instead of verifying that they're stable and work with other core-components to make sure they don't crash, they push it out - the latest and greatest - so you're system can break easily with it (granted I haven't had an issue yet).

Linux Mint was based off of Ubuntu but they now use more Debian than Ubuntu - it's a whole structured Tier of things - as an oversimplification:
Debian makes packages and puts them into DEB files using (depending on Testing, Unstable, or Stable) whichever version you're using. It's the barebones so to speak so it gives you the basics to get up and running. They don't have a software center like Ubuntu does, but they use Synaptics (which can be hard to figure out at first).
Ubuntu uses Debian as it's base, but configures it more custom-like for what it feels users should have, it then runs its own repositories (software caches) for users to download based on what they feel to make the system the best in their eyes. Usually newer software (not patches or security updates) aren't pushed out until a new release (e.g. 12.10, 13.04, 13.10) and they have a specific release schedule - every 6 months. PPAs are setup to where other users/developers/etc. can compile newer software and make it available to others to install - maintaining certain libraries and packages as well that may be required to install said software.
Now Kubuntu, Lubuntu, and Xubuntu take it further by taking Ubuntu and using their own set of packages, stripping what they feel isn't necessary and running their own DE (desktop environment) K = KDE, L = LXDE, and X = XFCE

You can always as questions and we'll answer. This is a very basic and oversimplification of things but it may help.

---

### Post by sudodus on 2013-03-05
> **Tuexnovia said:**
> I'd like to know for example what should be learning... thanks

Ubuntu or lubuntu?

sorry for this little misunderstanding of concepts, my problem is that I don't think that I'd be able to learn a new language...
- Are you trying to learn about Ubuntu and Lubuntu before installing?

- Or have you already installed one of the Ubuntu flavours?

- Do you need help to select what to install or do you need help to get an installed system running or do you want to do something in particular with your system?

If you describe your computer and what you intend to do with it, it will be easier to give advice.

- brand name and model
- present operating system
- cpu
- ram
- hard disk drive (and how is free)
- graphics card/chip
- wifi card/chip

and what will be your main tasks to do with Ubuntu, Lubuntu, Xubuntu or Kubuntu.

---

### Post by mastablasta on 2013-03-05
> **slooksterpsv said:**
> Ubuntu is the main distro, Lubuntu, Xubuntu, Kubuntu (well it's not anymore for Kubuntu) are all recognized distrobutions via Canonical.

i need to correct you here. Kubutnu is official Ubuntu spinoff. It's just that the developer that was working on is not on Cannonical payrole anymore. or he was moved to another cannonical department. not sure exaclty. anyway it then became like Xubuntu and Lubuntu ->> a community driven project. however, Kubuntu version 12.04 LTS still has official Cannonical 5 year support.

---

### Post by Tuexnovia on 2013-03-05
Guys really thanks for everything I was quite lost like 2 hours ago and now I've been reading this:
[http://linuxcommand.org/lc3_lts0060.php](http://linuxcommand.org/lc3_lts0060.php) -and I feel more comfortable-
well I'm coming from a win7 I7 gtx 670 total gamer. I do always OC I know really well the world of computers etc...

I wanted to start learning about something new, but I feel like a new language will be to hard for me (just my opinion)
Now I'm runiing Lubuntu 12.10 (I learned how to check my version **lsb_release -a** xD) but you see I can't remember all the codes.

in a Atom N455 1.6Gh perfect to put Lubuntu well is already on it xD

My idea right now that I can't put games and do hard work with this poor CPU. I'd like to learn something first of all I'll try to be able to manage and understand Lubuntu like if I were in windows to feel that I can do everything. and then I'll start learning something else it can be regarding S.O networking and so on. but I'd like to start slowly reading guides trough internet and maybe like this I fin my career and I really go to study something. I'm 27 so I'll have to run xD

---

### Post by sudodus on 2013-03-05
> **Tuexnovia said:**
> Guys really thanks for everything I was quite lost like 2 hours ago and now I've been reading this:
[http://linuxcommand.org/lc3_lts0060.php](http://linuxcommand.org/lc3_lts0060.php) -and I feel more comfortable-
well I'm coming from a win7 I7 gtx 670 total gamer. I do always OC I know really well the world of computers etc...

You can run the Ubuntu flavours with most eye-candy on this computer: Ubuntu with Unity and Kubuntu with KDE.
> 
I wanted to start learning about something new, but I feel like a new language will be to hard for me (just my opinion)
Now I'm runiing Lubuntu 12.10 (I learned how to check my version **lsb_release -a** xD) but you see I can't remember all the codes.

in a Atom N455 1.6Gh perfect to put Lubuntu well is already on it xD

My idea right now that I can't put games and do hard work with this poor CPU. I'd like to learn something first of all I'll try to be able to manage and understand Lubuntu like if I were in windows to feel that I can do everything. and then I'll start learning something else it can be regarding S.O networking and so on. but I'd like to start slowly reading guides trough internet and maybe like this I fin my career and I really go to study something. I'm 27 so I'll have to run xD

Lubuntu with its ultra light-weight desktop environment LXDE works well with your Atom CPU. So learn your graphical user interface programs for browsing, editing (word processing), image processing, video playing and editing ...

It is easy to find tips, tutorials and even books (paper books, ebooks) browsing the internet. Browse quickly until you find something really interesting :-)

And then it is time to learn about terminal window command. Read for example this thread

[[COLOR=#ff0000]https://help.ubuntu.com/community/CommandLineResources[/COLOR]]("https://help.ubuntu.com/community/CommandLineResources")

Good luck :-)

---

### Post by Tuexnovia on 2013-03-05
Really thanks for everything guys, let me ask you something else and I won't disturb you again xD I mean xDDDD
I'd like to study something related with networking like CCNA, but I can't find a guide to follow and get started... (Just in case you know something)
and my last question, I've checked in google but I can't find a proper way to mont my seconds partition NTFS (D:) and leave it like this even when I reboot...

Thanks I can't stop reading xDDD

Lubuntu 12.10

---

### Post by sudodus on 2013-03-05
> **Tuexnovia said:**
> Really thanks for everything guys, let me ask you something else and I won't disturb you again xD I mean xDDDD
I'd like to study something related with networking like CCNA, but I can't find a guide to follow and get started... (Just in case you know something)
and my last question, I've checked in google but I can't find a proper way to mont my seconds partition NTFS (D:) and leave it like this even when I reboot...

Thanks I can't stop reading xDDD

Lubuntu 12.10

Is this what you mean [[COLOR=#ff0000]https://en.wikipedia.org/wiki/CCNA[/COLOR]]("https://en.wikipedia.org/wiki/CCNA")?

You can browse the internet for ***ubuntu network*** and find several interesting links

Also remember the security aspects. Start with this link [[COLOR=#ff0000]https://wiki.ubuntu.com/BasicSecurity[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")

---

### Post by sudodus on 2013-03-05
> **Tuexnovia said:**
> and my last question, I've checked in google but I can't find a proper way to mont my seconds partition NTFS (D:) and leave it like this even when I reboot...


Do you want to mount ***always***? Or would it be OK to mount it with the file browser (by selecting it), when you need it?

---

### Post by mastablasta on 2013-03-05
only for second question : 
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

look under manual set up help

used to be a GUI for that, but they were causing major errors for some, so they were dropped.

---

### Post by Tuexnovia on 2013-03-05
> **sudodus said:**
> Do you want to mount ***always***? Or would it be OK to mount it with the file browser (by selecting it), when you need it?

Thanks to all of you guys, really thanks.

1. I wanted always the partition mounted, (I've checked the article very helpful "I can't find the option always mounted") but I guess messing with the proper file I'll be able to do it.

2. Yes I wanted to study something about networking CCNA cysco, just to do something with my life. (Maybe I like to learn about linux instead) I'll need good tutorials...

Most of the commands... I don't even know how to use them but with YouTube I can easily see how they work and then be able to settle a nice base to start with.

What do you think?

I follow a guide of the basic commands but in the third page with just one example I was already lost.

---

### Post by audiomick on 2013-03-05
> **Tuexnovia said:**
> 
1. I wanted always the partition mounted, (I've checked the article very helpful "I can't find the option always mounted") [COLOR="#FF0000"]but I guess messing with the proper file I'll be able to do it.[/COLOR]...

Yes, you need to "mess with" fstab. 

From the article that mastablasta linked to, this is the pertinent section

[https://help.ubuntu.com/community/AutomaticallyMountPartitions#Editing_Ubuntu.27s_filesystem_table]("https://help.ubuntu.com/community/AutomaticallyMountPartitions#Editing_Ubuntu.27s_filesystem_table")

---

### Post by sudodus on 2013-03-05
> **Tuexnovia said:**
> Thanks to all of you guys, really thanks.

1. I wanted always the partition mounted, (I've checked the article very helpful "I can't find the option always mounted") but I guess messing with the proper file I'll be able to do it.


You can enter a line in the file [FONT=courier new]**/etc/fstab**[/FONT] for that second partition.. You get one template from the root drive (mounted on /), and you can get another one if you automount the second partition with your file browser. See in the file [FONT=courier new]**/etc/mtab**[/FONT]. There is also good information in the following man pages:

```
man fstab
```
```
man mount
```

Who do you want to own the file system and who do you want to have access? Only you or several users? Maybe several users should have one directory tree each on the partition.

---

### Post by Tuexnovia on 2013-03-05
Seriously guys... I've been checking this and is really difficult, xDDD I won't give up but wow... guys... I hope I can be able to learn but how people can learn all those codes? WOW xDDD

Ok I've seen that when I mount the NTFS partition as /dev/sda3 trough disks in preferences,(Automatic) I can even mount that disk that already is in:.....

/media/tuexnovia/D
I'd like to put it in:... for more organization...
/home/tuexnovia   


I think that is possible but well first I'm gonna try to find the way of mount the disk and keep it mounted forever...
I thought that I just had to open fstab's file and just edit it... and is not so...

I was thinking ok now I'll check fstab and let's see what it says... then I auto mounted the disk and then when I checked again the file fstab it didn't change anything...

> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0



> /dev/loop0 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
none /run/user tmpfs rw,noexec,nosuid,nodev,size=104857600,mode=0755 0 0
/dev/sda2 /host fuseblk rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 0 0
gvfsd-fuse /run/user/tuexnovia/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,user=tuexnovia 0 0
/dev/sda3 /media/tuexnovia/D fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0

                               [ Read 15 lines (Warning: No write permission) ]



>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   122882047    61337600    7  HPFS/NTFS/exFAT
/dev/sda3       122882048   625137663   251127808    7  HPFS/NTFS/exFAT
tuexnovia@ubuntu:/etc$ 





Jejej no worries guys I'm just learning thanks for all your help. I keep going and reading tutorials and watching videos...  xDD

---

### Post by sudodus on 2013-03-06
> **Tuexnovia said:**
> Seriously guys... I've been checking this and is really difficult, xDDD I won't give up but wow... guys... I hope I can be able to learn but how people can learn all those codes? WOW xDDD

Ok I've seen that when I mount the NTFS partition as /dev/sda3 trough disks in preferences,(Automatic) I can even mount that disk that already is in:.....

/media/tuexnovia/D
I'd like to put it in:... for more organization...
/home/tuexnovia   

Yes, I could see that you have a wubi install with windows on this partition
```
/dev/sda2 /host fuseblk rw,nosuid,nodev,relatime,user_id=0,group_id=0,allo  w_other,blksize=4096 0 0
```
and that the second partition D: can be automounted as  /media/tuexnovia/D
```
 /dev/sda3 /media/tuexnovia/D fuseblk rw,nosuid,nodev,allow_other,default_permissions,bl  ksize=4096 0 0
```
and there is also a small partition (I guess a recovery partition for Windows)
```
 /dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
```
> 
I think that is possible but well first I'm gonna try to find the way of mount the disk and keep it mounted forever...
I thought that I just had to open fstab's file and just edit it... and is not so...

I was thinking ok now I'll check fstab and let's see what it says... then I auto mounted the disk and then when I checked again the file fstab it didn't change anything...
Jejej no worries guys I'm just learning thanks for all your help. I keep going and reading tutorials and watching videos...  xDD
Ubuntu's own partitions reside in files and are loop-mounted
```
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
```

I think this setup is OK, at least for a test period. You need not arrange anything to mount
```
/dev/sda3 /media/tuexnovia/D
```
Let it automount when you click on its icon in the file browser :-)

But after a test period with wubi, I suggest that you consider migrating to a real installation of Ubuntu, for example a dual boot installation alongside Windows.

See this link [[COLOR=#ff0000]https://help.ubuntu.com/community/MigrateWubi[/COLOR]]("https://help.ubuntu.com/community/MigrateWubi")

---

### Post by Tuexnovia on 2013-03-06
Ok I'll just mount the drives trough the application DISK, I wanted to do what I'm asking for, "just as a challenge"

Well About wubi, I've to tell you that the first that I did when I tried to install Lubuntu was to put it in a USB bla bla, and due that my netbook is **** I couldn't manage an error that was giving me all the time, and in the middle of the installation was crashing. I put the error in google and many people was having the same problem than me, xDDD

I eventually decided to install Lubuntu instead trough that wuby.

Now I want to change what you told me xDDD

---

### Post by sudodus on 2013-03-06
> **Tuexnovia said:**
> Ok I'll just mount the drives trough the application DISK, I wanted to do what I'm asking for, "just as a challenge"

Well About wubi, I've to tell you that the first that I did when I tried to install Lubuntu was to put it in a USB bla bla, and due that my netbook is **** I couldn't manage an error that was giving me all the time, and in the middle of the installation was crashing. I put the error in google and many people was having the same problem than me, xDDD

I eventually decided to install Lubuntu instead trough that wuby.

Now I want to change what you told me xDDD
Before migrating to a dual boot you should

1. Backup your system or at least your personal data (because things can go wrong). I suggest that you put the backup on an external drive.

2. Booted from the Ubuntu boot drive, edit your partitions with gparted, to create space for the real dual boot partition and a swap partition.

3. Migrate ...

---

### Post by Tuexnovia on 2013-03-06
> **sudodus said:**
> Before migrating to a dual boot you should

1. Backup your system or at least your personal data (because things can go wrong). I suggest that you put the backup on an external drive.

2. Booted from the Ubuntu boot drive, edit your partitions with gparted, to create space for the real dual boot partition and a swap partition.

3. Migrate ...


Ok thanks but I'm scared because if it goes wrong, there is just one way of install this S.O due to my netbook as I said. (Well maybe other version of lubuntu or whatever make it work...)

Will I get something changing what you're telling me? (Just organization right?) 

Besides I won't use windows I don't need it, unless I have to use photshop... This is a netbook I guess that in a I7, I won't be using Lubuntu, I like it but if I learn the shell and so on... what I'm gonna do with that if what I do is just playing, watching movies make some videos and browsing... with I7 and SSD, win 7 flies... I know is not the same but it's enough for me right now unless I study something...

I'd like to study networking CCNA, for now but I can't find any good tutorial... Well I want to study that just because I know it will be useful in a future just because of that... I don't know guys you can maybe change my mind xDD

---

### Post by sudodus on 2013-03-06
It seems to be too early to migrate your wubi install. Don't worry about that now, continue to discover your system and the programs that belong to it, maybe learn a little about terminal window commands etc.

I'm sorry, but I don't know anything about CCNA. I think that you can find a lot about it browsing the internet and search with different word combinations. Maybe someone else can give you some good links :-)

---

