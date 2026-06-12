---
title: "USB installer that works on Ubuntu"
date: 2011-11-18
forum: New to Ubuntu
---

### Post by shotgunxbaby3 on 2011-11-18
I'm looking for something similar to the Universal USB installer that works on Ubuntu. I'm trying to install Linux Mint and try that out, but the USBinstaller.exe doesn't work on ubuntu.

---

### Post by TeoBigusGeekus on 2011-11-18
unetbootin

---

### Post by shotgunxbaby3 on 2011-11-18
I'm using Ubuntu 11.10, forgot that bit. I downloaded the UNetbootin thing and it's wasn't in a format executable by Ubuntu.

---

### Post by TeoBigusGeekus on 2011-11-18
Try to search for it in the software centre.
If it isn't there, there is a linux version in Unetbootin's page.

---

### Post by Paddy Landau on 2011-11-18
Try the Startup Disk Creator, which comes with Ubuntu. I believe that Unetbootin no longer works with Ubuntu.

---

### Post by dniMretsaM on 2011-11-18
UNetbootin works fine on Kubuntu 11.10, not sure about Ubuntu though.

---

### Post by kurt18947 on 2011-11-18
> **dniMretsaM said:**
> UNetbootin works fine on Kubuntu 11.10, not sure about Ubuntu though.

Works fine with Ubuntu as well.  Unetbootin will now enable persistence.  I don't believe it had a capability previously.  And yes, mine came from the repos.

---

### Post by shotgunxbaby3 on 2011-11-18
Hmmm...maybe that's the issue i'm having with unetbootin. i found it on the software center and not it works, but i couldn't get it to work. i'll try startup disk creator tomorrow and see how that works.

---

### Post by shotgunxbaby3 on 2011-11-18
Startup disk creator= best answer

---

### Post by jjex22 on 2011-11-18
+1 Startup disk creator - native and what it's for!

of course the classic approach is to 

sudo dd if=/path-to-iso-image.iso of=/dev/location of usb key (usually /dev/sdb)

I'm not technical enough to know why but this no longer works for Ubuntu 11.xx releases, so I don't know if it's working for mint- just remember mint 12 is about to be released - looks very interesting to - no unity, but a sort of blended gnome 2 and 3 approach if the RC is to be believed.

---

