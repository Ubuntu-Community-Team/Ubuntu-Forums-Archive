---
title: "[SOLVED] Is there a way to safely try out or dual Linux distros?"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by Dani Filth on 2008-07-10
Hi folks,

I'm quite getting used more & more to the *buntu distros, thus, I wanna try out other different distros, but I wonder if there is a way to safely try them out without damaging **too much** to your system/PC (I do backing-up my data, of course). LiveCDs are ok despite being slow, but I reckon LiveCDs themselves lack of some certain features compared to the full/fresh installation.

Normally, I would let the installation do its job by choosing to install "automatically" or "use the entire disk", but this leads to re-formatting the disk again & again. (Do I get this right or it just removes the current system and "replace" with the new one - like one of Fedora installation option?)

Any tips that you folks can suggest me? Thanks in advance :D

---

### Post by purplepaint on 2008-07-10
I've tried out a lot of Distros using VirtualBox.  That way, you won't change anything about your existing OS.

---

### Post by Troll_the_Great on 2008-07-10
I would say to create a separate partition (about 15 GB should be enough) and install whatever distro you want.This way you can keep a permanent linux installation and try out as many as you want, without the need of formating your entire disk.By the way, what distro do you have at the moment and what are you wanting to try?

---

### Post by Elfy on 2008-07-10
I tend to run them in a vm first - then if I decide I might be a bit more interested only then run it from it's own partition - I have a couple just sat there, one will get intrepid shortly (again :) )

But to get the full 'thing' the only real way is to install them as you say.

They will all, or at least the ones I've tried, have a manual partitioner of some sort - so I would use a prtition editor to resize and make partitions, then you have one to use for them.

---

### Post by Dani Filth on 2008-07-10
Thank you guys for your suggestions! :popcorn:

> **Troll_the_Great said:**
> By the way, what distro do you have at the moment and what are you wanting to try?
I have Ubuntu 64-bit on my desktop, Xubuntu i386 on my laptop. There are many interesting distros which I wanna try : Fedora, openSUSE, Mandriva, Gentoo. I would try them on my laptop so probably I prefer XFCE edition more :D, ZenWalk is another one that I wanna try out.

I've read some reviews, they say that in the year 2008, Mandriva 2008.1 seems to be better than other distros, ZenWalk is one of the best XFCE distros, openSUSE may be a bit hard to deal with, Gentoo which users need to build everything themselves, but hey, like I said, I wanna try out to see which distro fits my needs the best.

In this case, if I give the new distro a separate partition (about 15GB) then if I don't like it or I wanna install a different distro, do I have to format that partition or just use GParted to erase that partition then install the distro on it?

Cheers! :guitar:

---

### Post by Troll_the_Great on 2008-07-10
> In this case, if I give the new distro a separate partition (about 15GB) then if I don't like it or I wanna install a different distro, do I have to format that partition or just use GParted to erase that partition then install the distro on it?

When you install a distro choose manual partitioning and then choose that partition for boot ( the "/" partition).You should have a box that says "Format Partition".Check it and when you install the new distro you will also format the partition.Good luck with your experiments and tell us the results.:)

---

### Post by AndyCooll on 2008-07-10
> **forestpixie said:**
> I tend to run them in a vm first - then if I decide I might be a bit more interested only then run it from it's own partition - I have a couple just sat there, one will get intrepid shortly (again :) )

But to get the full 'thing' the only real way is to install them as you say.

They will all, or at least the ones I've tried, have a manual partitioner of some sort - so I would use a prtition editor to resize and make partitions, then you have one to use for them.
If you're going to try out lots of distros, unless you have a test machine, this is the best method. Virtual machines (e.g. VirtualBox, VMware, Qemu, Xen etc) run within your current session, no need to continually reboot etc and you can quickly try lots of them.

You can go along the "full thing" route each time if you like, but it becomes a chore after awhile. Continuing forestpixies suggestion,I'd suggest you only do a full install of the distros that you truly want to investigate further. Use a VM first, that way you're not wasting your time doing a full install of a distro that has no appeal to you.

:cool:

---

### Post by Canis familiaris on 2008-07-10
Use Virtualbox. It is stable and easy to use. However sadly you cannot use Virtualbox for 64bit OS.
If dont know whether VMWare supports 64bit guests but I have tried 64bit OS using KVM.

---

### Post by Dani Filth on 2008-07-10
Thank you guys again :popcorn:

