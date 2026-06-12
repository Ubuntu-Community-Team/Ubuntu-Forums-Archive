---
title: "Hello everyone. Need some advice please."
date: 2019-06-03
forum: New to Ubuntu
---

### Post by koollaydtac on 2019-06-03
Hello everyone. Need some advice please. I need to know how much space I should break off for an install of Ubuntu. This is my situation. I have a Dell Optiplex 755 with Windows 7 on it. I have 7 gigs or ram. I have a AMD Radeon HD 5450 for my video card currently. The original drive with Windows 7 got messed up during an update from Avast. It is on a 232 gig hard drive. I went out and bought a 2tb drive and right now currently have Windows XP on it that I was going to use for purely maintenance programs and things of that sort, but having issues getting it to load in ahci mode. That's another headache all together. Long story short I didn't have a disk for Windows 7 so was looking for a program to image that on a separate partition for the new drive. So if anyone knows of one that would restore a Windows created image I'd appreciate it. Which once I fixed my original copy of Windows 7 on the other drive I would probably upgrade it to Windows 10 and test that out possibly. Provided I even want to bother at that point after all the headaches are all said and done.

Anyway main point of my post is I have a copy of Ubuntu the ubuntu-18.04.1-desktop-amd64.iso burned to a disk. If I recall right this is the LTS version and I assume would update to the current version once installed so figure was no need to redownload and reburn a disk for install. I originally was going to test this in virtual machine, but decided since I need or want to rather install an os on the new drive as a back up that I'd get a better test of Ubuntu on my actual machine rather then a VR machine. I wanted to or the idea was I'd toss 500 gigs for the Windows XP and 1 tb for Windows 7 and the remaining 500 gigs for Ubuntu. Thing is a brother of a friend mentioned needing 2 partitions. I read some where about needing 3. No doubt this OS seems a little more complicated for a noob. lol :D

I am currently booting my machine up with Hirens Boot CD the Windows 10 version. I was going to use AOMEI Partition Assistant to break up the partitions. Before I do anything though I wanted to check and make sure. So I wanted to ask what would be the best way possible to install Ubuntu on my rig given my situation and circumstances? Not that I am not already messing things up as it is already, but I just don't want to go from bad to worse. lol Anyway thanks in advance for any advice and help regarding this matter. I appreciate it. :)

---

### Post by QIII on 2019-06-03
Do you have valid product codes for Windows 7 and Windows 10?

---

### Post by koollaydtac on 2019-06-03
> **QIII said:**
> Do you have valid product codes for Windows 7 and Windows 10?

Only for Windows 7 Ultimate currently. I think the code I have for Windows 7 is OEM. It's a valid code, but the reason I say that is because it doesn't let me download the Windows 7 iso disk and that'd be the only reason it wouldn't. Which is weird because from what I read I can upgrade 7 to 10 with a OEM code and I can even download the Windows 10 iso disk, but I just can't download the Windows 7 iso for it. Not really getting Microsoft's logic in that. Suppose that's just another way of forcing the upgrade. lol :D

---

### Post by koollaydtac on 2019-06-03
> **koollaydtac said:**
> [Last edited by QIII]("https://ubuntuforums.org/posthistory.php?p=13863733"); 26 Minutes Ago at 08:34 PM.                                                       Reason: Implied vulgarity edited.
Sorry about that mate. And thanks for the edit. Shoulda known better. lol ;)

---

### Post by CatKiller on 2019-06-03
> **koollaydtac said:**
> Anyway main point of my post is I have a copy of Ubuntu the ubuntu-18.04.1-desktop-amd64.iso burned to a disk. If I recall right this is the LTS version and I assume would update to the current version once installed so figure was no need to redownload and reburn a disk for install. 

There is a wrinkle that's unlikely to interest you at this stage, but, yep, pretty much. 

> I originally was going to test this in virtual machine, but decided since I need or want to rather install an os on the new drive as a back up that I'd get a better test of Ubuntu on my actual machine rather then a VR machine. I wanted to or the idea was I'd toss 500 gigs for the Windows XP and 1 tb for Windows 7 and the remaining 500 gigs for Ubuntu. 

