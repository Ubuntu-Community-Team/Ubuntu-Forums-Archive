---
title: "NFG with questions"
date: 2012-10-13
forum: New to Ubuntu
---

### Post by Bugscuffle on 2012-10-13
I am the newbie here and have not a clue as to how UBUNTU works. Not only that, but I am digitally challenged. Every time that I get a new cell phone, I have to find a ten year old girl to explain it to me. I am sick and tired of having to revert my computer to the "out of the box" state in order to clear the Trojan that some S.O.B. has slipped onto my computer. I bought a used UNBUNTU computer in the hopes of eliminating this irritation. Now what I want to do is load Windows XP onto one partition of my new (to me) 80 GB hard drive and UNBUNTU onto a second partition. This is strictly a home computer and ½ of the 80 GB hard drive will be plenty for my use. My problem is that I have no clue as to how to go about doing this. The computer will be arriving in about one week and it will have the UNBUNTU preloaded on it. I have the distributive disk for Windows XP, so how do I get them both onto the disk without loosing any of the programming that is already on there? Will partitioning the disk wipe any of the programming that is on it? How do I partition an UNBUNTU hard drive? Will I have to reformat the hard drive after I partition it?

---

### Post by nrundy on 2012-10-13
The easiest thing for you to do will probably be the following:

1. download an Ubuntu installation package from the Ubuntu website. For example, download Ubuntu 12.04 32 or 64 bit install package. Burn this to CD or place it on a USB for later use.

2. although your new computer will come with Ubuntu preinstalled, since you want to install WinXP on it, it will be easier for you to install WinXP from a retail CD of WinXP over your preinstalled Ubuntu installation. Windows XP does not place nice with other Operating Systems and it is much easier to just install XP as if it will be the only OS on the drive.

