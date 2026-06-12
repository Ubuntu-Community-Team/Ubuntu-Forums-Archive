---
title: "I can't upgrade edubuntu"
date: 2012-07-30
forum: New to Ubuntu
---

### Post by lascetic on 2012-07-30
Hello, I am more than a beginner as the computer that has linux on is not even mine.

Anyway our problem is that the computer has edubuntu 9.04 installed but it won't upgrade. 
The reason for this is (I suspect) that it has been corrupted from previous upgrades that caused issues to the computer so my friend did a recovery to its original state.
It does not even show the available upgrades. I would really appreciate if anyone can suggest any links with detailed step-to-step information of how to resolve this issue. 

I have looked a bit on how to make a clean installation of the latest edubuntu, but as it seems quite complicated for a linux beginner like me (I would probably be able to do it on windows) I though to ask here coz there might be a more simple solution. You see, I haven't got a clue of where and how to get whatever drivers that a clean installation would require (linux where pre-installed when my friend bought the netbook).
Thanks a lot.

---

### Post by NikTh on 2012-07-30
Hi , 
take a look at here [http://www.edubuntu.org/download/](http://www.edubuntu.org/download/) , to see how you can download Edubuntu 12.04 LTS , or how you can transform an existing Ubuntu 12.04 LTS to an Edubuntu. 
If you want guidance on how to burn the .iso post back here. 

It would be good idea to inform us with specifications of your computer , before proceed with installation of 12.04. e.g Cpu , Ram . 
Thanks

---

### Post by arochester on 2012-07-30
9.04 stopped being supported in 2010.

A clean install is not as difficult as you think it is. Caution; it will wipe out anything you have on the Hard Disk - so if there is anything you want to save you need to copy it off first.

With 9.04 try opening a Terminal, when connected to the Internet, and issuing the commands:
sudo apt-get update
sudo apt-get upgrade

What happens? Do you get any error messages? Copy and paste the results here so we can see.

---

### Post by kansasnoob on 2012-07-30
If you are in fact running 9.04 it won't upgrade (or even update) because it's reached "End of Life". That is 9.04 was only supported until October 2010 :(

I don't typically use Edubuntu so I need to do some reading, I may even burn Edubuntu 12.04 to do some investigating myself, so be a bit patient :)

In the meanwhile please post the results of these commands from the terminal (just copy-n-paste):

```
lsb_release -a
```

```
df -H
```

```
sudo parted -l
```

```
cat /proc/cpuinfo | head -10
```

```
lspci | grep VGA
```

```
lspci | grep Audio
```

```
lspci | grep Ethernet
```

That will provide some basic system and hardware info so we can try to come up with a plan. In the meanwhile I'll study the [12.04 release notes]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/Edubuntu") :D

I do see that Edubuntu 12.04 is supported until April 2017 so lets take the time to figure out a decent plan of action, IMHO it'll be worth the effort. 

Please do be patient though as I'm working on other non-puter issues due to the heat ;)

---

### Post by kansasnoob on 2012-07-30
I'm downloading it now:

[ATTACH]221982[/ATTACH]

Since I don't typically test or use Edubuntu I want to see it for myself :D

BTW I'm going with i386 (32 bit) because my preferred testing hardware is not capable of handling 64bit.

I'm a bit surprised at the iso size; 2.6GB. No problem but it will require the use of either a DVD or an adequate USB flash drive. I'll be using a DVD :)

---

### Post by kansasnoob on 2012-07-30
Please also post the output of this command:

```
grep --color=always -i PAE /proc/cpuinfo
```

Just need to be sure the CPU has PAE support, as the release notes say:

> The Edubuntu 12.04 installation image does not include support for old computers that do not support PAE. If your computer is affected, you can either first install Edubuntu 10.04 or 11.10 and upgrade to 12.04 or you can use the Lubuntu or Xubuntu images. The non-PAE version of the Linux kernel will be dropped completely following the 12.04 release. 

This is easy to work-around but we need to know before you begin :)

---

