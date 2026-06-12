---
title: "Complete newbie... need help with Compiz"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by estebancam on 2011-10-29
So I have installed Compiz for the sole purpose of the 3D cube and the Wobbly windows. I really, really like those effects, and they are what really drew me to install Ubuntu two days ago. I have been trying for the last two days, and cannot get ANYTHING AT ALL from Compiz to work. I enable wobbly windows, and nothing happens. I enable the  3D rotation, yet nothing happens. 

I really need the help since I am new to all this, and more importantly, the features that drew me to this OS are not working. :-(

Thanks in advance!

---

### Post by sadaruwan12 on 2011-10-29
Welcome to the forum.

Can you please tell us what is the version of Ubuntu you're using and how did you install compiz and what components you've installed.

---

### Post by estebancam on 2011-10-29
Thanks for the welcome!

I am running version 11.10, which I believe is the latest one. I installed it using the Wubi method so I can run it alongside windows (only for emergencies... I don't like Windows)

I have installed only compiz and a few drivers to make my Synoptics Trackpad work like it's supposed to. 

I dug around a little more, and I saw on my "System Info" that it doesn't recognize my ATI graphics card... is this perhaps the error, since everything I am trying to do is graphical?

---

### Post by estebancam on 2011-10-29
Also, there are two drivers that the "Additional Drivers" program is telling me to install. Both for ATI graphics sets. One of them was installed successfully, the other is giving me the following error:

Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

---

### Post by blade4 on 2011-10-29
Try installing compiz-plugins-extra from synaptic .... dunno why but that did the trick for me on lucid .

---

### Post by estebancam on 2011-10-29
> **blade4 said:**
> Try installing compiz-plugins-extra from synaptic .... dunno why but that did the trick for me on lucid .

Ok downloading synaptic now.

---

### Post by sadaruwan12 on 2011-10-29
Only one driver will work no need for the second one to be installed. And in 11.10 the wobbly windows that you wanted is not much recognized 'cos the appearance is set automatically.

and install compizconfig-settings-manager and the extra plugins after that you can tweak the windows the way you want. And the other thing wobbly windows and other effects mostly works with GNOME in 11.10 it's unity which runs on top of GNOME environment so some times effects might not be that dashing as one accepted.

---

### Post by estebancam on 2011-10-29
> **blade4 said:**
> Try installing compiz-plugins-extra from synaptic .... dunno why but that did the trick for me on lucid .

No luck, or so it seems. Darn... I can't get this to work....

---

### Post by estebancam on 2011-10-29
> **sadaruwan12 said:**
> Only one driver will work no need for the second one to be installed. And in 11.10 the wobbly windows that you wanted is not much recognized 'cos the appearance is set automatically.

and install compizconfig-settings-manager and the extra plugins after that you can tweak the windows the way you want. And the other thing wobbly windows and other effects mostly works with GNOME in 11.10 it's unity which runs on top of GNOME environment so some times effects might not be that dashing as one accepted.

Ok I will download that. 

One more question, what about music? My music won't play. I just transfered it from a hard drive to the computer and it says I need a plug in but cannot find that plug in.

---

### Post by sadaruwan12 on 2011-10-29
> **estebancam said:**
> No luck, or so it seems. Darn... I can't get this to work....

My dear friend wobbly windows is a GNOME advance effect which came with GNOME 2.xx but after Ubuntu moved to unity it's not there but you can enable and use the extra effect like the burn effect or leaf fold they look very cool when assigned to a windows functions using the manager please try that.

---

### Post by sadaruwan12 on 2011-10-29
> **estebancam said:**
> Ok I will download that. 

One more question, what about music? My music won't play. I just transfered it from a hard drive to the computer and it says I need a plug in but cannot find that plug in.


Can you tell me what is the format your music is in mp3, wma, rma .. etc

---

### Post by estebancam on 2011-10-29
> **sadaruwan12 said:**
> Can you tell me what is the format your music is in mp3, wma, rma .. etc

MP3, mp4, and some AAC, but not too many. Mostly MP3.

---

### Post by estebancam on 2011-10-29
Also, I still cannot get ANYTHING from Compiz to work. Nothing at all. Not wobbly windows, not expo, not animation, not water effects, nothing at all whatsoever. What is the issue? 

With this much stuff not working, WIndows is almost better. lol.

---

### Post by beew on 2011-10-29
> **sadaruwan12 said:**
> My dear friend wobbly windows is a GNOME advance effect which came with GNOME 2.xx but after Ubuntu moved to unity it's not there but you can enable and use the extra effect like the burn effect or leaf fold they look very cool when assigned to a windows functions using the manager please try that.

This is just not true. I have activated wobbly windows and the cube in 11.10 and other effects without problem(burn, magic lamp etc, which require the extra plugins but not the cube or wobbly windows) Unlike in 11.04 it was tricky to play with the ccsm with 11.10 it is as easy as it could be. I am not on the computer with 11.10 installed now but I wish I am so I can post a screenshot.


BTW, Unity is Compiz (more precisely it is a Compiz plugin) and wobbly windows is a Compiz effect.


@Op,

It could be your graphic card (which one is it?)  or WUBI. If you don't like WIndows as you said why not at least do a real dual boot so that Ubuntu is given an equal footing as Windows? WUBI is not a real dual boot and you will experience problems that otherwise don't exist.

---

### Post by estebancam on 2011-10-29
> **beew said:**
> This is just not true. I have activated wobbly windows and the cube in 11.10 and other effects without problem(burn, magic lamp etc, which require the extra plugins but not the cube or wobbly windows) Unlike in 11.04 it was tricky to play with the ccsm with 11.10 it is as easy as it could be. I am not on the computer with 11.10 installed now but I wish I am so I can post a screenshot.


BTW, Unity is Compiz (more precisely it is a Compiz plugin)


@Op,

It could be your graphic card, or WUBI. If you don't like WIndows as you said why not at least do a real dual boot so that Ubuntu is given an equal footing as Windows? WUBI is not a real dual boot and you will experience problems that otherwise don't exist.

That's exactly what I was thinking. The graphics card was not recognized, so I thought that may be it. I also thought it may be the WUbi system of installation. 

I am a little afraid of doing the full dual boot because I am not computer savvy. Is there a place I can get idiot proof instructions on how to do it? I already have Ubuntu downloaded on a separate CD, which was about 700MB. WHat do I do from there?

---

### Post by Miljet on 2011-10-29
[http://news.softpedia.com/news/Installing-Ubuntu-11-10-227809.shtml](http://news.softpedia.com/news/Installing-Ubuntu-11-10-227809.shtml)

---

### Post by beew on 2011-10-29
Before you make a dual boot though you probably should test with a live usb to make sure that the hardware works ok. You may need to install something or reboot so you should make a live usb with persistence so you can store your settings on reboot. 

Use this tool to make a live usb with persistence in Windows
[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

Live usbs are slow, it doesn't give you a true glimpse of performance, butit is good for testing basic compatibility. A much better way would be to make a full install of Ubuntu on an external hard drive (say an old hard drive from a dead computer will do) This would allow you to do things like system updates and installing proprietary drivers etc, which are not supported in live usb mode. It is also fast because it is a real install, you can do everything that is allowed in an installation in internal drive with this set up.

Here is a guide
[http://ubuntuforums.org/showthread.php?t=1650699&page=2](http://ubuntuforums.org/showthread.php?t=1650699&page=2)
It is for installing 10.04 in an usb, but the same procedure works for installing 11.10 in an external hard drive with some modifications (the layout of the installer is a bit different in 10.04 than 11.10, you can see the updated screenshot in Miljet's post above)

Basically you install just as you would in the internal hard drive but set the target drive to the external one (say sdb or sdc, sda is usually the internal hard drive, don't touch it) and the crucial point is to install the bootloader in the targeted drive (so it would be sdb or sdc,say) You choose where to install the bootloader in the allocate drive space window (the box in the bottom), see Mijet's link.

(Some people recommend removing the internal drive first if you are afraid of messing things up, though I never do that)

---

### Post by antoinethewiz on 2011-10-30
From what I understand from personal experience, Compiz won't work on 11.10 (but it will on [11.04]("http://ubuntuforums.org/showthread.php?t=1754637")) properly if you enable anything OpenGL. I did and my GUI disappeared. So I fellback to console, rebooted, and removed Compiz with the command "dpkg -r compiz compiz-plugins-extra compiz-plugins-main compizconfig-settings-manager".

---

### Post by fractalman on 2011-10-30
If you having trouble playing your music you might need some codecs, did you install the restricted extras package? it contains loads of stuff for playing your media  its in the repositories as  ubuntu-restricted-extras

---

### Post by beew on 2011-10-30
> **antoinethewiz said:**
> From what I understand from personal experience, Compiz won't work on 11.10 (but it will on [11.04]("http://ubuntuforums.org/showthread.php?t=1754637")) properly if you enable anything OpenGL. I did and my GUI disappeared. So I fellback to console, rebooted, and removed Compiz with the command "dpkg -r compiz compiz-plugins-extra compiz-plugins-main compizconfig-settings-manager".

That is plainly false. Unity is a Compiz plugin and it requires Compiz to work. Maybe Ubuntu11.10 with Unity 3d doesn't work on your system for hardware reasons, but there is no way that it doesn't work in Ubuntu 11.10 in general.

---

