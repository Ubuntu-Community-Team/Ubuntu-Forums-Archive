---
title: "Ubuntu needs major re-development"
date: 2014-09-07
forum: Recurring Discussions
---

### Post by timi2 on 2014-09-07
Im sorry to say but i am pissed at canonical. Ubuntu is a nice, light, fluid operating system that can replace windows but it is targeted at only computer geeks. I am a windows fanboy and I have always used windows but a few months ago I installed Ubuntu and I enjoyed the experience. Ubuntu was fun and fast. I had to uninstall Ubuntu at some point because my UEFI bios had some issues so i had to flash. Today I saw Ubuntu on someones pc and I decided to Reinstall. Its sad to say but the process was just to cumbersome. I had to turn of fast startup, turn off secureboot. I did those but kept booting to a black screen. I eventually passed there by typing nomodeset after _________(forgotten the name).
After several tries it finally went into the install screen and i installed it. Now it was time to use boot repair. I wonder why something as important as boot repair is not included in the Os when installing the OS. Well, i tried connecting to my Wi-fi network but it kept connecting and disconnecting. I could not install boot repair up till now. Tell me who can go through all this? Who can do all this? Only a computer geek. No average computer user will go out of their way to install ubuntu. Canonical should make the installation process less cumbersome and annoying. Note: This is something i have installed 3 times before but could not install now. Once i installed windows my first time it was super easy the next time. Canonical should redevelop Ubuntu! Dont get me wrong Ubuntu is a fast and fluid os when everything works but it's not just for me anymore.

---

### Post by wildmanne39 on 2014-09-07
*Thread moved to **Recurring Discussions**.*

---

### Post by uRock on 2014-09-07
I've installed ubuntu 14.04 several times on different machines, None of these problems were observed. Reading the release notes and skimming through the wiki sites to find out what you'll be dealing with when it comes to your computer's specs is a must and will make installations much easier.

---

### Post by ian-weisser on 2014-09-07
> **timi2 said:**
> I had to turn of fast startup, turn off secureboot. I did those but kept booting to a black screen. I eventually passed there by typing nomodeset after _________(forgotten the name).

Blame your hardware manufacturer. Ubuntu didn't install that UEFI crudware on your system.
You paid for that feature.
You paid your hardware manufacturer to make it hard for you to install Ubuntu.


> **timi2 said:**
> Now it was time to use boot repair.

Seems like you chose to dual boot.
Windows deliberately makes dual-boot hard to do. Not Ubuntu's fault.
You paid for that feature.
You paid Microsoft to make it hard for you to dual-boot install Ubuntu.


[EDIT]: Thanks to uRock for pointing out that occasionally the Live environment works, but a fresh install still needs proper drivers.


Please let us know your hardware manufacturer and model.
We can recommend Ubuntu users away from buying the same incompatible hardware.

---

### Post by uRock on 2014-09-07
> **ian-weisser said:**
> Seems like you didn't test your hardware with the Live environment first.
I can't see how it's Ubuntu's fault that you didn't test your hardware with the provided free, easy-to-use tool.

To be fair, I have had a few ubuntu installs in the past where everything worked during the live session just to install and find I had to drop to command line and install graphics drivers. To make it more fun, I had to use another machine for downloading the driver because the Wifi stopped working as well. I had to do that for every release starting 10.04 through 12.04. Not long after installing 12.04 I tested Linux Mint and found that I no longer had to install any drivers on the first startup, so I used Mint with Cinnamon all the way up until I downloaded ubuntu 14.04.

---

### Post by andrew102 on 2014-09-08
> **uRock said:**
> I've installed ubuntu 14.04 several times on different machines, None of these problems were observed. Reading the release notes and skimming through the wiki sites to find out what you'll be dealing with when it comes to your computer's specs is a must and will make installations much easier.

I think there's some issues with Win8 and newer BIOS that make the steps of disabling boot options necessary.

Also I've noticed little problems except for a server box that was running 12.04 failed a dist-upgrade. Afterwards used a DVD to install and it worked but had display issues at login (might I add that it's extremely old machine with about 64MB of available video memory, [no issue as I only need to access by SSH])

On my normal desktop - I found there was a bug after upgrading to 14.04, this -http://askubuntu.com/questions/450567/failed-to-start-session-after-interrupted-upgrade-to-14-04 

I don't disregard that regular old windows people might have trouble with Ubuntu. But having said that, I can definitely say the support behind Ubuntu is far greater in quality if you know where to look. Too often have I seen "an error has occured: error code 0x0000000f" then to go to the microsoft support to see a far less the helpful **acknowledgement that it indeed is a windows error with no real solution. <click> on the "No" next to "was this helpful?"**

---

### Post by impinball on 2014-10-28
There really needs to be a script/equivalent written to work around as many of the known Windows 8 dual boot issues as possible, automatically run. Then (using manufacurer detection), there should be some sort of prompt that tells what key to press repeatedly until the BIOS screen appears. It should display exactly what setting(s) to edit and save, and then restart the system (after an obvious prompt). VBScript/JScript may be helpful here, except for maybe the manufacurer detection.

---

### Post by bro2 on 2014-10-28
> **timi2 said:**
> Im sorry to say but i am pissed at canonical. Ubuntu is a nice, light, fluid operating system that can replace windows but it is targeted at only computer geeks. I am a windows fanboy and I have always used windows but a few months ago I installed Ubuntu and I enjoyed the experience. Ubuntu was fun and fast. I had to uninstall Ubuntu at some point because my UEFI bios had some issues so i had to flash. Today I saw Ubuntu on someones pc and I decided to Reinstall. Its sad to say but the process was just to cumbersome. I had to turn of fast startup, turn off secureboot. I did those but kept booting to a black screen. I eventually passed there by typing nomodeset after _________(forgotten the name).
After several tries it finally went into the install screen and i installed it. Now it was time to use boot repair. I wonder why something as important as boot repair is not included in the Os when installing the OS. Well, i tried connecting to my Wi-fi network but it kept connecting and disconnecting. I could not install boot repair up till now. Tell me who can go through all this? Who can do all this? Only a computer geek. No average computer user will go out of their way to install ubuntu. Canonical should make the installation process less cumbersome and annoying. Note: This is something i have installed 3 times before but could not install now. Once i installed windows my first time it was super easy the next time. Canonical should redevelop Ubuntu! Dont get me wrong Ubuntu is a fast and fluid os when everything works but it's not just for me anymore.
My BIOS doesn't have Secure Boot, but it has UEFI, and when booting from USB, I can choose to boot from UEFI or not (device appears twice in boot menu). Obviously disable Secure Boot, and UEFI as well, but without UEFI/Secure Boot Ubuntu's ridiculously easy to install (same install process as Windows 7/8 really)

---

