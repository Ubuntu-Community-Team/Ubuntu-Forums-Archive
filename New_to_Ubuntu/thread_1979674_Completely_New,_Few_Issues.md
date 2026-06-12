---
title: "Completely New, Few Issues"
date: 2012-05-13
forum: New to Ubuntu
---

### Post by SirMortus on 2012-05-13
I recently decided to try Ubuntu and I managed after a lot of trial and error and forum browsing to get it to load but I still have issues I was hoping I could get some help with. I'll try to give as much information as I can as I am very interested in learning Ubuntu and seeing what all it has to offer in return. 

Okay onto my issues:
- Ubuntu normally does not boot. I downloaded the 64-Bit Torrent ISO and burned it onto a disk. Then preceded to reboot and hit F12 to 'Boot Options' -> 'Boot From Disk'. The computer then boots to the Ubuntu Logo menu with four loading dots under it. I use to let this continue but it would go to the login screen then freeze with just the wallpaper after this (no taskbar or anything). I decided to try the alternate menu at load and selected 'Advanced Options' -> 'nomodeset' and it actually loaded up, very, very slowly. (I did not install Ubuntu by the way, I am trying it from the disk first as I need to learn how to install it properly).
- I also ran the Disk Check from this menu and it said it finished with one error, then to press okay to reboot. (I don't know how to see what the error is.)

I could use help with these issues. Here is my PC information:
Memory 5.6GB (Not sure why it's this number instead of 6GB)
AMD Phenom(tm) II N870 Triple-Core Processor × 3 
Usual OS is Win7 64-Bit
Disk 6GB (Guessing the Disk for Ubuntu?)
Radeon HD4200
500GB Hard Drive

Any other information just ask.

Thanks for taking the time to read this, 
SirMortus

---

### Post by SirMortus on 2012-05-13
Also I am wanting to install this so I can either use Win7 or Ubuntu since I am very familiar with Win7.

---

### Post by Lisiano on 2012-05-13
Did you try the "Install Ubuntu" or "Try Ubuntu without Installing" after picking nomodeset? Also try loading without nomodeset the "Try Ubuntu" option.

Can you tell us what GPU you have?

FYI: 5.6GiB, normally you see it as GB or Giga Bytes (Or multiple of 1000) while normally our systems show Gibi Bytes (Or multiple of 1024). More info on it here [http://en.wikipedia.org/wiki/Gibibyte](http://en.wikipedia.org/wiki/Gibibyte)

EDIT: There is an edit button near your posts, use it to add information to your last post if no one posted after you yet, keeps stuff clean.

---

### Post by SirMortus on 2012-05-13
I selected the Try Ubuntu Without Install for now as I wanted to learn how to properly install it first to have both Win7 and Ubuntu on my laptop.
If GPU is my graphics I believe it's a Mobile Radeon HD4200

When I tried using the Try Ubuntu Without Install with no 'Nomodeset' selected it hangs at an empty wallpaper.

---

### Post by Lisiano on 2012-05-13
Strange. Your GPU should work fine with Ubuntu. Though I'd say install Ubuntu while having nomodeset on, performance is always better when not using the LiveCD.
Here are 2 articles that will help you install Ubuntu and understand the process better
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by SirMortus on 2012-05-13
Thanks for the help. By the way, what exactly does 'nomodeset' do?

---

### Post by JKyleOKC on 2012-05-13
Accurately answering your question about what "nomodeset" does is going to be almost impossible without getting into lots of deep technical detail, but I'll try to give you an overview.

Up until a year or so ago, maybe two, the video drivers handled lots of little details to make the displays work properly -- but there wasn't any standard way for them to do so. Each different manufacturer's drivers did things in their own way. This required that the video configuration files iron out those differences so that the kernel could send data out to the screen in a standard fashion -- making said files a critical point in setting up a system.

Then the kernel developers found ways to handle things inside the kernel code itself, eliminating (or at least reducing) the configuration file bottleneck. Those changes went into the kernel (which is the heart of the system) -- and we all promptly discovered that while they worked for the majority of video systems, they did NOT work for all of them. It's quite likely that your system is one of those on which the changes don't work properly yet.

That's when they introduced the "nomodeset" command, which tells the kernel to ignore these changes and just do things the way it did before the changes were added.

Development continues on the video code changes, and everyone hopes that "nomodeset" won't be needed much longer. However, at present it solves many mysterious problems, by forcing use of the older approach.

I hope this helps a bit. Entire books have been written about the intricacies of video driver design, but fortunately most of us don't need to know all the details in order to use their result.

---

### Post by mastablasta on 2012-05-14
i hope you checked the md5sum to see if the download was good.
 
image on your computer has to be exaclty the same as it is on server.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
 
radeon 4200 should work fine. if you managed to get it and it was working slow (but working) then it means you need proprietary drivers. a reboot will remove them unless you are booting from USB key with persistance enabled.

---

