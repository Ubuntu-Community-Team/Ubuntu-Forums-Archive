---
title: "No network device detected in ubuntu 12.04.Dual booted with windows 7/net is ok"
date: 2013-06-13
forum: New to Ubuntu
---

### Post by davidcholo on 2013-06-13
Arrrrghhhh!! ita been days! I can't connect to internet in ubuntu! why? please help me,  had to download manually some applications like linux-headers-generic, i tried installing build essentials and the required programs or so, all i got is this


dpkg: dependency problems prevent configuration of dpkg-dev:
dpkg-dev depends on libdpkg-perl (= 1.16.1.2ubuntu7); however:
Package libdpkg-perl is not installed.
dpkg: error processing dpkg-dev (--install):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of g++:
g++ depends on g++-4.6 (>= 4.6.3-1~); however:
Package g++-4.6 is not installed.
dpkg: error processing g++ (--install):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6-dev:
libc6-dev depends on libc6 (= 2.15-0ubuntu10.2); however:
Version of libc6 on system is 2.15-0ubuntu10.3.
libc6-dev depends on libc-dev-bin (= 2.15-0ubuntu10.2); however:
Version of libc-dev-bin on system is 2.15-0ubuntu10.3.
dpkg: error processing libc6-dev (--install):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
linux-headers-generic depends on linux-headers-3.2.0-48-generic; however:
Package linux-headers-3.2.0-48-generic is not installed.
dpkg: error processing linux-headers-generic (--install):
dependency problems - leaving unconfigured
Setting up make (3.81-8.1ubuntu1) ...
dpkg: dependency problems prevent configuration of build-essential:
build-essential depends on libc6-dev | libc-dev; however:
Package libc6-dev is not configured yet.
Package libc-dev is not installed.
Package libc6-dev which provides libc-dev is not configured yet.
build-essential depends on g++ (>= 4:4.4.3); however:
Package g++ is not configured yet.
build-essential depends on dpkg-dev (>= 1.13.5); however:
Package dpkg-dev is not configured yet.
dpkg: error processing build-essential (--install):
dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
dpkg-dev
g++
libc6-dev
linux-headers-generic
build-essential


well, i followed the instructions of mr chili555 on one of his replied threads.
[http://ubuntuforums.org/showthread.php?p=12206393](http://ubuntuforums.org/showthread.php?p=12206393)
is seems i have problems, i hope you can help, and even if someone else, please, we are using ubuntu now at school!!! I'm a computer science student, please help! i'll be happy to reply if someone ask me something

---

### Post by steeldriver on 2013-06-13
Hello and welcome to the forum

Let's take a step back - exactly what wireless AND wired devices does your computer have? Can you post the output of

```
lspci -nn | grep -e '\[0200\]' -e '\[0280\]'
```

---

### Post by chili555 on 2013-06-15
Yes, please identify your hardware as steeldriver requested.

---

### Post by davidcholo on 2013-06-15
OOOOOOHHHHH!!! Thank you all for your replies, okey i'll do that, but please be patient cause I literally have to boot to ubuntu and boot again to windows 7 to be able to reply,

---

### Post by davidcholo on 2013-06-15
Here is the output.

03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8161 Gigabit Ethernet [1969:1091] (rev 10)

---

### Post by chili555 on 2013-06-15
We could instruct you how to continue to download dependencies and dependencies of dependencies for several dozen posts and eventually you'd get the driver *alx* compiled and installed. That assumes you stick with the process for that long and don't get disgusted and go back to Windows.

Or you could install 13.04 and your device would work immediately with no other steps!

What do you prefer? steeldriver and I will help in either case. We secretly hope you pick 13.04 but don't tell anybody! Shhh!

---

### Post by davidcholo on 2013-06-15
well sir, if it what you suggest then I shall go with 13.04, :)
so now, first i think i have to get rid of my 12.04, any recommendation?

---

### Post by chili555 on 2013-06-15
> **davidcholo said:**
> well sir, if it what you suggest then I shall go with 13.04, :)
so now, first i think i have to get rid of my 12.04, any recommendation?I am not very experienced with dual-boot, but I'd suggest you open Update Manager, and select 'For any new version.' as attached. You should be offered an update to 13.04 and I'd install it.

steeldriver will chime in with his opinion, I hope.

---

### Post by davidcholo on 2013-06-15
mmm. but will I even be able to update without internet?

---

### Post by davidcholo on 2013-06-15
arrrgghh,,,if needed, I think it would be hard to uninstall ubuntu cause I installed it in the windows partition!!! arrrgggghhhh!!! I'm scared now,

---

### Post by chili555 on 2013-06-15
Hang on, we're rounding up the experts for you.

---

### Post by davidcholo on 2013-06-15
well how about this sir, If I won't be able to update ubuntu cause no internet, I think its better to have 12.04 fixed first then go with the update,