### Post by lascetic on 2012-07-30
Wow, so many responses! Thanks to all of you guys! 

> NikTh                       Hi , 
take a look at here [http://www.edubuntu.org/download/](http://www.edubuntu.org/download/) , to see how you can download Edubuntu 12.04 LTS , or how you can transform an existing Ubuntu 12.04 LTS to an Edubuntu. 
If you want guidance on how to burn the .iso post back here. 

It would be good idea to inform us with specifications of your computer ,  before proceed with installation of 12.04. e.g Cpu , Ram . 
Thanks     I've already checked that, but as the computer has already edubuntu I can't transform it. I've downloaded **edubuntu-12.04-dvd-i386.iso**
The netbook doesn't have a DVD player so if I need a clean install we will need to do it from my **flash drive**.
Computer specs:
**Acer, intel atom CPU N270 @1.60GHz, 1.05 GHz 0.98GB RAM**

The netbook has dual booting. I'd like to ask if I have to format the linux partition and the linux boot sector and make them as one or keep the as they are and format them separately.

When I do **sudo apt-get update** I get the following:

Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty Release.gpg 
Get: 1 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/main Translation-en_GB [52.6kB] 
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) jaunty-athens Release.gpg 
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) jaunty-athens/public Translation-en_GB 
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) jaunty-athens Release 
Get: 2 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/universe Translation-en_GB [35.2kB] 
Get: 3 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/multiverse Translation-en_GB [47.5kB] 
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) jaunty-athens/public Packages    
Get: 4 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/restricted Translation-en_GB [4640B] 
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty Release                               
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/main Packages                         
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/universe Packages 
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/multiverse Packages 
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/restricted Packages 
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/main Sources 
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/universe Sources 
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/multiverse Sources 
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/restricted Sources 
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) jaunty-athens/public Sources 
Fetched 140kB in 1s (70.7kB/s) 
Reading package lists... Done 

And for **sudo apt-get upgrade**:

Reading package lists... Done 
Building dependency tree         
Reading state information... Done 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 


> kansasnoob                       Please also post the output of this command:

     Code:
     grep --color=always -i PAE /proc/cpuinfo 
Just need to be sure the CPU has PAE support, as the release notes say**grep --color=always -i PAE /proc/cpuinfo **
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm lahf_lm 
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm lahf_lm

---

### Post by lascetic on 2012-07-30
> kansasnoob                       If you are in fact running 9.04 it won't upgrade (or even update)  because it's reached "End of Life". That is 9.04 was only supported  until October 2010 :sad:

I don't typically use Edubuntu so I need to do some reading, I may even  burn Edubuntu 12.04 to do some investigating myself, so be a bit patient  :smile:

In the meanwhile please post the results of these commands from the terminal (just copy-n-paste)**lsb_release -a **
No LSB modules are available. 
Distributor ID:    Ubuntu 
Description:    Ubuntu 9.04 
Release:    9.04 
Codename:    jaunty 

**df -H** 
Filesystem             Size   Used  Avail Use% Mounted on 
/dev/sda7               46G   3.5G    40G   8% / 
tmpfs                  520M      0   520M   0% /lib/init/rw 
varrun                 520M   107k   520M   1% /var/run 
varlock                520M      0   520M   0% /var/lock 
udev                   520M   160k   520M   1% /dev 
tmpfs                  520M   308k   520M   1% /dev/shm 
lrm                    520M   2.3M   518M   1% /lib/modules/2.6.28-14-generic/volatile 
/dev/sda2               94G    58G    36G  62% /media/ACER 

**sudo parted -l **
Model: ATA ST9160310AS (scsi) 
Disk /dev/sda: 160GB 
Sector size (logical/physical): 512B/512B 
Partition Table: msdos 

Number  Start   End     Size    Type      File system  Flags 
 1      1049kB  12.9GB  12.9GB  primary   ntfs                
 2      12.9GB  106GB   93.4GB  primary   ntfs                
 3      106GB   160GB   53.7GB  extended                      
 5      106GB   108GB   2155MB  logical   linux-swap          
 6      108GB   114GB   5388MB  logical   fat32        hidden 
 7      114GB   160GB   46.2GB  logical   ext3         boot   

