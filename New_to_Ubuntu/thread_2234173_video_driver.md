---
title: "video driver"
date: 2014-07-13
forum: New to Ubuntu
---

### Post by M_Lawless on 2014-07-13
I am new to the Linux world and I have been having trouble with my laptops video.  I have an older IBM lapatop with an ATI Radeon FireGL 7500 video card.  I loaded Ubuntu 14.04 but it ran very slow.  I did my research and determined it was the video driver that was loaded in the operating system.  I tried, without any luck, to find a new driver.  During my research I did find that version 9.04 worked on my laptop so I loaded 9.04 and it works great now.  There are some things that the newer OS had that 9.04 does not.  Does anyone know how to fix this issue or at least know of a newer version I can install that will work with my video card?

I really liked 14.04 but just cannot get around the video issue.

---

### Post by claracc on 2014-07-13
You problem is with the ATI Radeon graphics driver.

You need specific drivers for it. You can find them in the following ppa repository:

[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa?field.series_filter=trusty](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa?field.series_filter=trusty)

In order to add the ppa and install the proper components, you will have to open a xterm:

CTRL+ALT+T

and there, you write the following code:

```
sudo add-apt-repository ppa:xorg-edgers/ppa

sudo apt-get update

sudo apt-get upgrade
```

System will find the neccesary components, and the problems with graphics will disappear.

It is not recommended to use a no supported release as 9.04, security problems will arise.

---

### Post by Vladlenin5000 on 2014-07-13
> **claracc said:**
> System will find the neccesary components, and the problems with graphics will disappear.

No, it certainly won't. It's a legacy product no longer supported by the manufacturer. It currently uses the open source driver Radeon and that is the best you can have now. 
I'm sorry to disappoint you but the truth is your hardware is too old to support Unity, the standard Ubuntu desktop environment. A different flavor of Ubuntu like Xubuntu or Lubuntu is strongly recommended. I know that Unity is probably the "thing" you like the most in 14.04 but in order to have performing acceptably an hardware upgrade is in order.

That said I also must reiterate the suggestion NOT to use an EoL (end of life) - hence unsupported - release. You absolutely SHOULDN'T use it. Again, what you need is a different DE.

---

### Post by M_Lawless on 2014-07-15
Thanks for the advice.  I will give it a try tomorrow when I get off work and let you know how it comes out.

---

### Post by M_Lawless on 2014-07-18
> **claracc said:**
> You problem is with the ATI Radeon graphics driver.

You need specific drivers for it. You can find them in the following ppa repository:

[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa?field.series_filter=trusty](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa?field.series_filter=trusty)

In order to add the ppa and install the proper components, you will have to open a xterm:

CTRL+ALT+T

and there, you write the following code:

```
sudo add-apt-repository ppa:xorg-edgers/ppa

sudo apt-get update

sudo apt-get upgrade
```

System will find the neccesary components, and the problems with graphics will disappear.

It is not recommended to use a no supported release as 9.04, security problems will arise.

I tried to perform the operation you had in your reply to my issue but the first line would not run.

I finally installed Xubuntu 14.04 which works with my video card.  I also installed Lubuntu and Kubuntu to find one that I liked and finally settled for Xubuntu.  While all three versions were 14.04 it seem like Ubuntu Desktop would install the same drivers.  I hope that they add that update in the future.

Thank you for your assistance in this matter.

---

### Post by claracc on 2014-07-19
Glad you got fixed your problem.

Which code line didn't work? was it ```
sudo add-apt-repository ppa:xorg-edgers/ppa
```?, did you copy and paste the code line in a xterm?.

This is for adding the repository to your system and then with the two other lines (update and upgrade) install the proper graphics drivers.

Please, mark the thread as solved with tread tools in the right upper part of the page.

Thanks.

---

### Post by Rob Sayer on 2014-07-19
I think it's just as well it didn't work.  Actually that ppa ... like all external 3rd party ppa's ... is not supported by ubuntu.  I wouldn't *touch* something like that for something like video with a 10 foot pole unless it just won't work any other way.  And then I'd just reinstall ubuntu when a better supported kernel came out.  3rd party ppa's may work at first but there is a very good chance your video will get borked when you do an update at some point.  

Or,if the ppa holds the kernel version to something that works with it, something else may break later.

The main reason "ubuntu desktop" ... which is actually the Unity DE ... worked so poorly is because it's just not designed for old/slow hardware.  The fact that you're using the open source driver ... which, despite the slowness, is the one you should be using ... doesn't help much.  But it wouldn't work well even on properly supported video cards.

Basically, you don't have 3D hardware acceleration enabled in linux with old AMD gmas.  As mentioned, AMD doesn't support linux for anything but their newer products, and there's no good workaround for this.  My netbook has the infamous ooutsourced Intel GMA3600 and has the same problem.  Fortunately I don't use it to watch videos but I do sympathize with those who want to do so.

So Unity ... or Cinnamon or any other DE that requires 3D accel just to run *itself* ... is a very bad idea on such hardware.  I'd never install any of them on my netbook.

The other thing I'd recommend you do in Xubuntu with no 3D accel is to go into settings and turn off all effects and compositing.

---

