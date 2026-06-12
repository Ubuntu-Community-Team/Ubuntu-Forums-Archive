---
title: "Can Windows 8.1 be installed over Ubuntu 13.04?"
date: 2014-01-28
forum: New to Ubuntu
---

### Post by courtneyking1990 on 2014-01-28
I started using Ubuntu because I was curious about Linux and since it was free I figure why not. I wiped Windows 8 (smart move:roll:) and installed Ubuntu and while its a nice OS with some great benefits, I have a hard time trying to install things and of course compatability issues so I'm thinking about biting the bullet and purchasing the Windows 8.1 download. My question is will the Windows OS install over it or would I need to wipe Ubuntu first and then install?

I should say I'm not the techie type so its hard for me to understand complicated computer terms/explanations so if you don't mind can you kinda break it down?

---

### Post by GrouchyGaijin on 2014-01-28
You will need to wipe the drive.
Can you install Windows 8.1 by itself?  It [COLOR=#ff0000]*may*[/COLOR] be an upgrade to 8.0 that won't install unless you already have Windows 8.0 installed on the computer.

---

### Post by Bucky Ball on 2014-01-28
Off-topic, but what programs did you have trouble trying to install?

---

### Post by 3rdalbum on 2014-01-28
Well, if you are having trouble installing things on Ubuntu, then you are probably making it more difficult than it needs to be. If you haven't already, you could look up some tutorials or ask about it on here.

If you want to remove Ubuntu to install Windows, you need to back up your Ubuntu personal files. Then boot the Windows CD, it will give you the option of erasing a partition or the whole hard drive to install Windows.

It will not preserve your Ubuntu files unless you purposely install to a different partition.

---

### Post by fantab on 2014-01-28
> **courtneyking1990 said:**
> My question is will the Windows OS install over it or would I need to wipe Ubuntu first and then install?

If all of your HDD space is occupied with Linux/Ubuntu partitions then Windows will NOT install, or will probably ask you to reformat the partitions with Windows filesystem. So it will be a good idea to setup your partitions for Windows.

If I were you, I would **dual-boot** both **Ubuntu and Windows**. I would keep my peresent Ubuntu install and install Windows to its own partition separately.
And if you consider dual-boot, then its important to see how you've installed Ubuntu, ie, did you install it in UEFI mode or 'Legacy/CSM/MBR' mode? So start by posting the output of the following commands from Ubuntu:
```
sudo parted -l
sudo fdisk -l
```

I also suggest you clarify all the problems (with installing software) you have with Ubuntu before you invest in Windows. For all we know, you could find easy alternatives in Linux.

---

### Post by courtneyking1990 on 2014-01-28
> **fantab said:**
>  I also suggest you clarify all the problems (with installing software) you have with Ubuntu before you invest in Windows. For all we know, you could find easy alternatives in Linux.

> **3rdalbum said:**
> Well, if you are having trouble installing things on Ubuntu, then you are probably making it more difficult than it needs to be. If you haven't already, you could look up some tutorials or ask about it on here.

> **Bucky Ball said:**
> Off-topic, but what programs did you have trouble trying to install?

I've tried to install SuperOneClick for rooting my phone and tablet but it never installed correctly with WINE. I wanted to start using LiveMocha (a language learning site) but it tells me the site is not compatable with Linux systems and I know that any language software I buy probably won't either. Other programs I've tried to install are Audacity and Debut Video Capture Software. 

My main problem is that I don't think I'm competent enough for Ubuntu, for me things are harder to do 1) because it's different from what I'm used to and 2) because I don't understand the jargon. You guys mentioned a installing Windows on it's own partition. No clue what that means, I guess you mean on it's own special space in the hard drive.

