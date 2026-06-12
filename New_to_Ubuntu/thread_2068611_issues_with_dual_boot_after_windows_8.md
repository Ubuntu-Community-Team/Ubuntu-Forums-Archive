---
title: "issues with dual boot after windows 8"
date: 2012-10-09
forum: New to Ubuntu
---

### Post by rochford77 on 2012-10-09
back story:
-im using windows 7 right now, and wish to Dual Boot with Ubuntu
-ive used ubuntu before through WUBI. but its off the machine as of now 
- i have a live/install cd with ubuntu on it that i just made
-i had a dual boot of windows 8 and windows 7, windows 8 is now gone, as well as the partition for it
-ive been on irc, they were not 100% sure how to resolve my issue

after taking windows 8 off my machine and now ONLY running windows 7, i put the ubuntu disk in, and i get the following options "install ubuntu alongside of _windows 8_, replace _windows 8_, advanced options" we think its just a boot issue, but my question is this: if i choose "install alongside of windows 8, will i loose my current/only OS (windows 7) or is grub just calling windows 7, windows 8? 

i DO NOT want to loose my windows 7 OS and Data :-)

---

### Post by audiomick on 2012-10-09
Ok, I'm guessing a bit, but I have seen several times where the Ubuntu side of things incorrectly identifies a windows install. On this machine, for instance, grub thinks that my Vista install is a windows recovery. I strongly suspect that what it is seeing as windows 8 is in fact your win7 installation.

What I would do is to boot into the live environment from the CD and use the partitioning program gparted to have a good look at your drive. You could even post a screen shot here so that people can have a look at it and offer their advice. 

If you can boot into win7, and can only see one windows partition in gparted, then it is a pretty sure thing the the installer is just identifying it wrongly.

I probably don't need to tell you that it is a good idea to back up anything really important before you do your install. That is a good idea in any case, but in your situation even more so.

---

### Post by rochford77 on 2012-10-09
"If you can boot into win7, and can only see one windows partition in gparted, then it is a pretty sure thing the the installer is just identifying it wrongly."
 
assuming you are correct, i will be fine with the "boot alongside windows" yes?
 
and im guessing "gparted" is in software center?

---

### Post by Mark Phelps on 2012-10-09
> **rochford77 said:**
> "If you can boot into win7, and can only see one windows partition in gparted, then it is a pretty sure thing the the installer is just identifying it wrongly."
 
assuming you are correct, i will be fine with the "boot alongside windows" yes?

NO -- not if you (1) do not have some unallocated space on the drive in which to create partitions for Ubuntu or (2) use the Ubuntu installer to shrink the Win7 OS partition to make room.

Shrinking using the installer can result in filesystem corruption in Win7, which can then render Win7 unbootable.

So, BEFORE you attempt that, if you don't have some unallocated space, shrink the Win7 OS only using the Win7 Disk Management utility.

Then, use the Win7 Backup feature to create and burn a Win7 Repair CD (if you don't already have one).  This will provide you the tool needed to repair/restore the Win7 boot loader, should it become corrupted later due to your Ubuntu install.
 
>  and im guessing "gparted" is in software center?
Yes ... but ... you can't use GParted on a partition that is currently being used -- which is the case when you're running Ubuntu off your hard disk.  IF you want to make changes to partitions that Ubuntu uses, you need to boot from a LiveCD or LiveUSB and run Gparted from there.

---

### Post by audiomick on 2012-10-09
> **rochford77 said:**
> assuming you are correct, i will be fine with the "boot alongside windows" yes?

Yes, if I am right, you can safely "install alongside", but do have a look for yourself

 > 
and im guessing "gparted" is in software center?

gparted is in the software center, and you can install it once you have Ubuntu installed.

In the Live environment, i.e. when you boot from the CD into the "try without installing" option, it is already installed by default.

---

### Post by oldfred on 2012-10-09
When you dual boot Windows the second install overwrites the boot files of the first. Only the partition with the boot flag has the Windows boot files & BCD. 
So it probably is correctly identified, its just the Windows 8 boot files are still in your Windows 7.

Vista & XP but still the same:
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by NikTh on 2012-10-09
> **oldfred said:**
> 

Vista & XP but still the same:
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

This definitely needs to be read. 

Thanks oldfred

---

### Post by audiomick on 2012-10-09
I have yet to see a post from oldfred that is not worth taking note of. ;)

