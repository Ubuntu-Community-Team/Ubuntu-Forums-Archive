---
title: "Safety / Stability of Ubuntu?"
date: 2024-09-30
forum: New to Ubuntu
---

### Post by nearos on 2024-09-30
Hi everyone, i'm a new user in the phase of planning out my next move. I thought of switching to linux on my laptop. 
However, I'm worried, as i had previously attempted to install Linux Mint on an old PC, and while it worked, the second day it couldnt boot and i had to reinstall it again (i assume i restarded while it was updating the kernel, or some important file.)
I've heard that ubuntu is better in terms of stability and i'd like to switch to that seeing that im not really comfortable with Windows security.

So how safe and stable is it? How do i make sure that i wont wipe my OS when i close my pc to go to sleep? I apologise if this is a dumb question. Cheers everyone. :P

---

### Post by TheFu on 2024-09-30
Switching OSes isn't something that should be taken lightly.  Please spend a year running the Linux you want before making a choice like that.  

I've been trying to remove MSFT from my computing for over 15 yrs and I'm down to 2 programs that simply cannot be replaced that only run on MS-Windows.  I keep an MS-Windows VM around just for those 2 programs.  One of them gets used 1 week a year. The other one gets used about 2x a month for 30-60 minutes.  Everything else is done on Linux.

I've been using Linux since 1993.  I've been a Unix and Linux admin since 1995.  Switching OSes "cold turkey" is a bad idea unless you've carefully planned how you'll accomplish every task from the old OS on the new OS.

BTW, on the desktop, I find Mint just as stable as Ubuntu AND it doesn't add the less-than-great mandates that Canonical has been heaving on users which started in 2012.  In 2020, they started pushing some things that were just too far for me, so 20.04 is the last Ubuntu desktop I'll ever personally use by choice.

Mint handles some very important things much nicer than Ubuntu too - like **Timeshift** and **Back-in-Time** setup in their post-install wizard. Hopefully, you actually did what they recommend and created snapshots with Timeshift to make recovery nearly trivial for any boot issues.  Both of those tools should work for normal Ubuntu installs too.  I'm less certain about installs that are like mine with LVM or ZFS file systems or encrypted storage.  I've only seen timeshift and b-i-t on a normal ext4 with partitions install, where both worked nicely.

As for wiping an OS, that would only happen if you setup the system to do that or there's some hardware issue.  Of course, bonehead mistakes can happen too.  I've made my share of those too.

---

### Post by ian-weisser on 2024-09-30
> **nearos said:**
> So how safe and stable is it?

Depends upon your usage.
Depends upon your habits.
Depends upon your existing skills.
Depends upon your willingness to learn new skills.
Depends upon your expectations and goals.

Some people take to Linux like a fish to water. For them, it's stable.
Others try to hammer Linux into an obtuse configuration. For them, it's unstable.

Some people have good security habits. For them, Linux is secure.
Others with poor security habits may find their systems compromised.

---

### Post by nearos on 2024-10-01
Regarding the smooth transition from one OS to another OS, do you suggest creating another partition to boot into linux? Or have an ubuntu virtual machine?
I'd agree that cold turkey isn't really the way to go since i've been using Windows for most of my life. I did try linux mint and i honestly enjoyed it but i kinda screwed around since i didn't really know what i was doing. Learned it the hard way lol.

---

### Post by tea for one on 2024-10-01
More ways to explore/experiment with Ubuntu without affecting your Windows PC:-
Ubuntu in a live session on a USB
Ubuntu live with persistent storage 
Ubuntu installed with user and password on an external device (SSD or USB)

---

### Post by ian-weisser on 2024-10-01
> **nearos said:**
> Regarding the smooth transition from one OS to another OS, do you suggest creating another partition to boot into linux? Or have an ubuntu virtual machine?

Start with a VM, if your hardware permits. Dual-boot can be fraught.

Work methodically, application by application.

Take notes of account details, settings, and software you install. Many  new users reinstall as their needs evolve, and notes will enable you to reinstall all your applications, accounts, and settings easily and quickly.

In early days, stick to default settings. It's much easier to get help if your screenshot looks familiar to the helper's.

If, on the Windows side, you use proprietary software (like MS Office), migrate to a cross-platform alternative (LibreOffice) that will behave similarly on either system.

---

### Post by yancek on 2024-10-01
>  So how safe and stable is it? How do i make sure that i wont wipe my OS when i close my pc to go to sleep?

You would have to do more than close your PC to wipe an OS.  What you need to do is some research before beginning. I don't think there is that much difference between Mint and Ubuntu although Ubuntu probably has better support.  Using virtual software if your hardware is capable or a live usb would probably be best as a test environment.

---

### Post by TheFu on 2024-10-01
> **ian-weisser said:**
> Start with a VM, if your hardware permits. Dual-boot can be fraught.

Work methodically, application by application.