It depends what you're doing with it, in a *how long is a piece of string?* kind of way. For a basic install where you don't do much, and you don't have games, and your media is elsewhere, 100 GB will be pretty comfortable. Some people get by with just a tiny footprint. If you install a bunch of stuff because it's new and exciting, the amount of space you need will go up, of course, and if you have an enormous media library and install lots of stuff off Steam then the sky's the limit. 

> Thing is a brother of a friend mentioned needing 2 partitions. I read some where about needing 3.  

The filesystem is a tree that starts at /, which is why that's called the root directory. Everything that branches from there could be just a directory, or a different partition that you've mounted there, or some location on a completely different machine.

For you, now, the thing to know is that all the user files and settings are stored in /home. All the system stuff is in different directories (which all have a particular purpose) somewhere branching off from /, but /home is specifically set aside for user bits.

What this means is that, if /home is a different partition than the rest of /, should one wish to reinstall everything, one can do so without formatting that /home partition, and all the user settings are preserved. It can be quite handy. 

As with all partitioning schemes, the trick is knowing how much to allocate in advance. 100 GB for / and 400 GB for /home gives you plenty of space to play with. You *can* resize them later should you find that you need to, but you'll need to do it from your install disk. 

It used to be the case that you needed a swap partition, but that's not the case any more: a swap file is just as good. 

>  No doubt this OS seems a little more complicated for a noob. lol :D

It's actually really easy for a noob. You just read the instructions and do what it says. The people that have the hardest time, by far, are Windows power users that think they know better because they've been conditioned by years of Windows use. I cannot stress enough that Linux is not Windows, and that intuition based on Windows use will lead you astray very quickly.

---

### Post by Impavidus on 2019-06-03
Windows XP is, apart from returned to ashes and dust, from an era when the typical computer has a 60GB hard drive and 512MB memory. It may be simply too old for your hardware. I know for sure it can't deal with hard drives larger than 2TiB, but your's is a bit smaller.

You need for Ubuntu at least a single 15GB partition. That's all. You may even squeeze it in 10GB. A swap partition, which your friend's brother may be referring too, is optional. It can be handy if you already have one or if you want to share swap space among multiple Linux systems, but otherwise a swap file works just as well and is now the default. And you probably never use swap anyway. A /home partition can also be handy, but is optional. If you want to give more than 40GB or so to your Ubuntu system, it may be best to create a /home partition or some other sort of data partition. If you store your data in a /home partition or some other sort of data partition, 30GB is more than enough for your root partition.

On a 2TB drive you don't care about 20GB that haven't been used efficiently, so don't overthink it.

---

### Post by koollaydtac on 2019-06-03
> **CatKiller said:**
> There is a wrinkle that's unlikely to interest you at this stage, but, yep, pretty much. 
Out of curiosity what is the wrinkle? I just had to ask. lol :D

 

> **CatKiller said:**
> It depends what you're doing with it, in a *how long is a piece of string?* kind of way. For a basic install where you don't do much, and you don't have games, and your media is elsewhere, 100 GB will be pretty comfortable. Some people get by with just a tiny footprint. If you install a bunch of stuff because it's new and exciting, the amount of space you need will go up, of course, and if you have an enormous media library and install lots of stuff off Steam then the sky's the limit. 
Honestly I am actually curious if I'd get better performance gaming. I keep most my Steam games on an external drive and the ones I actually play hard core on my main drive. And while there are alot of different OS'es to choose from in this regard I looked at Ubuntu because it seemed to be the most well rounded. Everything I've read seems to be on the fence post. Some say performance is better and some say it's roughly the same. So gaming and general usage is what I'd be using it for. I figured 500 gigs should cover me for now.

 

> **CatKiller said:**
> The filesystem is a tree that starts at /, which is why that's called the root directory. Everything that branches from there could be just a directory, or a different partition that you've mounted there, or some location on a completely different machine.

