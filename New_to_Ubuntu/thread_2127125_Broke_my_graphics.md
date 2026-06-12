---
title: "Broke my graphics"
date: 2013-03-19
forum: New to Ubuntu
---

### Post by Wurstinator on 2013-03-19
Hello,
after using Ubuntu (12.04 amd64) for about 5 months, I seem to finally broke it up to a point where I can't fix it myself.
I am using a Samsung 700Z7C notebook with an Intel HD 4000 onboard graphic and a Nvidia GT650M external with Optimus. That is, I can use the Intel graphics for most of the time for less power consumption and switch to Nvidia if I need more performance.
As far as I read, only the Intel card is used by default. To use the Nvidia one I tried to install Bumblebee which should enable Optimus support on Linux.
Well, that went not as well as I hoped. Basically, it says I have to install "nvidia-glx" first. That, however, is in conflict with "xserver-xorg-core" and removed or at least damaged that crucial package.
I reinstalled XServer after that (which again removed nvidia-glx). 
Sadly, now my "task bar" to the left of Unity lost all its transparency. It's kind of hard to describe it. If needed, I will upload a screenshot.
The two things I need help with are
1. bring back my system to its old state so at least Unity looks normal again
2. install Bumblebee and all its dependencies so I can use Nvidia Optimus

Would be great if someone could help me :)

---

### Post by khelben1979 on 2013-03-20
From what I can see your nVidia chipset is supported by [nVidia driver version 310.40]("http://www.nvidia.com/object/linux-display-amd64-310.40-driver.html"). So if you read the README file which comes with that and follow the instructions you should be good to go (hopefully!). If the driver gives the possibilities for you to switch between your intel graphics (Intel driver is supported by the Linux kernel) and the new nVidia driver once installed, I don't know. So if you want to test it, make a full backup of your system, then after that you can try it out if it works!

I would also like to inform about that the open source nVidia driver ([Optimus nouveau wiki on the open source driver]("http://nouveau.freedesktop.org/wiki/Optimus")) does not yet support switching between the nVidia and Intel graphics. Linus Torvalds himself expressed last year how he felt about nVidia and the problem with supporting Optimus in the Linux kernel, and it was not positive. So there will probably not be much happening there for a while, so unless the non-free nVidia driver works, you are stuck using the Intel driver only without switching.

The downside of downloading and installing the nVidia driver without adding a repository for it, is that the driver will break each time your Ubuntu system makes a minor upgrade to your Linux kernel, so either you control and make sure that no upgrades are being done to your Linux kernel, or you add a repository for the nVidia kernel, and install the driver from the Ubuntu Software Center, giving the nVidia driver a possibility to receive new updates by automatic and having that working (hopefully) all the time as the new Ubuntu Linux kernel are getting upgraded as time moves forward. So I would recommend an nVidia repository for it for less pain and hassle.

Not sure if this can help you in any way, but hopefully this new nVidia driver can help you out in this!

---

### Post by Wurstinator on 2013-03-22
Sorry for not answering yesterday but I think I managed to get it done myself.
Installing the driver from the Nvidia website didn't work for me, it threw several errors.
Anyway, what I did:
[LIST]
[*]uninstall every package related to nvidia, nouveau or bumblebee
[*]install the newest Nvidia experimental driver with the Ubuntu Hardware Driver Manager
[*]install Bumblebee
[/LIST]
I also restarted after each step, which probably wasn't necessary, but I just wanted to be sure.

I hope this might help, if someone has the same problem in the future.

---

