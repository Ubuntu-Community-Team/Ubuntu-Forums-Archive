---
title: "Switching to Ubuntu has crippled my computer. Help!"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by jmacg on 2008-09-01
I have an old Dell P4-1500 with 1Gb RAM and a 40Gb boot drive that had been running XP Home. I decided to reformat the boot drive and set it up with Ubuntu 8.04, mainly for Internet use by visiting family. 

Ubuntu installed smoothly and connected straight up with the Internet. So far so good. But the machine is MUCH more sluggish than it was under XP. OK, a P4-1500 is not a speed demon, but this was ridiculous. Examples:

1. The Torus screen saver runs slowly and jerkily. I’ve seen it running very smoothly on a Celeron 2400 machine.
2. When playing Mah Jong, some tiles I click on take some several seconds to ‘activate’. Others work OK.
3. DVDs sound OK, but they are dropping many frames and look either quite jerky or, at worst, just a procession of still frames.
4. General web browsing feels sluggish. Much slower than on my eee PC900 which only has a Celeron 900 processor.

I’ve read that Ubuntu is a bit bloated and that Xbuntu or Kubuntu might be zippier. How would I switch to Kubuntu? Would I have to reformat the drive and install these alternative OSs from scratch? 

However, I’d rather stay with Ubuntu because I'd have access to a much bigger user support community. I am a Linux newbie and have neither the time nor desire to get too far 'under the hood' to use my machine. (I am prepared to get my hands a bit dirty though.)

Is it unreasonable to expect Ubuntu to run OK on an old P4? I’m not expecting real zip and fire, but the performance I’m getting is ridiculous. Even half as fast as XP with be a huge improvement.

I’ve read that my video driver could need updating. How do I find out what I’ve got and how would I go about getting a better driver and installing it?

Are there any other things I should be looking into?

---

### Post by Gonz_91 on 2008-09-01
In order to get the info, I'd recommend this: [http://www.watchingthenet.com/ubuntu-guide-for-windows-users-display-system-hardware-information.html](http://www.watchingthenet.com/ubuntu-guide-for-windows-users-display-system-hardware-information.html)


After knowing what graphics card you have installed, the drivers are most likely at the manufacturer's website.

---

### Post by kellemes on 2008-09-01
Yes, previous link is fine to get hardware info, especially videocard.
When you have the videocard-info you need to find out how to install the drivers for it, you can always post back so we can help.

---

### Post by kellemes on 2008-09-01
> **Gonz_91 said:**
> In order to get the info, I'd recommend this: [http://www.watchingthenet.com/ubuntu-guide-for-windows-users-display-system-hardware-information.html](http://www.watchingthenet.com/ubuntu-guide-for-windows-users-display-system-hardware-information.html)


After knowing what graphics card you have installed, the drivers are most likely at the manufacturer's website.

Most likely they're not.

---

### Post by Samhain13 on 2008-09-01
> I&#8217;ve read that Ubuntu is a bit bloated and that Xbuntu or Kubuntu might be zippier. How would I switch to Kubuntu? Would I have to reformat the drive and install these alternative OSs from scratch?

You don't have to reinstall. Just **sudo apt-get install xubuntu-desktop** or **sudo apt-get install kubuntu-desktop** to install Xubuntu or Kubuntu, respectively.

Of course, installing either desktop will require a bit more disk space-- but not so much. For community support, you can still use this forum.

Cheers! :)

---

### Post by Sef on 2008-09-01
> I’ve read that Ubuntu is a bit bloated and that Xbuntu or Kubuntu might be zippier

Kubuntu and Ubuntu are about the same size, so not much of a difference in how fast they would be.  Xubuntu would be faster since it is made lightweight.

---

### Post by halitech on 2008-09-01
I've got a homebuilt P4 1.8 with 896 meg of ram and a 160 gig hard drive and I find it is alot faster then my old windows 2000 install every was. I'm doing the hard info now 

