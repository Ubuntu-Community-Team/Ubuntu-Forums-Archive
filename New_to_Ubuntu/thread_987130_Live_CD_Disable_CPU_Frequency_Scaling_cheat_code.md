---
title: "Live CD Disable CPU Frequency Scaling cheat code"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by dkaddict on 2008-11-19
I am having trouble getting any Ubuntu live cds to work on my machine. I either get a black screen with Gnome or KDM running in the background or, if I try Safe Graphics mode, KDM or Gnome almost get to load but crash and I get an error message about it being unable to create a file for CPU Frequency Scaling support because my notebook doesn't have that technology. I can get around this with cheat codes on other live cds but can't find any for Ubuntu. I Sabayon it is just 'nofreqscaling'. Can I use that with Ubuntu 7.10 or not? Surely there is a cheat code list for Ubuntu live cds, I can only find a few?

Please help, I have been trying to upgrade from Feisty for ages now but can't get a live cd to load and can't do an upgrade so it has to be a fresh install!

Cheers for any help.

JahGuide

---

### Post by Dedoimedo on 2008-11-19
Hello,

While booting, edit the grub menu and try specifying in the kernel line noapic or apic=off. See if this helps.

Don't edit the grub config file permanently until you're sure this works. Backup your data.

Dedoimedo

---

### Post by dkaddict on 2008-11-19
I already have that /boot/grub/menu.lst file edited with 'noapic' on my Fesity install. Are you saying that I can use 'noapic' as a cheat code on the live cd boot prompt? I need the cheat code to stop the live cd from trying to load CPU Freq Scaling support when it boots. As I said above, I think, the Sabayon live cd accepts 'nofreqscaling' to get around it.

I will try noapic!

Give thanks for your reply yeah. I well appreciate it. I don't want to have to go to another distro because of a Live CD.

It is stuff like this that inspires MS to make ads about 'life with no walls', which is a damn shame because the Ubuntu family of distros are so good once they are up and running. I bought my machine a few years ago. It isn't that old and was cheap so I expect they sold plenty of them. There must be a fair few people out there who tried an Ubuntu live cd but got the same as me. That can't be good for the image of Ubuntu because they claim that stuff like this is a thing of the past.

Peace

PS-Just tried 'noapic' and 'nolapic' as described on the live cd but I got the same result. Ubuntu gave me the black screen in normal boot and got caught in a loop when trying to load GDM. Kubuntu gives the blue screen and a cursor but crashes right at the last minute. I am going to have to try and burn a load more CDs. I will try 8.04 too. I must have burnt about 20 live cds so far. This is really hard work eh, unless you have a brand spanking high spec machine I suppose?

---

### Post by Dedoimedo on 2008-11-19
Try Xubuntu ...?
Dedoimedo

---

### Post by Tomatz on 2008-11-19
Just download the alternate (text based) .iso. Its just as easy to use as the live cd.

*(UK mirror, be sure to download the "alternate" NOT the "desktop" version)*

[http://mirror.ox.ac.uk/sites/releases.ubuntu.com/releases/intrepid/](http://mirror.ox.ac.uk/sites/releases.ubuntu.com/releases/intrepid/)

---

### Post by dkaddict on 2008-11-20
I am gonna have to get a load more blank cds and have another go at burning. I got hold of a load of boot codes but nothing made any difference. I have gone through a fair few CDs now so maybe my burner is faulty? The Kubuntu 7.10 and Ubuntu 7.10 Live CDs I have been getting the problems mentioned above with, however, have both passed the MD5 sum test every time I have tried it??? As it stands I've nearly given up. If the next 10 burns don't yield any success, I am calling it a day. I can't be going through all the hassle. Wasting so many CDs doesn't sit well with me either.

Bottom line: I need a hardware upgrade.

I did get longer out of this notebook than I would have if I had kept XP. I bought the laptop before I even had a clue about running any Linux distro so it was always going to have compatibility issues. It was a stunt learning everything I had to with no previous cli experience when I first installed Edgy, I was your typical point and click end-user. My only gripe is that it has become more difficult for me to sort out Ubuntu as the distro goes forward because hardware technology has moved on yet the software that works with my machine with absolutely no problems is on the Edgy and Feisty live CDs.

I haven't tried a Xubuntu7.10+ live CD yet, cheers for the idea. Will give that a burn too next, I haven't tried it so am hoping it will work. I do want to stick with Ubuntu somehow, I just like the way it works when it is up and running. It's the best way to run a computer for a user like me.

Cheers again

JahGuide

---

