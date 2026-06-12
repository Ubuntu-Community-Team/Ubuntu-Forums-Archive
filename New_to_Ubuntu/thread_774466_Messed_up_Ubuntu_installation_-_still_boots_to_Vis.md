---
title: "Messed up Ubuntu installation - still boots to Vista"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by johnnyking on 2008-04-29
Hey

I'm new to Ubuntu... or at least I will be when I get it installed!

I ran the installation, with the intent to install it alongside my current Windows Vista install.

I used the manual partition maker.

Setup two partitions.

1 - Ext 3 - and just a slash /
2 - swapfile

Was one of these meant to be /boot?

What happend was once the installation was finished. The pc booted, said something had gone wrong, and asked if I want to boot to safe mode plus a few other options. or just boot to normal windows.

thanks if someone can help me rectify my mistake! i'd still like to get ubuntu installed

and yes im very embarrassed i messed up in the first place. because ive read everywhere its easy to install!

---

### Post by Nano Geek on 2008-04-29
The top option on that list should boot into Ubuntu.
If you don't click anything, it will select the top choice automatically.

Enjoy Ubuntu. :)

EDIT: I forget to tell you that you do not need to have a **/boot** partition unless you want to.

---

### Post by phr0ze on 2008-04-29
I wouldn't even do the manual partioning since you didn't really do anything the install would do for you. When you install you can just adjust the slider to decide how much room to give windows. Now that you have these partitions, you may as well use them. I'd reinstall if you are still having problems.

Also, it would help if you run the CD check before installing.

---

### Post by johnnyking on 2008-04-29
Now that I've booted to Vista and shut it down correctly...

The PC just boots straight to Windows.

So it looks like the boot loader hasn't been installed correctly. Any ideas how I can correct this?

---

### Post by phr0ze on 2008-04-29
Looks like a reinstall of Ubuntu. I wouldn't mess with trying to get Grub setup only to find out the install is bad.

Just run the CD check and install again.

---

### Post by johnnyking on 2008-04-29
> **phr0ze said:**
> I wouldn't even do the manual partioning since you didn't really do anything the install would do for you. When you install you can just adjust the slider to decide how much room to give windows. Now that you have these partitions, you may as well use them. I'd reinstall if you are still having problems.

Also, it would help if you run the CD check before installing.

I see what you mean. The issue was that my C drive with Vista on didn't have much spare room. I had a seperate partition that had spare space, and was scared to use the option called "use largest continuous space" in case it didn't use that space.

that said. according to the last poster i didn't mess up the partition bit.

i can reinstall. i'm just not sure what i can do differently this time.

at the end of the install there was an "advanced" tab that i looked at where i could specify where to install the boot loader. but i didn't modify this.

---

### Post by johnnyking on 2008-04-29
i did initially run the CD check. so that's definetly okay.

i'll try running the installation again =)

---

### Post by sailor2001 on 2008-04-29
download and keep a 'bootmagic' disk.

---

### Post by johnnyking on 2008-04-29
booted to the ubuntu disc. ran the install... again

still no luck

the grub bootloader isn't showing up when i boot

any tips for getting this sorted?

---

### Post by Sef on 2008-04-29
Could you explain exactly how you are manually partitioning?   I always do it, so I should be able to pick up any problems.

---

### Post by iSplicer on 2008-04-29
Are you planning to dual boot? If not, simply use one of the presets that are available to you... That should save confusion during install. All that is needed if you manually partition is a ext3 partition mounted at / and a swap partition. Install ubuntu, and it should work fine.

---

### Post by lwvmobile on 2008-04-29
Toward the end of the Ubuntu installation is there any error about Grub not being able to be installed on the MBR? If its going strait to Windows bootloader, then it sounds like Grub isn't installed at all. Either that or you have more than one hard drive.

Another tip most people mention is to use the disk management utility in Vista to resize the partition if you only have one partition taking up the entire hard drive. Some people state that Vista has problems when the partition is resized by other utilities.

---

