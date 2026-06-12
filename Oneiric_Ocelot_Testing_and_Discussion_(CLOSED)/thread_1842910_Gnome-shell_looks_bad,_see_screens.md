---
title: "Gnome-shell looks bad, see screens"
date: 2011-09-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ale.junuzovic on 2011-09-12
[IMG]http://i52.tinypic.com/zn4qo3.jpg[/IMG]



Fresh installed 11.04, then updated to 11.10 and installed gnome shell. Naut. giving error report. I don t know what to do, any help?

---

### Post by NightwishFan on 2011-09-12
What kind of graphics card do you have and if available did you install a proprietary driver from the hardware drivers tool? If you answer Nvidia/ATI and the answer is no I did not install the driver.. Try installing the driver and rebooting to see if it fixes. If not you can optionally revert it or not if it gives you a worse experience. With Nvidia it will certainly give a better one, with ATI it might be mixed.

---

### Post by ale.junuzovic on 2011-09-12
Thanks for your reply. I ave an ATI HD Radeon 4 Series with suggest driver installed. Should i remove it?

---

### Post by 23dornot23d on 2011-09-12
Gnome Shell will usually come up with a error in the first place if the graphics are not
suitable then - it will not start and drops into fallback mode.

My first thoughts are the Graphics driver ..... but if its installed and Gnome Shell is running ..... 

then try to ensure that it is a graphics driver problem first ....

Does Unity 3D run ok ..... what are the screenshots like from it ... ?


Try this first ......

apt-get update 
apt-get install aptitude
aptitude reinstall gnome-shell

see if there are any changes ..... maybe the full package did not install ..... maybe 
its a [[COLOR=Red]_**mutter**_[/COLOR]]("http://en.wikipedia.org/wiki/Mutter_%28window_manager%29") problem  ....

---

### Post by jcphil on 2011-09-12
I have the same problem, as do many others. I have an ATI graphics card with the Catalyst driver (proprietary). ATI is aware of the problem and is promising a fix in October. Maybe you can use the open source driver. I can't, because my laptop overheats when I'm not using the Catalyst driver. Unity 3D should be unaffected by this issue.

---

### Post by ale.junuzovic on 2011-09-12
jcphil thnx! how do you follow the gpu sensor? i mean the FGLRX driver (suggested by ubuntu) doesnt offer a view into.

---

### Post by effenberg0x0 on 2011-09-12
I never had anything ATI so I'm not totally sure. But, generally, you can see hardware sensors (CPU, GPU, etc) by installing lm-sensors.

```
sudo apt-get install lm-sensors
sudo sensors-detect
sensors
```Up to this point, there are indicator apps, screenlets, whatever, that will read info from sensors and display them in nicer GUI ways.

Regards,
Effenberg

--------------------------
Ubuntu Oneiric is Beta 1. It is expected to not work 100% and is not what I would personally recommend for anyone that just needs to get the job done. It's aimed at beta testers and people that can afford to have a broken PC right now. So PLEASE: DO NOT attempt any of the mentioned procedures if you're working on a server / production machine, if you don't have backup of your data or if you don't have the habit of performing fixes in Ubuntu / Linux distros. You can end up having to do a new install from scratch. I can't be held responsible for any damage, ok? :-)

---

### Post by jbicha on 2011-09-12
This is a known issue with ATI's proprietary driver; unfortunately I don't think ATI will be releasing the fix until after Ubuntu 11.10 is released. See [bug 838577]("http://pad.lv/838577") .

---

### Post by ale.junuzovic on 2011-09-12
> **effenberg0x0 said:**
> I never had anything ATI so I'm not totally sure. But, generally, you can see hardware sensors (CPU, GPU, etc) by installing lm-sensors.

```
sudo apt-get install lm-sensors
sudo sensors-detect
sensors
```Up to this point, there are indicator apps, screenlets, whatever, that will read info from sensors and display them in nicer GUI ways.

Regards,
Effenberg

--------------------------
Ubuntu Oneiric is Beta 1. It is expected to not work 100% and is not what I would personally recommend for anyone that just needs to get the job done. It's aimed at beta testers and people that can afford to have a broken PC right now. So PLEASE: DO NOT attempt any of the mentioned procedures if you're working on a server / production machine, if you don't have backup of your data or if you don't have the habit of performing fixes in Ubuntu / Linux distros. You can end up having to do a new install from scratch. I can't be held responsible for any damage, ok? :-)

I ave got it at the aticonfig - it s 64.5, on windows 50 - 53 

so i enabled ati overdrive, but didn t got a better result because 

```
 Configurable Peak Range : [600-790]     [900-1100]
``````

```

I remember at the win driver you are able to change the peak range to 450 and mhz to 700, which cools it down. 

jbicha, thank you.

---

