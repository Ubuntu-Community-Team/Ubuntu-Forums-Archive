---
title: "Dual booting with Vista - Seeking reassurance"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Extraneous on 2008-04-24
Greetings,

I've been considering giving Linux a try and after some research, decided to start with Ubuntu. Fed up as I am with Windows, I'd still like to keep it for gaming and such. I've read articles and watched video tutorials on dual booting, however I still want a little reassurance that everything will work out.

So, currently I have my computer setup thuswise: I have 2 HDDs, a 250GB one and a 500GB one. The first, smaller drive is split into 2 partitions - a 50GB partition for Vista, and the rest for storage. The second, bigger drive is also for storage.

I'm planning on giving Ubuntu its own partition on the second drive, perhaps 30GB in size. I will use Vista to shrink the current volume and format the unallocated space to create a new partition, and install Ubuntu here.

So my first, simple question arises: Can I be sure that I won't damage or over-write my Vista installation/existing files? I'll be able to choose which OS to boot to every time I start up my computer? I know it's a simple question and I'm pretty sure the answer is yes, but I just need some words of comforting reassurance!

My second question pertains to display drivers. I've obviously got the latest nVidia display drivers installed on my system for Windows, but will I have to download and install display drivers for Linux, too? If I do, I'm guessing they won't interfere with my existing Windows drivers?

I know these are really basic questions that are asked a hundred times, but venturing out into a new OS is something I look upon with both excitement and trepidation. I obviously poked around the documentation and this forum first, however couldn't see a definite answer to my display driver question, and the dual boot tutorials I've read/watched either start with a totally blank drive, or involve only one physical HDD (I'm going to end up with 4 partitions over 2 HDDs.. Possibly 5 if I need a swap drive?)The last thing I want to do is mess up my system.

Many thanks!

Ex.

---

### Post by dyous87 on 2008-04-24
I have myself dual booted Ubuntu and other distros with Windows (all current versions) on numerous occasions and it has been successful every time so I don't see why you should have any problem, especially if the drive is already partitioned and all you have to do is point Ubuntu to install there. 

All should go smooth, worry not :). (*Just to be safe, it doesn't hurt to back up your files. You should try to always do this regularly.)*

After Ubuntu installs, it will automatically configure your boot manager to give you an option as to which OS you want to start up in whenever you boot your computer.

As for your nvidia drivers, depending on your card, if Ubuntu does not auto detect them with the restricted driver manager, you will have to download them from Nvidia's site. 

To answer your question, no these will not interfere with the Windows drivers in anyway. Once you get Ubuntu installed you can post back here and I can help you getting that done. 

If you have any questions feel free to ask away. I will be more then willing to help. Good Luck! I hope you enjoy Ubuntu!

---

### Post by starcannon on 2008-04-24
Use the wubi installer that comes with Ubuntu 8.04 or download Wubi from:
[http://wubi-installer.org/](http://wubi-installer.org/)
This little gem lets you install from windows, dual boot, and if for some reason you don't like it, you just uninstall it from windows using the windows software manager. Works great, and lets you try Linux without the big commitment.

---

### Post by moinster on 2008-04-24
Make sure you DEFRAG the HDD you are going to shrink.

---

### Post by Extraneous on 2008-04-24
Ooh, this Wubi thing looks interesting. I shall check it out. Stupid question but: it does work, doesn't it? Edit: Looking at it it suggests that I won't even need to bother partitioning my hard drive. Is this correct? Will I still get full Ubuntu functionality and the option to boot into either OS at startup?

And OK, I thought Dual-booting should be fine but when your precious files are at stake, not to mention the threat of an hour or two of troubleshooting or having to reinstall Windows, I like to be certain!

And OK, I was a little confused as to whether I needed Linux and Windows drivers. Thanks for clearing that up.

I expect I shall post again after I've installed Ubuntu (tomorrow, I'm going to bed now), probably with some more incredibly basic questions.

Thank you very much for your prompt and helpful replies :)!

---

### Post by elmer_42 on 2008-04-24
I dual-boot XP and Ubuntu, and know a guy who boots Ubuntu and Vista. You should be fine as long as you don't tell it to install to your Vista partition. Ubuntu doesn't automatically run in and try to take over your HD, it installs to the specified partition.

As far as the drivers, they will not interfere with each other. Drivers are linked more to the OS than the actual GPU. That is, they don't project themselves onto the GPU. I myself am running a 7600GT, and Restricted Drivers Manager found it right off the bat.

