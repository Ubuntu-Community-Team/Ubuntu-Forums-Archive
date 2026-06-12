---
title: "Ubuntu or Mint? Wireless Network use?"
date: 2014-03-05
forum: New to Ubuntu
---

### Post by NtuitEve on 2014-03-05
Hi,
I suppose it is just a matter of personal preference, but I would like some opinions on Ubuntu and Mint.
I am experienced with PCs, but a Linux beginner.  With support ending in April for WinXP, I am considering eliminating WinXP completely in my desktop, and possibly in my Toshiba Laptop; and dedicating a separate hard drive with Linux in my husband's desktop system ( he wants to keep his XP because of his expensive programs ( Video Editing, Video Capture, TV Tuner, Green Screen, and Karaoke ).
My primary motivation for wanting to eliminate WinXP is that it is so insecure for internet use, when compared to Linux; according to what I have read.  I have had endless hacking and hijacking with my Wireless Connection and Network, which I have been unable to stop, no matter what I have tried.

I am considering both Ubuntu and Mint 16 Petra with Cinnamon ( 32bit ).  I may be able to get some of my husband's XP programs to work with WINE in either Ubuntu or Mint.
 
I would be using Cable Internet and Wireless Networking, and have been seeing quite a few problems with both Ubuntu and Mint, with relation to Wireless Connectivity and Networking.  Wireless Connectivity and Networking with WinXP and Vista has never given me any problems establishing and maintaining a Connection; so the Linux Wireless problems I have been reading about are a bit disturbing.
What is the source of this situation?  Is it a compatibility issue with specific wireless modems and routers?
I would like some opinions on this before I leap into it.

Thanks in advance for your opinons.

NtuitEve

---

### Post by Mark Phelps on 2014-03-05
>  I have had endless hacking and hijacking with my Wireless Connection and Network, which I have been unable to stop, no matter what I have tried.

This is very disturbing -- because access to your network is completely independent of any OS that you run on a desktop or laptop machine.

If outsiders are getting into your wireless network, running Ubuntu or Mint on your PC is not going to change that.

---

### Post by JeQhdMD on 2014-03-06
Eve,

Security in any Linux version (aka distro) is normally much better than a stock windows install, especially XP.  So, when you talk your wireless being hacked, perhaps that's because the initial setup was insecure (lack of WPA-PSK2 and strong password) OR because you may have had some unpatched programs and browser plugins (java).

So, in MOST cases, any Ubuntu based distro WILL indeed provide more network and Local machine security, if you follow best practises (keeping your OS updated with bug & security fixes.).   This is easy to do for the most part, but you have to be careful with browser plugins.  And this certainly won't fix issues caused by phishing and clicking on websites with malicious applets, etc.

Re the expensive apps your husband uses.   You can run 100% of them if running XP inside linux via "Virtual Machine" software (VMWare Player or Virtual Box for example).   You just need a PC with at least 3 gigs of ram, and 4 to 6 is preferable.  (btw, in this case, you also need the install media/licenses).   VMWare Player and Virtual Box are no cost for personal consumer use (and readily available via the ubuntu software center OR the web at the official sites of each).

---

### Post by varunendra on 2014-03-06
You don't really need to "Jump in" at once. There is an option (and I strongly recommend it for you) to create a Live DVD or USB and test/use Ubuntu in Live mode by booting from that DVD/USB. (See [here]("http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install"))

It will have two-fold advantage -

**1)** You can verify whether the networking (and other hardware) would work with your computer or not. If not, whether it is easily fixable or not.

**2)** You can use the OS without actually installing it, and without even touching your hard disk unless you wish to. There is a "Persistence" mode in Live USBs, which allows to install applications and save changes to be able to use them again in a Live session, almost like a full install. (Read more about Live Persistent Vs. Full Install [here]("http://ubuntuforums.org/showpost.php?p=12857885"))

If the Live session works smoothly on the computer, you may keep using it in that mode until you are comfortable enough with Ubuntu. There are a few limitations in the Live mode, but for testing purpose, it is quick, safe and perfect.

---

### Post by 3rdalbum on 2014-03-06
Linux Mint is based heavily on Ubuntu and as far as I know they have identical wireless support.

There is no widespread wireless problem on Linux. Some WiFi cards don't have a driver or don't have a good driver, but the vast majority will work without a problem. By booting the Ubuntu / Linux Mint CD and choosing the "Try Ubuntu" option you can see whether your wireless is supported before you install.

---

### Post by Rob Sayer on 2014-03-09
It does sound like you need to look at your wireless router and security settings ...

Re. ubuntu v. mint ... I've had both on this netbook.  The laptop I generally use at home has kubuntu 12.04 lts on it but the 12.04 lts doesn't work as well on the netbook.  So I've tried a bunch of desktops and ubuntu, mint and fedora on this thing and will install 14.04 lts for good in a couple of months.

Mint may be ubuntu based but they use an older version of the kernel ... which controls all hardware & RAM and controls all program processes and which files are opened by which program and stuff like that.

So it's not 100% correct to say that wireless or other hardware will run the same necessarily the same on ubuntu and mint that's based upon the same ubuntu version.  I had mint installed about a year ago and had to go back to ubuntu because the mint kernel version had hardware support issues.  Same ubuntu version mint was based on.

Which brings up the other issue I have with mint.  While I don't think it's a bad distro per se, the tech support is awful.  *Wretched*.  For that reason, I would absolutely NOT recommend mint to a linux novice.  While linux is much more reliable and stable than windows you will tend to have to do more configuring to get it  to work right in the first place.

In other words, a linux novice absolutely has to have good tech support.  For newbies I  don't think there's anything to compare with ubuntu as far as tech support goes.  I know for a fact that it's better than some tech support you have to pay for in terms of expertise.

It's hard to recommend a specific desktop without knowing the actual hardware specs but most XP machines I've seen wouldn't run desktops like unity or cinnamon all that well.  They're really meant for newer hardware.

As mentioned, the best thing would be to just try some live CDs of different ubuntu desktops.

If you really have to have the xp programs ... there are usually linux programs that do the exact same thing ... I'm not sure wine is the ultimate solution.  It's not always that reliable.  A VM is a better choice.

Actually, if you absolutely need the XP programs, you could probably just set it up as dual boot xp/ubuntu and just NEVER go online in xp ... turn off auto network connect and windows update (which won't do much soon).

---

### Post by Mark Phelps on 2014-03-09
Few general comments ...

If you're following "best practices" in securing your wireless network (as in, using WPA2 and restricting Mac addresses), then running a Wireless router connected to an XP machine is no more risky than running a Wireless router connected to a Linux PC. The OS running on the host PC is unrelated to the security being enforced on the Wireless router -- either will do equally well.

As to using a Wine, my experience with using it for months is that it was essentially a waste of time.  Not only do you have to reinstall every Windows app you want to use, in many cases, the apps don't work well, and in some cases, don't work at all.  To check on this, you should go to the WineHQ website and look up the compatibility ratings of the apps and versions you want to use in Wine.  Anything that is not listed, or is listed but is rated less than Gold is essentially going to be a waste of time trying to use in Wine.

As to using a VM, you would have to reinstall XP from scratch and then, reinstall all the apps you want to use.  If the existing XP install is infected with malware, this will give you a clean start -- but reinstalling XP from scratch will accomplish the very same results.  If you think XP may be infected, then check out the free antivirus downloads from Kaspersky and Avira.  You can burn CDs from those, boot from them, and clean up your XP installation.

---

