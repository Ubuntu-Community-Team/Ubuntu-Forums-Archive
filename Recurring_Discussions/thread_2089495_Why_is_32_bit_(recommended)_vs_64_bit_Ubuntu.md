---
title: "Why is 32 bit (recommended) vs 64 bit Ubuntu"
date: 2012-11-29
forum: Recurring Discussions
---

### Post by JeffreyDB on 2012-11-29
The [desktop download screen]("http://www.ubuntu.com/download/desktop") lists the 32 bit versions as (recommended) vs the 64 bit.

I'm curious as to why that would be so for 64 bit computers.

---

### Post by grahammechanical on 2012-11-29
That recommendation is there so that new Ubuntu users get a good install experience.

The 32bit version of Ubuntu will load as a live session, will install and will run on a 64bit CPU as well as a 32bit CPU.

The 64bit version of Ubuntu will only load, install and run on a 64bit CPU.

Someone who lacks understanding of the difference between 32bit CPUs and 64bit will get a bad experience trying out a 64bit version of Ubuntu on a 32bit CPU machine. But if the try a 32bit version of Ubuntu they will get (fingers crossed) a good experience of Ubuntu whether the machine has a 32bit CPU or a 64bit CPU.

This is the logic as far as I can tell.

Some people also get confused when they notice that the 32bit version is called i386 and the 64bit version is called amd64. They think that one is a version for Intel CPUs and the other for AMD CPUs. But both versions will run on either an Intel or an AMD CPU. What matters is whether the CPU is 32bit or 64bit.

Regards.

---

### Post by JeffreyDB on 2012-11-29
> **grahammechanical said:**
> That recommendation is there so that new Ubuntu users get a good install experience.

The 32bit version of Ubuntu will load as a live session, will install and will run on a 64bit CPU as well as a 32bit CPU.

The 64bit version of Ubuntu will only load, install and run on a 64bit CPU.

Someone who lacks understanding of the difference between 32bit CPUs and 64bit will get a bad experience trying out a 64bit version of Ubuntu on a 32bit CPU machine. But if the try a 32bit version of Ubuntu they will get (fingers crossed) a good experience of Ubuntu whether the machine has a 32bit CPU or a 64bit CPU.

This is the logic as far as I can tell.

Some people also get confused when they notice that the 32bit version is called i386 and the 64bit version is called amd64. They think that one is a version for Intel CPUs and the other for AMD CPUs. But both versions will run on either an Intel or an AMD CPU. What matters is whether the CPU is 32bit or 64bit.

Regards.

Thanks grahammechanical. I thought maybe the drivers weren't as comprehensive on the 64 bit version or something. My laptop is definitely 64 bit and runs the 64 bit version of Windows 8. I'm hoping to do my first Linux install ever using Virtual Box to run it as a Window within Windows so to speak.

Do you think the 64 bit version would be better for me?

---

### Post by oldos2er on 2012-11-29
It's an old bug that the web site team hasn't fixed yet. There's no real reason not to use 64-bit these days.

---

### Post by JeffreyDB on 2012-11-29
> **oldos2er said:**
> It's an old bug that the web site team hasn't fixed yet. There's no real reason not to use 64-bit these days.

Thank you, Ann.

---

### Post by pkadeel on 2012-11-29
> **JeffreyDB said:**
> Thanks grahammechanical. I thought maybe the drivers weren't as comprehensive on the 64 bit version or something. My laptop is definitely 64 bit and runs the 64 bit version of Windows 8. I'm hoping to do my first Linux install ever using Virtual Box to run it as a Window within Windows so to speak.

Do you think the 64 bit version would be better for me?
If you are going to install it within virtualbox then I would recommend 12.04.1 instead of 12.10 for better experience. The reason is the virtual box has yet to upgrade their software to become at par with kernel used in ubuntu 12.10

---

### Post by audiomick on 2012-11-29
> **JeffreyDB said:**
> I thought maybe the drivers weren't as comprehensive on the 64 bit version or something.

This used to be the case. There was particularly rather a lot of bother with Flash on 64 bit systems. That was about 4 years ago, though.

---

### Post by snowpine on 2012-11-29
If Ubuntu is going to be a virtualbox "guest" OS then there are a couple of extra steps that must be satisfied in order to run 64-bit guest:

[http://www.virtualbox.org/manual/ch03.html#intro-64bitguests](http://www.virtualbox.org/manual/ch03.html#intro-64bitguests)

(32 bit requires no extra steps)

---

### Post by oldfred on 2012-11-29
Also if you are going to dual boot with Windows 8 that was pre-installed then you have to have the 12.10 64 bit version as that has the new grub2 2.00 that includes the UEFI secure boot capability. And installer has to be booted in UEFI mode not BIOS/Legacy/AHCI mode.

Grub2 2.00 is supposed to be included in the next point release of 12.04 in Jan. I would think then 12.04 could be dual booted in secure boot UEFI configurations.

The 32 bit versions are for older computers and do not even have UEFI capability.

---

### Post by nothingspecial on 2012-11-29
grahammechanical is correct.

32 bit will work on any computer, 64 bit will only work on 64 bit machines. It is recommended for users who wouldn't know or care about the difference.

Or so I have been told anyway.

---

### Post by JeffreyDB on 2012-11-29
> **pkadeel said:**
> If you are going to install it within virtualbox then I would recommend 12.04.1 instead of 12.10 for better experience. The reason is the virtual box has yet to upgrade their software to become at par with kernel used in ubuntu 12.10

Aargh, but thanks for the heads up, pkadeel. 

I downloaded the 12.10 32 bit version because it was (recommended). But after thinking about it a bit and posting this thread & getting the responses I downloaded 12.10 64 bit. Now I guess I'll need to download the 12.04 64 bit version. At least I found the torrent for it rather than burdening the servers here any more.

I wish I had just asked first. But if I do go dual boot later, the 12.10 64 bit version sounds like it would be better per post below.

---

### Post by JeffreyDB on 2012-11-29
> **snowpine said:**
> If Ubuntu is going to be a virtualbox "guest" OS then there are a couple of extra steps that must be satisfied in order to run 64-bit guest:

[http://www.virtualbox.org/manual/ch03.html#intro-64bitguests](http://www.virtualbox.org/manual/ch03.html#intro-64bitguests)

(32 bit requires no extra steps)

Thanks snowpine. I had been bouncing around in the V Box manual a bit last night and had seen the section talking about modifying the setup for 64 bit guest operating systems on top of 32 bit host operating systems, but then read:
[INDENT]On 64-bit hosts (which typically come with hardware             virtualization support), 64-bit guest operating systems are always             supported regardless of settings, so you can simply install a             64-bit operating system in the guest.
[/INDENT]Which made me think I didn't have anything to worry about since my host, Windows 8, is also 64 bit. I'm not sure how I missed the highlighted warning below it, though:
**Warning**

On any host, you should enable the **I/O           APIC** for virtual machines that you intend to use in           64-bit mode. This is especially true for 64-bit Windows VMs. See           [the section called “"Advanced" tab”]("http://www.virtualbox.org/manual/ch03.html#settings-general-advanced"). In addition, for           64-bit Windows guests, you should make sure that the VM uses the           **Intel networking device**, since           there is no 64-bit driver support for the AMD PCNet card; see [the section called “Virtual networking hardware”]("http://www.virtualbox.org/manual/ch06.html#nichardware").


I had never heard of an **I/O           API**, but then again it sounds like the Wizard set up thingie will help set it up correctly for me.

---

### Post by monkeybrain2012 on 2012-11-29
I have not used WINE very much and never on 64 bits, but I read on these forums that it doesn't quite work on 64 bits, so if you use WINE you may want to investigate this.

---

### Post by Elfy on 2012-11-29
*Thread moved to **Recurring Discussions**.*

---

### Post by JeffreyDB on 2012-11-29
Uh oh.  Things were going swimmingly during the Virtual Box installation of Ubuntu (10.04.1 64 bit) until I got to a screen that said there was no operating system detected on the disk and gave me two options... erase the disk and install Ubuntu, Or "Something Else."(see attachment)

I'm not sure if this is referring to the virtual disk created by Virtual Box a step or two earlier, or if it means the entire hard drive.

I had been following along in the [Virtual Box Manual]("http://www.virtualbox.org/manual/ch01.html#idp8299040") to that point, but don't see any mention of that screen. I'm guessing that it means just that particular virtual drive, but am quite leery of "deleting any files on the disk".

Anyone with any experience with setting up the 1st operating system on Virtual Box?

---

### Post by nothingspecial on 2012-11-29
> **JeffreyDB said:**
> 

Anyone with any experience with setting up the 1st operating system on Virtual Box?

You current question no longer has anything to do with the title of your thread. 

Please make a new thread in the virtualisation section.

[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

Closed.

---

