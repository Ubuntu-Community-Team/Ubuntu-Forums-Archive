---
title: "Please hep to decide on version and how to get started"
date: 2012-03-01
forum: New to Ubuntu
---

### Post by mashavecher on 2012-03-01
Hello.
  Going through software for phylogenetic tree building I've chosen ARB which is designed for linux. It can be run on OSx, but mailing list reports many issues. Anyway, much useful biosoftware is linux based, so I came to point where I've decided to buy separate computer for all the stuff I need. I've chose ubuntu because it is recommended for linux newcomers and ARB developers support it.
  I'm looking at Toshiba Satellite with i7-2670QM. I plan dual-boot (windows 7 preinstalled), reading through partitioning at the moment.
  My questions are: 1) have I chosen appropriate hardware ?
2) which version of ubuntu would you recommend?
3) will I be able to use wireless (WiFi 802.11b/g/n)?

Yes I am just a user, but learn fast. No, I can't get geek to help me (surrounded by microbiology and molecular biology people, this is my first ever post actually).

I'll study hard just please direct me

Thank's

---

### Post by Lars Noodén on 2012-03-01
2) I would recommend looking at Kubuntu or Xubuntu first.  Use the live CD to get the feel of the distro.  I should point out that KDE is by far the most customizable.  You can burn the live CD images to CD RW and thus reuse the disc.  (I guess it's DVD RW now with the over-size images) Once you've tried the live CDs you can pick one and install it on the hard drive.

About dual boot, you might also look at running the legacy system inside a VM like in VirtualBox.  That will give you the advantage of snapshots.  When the system gets munged through bitrot, virus, or accident, you can just roll back to a clean snapshot and be going again in seconds.

---

### Post by Double.J on 2012-03-01
Hi there mashavecher, Welcome to the forums!

Having just returned to wikipedia a lot wiser on the meaning of Phylogenetics, to answer your question, it looks like Linux is the way to go as the ARB project design for Linux and then port to other OS. 

In terms of your hardware, it depends on the RAM - ARB recommend 4GB of RAM, and state that processor speed is not as important - so an i7 is far more than sufficient! (that machine should see you through a while!)

Ubuntu is a good choice, but bare in mind that there are binary packages for debian available should you encounter problems.

as this is obviously more than just a hobby machine, I'd recommend using 10.04 LTS and 32bit version - if you have more than4GB RAM this may seem wasteful, but I'm assuming you want the most stable? 64 bit shouldn't be too much of a problem if you do have 6 or more GB RAM however. (from what I can work out, ARB is 32 bit)

I would not recommend 11.10 however - it will be replaced in a month and a half, and you'd have to install all over again. Personally I'd download 10.04 and use that for a year before switching to 12.04.

Hope it helps!

---

### Post by mashavecher on 2012-03-02
The machine is packed with 4Gb RAM and it's cheaper to just change it to 8Gb (which is what I plan to do) then to buy one that has this much RAM from the box.
 ARB has 64bit version.

  Thank you so much.

---

### Post by mashavecher on 2012-03-02
I have one more question. Virtual box seems good option for me the only thing is ARB requires increased swap. Going through virtual box guides I can't figure out will I be able to set it.

---

### Post by col48 on 2012-03-02
re swap: Try looking in XP help as well - maybe you could change swap size in XP once you have it running in VM?  Long time since I've used Windows (long before XP) so I don't know.

Usual caveats when tinkering under the bonnet (US=hood) with the system.

---

### Post by mastablasta on 2012-03-02
virtual box will limit your ram. i mean your host system will use the ram and vbox (guest system) will again use it's own ram. for example i have XP with 2 GB ram and i can dedicate about 512MB to Vbox (maybe i could go up to 1GB) with out much performace loss. so the guest os in this case would only have 512 MB (1/4 of my RAM) available then...
 
since it seems you need as much ram as you can get and you also need something configurable Xubuntu is a very good option (it's a lighter Desktop environment and is more mature than Lubuntu). system itself will only use about 120-130MB ram. Debian XFCE will bring this down to 80-100MB.
Kubuntu (if you use lowfat package) would get ram consumption down to about 280MB on idle.
 
you do not need CD/RW to try them out you can use USB key for testing and trying. here is a nice programme for putting Linux ISO image on USB: [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)
Another nice one is Unetbootin: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by mashavecher on 2012-03-02
Thank you, links are very useful.

May be then I might still try to set up dual-boot? Instructions seem to be manageable.
I'm not in a hurry, so I can spend some time setting up everything correctly learn and prepare backups and recovery in linux and then get to one by one installing desired software. I guess 620 Gb hard drive is enouth to host two operating systems, especially considering that I don't keep almost any data on it placing it all on multiple USB sticks.

It's not that I really want to keep windows, but I'm planning to buy a separate new computer and deleting windows will affect warranty. Having windows may be useful sometimes, since I'm using MacBook and have to do some extra to make documents and presentations MS office friendly.

Tree building is heavy duty as well as sequence alignment, if hardware benefits from setting dual-boot it's worth trying.

---

### Post by 3rdalbum on 2012-03-02
Yeah, it sounds like you should just dual-boot for maximum RAM and performance.

No idea if the precise hardware in that computer is supported, but if you choose to run Ubuntu 12.04 then you maximise your chances of having everything work. If in doubt, take the 12.04 beta CD to the shop and ask if you can boot their display machine from the Ubuntu CD to check compatibility. In particular, check the wireless - maybe run your phone as a tethering hotspot so you can see if it works out-of-the-box.

Even if not everything works out-of-the-box it may be possible to get the rest of it running post-install anyway.

---

### Post by grahammechanical on 2012-03-02
The advantage of dual boot or triple boot for that matter is that whichever operating system you boot into will get full use of the hardware.

Each operating system takes up hard disk space and you can partition the hard disk so that data is on its own partition and can be read/accessed from either  OS. With plenty of hard disk space dual booting is not a problem at all.

I have four versions of Ubuntu on my hard disk (250GB) for experimenting and one of them is in 10GB partition. I would say that if you are not storing too much data/documents on the hard disk but want to find out what Ubuntu can do, then a 10GB partition will be fine. Or 15GB or 20GB.

Regards.

---

### Post by mashavecher on 2012-03-02
I've managed to partition hard drive on my  asus (2007, Windows Vista) it was a bit scary, but went smoothly, now trying different distroes from CD. I'll take them to the shop, hope they'll let me try.

Thank's

---