---

### Post by wildmanne39 on 2013-06-15
Hi, I recommend that you download 13.04 using windows then put the livecd in the  drive and choose something else under creating and removing partitions, then remove your ubuntu partitions.

I always reformat my partitions, but do not touch the widows partitions they should say ntfs.

After you have removed the ubuntu partitions you can follow the directions in this link for creating new partitions and installing 13.04.

If you do not remove the ubuntu partitions first then you will end up with 12.04 and 13.04 installed with windows.
[http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UbyL3hWZiJM](http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UbyL3hWZiJM)

If you have any questions please ask before proceeding.
Thanks

---

### Post by chili555 on 2013-06-15
Thank you, Wild Man! I appreciate your help.

---

### Post by varunendra on 2013-06-15
> **davidcholo said:**
> arrrgghh,,,if needed, I think it would be hard to uninstall ubuntu cause I installed it in the windows partition!!! arrrgggghhhh!!! I'm scared now,
Is it a WUBI install (Ubuntu installed on top of Windows as an application when Windows was running)?
If not sure, please post output of -
```
sudo fdisk -l
mount
```
..from Ubuntu.

> **davidcholo said:**
> well how about this sir, If I won't be able to update ubuntu cause no internet, I think its better to have 12.04 fixed first then go with the update,
Assuming it is a fresh installation of Ubuntu and you don't have any data or applications to save on it, it would be much better to just download the ISO of 13.04, burn it to a DVD (or make a live USB with it), then do a fresh install on its separate partition. It'll be quicker, safer and easier.

For downloading, I recommend 64-bit via official torrents (to ensure integrity of the downloaded ISO) : [www.ubuntu.com/download/desktop/alternative-downloads](www.ubuntu.com/download/desktop/alternative-downloads)


**EDIT:**
I see I'm late to the party (Wild Man ate the cake), but still I'd like to know if it is a WUBI installation. If so, then 'Uninstalling' Ubuntu should be another piece of cake :P
Just 'uninstall' it from control panel like you do with any other normal application.

---

### Post by davidcholo on 2013-06-15
> **varunendra said:**
> Is it a WUBI install (Ubuntu installed on top of Windows as an application when Windows was running)?
If not sure, please post output of -
```
sudo fdisk -l
mount
```
..from Ubuntu.


Assuming it is a fresh installation of Ubuntu and you don't have any data or applications to save on it, it would be much better to just download the ISO of 13.04, burn it to a DVD (or make a live USB with it), then do a fresh install on its separate partition. It'll be quicker, safer and easier.

For downloading, I recommend 64-bit via official torrents (to ensure integrity of the downloaded ISO) : [www.ubuntu.com/download/desktop/alternative-downloads]("http://www.ubuntu.com/download/desktop/alternative-downloads")


**EDIT:**
I see I'm late to the party (Wild Man ate the cake), but still I'd like to know if it is a WUBI installation. If so, then 'Uninstalling' Ubuntu should be another piece of cake :P
Just 'uninstall' it from control panel like you do with any other normal application.


here is the output sir, 

sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xc3e2044a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   247351295   123572224    7  HPFS/NTFS/exFAT
/dev/sda3       247351296   494702591   123675648    7  HPFS/NTFS/exFAT
/dev/sda4       494702592   976771071   241034240    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 15.9 GB, 15936061440 bytes
98 heads, 34 sectors/track, 9341 cylinders, total 31125120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064    31125119    15558528    c  W95 FAT32 (LBA)


mount

/dev/loop0 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda2 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
gvfs-fuse-daemon on /home/david/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=david)
/dev/sdb1  on /media/CHOLO type vfat  (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)

well sir, will that be ok  cause I only have 32 bit,

I just made a discovery, I see a ubuntu folder in my drive c:(windows OS), and saw an uninstall-wubi application, thus that mean it is a wubi installation?
And I can also see an Icon of ubuntu in remove programs(control panel)

---

### Post by 3rdalbum on 2013-06-15
You have used the Windows-based installer.

You can remove 12.04 from the Windows "Add/Remove Programs".

You should burn the 13.04 disc image to a CD or create a bootable USB, and boot your computer from it. When asked, choose "Try Ubuntu". When you get to the desktop, see if your network connection works. Then you can double click the Install Ubuntu icon and follow the on-screen instructions for installing Ubuntu alongside Windows.

---

### Post by davidcholo on 2013-06-15
by the way guys, I must tell you something, in the link given by mr. Wild Man, when I installed ubuntu, I was only at step 3, then I think it loaded so long or I restarted it or it rebooted and I booted to windows 7, there in one dialog box, there is choosing sizes, language, and then the username and password, then have to reboot, well I forgot the whole scenario, but I just want to tell you guys cause it might be the cause or something, and maybe that happened because I used universal usb installer, I don't realy know, I'm not an expert at this, :),

