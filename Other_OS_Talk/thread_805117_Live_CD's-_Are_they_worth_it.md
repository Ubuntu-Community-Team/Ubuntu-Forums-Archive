---
title: "Live CD's- Are they worth it?"
date: 2008-05-23
forum: Other OS Talk
---

### Post by joshjani on 2008-05-23
I've been using Ubuntu for a while, and am pretty pleased with it, mostly because of this forum's support. Like many of us, I had trouble getting started, and am still a relative noob, so having so many folks involved on this board is immensely helpful.

Ubuntu has piqued my interest in Linux and some other free distros, so I've downloaded several- Puppy, OpenSUSE, Knoppix, and Freespire. I use Live CD's to get a feel for them, but I am disappointed that really that's all I can get- a "feel". Never have I used one that works with wireless networking, for instance. I assume it's because I'm not actually installing, so can't really detect and configure the hardware. OpenSUSE comes close- tells me I need to get a firmware for my Broadcom AirForce card...Don't know how to tackle that right now...that's for another post, I guess.

Anyway, I'm looking for a way to test and enjoy other distros, but Live CD's aren't cuttin' it. Any thoughts?

JC

---

### Post by cardinals_fan on 2008-05-23
Have a spare partition and install them.  You can also use virtual machines (such as VirtualBox and VMWare) to test distros inside Ubuntu, but some distros won't work properly.

---

### Post by boyce1 on 2008-05-23
Wubi is pretty useful if your looking to install an ubuntu-based distro on a windows pc. Partitions are automatically made, and bootloader corrected, so you can choose at startup which OS to boot in. If you don't like ubuntu, you can remove from add/remove in control panel and it will be back to normal.

Another way to 'test' out Linux is to make another partition on your harddrive, using software such as Gparted. You can resize current partitions without corrupting data, and create new ones, as big as you want. You can then install an OS on that partion, and have the ability to boot into it by slightly modifing your Grub boot menu. Search google to find a few tutorials on how to do this, it's generally a step-by-step procedure.

Personally, i think of LiveCD's to be an invaluable tool. They let you test out an OS. Think about what your doing, your running a fully functional Operating System from a simple CD, and it runs at a fairly impressive speed. I think thats a pretty cool thing, nothing of the sort is offered by Windows. 

Also, LiveCD's are extremely useful in the case of a bootup problem, where you can't access your harddrive due to the inability of getting into your system. You can access your files through a LiveCD, this has saved me many times :). I advise keeping a LiveCD version of any installed Linux distro, for backup help.

Of course, theres some things a LiveCD can't offer you. For example, you wan't to install your restricted drivers and see if they work, but it requires a reboot. Things like this can't happen (as far as i know), but generally a LiveCD will give you as many functions as a regular install.

Overall, like i said, LiveCDs are infact very useful in both testing and fixing an Operating System. So, in my opinion, they defiantly are 'worth it'. :)

---

### Post by Barrucadu on 2008-05-23
LiveCDs are very useful. I just rescued an unbootable Arch with the Xubuntu LiveCD.

---

### Post by joshjani on 2008-05-23
OK, I see your point of the value, and I really love the IDEA of my whole OS on a CD, or having something like Puppy on a thumb drive, so's I can play Linux in any machine...But practically, that doesn't seem to work, really. My specific example of the Braodcom card wireless card again...How would I go about configuring that for internet use when I run a live CD, or from a thumb drive? If I need firmware and an app to extract that, etc, can I carry that around on said thumb drive and make it work? 

I may indeed make a partition or two to allow me to play around...I really like Freespire, and would love to configure it properly and make use of it. 

Which brings me to another question- Freespire is "based" on Ubuntu, but what exactly does that mean? On the website it says that you use the Ubuntu repositories- is that for apps, desktop environments, updates? How closely related are Ubuntu and Freespire? Can I still hang out and get help here if I'm a Freespire user?:confused:

---

### Post by gameryoshi600 on 2008-05-23
Heck. YES!

---

### Post by pawnrocket on 2008-05-23
I know this is an insane idea, but wouldn't it be nice to simply "test" Ubuntu over a Terminal Server service. "Hey come test ubuntu, network boot right into it. No downloads! No installs! Just Ubuntu!" 

Every hour or so the OS image on the Server could be replaced with a fresh copy and that way no one would make a permanent home out of the service.

Its insane, I know.

---

### Post by LaRoza on 2008-05-23
> **joshjani said:**
> I've been using Ubuntu for a while, and am pretty pleased with it, mostly because of this forum's support. Like many of us, I had trouble getting started, and am still a relative noob, so having so many folks involved on this board is immensely helpful.

Ubuntu has piqued my interest in Linux and some other free distros, so I've downloaded several- Puppy, OpenSUSE, Knoppix, and Freespire. I use Live CD's to get a feel for them, but I am disappointed that really that's all I can get- a "feel". Never have I used one that works with wireless networking, for instance. I assume it's because I'm not actually installing, so can't really detect and configure the hardware. OpenSUSE comes close- tells me I need to get a firmware for my Broadcom AirForce card...Don't know how to tackle that right now...that's for another post, I guess.

