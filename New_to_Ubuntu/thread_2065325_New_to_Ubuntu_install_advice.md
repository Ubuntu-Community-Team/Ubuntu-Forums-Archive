---
title: "New to Ubuntu install advice"
date: 2012-10-01
forum: New to Ubuntu
---

### Post by Rover2000 on 2012-10-01
Hi all, 
I have just registered here and am hoping for some advice.
I am a long time computer user but have almost always used windows from way back starting with windows 3 and dos 6.
I am a pretty fast learner but I have no Linux experience other than web servers and hardware.

After reading up a little I thought that Ubuntu seemed the best OS to take my leap into Linux , I have downloaded the 64 bit desktop option and will be doing a clean install onto a raid 0 using 2 SSD's.

Before I reformat my drives and wipe out windows, is there anything else I will need to download other than drivers, to give me the best start in Linux.

Many thanks in advance.

:guitar:

---

### Post by critin on 2012-10-01
>  hoping for some advice.

Hello, welcome!

I'm sure you know yourself well, but quitting Windows cold turkey is drastic.  Separate hdd or dual boots are easy to do.  :p

Follow instructions during the install and you'll be fine.  Oh, if you can, install using a wired internet.  Wireless installation is iffy because it tends to drop off during critical times.

---

### Post by The Cog on 2012-10-01
Try the live CD for hardware compatibility. You shouldn't need to download extra drivers first.

---

### Post by Mark Phelps on 2012-10-01
> **Rover2000 said:**
> ... 

Before I reformat my drives and wipe out windows, is there anything else I will need to download other than drivers, to give me the best start in Linux. :guitar:

Yes ... the first thing you need to find out is how well your PC actually runs Ubuntu.  Drivers for MS Windows are a given -- especially since so many PCs come with MS Windows preinstalled.  Linux OSs are not so common.

So, boot from an Ubuntu LiveCD  or LiveUSB, choose the Try Ubuntu option -- and see how well Ubuntu detects all your hardware and installs all the drivers.

Linux is not MS Windows -- you don't just download and install drivers.  Anything that does not work in LiveCD/LiveUSB mode is going to range from easy to impossible to fix.  Better to find out what does NOT work before you wipe Windows from your PC.

---

