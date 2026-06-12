---
title: "easy question im sure"
date: 2005-04-04
forum: Outdated Tutorials &amp; Tips
---

### Post by cinders on 2005-04-04
sorry for the trivial question but i'm so new at this, and i don't want to mess my nice looking new system up.

here is my question...how do i install new packages in synaptic...im trying to get my wireless card working, and i'm following the ndiswrapper howto faq on the main ubuntu page but i can't seem to get past stage 1... 

i'd love to sit down and read all the documentation right now, but i'd really like to do it from my new laptop and it needs some internet...anyways, i downloaded the ndiswrapper1.1.tar but im not sure if i even need this...i just want to know how to install it so i can keep going with the faq.

im using Ubuntu 4.10

thanks

---

### Post by gw90se on 2005-04-04
First, click on "Reload" to make sure that Synaptic is up to date
Find your package, click on the little box and select "mark for download". It may sat that others items are needed, too. Click OK. Then click "apply" at the top of the page.

I prefer using apt-get, though, so I can see what is happening better.

---

### Post by az on 2005-04-04
If you are trying to install it from source because the version you already have does not work, try (from a console)

sudo apt-get install linux-headers-2.6.8.1-3-386 (If this is your running kernel - If you are running Warty and have no internet acces, yes it is.)

tar xvzf ndisw*
cd ndiswrapper*
sudo debian/rules binary
cd ..
sudo dpkg -i ndiswapper*.deb
cd (to where your driver is)
sudo ndiswrapper -i xxxxxxxx.inf
ndiswrapper -l
sudo modprobe ndiswrapper

Go to the networking thingy.  It should be device wlan0.

Lemme know if I forgot a step.

---

### Post by telmo on 2005-04-04
This solved all my problems regarding ndiswrapper. I stole it from this forum somewhere  O:) 
[QUOTE=rob martin]I got the latest ndiswrapper source from here [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/) and following the posting here [http://ubuntuforums.org/showthread....ndiswrapper+deb](http://ubuntuforums.org/showthread....ndiswrapper+deb) simply did sudo make deb and installed the packages using dpkg -i.
It didn't work, as the new deb package placed the new ndiswrapper kernel module in /lib/modules/2.6.10-5-686/misc rather than work out why, and as a quick and dirty hack, I just copied the new ndiswrapper.ko to /lib/modules/2.6.10-5-686/kernel/drivers/net/ndiswrapper/ndiswrapper.ko

then did a sudo modprobe ndiswrapper

make sure you back up the original ndiswrapper.ko to another place, so if it doesn't work, you can always drop it back in, without the need to reinstall the kernel image

It'll work for now, but it's not pretty, every time you upgrade the kernel package you'll have to repeat the process.

You could always wait a few days and get a fixed up ndiswrapper deb from Hoary.

hope this helps[/QUOTE]

---