I've checked several distros, and here's what I got if anyone may be interested in various distros :guitar: 
(this is just my own thoughts)

**Mandriva**
I tried Mandriva 2008.1 XFCE, quite ok, it loads fast, it detects all my hardware, wireless works but I couldn't play any mp3 songs or avi videos even though I installed the Official media and PLF media from easyurpmi.zarb.org - not sure if this is caused by XFCE, I haven't tried the official KDE edition. Another drawback that happened to me is occasionally, when I plugged in the USB drive, sometimes all the icons on the desktop disappear and I need to reboot in order to get them back.

One thing occured during installation is at the last or second last step, a screen with all French appeared which I don't understand at all because I know nothing about French language so I just chose the default option - still hasn't known what I got there.

Their forum, ugh, I don't like yellow & orange which are the colors they use. And they don't seem very lively compared to Ubuntu forum.

**Fedora**
Fedora 9 is a bit plain IMO. Everything is so-so. Fedora doesn't have XFCE edition at the moment so I checked out the GNOME version. But it seems that the sound quality is no good compared to Ubuntu. And "su -" is different from "su".

**ZenWalk**
ZenWalk seems fine. It has flash, codecs pre-installed. So videos, mp3s and flashes while surfing are all played well. It runs pretty fast too. However, it package manager "netpkg" is a little hard to deal with. Instead of fully install the related packages, it asks the users to step-by-step install it. Perhaps experienced users may like this as they will know what is going on. Moreover, "netpkg upgrade" which upgrades the whole system doesn't upgrade the kernel, you need to upgrade the kernel by yourself.
There's a slight difference between ZenLiveCD and Zen Standard Edition/Installation.

ZenWalk lacks of some common features such as VLC, msttcorefonts etc.

And their forum isn't very active, in my opinion.

**openSUSE**
I haven't tried it properly yet, the openSUSE 11.0 KDE LiveCD took so long to boot on my laptop and eventually got stuck somewhere with the black screen. If I put the LiveCD in my desktop then it loaded but I haven't had time to try it much.
There's no XFCE LiveCD yet.

**Gentoo**
I haven't tried Gentoo 2008.0.

None of those that I tried failed to detect my hardware yet.

But after all, none of those communities can ever compare to Ubuntu's. The community here is the best :guitar:

If you have experienced those distros, please feel free to give more comments. :D

---

### Post by markbuntu on 2008-07-10
I just put my different distros on different hard drives, they are so cheap and it is so easy with SATA and avoids so many potential problems. 

The time/money equation leans heavily towards this solution for me. $30 for a hard drive or 6-12 hours rebuilding a wrecked distro.

---

### Post by TrashmanL on 2008-07-14
I have a related question. When doing these multiple distros, are you using the same swap space for all of them? I ask because on my main desktop, I originally had a Slackware installation. My original plan was to install Dapper on a separate partition before changing over. I had already partitioned my drive the way I wanted it, but it didn't let me use the same swap space. The install insisted on making another swap partition. In the end, I ended up making one big / partition and installing Fiesty. 

I'm asking because I want to upgrade it to either Gutsy or Hardy, and I wanted to do a similar thing, putting the new distro on a different partition before deciding on making it the main distro on my machine, but I think it's silly to use up another 2GB of swap space. From my experience, the Fiesty installer was much better than Dapper, so I'm thinking I won't have the same problem, but I just thought I'd ask someone who's done this.

---

### Post by lazyart on 2008-07-14
> **TrashmanL said:**
> I have a related question. When doing these multiple distros, are you using the same swap space for all of them? I ask because on my main desktop, I originally had a Slackware installation. My original plan was to install Dapper on a separate partition before changing over. I had already partitioned my drive the way I wanted it, but it didn't let me use the same swap space. The install insisted on making another swap partition. In the end, I ended up making one big / partition and installing Fiesty. 

I'm asking because I want to upgrade it to either Gutsy or Hardy, and I wanted to do a similar thing, putting the new distro on a different partition before deciding on making it the main distro on my machine, but I think it's silly to use up another 2GB of swap space. From my experience, the Fiesty installer was much better than Dapper, so I'm thinking I won't have the same problem, but I just thought I'd ask someone who's done this.

In the future create a new thread for your question.
You can use the same swap for the distros you install.  Nothing useful is left there after rebooting.  Just select the partition and tell the installer to use it as swap.

---