For you, now, the thing to know is that all the user files and settings are stored in /home. All the system stuff is in different directories (which all have a particular purpose) somewhere branching off from /, but /home is specifically set aside for user bits.

What this means is that, if /home is a different partition than the rest of /, should one wish to reinstall everything, one can do so without formatting that /home partition, and all the user settings are preserved. It can be quite handy. 

As with all partitioning schemes, the trick is knowing how much to allocate in advance. 100 GB for / and 400 GB for /home gives you plenty of space to play with. You *can* resize them later should you find that you need to, but you'll need to do it from your install disk. 

It used to be the case that you needed a swap partition, but that's not the case any more: a swap file is just as good. 
Ok so essentially if I understand this right the install disk will take care of the partitioning and all I need to do is tell it how much space to break off for it? Will I need to worry with selecting a file system type in order to be able to transfer files between drives or will it do all that for me? I guess what i want to know is will I be able to see the disk from a Windows OS or will all my file transfers need to be done in Ubuntu as far as swapping files between drives go?



> **CatKiller said:**
> It's actually really easy for a noob. You just read the instructions and do what it says. The people that have the hardest time, by far, are Windows power users that think they know better because they've been conditioned by years of Windows use. I cannot stress enough that Linux is not Windows, and that intuition based on Windows use will lead you astray very quickly.
While I guess I could probably say I am a Windows power user I got so self delusions mate. lol If anything I think I am overly cautious because it is such a different beast, but the try option on the disk intrigued me enough to want to give it a full on test run. Anyway thanks for the advice and help. I appreciate it. :)

---

### Post by koollaydtac on 2019-06-03
> **Impavidus said:**
> Windows XP is, apart from returned to ashes and dust, from an era when the typical computer has a 60GB hard drive and 512MB memory. It may be simply too old for your hardware. I know for sure it can't deal with hard drives larger than 2TiB, but your's is a bit smaller.

You need for Ubuntu at least a single 15GB partition. That's all. You may even squeeze it in 10GB. A swap partition, which your friend's brother may be referring too, is optional. It can be handy if you already have one or if you want to share swap space among multiple Linux systems, but otherwise a swap file works just as well and is now the default. And you probably never use swap anyway. A /home partition can also be handy, but is optional. If you want to give more than 40GB or so to your Ubuntu system, it may be best to create a /home partition or some other sort of data partition. If you store your data in a /home partition or some other sort of data partition, 30GB is more than enough for your root partition.

On a 2TB drive you don't care about 20GB that haven't been used efficiently, so don't overthink it.

I was thinking about just axing XP all together because it does have some limitations and was curious if I do go that rout do you know if I could just simply restore my Windows 7 image from my external drive and it just wipe out XP and replace it with my default Windows 7 image? I only originally installed it as a work drive os for some older software I could just as easily use in a preloaded environment anyway. At best for some older games. I've yet to find a working way to install ahci drivers in to an existing install for XP and I don't want to have to switch to Legacy mode everytime just to use a simple OS. It sorta defeats the purpose of having it installed if I have to disable the main drive to boot it anyway because Legacy mode doesn't exactly allow you to choose the boot order of your hard drives sadly. If I can simply do that I may just rock it that way and leave it at 2 OS'es on the drive only. Anyway thanks mate. I appreciate it. :)

---

### Post by CatKiller on 2019-06-03
> **koollaydtac said:**
> Out of curiosity what is the wrinkle? I just had to ask. lol :D

18.04 and 18.04.1 came with the 4.15 kernel, with 4.18 available as part of the Hardware Enablement Stack. With the release of 18.04.2, 4.18 was made the default kernel. So if you install and upgrade you use an older branch than if you install the newer version, since people don't like being shunted to another branch when using a Long Term Support release. Other than that, you're going to have the same versions of software with the same security patches whichever way you go.
 