[http://macdonaldfamily.ath.cx/personal/hardinfo_report.html](http://macdonaldfamily.ath.cx/personal/hardinfo_report.html)

---

### Post by aimpau on 2008-09-01
I had my xubuntu running on my GF's old laptop:

P3
128MB RAM
7GB HD
4MB video card

and it was running better than my XP.

I can watch movies w/ xine-ui AND edit my music composition with seq24 AND edit raster graphics w/ gimp.

Check your video card:

```

gksu displayconfig-gtk

```

---

### Post by jmacg on 2008-09-01
Many thanks to the poster and the rest of you for your comments and suggestions. It's good to know that I _should_ be able to get decent performance on my P4-1500.

Unfortunately I won't be able to try out your suggestions until the end of the week, when I'll be back where the computer is installed.

One thing I'd like to know, in case I can find a better video driver, is how to install it. I'm still a bit bemused by the program installation processin Linux and have no idea how to install a video driver.

Thanks
John

---

### Post by kansasnoob on 2008-09-01
If you want to change desktops look at this section:

> Playing Around
Enable Desktop Effects
KDE/Gnome Comparison
Install Gnome
Install KDE
Install XFCE
Install IceWM
Install XPDE
Pure Gnome
Pure KDE
Pure XFCE
A faster KDE
Replacing Nautilus 

of this tutorial:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

To make changing desktops simpler in the future it's best to use aptitude rather than apt-get as you can see here:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by halitech on 2008-09-01
> **jmacg said:**
> One thing I'd like to know, in case I can find a better video driver, is how to install it. I'm still a bit bemused by the program installation processin Linux and have no idea how to install a video driver.

Thanks
John

typically Linux will probe all the hardware on every boot and *should* install a compatible driver on boot. There are a few ways of installing video card drivers (both manually and with a script) in case it doesn't detect the best one or you want to install the non-free version.

---

### Post by jmacg on 2008-09-06
I'm back with the computer in question again and I've discovered that the Dell P4-1500 has an ATI Rage 128 video card. I still don't know how I check if my drivers are up to date or how to update them.

As the card is years older than Ubuntu 8.04, shouldn't any Ubuntu driver be the latest it could be?

---

### Post by knix on 2008-09-06
as far as I know you need to use the "ati" driver. check in your /etc/X11/xorg.conf, Section "Device"  "Driver" line. The problem is that the best drivers may not be enabled by default. the "ati" driver is an open source 3d driver, and I don't believe that the binary only driver (flgrx) supports the rage 128.

---

### Post by otamotacon on 2008-09-06
i have pretty much the same specification on my computer. it crashed with windows 2000. with Ubuntu it is faster and just an all around better OS. I'm not sure what could be wrong with yours.

---

### Post by knix on 2008-09-06
sluggish games, dvd playback problems, sluggish web browsing are all symptoms of video problems. (web browsing has to do with rendering). You're probably not using a very good driver. this does not mean that your driver is out of date, just not ideal. Try switching drivers. the ati driver has acceleration, but has some problems; the vesa diver is more stable without acceleration.

---

### Post by jmacg on 2008-09-06
> **knix said:**
> sluggish games, dvd playback problems, sluggish web browsing are all symptoms of video problems. (web browsing has to do with rendering). You're probably not using a very good driver. this does not mean that your driver is out of date, just not ideal. Try switching drivers. the ati driver has acceleration, but has some problems; the vesa diver is more stable without acceleration.
Sorry - I'm a newbie - where would I get the vesa driver and how would I install it?

---

### Post by knix on 2008-09-08
Sorry for the delay.
In the file /etc/X11/xorg.conf, there is a sction "Device".
Within that section there is a lin "Driver"
Just change your driver to "vesa"
It's installed by default.

I will warn you, however, that it probably won't perform very well. It's a generic driver. However, it is at least stable.

---

### Post by jmacg on 2008-09-08
Knix said, "I will warn you, however, that it probably won't perform very well. It's a generic driver. However, it is at least stable."

Could I be going from the frying pan to the fire!

If it's worse than whatever driver installed itself when Ubuntu was installed, how can I reinstall that orginal driver?

No problems re your delay in replying because I'm kind sorting this out at arm's length too. The computer is in our out-of-town weekender cottage that I only get to in the weekends. 

I guess from what you're effectively saying is that the Rage 128 card just doesn't cut it with Ubuntu. Any recommendations for a _cheap_ video card that will work OK? It doesn't have to be super-fast - no one plays games on the machine.

Thanks
John

---

### Post by knix on 2008-09-08
to switch back, just change the driver line to the original. all the open source drivers are installed by default.

for an alternate: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814139150]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814139150")
or something similar. I don't know about ATI pci cards - drivers can be dificult to set up.

---

### Post by jmacg on 2008-09-09
Thanks very much.

John

---

