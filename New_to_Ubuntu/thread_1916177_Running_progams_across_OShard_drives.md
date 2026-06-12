---
title: "Running progams across OS/hard drives"
date: 2012-01-27
forum: New to Ubuntu
---

### Post by Zvanochek on 2012-01-27
I've installed ubuntu and XP on separate partitions on the same hard drive  as there are still some programs that work better on windows but I like ubuntu.

Previously I have installed MS Word in Ubuntu and it worked fine; If I installed it in the Ubuntu section of the drive, can I still run it in windows or vice versa?

---

### Post by Double.J on 2012-01-27
Hi there, 

When you install a program in wine, it's files are stored in directories created within wine to run on ubuntu - wine is a compatibility layer to ubuntu. 

As for running a program installed on another OS, this is no more possible with ubuntu than installing office on an XP partition and just opening up XP's "D:" drive from win7 and trying to run programs installed in XP's Program files. Each OS has it's own programs. In linux, we can use a tool called chroot, to take control of another linux system on an attached drive and run it's programs, but this can't be done for windows.

Another problem to the situation is that windows can't read ubuntu partitions. You can install a driver to read the partitions, but you still won't be able to write to it.

You can make life easier for yourself by using cross platform programs such as Office, and VLC, GIMP, Firefox, Thunderbird etc.

Sorry if it's not the answer you were hoping for, I know office takes a while to set up and a fair bit of disk space for a program suite, but at least you can use the same purchased disk - I have a mac and it would seem that MS have decided that I should buy two office licences:lol:

Edit; one thing to remember about the EULA of MSOffice - you can install it on machines owned by you. Whilst MS would prefer you didn't install it on linux, as far as I'm aware this isn't currently against their EULA. You can install it on multiple machines - for example your desktop and your laptop, so long as they are yours; Even if they are your wife/daughter/mother/son's MS say you need a seperate licence, or a multi user licence. I take this to mean that You can install the same version of Office on both ubuntu and windows at the same time and still comply, as installing the same copy on XP and Win7 on the same machine would be okay :)

---

### Post by Zvanochek on 2012-01-27
Thank you for your clear reply. I had suspected as much, but it was worth checking before I wasted the effort of installing office twice! The plan is to run pretty much everything on Ubuntu, only swapping over when needed.

---