> Honestly I am actually curious if I'd get better performance gaming. I keep most my Steam games on an external drive and the ones I actually play hard core on my main drive. And while there are alot of different OS'es to choose from in this regard I looked at Ubuntu because it seemed to be the most well rounded. Everything I've read seems to be on the fence post. Some say performance is better and some say it's roughly the same. So gaming and general usage is what I'd be using it for. I figured 500 gigs should cover me for now.

Mileage varies. Some games benefit from the lower overhead of Linux compared to Windows, and some benefit from efficiencies of Vulkan compared to older versions of DirectX. On the other hand, some DirectX features haven't been implemented in the translation layers yet, and translation comes with its own overhead, and often less care was taken by developers with their OpenGL rendering paths than their DirectX rendering paths. Some games will work better, some will work worse, and some won't work at all. It's easy enough to see for yourself, thsese days. Don't be tempted to point your Linux Steam install at your NTFS Windows library, though.

For day-to-day stuff, workflow dwarfs any changes in performance. Linux would probably have the edge, but not in any way that's noticeable.
 
> Ok so essentially if I understand this right the install disk will take care of the partitioning and all I need to do is tell it how much space to break off for it? 

You'll have the easiest time if you have the space unpartitioned before you start. The installer *can* resize existing partitions, but Windows is notoriously fragile. Dumping everything into a single partition is the default, but if you *do* want a separate /home partition you'll need to use the Something Else option. I think; it's been a while.

> Will I need to worry with selecting a file system type in order to be able to transfer files between drives or will it do all that for me? I guess what i want to know is will I be able to see the disk from a Windows OS or will all my file transfers need to be done in Ubuntu as far as swapping files between drives go?

ext4 is what you should be using for your Linux partitions. Windows can't read ext4, but Linux can read and write to NTFS and FAT partitions.

> While I guess I could probably say I am a Windows power user I got so self delusions mate. lol If anything I think I am overly cautious because it is such a different beast, but the try option on the disk intrigued me enough to want to give it a full on test run. Anyway thanks for the advice and help. I appreciate it. :)

If you find yourself thinking, "ooh, I need a driver: I'll download some file off some random website!" don't do that. That's the main one that messes people up.

Good luck, and have fun with your adventure!

---

### Post by Impavidus on 2019-06-04
> **CatKiller said:**
> 
ext4 is what you should be using for your Linux partitions. Windows can't read ext4, but Linux can read and write to NTFS and FAT partitions.

But to be on the safe side, don't use Linux to write to the C partition. It's easy to damage Windows. Mount it read-only, if you mount it at all. Writing to the D partition is safe.

---

### Post by oldrocker99 on 2019-06-04
As someone who got sick of the malware magnet from Microsoft, I've been a Linux user for 9 years.

When I set up a new disk, I make a / partition no larger than 64GB, and I have had no problems creating a / partition of 32GB.

The rest I format and mount as /home. Then, installations are quick, with no need to copy everything from a backup, since /home is already mounted.

If you select "Something Else" when the installation screen comes up, you'll be able to create the partitions easily.

Here's how: [https://www.howtogeek.com/howto/35676/how-to-choose-a-partition-scheme-for-your-linux-pc/](https://www.howtogeek.com/howto/35676/how-to-choose-a-partition-scheme-for-your-linux-pc/).

---

### Post by CatKiller on 2019-06-04
> **Impavidus said:**
> But to be on the safe side, don't use Linux to write to the C partition. It's easy to damage Windows. Mount it read-only, if you mount it at all. Writing to the D partition is safe.

Yes, that's a sensible precaution.

---

### Post by bigbangnet on 2019-06-05
If its for general usage and gaming, I highly suggest sticking with Windows. Its should be your best option. Now if you want to restore it or you got a damaged copy, harddrive or installation, head over to the ms windows forum as you'll find geeks that will help you. This part can be very difficult. I've done it myself and sometimes its not easy.

If you want to dual boot, just use whatever partition for WIndows and leave unlocated space left for your Ubuntu. During the installation, Ubuntu should pick up the left space untouched and install itself there. But you'll have to fiddle with your boot loader for the dual boot to work though. Just be careful since if you ever want to use WIndows 10, those updates might mess with your MBR or boot loader and create a nightmare.