### Post by iSplicer on 2008-04-29
This should not be a big issue at all. Make your patition table look like this:

-First partition: sda1 - NTFS - vista
-second partition: sda2 - ext3 - ubuntu
-third partition: sda3 - swap - ubuntu swap

Thats all you need, that should work. Install ubuntu onto the second partition, it should install GRUB and handle everything perfectly. If it doesnt, post here explaining your porblem exactly please.

---

### Post by johnnyking on 2008-04-29
> **Sef said:**
> Could you explain exactly how you are manually partitioning?   I always do it, so I should be able to pick up any problems.

Hi. Perhaps this screenshot will do better than an explanation.

[[IMG]http://i6.photobucket.com/albums/y226/the_aph/partitions1.jpg[/IMG]]("http://i6.photobucket.com/albums/y226/the_aph/Partitions2.jpg")

It shows the partition table at the moment.

I did manage to boot to the grub boot loader by using EasyBCD - to edit Vista's boot menu. Once I was into the Grub loader... I got no further.

When I clicked on Ubuntu there was an error message. I could perhaps get a shot of that if needed.

---

### Post by johnnyking on 2008-04-29
> **lwvmobile said:**
> Toward the end of the Ubuntu installation is there any error about Grub not being able to be installed on the MBR?

I don't think I got an error either times. Granted I wasn't looking at the install 100% of the way through. I was watching tv at the same time.

---

### Post by johnnyking on 2008-04-29
> **iSplicer said:**
> This should not be a big issue at all. Make your patition table look like this:

-First partition: sda1 - NTFS - vista
-second partition: sda2 - ext3 - ubuntu
-third partition: sda3 - swap - ubuntu swap

Thats all you need, that should work. Install ubuntu onto the second partition, it should install GRUB and handle everything perfectly. If it doesnt, post here explaining your porblem exactly please.

When I setup the partition table that's how it looks, except for the extra HDD's.

Perhaps they have something to do with the problems?

---

### Post by johnnyking on 2008-04-29
> **iSplicer said:**
> Are you planning to dual boot? If not, simply use one of the presets that are available to you... That should save confusion during install. All that is needed if you manually partition is a ext3 partition mounted at / and a swap partition. Install ubuntu, and it should work fine.
Yes I wanted to dual boot.

...yes that's how i partitioned it.

---

### Post by lwvmobile on 2008-04-29
I bet grub was installed on what Vista's disk management deemed Disk 0 and BIOS boots Disk 1 where Window's bootloader is, I am assuming since it contains the C: Drive. 

Try changing up the hard drive order in BIOS, you may also need to edit the boot list in Grub if you get a boot error(if you find grub, that is). I always have to when I install on multi hard drive systems.

---

### Post by johnnyking on 2008-04-29
> **lwvmobile said:**
> I bet grub was installed on what Vista's disk management deemed Disk 0 and BIOS boots Disk 1 where Window's bootloader is, I am assuming since it contains the C: Drive. 

Try changing up the hard drive order in BIOS, you may also need to edit the boot list in Grub if you get a boot error(if you find grub, that is). I always have to when I install on multi hard drive systems.

I see. So it's the multiple HDD's causing the problem.

I'm a bit tired tonight, so I'll leave it until tomorrow.

The hard bit (for me) will be editing the boot list in Grub. I'll look into that...

---

### Post by lwvmobile on 2008-04-29
It shouldn't be too big of an issue. _IF_ you have to edit it, you will just change the line

root (hd _0_,0)

to 1 or 2


For now, just work on changing the hard drive boot order in bios and try to find grub first, then you may have to change it back to get back to Vista if you get any further errors. But if you do get to grub and have boot up issues, you can use the e key on the keyboard to edit lines, just edit the above line, the first number which is underlined is the hard drive number, just try 0,1, or 2 and then hit the b button to boot it.

---

### Post by iSplicer on 2008-04-29
Your multiple hard drives complicates the situation a tiny bit. After windows is installed, reinstall ubuntu onto its own partition and then set the boot loader to install onto HD(1,0). The "1" on the front indicates the hard drive plugged into your motherboard, the second number specifies the partition. Note that this is zero-based so 0 is the first partition, and 1 is the second, etc. This is a different way to show rather that /dev/sda, /dev/sda1, /dev/sdb1, etc..

---

### Post by madjr on 2008-04-29
use wubi dude

[http://wubi-installer.org/](http://wubi-installer.org/)

[IMG]http://www.ubuntu.com/files/banners/wubi-123.jpg[/IMG]

it's just simple and no partition requiered (thats why ubuntu includes it) 

i can't believe the people here.... everyone is helpful and very friendly yes, but overwhelming new users with technical posts should be a no no...

but if u think you're prepare to partition yourself (u done it before) then go ahead :)

---

### Post by johnnyking on 2008-04-29
> **madjr said:**
> use wubi dude

[http://wubi-installer.org/](http://wubi-installer.org/)

[IMG]http://www.ubuntu.com/files/banners/wubi-123.jpg[/IMG]

it's just simple and no partition requiered (thats why ubuntu includes it) 

i can't believe the people here.... everyone is helpful and very friendly yes, but overwhelming new users with technical posts should be a no no...

but if u think you're prepare to partition yourself (u done it before) then go ahead :)

Okay but I actually tried that before... and got the same result. The issue was related to having multiple HDD's. It didn't matter which way I installed Ubuntu.

---

### Post by johnnyking on 2008-04-29
> **lwvmobile said:**
> It shouldn't be too big of an issue. _IF_ you have to edit it, you will just change the line

root (hd _0_,0)

to 1 or 2


For now, just work on changing the hard drive boot order in bios and try to find grub first, then you may have to change it back to get back to Vista if you get any further errors. But if you do get to grub and have boot up issues, you can use the e key on the keyboard to edit lines, just edit the above line, the first number which is underlined is the hard drive number, just try 0,1, or 2 and then hit the b button to boot it.

You were completely spot on about the hard drive boot order.

I didn't even think of it - because I assumed that if the boot order worked fine for Vista - it should work fine for Ubuntu.

Clearly not?!

Well I changed the boot order. First go didn't work - so changed it again and this time it worked. I didn't have to change the Grub menu... but thanks for the explanation about how to do that.

I'm typing from within Ubuntu now.

Thanks sir, really appreciate the help =)

---

### Post by lwvmobile on 2008-04-29
Cool, glad that worked for you. Also even happier you didn't have to change Grub. I always have to on ONE system of mine in particular, so I have the routine down by now.

---

### Post by kansasnoob on 2008-04-29
Hey, you're still bootable to Vista, that's great! You have not broken anything!

Take a breath and slow down, then read through these tuts:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Not that you'll particularly want to follow any of them to a "tee", but they give some real great perspective of how things work.

I followed APC's guides for my first few dual boots and they worked! Sort of :^/ (Just more fiddly than necessary.

Personally, the one puter I have with two hard drives still has XP and 8.04 sharing a drive and the other drive is for data stoarge, so in my scenario I'd want a GParted Live CD (you can use GParted from the Ubuntu live CD but it's slower and "fiddly-er" and I'd delete the faulty Ubuntu partitions (both main and swap) then I'd make sure that's just one blank area on the drive. (If Ubuntu and Windows are installed on different drives I've never done it, but I'm currently fiddling with running Ubuntu off an external hard drive ....... still fiddling!)

Then when installing Ubuntu 8.04 I'd just tick "use largest continuous free space". I'd personally want no less than 10 GB for Ubuntu, but the installer takes care of GRUB and the MBR and then when booting it will go to Ubuntu unless you press "esc" when the GRUB menu shows up on the screen. If you press "esc" then you can just "arrow" up or down to the OS you want to boot.

Time to walk the dogs!

---

### Post by kansasnoob on 2008-04-29
Oops, I was still typing while it was solved.

Just enjoy Ubuntu, I do!

---