3. when XP is fully installed, use your CD or USB of Ubuntu to install Ubuntu alongside your WinXP installation. Excellent instruction for doing this can be found at the ubuntu website found here: [http://www.ubuntu.com/download/help/install-ubuntu-desktop](http://www.ubuntu.com/download/help/install-ubuntu-desktop).

Once ubuntu is installed, when you press power to boot you will be present with a boot menu which will allow you to boot into either WinXP or Ubuntu.

---

### Post by DuckHook on 2012-10-13
Welcome to the forums Bugscuffle (btw, love your moniker!--sounds like one of Harry Potter's professors).

I have introduced Linux to dozens of people migrating from Windows, but, until now, only when they were physically present. It is always gratifying to see a new user trying out our favourite OS.

Firstly, a direct answer to your immediate question, and then some comments about what I perceive as two larger issues:

Although the details are more complicated, I will try to summarize the situation simply in light of your self-described computer experience. Essentially, Windows does not play nice with other operating systems. If your computer is preloaded with Ubuntu, then loading Windows XP on it will wipe out your Ubuntu installation. However, if Windows is loaded first, and especially if you pre-configure your partitions to allow space for Ubuntu, then Ubuntu plays very nice with Windows. There is an option during the Ubuntu installation for you to install Ubuntu into a different partition. Moreover, the bootloader will allow you to choose which operating system you want to start each time you boot. But, as I have said, this requires you to load Windows first and Ubuntu afterwards.

There is a way for more advance users to load Windows after Ubuntu. But in my experience, the details are sufficiently complicated that it just confuses new users. Therefore, I suggest the following:

1. Ask the person you are buying the computer from to supply you with the Ubuntu CD. Alternately, you can download the Ubuntu install disk from Ubuntu's website.

2. When your computer arrives, install Windows XP. However, during the install process, when it asks you if you want to use the whole disk, answer "no". This will take you into a screen where you can shrink the partition for the XP installation down to 40Gb or about half the disk.

3. Complete the Windows install, fire it up and make sure that everything is running.

4. Boot up with your Ubuntu CD and install the Ubuntu OS. However *very important*, do not choose "use the whole disk". Instead choose "install along side other OS". Then choose "install on unused disk space". This will give you a working dual boot system. It's that simple.

I would also note that unless you are buying your used PC from a trusted source who knows what he/she is doing, it may very well come with a trojan of its own. I am probably being needlessly alarmist, but you are always better off installing OSes on your own from original sources (my philosophy anyway) on used PCs.

Now for the larger issues:

1. Your question has me asking: where are you posting from? Because if you already have a Windows PC, why do you want to bother with a dual boot system? I ask because I find that the single biggest headache for new users is system complexity. A dual boot system is not really that complicated, but if you can simplify it even further, then that is the way to go.

2. I encourage you to visit the following website:

[http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/](http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/)

A lot of Windows users come to Ubuntu with unrealistic expectations. Logically, they recognize that Linux is different from Windows, but in their heart of hearts, they think that they can just pick up where they left off. In short, they expect Ubuntu to be Windows, only better. I think that the biggest favour Linux enthusiasts like me can do for new users is to set up realistic expectations. And I believe that the whole psychocats website is a good place to start.

---

### Post by Bugscuffle on 2012-10-13
You said: &#8220;I would also note that unless you are buying your used PC from a trusted source who knows what he/she is doing, it may very well come with a trojan of its own. I am probably being needlessly alarmist, but you are always better off installing OSes on your own from original sources (my philosophy anyway) on used PCs.&#8221;

I see your point, but I trust Goodwill Industries implicitly. They rebuild and sell 100&#8217;s of computers every month. Those that they refurbish completely, like this one, they load with UNBUNTU. If you go to this URL: [http://www.shopgoodwill.com/[/COLOR]]("http://www.shopgoodwill.com/") you will find many very inexpensive but still very serviceable computers at bargain prices. You won&#8217;t run across any Cray supercomputers, but there are some good buys there.

You asked: &#8220;Your question has me asking: where are you posting from? Because if you already have a Windows PC, why do you want to bother with a dual boot system? I ask because I find that the single biggest headache for new users is system complexity. A dual boot system is not really that complicated, but if you can simplify it even further, then that is the way to go.&#8221;

This is going to be my home computer. I am freshly retired and I want to replace the laptop that I used in my work for a desk top, so the reason behind all of this is that I&#8217;m changing computers. I do want to have both systems available to me, but after reading what little bit that I have read, it seems that to make both systems available on one computer, I must either have two separate hard drives or partition my hard drive into at least two partitions. My only decision after that is whether to have the machine boot up to either the windows or the UNBUNTU automatically and then go trough some machinations to change the OS when I want to, or have it ask me at the start whether to boot to the Widows or the UNBUNTU. As I said I have only done some very preliminary research and so far it tells me that the later solution is the easier and better one, but please tell me if I&#8217;m all wet.

In that I already have the distribution disk for Windows and the UNBUNTU is free, I have no compunctions about wiping the UNBUNTU off of the new machine. I just need to now how to manipulate The UNBUNTU to arrive at the desired configuration.

---

### Post by DuckHook on 2012-10-14
> **Bugscuffle said:**
> ...[FONT=Tahoma]but please tell me if I’m all wet.[/FONT]

Far from wet, your conclusion is very well thought out. A dual boot will work quite well for you.

> [COLOR=black][FONT=Tahoma]I just need to now how to manipulate The UNBUNTU to arrive at the desired configuration.[/FONT][/COLOR]Following my instructions from 1-4 above will get you your desired configuration. Also, see this:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

It provides detailed step-by-step instructions that I just summarized above.

In the interest of providing complete info, it is also possible to install Ubuntu using a program called WUBI. This program does not require you to define two separate partitions and installs Ubuntu "inside" of Windows. It is a perfectly legitimate way to run Ubuntu and many people use it happily and without problems.

I prefer to make my Ubuntu installations truly dual boot for two reasons:

1. I am wary of having one operating system reliant on the file integrity and system integrity of another system. Too much like having all my eggs in one basket.
2. One of the best features of Linux is its better native security. Installing Ubuntu using the WUBI method basically exposes Linux to Windows security holes, which makes no sense to me.

But that's just me. Using WUBI makes for an easier install, so you should decide for yourself.

---