You will end up with five partitions, [1] Vista on HD1 [2] Storage on HD1 [3] Ubuntu main on HD2 [4] Ubuntu swap on HD2 (this should be twice the size of your RAM) and [5] Storage on HD2. If you are very paranoid about keeping Vista safe, you could unplug the HD inside your computer before you install and then plug it back in after the installation.

Good luck with Ubuntu! Don't be afraid to ask questions. There are so many helpful people here that helped (and continue to help) me get Ubuntu working on my computer. That, after all, is one of the biggest reasons Ubuntu is so popular.

---

### Post by Old_Grey_Wolf on 2008-04-24
Extraneous,
You may want to look at EasyBCD as well ([http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1))

---

### Post by Extraneous on 2008-04-24
EasyBCD looks interesting - Tweaky things fascinate me.

OK, I'll make sure to add a swap partition as well as one for Ubuntu. Should I do this through Vista or using the Ubuntu installer? Am I correct in thinking that the swap partition shouldn't be NTFS? And while I won't go so far as disconnecting my other hard drive, I'll be sure to back up files I'm worried about losing.

Thanks again!

---

### Post by grannyw on 2008-04-24
dont forget to backup

---

### Post by IHATEDLINK on 2008-04-24
Hey
I successfully dual-booted Ubuntu and xp and Ubuntu and vista
Don't be scared! everything goes smoothly and just like th tutorials :)
I don't recommend you to install Wubi, what if you want to completely switch to Ubuntu later? also, Ubuntu (or Kubuntu) doesn't run that well on Wubi.
And remember BACK UP! I don't care if you use an external drive, online storage or your iPod just make sure everything important on your computer is backed up!

Good luck!

---

### Post by elmer_42 on 2008-04-24
> **Extraneous said:**
> OK, I'll make sure to add a swap partition as well as one for Ubuntu. Should I do this through Vista or using the Ubuntu installer? Am I correct in thinking that the swap partition shouldn't be NTFS?
Personally, I used GParted to partition everything. I defragged my hard drive, then resized it. The unpartitioned space I then formatted into 30GiB of ext3 and 2GiB of swap. Swap partitions are actually a different file system, so you are correct in thinking that the swap partition shouldn't be NTFS.

---

### Post by dyous87 on 2008-04-24
For new users I'd also recommend WUBI. I have tried it myself and it works well. The great thing about it is you can easily "uninstall" ubuntu from withing windows if you want. And yes WUBI also allows you to pick your OS from a list at boot time.

David

---

### Post by Tetyl on 2008-04-24
I've got a 2 HDD system running with Vista and Ubuntu dual-booting. There are some tricky parts to it, especially because I was never able to figure out exactly how the HDDs were numbered by different parts of the system. Grub seems to use hd0 and hd1 where hd0 is the first drive in the boot order. Meanwhile Ubuntu itself uses sda and sdb which don't seem to be directly related to the boot order. Anyways I did eventually get it working, and I'm sure you will too. Backup beforehand and pay attention to what you are doing while performing the installation and you should be okay.

A couple things I think you are confused about:

After shrinking the partition on you second HDD with Vista, don't format it yet. The Ubuntu installer will prompt you to tell it where to format and install itself and you will point at that unformatted space.

The swap partition will not be NTFS, swap implies a special formatting type all its own.

Your Ubuntu partition won't be NTFS either. I don't know if that's even possible, but the much more common thing would be to use ext3.

You need to think about how you are going to handle booting. My recommendation would be to install Grub to your main Ubuntu partition, and use EasyBCD to add an entry to your Vista bootloader that points to this Grub installation. The Ubuntu installer does ask you where you want to install Grub, but in the 7.10 installer it was not very clear. There are multiple tutorials out there that cover this exact approach.

---

### Post by apostate on 2008-04-25
> **Tetyl said:**
> I've got a 2 HDD system running with Vista and Ubuntu dual-booting. There are some tricky parts to it, especially because I was never able to figure out exactly how the HDDs were numbered by different parts of the system. Grub seems to use hd0 and hd1 where hd0 is the first drive in the boot order. Meanwhile Ubuntu itself uses sda and sdb which don't seem to be directly related to the boot order. Anyways I did eventually get it working, and I'm sure you will too. Backup beforehand and pay attention to what you are doing while performing the installation and you should be okay.

A couple things I think you are confused about:

After shrinking the partition on you second HDD with Vista, don't format it yet. The Ubuntu installer will prompt you to tell it where to format and install itself and you will point at that unformatted space.

The swap partition will not be NTFS, swap implies a special formatting type all its own.

Your Ubuntu partition won't be NTFS either. I don't know if that's even possible, but the much more common thing would be to use ext3.

