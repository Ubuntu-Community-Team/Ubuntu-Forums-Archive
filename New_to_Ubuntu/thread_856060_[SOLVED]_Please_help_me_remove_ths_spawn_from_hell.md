---
title: "[SOLVED] Please help me remove ths spawn from hell OS"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by mefistofeles666 on 2008-07-11
please don't give me #$%...I just spent hours installing ubuntu 8.04 and Now i've spent like 3 freaking hours trying to uninstall it. Why? be cause nothing works!!! I can't even install jaja, and firefox is constantly freezing and I need to restart several times.

Point being, my experience has been crap. I installed because supposedly I could remove it easily without losing files...but I don't know how to.

Please someone help this poor soul in distress and tell me how to remove/uninstall ubuntu 8.04 and be able to start my laptop in windows? I can't even do that!!! How do I start in windows..I just want to go back to my reliable xp that has never, ever, ever crashed on me.info you need: xp, sp2. and i don't have the windows cd and I made the mistake to install ubuntu in the same drive so no partition. 
please help me!!!

---

### Post by philinux on 2008-07-11
Ok one thing, have a coffee/tea calm down.


Boot the machine, when you see **grub stage 1.5** press the esc key.

A menu will appear, If you have not wiped windows one option will mention windows OS.

Select this and press enter. If not you have wiped windows.

---

### Post by jimmy the saint on 2008-07-11
If you did not install Ubuntu to a seperate partition, threby allowing both OSs to coexist, you removed windows.  There is no going back without a windows install disk. If you installed Ubuntu to a seperate partition, reformat that partiton.  That will remove Ubuntu.  From my brief googling it appears that you need an xp cd to restore the windows bootloader though.

---

### Post by aktiwers on 2008-07-11
It could sound like you deleted Windows from your computer? 
Dont you see windows as an option when you boot your computer? I mean when it loads Grub?

But before jumping to any conclusions, try open op Terminal (Applications = Accessories = Terminal) and type in:
```
sudo fdisk -l
```

Type in your password and copy paste the output here.
Note it wont show you typing the password, just type it anyways and hit Enter.

By the way, dont be so mean to Ubuntu ;) 
Its a good OS, and we did not see you ask for any solutions to the problems you might be having.

But please post the output of that command, so we can see if Windows is still there

---

### Post by steveneddy on 2008-07-11
One post?

Where is the asking for support thread?

Aren't you going to ask for help to get it running?

We don't even know your hardware specs.

Ubuntu works well for me.

Did you download it? Maybe you burned it too fast.

Burn the .iso slow, like 4X or slower.

Good luck.

---

### Post by alienexplorers on 2008-07-11
Just put your windows disk in and select to format the partition.  Reload windows and using windows partition manager reformat any other partitions you have.

---

### Post by Bucky Ball on 2008-07-11
Alienexplorers has got it when he says chuck in the Windows CD and partition from there. You really need to find out what you have on there first though, Windows could still be there but your bootloader is just confused. This will help you find out if that is the case:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

When you have fixed all this up, get a piece of paper, imagine your 80 Gb hard drive or whatever size and divide that up. A partition for Windows (which you should load first) and then a partition for Ubuntu. Then a third partition for data in fat32 format so you can share between OSs. Keep all your personal data stored OFF the os partitions (Drive C is called 'Windows' with windows and its programs all that resides there).

This way, if you ever run into hot water again, you won't lose your precious personal data (and we all hate that) and you can kill and reinstall whatever on your two OS partitions, leaving the good stuff alone. Please tweak this for your system, but these are my general guidelines when I'm setting up a machine. You may have 4 drives and partitions everywhere, in which case you could spend sometime planning, and OS on a seperate drive rather than partition is even better. Then you never have this issue and if you do, it is a bootloader problem, not a data loss one.

