---
title: "New to Ubuntu: issues on installing it on a XPS + few questions"
date: 2018-09-18
forum: New to Ubuntu
---

### Post by lee-lith- on 2018-09-18
Hi folks,

I just installed Lubuntu after few years on Windows, but running other Linux distros on VMs. I finally made the jump and I'm quite happy, the interface is extremely fast, I love it!


**Installation**
I'm using a Dell XPS 9360, running on a SSD.

I did use rufus on Windows to format an USB drive and put the Lubuntu ISO on it. I did reformat my Windows partition (I wasn't able to format it directly from Lubuntu GParted). I also had to go back to the Legacy mode to boot from the USB **_and_** install it, if I didn't do that change and used UEFI boot (even without the secure mode on) Lubuntu was just not going to install.

I did installed it with the disk encryption. For some reasons, when I do change the boot option back to UEFI, it's not working. If I leave it into the Legacy mode, it just won't start and I have to manually go into the boot menu options, and select the Ubuntu partition.

Any idea why it's behaving like that? I tried several different things without success :/

[B]Tips for new comers
[/B]I never been using Ubuntu fully and completely, and as a result I don't know the shortcuts etc. Is there a good reference of the most useful shortcuts to know (obviously ctrl+c|x|v are well known ones :D)?

I did had an Apple few years back, and one soft that was killing it was an app launcher called Quicksilver, is there something similar for Ubuntu that allows to quickly lunch an app by pressing a shortcut + typing the app name?

I used extensively SnagIt on Windows for taking screenshots and quickly editing the screenshots. There is no Linux version of SnagIt by the Software editor, but is there a Linux alternative that could do most of what SnagIt can do?

I do have a 4k screen, which makes all fonts etc extremely small, how can I change the size of the windows, fonts, terminal, etc?

I think that's all but I'm sure I will have more questions coming next days :)

Thanks!

---

### Post by oldfred on 2018-09-18
UEFI/gpt & the now 35 year old BIOS/MBR configurations are not compatible.

Dell does need some UEFI settings changed to work correctly

UEFI has to have the ESP and highly recommends gpt partitioning. Windows only boots in UEFI mode with gpt. If drive was gpt & you still have the ESP - efi system partition, you probably can just reinstall grub to convert to UEFI. But if you erased ESP & converted drive to MBR, even though most of it really is LVM, you would have to reinstall.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Just run the summary report, the auto fix sometimes can create more issues.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Other Dell installs.
       
 Dell XPS 13 9360 