> **GrouchyGaijin said:**
> You will need to wipe the drive.
Can you install Windows 8.1 by itself?  It [COLOR=#ff0000]*may*[/COLOR] be an upgrade to 8.0 that won't install unless you already have Windows 8.0 installed on the computer.

I'm not sure. I think it is but I told the person on the customer chat that I had another OS altogether and he didn't indicate to me that I'd have to download Windows 8 and then upgrade.


Here's what I got from the Terminal when I did the sudo parted -l:

Model: ATA TOSHIBA MK3265GS (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  316GB  316GB   primary   ext4            boot
 2      316GB   320GB  4020MB  extended
 5      316GB   320GB  4020MB  logical   linux-swap(v1)


And this is the sudo fdisk -l:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000c090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   617287679   308642816   83  Linux
/dev/sda2       617289726   625141759     3926017    5  Extended
/dev/sda5       617289728   625141759     3926016   82  Linux swap / Solaris

---

### Post by fantab on 2014-01-28
You should probably install Windows if it is inevitable. I still use Windows to play games which are only available in that platform.

On my Netbook I have 320Gb Hard Disk and I use it to dual boot Windows (the graphics card here is not well supported in Linux so I use Windows to watch HD movies/videos and YouTube HD Videos) and Linux. 
This how the partitions on my HDD are set up:
70Gb Primary NTFS Windows C:
100Gb Primary NTFS DATA or D:
20Gb Primary EXT4 Ubuntu /
150Gb EXTENDED
146Gb Logical Ext4 Linux DATA or /home
4Gb Logical SWAP

You can use the above partition scheme as reference and Dualboot.
Ubuntu can read and write to NTFS Windows partitions but Windows cannot use Linux partitions. So you can share NTFS DATA or D: partition between Win and Ubuntu.

If you like the idea of Dual-Boot then let us know and we'll help you set em' up.
Good Luck...

---

### Post by courtneyking1990 on 2014-01-28
> **fantab said:**
> You should probably install Windows if it is inevitable. I still use Windows to play games which are only available in that platform.

On my Netbook I have 320Gb Hard Disk and I use it to dual boot Windows (the graphics card here is not well supported in Linux so I use Windows to watch HD movies/videos and YouTube HD Videos) and Linux. 
This how the partitions on my HDD are set up:
70Gb Primary NTFS Windows C:
100Gb Primary NTFS DATA or D:
20Gb Primary EXT4 Ubuntu /
150Gb EXTENDED
146Gb Logical Ext4 Linux DATA or /home
4Gb Logical SWAP

You can use the above partition scheme as reference and Dualboot.
Ubuntu can read and write to NTFS Windows partitions but Windows cannot use Linux partitions. So you can share NTFS DATA or D: partition between Win and Ubuntu.

If you like the idea of Dual-Boot then let us know and we'll help you set em' up.
Good Luck...

That would be ideal. I know there's gonna be a new version of Ubuntu coming up in April so I'm definitely curious about that and whether or not that'll bring some better compatibility. That's the thing, with Windows I know just about everything program will work with it, but its so damn expensive plus you need to other programs to make it safe and usable for school and work purposes. My boyfriend works in IT and advised me against using a Linux OS but at least running Ubu I don't have to try to buy what should be offered from the get go (a viable office suite and good virus and malware protection)

Hell, I might just stick with Ubuntu. In that case, any thing you guys can suggest I read so I can figure out how to actually use it smoothly?

---

### Post by newb85 on 2014-01-28
> **courtneyking1990 said:**
> I've tried to install SuperOneClick for rooting my phone and tablet but it never installed correctly with WINE. I wanted to start using LiveMocha (a language learning site) but it tells me the site is not compatable with Linux systems and I know that any language software I buy probably won't either. Other programs I've tried to install are Audacity and Debut Video Capture Software. 


Yeah, using WINE to install applications for interfacing with peripherals doesn't work.  There are linux versions of SuperOneClick that can be installed, though.

From what I've read, you can get LiveMocha to work by having your browser tell LiveMocha you're using Windows.  However, that seems to be a bit of an involved process.

Audacity is a piece of cake to install.  It's in the repositories, so it can be installed from the Software Center.

Debut Video Capture is Windows utility.  You're best off here installing a Linux program that does the same thing.  Desktop Recorder is in the repos and can be installed from the Software Center, too. 

> **courtneyking1990 said:**
> 
My main problem is that I don't think I'm competent enough for Ubuntu, for me things are harder to do 1) because it's different from what I'm used to and 2) because I don't understand the jargon. 


It does take some time and effort to get the hang of it, and it's not for everyone.

---