### Post by Frogs Hair on 2012-10-01
Make sure you don't need Windows for anything before wiping it out.
Dual booing is an option also . You may want to look here also.  [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

### Post by offgridguy on 2012-10-01
Hi Rover2000;  If I may just throw my hat in here as well,,I agree with the previous advice
about dual booting, or not wiping out your windows until you are sure ubuntu will do 
everything you want.  Depending on what software you use and programs you run you 
may find / make that will find some compatibility issues.  In my own case I have found
ubuntu cannot entirely replace windows,  this is mostly in regard to third party software
that wont work on a linux system.

---

### Post by AndyOpie150 on 2012-10-01
Maybe you could tell us what Manufacturer, Model, year, size of RAM, Hardisk (or Disks) size, what wireless card manufacturer and model (if any) or wireless driver manufacturer. 

Most of the issue's I've seen are wireless drivers, and RAM and Disk space. If you have at least 1GB RAM and 70-100 GB hard drive then Kubuntu (All the bells and whistle's but without the annoying Unity desktop environment) and Ubuntu (I opted to install the Gnome classic desktop environment) would be a good choice. Anything less and Lubuntu and Xubuntu depending on the size.


Penndrive Linux has a utility that will format,configure and install one of almost 200 linux distros onto a USB drive. It also has a version that will configure for a live .iso. I personally like this the best for portability with the added plus that I can leave it in the machine and transfer anything back and forth between my Windows OS and my Ubuntu distro super easy. As I add to my Ubuntu distro I just copy and paste to the Ubuntu folder on the USB drive. If I ever mess up my distro I just go back and install it and all the packages that I saved (all from in one place).



The wireless might be the hardest thing to get up and running, but it's pretty easy and there are two or three methods if you drivers aren't auto recognized (kind of hard to get every single wireless driver to  be recognized)

The best way to install is with a live version on a CD or USB drive. This way you can see what problems you might encounter and be prepared for them on install.

Another good idea is to make a boot repair CD just in case. The info can be found here: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you have multiple hard drives you can install Ubuntu on one and leave Windows on the other. If you have a single then you can dual boot Windows and Ubuntu. I opted for this because I have several things that will only work in Windows (even Wine didn't work on them)

---

### Post by newb85 on 2012-10-01
I would also strongly urge you to start dual-boot (separate hd partitions), provided you have the space.  How large are those two SSDs?

---

### Post by Rover2000 on 2012-10-02
Hi thanks for the replies, I was hoping to be able to do without windows but most of you think that I will need to keep it. I don't really play many games and use it mostly for downloading from a news service and photo editing / printing.

My set up is quite high end ( or was when I built it 3 years ago, lol )

Everything is mounted in a mountain mods double width case.

I have a dual loop water cooling system one loop for CPU and north bridge the other for my 2 ati 3870x2 graphics cards running quad crossfire.
The mobo is an asus rampage 2 rog.
My CPU is an intel 920 d0 running stable at 4 ghz , I have 6 gb trident triple channel ddr3 ram running at 2003 MHz .
There are 2 DVD rewriters one is lightscribe the other is lableflash.
I have 5 hard drives 2 SSD's each 128 gb in raid 0 , 2 wd velociraptors each 150 gb in raid 0  and a 7200 rpm 750 gb drive that I just use for backups and games.
I don't use wifi on this computer I use the built in gigabit LAN .
The on board sound is sound blaster x-fi.

I think that's everything, it runs windows 7 well but I really was hoping that Linux would be faster and give me a new learning experience :)

---

### Post by sandyd on 2012-10-02
> **Rover2000 said:**
> Hi thanks for the replies, I was hoping to be able to do without windows but most of you think that I will need to keep it. I don't really play many games and use it mostly for downloading from a news service and photo editing / printing.

My set up is quite high end ( or was when I built it 3 years ago, lol )

Everything is mounted in a mountain mods double width case.

I have a dual loop water cooling system one loop for CPU and north bridge the other for my 2 ati 3870x2 graphics cards running quad crossfire.
The mobo is an asus rampage 2 rog.
My CPU is an intel 920 d0 running stable at 4 ghz , I have 6 gb trident triple channel ddr3 ram running at 2003 MHz .
There are 2 DVD rewriters one is lightscribe the other is lableflash.
I have 5 hard drives 2 SSD's each 128 gb in raid 0 , 2 wd velociraptors each 150 gb in raid 0  and a 7200 rpm 750 gb drive that I just use for backups and games.
I don't use wifi on this computer I use the built in gigabit LAN .
The on board sound is sound blaster x-fi.

I think that's everything, it runs windows 7 well but I really was hoping that Linux would be faster and give me a new learning experience :)

Alright.
If you want to check if all your hardware is compatible, head over to [http://ubuntu.com](http://ubuntu.com) , download the ISO, and [check the md5sum]("https://help.ubuntu.com/community/UbuntuHashes") You could just use torrents to download Ubuntu as well, under 'Alternative Downloads'. The torrent client does automatic hash checks, so you don't need to run md5 to make sure you don't have a corrupted iso.

After burning the iso to a cd/dvd, boot it up on your computer (you might need to change your boot order to cd first, or press a key to set what to boot from), and choose "Try Ubuntu".

The Ubuntu disc will not make any changes to your system, and will instead load Ubuntu into your RAM. This allows you to test if all the hardware is compatible.

Good luck!

---

### Post by PryMaL on 2012-10-02
Welcome to Linux!  :-)

First thing you should do is ensure there's nothing tied up on the Windows world that you simply cannot do without.  If there is; Dual boot, separate hdd or even booting from a USB drive to learn about linux is certainly an option.

I'd suggest realistically, unless you're a hardcore gamer that Ubuntu will certainly suffice your needs day to day and if there's not a like for like option with programs that there will certainly be a similar alternative.

---

### Post by Rover2000 on 2012-10-02
Hi again, 
Thx again for the advice so far,
I have downloaded abuntu onto a cd ( the 64 bit desktop ) but mostly what I want to know is what other program's and apps I will need.
I have read that I need wine to run some windows apps and what is kubuntu compared to Ubuntu ? I know that I can read up on all of this but I find that first hand experience is far better, as others have already made the mistakes that we all can learn from.
I would therefore love a list of the addons I might need for my Linux setup, such as wine, gnome, etc, etc.
Also the last time I tried Linux was a red hat server, I could not get along with it at all, mainly because it seemed to have many different desktops. Is this the norm with Linux, or does Ubuntu just use gnome ?
Again what is the difference between Ubuntu and kubuntu.
Thank you again,
Clayton.
:popcorn:

---

### Post by sandyd on 2012-10-02
> **Rover2000 said:**
> Hi again, 
Thx again for the advice so far,
I have downloaded abuntu onto a cd ( the 64 bit desktop ) but mostly what I want to know is what other program's and apps I will need.
I have read that I need wine to run some windows apps and what is kubuntu compared to Ubuntu ? I know that I can read up on all of this but I find that first hand experience is far better, as others have already made the mistakes that we all can learn from.
I would therefore love a list of the addons I might need for my Linux setup, such as wine, gnome, etc, etc.
Also the last time I tried Linux was a red hat server, I could not get along with it at all, mainly because it seemed to have many different desktops. Is this the norm with Linux, or does Ubuntu just use gnome ?
Again what is the difference between Ubuntu and kubuntu.
Thank you again,
Clayton.
:popcorn:
Kubuntu and Ubuntu are the same - except that they have a different desktop environment. Ubuntu uses unity, and Kubuntu uses KDE. There a lot more desktop environments - cinnamon, mate, openbox, xfce, lxde, .etc .etc and they all look and function differently. Ive found that testing them helps in the choosing section.

---

### Post by mansonfan78 on 2012-10-02
As for additional things to install after installing Ubuntu - number one would the ubuntu-restricted-extras package which includes codecs for many audio and video formats (without it you won't be able to listen to mp3s).  I also recommend Synaptic Package Manager, ubuntu-tweak, Bleachbit, and VLC media player.  And be sure to browse through the software center as there are a lot of apps that might interest you.

---

### Post by daslinkard on 2012-10-02
When I first came over to Linux one of the articles that interested me was something like 15 Things I Did After Installing Ubuntu 11.10....here's the [link]("http://www.techdrivein.com/2011/10/15-things-i-did-after-installing-new.html") so you can get other ideas.

---