---

### Post by davidcholo on 2013-06-15
> **3rdalbum said:**
> You have used the Windows-based installer.

You can remove 12.04 from the Windows "Add/Remove Programs".

You should burn the 13.04 disc image to a CD or create a bootable USB, and boot your computer from it. When asked, choose "Try Ubuntu". When you get to the desktop, see if your network connection works. Then you can double click the Install Ubuntu icon and follow the on-screen instructions for installing Ubuntu alongside Windows.

Alright sir, I am currently downloading 13.04 now. Now, can you help me sir how to make a properly bootable usb?
And there is an option in bios what to boot. I use a flash drive. Then there are two names with my flash drive's name in the option. But the other one have EFI something, sorry I really don't remember.

---

### Post by davidcholo on 2013-06-15
I'm really sorry if I ask too many questions guys. I just don't wan't to learn it like 1, 2, 3.

---

### Post by davidcholo on 2013-06-15
mr Wild Man, it seems I will be able to uninstall ubuntu 12.04, so after i downloaded 13.04, i'll try it then, thank you, keep in touch please, :D

---

### Post by wildmanne39 on 2013-06-15
Hi,  in 13.04  wubi was discontinued so you will have to do a normal dual boot install.

If you are using UEFI it will be much more difficult and beyond my experience, it would be best to start a new thread for that or I can change the title of this one.

Oldfred is the best with that particular setup, he helped me install ubuntu with windows 8 because it is such a hassle using UEFI, hopefully you do not use UEFI for windows 7.
Thanks

---

### Post by davidcholo on 2013-06-16
Hello. yes I didn't used it. I am now installing 13.04. it's in windows again, it says
Downloading ubuntu-13.04-desktop-amd64.iso.torrent

but why?
I used 32 bit cause I have 32 bit, is it normal?

---

### Post by varunendra on 2013-06-16
> **davidcholo said:**
> Hello. yes I didn't used it. I am now installing 13.04. it's in windows again, it says
Downloading ubuntu-13.04-desktop-amd64.iso.torrent

but why?
I used 32 bit cause I have 32 bit, is it normal?

No, it's not normal. But what is your CPU model? Maybe it is 64 bit one?

---

### Post by davidcholo on 2013-06-16
arrrrggg, i thought I had it, its an error again,:((((((((((((((((((((((((((((((((((((((((((
 i have amd processor,

---

### Post by davidcholo on 2013-06-16
I'm like extremely sad about this.!!!! aaaaahhh ahhhhh aahhhhh!

---

### Post by davidcholo on 2013-06-16
please someone help me!!! I'm like desperate !!!! T_T

---

### Post by davidcholo on 2013-06-16
> **varunendra said:**
> No, it's not normal. But what is your CPU model? Maybe it is 64 bit one?

It really is 32bit, my system. oh men, what now

---

### Post by wildmanne39 on 2013-06-16
Hi, go back to the download page and select the 32bit ubuntu version.

Please install without intalling inside windows because wubi is not officially suported in 13.04.

I am going to be off a lot today because it is Fathers Day.
Thanks

---

### Post by davidcholo on 2013-06-16
> **Wild Man said:**
> Hi, go back to the download page and select the 32bit ubuntu version.

Please install without intalling inside windows because wubi is not officially suported in 13.04.

I am going to be off a lot today because it is Fathers Day.
Thanks

Hello sir, I have finished installing it. It works now. I am quite certain that I downloaded exactly 32 bit.

 File name: ubuntu-13.04-desktop-1386

It didn't work the first time because malwarebytes detected something and deleted it. Well sir, that's what I was thinking. You said its not supported in 13.04 but it still went to windows again. I don't know. Maybe I'm doing something wrong again.

---

### Post by wildmanne39 on 2013-06-16
If it is working then I would not worry about it but you need to know that wubi is just for testing.

Here is a link that says it is not supported anymore but might still work.
[http://askubuntu.com/questions/285418/upgrading-from-12-10-wubi-install-to-13-04](http://askubuntu.com/questions/285418/upgrading-from-12-10-wubi-install-to-13-04)

Is your wireless working now?
Thanks

---

### Post by davidcholo on 2013-06-16
Well sir i use a pc. Its not wife-enabled. 
Wow. I hope it doesn't make problems in future.


[SIZE=6]I JUST WANT TO SAY THANK YOU TO ALL THAT REPLIED TO THIS THREAD AND HELPED ME!!! THANK YOU VERY MUCH! I REALLY APPRECIATE IT! 
IT WORKS!!! I HOPE NOT JUST FOR NOW. :D
[/SIZE]

---

### Post by wildmanne39 on 2013-06-16
Your welcome!

---