[https://ubuntuforums.org/showthread.php?t=2353288](https://ubuntuforums.org/showthread.php?t=2353288)
Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install)
Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04 AHCI NVMe
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488)
Ubuntu 16 on the DELL XPS15 9550 Tutorial
[https://ubuntuforums.org/showthread.php?t=2345444](https://ubuntuforums.org/showthread.php?t=2345444)

---

### Post by lee-lith- on 2018-09-19
Thanks for your reply.

I did run boot-repair utility, and it gave me the following report:

[http://paste.ubuntu.com/p/vQPV9WQWpB/](http://paste.ubuntu.com/p/vQPV9WQWpB/)

If I have to reinstall my system I'm fine with that as my system is empty., I just don't know how to properly do that.

(I did select the LVM option at the installation)

Edit: I don't want to have dual boot, I just want to have Ubuntu. I did completely format the drive as exfat when I did erase Windows (I had to do that otherwise Ubuntu wasn't able to see my SSD drive).

---

### Post by oldfred on 2018-09-19
Dell needs UEFI update, and SSD firmware update.
And  you need to change drives to AHCI, not RAID nor Intel SRT for Ubuntu to correctly see drive(s).

I do not know LVM, nor encryption.

Do not use Legacy.
Your install is configured for UEFI boot and somehow you have a BIOS Windows boot loader installed to MBR which obviously will not work

---

### Post by mastablasta on 2018-09-20
> **lee-lith- said:**
> 
[B]Tips for new comers
[/B]I never been using Ubuntu fully and completely, and as a result I don't know the shortcuts etc. Is there a good reference of the most useful shortcuts to know (obviously ctrl+c|x|v are well known ones :D)?

Check the ubuntu manual, there are also various "reference cards" or "cheat cards" out there.

> 
I did had an Apple few years back, and one soft that was killing it was an app launcher called Quicksilver, is there something similar for Ubuntu that allows to quickly lunch an app by pressing a shortcut + typing the app name?

hit windows key and start typing. in kubuntu there is also alt+f2
> 
I used extensively SnagIt on Windows for taking screenshots and quickly editing the screenshots. There is no Linux version of SnagIt by the Software editor, but is there a Linux alternative that could do most of what SnagIt can do?
a bunch of them. i use Ksnapshot:
[https://alternativeto.net/software/snagit/?platform=linux](https://alternativeto.net/software/snagit/?platform=linux)

i then use *nomacs* for picture viewer and quick editing because it loads realy fast and is easy to use.

> 
I do have a 4k screen, which makes all fonts etc extremely small, how can I change the size of the windows, fonts, terminal, etc?

i don't know how to deal exactly with 4k in Ubuntu but my guess would be you need to make changes in desktop settings. in Kubuntu you would do changes like this over at the "control panel" (system settings).

---

### Post by lee-lith- on 2018-09-21
> **oldfred said:**
> Dell needs UEFI update, and SSD firmware update.
And  you need to change drives to AHCI, not RAID nor Intel SRT for Ubuntu to correctly see drive(s).

I do not know LVM, nor encryption.

Do not use Legacy.
Your install is configured for UEFI boot and somehow you have a BIOS Windows boot loader installed to MBR which obviously will not work

The issue was with intel RAID, I switch that to AHCI as you mentionned and it's now booting normally, and really quickly. Thanks! :)

> **mastablasta said:**
> Check the ubuntu manual, there are also various "reference cards" or "cheat cards" out there.


hit windows key and start typing. in kubuntu there is also alt+f2

I can type but nothing is launching, I guess in Lubuntu is maybe different?

> **mastablasta said:**
> 
a bunch of them. i use Ksnapshot:
[https://alternativeto.net/software/snagit/?platform=linux](https://alternativeto.net/software/snagit/?platform=linux)

i then use *nomacs* for picture viewer and quick editing because it loads realy fast and is easy to use.


i don't know how to deal exactly with 4k in Ubuntu but my guess would be you need to make changes in desktop settings. in Kubuntu you would do changes like this over at the "control panel" (system settings).

I will check on Google, I have change some settings which makes fonts bigger but it's still not perfect.

---

### Post by mastablasta on 2018-09-24
> **lee-lith- said:**
> 
I can type but nothing is launching, I guess in Lubuntu is maybe different?
.

eh lubuntu. it is missing plenty of things in order for it to work faster and to be lighter. Unless you are limited with resources (older PC?!), unless you need every small piece of hardware dedicated to other tasks, then Gnome, Mate, KDE and Cinnamon offer a much better deskotp experience. XFCE is next, then LXDE in Lubuntu and then windows managers. too bad LXQT is still in development.

due to modular nature of Linux you can add various things to your Lubuntu desktop from other desktops.

try: 
alt+f2 
or: 
windows key+R

then type the app name.
Lubuntu shortcuts:
[https://help.ubuntu.com/community/Lubuntu/Keyboard](https://help.ubuntu.com/community/Lubuntu/Keyboard)

[http://www.comfsm.fm/~dleeling/tech/lubuntu-lxde-openbox-desktop-keyboard-shortcuts.html](http://www.comfsm.fm/~dleeling/tech/lubuntu-lxde-openbox-desktop-keyboard-shortcuts.html)

---

### Post by lee-lith- on 2018-09-24
Windows key + R works! thanks :)

I will have a look at your links.


One of the mean reasons I choose Lubuntu over Standard Ubuntu is because of the battery usage. I see a clear decrease of battery capacity on Lubuntu compared to when I was using Windows 10. My though was if I use a very light version of Ubuntu, I will have a better battery life.

If you have some recommendations and tips on how to have a good battery life on stnadard Ubuntu I'm highly interested :)

I heard about XFCE too, but from my researches on Google it was advised to go with Lubuntu and LXDE. I also heard about LXQT, but many people say it's not stable yet, but from my understanding it looks promising in terms of user experience and still being light, right?

---

### Post by mastablasta on 2018-09-24
> **lee-lith- said:**
> 
If you have some recommendations and tips on how to have a good battery life on stnadard Ubuntu I'm highly interested :)

battery life depends on many factors. including good drivers, reduced background processes (or at least their good management), proper system settings (power management). in linux i found that many times out of the box setup is too general and much more can be done with tweaking. 

for example my Kubuntu dual boot with win7 - Kubuntu uses battery faster- the reason is worse GPU drivers & lack of support for some motherboard features. the difference is noticeable but is not that big (maybe 20-30 mins). mayb ei could improve it with tlp and various power management apps, but i don't use the laptop that often anymore especially now that they got me a laptop at work.

> 
I heard about XFCE too, but from my researches on Google it was advised to go with Lubuntu and LXDE. I also heard about LXQT, but many people say it's not stable yet, but from my understanding it looks promising in terms of user experience and still being light, right?

LXQT is light, but has the power of QT (used by KDE) behind it. QT apps are (in terms of GUI) usually more feature rich. running them on GTK (LXDE, Gnome, XFCE) is kind of pointless (although they do work just fine). many of them are really good and they are my kind of apps because i can find the feature i need through menus or on icons. while gnome (GTK) apps often have many features hidden or are too simplistic. sometimes that is not a bad thing, but sometimes you just want a bit more from the app. if you install qt app on gnome interface then it loads all sorts of other libraries with it. so the downloads can get a bit bigger.

---

### Post by lee-lith- on 2018-10-02
Sorry for the late answer, have been quite busy with work.

All the Ubuntu versions such has Ubuntu, Kubuntu, Lubuntu etc, all use the same drivers right? If yes, is the Desktop Environment using sugnificantely more power on heavier versions (like Ubuntu) than lighter ones such as Lubuntu?

If you have to optimize battery life, what do you recommend?

I'm fine to change for Kubuntu or standard Ubuntu, but I heard Lubuntu is the lightest one and so battery will last more (in my opinion, but I'm not experienced with Ubuntu). Am I wrong?

---

### Post by mastablasta on 2018-10-03
> **lee-lith- said:**
> Sorry for the late answer, have been quite busy with work.

All the Ubuntu versions such has Ubuntu, Kubuntu, Lubuntu etc, all use the same drivers right? If yes, is the Desktop Environment using sugnificantely more power on heavier versions (like Ubuntu) than lighter ones such as Lubuntu?

If you have to optimize battery life, what do you recommend?

I'm fine to change for Kubuntu or standard Ubuntu, but I heard Lubuntu is the lightest one and so battery will last more (in my opinion, but I'm not experienced with Ubuntu). Am I wrong?

There is nothing wrong with Lubuntu. it's a fine system. the only downside is (potentially) that they do not offer 5 year support. but this might not be important.

KDE and Ubuntu by default use more ram, they have various advanced desktop features and effects that make it all look smooth and fancy. but if oyu don't need any of these then a lighter distro is the way to go. 

they all use same drivers (since they use same kernel).

tlp is one of the power managers. there is also jupiter. however, if all is working fine for you right now i would leave it alone (it is easy to make things worse). 
but if you decided to gibve it a try

[https://askubuntu.com/questions/285434/is-there-a-power-saving-application-similar-to-jupiter](https://askubuntu.com/questions/285434/is-there-a-power-saving-application-similar-to-jupiter)

[https://www.tecmint.com/tlp-increase-and-optimize-linux-battery-life/](https://www.tecmint.com/tlp-increase-and-optimize-linux-battery-life/)

there is also a GUi (beta) for TLP that aims to prevent users doing a bad setup: [https://github.com/d4nj1/TLPUI](https://github.com/d4nj1/TLPUI)

---

