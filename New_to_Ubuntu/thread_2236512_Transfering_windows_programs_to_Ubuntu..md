---
title: "Transfering windows programs to Ubuntu."
date: 2014-07-27
forum: New to Ubuntu
---

### Post by george62 on 2014-07-27
Hi, I'm new to ubuntu and have a few questions.
A friend of mine introduced me to Ubuntu and suggested I download it. When I installed it, I wasnt sure it would be for me so I kept windows7 installed on my computer. 
I have become a big fan of Ubuntu and I think I'm ready to give windows the boot. The only thing I ever use windows for anymore is to use some of the programs that I had installed. 
My question is, is there a way to transfer those windows based programs to Ubuntu? And after I transfer them, how do I go about eliminating windows7 from this computer?
Thanks in advance!

---

### Post by Mark Phelps on 2014-07-27
> My question is, is there a way to transfer those windows based programs to Ubuntu

Basically, no.  Linux is a different Operating System from Windows and, in most cases, Windows programs won't work.

I you want to try, you would have to reinstall each application using Wine. You can check the WineHQ website for the apps and versions you want to run, but anything not listed, or rated lower than Gold, is not going to work.

---

### Post by Bucky Ball on 2014-07-27
We'll take one question at a time. Please post a new thread for the second part when you get there: how to remove Windows. ;)

Windows programs don't work in Ubuntu, period (unless they are ported to Linux and have a Linux version). To run Windows programs in Linux you have two options: run a Windows virtual machine inside Linux or use Wine. In Wine, some programs will work, some won't. Find out here:

[https://appdb.winehq.org/](https://appdb.winehq.org/)

Your best bet is to see if you can find Linux alternatives to your Windows programs. Good luck.

* Ninja-ed! Like Mark Phelps said. ;)

---

### Post by coffeecat on 2014-07-27
> **george62 said:**
>  
My question is, is there a way to transfer those windows based programs to Ubuntu? And after I transfer them, how do I go about eliminating windows7 from this computer?
Thanks in advance!

As Mark Phelps said, Windows applications won't work in Ubuntu. I suggest you post a list of the Windows applications that you need to use, and then people can advise you on the nearest equivalents. In many cases, Linux equivalents will be able to read and modify data files saved from Windows applications, but we need to know more about what your uses are.

Don't be in a hurry to remove Windows from your computer. Many people dual-boot and there is no urgency in converting yourself from a Windows user to an Ubuntu user. It may be that there will be one or two Windows applications that you cannot do without and for which there is no viable Linux alternative. Many forum members find themselves in this situation and compromise by keeping Windows for those special use occasions, and running Ubuntu where considerations of security and usability make Ubuntu their favoured choice.

---

### Post by Bucky Ball on 2014-07-27
> **coffeecat said:**
> As Mark Phelps said, Windows applications won't work in Ubuntu. I suggest you post a list of the Windows applications that you need to use, and then people can advise you on the nearest equivalents. In many cases, Linux equivalents will be able to read and modify data files saved from Windows applications, but we need to know more about what your uses are.

Don't be in a hurry to remove Windows from your computer. Many people dual-boot and there is no urgency in converting yourself from a Windows user to an Ubuntu user. It may be that there will be one or two Windows applications that you cannot do without and for which there is no viable Linux alternative. Many forum members find themselves in this situation and compromise by keeping Windows for those special use occasions, and running Ubuntu where considerations of security and usability make Ubuntu their favoured choice.

+1 to all of this. I run an offline XP for a couple of audio/visual things I must have and there is no Linux equivalent for and boot to Ubuntu when I need to get online or do Ubuntu things on that machine.

---

### Post by Rob Sayer on 2014-07-27
This is why I still have one windows 7 partition.  I can't think of much now I'd need it for besides ripping a DVD because the linux programs aren't as up to date on encryption schemes as windows ones.

The transition from windows to ubuntu was maybe a little easier for me because I had switched before to linux ports in windows.  I was getting sick of program .exe installers also installing crappy codecs and other things with no warning.  Linux programs (especially from the standard tested repositories) are much better behaved.

As mentioned, running windows in a virtual machine is arguably best, but it's not exactly beginner stuff setting it up and for many users dual booting is fine.

---

### Post by whitesmith on 2014-07-27
Wine works with most Windows apps. There is a paid version called cxoffice ($80) that comes with both email and telephone support. The great thing about Wine/cxoffice is that emulation is not involved. It's sort of like the case where a program won't install under, say, Windows 7 unless you right-click setup.exe and then pick Windows ME--an application-compatibility layer in other words. That way there's no slowing down or bizarre behavior. Also, wine/cxoffice allows data to be exchanged between Windows programs and Linux programs, something that can't be done using VMs.

---

### Post by Cliff_Simonds on 2014-07-27
I personally recommend people to stay dual boot (no matter the os) ..._until the electronics industry starts making linux versions of firmware and bios updates_. I've shrank my windows partition(works safer and easier on an ssd than an hdd without any loss) and keep windows for this reason, using ubuntu 99% of the time and keeping windows updated on patch tuesdays.  Just last month I had a firmware update for my 256GB Samsung 840Pro and now it's blazing fast at last benchmark 10100 random read/write IOPS before it was between "only" 80K-90K, now that's a big jump and one reason I keep windows around.  Of course I'd have prefered that I could have downloaded a tarball, but the world isn't perfect.
  Also with dual boot, be it windows-linux, mac-linux or even linux-linux: if you have a catastrophic crash; so long GRUB is not affected, you have a backup system on the same computer to get help,or at the very least stay connected.

---

### Post by Bucky Ball on 2014-07-27
> **Rob Sayer said:**
> The transition from windows to ubuntu was maybe a little easier for me because I had switched before to linux ports in windows. 

Same here. Apart from the programs I still use in Windows, pretty much everything else was open-source - Firefox, Thunderbird, Zotero, Open Office, others I don't remember - and I was thrilled to find they were all available and running natively already in Ubuntu (and a heck of a lot easier to install directly from Synaptic)! That was a 'penny drop' moment and the rest, as they say, is history. ;)

@george62: As suggested, if you want to give us a list of the programs you're wanting to use we might be able to suggest some viable alternatives, if they exist.

---