You need to think about how you are going to handle booting. My recommendation would be to install Grub to your main Ubuntu partition, and use EasyBCD to add an entry to your Vista bootloader that points to this Grub installation. The Ubuntu installer does ask you where you want to install Grub, but in the 7.10 installer it was not very clear. There are multiple tutorials out there that cover this exact approach.


For the reasons mentioned above, I wouldn't install Ubuntu on the second physical volume, but the first, right after Vista. I'd use yer big drive to back everything up to, and then use the portion of that first disk that is NOT allocated to Vista.

So, you have a 50 GiB Vista partition and presumably a 200 GiB partition of NTFS for storage? Pop in the Ubuntu disk, and boot her up. Click the Install icon. Elect to do manual partitioning and nuke the "storage" partition on the first drive, which should appear as sda or hda. MAKE SURE YOU GET THE STORAGE PARTITION and not Vista! 

Then, in the newly created vacancy, create a 10-20 GiB partition and format it as ext3. Mount it at   /

Then create a swap partition as stated above. Format as swap. It won't let you mount it anywhere, this is ok.

Create the remaining space as a partition in ext3. Mount it at   /home

For your convenience, you may wish to identify the Vista partition and mount it at  /windows  -This will create a folder in your root Linux filesystem called windows that is...you guessed it! your Vista hard-drive. So if you ever need to grab anything out of Windows while in Linux, you can just navigate to /windows and grab it. All this is done with a nice, easy to understand GUI with dropdowns and check boxes. Piece of proverbial cake.


...And let her rip.  It will be ok!

---

### Post by Extraneous on 2008-04-25
If you think installing Ubuntu on the small HDD would be simpler, I'll do that. How would I go about mounting the Vista partition at /windows? Part of the install process?

I'll probably keep some of the first hard drive as NTFS storage, some of it as ext3 storage, another partition for Ubuntu and a swap partition.. which makes 5 (including the Vista partition).. Huh.. is that OK?

If all this talk of my existing partitions and possible partitions is confusing anyone else (it is me xD), I'll try and simplify

**Current setup:**

HDD1:
- C:\ (Vista)
- D:\ (Documents)
HDD2:
- E:\ (Programs)


**Proposed setup:**

HDD1:
- C:\ (Vista)
- D:\ (Documents)
- V:\ (/home)
- U:\ (Ubuntu/root)
- S:\ (swap)
HDD2
- E:\ (Programs)

Phew.

---

### Post by Paul133 on 2008-04-25
You can just create and resize partitions while installing Ubuntu. You don't necessarily have to do that beforehand.

---

### Post by nero22 on 2008-04-25
> **Extraneous said:**
> EasyBCD looks interesting - Tweaky things fascinate me.

I don't think you'll need it for dual booting, I use it to triple boot XP, Vista and Ubuntu though, and it works fantastic.
Also I'd recommend that you make two linux partitions, one for your system and one for your home folder. This way you won't lose all your preferences when you reinstall.

---

### Post by Extraneous on 2008-04-25
> **nero22 said:**
> I don't think you'll need it for dual booting, I use it to triple boot XP, Vista and Ubuntu though, and it works fantastic.
Also I'd recommend that you make two linux partitions, one for your system and one for your home folder. This way you won't lose all your preferences when you reinstall.
'Tis what I'm planning on :).

---

### Post by apostate on 2008-04-25
> **Extraneous said:**
> If you think installing Ubuntu on the small HDD would be simpler, I'll do that. How would I go about mounting the Vista partition at /windows? Part of the install process?

I'll probably keep some of the first hard drive as NTFS storage, some of it as ext3 storage, another partition for Ubuntu and a swap partition.. which makes 5 (including the Vista partition).. Huh.. is that OK?

If all this talk of my existing partitions and possible partitions is confusing anyone else (it is me xD), I'll try and simplify

**Current setup:**

HDD1:
- C:\ (Vista)
- D:\ (Documents)
HDD2:
- E:\ (Programs)


**Proposed setup:**

HDD1:
- C:\ (Vista)
- D:\ (Documents)
- V:\ (/home)
- U:\ (Ubuntu/root)
- S:\ (swap)
HDD2
- E:\ (Programs)

Phew.


Well,

Personally, I think  your first time out this may be a bit overkill. The purpose of your home is largely to store documents and such, so you may be making things hard on yourself and introducing room for error by chopping your HD into itty bitty pieces. Your proposed D: drive sounds a bit unnecessary.

The proposal I gave you has your / and /home on different logical drives, so that should be fine.  To mount windows under Linux, do this as part of the install.  While you are creating and editing partitions, it will show you the Windows one. Click "Edit Partition", and then in the drop-down for mount-point, select /windows.

Done.

:-)

---