If youre experienced with Ubuntu or linux, sure go ahead with it or dualboot but if your a noob or a new guy and barely know about Ubuntu or linux, I don't think dual boot would be a good idea as if something happens (with Windows, something always happens lol) well wind might just break it.

---

### Post by gohokies95 on 2019-06-05
Sounds like windows is your primary.  That is the way my computers are oriented.  I have a 24G slice of my harddisk for ubuntu, but I automount the ExtFat drive of my windows partition, so I never really run out of room on the ubuntu side of things... Windows... that's a different story.  I could buy a 500TB of space and windows would find a way to consume it.

---

### Post by koollaydtac on 2019-06-12
Thanks for the help everyone. Sorry for the delayed response back. I been trying to set things up on the OS. I ended up having to use one partition for it anyway. I didn't realize mbr only limits you to 4 so I was already at my limit for it. For some reason I have two system reserve partitions along with the Windows 10 partition and the remaining one I used for Ubuntu. I actually do like the boot loader as it essentially has Ubuntu at the top of the list which on this drive I'd mainly be logging in to it anyway. 

One thing I noticed that struck me as odd and not sure when this changed, but the partitions no longer have drive letters assigned to them when I loaded in Hirens boot disk to work on my original Windows 7 disk. Even the system partitions that normally don't have letters get assigned letters when I load up that disk normally. So I am wondering should I be concerned? Is that normal that it does that?

My original game plan was to just swap the boot order of the drive depending on the os I wanted to use, but not sure if assigning a drive letter to it will mess something up or not when I am in my Windows 7 hard drive. If it's best I leave it with out a letter then I was wondering if is there a program I can use if I want to transfer data to it from the Windows OS while logged in to that? I also wanted to know if it is safe to enable that drive as the secondary to access files or will it remove the drive letter and make the hard drive unbootable?

Other thing I wanted to know is do I need to manually look for lack of a better term drivers for my video card and other things on Ubuntu? I was under the impression the install set all that up since I am using an AMD Radeon HD 5450 card and I only needed to worry with it if I was using a nVidia card, but when I tried to test out OBS my pc shut down and started back up every time I tried to use that program. 

I think that is so far the only questions I have currently for the moment. Over all from the testing I have done I have to actually say the OS is impressive. The menu did make me think of Windows 8.1 not gonna lie or scrolling apps on a phone, but over all I found it to be a very fast and smooth running OS. I did notice some improvements compared to Windows which I like. Not having to be as cautious or concerned about malware and stuff is also a big bonus for me. 

I did do a stress test using a mmo game/social platform called Second Life I checked out a while back with the Firestorm viewer and it seemed to run actually fairly well compared to running it on a Windows platform. That actually took some set up to get it to function decently as it should. Only issue I had with it really was not being able to get certain media to play. I tried almost every fix I could for that to no avail. If anyone knows a fix for that please let me know. Thanks.

I did try to test out 7 Days To Die, but it gave a Kernel 'KEyeHistogram' not found error in the game. So far Ubuntu users have had this issue with the A17 version of that game. If anyone's worked out a fix for that let me know that too please. Thanks.

I'll probably try and test out Ark Survival Evolved next since there is a Linux version for that. Hopefully that test will go well. 

Oh I did notice I had to reinstall GParted because it was not on the installed version of the OS. Are there any other programs on the Live version disk besides that that does install I need to grab up manually or is that the only program?

Anyway thanks for all the help everyone. I really do appreciate it mates. :)

---

### Post by Impavidus on 2019-06-12
> **koollaydtac said:**
> Thanks for the help everyone. Sorry for the delayed response back. I been trying to set things up on the OS. I ended up having to use one partition for it anyway. I didn't realize mbr only limits you to 4 so I was already at my limit for it. For some reason I have two system reserve partitions along with the Windows 10 partition and the remaining one I used for Ubuntu. I actually do like the boot loader as it essentially has Ubuntu at the top of the list which on this drive I'd mainly be logging in to it anyway. There's a limit of 4 primary partitions, but you can make one of those primary partitions an extended partition, with as many logical partitions as you want inside.

