---
title: "Question about torrents and viruses"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by LeeHamo on 2008-09-29
Hi,

As there is no need for a virus scanner, firewall, spyware, malware and all that stuff scanner then is it possible for me to d/l a virus from a torrent into ubuntu and not find out cause ubuntu has no scanner?

Then even run it or play the video etc and it breaks my pc?

Cheers,

Lee.

---

### Post by iaculallad on 2008-09-29
> **LeeHamo said:**
> Hi,

As there is no need for a virus scanner, firewall, spyware, malware and all that stuff scanner then is it possible for me to d/l a virus from a torrent into ubuntu and not find out cause ubuntu has no scanner?

Then even run it or play the video etc and it breaks my pc?

Cheers,

Lee.

Yes, it's possible for you to download a virus-infected file and be able to execute it through wine but it won't break your PC. Remember that Ubuntu is not windoze. Ubuntu differs from its file system architecture with that of windoze.

---

### Post by Bakon Jarser on 2008-09-29
It's possible to download one but it won't hurt your computer.  If there were viruses like that then we would need virus scanners.

---

### Post by LeeHamo on 2008-09-29
What is Wine? (ill look it up)  Sorry I only installed ubuntu 2 days ago and before that linux was just a word to me.

So if it cant hurt my ubuntu can it hurt my other HDD with windows on it even though I d/l it in ubuntu?

And if I have d/l such virus will it just sit forever in my ubuntu install somewhere unable to function?

If I boot into windows is it possible to use my windows virus scanner to scan my ubuntu HDD.

Cheers,

Lee.

---

### Post by aysiu on 2008-09-29
Any virus you download will be a Windows virus that will not execute on the Ubuntu side.

But if you open it from the Windows hard drive, it'll operate just as it would if you downloaded it there in the first place.

If you're worried about viruses in Ubuntu, you shouldn't. If you're worried about viruses in Windows, install and use SuRun and get rid of that useless antivirus software.

---

### Post by iaculallad on 2008-09-29
> **LeeHamo said:**
> What is Wine? (ill look it up)  Sorry I only installed ubuntu 2 days ago and before that linux was just a word to me.

An application that emulates the execution of M$ applications in Ubuntu.

> **LeeHamo said:**
> So if it cant hurt my ubuntu can it hurt my other HDD with windows on it even though I d/l it in ubuntu?

No it won't if those virii infected files resides in your /home directory or any Linux file system folder as windoze does not automatically recognize Ext3/Ext2 (just a sample) partitions. It can only infect other files when saving it on NTFS partitions and executing it while booted on M$ windoze.

> **LeeHamo said:**
> And if I have d/l such virus will it just sit forever in my ubuntu install somewhere unable to function?

Yes, it will just remain on a dormant-state until executed when in windoze.

> **LeeHamo said:**
> If I boot into windows is it possible to use my windows virus scanner to scan my ubuntu HDD.

No, to reiterate it, windoze does not automatically support a Linux-based file system. But you can do the other way around, when in Ubuntu, you can scan NTFS partitions.

---

### Post by LeeHamo on 2008-09-29
> **iaculallad said:**
> An application that emulates the execution of M$ applications in Ubuntu.

Ok thanks.

> **iaculallad said:**
> No it won't if those virii infected files resides in your /home directory or any Linux file system folder as windoze does not automatically recognize Ext3/Ext2 (just a sample) partitions. It can only infect other files when saving it on NTFS partitions and executing it while booted on M$ windoze.

When I bought this drive for ubuntu, I first formatted it in windows to NTFS and then installed ubuntu on it, does this mean it is still NTFS or has ubuntu changed it?

> **iaculallad said:**
> Yes, it will just remain on a dormant-state until executed when in windoze.

Not keen on the thought of having a virus living dormant in my PC forever :( 

> **iaculallad said:**
> No, to reiterate it, windoze does not automatically support a Linux-based file system. But you can do the other way around, when in Ubuntu, you can scan NTFS partitions.

How do I do this?

---

### Post by Greyed on 2008-09-29
> **LeeHamo said:**
> As there is no need for a virus scanner, firewall, spyware, malware and all that stuff scanner then is it possible for me to d/l a virus from a torrent into ubuntu and not find out cause ubuntu has no scanner?

Who said there's no virus scanner?

[http://packages.ubuntu.com/hardy/clamav](http://packages.ubuntu.com/hardy/clamav)

---

### Post by iaculallad on 2008-09-29
> **LeeHamo said:**
> Ok thanks.
When I bought this drive for ubuntu, I first formatted it in windows to NTFS and then installed ubuntu on it, does this mean it is still NTFS or has ubuntu changed it?

If you've installed Ubuntu through Wubi, then, virus will thrive in your NTFS partition and not in Ubuntu's virtual disk.

But if you had installed Ubuntu on a dedicated disk, then, Ubuntu might have partitioned your drive with Ext3/Ext2 (Just a sample). So these viruses are totally wiped out.

> **LeeHamo said:**
> How do I do this?

Install Clamav in your Ubuntu machine and use it to scan all your drives/partition as it doesn't care if it's formatted to NFTS or FAT32. Just be sure that those partitions are mounted.

---

### Post by LeeHamo on 2008-09-29
I installed ubuntu through the CD I have with it on, installed hdd in windows, formatted it to ntfs, put ubuntu disk in, rebooted pc and installed ubuntu on new drive.

---

### Post by iaculallad on 2008-09-29
> **LeeHamo said:**
> I installed ubuntu through the CD I have with it on, installed hdd in windows, formatted it to ntfs, put ubuntu disk in, rebooted pc and installed ubuntu on new drive.

No worry, As long as it's an Ubuntu dedicated installation. GParted had formatted that NTFS drive with either Ext3/Ext2 (Just a sample).

---

