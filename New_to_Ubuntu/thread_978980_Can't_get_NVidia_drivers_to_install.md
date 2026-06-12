---
title: "Can't get NVidia drivers to install"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by Marcel Beaudoin on 2008-11-11
I go to System -> Admin -> Hardware Drivers and it shows me two possible NVidia drivers (173 and 177). I choose 177 (recommended) and then click on Activate. It asks for my password, I enter it, and then a downloading screen comes up. It disappears after a couple of seconds, never getting past 0%, and the driver remains unactivated.

I am connected to the internet.

HELP!!

---

### Post by Elfy on 2008-11-11
sometimes it can take a while for it to connect to the source - have you tried more than once?

If you have, open software sources - Sys>Admin menu - make sure that open, multiverse, universe and restricted are enabled

---

### Post by phidia on 2008-11-11
Open synaptic and click the reload icon.
Then try to enable that driver again.

---

### Post by Technoviking on 2008-11-11
What NVidia card do you have? 

Also, the Ubuntu servers are still slow due to downloads of the isos (Uses the torrents Luke!!!), so it may take a few minutes.

I would suggest using the 173 driver, unless you have the latest and greatest NVidia card.

---

### Post by waffen on 2008-11-11
I have installed the 177 with my Nvidia and I dont have problems, for what it your recomendation?

---

### Post by sharkster2007 on 2008-11-11
Have you tried this on my thread:
[http://ubuntuforums.org/showthread.php?t=973038](http://ubuntuforums.org/showthread.php?t=973038)

It worked for me on my Nvidia 6600GT (AGP) Card and has worked for others, hope it helps you, as it was a pain in the butt for me too, until I worked it out :-)

*My machine is NOT on the internet, I am downloading individual files from a windows web browser, but have located the individual files and websites needed to get it to work*

PS It is up and running on mine, was down to 3 individual .deb files required

---

### Post by Marcel Beaudoin on 2008-11-11
> **forestpixie said:**
> sometimes it can take a while for it to connect to the source - have you tried more than once?

If you have, open software sources - Sys>Admin menu - make sure that open, multiverse, universe and restricted are enabled

I tried it several times, and it didn't work any of them. I went to Software sources, and it looks as if third-party software wasn't enabled. I enabled it and it is now downloading a bunch of different packages.


> **phidia said:**
> Open synaptic and click the reload icon.
Then try to enable that driver again.

Synaptic??

> **Technoviking said:**
> What NVidia card do you have? 

Also, the Ubuntu servers are still slow due to downloads of the isos (Uses the torrents Luke!!!), so it may take a few minutes.

I would suggest using the 173 driver, unless you have the latest and greatest NVidia card.

I have an NVidia GeForce 6150 that is onboard my motherboard. I tried both drivers, neither one worked.

> **waffen said:**
> I have installed the 177 with my Nvidia and I dont have problems, for what it your recomendation?

I am just going off of what Ubuntu recommended to me.

---

### Post by Marcel Beaudoin on 2008-11-11
> **sharkster2007 said:**
> Have you tried this on my thread:
[http://ubuntuforums.org/showthread.php?t=973038](http://ubuntuforums.org/showthread.php?t=973038)

It worked for me on my Nvidia 6600GT (AGP) Card and has worked for others, hope it helps you, as it was a pain in the butt for me too, until I worked it out :-)

*My machine is NOT on the internet, I am downloading individual files from a windows web browser, but have located the individual files and websites needed to get it to work*

PS It is up and running on mine, was down to 3 individual .deb files required

I will be trying your method as well if the stuff suggested above doesn't work.

---

### Post by RJARRRPCGP on 2008-11-11
You didn't wait long enough! It never actually freezes. 

But people think that it freezed on them, because the progress bar sits there.

Looks like you're gonna end up reformatting and reinstalling. Sorry. :(

---

### Post by sharkster2007 on 2008-11-11
I can't speak about the internet update feature as I can't use it as stated before. 

It did freeze on me (due to lack of internet connection), I installed the three (Nvidia 177 Driver) .deb files (required) manually (by just double clicking on them) and activated via Hardware drivers and is now A ok on mine.

I am a noob user, just trying to help out, I couldn't follow the command line ways of doing it so i went my own way :-)

---

### Post by Marcel Beaudoin on 2008-11-11
So I managed to download and install the 173 drivers (I changed the DL location to main server from Canada server). When I restarted, the resolutions available went in the wrong direction. I was at 800x640, now I am at 640x480.

---

### Post by Marcel Beaudoin on 2008-11-11
> **RJARRRPCGP said:**
> You didn't wait long enough! It never actually freezes. 

But people think that it freezed on them, because the progress bar sits there.

Looks like you're gonna end up reformatting and reinstalling. Sorry. :(

It didn't freeze. The downloading screen actually disappeared.

My system just did a bunch of updates, so hopefully that will fix this problem.

---

### Post by sirgogo on 2008-11-11
Hey man,

I have the same two options. I have an on-board NVidia 6100, and a PCI-E NVidia 8600 GT.

While this works for me now, before I've had lots of trouble with video drivers. You may want to try Envy. Its basically a software that identifies possible drivers, installs them, and configures your xorg.conf file well (and tidily). The link is: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) .

I opened it up in terminal, installed it there, then restarted and it works great. Give it a shot and let us know.

---

### Post by Marcel Beaudoin on 2008-11-11
> **Marcel Beaudoin said:**
> It didn't freeze. The downloading screen actually disappeared.

My system just did a bunch of updates, so hopefully that will fix this problem.

Well, the updates partially worked. I am now up to 1024x768. Closer, but not at the 1280x1-24 that I want.

> **sirgogo said:**
> Hey man,

I have the same two options. I have an on-board NVidia 6100, and a PCI-E NVidia 8600 GT.

While this works for me now, before I've had lots of trouble with video drivers. You may want to try Envy. Its basically a software that identifies possible drivers, installs them, and configures your xorg.conf file well (and tidily). The link is: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) .

I opened it up in terminal, installed it there, then restarted and it works great. Give it a shot and let us know.

Thanks!! I am trying to DL it, but the DL link brings me to the FAQ, not an actual place to download anything.

Never mind. Reading helps all the good little boys and girls in the world.

---

### Post by Marcel Beaudoin on 2008-11-11
So I installed EnvyNG, but it doesn't actually show up in Applications -> System Tools.

---

### Post by Marcel Beaudoin on 2008-11-11
Could it have someting to do with the fact that it still lists my monitor as Unknown??

---

### Post by Marcel Beaudoin on 2008-11-11
OK, I figured it out.

I also play my XBox 360 on my monitor, so I have a Belkin Flip ([http://www.belkin.com/flip/support/](http://www.belkin.com/flip/support/)) KVM switch located inline. This prevents Ubuntu from actually seeing my monitor and giving me the proper resolution.

When I unplug my monitor from the KVM switch and plug it directly into the computer, I can get to my desired resolution.

So now, how do I, knowing this, force Ubuntu to allow me to keep this resolution?

---

### Post by Technoviking on 2008-11-11
I have had some issues with 177 text corruption issues in gnome-terminal and Firefox with my 8400m GS card.

---