> Other thing I wanted to know is do I need to manually look for lack of a better term drivers for my video card and other things on Ubuntu? I was under the impression the install set all that up since I am using an AMD Radeon HD 5450 card and I only needed to worry with it if I was using a nVidia card, but when I tried to test out OBS my pc shut down and started back up every time I tried to use that program. No. Most drivers are built-in. If you need any proprietary drivers, there's a utility that helps you select, download and install the driver. You don't have to look for one manually.

> Oh I did notice I had to reinstall GParted because it was not on the installed version of the OS. Are there any other programs on the Live version disk besides that that does install I need to grab up manually or is that the only program?
Gparted is not installed by default because it's rarely needed. You only need it to partition external drives, something most people rarely do. Gparted is included on the live disk, because one of the main reasons why people use the live disk is to partition the internal hard drive.

---

### Post by oldfred on 2019-06-12
Microsoft confuses drives & partitions.
With Windows you have a d: drive. That can be a second partition on first drive or the first partition on a second drive.

With Linux drives & partitions are clearly separated.
The drives all are sda, sdb, sdc etc. Newer systems may have NVMe drives or very lightweight systems may have MMC devices as only drive.
Partitions then are numbers after the drive or sda1 is first partition on first drive, sdb3 is third partition on second drive.

Often best to set Windows system partition as read only. Back when I was a Windows user I would turn on the settings to see the hidden files & extensions. But often in clicking and moving mouse would move an essential folder to another (incorrect) place and totally break Windows. With Linux the hidden files & folders are always shown, so user error is a possibility.

You can then create another NTFS partition for shared data and use it as read/write from both systems. 
Newer Windows 8 & 10 have made that a bit more difficult as they use fast start up which is a form of hibernation and sets hibernation flag. Linux NTFS driver will not auto mount nor write into hibernated NTFS partitions to prevent damage. So newer Windows must have fast start up setting off.

---

### Post by koollaydtac on 2019-06-14
> **Impavidus said:**
> There's a limit of 4 primary partitions, but  you can make one of those primary partitions an extended partition, with  as many logical partitions as you want inside.
Ok I am gonna have to do some serious reading on that then. I wasn't aware of that. 

> **Impavidus said:**
> No. Most drivers are built-in. If you need any  proprietary drivers, there's a utility that helps you select, download  and install the driver. You don't have to look for one manually.
Ok I hadn't come across the utility yet for it, but considering I was using an AMD card I figured I was covered during the set up, but wanted to be sure. 

> **Impavidus said:**
> Gparted is not installed by default because  it's rarely needed. You only need it to partition external drives,  something most people rarely do. Gparted is included on the live disk,  because one of the main reasons why people use the live disk is to  partition the internal hard drive.
That makes sense. I mostly use partition programs for other drives connected to my pc which was really the only reason I was curious about it or any other differences between the live disk and the OS installed. Thanks mate. :)



> **oldfred said:**
> Microsoft confuses drives & partitions.
With Windows you have a d: drive. That can be a second partition on first drive or the first partition on a second drive.

With Linux drives & partitions are clearly separated.
The drives all are sda, sdb, sdc etc. Newer systems may have NVMe drives or very lightweight systems may have MMC devices as only drive.
Partitions then are numbers after the drive or sda1 is first partition on first drive, sdb3 is third partition on second drive.

Often best to set Windows system partition as read only. Back when I was a Windows user I would turn on the settings to see the hidden files & extensions. But often in clicking and moving mouse would move an essential folder to another (incorrect) place and totally break Windows. With Linux the hidden files & folders are always shown, so user error is a possibility.

