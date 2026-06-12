---
title: "I think I've had it with Microsoft"
date: 2018-05-21
forum: New to Ubuntu
---

### Post by swampwiz on 2018-05-21
I'm a globetrotter, and happened to be in country whose language it not my own (English), and I needed to buy a system, so I bought one, ostensibly with Windows 10 Home.  It seems that the license for this system (brand: HP) is only good for the single language version of the country of purchase (Russia), so when I reinstalled with Windows 10 Home, the key that came with the system turned out to be invalid. :x  I suppose that I could use the key that is on the current system I using as a type, and then change that to an emergency system running Ubuntu, but I am considering just getting on with it and using Ubuntu on the new system.

However, there must be a number of conditions for this to work:

- I be able to get the proper drivers for my hardware.

- I must be able to use the files on my WD Passport drives as I can currently use them in Windows; I presume that my OpenOffice files will transition seamlessly.

- There must be a decent Windows emulator that I can use for those apps that I have that I cannot get in Ubuntu/Linux.

- There must be a pathway for me to recover after a system catastrophe, especially if this is the only system I happen to have.

- As a (retired, for now) Winforms/C#/C++, I need to be able to create new GUI apps using this; I know that I can do my Python & R in Ubuntu, but I don't feel like learning a new GUI stack.

I have only used Ubuntu in the past to do a repartition on, ironically, my current rig, when I had bought it having the craptastic Windows 8 pre-installed, installing Windows 7 instead.  But I am open to being a noob in the Ubuntu universe.

---

### Post by oldfred on 2018-05-21
First:
       Linux is not Windows:
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
[http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux)
The ultimate guide to Linux for Windows users 
[http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html)
Advice For New Users On Not Breaking Their Debian System - also Ubuntu
[https://wiki.debian.org/DontBreakDebian](https://wiki.debian.org/DontBreakDebian) 
    
You cannot really do Windows programming in Linux. If you need Windows purchase a copy of Windows. Wine may run some Windows programs, but many only partially work. 
And while learning a new gui is not the easiest thing, better to make leap.

I found geany relatively easy to do python programing, but I am only a beginner and now retired, so nothing critical. Used MS Access & dBase for years at work.

With Ubuntu I keep several flash drives with full installs of Ubuntu and ISO for reinstalling. So I only back up my data using rsync and would reinstall Ubuntu. I used to make sure all my Windows data was in one set of folders & used a .bat file to copy data, rsync is much better.

---

### Post by yancek on 2018-05-22
> It seems that the license for this system (brand: HP) is only good for the single language version of the country of purchase (Russia)

Did you get this information by contacting microsoft?  If not, I would definitely try contacting them.

[QUOTE]- I be able to get the proper drivers for my hardware.[QUOTE]

Can't help with that as we know nothing about your hardware so I would suggest you take a look at the hardware compatibility for Ubuntu, link below.

[https://certification.ubuntu.com/desktop/](https://certification.ubuntu.com/desktop/)

You can use wine on Ubuntu to run some windows software but it's pretty limited, no reason why it would not be.  Various software you can use to do backups and recovery.

---

### Post by sp40140 on 2018-05-22
Come to Linux world with your eyes (and mind) open to doing things differently. MS support might be able to help with license thing (YMMV).
As for "some sort of emulator", I would say use virtual env (virtualbox, vmware, kvm) install win and do all the work. If you keep regular back-up of your virtual disks, you can mitigate risk of crashes.
The new Ryzen cpus come with more cores so its easy to run vms.

I think with your use case, I would suggest you use vm even if you don't switch to linux.

---

### Post by oldrocker99 on 2018-05-22
Do understand that 99% of hardware drivers are already in the kernel. Printers usually need drivers, and nVidia cards do need drivers. Intel and AMD/ATI graphics processors use open-source drivers, and no need to install anything.

If you choose "Something Else" in the preparation screen, create a 64GB system disk, which is plenty of room, and use the rest as your /home drive, which is the **only** directory that you have read-write access to.

If a catastrophe happens, you simply reinstall, formatting the system partition, and mounting the rest as /home. That way, you will not lose any data.

There is a program for Linux called PlayOnLinux, which is a frontend for wine, the program that lets you run many (not all by any means, but still a lot) Windows programs. PoL has many scripts that automate installation of many programs. I installed Steam for Windows so I can play Wasteland 3, Skyrim, and Oblivion, and a few other games. It isn't just for games, either.

In 10 years, I have yet to find something Linux can't do for me, although I am certainly not a coder. However, Linux has the well-deserved reputation as a superior development platform.

In a world of freedom, who needs windows or gates?

---

### Post by darthvader0 on 2018-05-23
> **swampwiz said:**
>  It seems that the license for this system (brand: HP) is only good for the single language version of the country of purchase (Russia), so when I reinstalled with Windows 10 Home, the key that came with the system turned out to be invalid. :x
I'm not trying to be divisive, especially since I'm so new, but I am trying to understand your problem. You've had it with MS because the system you bought in a foreign country had a bad (counterfeit?) license code.  That isn't MS' fault but have you tried calling them and working through what your options are?

As for Linux, I recommend you research what tasks you do and see if Ubuntu (or any distro) aligns with those needs.  You mention writing apps (presumably for windows), as noted that's not something that can be done natively in Linux.  You'll have to deal with work arounds, and sometimes work arounds produce their own set of frustrations.

> [COLOR=#000000] I be able to get the proper drivers for my hardware.[/COLOR]
Do your homework, make sure you have a good inventory of the hardware and see what's available.

> [COLOR=#000000]There must be a pathway for me to recover after a system catastrophe, especially if this is the only system I happen to have.[/COLOR]
I would use a backup application and/or utilities to save your home directory to an external drive.


> [COLOR=#000000]There must be a decent Windows emulator that I can use for those apps that I have that I cannot get in Ubuntu/Linux. 
The best and most encompassing solution is to run windows inside a virtualbox vm.

Ubuntu has a lot to offer, and I'm no where near an expert, but what I have used it for, has been excellent. [/COLOR]

---

### Post by pete-br on 2018-05-24
The easiest and fastest way to find out if Ubuntu will give you problems on your system is to boot it up with the Ubuntu installation disk to run the Live Environment. From the Live environment you can test if everything works (sound, internet) and definitely test if your external drive will work with Ubuntu too.
Run 'dmesg' in a terminal window and inspect it's output to see if it shows any problems. Especially look for anything that is shown in red. If you need advise and internet works from the Live Ubuntu, why not come here and ask. You copy-and-paste your errors from the terminal window to the Ubuntu forum all from the Live environment. Use it!

For Windows development however, use Windows. Wine isn't without flaws.

---