Too late at night now, but I will look at it tomorrow. Thanks for that. I have been wondering why it turns up strange in the grub menu. The one on my netbook is wrong too.

---

### Post by audiomick on 2012-10-09
> **Mark Phelps said:**
> NO -- not if you 

I've been away for a bit, so I didn't notice that Mark had posted at the same time I was posting. What he says is true. Use the Windows tool to shrink your windows partition.

---

### Post by rochford77 on 2012-10-09
> **Mark Phelps said:**
> NO -- not if you (1) do not have some unallocated space on the drive in which to create partitions for Ubuntu or (2) use the Ubuntu installer to shrink the Win7 OS partition to make room.
 
Shrinking using the installer can result in filesystem corruption in Win7, which can then render Win7 unbootable.
 
So, BEFORE you attempt that, if you don't have some unallocated space, shrink the Win7 OS only using the Win7 Disk Management utility.
 
Then, use the Win7 Backup feature to create and burn a Win7 Repair CD (if you don't already have one). This will provide you the tool needed to repair/restore the Win7 boot loader, should it become corrupted later due to your Ubuntu install.
 
 Yes ... but ... you can't use GParted on a partition that is currently being used -- which is the case when you're running Ubuntu off your hard disk. IF you want to make changes to partitions that Ubuntu uses, you need to boot from a LiveCD or LiveUSB and run Gparted from there.
 
so what your saying is yes, but not without risk.
 
my original intent was to create a new partition using windows disk utility. i put in my ubuntu install disk and chose "advanced/other options" then i saw the 70Gb partition i made for ubuntu, selected it, hit "install now" and it gave me a (and im going off memory here) "no root system dected" or something along those lines. after looking further into it, it looked like i had to set up 3 or more disk partitions all formatted difffrently to install ubuntu. so i gave up and expanded driveC (windows 7) to swallow the partition i made for ununtu and then the OP issue began. 
 
i would not mind setting this all up manually using windows disk utility, but how many partitons do i need and about what size. i plan to use about 80GB total for ubuntu.
 
so how many new partitions do i need to make using windows disk managment, how big should i make each one, (out of my 80GB im allocating for ubuntu).
 
once i have the partitions made should i format them at all in windows disk managment or do that in the ubuntu installer? and how do i format them?
 
if someone could walk me through manually setting this up id rather just do that :-)

---

### Post by audiomick on 2012-10-09
OK, so you look like you are not to fazed by the concept of messing around with partitions. Here is what I would do.

Use the windows tool to shrink down the windows partition to what ever size you want to have. I believe it is then a good idea to start windows a couple of times to let it decide it is happy and to run ckdisk if it wants to, and that de-fragmenting before you start is to be recommended.

I would leave the rest of the space empty. The windows tool can't format the free space into the type of file system you need for a linux install

Start the installer and choose the option "something else" (at least I think that is what it is called. The one that lets you do the partitioning manually.)

I like to make a separate partition for my /home folder. Doing that allows you to simply re-mount that partition if you need to do a fresh install for any reason. That is where your data and your config files are stored. Being able to re-mount that has saved me some bother a few times.

So, make an extended partition using up all of the free space. Linux can be installed in a logical partition without a problem. (I hope no-one comes along and contradicts me on that...)

Inside that, make a partition of around 15GB and choose / as the mount point. This is the partition that the system goes in to. You can give it a bit more space if you have plenty of room on your drive, but, say, 50GB would be overdoing it. You can see from the attached screenshot that the /partition on this machine is just under 12GB and only has a bit less than 4GB in it.

With the rest of the space, you need to make a swap partition and one for /home. I always put the swap at the end so that I don't have to move it if I want to change the partition set up at a later date, but that is just me. 

If you want your standby function to work, you should give the swap partition a little more that you have RAM. When the computer goes to standy, the contents of RAM are written into the swap space. If you never use standby, about a GB of swap should be more than enough unless you do things like really intensive video editing, or having hundreds of photos open at once. 

The rest of the space becomes one partition that is mounted at /home.

I hope that is clear enough. If it seems confusing, go into the installer and have a look at it. The installer doesn't do anything permanent without telling you it is about to do that. You do have a chance to bail out if it all gets too confusing. Just look carefully at what you are seeing on the screen.

