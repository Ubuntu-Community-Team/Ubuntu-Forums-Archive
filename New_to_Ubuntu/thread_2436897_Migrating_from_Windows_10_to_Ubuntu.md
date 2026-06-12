---
title: "Migrating from Windows 10 to Ubuntu"
date: 2020-02-15
forum: New to Ubuntu
---

### Post by dbee on 2020-02-15
I'm getting kinda tired of Windows 10. I have a pretty cheap computer with only the following specs ...

Processor	Intel(R) Celeron(R) CPU  N3060  @ 1.60GHz, 1601 Mhz, 2 Core(s), 2 Logical Processor(s)
System Model	HP Stream Laptop 11-y0XX
OS Name	Microsoft Windows 10 Home
Version	10.0.17763 Build 17763
RAM 2GB

Basically this system is problematic for 3 reasons ... 1) the cpu and mem are always running at capacity 2) i've a 29 GB harddrive that only has around 2 GB free space left, 16.6 GB of that data is taken up with Windows and reserved files (and i can't install the latest windows updates) 3) i've heard windows 10 is very vulnerable to hackers, web scripts etc...

My question is this - will an install of ubuntu fix my cpu/mem capacity issues ? I'm presuming it'll fix my harddrive issues since ubuntu will take about 3GB to install and update ?

Is there any compatibility issues with ubuntu and my system hardware ? Last time I installed ubuntu (many years ago) there were issues with my HP Pavillion touchpad. Although i can try Ubuntu Live and see for myself i suppose.

Can i still read files on my external hard drive ADATA HV 300  I presume it's formatted for windows so i'll have to reformat it and transfer the files to a usb key ? Can i transfer the files to the same bootable usb key that i use for ubuntu 'live' or do i have to get another key ?

Thanks and sorry for the barrage of questions.

---

### Post by yancek on 2020-02-15
> will an install of ubuntu fix my cpu/mem capacity issues 

Not sure what you mean by 'fix' but software will not repair hardware.  You have a very small amount of memory for a current computer and adding more RAM might help.

> I'm presuming it'll fix my harddrive issues since ubuntu will take about 3GB to install and update ?
 

Not sure where you got  that info.  The install iso itself is around 2GB and a very basic install will be 7-8GB.  Recommended hardware at the link below.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

If you do manage to get Ubuntu installed, you should be able to access external drives and read/write to them.  You will need to learn about ownership and permissions of external drives.  Linux systems can access/read/write to windows filesystems but the reverse is not true.  If you want to use ethe Ubuntu install usb for data later, create a new partition table on the drive and format it first.

---

### Post by Impavidus on 2020-02-15
For regular Ubuntu your specs are a bit low, but you should be able to run one of the lighter flavours. If you keep your system lean, the OS with basic applications needs about 10GB of hard drive space and less than 1GB of memory. Use your other GB for the web browser. I don't know about drivers for specific hardware.

---

### Post by him610 on 2020-02-15
I looked up the specs for your machine and found,
> Windows 10.
11.6-inch HD 1366 x 768 resolution display.
1.6GHz Intel Celeron N3060 CPU.
Intel HD Graphics 400.
4GB RAM.
32GB eMMC flash.
802.11ac.
Bluetooth 4.0.

Xubuntu or Lubuntu would run satisfactorily on your machine *[COLOR="#B22222"]sans Windows[/COLOR]*. I have installed and run Xubuntu on lesser machines.

---

### Post by dbee on 2020-02-16
Afaik it's a 2 GB machine. At least that's what Task Manager is telling me ... with 29.1 GB storage.

It's a 'refurbished' model so maybe they took the 2 GB memory out somehow ?

Windows 10 only needs 2 GB to run on 64 bit.

I'll try a boot disk of xubuntu and see if that works ...

PS: I was going to post a screenshot of performance manager, but when i go to 'add image' it asks me for a url. So i can't post from the harddrive :-(

---

### Post by Impavidus on 2020-02-16
You can add pictures to your forum post as an attachment.

Ubuntu can read and write Windows filesystems (NTFS), but only if the filesystem is in a clean state. It cannot repair Windows filesystems or access a hibernated Windows partition. If you safely remove and unplug the external hard drive before shutting down Windows, it should work. But if you don't use Windows anymore, don't use Windows filesystems.

---

### Post by The Cog on 2020-02-16
It would be worth trying an Xubuntu live USB. The install USBs have a try before you install option. It will be slow to load because of USB throughput, but should give you a feel for how it performs once an app is loaded into memory, and answer your questions about the trackpad. In my opinion, unless you have hardware compatibility issues, Xubuntu should be OK though not lightning fast. My OS occupies around 5G of disk, though I don't install a great deal other than the default applications.

---

### Post by mastablasta on 2020-02-17
if you have 2 GB, then this is quite low. some of this memory is used by the GPU chip. i have a small HP laptops with 2 GB and 512MB of that is taken by the AMD GPU. so i have 1.5 Gb left. it has windows 7 starter on the other side. which is stupid because the Starter edition supports only 2 GB ram max, while the PC can actually take up to 8 GB ram.

anyway the other side of the drive is taken by Kubuntu, which used about 380 MB -450 MB ram on boot. this leaves about 1 GB ram for browser. it means i can't use too many tabs. but otherwise it works quite well and reasonably fast (it has slow HDD). i can even play some old games on it (Morrowind, Minecraft...). what i am trying to say it's the apps that eat ram not OS and if you can add a 2GB stick it would benefit your experience. however this migth be expencive and a better used  laptop might be cheaper. Kubuntu also has an interesting install option that will install the OS only with only basic apps. new KDE Plasma desktop can be quite fast. that old PC boots in 56 seconds. compare to about 9-10 minutes of windows 7 boot time on the same machine... and let's not even start talking about that automated "antimalware" service running like crazy for the first 30-45 minutes after Windows boots.

however, Xubuntu is also a good option for this machine and highly and easily configurable. if you need something even lighter then MX linux and AntiX linuxis worth looking at.

Operating system is small and again it's the apps that take the hard disk. so it depends what you need and what you plan to install. i added osme games so the root folder with apps and all that is about 18 GB. but i did install XFCE desktop only with basic apps and browser using minimal install and it took just over 6GB. with some normal use i would say system needs about 12 GB and in your case you will need space for swap partition or swap file (like pagefile in windows). so overall you will have about 15 GB left for data. this could be increased with SD card or external USB key or external hard drive.

before you install use a live USB boot to check if everything works.

---

### Post by oldrocker99 on 2020-02-17
There are even lighter distros than Lubuntu (this list does include Lubuntu). Here's a list.
[https://itsfoss.com/lightweight-linux-beginners](https://itsfoss.com/lightweight-linux-beginners).

---

