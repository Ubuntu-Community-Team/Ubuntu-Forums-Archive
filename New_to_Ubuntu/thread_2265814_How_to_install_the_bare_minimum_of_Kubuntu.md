---
title: "How to install the bare minimum of Kubuntu?"
date: 2015-02-18
forum: New to Ubuntu
---

### Post by garycheng12 on 2015-02-18
What I'm looking for is a stripped-down Kubuntu (one without any of the extra pre-installed applications--many of which I have my own selection of application that replace it) and also as "lightweight" but fully functional (GUI and drivers) once I install my own applications. I have googled and found different ways of people getting a cleaner Kubuntu, but different packages are installed depending on what they want their Kubuntu to be and I'm not sure of the differences and options that are available for me. For example, there are so many different packages that are similar: kde-minimal, kde-desktop, kde-full, kde-plasma-desktop, plasma-desktop, kde-workspace, etc. The dirty and much less-effective way is to just download Kubuntu and then remove all applications that I don't use and I much rather build from a functional bare minimum up instead. Several questions:

1. What are the options available to me? For example, seems like kde-base, kde-minimal, plasma-desktop, and kde-desktop are stripped down versions of kde-full. If so, how do they differ? I just want a KDE environment (is saying this any different than saying I want Kubuntu without pre-installed applications? 

2. Am I supposed to start from Ubuntu minimal.iso? Under "Software Selection", I see "Kubuntu desktop" and "Kubuntu full" as options and I'm thinking maybe even "Kubuntu desktop" is too bloated for my purposes.  If possible, can anyone guide me step-by-step how? 

3. How do I find/install drivers after? From my experience, third-party drivers offer better performance/reliability. I can download straight from Nvidia for the graphics driver (but is there an official PPA I can add to automatically update it in the future?) but what about other drivers like network adapter, etc.?

4. Any precautions I need to take, such as having to mark certain packages as manual so I don't accidentally delete the system due to deleting a dependency or something like that? 

5. I plan on having this stripped-down version of Kubuntu on both a virtual machine and on my laptop. I never dealt with virtual machines before but I managed to have the mini.iso running--any tips to possibly enhance the performance of the OS on the virtual machine? It doesn't seem too slow or anything but I might be able to increase performance somehow.
Thanks.

---

### Post by mastablasta on 2015-02-18
are you low on disk space? Kubuntu is preconfigured with some applications that will make your life easier (e.g. network manager, updater, package manager...). while some are just there in case you might want to use them (e.g. office). but even if you have them they represent "bloat" as you call it, only to your disk not your system. so if you want a lighter, faster system - simply removing the apps left and right that are not running when system is non won't make it any faster.

Kde issue is they way it is drawn on screen, it's special effects and Akonadi or whatever that indexer is now called. I am not sur eif this is still the case for 14.04, but 12.04 had a lowfat package that just by running it it made the system lighter as it disabled many functions otherwise present.

you can build form minimal but you will still be actually building your own system. and I am sure there are some things that might have been ironed out in the full Kubutnu. and in this kind of system you will have to do the search and solve any issues yourself. 

anyway maybe start with kde minimal and build from there.

I used XFCE for virtual PC. there is no need for special effects so I turned off those and set up a light theme. then I replaced the login manager with a lighter one. still had to add plenty of things my self. result is very bare XFCE. and as soon as I want to do more things on it, I need ot add stuff. which make me wonder if it wouldnt' be easier to just use Xubuntu  and make it lighter instead.

---

### Post by Bucky Ball on 2015-02-18
[Minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD") and then install KDE. You need to do the rest. Only apps and whatever else you want/need. Mini.iso only installs the base kernel. You do the rest with 'sudo apt-get install'.

---

### Post by v3.xx on 2015-02-18
As stated, kde-plasma-desktop looks to be the minimum required.
[http://packages.ubuntu.com/trusty/kde/kde-plasma-desktop](http://packages.ubuntu.com/trusty/kde/kde-plasma-desktop)

[https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE)

---

### Post by deadflowr on 2015-02-18
+1 to mini install
I'd say install these two packages.
plasma-desktop
konsole

plasma-desktop will give you the barest desktop.
it will have no file manager or much of anything.
Which is why you also install konsole. So you can have at least a terminal.

---

### Post by garycheng12 on 2015-02-18
Yea, initially I was thinking of kubuntu-desktop with --no-install-recommends but I think I can I get a way with an even more stripped-down version. Disk space is not an issue--I just want to build from ground up to have a cleaner system and find out what I actually need and don't need as I use the system.
I think I'm going to go with "plasma-desktop" but then I saw "kde-plasma-desktop" and am guessing I will be missing some system tools and configuration tools (is this true)? Kubuntu is my first Linux system and I'm not sure if the settings to configure the desktop were part of Kubuntu or KDE itself. I won't get the pre-installed applications from plasma-desktop which is what I want (the obvious ones like a word processor, browser, file manager, etc.) but what about the utility applications?

---

### Post by deadflowr on 2015-02-18
I figure as long as you have konsole, or any other terminal emulator, then adding stuff like a file manager or browser will be easy.
plasma-desktop does install the system settings package, and the system monitor tool, ksysguard.

Stretching it a little bit, I'd recommend some sort of package manager, like muon, or synaptic, or adept.
muon and adept are both native kde apps, but synaptic is not.
Muon is kubuntu's package manager app.
I've never used adept, so can't say anything beyond acknowledging it exists.

Added: ( and of course tasksel ; the thingy used when you install packages at the end of installing during mini install can also be installed)

I recommend a package manager because you might find even lighter apps, than what you may be thinking of, like file managers, or browsers.
which would otherwise go under the radar for reasons of utter obscurity. 

If that makes sense.

---

### Post by Frogs Hair on 2015-02-18
Razor QT may be worth a look and it's in the repository . [http://razor-qt.org/screenshots/](http://razor-qt.org/screenshots/)

---

### Post by garycheng12 on 2015-02-18
> **deadflowr said:**
> I figure as long as you have konsole, or any  other terminal emulator, then adding stuff like a file manager or  browser will be easy.
plasma-desktop does install the system settings package, and the system monitor tool, ksysguard.

Stretching it a little bit, I'd recommend some sort of package manager, like muon, or synaptic, or adept.
muon and adept are both native kde apps, but synaptic is not.
Muon is kubuntu's package manager app.
I've never used adept, so can't say anything beyond acknowledging it exists.

Added: ( and of course tasksel ; the thingy used when you install  packages at the end of installing during mini install can also be  installed)

I recommend a package manager because you might find even lighter apps,  than what you may be thinking of, like file managers, or browsers.
which would otherwise go under the radar for reasons of utter obscurity. 

If that makes sense.

Yea, I definitely will want either Muon or Synaptic. Will check out lighter apps for the virtual machine. Thanks for your help.

And will check out Razor-qt for the virtual machine.

Thanks everyone.

---

### Post by garycheng12 on 2015-02-19
Ok, here's another thing I'm wondering about. I wanted to create a separate thread because it was a long post and I'm not sure if it's different enough such that it wouldn't be considered a duplicate, but here it is:

When I ran mini.iso and installed only plasma-desktop, I had Ubuntu  with KDE and no pre-installed applications but with no driver manager as  well. 

  Question 1: What are the differences, if any, between these a clean Ubuntu with KDE and a clean Kubuntu? (I am not using pre-installed applications and I am sticking  with KDE, not GNOME, so are there any more differences such that I would  prefer a clean Ubuntu with KDE over a clean Kubuntu? I will be using both GNOME-based and  KDE-based applications, if that makes any difference. If there are any differences, how would I get a clean Kubuntu by building up (since "plasma-desktop" is KDE but not Kubuntu and kubuntu-desktop includes pre-installed applications? The common  consensus I found after reading online is that Kubuntu's performance is smoother than Ubuntu's  but I don't know if that's entirely because of KDE (which would be  negligible if I had a clean Ubuntu with KDE).
  
Question 2: I am lacking certain system tools  such as a driver manager after installing only plasma-desktop. How can I install all system tools but not any of the pre-installed applications?

  P.S. mini.iso works only with BIOS. What if I want to do the same  thing for a UEFI system? Building from mini.iso, rather than installing a  full *buntu and then removing uninstalled pre-installed applications. I read that UEFI-capable system can use BIOS for the mini.iso to work, but is it not possible to take advantage of UEFI while having the ability to build up via mini.iso rather than stripping down via apt-get kubuntu-desktop --no-install-recommends?

---

### Post by deadflowr on 2015-02-19
KDE has a few packages which Kubuntu doesn't install or replaces with more common packages used by Ubuntu.
Kubuntu includes libreoffice packages, which kde would not include, opting for something like calligra or koffice or whatever it is kde would call it's office suite.
(You're probably going to be mostly right about kde packages as long as you slap a K in front)

So in that regard there are differences between KDE and Kubuntu.

---

### Post by v3.xx on 2015-02-19
Have you seen these threads?

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=minimal+kde+install&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=minimal+kde+install&sa=Search&cof=FORID:9)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=minimal+kubuntu+install&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=minimal+kubuntu+install&sa=Search&cof=FORID:9)

---

