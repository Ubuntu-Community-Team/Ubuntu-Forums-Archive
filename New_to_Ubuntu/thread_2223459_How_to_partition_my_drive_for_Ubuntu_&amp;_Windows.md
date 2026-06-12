---
title: "How to partition my drive for Ubuntu &amp; Windows (dual boot) or VM?"
date: 2014-05-11
forum: New to Ubuntu
---

### Post by Xoxy on 2014-05-11
Hello,
I'm really new to this.
I have a 100 GB SSD and a 1 TB HDD.
ATM I'm running Windows7 on the SSD and all my files and programs are on the HDD.
My RAM is 8GB.

My problem is: there are some programs I am not able to run in Ubuntu and which I don't want to give up.

So I was thinking about a **dual-boot system**.
**Should I format the SSD into two partitions for the two OS?** If so, how large should they be respectively? I want to use [LXLE]("http://lxle.net") as my ubuntu-derived OS.
My /home folder can sit in the HDD. What size do you recommend for it? I occassionally play MMOs but I rarely have more than one installed. Most of my time is spending writing and internet browsing.

OR: someone at G+ suggested that I can run Ubuntu soley and use a **Virtual Machine for Windows 7**.
Would you recommend that?
Can Windows 7 as VM get access to your hard drive? I know it can't do .ext4 per default, you need to install a separate program. Can I do that in a VM?

Thank you very much!

---

### Post by ibjsb4 on 2014-05-12
I do not run windows or SSD, so there are questions that I cannot answer.  But ..

I do run VirtualBox and find it for testing or trying out an OS to be very helpful.  Examples:
No need to burn a CD/DVD, a guest system can be install direct from the host system.
You can take snapshots of guest system and use it to restore a broken system with just a few clicks.

There is a learning curve and again I don't know/use windows so I will not be of much help.

If you want to know more about VM's, I suggest starting a thread in the 'Virtual Machine' sub-fourm.

---

### Post by Impavidus on 2014-05-12
You can partition the SSD to have both systems installed there. Alternatively, you can install Ubuntu on the HDD. This will cost you a few seconds every day because Ubuntu will boot slower and will start its applications slower, but the advantage is that you can keep the Windows boot loader on the SSD. If anything goes wrong with grub, you can still boot Windows by changing the boot order in the bios.

Ubuntu and its derivatives work well with a root partition of about 20GB. Less works too, but you have to be careful. You can make your /home partition as large as you can spare. You know best how much data you want to store.

I don't use SSDs, Windows or virtual machines myself, but I do know that virtual machines have lower performance than real machines. If your Windows-only programs depend on fast graphics it wouldn't be an option I think.

---

### Post by LastDino on 2014-05-12
You can certainly run W7 on VM with that RAM (What is the processor?), but assuming it is genuine, I would rather keep it where it is right now and simply duel boot. You seem to have done your research, so this shouldn't be too hard.
For /home anything around 100 GB is more than enough if you're keeping it on that 1TB HD. 
''/'' = root should be of 24 GB max
Looking at given amount of RAM, you can get away with making small SWAP partition.
You can also make separate /boot if you want, which should be of in between 200-300 MB.

But first and foremost, do find out whether your system is UEFI or Legacy BIOS.

---

### Post by impliedconsent2 on 2014-05-17
> **Xoxy said:**
> ***I occassionally play MMOs*** but I rarely have more than one installed. Most of my time is spending writing and internet browsing. OR: someone at G+ suggested that I can run Ubuntu soley and use a **Virtual Machine** for Windows 7. Would you recommend that? Can Windows 7 as VM get access to your hard drive? I know it can't do .ext4 per default, you need to install a separate program. Can I do that in a VM?

**READ ALL THE WAY THROUGH BEFORE HITTING LINKS**


[LIST]
[*]Gratz on getting this on an SSD. New or old systems - best, absolutely no argument, upgrade, ANYONE can make to their system.  I welcome anyone to dare to argue (separate thread please, don't hijack Xoxy's post).
[*]Virtual Machine (recognized leader for Linux - [Virtualbox]("http://www.oracle.com/technetwork/server-storage/virtualbox/overview/index.html")):  Depends on the MMO. You might be able to get away with a decent playing experience if you lower the game's visuals - or - if you have a hefty processor, you might be alright. I've been tempted to test this on my (thankfully last remaining subscription - no longer interesting) WoW. Yes, W7 can access the Linux hard-drive and visa-versa.  You can certainly access ext4.  I don't know why Oracle does simply include the [Oracle VM VirtualBox Extension Pack]("http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack"), but it's installed after installing [Virtualbox]("http://www.oracle.com/technetwork/server-storage/virtualbox/overview/index.html").
[*]First thing I would do is fully read and comprehend [The Virtual Box User Manual]("http://www.oracle.com/technetwork/server-storage/virtualbox/documentation/index.html")
[*]There 'could' be a way of capturing your existing Windows installation, keeping all apps, custom stuff without re-installing from scratch, as it is now, into a format that Virtual Box will recognize and use.  I have not done this, but, sounds promising.  See [How to Convert a Physical Computer to a Virtual Machine]("http://www.serverwatch.com/server-tutorials/how-to-convert-a-physical-computer-to-a-virtual-machine.html")
[/LIST]

I always push Virtualbox to run other OSs if your hardware is up for it.  Old laptops (like my 2006 HP, 1.86GhZ, 2GB) is painful to use with a VirtBox, but still workable.  My current new system (homebuilt 4670k (no OC), 16GB, SSD + storage HDD), Virtualbox absolutely rocks (sadly, I only NEED W7P for 1 VPN connected resource intensive application and Virtualbox laughs at it...love Virtualbox).  Running my Kubuntu host and pushing the the VB/W7 app, I still have 4GB available RAM to play with.  Still not hitting swap.

If your dead set on dual boot - see this: [WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot"). I've successfully had a dual boot scenario, but wasn't worth it to me for just 1 application.  Good Luck!

---

### Post by Xoxy on 2014-05-31
Thank you for all your answers! I appreciate that.

---

### Post by newbie2244 on 2014-05-31
And because you appreciate answers, here's on!e more . . . 

My suggestion, although I'm a noob, is the dual boot system. Virtual installs are always slower. I have a dual boot system, that I stupidly virtualized and it is much slower than my other older system which is a simple dual boot system.

 I don't have ssd, so I don't know about partitioning an ssd. But you could use your hdd for one OS and ssd for the other. I think it all depends on what apps you intend to use most frequently and which apps will generate the most data. If you use mostly Ubuntu/Linux based apps, then make your linux root partition as large as you can on whichever drive you choose to use. 

On my other, older, system, I had a root disk of 30 GB and I now get "insufficient memory" warnings. On my currrent system (I still have the older system), I partitioned my disk so my "root" or "Ubuntu" partition has 207 GB.  My swap is 117GB.  This way I can do graphics animation programming without fear of running out of memory. 

Partitioning is a bit tricky, because at least on an hdd, you should have your partitions begin on a boundary of some multiple of 4096 bytes. I think OldFred's posts on this topic are helpful. Before you actually partition anything read the old posts first. CHeck to see which partition tool gparted or parted you should use. The results are different depending on which tool you use. 

  Hope this helps and GOOD LUCK!

ALso check this post -  it explains everything succinctly.  

[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

---