### Post by beew on 2011-11-18
I highly recommend multisystem  [http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

It doesn't create live usb only for Ubuntu but many other distros as well, it also supports persistence if the distro's live image does  But the best part is that you can easily create a multiboot usb, i.e, a single live usb with several different Linux systems to choose to boot into.  These features  are supported by neither the Ubuntu usb creator(which only works on *buntus,--probably works on Mint too) nor unetbootin (which supports persistence only for Ubuntu)

The website is in French, but the download is actually in English (guess that depends on where you download from) Installing it will create an entry in your sources list so it will get frequent updates.

P.S. There is also a script called multi-iso or something like that on the forum that does the same thing, but it is buried somewhere deep in the forum, you can probably find it with a forum search

---

### Post by jjex22 on 2011-11-18
Just to clarify Unetbootin no longer works for ubuntu, this has been replaced by [univeral usb installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") - to be honest it's much better, so long as you're distro is supported - it is very irritating in that you can't just point an iso at it - you have to select the distro from the list. But a lot less buggy!

---

### Post by beew on 2011-11-18
> **jjex22 said:**
> Just to clarify Unetbootin no longer works for ubuntu, this has been replaced by [univeral usb installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") - to be honest it's much better, so long as you're distro is supported - it is very irritating in that you can't just point an iso at it - you have to select the distro from the list. But a lot less buggy!

What are you talking about??? The universal usb installer works only in Windows. It is an .exe file.

---

### Post by jjex22 on 2011-11-18
> **beew said:**
> What are you talking about??? The universal usb installer works only in Windows. It is an .exe file.

lol sorry you need to link my two posts - I meant that IMHO no reason to run unetbootin or usb installer in ubuntu, - im a serial disto junky and bewteen dd and the disk creator I've not had any problems. Sorry for confusion I should have just edited it in my OP!

---

### Post by beew on 2011-11-18
> **jjex22 said:**
> lol sorry you need to link my two posts - there's no reason to run unetbootin or usb installer in ubuntu, sorry I should have just added an edit to be clearer.

I am not sure if I understand. So if I am in Ubuntu and I want to make a live usb for Xubuntu, Mint or Fedora I have to boot into Windows? What if I don't have Windows? I am not sure if you can make a live usb with persistence with the dd command, I think you have to do something with the usb afterward depending on the distro, and with some you may have to install grub in it separately as well.

P.S. Unetbootin still works.

---

### Post by jjex22 on 2011-11-18
> **beew said:**
> I am not sure if I understand. So if I am in Ubuntu and I want to make a live usb for Xubuntu, Mint or Fedora I have to boot into Windows? What if I don't have Windows?

I would recommend using dd or disk creator, sorry my OP on this was on page one - sorry if I'm being confusing!!

Edit sorry again Beew -you are quite right persistence would require additional software, though obviously not for mint. I can't testify to unetbootin I had a number of failed live boots from both the windows and linux versions a few months back under 11.04, and still getting issues with the windows version so gave up on it. I was also only looking at this from an install point of view so forgot about persistance (short sighted I know but I just don't use it). Never had any problems using dd on any live .iso other than ubuntu though?

Anyway as usual a nice selection of options for the OP :)

---

### Post by beew on 2011-11-19
@jjex22

What you and **Paddy Landau** said about Unetbootin no longer works got me curious so I did a bit of experiements tonight. My finding is that it does work, what doesn't work is Ubuntu 11.10. 

I was able to create a live usb for LMDE (Linux Mint Debian Edition) and Fedora16 using Unetbootin in Ubuntu 11.04 (same usb, I wiped it to install the second os) , Both booted successfully. However, I did the same in Ubuntu 11.10 and both failed.

So I decided to try multisystem (see link in my post #11), again same outcome. In 11.04 I created easily a dual boot usb with both Fedora16 and LMDE and persistence for Fedora (multisystem supports only one presistent partition in the usb so if it is a multiboot usb only one OS is persistent). But in 11.10 I couldn't even install one, moreover, Firefox and VLC froze when multisystem was working. 

So I think the problem is really with Ubuntu 11.10, that is not surprising for me because at the moment it seems that more than half of everything I tested are broken. 11.10 has been a big disappointment for me so far, it is good that I haven't "upgraded" or installed it in any serious work machine. I will wait at least another two months before I will consider it seriously.

---

### Post by Paddy Landau on 2011-11-19
Have you tried Startup Disk Creator yet? In Ubuntu, that is what you are supposed to use.

---

### Post by beew on 2011-11-19
> **Paddy Landau said:**
> Have you tried Startup Disk Creator yet? In Ubuntu, that is what you are supposed to use.

If you are asking me of course not. How do you use the Startup disk creator to make a live usb for Fedora? It only works for *buntus, may be Mint, but then probably not even LMDE.

EDITED: Neither does it create multiboot usb, though it is not OP's requirement, but since I have a better app why would I want to use Ubuntu's startup disk creator? I don't think I am supposed to use the startup disk creator simply because I use Ubuntu any more than I am supposed to use IE to browse the internet if I run Windows.

---

### Post by Paddy Landau on 2011-11-19
> **beew said:**
> If you are asking me of course not. How do you use the Startup disk creator to make a live usb for Fedora? It only works for *buntus, may be Mint, but then probably not even LMDE.
All right, all right, I didn't know, OK?

But it does work for Mint (I've just double-checked), and that is what [post=11469585]the OP asked for[/post].

Actually, the OP has got his answer, so he can [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by kurt18947 on 2011-11-19
I have a clean install of 11.10 64 bit and Unetbootin works as expected, no problems.  What I **have** run into is that a USB drive will boot in one machine but not in another.  The problem was with the USB drive's FAT32 formatting and a machine's BIOS, not Unetbootin.  When I reformatted the drive using Windows then created a LiveUSB using Unetbootin, the USB drive booted as expected on all machines.

---

### Post by dniMretsaM on 2011-11-19
You might try [LiveUSB Install](http://live.learnfree.eu/). It seems to be pretty powerful. I'll probably be replacing UNetbootin with it.

---

### Post by Paddy Landau on 2011-11-19
> **dniMretsaM said:**
> You might try [LiveUSB Install]("http://live.learnfree.eu/").
Good find! It even has a repository.

---

### Post by dniMretsaM on 2011-11-19
> **Paddy Landau said:**
> Good find! It even has a repository.

It does? Where?

---

### Post by beew on 2011-11-19
> **dniMretsaM said:**
> It does? Where?

[http://live.learnfree.eu/download](http://live.learnfree.eu/download)

> for [USU]("http://learnfree.eu/"), Ubuntu, Debian and other apt-based distributions there is a repository, providing automatic updates: [http://download.learnfree.eu/repository/skss/](http://download.learnfree.eu/repository/skss/)Interesting selection of distros, but I still think multisystem is better for Ubuntu users because you can create multboot live usb with it, thereby save a lot of pen drives, it also has a repository, it will be added to your source list after you run the install script.

[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

---

### Post by klein de usa on 2011-11-19
hi 
i use the multisystem boot and it has always worked for me and works really well with a polop cd if the computer your working with doesn't support usb boot.

---

### Post by shotgunxbaby3 on 2011-11-19
I made the boot disk on my USB thumbdrive but when I try to boot from it i get the message on the boot screen "not a COM32R image" dunno what that means.

---

### Post by shotgunxbaby3 on 2011-11-19
trying to use LiveUSB installer but it won't recognize my thumb drive.

---

### Post by shotgunxbaby3 on 2011-11-26
I can't get live USB to boot every time and when it boots its like my thumbdrive doesn't exist.

---

### Post by shotgunxbaby3 on 2011-11-26
> **Paddy Landau said:**
> All right, all right, I didn't know, OK?

But it does work for Mint (I've just double-checked), and that is what [post=11469585]the OP asked for[/post].

Actually, the OP has got his answer, so he can [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

Well startup disk creator was the only program that has allowed me to create a live USB drive; however, I was not able to boot from the drive. Unetbootin and live USB installer fail to recognize my USB drive whether mounted or not. I am currently trying startup disk creator again because I really hate Ubuntu 11.10 and its lack of customization through native settings.

---

### Post by dniMretsaM on 2011-11-26
> **shotgunxbaby3 said:**
> trying to use LiveUSB installer but it won't recognize my thumb drive.

What is it formatted as? Also, make sure it's not mounted as read-only. You might want to fsck it, there could be some file system errors.

---

### Post by shotgunxbaby3 on 2011-11-26
It is formatted as FAT32 and I just reformatted it a few minutes ago. Live USB also will not even boot if the thumbdrive is connected. 

Startup disk creator works like magic, but when I boot from the USB it always says "not a COM32R image" if I could figure out what is causing that and fix it I would be good to go.

---

### Post by dniMretsaM on 2011-11-26
Try formatting it as ext4 or something. That's how I format all my USB drives and I've yet to run into a problem. What OS is it?

---

### Post by beew on 2011-11-26
I have tried unetbootin and multisystem in 11.10 last week and both failed, but in Natty and Maverick they created live usb for LMDE and Fedora 16 (that actually boot and install) with no issue (with persistence too with multisystem) I think there may be something wrong with 11.10. It has a kernel updare a few days ago, maybe I will try again.

I always format the usb as FAT, shouldn't be a problem.

---

### Post by dniMretsaM on 2011-11-26
You might try using GRUB to boot directly from the ISO file. A little slower, but it's handy for multi-booting and/or if you want to just drop the ISO in and not worry about burning. Doesn't work with all OS's though.

> **beew said:**
> I have tried unetbootin and multisystem in 11.10 last week and both failed

Weird. I just used UNetbootin a few weeks ago (before the kernel update btw) and it worked fine on Kubuntu. I suppose it might not work on Ubuntu though. Haven't used Multisystem.

---

### Post by beew on 2011-11-26
> **dniMretsaM said:**
> 

Weird. I just used UNetbootin a few weeks ago (before the kernel update btw) and it worked fine on Ubuntu. I suppose it might not work on Ubuntu though. Haven't used Multisystem.

Which Ubuntu? It works perfectly in 11.04 and 10.10, just not in 11.10.

EDITED: And with multisystem running VLC and Firefox became semi frozen, never experienced that before in Natty or Maverick, that made it looked more like it was an Oneiric problem

---

### Post by shotgunxbaby3 on 2011-11-26
> **dniMretsaM said:**
> Try formatting it as ext4 or something. That's how I format all my USB drives and I've yet to run into a problem. What OS is it?

Trying to boot mint 11, I think. I'll try the different format and see if it works with startup disk creator.

I'm seriously beginning to regret the purchase of this net book.

---

### Post by alecdebian on 2011-11-26
[URL="http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3"]try pendrive for usb booting too. down is the link
[/URL]
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3")

---

### Post by Jon Banquer on 2011-11-27
I just downloaded Ubuntu 11.10 and burned a boot CD from the ISO file. Works fine but I'd like to boot from a USB drive instead. Can I create a bootable USB using Windows 7 Pro 64bit and the Windows version of uNetbootin as well as the ISO for Ubuntu 11.10 that I made the boot CD with? 

[http://unetbootin.sourceforge.net/#features](http://unetbootin.sourceforge.net/#features)

---

### Post by Paddy Landau on 2011-11-27
> **Jon Banquer said:**
> Can I create a bootable USB using Windows 7 Pro 64bit and the Windows version of uNetbootin as well as the ISO for Ubuntu 11.10 that I made the boot CD with?
Forgive me if I have got confused, but I thought you had already tried that early on in the thread?

Have you tried the Universal USB Installer that [post=11491983]alecdebian suggested[/post]?

---

### Post by Jon Banquer on 2011-11-27
> **Paddy Landau said:**
> Forgive me if I have got confused, but I thought you had already tried that early on in the thread?

Have you tried the Universal USB Installer that [post=11491983]alecdebian suggested[/post]?

I did not post earlier in this thread and I have not tried it.

---

### Post by dniMretsaM on 2011-11-27
> **beew said:**
> Which Ubuntu? It works perfectly in 11.04 and 10.10, just not in 11.10.

EDITED: And with multisystem running VLC and Firefox became semi frozen, never experienced that before in Natty or Maverick, that made it looked more like it was an Oneiric problem

I used it on Kubuntu 11.10.

> **Paddy Landau said:**
> Forgive me if I have got confused, but I thought you had already tried that early on in the thread?

Have you tried the Universal USB Installer that [post=11491983]alecdebian suggested[/post]?

He's not the starter of this thread. He's an innocent bystander. So yes, you are confused (but we forgive you).

---

### Post by Jon Banquer on 2011-11-27
I ended up using:[ http://unetbootin.sourceforge.net/#features]("http://unetbootin.sourceforge.net/#features") and the ubuntu ISO for my USB drive that I want to boot from.

Unfortunately I can't boot from it because the BIOS on my computer doesn't seem to give me a choice to boot from a USB drive. If I don't see a choice in the Award BIOS does this mean I have no choice but to update the BIOS by flashing it?  My motherboard is an ASUS P5KPL-CM. I see choices in the BIOS for my  hard drives and for the CD / DVD drive but not for my USB drive.

---

### Post by Jon Banquer on 2011-11-28
Holding down F8 solved the problem. I'm able to boot ubuntu from the USB stick now so unetbootin works.

---

### Post by shotgunxbaby3 on 2011-12-06
If I formatted the computer's hard drive what is the chance that the thumb drive will boot?

---

### Post by Paddy Landau on 2011-12-07
> **shotgunxbaby3 said:**
> If I formatted the computer's hard drive what is the chance that the thumb drive will boot?
The thumb drive and the hard drive have nothing to do with each other. If you can boot from the thumb drive, it will make no difference whether or not your hard drive is formatted.

As thumb drives can be subject to sudden failure (more frequently than hard drives), it would be a good idea to have a second thumb or CD on hand to be able to boot from.

---