### Post by GrouchyGaijin on 2014-01-29
Basically, Windows and Linux are two different systems and programs written for Windows do not run in Linux.
As you mentioned there is WINE that will allow you to run [COLOR=#ff0000]***some***[/COLOR] Windows programs.  Some is the key word.
Personally, I run Microsoft Office 2007 using a version of WINE.

In most cases however there are Linux alternatives to the programs you run in Windows.
For video editing I use a program called Kdenlive.
Some programs like Thunderbird for email come in both Windows and Linux versions.

I'm going to buy a new computer on my next trip to the US and have decided to buy one with Ubuntu preinstalled and then add Windows to it in order to have a dual boot machine.
The reason is because I need to run a program called EndNote, which is Windows only and I'd like to run iTunes so I can sync my iPhone.
If it were not for EndNote though, I wouldn't even consider a dual boot machine.

---

### Post by mastablasta on 2014-01-29
> **newb85 said:**
> From what I've read, you can get LiveMocha to work by having your browser tell LiveMocha you're using Windows. However, that seems to be a bit of an involved process.
.

if this is really the case then solution is rather simple. just install user agent switcher in firefox: 
[https://support.mozilla.org/sl/questions/679978](https://support.mozilla.org/sl/questions/679978)
[https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/)

playonlinux can be used to install windows programs in wine. it might be easier on the eyes :-)

disk partition = part of disk (in windows they are marked as separate disks C:\>, D:\>, E:\> ...in linux they are sda1, sda2 ...).

reformating the disk during windows install to NTFS will erase all data and enable windows to be installed. creating dualboot is a bit more complicated.

sometimes epopel use alternative programs in linux (not the same but similar, sometimes better), while sometimes even thta is not possible so we just use windows.those with more powerfull mashcines will run windows in virtual maschine inside linux. i can't afford a powerfull mashcine so i run dualboot when i need to.

---

### Post by fantab on 2014-01-29
> **courtneyking1990 said:**
> That would be ideal. I know there's gonna be a new version of Ubuntu coming up in April so I'm definitely curious about that and whether or not that'll bring some better compatibility. That's the thing, with Windows I know just about everything program will work with it, but its so damn expensive plus you need to other programs to make it safe and usable for school and work purposes. My boyfriend works in IT and advised me against using a Linux OS but at least running Ubu I don't have to try to buy what should be offered from the get go (a viable office suite and good virus and malware protection)

Hell, I might just stick with Ubuntu. In that case, any thing you guys can suggest I read so I can figure out how to actually use it smoothly?

I suggest you read this: [Linux is NOT Windows]("http://linux.oneandoneis2.org/LNW.htm").
And also:[Why not Windows]("http://getgnulinux.org/windows/")

Also search and read about 'Open Source Software'  and 'Free Software'.
This article highlights the difference:[URL="https://www.gnu.org/philosophy/open-source-misses-the-point.html"] [https://www.gnu.org/philosophy/open-source-misses-the-point.html](https://www.gnu.org/philosophy/open-source-misses-the-point.html)
[/URL]
Ubuntu releases a new version twice a year, every six months. There are two kinds of releases, 1. Regular (supported for 9 months since the date of release), 2. LTS (Long Term Support- supported for 5 years). 
LTS version is released every two years. The next release 14.04 (20**14**.April) is going to be LTS which is likely to supported until 2019.

Though I have MS Windows7, I don't have MS Office. Sometimes, when I need to share and collaborate .docx files I use 'Online Office via my Skydrive. Skydrive gives me about 7Gb free storage and its more than enough for docs. For everything else I got LibreOffice.... which is also available for Windows.

@GrouchyGaijin: Have you tried [Zotero]("https://www.zotero.org/") as an alternative to EndNote? Though storage beyond 300Mb is NOT free, its available across platforms.

Since we are so accustomed to using Windows, it takes time to be "Windows Free". Until such time lets dual-boot.

---

### Post by Bucky Ball on 2014-01-29
Zotero and Zim do me. Zotero is brilliant, but not a drop-in replacement for Endnote. Not many Endnote users are happy with Zotero (evidenced by my many interactions about it on here). ;)

---

### Post by GrouchyGaijin on 2014-01-29
Yeah - I tried Zotero, but I prefer EndNote.

---

### Post by courtneyking1990 on 2014-01-29
Thanks for the help everyone. If there are workarounds to compatablity issues then I'm all for just using the workarounds. I'm not doing anything super complicated although I'll be looking at Accounting software pretty soon. As I've said I like Ubuntu and I orginally replaced Windows in the first place to force myself to learn more about the computer but I slipped back into old habits.

---

### Post by GrouchyGaijin on 2014-01-29
> **courtneyking1990 said:**
> Thanks for the help everyone. If there are workarounds to compatablity issues then I'm all for just using the workarounds. 

This is a community.  We help each other.  Welcome to the club :P
When you have a question post it to the form, there are a lot of really experienced users here.  Most people here are friendly and helpful.
You won't find any replies along the lines of RTFM, so don't be shy.

---