Doing a backup of anything important in the windows install is a very good idea before you start doing any of this stuff. The installer is quite ok, but you never know. A power failure, for instance, half way through the process could be bad news.

---

### Post by rochford77 on 2012-10-09
Great!

Now where does my saved data go? Lol. Does that run out of the system drive or the home drive. Or should I just make a drive just for data...? Like what will show up as my"c drive(equivalent)" by default?

---

### Post by rochford77 on 2012-10-09
thought i had it all figured out. created an 80Gb partition for ubuntu. ran defrag. booted up a few times. then changes BIOS to boot to CD drive. put in install disk. chose "do something else". i tried to format the whole block as an "extended drive" but did not see the option so i left it as "free space" i clicked on "free space" hit "add" made a partition at the end, for the swap for 4Gb (how much ram i have). then clicked on "free space" again and hit "add" and made a partition that was ext4 for 15gb with / as the mount point. then i used the remainder of space to make another partition as /home also as ext4. then i hit "install" and everything ran smooth!

it said "needs to reboot to complete install" so i did, my CD drive opened up. i took the disc out and hit "enter" 

then it booted to windows.... never got an option to boot to ubuntu. WTF?

---

### Post by oldfred on 2012-10-09
With manual partitioning, there is a combo box at the bottom of the partition screen that says where to install the grub2 boot loader. It needs to go into sda the drive not a partition like sda5, but may default to something else.

You can fix it by booting into your install CD or USB in the live mode and install Boot-Repair.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Herman's example of the install grub2 boot loader combo box shows many drives & partitions.
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)
Herman has lots of detail but has changed to using the alternative installer which is text based. Still lots of good info.
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by rochford77 on 2012-10-10
ok thanks. i did put the bootloader in the wrong place, i told it to boot from whatever partition i made "system" / so that would make since. however i still think im having an issue. i cant make the unallocated space an "extnded drive." through wither windows disk management OR the Ubuntu live CD. my drive tree looks something like 
...
-sda
...sda1 ntfs..windows system.................508GB
...sda2 ntfs..windows 8 boot.................100MB
...sda3 nfts..system recovery (windows 8 )...16GB
...sda4 ext4../home..........................61GB 
...sda5 ext5../..............................15GB
...sda6 swap-space...........................4GB

when i think it should be looking something like this

-sda
...sda1    ntfs windows system.................508GB
...sda2    ntfs windows 8 boot.................100MB
...sda3    nfts system recovery (windows 8 )...16GB
...[COLOR="Red"]sda7 extended[/COLOR]
......sda4 ext4 /home..........................61GB
......sda5 ext5 /..............................15GB
......sda6 swap - space........................4GB

im not sure how to make an extended drive...its not an option that i can see anywhere. even in WDM all i can do with the unallocated space is "make a new simple drive" 

so i booted back to windows, deleted the 3 partitons that ubuntu made. so it is back to 80GB of unallocated space. 

can i just go back and make the first tree again with the bootloader on sda (rather then sdaX like i mistakenly did earlier) and have it work. or is the extended drive a necessary component. 

thank you all for the help :-)

---

### Post by oldfred on 2012-10-10
Post link to BootInfo report:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by rochford77 on 2012-10-10
Hmm, not sure that helps me, at least not yet. My main issue is not being able to make my unallocated space an extended drive. Once I figure that out I should be good to go.

---

### Post by audiomick on 2012-10-10
> **rochford77 said:**
> im not sure how to make an extended drive...its not an option that i can see anywhere. 

You mean "extended partition" rather than "extended drive".... ;)

In gparted, click on the empty space to select it.
Go to the menu "partition" and select "new".
You should then have a window like the one in the attached screen shot and be able to select the type in the drop down menu that my mouse is pointing at.

Just to avoid confusion, the bit of my drive that I am pointing at is a tiny bit of leftover space, hence the small numbers. The options "logische", i.e. logical, and "erweitert", i.e. extended, are greyed out because I already have an extended partition on that drive, and I believe you can only have one per drive. Not a problem, as you can put more logical partitions in there than any normal person is likely to need.