You can then create another NTFS partition for shared data and use it as read/write from both systems. 
Newer Windows 8 & 10 have made that a bit more difficult as they use fast start up which is a form of hibernation and sets hibernation flag. Linux NTFS driver will not auto mount nor write into hibernated NTFS partitions to prevent damage. So newer Windows must have fast start up setting off.

I get what your saying, but I didn't think the hibernation feature would apply considering I don't use that copy of Windows 10 and haven't since I installed it. I only got it for DX12 games should I buy any in case I need it down the road in the future. This is what gets me though. I mounted and unmounted that partition of the drive while in Ubuntu and the next time I loaded in to Hirens Boot CD the drive letters showed back up mate. lol I got no clue what that's about, but I am wondering if I am going to have that same issue if my other hard drives are connected or if I only had with that one because it's a partition on the same drive I am using Ubuntu on? 

As far as Windows 7 goes that's on a completely separate hard drive and I am trying to set it up to once I fix that OS to where all I got to do is just switch the boot order of the hard drives according to which OS I decide to run in. For the most part I don't plan on much file swapping between the OS'es and mainly want to keep them as separate as possible. That's why I gave myself 450 gigs on Ubuntu because I figured that was more then plenty for a few games to run on it and to do basic stuff on. All my competitive gaming has to be done on Windows due to anti-cheats only working on Windows and what not. Given that I actually been enjoying Ubuntu a lot it is looking more and more likely that I'll only be on Windows for competitive gaming only. Thanks mate. :)

---

### Post by koollaydtac on 2019-06-19
Ok an update for anyone else who has this issue. I found out why 7 Days To Die was getting a error Kernel 'KEyeHistogram' not found as shown in this photo. 
[https://steamcommunity.com/sharedfiles/filedetails/?id=1772930326](https://steamcommunity.com/sharedfiles/filedetails/?id=1772930326)

From what I can tell the last supported official driver for Radeon is for Ubuntu 14.04 which you need to support OpenGL 4.4 for the card. The standard driver that comes with the current version 18.04 only supports OpenGL 3.3 sadly. Big thanks to the guys here in this thread for helping me work that one out. :)