Anyway, I'm looking for a way to test and enjoy other distros, but Live CD's aren't cuttin' it. Any thoughts?


If you have the RAM, virtualbox. If you have the time, just install it.

---

### Post by handy on 2008-05-23
> **Barrucadu said:**
> LiveCDs are very useful. I just rescued an unbootable Arch with the Xubuntu LiveCD.

I agree, LiveCD's can save so much time when you need to repartition a drive - the Gutsy LiveCD with GParted is better than Knoppix in my experience.

I have used the Arch install CD multiple times to chroot into a non booting system & edit config' files, xorg.conf whatever.

LiveCD's are wonderful.

---

### Post by handy on 2008-05-23
> **joshjani said:**
> OK, I see your point of the value, and I really love the IDEA of my whole OS on a CD, or having something like Puppy on a thumb drive, so's I can play Linux in any machine...But practically, that doesn't seem to work, really. My specific example of the Braodcom card wireless card again...How would I go about configuring that for internet use when I run a live CD, or from a thumb drive? If I need firmware and an app to extract that, etc, can I carry that around on said thumb drive and make it work? 

I have had no need to explore the situation, though it is my understanding that you can set up a Linux distro' in such a way that you can transfer it to your thumb drive.

Which would of course solve your internet problems for any & all hardware that your setup has drivers for.

I would think that you could make a very portable & useful thumb-drive in this fashion.

If you have a search around on DistroWatch.com I expect that it has already been done in a very portable fashion & still using Firefox.

If you had the desire, you could set up Arch, which is lite & fast, then build all of the available LAN & W-LAN drivers into it & configure it to suit your purposes.  Quite an interesting project I would think, you will get great help on the Arch forums too.  If you were interested you could go fishing for advice there.

---

### Post by wolfen69 on 2008-05-23
except for things that  require reboot such as video drivers, you can install apps and do anything you can like a real install. live cd's are awesome.

---

### Post by kagashe on 2008-05-24
Puppy is wonderful Live distro and works out of the box for most hardware.

You need to set up any net connection (even eth0 through dhcp) but the GUI is very simple.

Did you try the wireless card through the network wizard?

kagashe

---

### Post by DreamcastJack on 2008-05-24
I use Puppy as a LiveCD, and I love it!

---

### Post by lisati on 2008-05-24
> **pawnrocket said:**
> I know this is an insane idea, but wouldn't it be nice to simply "test" Ubuntu over a Terminal Server service. "Hey come test ubuntu, network boot right into it. No downloads! No installs! Just Ubuntu!" 

Every hour or so the OS image on the Server could be replaced with a fresh copy and that way no one would make a permanent home out of the service.

Its insane, I know.

Hey, that might work if you have a connection to a suitable server and the bandwidth and any other resources that might be useful to go with it.....

---

### Post by handy on 2008-05-24
> **pawnrocket said:**
> I know this is an insane idea, but wouldn't it be nice to simply "test" Ubuntu over a Terminal Server service. "Hey come test ubuntu, network boot right into it. No downloads! No installs! Just Ubuntu!" 

Every hour or so the OS image on the Server could be replaced with a fresh copy and that way no one would make a permanent home out of the service.

Its insane, I know.

> **lisati said:**
> Hey, that might work if you have a connection to a suitable server and the bandwidth and any other resources that might be useful to go with it.....

The world is heading in that direction, as new network technologies are implemented, more software will be housed on servers that some hosts will charge for, other's won't. Adobe & Google are already fighting over that arena.  It is very likely the main reason why MS wants Yahoo.

There is certainly a foreseeable future where nobody installs applications on their own computers, they use hosted applications instead.

Personally I don't like that future scenario, I much prefer the ocean to be full of a great variety of little fish.

---

### Post by sujoy on 2008-05-24
really for all linux users, its imperative to have a live CD for instances when the system refuses to boot. 

other than that a separate partition to install the distros is IMO the best way to test them, rather than a 1hr live session

---

### Post by SunnyRabbiera on 2008-05-24
> **sujoy said:**
> really for all linux users, its imperative to have a live CD for instances when the system refuses to boot. 

other than that a separate partition to install the distros is IMO the best way to test them, rather than a 1hr live session

Perhaps, but lives have their purpose.

---

### Post by smoker on 2008-05-24
live cds are great for giving you that quick first impression of what the distro is all about, as well as seeing if it suits your needs, and hardware. if you decide you like it, then do an install, if you don't, bin the cd and move on to the next, you've only wasted a little time, and committed yourself to nothing!

---

### Post by Cap'n Skyler on 2008-05-26
[http://www.frozentech.com/content/livecd.php:popcorn:](http://www.frozentech.com/content/livecd.php:popcorn:)
live cd's rock!! try these too !!

---