Take notes of account details, settings, and software you install. Many  new users reinstall as their needs evolve, and notes will enable you to reinstall all your applications, accounts, and settings easily and quickly.

In early days, stick to default settings. It's much easier to get help if your screenshot looks familiar to the helper's.

If, on the Windows side, you use proprietary software (like MS Office), migrate to a cross-platform alternative (LibreOffice) that will behave similarly on either system.
^^^^^^^^^^
This is my preferred recommendation. Run the VM full screen and use it for everything, all day.  You will struggle. The struggle is important to learn to "think the Unix way" and think the MS-Windows way less and less.  They are very different OSes with very different philosophies.

Using a bootable, persistent flash drive install of Linux can also work, but the amount of storage will be limited and flash drive media does where out.  Some people use an external SSD instead of Flash drives for better wear and performance.  This is like dual boot, without the dangers that dual boot provides.  

MSFT is known for screwing up the dual boot, breaking the linux-side boot about once a year.  Of course, that never happens when you have 2 days to figure out the issue. It will happen when you are in a hurry, busy.

With a VM, booting of the system is really never at risk.  Most VM virtual storage that people use supports "snapshots" and it is easy to make an exact copy of the entire OS (everything), just by copying the VM virtual storage file.  With that file, you have YOUR desktop, all data, all installed program, all settings and can take it to another computer using the same VM hypervisor to run.  Around 2009, when I was traveling for work, I'd put a copy of my VM on a flash drive as a backup.  Had my laptop stolen at an airport, but still needed to catch a 16 hr flight to a client.  On arrival, I bought a new laptop at a market, took it back to the hotel, loaded the VM hypervisor I'd been using, then copied over the .VDI file and immediately had "MY desktop" back.  It was an inconvenience, not a disaster.  Of course, back then, we didn't have USB3 nor did we have huge flash storage devices, so my desktop was limited to 32GB, but that wasn't an issue.

Lots of flexibility.

In 6-12 months, after you've learned what Linux can do, perhaps you'll want to switch the booting OS from MS-Windows to Linux and put MS-Windows into a VM for emergency use only.  But don't rush it.  I ran with Linux inside a VM for a number of years because I did video editing under MS-Windows with a Windows-only commercial tool.  That program wouldn't run inside a VM, as it used the GPU directly.

---

### Post by nicolasdentremont on 2024-10-01
> **nearos said:**
> Regarding the smooth transition from one OS to another OS, do you suggest creating another partition to boot into linux? Or have an ubuntu virtual machine?
I'd agree that cold turkey isn't really the way to go since i've been using Windows for most of my life. I did try linux mint and i honestly enjoyed it but i kinda screwed around since i didn't really know what i was doing. Learned it the hard way lol.

Using a VM is usually a pretty safe way to experiment and try new things. The level of difficulty that people experience switching from Windows to Linux varies from person to person.

I switched over from Windows to Ubuntu maybe 8 months ago. I was already using free/open source software for everything I do so it all worked on Linux without any issue. If you use a lot of software without Linux support or want to play the newest PC games it could be harder.

Something that helped me a lot at first was the book The Linux Command Line by William Shotts, you can get it as a PDF at [https://linuxcommand.org/tlcl.php](https://linuxcommand.org/tlcl.php)

---

### Post by TheFu on 2024-10-01
Thanks for posting your more recent conversion *nicolasdentremont*.  I've used that book in my *Beginning Linux* course at the local university.  Having the non-GUI knowledge as a foundation makes many things so much more understandable, I've found.  

It is the difference between someone who can start up a car to use it and someone who is can do minor maintenance themselves in addition to driving their car.  If you don't know how things work a little behind the scenes, many things in Linux/Unix don't make too much sense. But if you do have that behind the curtain understanding, there is an elegance for how almost everything works.

[https://linux.oneandoneis2.org/LNW.htm](https://linux.oneandoneis2.org/LNW.htm) is another quick read to get your mind right for Linux use.

---

### Post by grahammechanical on 2024-10-02
> However, I'm worried, as i had previously attempted to install Linux Mint on an old PC

How old? It could be that Ubuntu might not be the best choice for that old machine. There are what we call flavours of Ubuntu which use a different desktop environment and user interface than Ubuntu which uses Gnome desktop environment.

Flavours such as Xubuntu and Lubuntu might work better on that machine than Ubuntu because need less resources.

[https://xubuntu.org/](https://xubuntu.org/)

[https://lubuntu.me/](https://lubuntu.me/)

Because they are official flavour of Ubuntu they are as stable and secure as Ubuntu.

Regards

---

### Post by Norm24 on 2024-10-02
> **nicolasdentremont said:**
> Something that helped me a lot at first was the book The Linux Command Line by William Shotts, you can get it as a PDF at [https://linuxcommand.org/tlcl.php](https://linuxcommand.org/tlcl.php)

Excellent reading.

---