Perhaps a little partition planning. Cheers and good luck ... I used Gutsy for about 6 months but Hardy 8.04 has worked a treat for me (it's the bomb!) so persevere if you can be bothered, definitely worth the effort ...

Really good point made by steveneddy, which leads to another ...  

> Burn the .iso slow, like 4X or slower.

Did you check your disk before you installed? When you boot the installer disk, in the options under 'install ubuntu', there is an option that allows you to check your disk for defects before you kick off ... *always* run that, you can save yourself hours.

If you have fixed this problem and are never to return, you forgot to say goodbyes ... ;(

---

### Post by mefistofeles666 on 2008-07-11
bucky ball..would you be kind enough to tell me how to do everything you mentioned? I didn't know I could still divide win and ubu into two diff partitions at this point...

sudo fdisk -l gave me this

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04230422

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11787    94679046   83  Linux
/dev/sda2           11788       12161     3004155    5  Extended
/dev/sda5           11788       12161     3004123+  82  Linux swap / Solaris


I don't really know what it means..and I think it did delete windows, since everyone here keeps saying that if you don't install it in a diff partition it deletes windows...I thought I could access "my documents" from windows, which I actually was able to but then my c:/ stopped appearing after I restarted it the first time. now all I see is file system...wtf?
and no I'm not hating on the os, I was excited to use it, I'm just disappointed it came up to be worse than windows. but I've been reading that many laptop users have the same problem. and the problem is not really my system specs...but rather the fact that nothing seems to work and I can't even enter windows and my files anymore.

well if you want me to ask a question that will satisfy then tell me..why is it that I can't install updates, firefox keeps getting black and white and gets stuck, and how in the hell do i install flash player 9? I miss me youtube :P


and thanks for your helpful responses!!! and believe me, if I could keep win and ubu and have dual boot I would...but how do I do that at this point?

---

### Post by jimmy the saint on 2008-07-11
This is all good advice, but I think the fact that he does not have his windows cd is being missed.  If he did wipe windows out, he is in a pickle.

---

### Post by nothingspecial on 2008-07-11
I`ve you`ve no windows disk, my advice would be to post your problems here and see if we can`t fix them.
 I remember I wanted to chuck the whole damn thing in the bin when I first got ubuntu. Wouldn`t change it for the world now.

---

### Post by ad_267 on 2008-07-11
> **mefistofeles666 said:**
> sudo fdisk -l gave me this

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04230422

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11787    94679046   83  Linux
/dev/sda2           11788       12161     3004155    5  Extended
/dev/sda5           11788       12161     3004123+  82  Linux swap / Solaris


I don't really know what it means..and I think it did delete windows, since everyone here keeps saying that if you don't install it in a diff partition it deletes windows...I thought I could access "my documents" from windows, which I actually was able to but then my c:/ stopped appearing after I restarted it the first time. now all I see is file system...wtf?
and no I'm not hating on the os, I was excited to use it, I'm just disappointed it came up to be worse than windows. but I've been reading that many laptop users have the same problem. and the problem is not really my system specs...but rather the fact that nothing seems to work and I can't even enter windows and my files anymore.

well if you want me to ask a question that will satisfy then tell me..why is it that I can't install updates, firefox keeps getting black and white and gets stuck, and how in the hell do i install flash player 9? I miss me youtube :P

From the output of fdisk -l you don't have a Windows partition any more, only Ubuntu. So you need a Windows install CD to get Windows back.

I think your problems should be able to be solved pretty easily as everything works fine for most people.

So what do you mean by you can't install updates? Do you get some kind of error? Ubuntu 8.04 comes with Firefox 3.0 beta by default so hopefully if you update to the release version these problems will go. 

You can install flash player 9 by installing the flashplugin-nonfree package. I recommend you install the ubuntu-restricted-extras package as this comes with other things like mp3 codecs you will probably want. Go to System - Administration - Synaptic Package Manager. Click on Settings - Repositories and make sure there is a tick next to "universe", "restricted" and "multiverse." Click on the reload button and then search for ubuntu-restricted-extras. Mark this package for installation then click Apply.

If you're wondering why you need to download a package for mp3 codecs read this: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by philinux on 2008-07-11
I hope he's got a backup of his important stuff.

---

### Post by zxscooby on 2008-07-11
yes, you have overwritten the windows install on your hdd
your fdisk info would list a partition labeled as fat32 or ntfs
if you hadn't.
I would try starting over with a fresh ubuntu install , run all the updates and install the restricted extras and see how it goes. There is a good chance you will be able to find info here at the forums to get you going. 
 I have ubuntu installed on all my computers, some have taken a little work to get fully functional but most have been pretty easy. The main problem i've had is with hardware providers not offering good support for linux drivers but i have never not been able to work around them.

---

### Post by aktiwers on 2008-07-11
Yep I am sorry to say that it looks like you have deleted your Windows.

But hey, about the flash thing follow this guide:
[http://ohioloco.ubuntuforums.org/showpost.php?p=5197197&postcount=11](http://ohioloco.ubuntuforums.org/showpost.php?p=5197197&postcount=11)

You can also view YouTube through your movieplayer.
Goto Applications = Sound and Video = movie player

In there pick "edit" then "plugins" and enable Youtube plugin.
Then pick YouTube instead of "playlist" in the sidebar and start searching.

But agian, it might be easyer to install flash manually like in the link above.

Also make sure your Ubuntu is up-to-date! Look next to the clock, there should be a small update icon. It updates the whole system and all apps at the same time, meaning you will get the latest version of Firefox, which hopefully wont get black and white all the time.

If you want Windows back, You will need the CD :(

---

### Post by Bucky Ball on 2008-07-11
Yep, windows cooked.

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

That could be of some help.

Simply, install xp. Where it gets to the partitioner, wipe all partitions (delete them) and then make one that is big enough for your XP and programs (the programs can, of course go in a totally seperate partition or drive also). 15-20GB should do and even that could be excessive for your purposes.

Leave the rest free space or partition them into appropriate sized chunks for your other plans (this is probably best) but don't bother to format them, remembering again that you are going to have to make the EXT3 partition with Ubuntu installer anyway.

Make sure your windows boot is happening once installed.

Stick in your ubuntu disk and boot from that. Check disk for defects, if clean, go ahead and install.

When it gets to the partitioner, you have a number of options (depending on what you did with windows partitioner). You can just let Ubuntu take care of the free space and install itself, or you can partition it up manually or if you have left some unformatted partitions, you can go manually and just set them up appropriately.

Do one thing for me; hit manual partitioning and have a good look around here. Don't go near your windows install so you don't break anything, but click on an empty partition or just make one for practise to get relaxed and a feel for how it works. You can ***always*** pull out and cancel everything before you hit the big red button anyhow.

** You need to research this next bit to set up Ubuntu drives properly (there must be a root partition and a swap at least).* 

Remember - Windows does not natively see EXT3 formatted drives (which is what you will use for your Ubuntu partition). Consequently, if you want to swap data between both OSs, your are going to need to use a fat32 drive somewhere along the way. And also, you will see which drive the Windows OS is on here because it gives you a list of drives. If you have done good, the first drive, first partition is where it is (and will show format as NTFS), so just stay the hell away from that and you're good to go.

That is extreme nutshell but they are some ideas to start. I know, it can be really confusing to start. My first experience I loaded Ubuntu studio which is a total command line install, and omitted to load a desktop! I spent the next few weeks on here trying to figure it out, but boy, I learnt something along the way and the wisdom and generosity of this forum I consider a gift.

Ubuntu (and linux) offer a lot of options and freedoms that others more commonly used don't, it is easy to fall down a few holes along the way but as I say, for me it was worth the trip.

[http://screencasts.ubuntu.com/MoS2007/09_Installing_Ubuntu_Part_1](http://screencasts.ubuntu.com/MoS2007/09_Installing_Ubuntu_Part_1)

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

This is my style but if anyone has any suggestions or improvements, fire away ... Good luck.

---

### Post by zxscooby on 2008-07-11
yea , what ad_267 said lol

---

### Post by Canis familiaris on 2008-07-11
Why on the earth did you install a new OS after removing the old OS that worked?
Since you mentioned you do not have the Windows CD, you have to contact your manufacturer, and get another copy of the restore disk. They may ask for fees though.
Also calm down a bit. And post exact problems you face?

Firefox Crashing? Did you update the FF 3 Beta 5 to FF3?

I suggest you first install all the updates via update manager first, then if you have your problems we may help you fixing them.

---

### Post by Shippou on 2008-07-11
> **mefistofeles666 said:**
> sudo fdisk -l gave me this

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04230422

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11787    94679046   83  Linux
/dev/sda2           11788       12161     3004155    5  Extended
/dev/sda5           11788       12161     3004123+  82  Linux swap / Solaris


I don't really know what it means..and I think it did delete windows, since everyone here keeps saying that if you don't install it in a diff partition it deletes windows...I thought I could access "my documents" from windows, which I actually was able to but then my c:/ stopped appearing after I restarted it the first time. now all I see is file system...wtf?
and no I'm not hating on the os, I was excited to use it, I'm just disappointed it came up to be worse than windows. but I've been reading that many laptop users have the same problem. and the problem is not really my system specs...but rather the fact that nothing seems to work and I can't even enter windows and my files anymore.

well if you want me to ask a question that will satisfy then tell me..why is it that I can't install updates, firefox keeps getting black and white and gets stuck, and how in the hell do i install flash player 9? I miss me youtube :P


I am really not an expert here, but looking at the results, it seems that you have not alloted a partition to Windows. This means two things: either you have unconsciously deleted windows by using the option "guided: use entire disk" from the partition option during installation, or you have deleted all the partitions if you have used "manual" from the partition editor during installation. In simple terms, **you really have deleted your windows partition (and your OS).**

Which leads you to two choices:
1. Back-up all your data, then reformat again to Windows by using the Windows installation CD. 
2. If you have a Windows restore disk (is it really called that way?), use that to restore your windows OS.

my sudo fdisk -l gave me this: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        2491     9767520   83  Linux
/dev/sda3            9694        9729      289170   82  Linux swap / Solaris
/dev/sda4            2492        9693    57850065   83  Linux

Partition table entries are not in disk order

See the HPFS/NTFS at /dev/sda1 * ? That is my windows OS installed (I am dual boot.). the others are your other partitions: /dev/sda2 your root partition, /dev/sda3 your swap (equivalent to pagefile in windows), and /dev/sda4 the home partition.

You might be wondering how I have "guessed" that. You think you are the only one who has a bad Linux experience? Well, it is really not bad. I am using Kubuntu Hardy Heron last week when I decided, "why not dual-boot?" By this I spent **two to three straight days** just to get my computer set-up the way I want (meaning maybe a minimum of 5 reformats in the course of two to three days).

Therefore, don't panic and curse every Linux distro out there... You just have to have the courage, and maybe some divine intervention, to tweak your computer in order to achieve the effect you want.

I can't help but notice people really are used to only clicking and pointing to programs. :(

---

### Post by mefistofeles666 on 2008-07-11
I have my important files in an external hard drive so losing data is not a problem. so i guess the problem now is re-sintalling windows and reinstalling ubuntu in a new partition to have dual boot.

silly question..how do u install things? I downloaded the FF3 and "unzipped" it but I don't really know how to install it.

and the app manager thing always freezes up or tells me I need to do things manually.

---

### Post by philinux on 2008-07-11
> **mefistofeles666 said:**
> I have my important files in an external hard drive so losing data is not a problem. so i guess the problem now is re-sintalling windows and reinstalling ubuntu in a new partition to have dual boot.

silly question..how do u install things? I downloaded the FF3 and "unzipped" it but I don't really know how to install it.

and the app manager thing always freezes up or tells me I need to do things manually.

Well thats a relief. I would concentrate on getting ubuntu working then.

---

### Post by nothingspecial on 2008-07-11
This is the answer to a lot of new users problems. Just follow the guide (it will take about 10 mins)

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by ad_267 on 2008-07-11
> **mefistofeles666 said:**
> I have my important files in an external hard drive so losing data is not a problem. so i guess the problem now is re-sintalling windows and reinstalling ubuntu in a new partition to have dual boot.

silly question..how do u install things? I downloaded the FF3 and "unzipped" it but I don't really know how to install it.

and the app manager thing always freezes up or tells me I need to do things manually.

You don't install things by downloading them from websites. You install them by going to Applications - Add/Remove or System - Administration - Synaptic Package Manager. Read this later when you have time: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Can you please post the exact error message you get when trying to run synaptic package manager.

---

### Post by zxscooby on 2008-07-11
how to install anything in ubuntu!

[http://monkeyblog.org/ubuntu/installing/#script](http://monkeyblog.org/ubuntu/installing/#script)

---

### Post by nothingspecial on 2008-07-11
This is another invaluable beginners guide.

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

Bookmark it!

---

### Post by aktiwers on 2008-07-11
> **mefistofeles666 said:**
> I have my important files in an external hard drive so losing data is not a problem. so i guess the problem now is re-sintalling windows and reinstalling ubuntu in a new partition to have dual boot.

silly question..how do u install things? I downloaded the FF3 and "unzipped" it but I don't really know how to install it.

and the app manager thing always freezes up or tells me I need to do things manually.

When you get the Windows cd, remember to install Windows first and then Ubuntu afterwards. Windows will overwrite the bootloader, because it does not understand to be installed together with a non-windows OS.

You can install stuff from terminal as well. (the same place you typed in sudo fdisk -l)

To upgrade your system type in:
```
sudo apt-get upgrade
```

To install apps type in
```
sudo apt-get appname
```

where you replace the appname with the actual application name. Like suggested, install the ubuntu-restricted-extras, type in:
```
sudo apt-get install ubuntu-restricted-extras
```

But start out by upgrading the system, that might really help you. 

Also check if you have any drivers waiting to be installed in System = Administration = Hardware Drivers

Good luck

---

### Post by lisati on 2008-07-11
Hey,mefistofeles666, you're doing great!

With a little perseverance, and the patience to digest the information the forum members are providing, you'll end up with a really great system!

---

### Post by ChameleonDave on 2008-07-11
> **mefistofeles666 said:**
> 
and the app manager thing always freezes up or tells me I need to do things manually.
That is not normal.  Tell us what error message you are getting, and we will solve it.

Normally, you should just open Synaptic, and install everything through that.

---

### Post by mefistofeles666 on 2008-07-11
sypnptic manager always always give me this

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


?????

I was trying to install things with terminals, but when it came to entering a destination path I would type  in /usr/lib/whateverfolder and it told me it wasn't valid even tho whatever folder did exist...any ideas on that too?

---

### Post by ad_267 on 2008-07-11
> **mefistofeles666 said:**
> sypnptic manager always always give me this

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


?????

I was trying to install things with terminals, but when it came to entering a destination path I would type  in /usr/lib/whateverfolder and it told me it wasn't valid even tho whatever folder did exist...any ideas on that too?

Go to applications - accessories - terminal and enter:
```
sudo dpkg --configure -a
```

I'm not quite sure what you mean by installing things in terminals and the errors you are getting. If you want to install something in a terminal you type "sudo apt-get install package_to_install"

apt-get or synaptic or whatever package manager you are using works out where all the files need to go, you don't need to worry about that.

---

### Post by ChameleonDave on 2008-07-11
> **mefistofeles666 said:**
> sypnptic manager always always give me this

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



Well, it sounds like you interrupted an installation.

Have you tried doing what it said?  Just open a terminal and enter the following command:

```

sudo dpkg --configure -a

```

The "sudo" part means that it should be done with full admin privileges.

---

### Post by Bucky Ball on 2008-07-11
Yep, applications - Add/Remove and there is everything (well, almost) you need. :)

One after thought ... according to microsoft, if you bought a machine with Windows pre-installed and they didn't give you the recovery disk (Windows installer included on that disk) ... that is illegal and they want you to report the offender. Just thought I'd throw that in ...

---

### Post by mefistofeles666 on 2008-07-11
thanks everyone...screwing windows up at least wasn't a completely lost cause. I can install things now. I guess I'll give this a run.

last question to chose this. when I reinstall windows, dont judge, can I create a partition from ubuntu and install it there so I don't have to reinstall ubuntu?

thanks again. I'm finally getting the hang of this.

---

### Post by nothingspecial on 2008-07-11
I believe you have to install windows first, then install ubuntu afterwards, never done it myself. However I also believe it is possible to install windows inside Ubuntu using something called a virtual machine. Someone else will have to help you with that.
If your stuck with ubuntu for a few days you`ll end up with such a fine system, who knows you might not even want to\\:D/

---

### Post by Bucky Ball on 2008-07-11
> when I reinstall windows, dont judge, can I create a partition from ubuntu and install it there so I don't have to reinstall ubuntu?

Absolutely not. You need to create an EXT3 partition and Windows can't do that - NTFS and FAT only. Partition everything else in Windows (even in disk management) and do your Ubuntu partitioning with Ubuntu installer and partitioner. It's a learning curve ... You could try something like Damn Small Linux ([http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)) or even Xubuntu which *will* install from a USB device, not the hard drive, if that is what you're after. (Have a look about) You will definitely get faster performance and a better computing experience from the hard drive set up properly though.

But now you are installing stuff and getting a better idea of how things are, you might forget about Windows and not need all this advice anyhow! Linux is just a different approach so takes awhile to get the hang. All the basic concepts of computing still apply, the air's just much clearer here ... lol

Good luck with it all. :)

---

### Post by Canis familiaris on 2008-07-11
When you have that Windows recovery disk, do the following:

(1) Backup ALL the important data.
(2) Insert the Ubuntu live CD and boot to Ubuntu.
(3) In Ubuntu live environment, Go To System->Administration->Partition Editor
(4) Delete all the partitions.(If you really dont mind and BACK UP THE 
DATA)
(5) Now you will have a blank hard disk.
(6) Create a primary partition and allocate space you have to reserve for Windows and format it as NTFS.
(7) Create another Primary partition of size 8-16GB, That would be the Ubuntu partition. Format it as ext3. This would be your Ubuntu root partition.
(8) Create another Primary partition large enough so that it could hold all your personal files like documents, movies, music, etc. Format it as either NTFS or FAT32. This would be shared b/w Ubuntu and Windows.
(9) Now reserve the rest of the space as an extended partition.
(10) Create a logical partition(read: another partition) of enough size (at least 4GB IMO, I use 64GB) so that you could store enough in your home partition. Format it as ext3. This would be Linux only /home.
(11) Create another partition of twice the size or 512MB ore than your RAM whichever is less and format is as SWAP.
(12) Restart and install Windows on the first partition. Please do not play with other partitions.
(13) After Windows is installed, boot up with Ubuntu live CD again.
(14) Start the Ubuntu Installation.
(15) In the partitioning menu select Manual Partitioning
(16) Select partition you created in (7) and choose its mount point as /.
(17) Select partition you created in (10) and choose its mount point as 
      /home.
(18) Make sure you have indeed created the SWAP partition.
(19) Install Ubuntu and set up dual boot.
(20) Come back here and we'll discuss how to share data b/w Windows and Ubuntu and also in case your primary OS is XP, how to make it default choice in GRUB.

OMG! My post is long!

---

### Post by stalkingwolf on 2008-07-11
when you get ready to reinstall windows, there is a nice utility
you can get for ubuntu.  it is called remastersys.  with it you
can create a live cd/dvd of your system with all of your settings
and such. then when you are done with your partitioning and windows install just put in YOUR disk hit install and Bobs your uncle.

---

### Post by prismpirate on 2008-07-11
> **Bucky Ball said:**
> Absolutely not. You need to create an EXT3 partition and Windows can't do that - NTFS and FAT only. Partition everything else in Windows (even in disk management) and do your Ubuntu partitioning with Ubuntu installer and partitioner. It's a learning curve ... You could try something like Damn Small Linux ([http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)) or even Xubuntu which *will* install from a USB device, not the hard drive, if that is what you're after. (Have a look about) You will definitely get faster performance and a better computing experience from the hard drive set up properly though.

But now you are installing stuff and getting a better idea of how things are, you might forget about Windows and not need all this advice anyhow! Linux is just a different approach so takes awhile to get the hang. All the basic concepts of computing still apply, the air's just much clearer here ... lol

Good luck with it all. :)

I believe that he means creating a partition in Ubuntu, before installing windows into that particular partition. This is possible, if you still have your ubuntu live-cd. Boot into your live-cd, and click on 
Partition Manager or Editor under System. (Sorry, but I have forgotten the exact name)

The partition manager should appear. Shrink your partition, and format the empty space as NTFS. Restart, and insert the Windows Install Disc. Install Windows in that particular partition. After that, restart and insert your Ubuntu Live-Cd as you can now only boot into Windows. When the live-cd has loaded, go to terminal.

Applications > Accessories > Terminal

In terminal, enter the GRUB configuration mode, type in "sudo grub" and press Enter. Then type in the following commands in sequence:
root (hd0,0)
setup (hd0)
quit
exit

Reboot the system and remove the live-cd. You'll get the GRUB bootloader but Windows won't be included. Boot into Ubuntu instead, and open terminal again.
Copy and paste this:

```
sudo gedit /boot/grub/menu.lst
```

A text file will appear, scroll all the way to the bottom.

Copy and paste this at the bottom:

> title Windows XP
root (hd0,1)
makeactive
chainloader +1


(You might want to change Windows Xp to Windows Vista if thats what you installed)

Now, press Contrl-F and search for hiddenmenu.

When you find it, change it to #hiddenmenu. 

If you want to boot into windows now, restart and use your arrow keys to navigate to the bottom of the boot selection screen. You should see Windows Xp / Vista there.

For a more comprehensive tutorial, check:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)

---

### Post by tenjin1 on 2008-07-11
If you ever get Windows back...you should just instal Wubi from [here]("http://wubi-installer.org/"). This will install ubuntu in windows partition without deleting windows and you can uninstall it from Control Panel within Windows. Wubi is for ppl like you who use their windows as primary OS but dual boot Ubuntu too. If you are just wanting to try Linux like you said...you should always try a LiveCd before you go installing it first..so expect problems if you don't.

---

### Post by steveneddy on 2008-07-12
Um, why didn't anyone tell the OP that FF3 is already installed on a Hardy install?

Someone tell him about Synaptic so he can look for software that he thinks he needs.

To the Original Poster:

How about instead of trying to install every piece of software on the planet on a system that you know nothing about, why don't you ask on the forums about software you feel that you need so that we can educate you, telling you what software does what in Ubuntu.

Most applications are available to you free of charge without having to download everything and then install it manually.

Ask and we will tell you about Synaptic and apt. 

What do you want to do on your computer? I'll bet that there is already software either installed already or ready for you to install.

With an internet connection you can get all the software you will need from the Ubuntu repositories. It's easy, fast and painless.

---

### Post by Shippou on 2008-07-12
> **Bucky Ball said:**
> Absolutely not. You need to create an EXT3 partition and Windows can't do that - NTFS and FAT only. Partition everything else in Windows (even in disk management) and do your Ubuntu partitioning with Ubuntu installer and partitioner. It's a learning curve ... You could try something like Damn Small Linux ([http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)) or even Xubuntu which *will* install from a USB device, not the hard drive, if that is what you're after. (Have a look about) You will definitely get faster performance and a better computing experience from the hard drive set up properly though.

But now you are installing stuff and getting a better idea of how things are, you might forget about Windows and not need all this advice anyhow! Linux is just a different approach so takes awhile to get the hang. All the basic concepts of computing still apply, the air's just much clearer here ... lol

Good luck with it all. :)

+1. :)

I tried installing Ubuntu first then Windows. **It does not work.**

If you want Ubuntu to be your main OS (or just use it to transfer files for it is faster to transfer files in Linux), create a /home partition using Linux and format it using ext3. Then use the application from this link: [http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html](http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html) in order to make Windows read that partition. (PS. Install it using Windows.)

I am using the application, and I am happy about it.

---

### Post by stalkier on 2008-07-12
> **nothingspecial said:**
> I believe you have to install windows first, then install ubuntu afterwards, never done it myself. However I also believe it is possible to install windows inside Ubuntu using something called a virtual machine. Someone else will have to help you with that.
If your stuck with ubuntu for a few days you`ll end up with such a fine system, who knows you might not even want to\\:D/

Correct Windows First then ubuntu. This is because of the MBR. Windows overwrites it so the GRUB loader will be lost. Installing Ubuntu second makes it a lot easier. Trust me I have done it many times. :D

---

### Post by phidia on 2008-07-13
> **Bucky Ball said:**
> Yep, applications - Add/Remove and there is everything (well, almost) you need. :)

One after thought ... according to microsoft, if you bought a machine with Windows pre-installed and they didn't give you the recovery disk (Windows installer included on that disk) ... that is illegal and they want you to report the offender. Just thought I'd throw that in ...

Actually many computer makers now have a recovery section on the drive and don't supply a physical reinstall disk anymore. (HP for one does this) You can call or email their support and get one-provided they think your situation requires that, and this situation should fit that.

BTW I read the 1st half dozen reponses and the OP's replies. When I realized he was trying linux for the 1st time on a laptop I was a little taken back. Sure plently of people here will say no problem, but I have at least 8 years using linux. I bought a HP Pavilion last Christmas time and it's July now-it still isn't configured right. I have opensuse and ubuntu 7.10 installed but neither distro can suspend _and_ resume properly and it is not and easy fix because I've been reading and researching this for a while now. There are also many posts in the hardware & laptop forum with these problems-unsolved.  Also there have been issues on laptops with wireless, cooling fan not working correctly, and the early hard drive failure, and while the hard drive issue has been pretty well addressed it's not an automatic fix on install. 
So I'm just an SOB to say all that but I think on desktops most people will do ok with using linux-a laptop is a penguin of another color.

---

### Post by Bucky Ball on 2008-07-14
I am interstate at the moment but managed to check the forum quickly and this thread still bubbling away.

Replying to a few posts; yes, I meant install Windows and do whatever NTFS partitions you want. Then install Ubuntu and do the rest (ext3, fat, whatever). As I said at the time, this how I would go about it, but take your pick.

... And yes, Phidia, thanks for that. If you machine has no recovery disk and no recovery partition (a dodgy idea I reckon and I have a HP pavillion that came with just that) it could be unlawful blah blah blah.

Add/remove, synaptics ... all there and ready to go. Some good advice for those new to Linux and beyond. Good stuff ...

---

### Post by mefistofeles666 on 2008-07-16
Hi ya'll

I just wanted to let everyone know, which I hope it helps others, that most of the problems I was having were fix after doing a fresh, yet a bit complicated, re-install. 
Apparently installing ubuntu on the same partition as windows will not only delete windows but create problems when installing the new OS.

Also, when I installed it first ubuntu gave me the choice to install in a  new partition but didn't allow me to change the size of the new partition, which just wasn't big enough to install anything, and that is why I first installed it where my windows was.

Well, thanks everyone for your help.

YAY UBUNTU.

---

### Post by nothingspecial on 2008-07-16
Glad you got it sorted. Now you can mark this thread as solved. To do this click on "thread tools" at the top of the page.

[ATTACH]77900[/ATTACH]

And if you want to thank anyone you can do so by clicking the medal thingy at the bottom of their post.

[ATTACH]77901[/ATTACH]

Have fun.:)

---

### Post by nowshining on 2008-07-16
untar the linux firefox tar.gz - untar - run the firefox script :) - put it somewhere and manually create a menu to it.

---

### Post by appi2012 on 2008-07-16
Couldn't you install windows, burn a super grub disk, and then use that to rewrite grub to the mbr?

---

