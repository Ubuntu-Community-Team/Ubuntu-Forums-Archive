---
title: "I can't find my original post so I am doing it again"
date: 2023-04-02
forum: New to Ubuntu
---

### Post by mathman542 on 2023-04-02
Hi,
I am trying to load ubuntu onto a bootable external usb drive and getting nothing but aggravation. I have tried Rufus, useless. PowerISO no good. I am looking for something that is easy to use and works.
I am not liking the way the ubuntu community is providing help so far. That could change. I also am unable to find my post in the forum index.

Mark

---

### Post by TheFu on 2023-04-02
A few how-to guides:
[https://ubuntu.com/tutorials/install-ubuntu-desktop](https://ubuntu.com/tutorials/install-ubuntu-desktop)
[https://www.howtogeek.com/1261/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](https://www.howtogeek.com/1261/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/)
[https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I use 'cp', but have a number of friends that use Ventoy. [https://www.ventoy.net/en/doc_start.html](https://www.ventoy.net/en/doc_start.html) is for MS-Windows. The Linux version is about the same.

If you've never done this before, Etcher seems to be the easiest way to install, though it is pretty bloated. There are many new ideas in the Linux way of creating installation media that isn't typical. That's because commercial OSes like to be paid for doing that first step. Linux/Ubuntu is F/LOSS, so we have to provide our own media (flash drive).

This is your first post to these forums. Whatever you did before never got to the servers.

---

### Post by mathman542 on 2023-04-02
Well that was just as useless. It only finds my ssd external drive. Balens Etcher only finds my external ssd drive. This place is not user friendly. Rufus does not work.

---

### Post by TheFu on 2023-04-02
> **mathman542 said:**
> Well that was just as useless. It only finds my ssd external ssd drive. Balens Etcher only finds my external ssd drive. This place is not user friendly. Rufus does not work.

We are very friendly.  There are people here who really would like to help.  I get that you are frustrated. I've been there.  Sometimes USB controllers in some systems aren't compatible.  This usually happens when either really new hardware or niche hardware is being used.  Some flash storage isn't standard enough to work too.  The firmware could be out of date and needs to be updated.  That could be firmware for the storage device or the computer's BIOS.

Are you tied to Ubuntu or would a different distro work?
Which Ubuntu ISO, the exact name, are you using?

Are you giving up or want to try to figure out the root issue? Which OS is your computer running now that you are trying to build the flash install media from?  I can't help with MS-Windows or MacOS. I haven't used either recently.

---

### Post by mathman542 on 2023-04-02
I am using a year old dell system and my bios is up to date. Like I said I have become aggravated. I have worked with computers for 50 years and have never found anything to be so aggravating as this project has been. Many of these so called pieces of software that are supposed to make a bootable DVD to install Ubuntu on my blank hd HP computer. Many of these bootable pieces of software only want to install to my external ssd drive and not my external dvd drive. I've been on many forums and I don't like the way this one works. By the way, I tried all of the links you provided and none of those did me any good.,

---

### Post by TheFu on 2023-04-02
If you don't answer the questions, we cannot help. Nobody here is paid.  Consider that when posting too.
If you just wish to complain, fine.

---

### Post by mathman542 on 2023-04-02
I'm not complaining. Yesterday I tried to reinstall Windows 7 on my older HP system. I was running Winodws 7 on that computer. Then I have a Dell Windows 7 DVD. No product key required. I spent 5 hours trying to get it to reinstall. I finally gave up and decided to try a linux version that I could install to play Age of Empires II. I spent another 5 hours trying to get a bootable dvd. Nothing! Just aggravation. Everything that I downloaded just didn't work. So now I am aggravated. Doing things with linux has not been straightforward. Unlike Windows I just download and install. Quick and easy. Linux does not work that way. So now I am here trying to find a piece of software that finds all of my usb devices and move my Ubuntu.iso to open and get written to my usb dvd. By the way, Fu you are the only one that has so far been replying to this thread. This is my timeline. Why can't Ubuntu be as simple to install as Windows?

---

### Post by tea for one on 2023-04-02
Which operating system do wish to use to burn an Ubuntu ISO to DVD?
Which Ubuntu ISO do you wish to burn?

Also, I will add a caveat - Ubuntu ISO images are usually installed via USB thumb drives - it is more reliable.

---

### Post by mathman542 on 2023-04-02
I have a Dell with Windows !!. As for Ubuntu I am trying to use 20.x. I don't have a thumb drive.

---

### Post by tea for one on 2023-04-02
> **mathman542 said:**
> I have a Dell with Windows !!. As for Ubuntu I am trying to use 20.x. I don't have a thumb drive.
A bit more precision would be appreciated.
Windows version?
Ubuntu version 20.04?

Also, it would be useful to know the specification of your target PC?  i.e. where you eventually intend to install Ubuntu.
Ubuntu has a family of flavours and some older devices will function better with Xubuntu/Lubuntu etc.
More info here [https://ubuntu.com/desktop/flavours](https://ubuntu.com/desktop/flavours)

---

### Post by mathman542 on 2023-04-02
!! = 11 I downloaded Ubuntu last night. The target PC is an i7 HP I bought 12 years ago. The Ubuntu is a desktop version. So far I see nothing here that is going to help. The drive I want to write to is an external dvd drive.

---

### Post by mathman542 on 2023-04-02
The !! is 11. You have the right version. Target pc is an HP i7 with enough ram. I am using an Asus usb dvd.

---

### Post by tea for one on 2023-04-02
> **mathman542 said:**
> The !! is 11. You have the right version. Target pc is an HP i7 with enough ram. I am using an Asus usb dvd.
Two exclamation marks = 11 - that's a new one for me.

Anyway, having been a bit surprised that you do not have a thumb drive after working with computers for 50 years (post no. 5), it appears that you have a built-in utility in Windows 11.
Is this link useful for you?
[https://www.thewindowsclub.com/burn-iso-images-in-windows-7-without-3rd-party-software](https://www.thewindowsclub.com/burn-iso-images-in-windows-7-without-3rd-party-software)

---

### Post by TheFu on 2023-04-02
> **mathman542 said:**
> The !! is 11. You have the right version. Target pc is an HP i7 with enough ram. I am using an Asus usb dvd.

You can use any Windows DVD Burning software to take the ISO and put it on a blank DVD in ISO mode.  That has nothing to do with Linux or Ubuntu.
Be certain to validate the ISO file you have is correct.  There are lots of different flavors of Ubuntu and 20.x isn't sufficient as a version.  Versions are {yy}.{mm} - there are 2 releases a year.  In 2020, there was a release in April (04) and in October (10), to 20.04 or 20.10 would be the major Ubuntu release.  20.10 support ended in 2021. 20.04 standard support goes until April 2025 for the core OS.  Desktops usually need to be upgrade (meaning newer, not necessarily better) about every 2-3 yrs to stay current with security and internet services.  For example, in a few months, lots of things will break when a new version of TLS becomes mandated.  

We know this is coming and it will cause problems for older, unsupported, versions. They won't be able to connect to nearly any internet website or web service going forward.  20.04 is supported, so it will be fine.

Again, HP installs of Linux can be troublesome ... because they don't follow the standards. There are work-a-rounds.  If you search these forums for other people having troubles getting Ubuntu installed on their HP systems, you'll find the work-a-rounds.  I've avoided anything from HP PCs since 1999. Now, their HP-UX servers are great, but that's a completely different architecture - no Intel or AMD x86-64 CPUs in those servers.

---

### Post by mathman542 on 2023-04-02
HI Guys,
Never mind. I got windows 7 to finally install. I am now happy. If I could only find a decent network card to install and have it work. 
Thanks for the help.

---

### Post by tea for one on 2023-04-02
> **mathman542 said:**
> Never mind. I got windows 7 to finally install. I am now happy. If I could only find a decent network card to install and have it work.
I hope that you do not intend to use the internet with Widows 7.
It reached End of Life in January 2020 and the browser would not receive security updates.

---

### Post by TheFu on 2023-04-02
> **mathman542 said:**
> HI Guys,
Never mind. I got windows 7 to finally install. I am now happy. If I could only find a decent network card to install and have it work. 
Thanks for the help.

Nearly any Intel PRO/1000 NIC will work.  The Intel 2.5Gbps NICs used to have driver problems, but I haven't seen any in the last 6 months, so I assume intel finally fixed it, really this time, and got those updates into the mainline Linux kernels for all to get.

If all you wanted was Win7, I'm confused why you'd post here?  It isn't like changing an OS completely was every going to be easy.  It is like learning a new language.  Expecting to be dropping into Hungry and to pick up the local language in a few days is crazy. Learning a new OS is just as hard. We bring our preconceptions from the last OS with us, which aren't wrong, but usually very different.  You should have seen me trying to switch from Linux to MacOS.  The expensive, brand new, Mac almost ended up smashed against a wall. I decided to return it for my sanity.

Hopefully, your Win7 doesn't have a NIC or any other network connection. It isn't safe on any network.

---

### Post by MAFoElffen on 2023-04-02
Am I confused? 

Why is someone trying to use Rufus and Etcher to try to write to a USB DVD disk? They only work with USB thumb drives, right? Besides, all modern versions of Ubuntu Live Installer are designed to work with USB thumb drives and have timeout errors if you try to use an optical disk.

---

### Post by angisky on 2023-04-03
How much ram does the old dell have? I still own a Toshiba from that time period and even though it was a 64-bit core 2 duo they still only gave it 2gb of ram. That's just not enough ram for vanilla ubuntu 20.04. You'd have to go with Ubuntu Mate to get anything usable and still you'd have issues opening too many tabs in firefox. Mate is really nice on that hardware though. I can still use that old behemoth to log into Second Life just like it was 2009

---

### Post by TheFu on 2023-04-03
You have lots of smart people helping already, but I'll say these 3 things.

[LIST]
[*]Dual booting sucks. You will have issues caused by MSFT, eventually.
[*]25GB is a bit small for any Ubuntu Desktop you plan to actually "use".  I'm all for going thrifty on space/storage, but 35G has been the minimal useful amount since 2020. Bloat knows no boundaries, even in Linux.
[*]Lastly, if the system won't boot Windows at all (why would it?), then you don't need any NTFS anything. Use native Linux file systems for everything. You can access Linux storage over the network from Windows machines through Samba/SMB/CIFS (those are all the same practically speaking), and Linux really works better with native file systems. There are many things that cannot be done if NTFS is used.
[/LIST]

Anyway, consider those things.
A fresh Ubuntu install that wipes everything should take about 15 minutes.  Hardly a big deal.
If you post a little about the machine (exact CPU model, RAM, GPU) then we could suggest a good "Flavor" of Ubuntu Desktop for the best performance.  Any machine that isn't using UEFI for booting probably needs Xubuntu/Lubuntu or Ubuntu-Mate flavors to have good performance.  Gnome is just too heavy for most 10+ yr old computers, IMHO.

---

### Post by Topsiho on 2023-04-10
> **mathman542 said:**
> I'm not complaining. Yesterday I tried to reinstall Windows 7 on my older HP system.

You are aware, do you?  that Windows 7 is obsolete and not usable anymore if you connect to the internet?
Then, this is not a Windows forum, so most Windows questions should be asked elsewhere.

Also: this is a  very friendly forum, and not the cause of any aggravation you have. Most, if not all, members are very eager to help anyone, not being paid for their help, and for their sometimes very considerable efforts. Please consider this. 

Another 50+ years user of computers, not knowing very much of computers :) as I only use them, and Ubuntu giving me almost no problems at all.

Welcome to this forum :)

Topsiho

---

### Post by DuckHook on 2023-04-11
> **mathman542 said:**
> …getting nothing but aggravation.
…I am not liking the way the ubuntu community is providing help so far.

> **mathman542 said:**
> Well that was just as useless.
…This place is not user friendly.

> **mathman542 said:**
> …I have become aggravated.
…never found anything to be so aggravating as this project has been.
…I've been on many forums and I don't like the way this one works.

> **mathman542 said:**
> …Nothing! Just aggravation.
…now I am aggravated.
…By the way, Fu you are the only one that has so far been replying to this thread.

> **mathman542 said:**
> The !! is 11.

I can't judge the relative friendliness of the large and diverse Ubuntu communities. What I **can** judge is the peculiarity of those who think that they can successfully get help by resorting to putdowns, petulance, passive&#8209;aggression and an arrogant sense of entitlement.

I concede—with crucial qualifications—that this place is not *user* friendly. Rather, we are *courtesy* friendly. Like any self&#8209;respecting community, we are friendly to those who reciprocate. We have no obligation to show friendliness to those who rationalize away their rudeness under the rubric of "aggravation".

To those of you who have tried to help, you have shown admirable patience and forbearance in the face of barely concealed disdain. Your conduct is as commendable as the OP's conduct is not.

As for your collective efforts to render assistance, I suspect that there is no point talking sense to someone who considers Windows 7 a legitimate solution to anything, or whose motives for installing Linux is to play Windows games. In all candour, we should be relieved. By insisting on his zombie OS, the OP will be safely contained in the Windows malware swamp and won't be corrupting our ecosystem with his dreadful computing hygiene.

---

### Post by QIII on 2023-04-12
@mathman542:

You are welcome to start a new thread in which you remain objective, polite and appreciative.

This thread, however, is closed.

---