A word to the numbering of the partitions: sda1, sda2, sda3 and sda4 are numbers that are always primary or extended partitions. When you start putting logical partitions into the extended, the numbers will start with sda5 even if you only have sda1 as an extended partition on there up to that point, as you can see in the second attached screen shot. A very common thing you see is sda1 as a windows partition and then sda2 as an extended with several logical partitions in it.

What you were expecting, this
> -sda
...sda1 ntfs windows system.................508GB
...sda2 ntfs windows 8 boot.................100MB
...sda3 nfts system recovery (windows 8 )...16GB
...sda7 extended
......sda4 ext4 /home..........................61GB
......sda5 ext5 /..............................15GB
......sda6 swap - space........................4GB

is close, but it would have to be

> -sda
...sda1 ntfs windows system.................508GB
...sda2 ntfs windows 8 boot.................100MB
...sda3 nfts system recovery (windows 8 )...16GB
...sda[COLOR="Red"][SIZE="2"]4[/SIZE][/COLOR]extended
......sda5 ext4 /home..........................61GB
......sda6 ext5 /..............................15GB
......sda7 swap - space........................4GB

Also, I thought that the windows boot partition is always at the start, but that is immaterial to the questions at hand.

---

### Post by rochford77 on 2012-10-10
thanks ill go in there and take a gander at it this evening after work. around 8pm eastern time. (about 9 hours from now). ill post my results!

---

### Post by audiomick on 2012-10-10
Something occured to me just now. If the system is using UEFI, I think the restriction of 4 primary partitions no longer applies. 

[http://en.wikipedia.org/wiki/Uefi]("http://en.wikipedia.org/wiki/Uefi")

Unfortunately I have no idea how many machines are out there that are using that rather than the classic BIOS and an MBR partition table, nor do I know how to check on that. If the machine is a bit older, I don't think this is likely, but if it is only a year or two old, I believe it is a possibility.

---

### Post by oldfred on 2012-10-10
It is why I wanted to see BootInfo or run of bootscript. That will tell what is where and documents systems.

This will quickly tell if drive is MBR(msdos) or gpt(GUID).

sudo parted /dev/sdb unit s print

I am using gpt but not UEFI, so one of my gpt looks like this:

```
fred@fred-Precise:~$ sudo parted /dev/sdb unit s print
[sudo] password for fred: 
Model: ATA MAXTOR STM316081 (scsi)
Disk /dev/sdb: 312581808s
Sector size (logical/physical): 512B/512B
Partition Table: [COLOR=Red]gpt[/COLOR]

Number  Start      End         Size        File system     Name      Flags
 1      34s        16064s      16031s
 2      16065s     51215219s   51199155s   ext4            MAVERICK
 3      51215220s  57352049s   6136830s    linux-swap(v1)
 4      57352050s  312576704s  255224655s  ext4

```

---

### Post by rochford77 on 2012-10-10
all good. my problem was i was trying to make my partitions in the ubuntu installer. what i had to do was

-go into windows and using WDM shring my main drive by 80 Gb. 
-put in ubuntu CD and choose "try linux"
-press super key or "windows button" and type "gparted"
-open gparted and make 3 ext4 partitions (the "unallocated space) automatally shows up as "extended"
...-ext4 partiitons 
......-one 15gb labled "/"
......-one 4 gb labled "swap"
......-the remainder labled "/home"
-they went in the order of: /home, / , swap
-closed gparted
-clicked desktop item "install ubuntu 12.04
-chose install ubuntu
-chose "do soething else" "3rd  option"
-format the 4gb swap drive as the swap.
-format the 15gb / drive as ext 4, /
-format the rest as ext 4 /home

in the bottom drop down choose "install on sda" (should be default)

hit install.

/thread :-)

docs attached

---

### Post by audiomick on 2012-10-12
Well done! :popcorn:

---

### Post by jamvaru on 2012-10-20
just a pointer:

if you ever delete your windows boot partition (the 100mb) you will lose your extended partitions

the best bet is to reinstall windows and specify a certain size, like 200gb or so for your windows partition, leaving the rest of the space unformatted

later, when you want to install linux you can format the remaining space as primary partitions; then when you decide to delete windows, someday, you will not lose your other partitions as well

this happened to me personally, no bs ;]

i gave up on windows 7 (and 8, 9, 10, etc.), though I do run xp for now, till I can get a grip on wine goblin

anybody else have problems with deleting windows boot partition?

---

