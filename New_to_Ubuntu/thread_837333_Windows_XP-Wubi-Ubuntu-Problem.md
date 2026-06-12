---
title: "Windows XP-Wubi-Ubuntu-Problem"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by fidamehran on 2008-06-22
I am a complete Ubuntu Newbie. So I guess I'm asking weird and naive questions.

I installed Ubuntu from Within Windows through "Wubi". Now I Dual Boot (that's what happened by default) with Windows XP. I have 3 questions.

1. Is there a program with which I can start a virtualized session of Windows XP while inside Ubuntu? (kind of like using Wine to run Windows XP from boot up scratch/ OS load point).... Very weird idea, I must say.

2. What will happen if my Windows crashes? As far as I know Ubuntu has been installed like a program within Windows. So, then what? What do I do then? Re-install Win XP? Re-install Ubuntu by booting from CD? (which I didn't do the first time to avoid the drive partitioning hassle). What to do then?

3. Is it possible that a virus or malware will infect while I am running Windows and affects the Ubuntu part of the hard disk, or affect Windows Files and parts when I am in Ubuntu?

I am a COMPLETE newbie, so I'm very much nosy. I hope Ubuntu Gurus won't mind.

---

### Post by diablo75 on 2008-06-22
1.  If you want to run a virtual machine, look into Virtual Box or VMware Server (Virtual Box being the more simple software of these two popular titles).  Visit the Virtualization forums for more info on this.  But if you're thinking of trying to run your current Windows system in a VM while running Ubuntu, don't think about it.  It can be done, but it is very, very dangerous.  You're much better off installing a fresh copy of Windows in a VM instead.

2.  It depends on what kind of "crash" we're talking about.  The dual booting is not dependent upon windows, but it is dependent upon your Master Boot Record, and subsequently GRUB.  If you're hard drive were suddenly garbled in total by a nasty virus, it may pose a risk to Ubuntu.  If you want to truly protect Ubuntu from such an occurrence, you should consider installing it on a separate hard drive on it's own native ext3 partition.

3.  As mentioned in the second point, I believe it is possible for a Windows virus to pose harm to a Wubi install, simply because Wubi places Ubuntu inside of a folder called Ubuntu on your FAT32/NTFS partition, and not on it's own separate partition.  Though the odds of catching a virus that can modify your MBR without your virus scanner knowing about it is unlikely.

If you are dual booting, I would highly recommend you start getting into the habit of NOT using Windows for anything Internet related if you can help it.  Work on finding alternative software in Ubuntu that you can use instead of software that depends on Windows.  Eventually, and hopefully, you'll find you're not using Windows for much if anything.  This will dramatically reduce the risk of a virus infecting Windows and posing harm to other files on your hard drive.

---

### Post by Paqman on 2008-06-22
> **fidamehran said:**
> 
1. Is there a program with which I can start a virtualized session of Windows XP while inside Ubuntu? (kind of like using Wine to run Windows XP from boot up scratch/ OS load point).... Very weird idea, I must say.

There's several different good options for setting up a Virtual Machine. The most popular are Virtualbox and VMWare Server, both of which are freebies. After installing the VM software, you install Windows (or any OS) into it as if you were installing on a real machine.

> 
2. What will happen if my Windows crashes? As far as I know Ubuntu has been installed like a program within Windows. So, then what? What do I do then? Re-install Win XP? Re-install Ubuntu by booting from CD? (which I didn't do the first time to avoid the drive partitioning hassle). What to do then?


Wubi doesn't actually mean Ubuntu is being run inside Windows. It just creates a virtual hard drive that's located on the same partition that Windows is installed on. The idea is to avoid having to partition your drive.

Even if Windows dies horribly, you should still be able to boot into Ubuntu as long as the MBR and the part of the drive Ubuntu resides on are both ok.

If you do ever reinstall Windows however, you will nuke Ubuntu. Thats because the Windows installer will format the drive/partition during the install process.

If you like, you can migrate your Wubi-installed copy of Ubuntu onto it's own dedicated partition. It's done using something called [LVPM](http://lubi.sourceforge.net/lvpm.html)

> 
3. Is it possible that a virus or malware will infect while I am running Windows and affects the Ubuntu part of the hard disk, or affect Windows Files and parts when I am in Ubuntu?


Windows malware is designed to exploit the Windows environment. It can't operate properly in Ubuntu.
You should take all your normal steps to protect your Windows installation (firewall, antivirus, smart behaviour). That'll protect you from malware, no matter where it comes from. 
On the Ubuntu side, all you really need to do is keep up-to-date with security updates. If you start running any server software then look into firewall settings for Ubuntu.

> 
I am a COMPLETE newbie, so I'm very much nosy. I hope Ubuntu Gurus won't mind.

No problem, it's exacty what this forum is for. Welcome!

---

### Post by fidamehran on 2008-06-23
> **Paqman said:**
> 
No problem, it's exacty what this forum is for. Welcome!

You guys are so sweet. Bless you all.

---

