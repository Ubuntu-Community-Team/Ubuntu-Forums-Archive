---
title: "Best distro for Asus EEE PC 701?"
date: 2008-12-25
forum: Other OS Talk
---

### Post by miggols99 on 2008-12-25
Currently I have ubuntu eee installed on here, but it is running a bit slow. Is there a different distro I can try on here that will run faster?

---

### Post by jheaton5 on 2008-12-25
A popular solution is to install intrepid 8.10 and then ubuntu remix on top of it.  See this link: [http://www.canonical.com/projects/ubuntu/nbr]("http://www.canonical.com/projects/ubuntu/nbr") and this one: [http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html]("http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html")

---

### Post by miggols99 on 2008-12-25
Won't I need to install other things like the wireless drivers? I would really like one that works out of the box...

---

### Post by oswaldkelso on 2008-12-25
[http://wiki.debian.org/DebianEeePC](http://wiki.debian.org/DebianEeePC)

[http://wiki.debian.org/DebianPureBlends](http://wiki.debian.org/DebianPureBlends)

[http://lottalinuxlinks.com/podcast/ogg.xml](http://lottalinuxlinks.com/podcast/ogg.xml)

Dave Yates Talks about different distros on a eee pc in episopes 99 +100

---

### Post by miggols99 on 2008-12-26
Any more ideas? Debian doesn't seem to work very well for me...

---

### Post by Old_Grey_Wolf on 2008-12-26
A different Ubuntu remix like Eeebuntu perhaps. [http://www.eeebuntu.org/](http://www.eeebuntu.org/)

Eeebuntu worked out of the box on my wife's EEE PC 701/4G.

Downloaded Eeebuntu NBR ISO. Used "System > Administration > Create a USB startup disk" in 8.10 running on my laptop.

Put the USB stick in my wife's EEE and booted it. Had to hit the F2 key to change BIOS options, if I remember right, to get it to boot from the USB stick.

Followed the install instructions. Done. Just works fine for her now.

---

### Post by wolfen69 on 2008-12-26
i wrote a [tutorial]("http://forum.eeeuser.com/viewtopic.php?pid=470417#p470417") at eeeuser.com on how to get ubuntu installed on a eeepc 2G Surf. it is a minimal install with tweaks specific for the eeepc. mine runs very fast.

---

### Post by kamitsukai on 2008-12-26
One that I find very nice out of the box is linux mint although just a remix of ubuntu with all the nasty drivers and codecs installed (he says jokingly...) theres nothing stopping you from installing the ubuntu remix on this (linux mint is fully compatible with ubuntu packages)

[http://linuxmint.com](http://linuxmint.com)

---

### Post by wolfen69 on 2008-12-26
> **kamitsukai said:**
> **theres nothing stopping you** from installing the ubuntu remix on this (linux mint is fully compatible with ubuntu packages)

[http://linuxmint.com](http://linuxmint.com)

except if he only has a 2gb drive. then you are *very* limited.

---

### Post by miggols99 on 2008-12-27
> **Old_Gray_Wolf said:**
> A different Ubuntu remix like Eeebuntu perhaps. [http://www.eeebuntu.org/](http://www.eeebuntu.org/)

Eeebuntu worked out of the box on my wife's EEE PC 701/4G.

Downloaded Eeebuntu NBR ISO. Used "System > Administration > Create a USB startup disk" in 8.10 running on my laptop.

Put the USB stick in my wife's EEE and booted it. Had to hit the F2 key to change BIOS options, if I remember right, to get it to boot from the USB stick.

Followed the install instructions. Done. Just works fine for her now.
I did this with the base ISO, and all I get is a blinking line, and nothing appears to be happening. I've set the BIOS to boot from the USB drive...maybe the NBR ISO will work better?

---

### Post by MattBD on 2008-12-27
[Sidux ]("http://sidux.com/")works really well on the Eee PC. There's a KDE and Xfce version.I briefly ran the Xfce version on my 2G Surf, but there wasn't really enough room for it. It should be fine with 4G though.
You can install it on a pendrive using the built-in pendrive installer, then use the pendrive to install it on the Eee PC. While it doesn't support the wireless card out of the box, it's very easy to set it up - just run the fw-detect command and it will find your wireless card and will actually tell you how to install the driver.
I also liked the network management tool, Ceni. It's command-line based, but extremely powerful.
The provided documentation is REALLY good too.
One further advantage is that like Ubuntu it's a Debian derivative, so many of your existing Ubuntu skills will still be useful.

---

### Post by BigSilly on 2008-12-28
> **Old_Gray_Wolf said:**
> A different Ubuntu remix like Eeebuntu perhaps. [http://www.eeebuntu.org/](http://www.eeebuntu.org/)

Eeebuntu worked out of the box on my wife's EEE PC 701/4G.

Downloaded Eeebuntu NBR ISO. Used "System > Administration > Create a USB startup disk" in 8.10 running on my laptop.

Put the USB stick in my wife's EEE and booted it. Had to hit the F2 key to change BIOS options, if I remember right, to get it to boot from the USB stick.

Followed the install instructions. Done. Just works fine for her now.

+1 here.

We installed this on the Asus 701 we got for the kid's Christmas present. Absolutely gobsmacked. It's a tremendous OS for the Eee. I tried Ubuntu-Eee but it just wouldn't work. EeeBuntu was a dream to install to USB thanks to Intrepid, and a breeze to install to the Eee itself. Cue thrilled daughter come Christmas morning! 

The only thing to remember is if you want to use the webcam you have to first enable it in the Eee's BIOS, then install Cheese from Synaptic. Once that's installed, go into the Cheese preferences and set the camera to 320x240 resolution or it won't work. Works great now.

For me, this is definitely how you want to see Ubuntu on the Eee. No fuss, just a simple install easily configured. Highly recommended.

---

### Post by maluka on 2008-12-29
> **BigSilly said:**
> +1 here.

We installed this on the Asus 701 we got for the kid's Christmas present. Absolutely gobsmacked. It's a tremendous OS for the Eee. I tried Ubuntu-Eee but it just wouldn't work. EeeBuntu was a dream to install to USB thanks to Intrepid, and a breeze to install to the Eee itself. Cue thrilled daughter come Christmas morning! 

The only thing to remember is if you want to use the webcam you have to first enable it in the Eee's BIOS, then install Cheese from Synaptic. Once that's installed, go into the Cheese preferences and set the camera to 320x240 resolution or it won't work. Works great now.

For me, this is definitely how you want to see Ubuntu on the Eee. No fuss, just a simple install easily configured. Highly recommended.

I also installed eebuntu netbook remix on my daughter's eeepc 701 over christmas. we first upgraded the ram to 2gb. ram is super cheap these days! she's had it for close to a year now and the new OS refresh was very exciting for her. everything worked out of the box which is all you could ever wish for.:D


on a side note though, eeebuntu will be changing their name to easy peasy after they were pressured to do so by ubuntu. 

[http://www.eeebuntu.org/](http://www.eeebuntu.org/)

---

### Post by BigSilly on 2008-12-30
> **maluka said:**
> I also installed eebuntu netbook remix on my daughter's eeepc 701 over christmas. we first upgraded the ram to 2gb. ram is super cheap these days! she's had it for close to a year now and the new OS refresh was very exciting for her. everything worked out of the box which is all you could ever wish for.:D


on a side note though, eeebuntu will be changing their name to easy peasy after they were pressured to do so by ubuntu. 

[http://www.eeebuntu.org/](http://www.eeebuntu.org/)

Thanks for the info. I thought it wouldn't be too long before the name would have to be changed.

I didn't know you could upgrade the RAM in an Eee. How do you go about doing that, and what do I need to buy? Thanks in advance.

---

### Post by miggols99 on 2008-12-30
> **maluka said:**
> on a side note though, eeebuntu will be changing their name to easy peasy after they were pressured to do so by ubuntu. 

I have installed it now, and it works great! Although the boot times are a bit slow...is there a way to speed it up a bit?

---

### Post by Old_Grey_Wolf on 2008-12-30
> **miggols99 said:**
> I have installed it now, and it works great! Although the boot times are a bit slow...is there a way to speed it up a bit?

Just my opinion.

You may be expecting too much from a computer with a 900 MHz processor, 512 MB RAM, and 4 GB SSD.

I haven't seen specs that low in years. :P

I may find some time to create a bootchart in order to see what is taking so long in the boot sequence.

You may find something on the Eeebuntu forum ([http://forum.eeebuntu.org/](http://forum.eeebuntu.org/)) about speeding up boot time.

---

### Post by Old_Grey_Wolf on 2008-12-30
> **maluka said:**
> on a side note though, eeebuntu will be changing their name to easy peasy after they were pressured to do so by ubuntu.

Eeebuntu and Ubuntu Eee are different projects. Ubuntu Eee is changing its name. Eeebuntu from what I have read is not.

I have no problems with Canonical protecting their brand name - Ubuntu.

When I tried Ubuntu Eee, I con't get it to boot. Like BigSilly said above, it just didn't work. :) 

Ubuntu Eee is also based on 8.04.1 with a 8.10 release sometime in January 2009 (Easy Peasy). Eeebuntu is already at 8.10.

---

### Post by snowpine on 2008-12-30
The newest kid on the block is Cruncheee, an eee pc port of CrunchBang Linux: [http://crunchbanglinux.org/forums/topic/424/cruncheee-81001-release-candidate-1/](http://crunchbanglinux.org/forums/topic/424/cruncheee-81001-release-candidate-1/)

Highly recommended if you're a minimalist like me!

---

### Post by cmay on 2008-12-31
i use crunch bang on a asus Eee PC 701 sd . 
it works with a minmial amount of tweaking. which is installing a new kernel from array.org and it is a matter of a little shellscript on two lines to take care of that. i finds the webcam after you have played around in bios settings and enabled the webcam which is for some reason of by default from factory settings and the only thing i have a problem with is to figure out if or how it will use the sd card. i just been in the hospital for 8 days which is why i got my self a little notebook to use in there and it was working wonderful for me. i have tweaked it a bit doing my stay in there by adding removing some programs and making lots of new background wall papers on the gimp but i timed it boot and it takes around 60 sec to boot  and then  you are at the login screen. however it plays supertux really fast. the programs pop up a little slower than i am used to on gnome but i can say that consider the specs on a new asus it is really fast once it is going and it takes games and gimp and even movies from a extern dvd unit with same ease as any of the other pc i have. i would say besides debian which i want to install someday in my asus i cant imagine any ohter than crunch bang or the one called linpus linux light which comes preinstalled on some notebooks  as replacement for xandros .

---

### Post by jrusso2 on 2009-01-02
> **miggols99 said:**
> Won't I need to install other things like the wireless drivers? I would really like one that works out of the box...

Heck, even the one that comes with it Xandros does not work out of the box.  I have had many complain to me that the camera and wireless were not working when they got it.

---

### Post by jrothwell97 on 2009-01-04
> **jrusso2 said:**
> Heck, even the one that comes with it Xandros does not work out of the box.  I have had many complain to me that the camera and wireless were not working when they got it.
The camera works fine, it's just the fact that Xandros (or the distribution of it supplied with the 701) only supports WEP encryption over WLAN, no WPA. Incidentally, the Eee distribution in particular of Xandros is evil and it must die.

Ubuntu Intrepid should work OK on the Eee, but I've been impressed with Fedora 10&#8211;everything works out of the box with it (except Cheese, which needs a bit of fiddling to get it to work).

---

### Post by Old_Grey_Wolf on 2009-01-04
> **jrothwell97 said:**
> I've been impressed with Fedora 10–everything works out of the box with it (except Cheese, which needs a bit of fiddling to get it to work).

I'm interested in anything that works on the EeePC. How well does Fedora 10 handle the small screen resolution? Do you have to use ALT + left click to move windows around so you can see parts of the windows? 

Sorry, it took to much time to get my wife Eee set up with all her email and pics for me to just download and try it.

---

### Post by cmay on 2009-01-05
[http://opengeu.intilinux.com/News/Voci/2008/9/16_OpenGeeeU_8.04.1_Live_CD_for_EeePC_released.html](http://opengeu.intilinux.com/News/Voci/2008/9/16_OpenGeeeU_8.04.1_Live_CD_for_EeePC_released.html)

i am also very interested in everything that has t do with the eeepc so i found this and i am downloading right now. maybe you could use the link.

---

### Post by wolfen69 on 2009-01-06
> **cmay said:**
> [http://opengeu.intilinux.com/News/Voci/2008/9/16_OpenGeeeU_8.04.1_Live_CD_for_EeePC_released.html](http://opengeu.intilinux.com/News/Voci/2008/9/16_OpenGeeeU_8.04.1_Live_CD_for_EeePC_released.html)

i am also very interested in everything that has t do with the eeepc so i found this and i am downloading right now. maybe you could use the link.

no one is seeding! damn. :(

---

