---
title: "Driver Problems in HP pavillion zd8000 (ubuntu/kubunto)"
date: 2011-11-26
forum: New to Ubuntu
---

### Post by Flame57 on 2011-11-26
Good Evening.
I have a HP pavillion zd8000 and several problems with ubuntu/kubuntu. Probably it is a driver issue...

Firstly, i have Win7 on it. I also have Virtual box with Ubuntu on it, with zero problems.


What happens is, I have tried installing Ubuntu and Kubuntu via wubi (with the --32 command so it downloads the x86version) but i have several issues with either of them:

*My USB mouse (NGS brand) is identified in linux boot, since the optical light is on. However:
--Moving the USB mouse normally moves it very slowly in the screen.
--The touchpad moves normaly.

*Any USB Pen/Disk is identified in linux boot, because the light turns on and stays on.
--Can't find the device in the File Manager

*On boot, Linux identifies and sees if i have an Ethernet cable connected, however:
--Is unable to configure it. Even if i go to windows7, copy the IP/DNS/DHCP values and copy them over or change connection type.
--Can't connect to the Internet.

*If i remove any of the previous devices (the USB mouse, USB pen or ethernet cable) and insert again, nothing happens, lights don't turn on, etc....


I would like to know if anyone knows a solution, i would like to try kubuntu or ubuntu (preferably KUBUNTU) mainly because I need it for classes, but tried to search anything related in these forums but didn't succeed.
I found this thread ( [COLOR=#000000][FONT=Segoe UI]http://ubuntuforums.org/showthread.php?t=1439234 ) but since i cant "[/FONT][/COLOR]hardwire a network connection", I'm pretty much stuck.

Thank you for your time.

---

### Post by BC59 on 2011-11-26
Well it's Wubi and it's not the perfect installation.

Why don't you try an Ubuntu Live CD, to see if using the system normally and not through Windows, it's working better?

---

### Post by Paddy Landau on 2011-11-26
May I ask why you have decided to force 32-bit?

If you are looking at using Ubuntu (or Kubuntu) long-term, I would suggest you do not use WUBI. WUBI is useful for short-term experimentation but not long-term use.

The fact that it works in VB but not in WUBI reinforces the idea that perhaps you need a full installation.

If Ubuntu in VB works fine for you, of course you can just keep that. But if you want a native installation (perhaps for speed or higher reliability), you want to avoid WUBI.

Create a Live CD or (preferably) a Live USB of Kubuntu. I'd use 64-bit if your computer has at least 2Gb RAM and, of course, a 64-bit processor. Boot from the CD or USB and choose the option to try it out (this option will not affect your computer). If it seems to work fine, go for a full installation.

Before doing a full installation:

[LIST=1]
[*]Back up your data. Even though the installation process has been thoroughly tested and refined over the years, there is always a small chance of data loss.
[*]In Windows 7, go to Computer Management (in your Administration Tools) > Disk Management (I think that's what it's called). Shrink your Windows partition. *If you need help, please post back with a screen shot so that we can help you*.
[*]Reboot Windows (it seems to need a reboot after shrinking partitions).
[*]Boot from the USB and install Kubuntu into the freed space. *If you need help, please post back so we can help you*.
[/LIST]

---

### Post by Flame57 on 2011-11-26
I didn't know there was much difference between Windows install and Live CD.
Since it was installed in Windows through wubi, I actually thought that it could download any driver it needed...

I forced wubi to download the x86 because the first time i ran it, it installed the amd64 version, and i found it too "slow", now that i think about it (as "slow" being... the slow mouse bug i said last post xD).


I will try installing Kubuntu x64 via USB. Will first check any guides that can help me, since I've only managed to sucessfully install it once (about four years ago...)

Thank you both, will get back to you tomorrow.

---

### Post by BC59 on 2011-11-26
> **Flame57 said:**
> 
I will try installing Kubuntu x64 via USB. Will first check any guides that can help me, since I've only managed to sucessfully install it once (about four years ago...)

Thank you both, will get back to you tomorrow.

A suggestion

Before starting to touch your Windows partitions to make space for Ubuntu, just post to the forum a snapshot of your partition system, to suggest you, the best way to do it. It's easy, but sometimes gets tricky.

---

### Post by Flame57 on 2011-11-26
Thanks, here it is:

[http://img443.imageshack.us/img443/883/sem1z.png](http://img443.imageshack.us/img443/883/sem1z.png)


The language is Portuguese, any doubt just ask me and I'll translate.

I'd prefer to take 10GBs off E: (in order to install), since I can make backups to external HDDs.


EDIT: The processor is 64bi capable ;)

---

### Post by BC59 on 2011-11-27
Well, as I said is not that easy.

You have little space to install Ubuntu alongside Windows. You can leave 10 G  from your hard drive but I'm not sure if windows will leave you to free them all. For Ubuntu you need at least 5-6G for the system, some G for the swap file (normally you need the double of your RAM eg 2G RAM= 4G swap) and finally you need space for your storage. Closing to the limit of space.

I don't know if it's possible to do it.

So I suggest you to open a new thread to ask this question, to attract more members with more ideas about this.

---

### Post by Paddy Landau on 2011-11-27
> **Flame57 said:**
> I didn't know there was much difference between Windows install and Live CD.
Yes, a huge difference. One is installed inside Windows as an ordinary program (although it's not an ordinary program); the other is installed as a separate OS, just as (say) OSX or Windows 7 might be. WUBI is slower than a native installation, though not much, and has certain limitations that the native installation does not.

> **Flame57 said:**
>  Since it was installed in Windows through wubi, I actually thought that it could download any driver it needed...
It should, though it would have nothing to do with Windows. But it didn't -- I cannot comment why.

> **Flame57 said:**
> I will try installing Kubuntu x64 via USB.
I suggest that you first uninstall WUBI (but back up any data first!).

> **Flame57 said:**
> I'd prefer to take 10GBs off E: (in order to install), since I can make backups to external HDDs.
BC59's suggestion was a good one. However, you said you'd prefer to take 10Gb off E. According to your screen shot, you have three partitions, none of which is E. ;)

Your partitions are as follows:

[LIST=1]
[*]100Mb: System reserved (probably Windows recovery). Don't touch this partition if you wish to keep Windows.
[*]C: 40Gb: This is your Windows 7 system.
[*]F: 53Gb: This, presumably, is your data partition.
[/LIST]
Incidentally, these partitions will have different names in Linux. In order, they would most likely be called /dev/sda1, /dev/sda2 and /dev/sda3.

They are all *primary* partitions. A hard drive (for historical reasons) can have no more than four partitions. However, there is something called an *extended* partition. An extended partition can have many *logical* partitions, which allows you to have more than four partitions in total.

May I suggest that you shrink your F: drive by 12Gb. Then, when you install Ubuntu, partition the free space as follows.

[LIST]
[*]The entire 22Gb: A single *extended* partition.
[/LIST]
Within that extended partition, create the following *logical* partitions:

[LIST]
[*]10Gb: Your Kubuntu installation. This will hold your root (i.e. "/") folder. Format as ext4.
[*]10Gb: Your /home folder. Format as ext4.
[*]2Gb: Your swap space.
[/LIST]
You can do this partitioning at the time you install; choose manual partitioning when prompted.

When you install, ensure that you are connected to the Internet. The installation will automatically download any relevant drivers that are required but are not on the installation disk.

More information:

[LIST]
[*]The sizes I have suggested are, well, only suggestions. However, they are based on experience. The good news is that doing it the way I suggested will allow you to change your mind later, further shrinking F: and expanding the extended and logical partitions (specifically your /home partition).
[/LIST]

[LIST]
[*]Your swap space must be equal to your RAM, or greater, if you want to be able to hibernate Kubuntu. If you make your RAM smaller, you will not be able to hibernate. Having said that, if you choose to encrypt your home folder, you will not be able to hibernate anyway, because your swap space will also be encrypted.
[/LIST]

[LIST]
[*]The extended partition will be called /dev/sda4. The logical  partitions will be called (in the order you create them) /dev/sda5,  /dev/sda6 and /dev/sda7. You do not have to create the logical partitions in the order that I suggest; any order will be fine.
[/LIST]

[LIST]
[*]You will be able to read and write to your Windows folders from Kubuntu, but you cannot see your Kubuntu folders from Windows.
[/LIST]

[LIST]
[*]The purpose of splitting your root and /home into separate partitions is that if you really mess up your Kubuntu installation and need to reinstall, or you want to change (say) to Ubuntu, Xubuntu or even Mint, you can just (re)install without overwriting your /home. It makes it easier.
[/LIST]
If you hit errors or confusion, as BC59 says, just start a new thread. Post the thread link here so that we can find it.

> **BC59 said:**
> ... normally you need the double of your RAM eg 2G RAM= 4G swap...
On modern machines, that is no longer recommended. You are unlikely to need more than 4Gb swap, unless (as mentioned) you have more than 4Gb RAM, want to hibernate, and your /home folder is not encrypted.

---

### Post by BC59 on 2011-11-27
> **Paddy Landau said:**
> 
On modern machines, that is no longer recommended. You are unlikely to need more than 4Gb swap, unless (as mentioned) you have more than 4Gb RAM, want to hibernate, and your /home folder is not encrypted.

You have right, I stuck to the good old method.

> How much swap do I need?
As a base minimum, it's highly recommended that the swap space should be equal to the amount of physical memory (RAM). Also, it's recommended that the swap space is twice the amount of physical memory (RAM) depending upon the amount of hard disk space available for the system (although this "recommendation" dates back from a time when physical RAM was very expensive and most Unix systems ran with many processes in swap space - a situation that hardly applies in most situations these days, but ancient Unix/Linux myths like this "recommendation" tend to survive well past their "use by" dates). In reality, if you use hibernation you need what was outlined in the relevant paragraph above, otherwise you need as much swap space as your system will use - which actually may be very little in a modern hardware setup. The only downside to having more swap space than you will actually use is the disk space you will be reserving for it.

---

### Post by Paddy Landau on 2011-11-27
Oh, and I forgot to add:


[LIST]
[*]Back up all data before starting your partition shrinking. Although partition shrinking is reliable and well-tested, there is always a small chance of data loss.
[*]After shrinking your F: drive, reboot Windows even if it does not ask you to do so.
[*]Back up all data before starting your installation. Although the installation process is reliable and well-tested, there is always a small chance of data loss.
[/LIST]

---

### Post by Flame57 on 2011-11-27
I just installed Kubuntu, with the DVD, since i couldn't find the "USB" option in BIOS or boot menu.
I installed with 10GB root Ext4, 6GB /home Ext4 and 2GB swap file.

The only problem i had was when I actually tried to create an extended partition, i could only find "Primary" and "Logical".
Ended up with just creating the three partitions with the "logical" option, and they got the partition names you said above, Paddy Landau (sda5, sda6, sda7)

It works 100%: mouse, ethernet, sound and even USB flash drives. I didn't backup any data, since everything i had could be easily downloaded again. Even the whole Linux Partition Manager (can I call it that?) is intuitive and easy to work with (I'm not a newbie in formatting, installing, partitioning etc, just in Linux  ^_^).


One last question:

I only plan to use Kubuntu sporadicly, for college use only, to program in C or something like that.
Keeping that in mind, what is the recommended space for the partitions if I need/decide to reinstall Kubuntu?
It is currently at (used/total):
0.2 / 6.7GB (/home)
3.5 / 9.5GB (/root)
e.g, I'd prefer to take some GBs from /home and use it on Win7 instead, since my HDD is kinda small. How many GB is okay to take? 4GB? (I will only do that if i need/want to reinstall)


Thank you both for your help!

---

### Post by BC59 on 2011-11-27
> **Flame57 said:**
> 
One last question:

I only plan to use Kubuntu sporadicly, for college use only, to program in C or something like that.
Keeping that in mind, what is the recommended space for the partitions if I need/decide to reinstall Kubuntu?
It is currently at (used/total):
0.2 / 6.7GB (/home)
3.5 / 9.5GB (/root)
e.g, I'd prefer to take some GBs from /home and use it on Win7 instead, since my HDD is kinda small. How many GB is okay to take? 4GB? (I will only do that if i need/want to reinstall)


I personally don't use a lot of space on Home and have dedicated most of space in Windows part, for one simple reason. Windows doesn't recognize the Linux partitions, but Linux can communicate with the other part perfectly. In that case the data in windows part are accessible from both parts and you can store everything there. You only need 2-3GB of /home because Ubuntu is using the space to put some parts of programs.

---

### Post by Paddy Landau on 2011-11-28
> **Flame57 said:**
> I just installed Kubuntu, with the DVD... It works 100%...
I'm pleased it worked out OK.

> **Flame57 said:**
> The only problem i had was when I actually tried to create an extended partition, i could only find "Primary" and "Logical".
Well, somehow it all seems OK. You couldn't have created a logical partition unless within an extended, so I suppose that the Ubuntu installation must have handled that automatically for you.

> **Flame57 said:**
> Keeping that in mind, what is the recommended space for the partitions if I need/decide to reinstall Kubuntu?
As you can see, Linux doesn't take much space at all. Your root partition is recommeded to be about 10Gb. At 9.5Gb you are absolutely fine.

Your /home is only using 200Mb, so your current setting is, again, perfectly fine. Programs use your /home to save their settings (unlike Windows Registry, Linux has a clear separation of users, so each user has his own settings in his own /home), but those settings take little space. My guess matches BC59's -- around 3Gb.

---