[https://7daystodie.com/forums/showthread.php?119589-Anyone-play-on-Ubuntu](https://7daystodie.com/forums/showthread.php?119589-Anyone-play-on-Ubuntu)

I do have another issue that creeped up on me. I was in the middle of installing mod for Ark via Steam work shop and was having issues. So I decided to reboot. When I say reboot I actally mean I was trying to power off and was going to turn it back on manually. The reboot or shutdown rather hung for almost an hour on a line saying something to the effect of a boot process has started during shut shutdown and gave a time of 47 seconds to no limit. After about an hour I chanced it and hit the power button to restart. Now everytime I start I get a message saying system problem detected do you want to detect the problem now? I hit report and it goes away and nothing happens. 

In the var and crash folder I have two files both created at earlier times from this issue, but they are _lib_systemd_systemd-journald.0.crash and _usr_share_discord_Discord.1000.crash which are the only files in there. Now Discord did crash earlier along with Steam and some other programs when I was having issues with Ark hence the reason for the reboot. However that was definitely before my attempt to power down. Any idea on what I should do about that or how to fix it?

Also a minor question. On the temperature sensors what's the difference in Average and Maximum and which one should I be paying more attention to? I ask this because Average is usually the temp I get when monitoring it in Windows and Maximum is generally between 10 to 20 degree higher sometimes. Anyway thanks in advance for the help. :)

---

### Post by CatKiller on 2019-06-19
It's generally best to start a new thread with new problems, so that different people can see it.

> **koollaydtac said:**
> I do have another issue that creeped up on me. I was in the middle of installing mod for Ark via Steam work shop and was having issues. So I decided to reboot. When I say reboot I actally mean I was trying to power off and was going to turn it back on manually. The reboot or shutdown rather hung for almost an hour on a line saying something to the effect of a boot process has started during shut shutdown and gave a time of 47 seconds to no limit. After about an hour I chanced it and hit the power button to restart. Now everytime I start I get a message saying system problem detected do you want to detect the problem now? I hit report and it goes away and nothing happens. 

In the var and crash folder I have two files both created at earlier times from this issue, but they are _lib_systemd_systemd-journald.0.crash and _usr_share_discord_Discord.1000.crash which are the only files in there. Now Discord did crash earlier along with Steam and some other programs when I was having issues with Ark hence the reason for the reboot. However that was definitely before my attempt to power down. Any idea on what I should do about that or how to fix it?

I think it spams the message whenever it sees crash reports in /var/crash that haven't been uploaded. Since telling it to upload them hasn't stopped it, you might as well just delete the crash reports. Then it will stop spamming you. If you get new ones after that, you can deal with them then.

> Also a minor question. On the temperature sensors what's the difference in Average and Maximum and which one should I be paying more attention to? I ask this because Average is usually the temp I get when monitoring it in Windows and Maximum is generally between 10 to 20 degree higher sometimes. Anyway thanks in advance for the help. :)

As I understand it, the maximum value isn't generally the maximum value that it's read, but is the maximum value that the chip *can* read. Different chips will vary in what they display, of course.

---

### Post by koollaydtac on 2019-07-30
Sorry this reply is so late. I had been away from home with out internet access for a little over the last month or so. I'll probably do that. Just make another thread for some of the other issues. Only reason I was keeping everything in the same thread was to avoid having to many separate ones out there. far as the crash report goes for some reason it stopped doing it so I guess I am good now. lol On the sensor issue I did read something about that, but to me the only thing that doesn't make sense is if it's reading the maximum value the chip goes then it shouldn't be changing at all. There is not really any information out there that I have found that clearly explains what the difference is or which one is reading the actual current temperature of your machine. 

On a side note as far as gaming goes I found out at least for my machine that Ubuntu 18.04 LTS definitely didn't make the grade. My OpenGL driver only goes to version 3.1 and I'd have to downgrade to Ubuntu 14.01 I think it is if I wanted to use the AMD driver for my video card in order to raise that. I am not going to bother to downgrade though as for everything else it's seemed to be an excellent OS for and I have already set it up for the most part how I want it to be. So I'll just deal with the limitations. Plus I am just hoping I'll get lucky and they will raise the bar on that sometime in the future. If not then oh well. lol I just don't feel like I should have to down grade my OS in order to use software that should be a universal standard. So I'll be all right. lol

On the 7 Days To Die error I was getting for anyone who was interested. The only fix I found as I can type in gfx pp enable 0 in the command console, but for me it had me sliding on movement even though I could see everything fine at that point. I pretty much gave up on that point so that's where I am at with it or where I left off at rather. Anyone has better luck let me know. Thanks. I got a thread here on their official forums for those interested that I need to follow up on as well.
[https://7daystodie.com/forums/showthread.php?119589-Anyone-play-on-Ubuntu&p=986509](https://7daystodie.com/forums/showthread.php?119589-Anyone-play-on-Ubuntu&p=986509)

I am going to take your advice though and start off at another thread for another issue I recently realized I had regarding dual booting because I have ran in to some issues being able to boot in to Windows 10 now. I'll go more in to that when I finish writing up the other thread, but I'll drop the link in this one when I am done for anyone who wants to follow that.

Edited: Here is the link for anyone who wants it. Thanks again everyone. :)
[https://ubuntuforums.org/showthread.php?t=2423880&p=13876433#post13876433](https://ubuntuforums.org/showthread.php?t=2423880&p=13876433#post13876433)

Anyway I mostly wanted to drop by and say thanks to everyone for all the help and everything. I really appreciated it. Thank you all so very much and have a good one. :)

---

### Post by oldrocker99 on 2019-07-31
Back in the day, when I dual-booted, there was a Windows program called, iirc, readext2 or something like that. It would read ext4 partitions, but for that, since I was using Win7 strictly for gaming (and deep-sixed Windows once Steam for Linux got rolling), I just went back to Linux for that.

However, it **is** (or was) possible for Windows to read (only) ext4.

---