**cat /proc/cpuinfo | head -10** 
processor    : 0 
vendor_id    : GenuineIntel 
cpu family    : 6 
model        : 28 
model name    : Intel(R) Atom(TM) CPU N270   @ 1.60GHz 
stepping    : 2 
cpu MHz        : 800.000 
cache size    : 512 KB 
physical id    : 0 
siblings    : 2 

**lspci | grep VGA** 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) 

**lspci | grep Audio **
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 

**lspci | grep Ethernet **
01:00.0 Ethernet controller: Attansic Technology Corp. L1e Gigabit Ethernet Adapter (rev b0)

---

### Post by NikTh on 2012-07-30
> **lascetic said:**
> 
I've already checked that, but as the computer has already edubuntu I can't transform it. I've downloaded **edubuntu-12.04-dvd-i386.iso**
The netbook doesn't have a DVD player so if I need a clean install we will need to do it from my **flash drive**.
Computer specs:
**Acer, intel atom CPU N270 @1.60GHz, 1.05 GHz 0.98GB RAM**


Hi , 
you can burn the image to Usb (4GB at least)  , with unetbootin program. 

Here is unetbootin --> [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

If you have windows , you can use windows with unetbootin too. 

Thanks

---

### Post by kansasnoob on 2012-07-30
I'm glad I decided to test this. It's very much Unity:

[ATTACH]221990[/ATTACH]

I absolutely must work on some cooling for my goats (yes, real goats) and I'll be back later :D

BTW that set of testing hardware will only run Unity-2D.

---

### Post by kansasnoob on 2012-07-30
> **lascetic said:**
> Wow, so many responses! Thanks to all of you guys! 

I've already checked that, but as the computer has already edubuntu I can't transform it. I've downloaded **edubuntu-12.04-dvd-i386.iso**
The netbook doesn't have a DVD player so if I need a clean install we will need to do it from my **flash drive**.
Computer specs:
**Acer, intel atom CPU N270 @1.60GHz, 1.05 GHz 0.98GB RAM**

The netbook has dual booting. I'd like to ask if I have to format the linux partition and the linux boot sector and make them as one or keep the as they are and format them separately.

When I do **sudo apt-get update** I get the following:

Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty Release.gpg 
Get: 1 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/main Translation-en_GB [52.6kB] 
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) jaunty-athens Release.gpg 
Ign [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) jaunty-athens/public Translation-en_GB 
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) jaunty-athens Release 
Get: 2 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/universe Translation-en_GB [35.2kB] 
Get: 3 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/multiverse Translation-en_GB [47.5kB] 
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) jaunty-athens/public Packages    
Get: 4 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/restricted Translation-en_GB [4640B] 
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty Release                               
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/main Packages                         
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/universe Packages 
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/multiverse Packages 
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/restricted Packages 
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/main Sources 
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/universe Sources 
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/multiverse Sources 
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/restricted Sources 
Hit [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) jaunty-athens/public Sources 
Fetched 140kB in 1s (70.7kB/s) 
Reading package lists... Done 

And for **sudo apt-get upgrade**:

Reading package lists... Done 
Building dependency tree         
Reading state information... Done 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 


**grep --color=always -i PAE /proc/cpuinfo **
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm lahf_lm 
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm lahf_lm

I'm 90% sure we can work with that :)

Just please be patient, my goats are suffering.

---

### Post by lascetic on 2012-07-30
> **NikTh said:**
> Hi , 
you can burn the image to Usb (4GB at least)  , with unetbootin program. 

