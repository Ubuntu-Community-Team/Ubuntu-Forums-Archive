---
title: "New to Ubuntu, trying to escape Windows, touchpad help"
date: 2016-06-25
forum: New to Ubuntu
---

### Post by neil42 on 2016-06-25
Hello everyone...

I wasn't really sure how to title this thread, anyway here goes...

I come from an age when the BBC micro was the weapon of choice and have been using Windows based machines since they pretty much became available. I only use them for home use, surfing the web, family photos, email, a bit of word processing, just normal stuff. I'm not a programmer and have not much idea of what goes on under the hood. But I would like to learn.

So I dug out an old Dell XPS laptop that I had in the loft and managed to wipe the hard drive and get a clean install of 15.04 up and running. Everything seems to work, So riding high on a wave of confidence I upgraded to the latest version (16.04). Now it takes about 25 minutes to move the pointer from one side of the screen to the other. Looking in the settings, the touchpad speed and other options has disappeared, but the mouse settings remain. If I set the mouse pointer speed to fastest it's a little better but not much. A usb wireless mouse works fine.

I googled this and read loads, but if I'm honest I didn't understand too much, and lots seemed to be conflicting. I'm back to 15.04 and everything working again, but I presume that I should run the latest version and would like to understand what is missing and how I fix it


Thanks

N

:-)

Dell XPS 1530 Intel Core 2 Duo T9300 2.5GHz x2 GeForce 8600M 64 bit

---

### Post by oldfred on 2016-06-25
Depending on what graphics card/chip that system has, it may not run full Ubuntu well. Issue is more the graphics.
Have you installed the nVidia graphics driver?
       # list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices
# or
ubuntu-drivers devices | grep recommended  
   sudo apt-get remove --purge nvidia-*
sudo ubuntu-drivers devices
sudo ubuntu-drivers autoinstall 

Older systems then work better with Lubuntu or Xubuntu. Or perhaps Ubuntu Mate?
They do not use Unity which requires newer graphics cards/chips.

---

### Post by banceu_sergiu_ione on 2016-06-25
You may want to try Ubuntu Mate or Lubuntu 16.04 if you if you want the least relase or ubuntu 14.04 ( is what i have on an old pc with same spec. as your and also ubuntu 16.04 struggle to run )

I say this because 15.04 have not more support and you wont get anymore upgrades. 

Give a shot and see how Mate look, search same youtube videos.

---

### Post by grahammechanical on 2016-06-25
When we do an online upgrade it is always best to use Additional Drivers to activate the open source video driver. The open source video driver will be listed as X.Org X Server - Nouveau. In this way we avoid problems with video drivers.

The latest version of Ubuntu always come with the newest proprietary video drivers. But the newest proprietary video drivers often drop support of older video adapters.

When there is some conflict with video drivers the system uses as a fall back an open source video driver called llvmpipe. It gets us to a working desktop but it is slow and it would be especially slow on a video adapter that can only have 512 MB of video memory. And that is the situation with the Geforce 8600m

[http://www.nvidia.co.uk/page/geforce_8600m.html](http://www.nvidia.co.uk/page/geforce_8600m.html)

Additional Drivers may offer a legacy proprietary video driver for that video adapter but with only 512 MB video memory I would not expect much with Ubuntu + Unity. I have a Core 2 Duo and a GT220 + 1GB video memory and Ubuntu + Unity works fine. I think that 512 MB video memory is borderline with Ubuntu.

Regards

---

### Post by RobGoss on 2016-06-25
Hello and welcome to the forum, Ubuntu is a great choice when it come to desktops older machines may not always adapt to Unity desktop because it requires more resources to get things running. The lighter versions on the other hand maybe a better choice for this machine, also I would recommend sticking to the LTS distributions because they have longer support which may be something you might want to consider

Here are just a few you can test drive [Lubuntu ]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu") & [Kubuntu]("http://kubuntu.org/getkubuntu/") and last but not least [Ubuntu mate]("https://ubuntu-mate.org/") one of my favorites

---

### Post by Geoffrey_Arndt on 2016-06-25
When installing 16.04, was it a clean install from media, or was it an online upgrade from 15.04?? (which would not be good as 15.04 is long out of date).    If you can provide specs/info on what video system the Dell has, it will help forum members to better advise you.

---

### Post by gordintoronto on 2016-06-26
Also, how much memory on this computer?

---

### Post by elpak on 2016-06-30
kubuntu and mate is better than lubuntu for new user who working with windows 7 before.

---

### Post by HermanAB on 2016-06-30
Howdy,

The thing is, the newest Ubuntu is designed for the newest systems and is very power hungry.  If you have an older machine, then you should try the 'light weight' versions such as Xubuntu, Lubuntu and Mate.  

Deep down, they are all the same.  The difference is in the amount of graphical, power sapping cruft, layered on top.

---

### Post by kurt18947 on 2016-06-30
I have an old system with an *old* Nvidia card. Xubuntu was the best of the *buntus but still not great. What worked best for me on that machine is MX15. It's not a member of the *buntu family but is uses an XFCE desktop on a Debian base and has a reasonable graphical installer.

---

### Post by HermanAB on 2016-06-30
I prefer the XFCE desktop also and I'm OK with any of Fedora XFCE Spin, Xubuntu and Slackware.  Fedora has the best installer and Slackware the worst, but they all work the same in the end.  However, Slackware is much faster than other distributions (Patrick ensures that Slackware doesn't include any useless cruft), so if your laptop is old, then Slack is actually the best.

---