Here is unetbootin --> [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

If you have windows , you can use windows with unetbootin too. 

Thanks

Thank you, I looked at the software but it appeared easier to me to do it as suggested [here]("http://www.edubuntu.org/documentation/12.04/installation-guide")
(through  "System" menu, then "Administration", then "Startup Disk Creator"). So now I have the bootable flash drive.
From what I have gathered till now, I probably can't avoid the format. But before I do something I'd like to be sure of what I am doing, that is: do I have to format the partitions beforehand or it is done during the process, considering that the older version is already installed? Can anyone tell me from the information I posted before with which partitions I do what?

Looking at the following:
Number  Start   End     Size    Type      File system  Flags 
 1      1049kB  12.9GB  12.9GB  primary   ntfs                
 2      12.9GB  106GB   93.4GB  primary   ntfs                
 3      106GB   160GB   53.7GB  extended                      
 5      106GB   108GB   2155MB  logical   linux-swap          
 6      108GB   114GB   5388MB  logical   fat32        hidden 
 7      114GB   160GB   46.2GB  logical   ext3         boot   

I suppose the first 2 are windows and their recovery. The 3rd one (extended) I am not sure (maybe an external was connected when ran the command, I can't remember). As for 5,6,7 must be linux but I am not sure what to do with them.
Another issue is that I can't seem to boot from the flash. I only get the option between windows and linux. F12 does nothing and F2 gets me to a big bios menu that I am not sure what to do. The netbook is an Acer AO531h.

In the BIOS menu/boot I put the flash drive at the top of the list saved changes and exited. When I restarted I got this message:
SYSLINUX 3.63 Debian-2009-07-22 EBIOS Copyright (c) 1994-2008 H. Peter Anvin.
Unknown keyword in configuration file.
boot:_

And then nothing happened. I had to force shut down and reversed everything as it was. Any suggestions?

---

### Post by lascetic on 2012-07-30
I sorted out the flash drive boot thing (I should have listened NikTh in the first place and used unetbootin ;) ). So now I have the flash drive ready as bootable for edubuntu 12.04 (x32). I only need to know, as I have already said, what to do with the partitions. I also figured out what was number 3 in my previous post. Not external hard drive, but the total of the linux partition+swap+boot sector. Getting there :)

---

### Post by NikTh on 2012-07-30
Hi ,

if you continue with your bootable usb and click Install Ubuntu , at Ubuntu installer window you will see some options. Options like "Install Ubuntu alonside " or " something else" .. sorry but i cannot remember exactly all the options you will have. 
One of these options might be "Upgrade Ubuntu with ubuntu" , if you see this option click it. It will erase the Ubuntu installation without erase your personal files and will proceed with install of new Ubuntu version. 
If you not have this option the post back here with the options you have. 

Thanks

---

### Post by lascetic on 2012-07-30
> **NikTh said:**
> Hi ,

if you continue with your bootable usb and click Install Ubuntu , at Ubuntu installer window you will see some options. Options like "Install Ubuntu alonside " or " something else" .. sorry but i cannot remember exactly all the options you will have. 
One of these options might be "Upgrade Ubuntu with ubuntu" , if you see this option click it. It will erase the Ubuntu installation without erase your personal files and will proceed with install of new Ubuntu version. 
If you not have this option the post back here with the options you have. 

Thanks
Before I proceed I'd like to make sure that it will be installed in the correct partition and that it will not damage the windows partition. Where should I install it and what will happen with the previous linux swap? I guess there will be options for that but I don't want to screw up anything because I am not sure what I am supposed to do and where to install it. Thanks

---

### Post by lascetic on 2012-07-30
Finally I made it! I installed edubuntu 12.04. Tomorrow I will test it and if I have any difficulties I will come back. Thanks to everyone. I wouldn't have managed it without you guys (and a lot of reading). :)

---

### Post by NikTh on 2012-07-30
> **lascetic said:**
> Finally I made it! I installed edubuntu 12.04. Tomorrow I will test it and if I have any difficulties I will come back. Thanks to everyone. I wouldn't have managed it without you guys (and a lot of reading). :)

Hi , 

sorry for delay and glad you managed to install correctly. 

Post any other query you might have and i will be glad to answer (if i know)

Thanks

---

### Post by kansasnoob on 2012-07-31
> **lascetic said:**
> Finally I made it! I installed edubuntu 12.04. Tomorrow I will test it and if I have any difficulties I will come back. Thanks to everyone. I wouldn't have managed it without you guys (and a lot of reading). :)

I rather wish you'd waited for an answer to this:

> do I have to format the partitions beforehand or it is done during the process, considering that the older version is already installed? Can anyone tell me from the information I posted before with which partitions I do what?

Looking at the following:
Number Start End Size Type File system Flags
1 1049kB 12.9GB 12.9GB primary ntfs
2 12.9GB 106GB 93.4GB primary ntfs
3 106GB 160GB 53.7GB extended
5 106GB 108GB 2155MB logical linux-swap
6 108GB 114GB 5388MB logical fat32 hidden
7 114GB 160GB 46.2GB logical ext3 boot 

It really involved going back and also looking at this:

> df -H
Filesystem Size Used Avail Use% Mounted on
/dev/sda7 46G 3.5G 40G 8% /
tmpfs 520M 0 520M 0% /lib/init/rw
varrun 520M 107k 520M 1% /var/run
varlock 520M 0 520M 0% /var/lock
udev 520M 160k 520M 1% /dev
tmpfs 520M 308k 520M 1% /dev/shm
lrm 520M 2.3M 518M 1% /lib/modules/2.6.28-14-generic/volatile
/dev/sda2 94G 58G 36G 62% /media/ACER 

No point in discussing that now though since you already installed, but it appears that they must have had the Windows partition (/dev/sda2) set to mount in fstab, but that's just a guess ;)

The heat really wiped me out yesterday but I hope to be able to hang out in front of the A/C most of today so let us know what problems you might encounter.

---

### Post by lascetic on 2012-07-31
> **kansasnoob said:**
> I rather wish you'd waited for an answer to this:



It really involved going back and also looking at this:



No point in discussing that now though since you already installed, but it appears that they must have had the Windows partition (/dev/sda2) set to mount in fstab, but that's just a guess ;)

The heat really wiped me out yesterday but I hope to be able to hang out in front of the A/C most of today so let us know what problems you might encounter.

Sorry I have been so impatient but it really took my whole day to figure things out and when I so the option of just installing 12.04 over the old installation then I couldn't resist. I am not at all sure what you mean with "they must have had the Windows partition (/dev/sda2) set to mount in fstab".
Now, the only problem I've seen by now is that edubuntu won't restart. It just hangs on black screen and I have to force shut down. This has happened before and that is why my friend initially had the recovery which resulted in the problem with upgrading. I thought a new installation would resolve it, but it seems there is some other problem.

I've read of hundreds of people who had problem with restarting in various versions of linux but few of them seem to have resolved it and I didn't find a solid solution for edubuntu 12.04. So any suggestions are welcome.

Thank you very much.

---

### Post by NikTh on 2012-07-31
Hi , 

If this is a bug (with restart I mean) you must wait until some bug fix released and one day when update your system suddenly you will see this solved.

For now you can use a workaround commands from terminal : 
for reboot
```
sudo reboot 
```or for immediately reboot
```
sudo reboot -f
```For shutdown ```
sudo poweroff
```or for immediately shutdown 
```
sudo poweroff -f
```

And if Upgrade to Edubuntu went well , please mark this **thread as solved** from **thread tools**.

Thanks

---

### Post by lascetic on 2012-07-31
> **NikTh said:**
> Hi , 

If this is a bug (with restart I mean) you must wait until some bug fix released and one day when update your system suddenly you will see this solved.

For now you can use a workaround commands from terminal : 
for reboot
```
sudo reboot 
```or for immediately reboot
```
sudo reboot -f
```For shutdown ```
sudo poweroff
```or for immediately shutdown 
```
sudo poweroff -f
```And if Upgrade to Edubuntu went well , please mark this **thread as solved** from **thread tools**.

Thanks
I have no problems with shutting down only with reboot. The command **sudo reboot** has the same results as restart. The computer freezes and I have to force shut down. 
Thank you.

---

