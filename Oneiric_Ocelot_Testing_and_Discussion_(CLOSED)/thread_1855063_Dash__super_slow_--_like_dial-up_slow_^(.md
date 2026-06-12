---
title: "Dash  super slow -- like dial-up slow :^("
date: 2011-10-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2011-10-05
I actually set my clock to measure seconds and it's taking over a full minute (62 to 65 seconds) for dash to find an installed app :(

That can't be intentional. Does anyone else see this behavior?

Or are Ubuntu's system requirements just increasing?

I've tested with both my Intel box which runs unity-3D and my old VIA box that runs unity-2D, and they're both equally slow.

I don't think it's GPU related since the two use vastly different graphics chips, but both indicate an absurd amount of CPU usage when clicking on the dashboard.

Does anyone else see this?

PS: I've been out of the testing loop due to other issues so don't bash me too hard for not knowing what's going on ;)

---

### Post by MG&amp;TL on 2011-10-05
The Dash does take up quite a lot of CPU and RAM, but not that much. What are the specs of the machines?

If you have the compiz-config settings manager ("sudo apt-get install compizconfig-settings-manager"), go to the Unity plugin, and click on it. Go to "experimental", and see what sort of blur has been set. I find that adding no blur speeds it up dramatically.

---

### Post by MG&amp;TL on 2011-10-05
Hardware requirements:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by philinux on 2011-10-05
It's almost instant here. 3 yr old machine 2 gig RAM.

Maybe a fresh install is needed to clear the cobwebs of testing.

If these are fresh installs is there anything in the xorg I'd other logs.

---

### Post by kansasnoob on 2011-10-05
> **MG&TL said:**
> Hardware requirements:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Should be OK then:

> Box #1:
JetWay JATOM-GM1-230-LF Motherboard
Intel Atom 230 CPU @ 1.60GHz
System Memory 2GB DIMM
Intel 82945G/GZ Integrated Graphics
Intel N10/ICH 7 Family High Def Audio Controller

Box #2:
VIA PC2500 Mainboard
VIA Esther C7 CPU 1500MHz
System Memory 2GB DIMM
VT8233/A/8235/8237 AC97 Audio Controller
CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] Graphics

I just tried a fresh install on my Intel hardware to check changes in ubiquity and the dash is still super slooooooow, I mean slow as mud!

It really is a bit like using dial-up. Click on dash, then go the bathroom, and maybe it'll be done when you get back ;)

I'm used to things moving so fast with either set of hardware that blinking will cause you to miss something.

---

### Post by rburkartjo on 2011-10-05
mg your suggestion did speed it up a lot but still way to slow. sticking with xfce for now that is working like the cat's meow

---

### Post by kansasnoob on 2011-10-05
> **MG&TL said:**
> The Dash does take up quite a lot of CPU and RAM, but not that much. What are the specs of the machines?

If you have the compiz-config settings manager ("sudo apt-get install compizconfig-settings-manager"), go to the Unity plugin, and click on it. Go to "experimental", and see what sort of blur has been set. I find that adding no blur speeds it up dramatically.

Tried that on the Intel machine (the other doesn't use compiz) and it's a tiny bit faster ........... like it only takes 45 seconds for dash to open and search.

But, really, 45 seconds to find and open an app???????????

[COLOR="Red"]**45 seconds!**[/COLOR]

---

### Post by madjr on 2011-10-05
looks similar to this bug:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/824890](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/824890)

---

### Post by kansasnoob on 2011-10-05
> **madjr said:**
> looks similar to this bug:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/824890](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/824890)

I'm really not sure, but I do a lot of iso-testing, and upon noticing a great deal of changes to ubiquity (the live installer) I decided to give things a whirl since we have only a few days until Oneiric final iso-testing begins.

While zsyncing the new image on one box I decided to boot into Ubuntu on the other and update. ATM both updated and fresh installs have this super slow dash thing going on.

Sadly I'm real busy, and I'm going into the hospital tomorrow (hopefully for hours rather than days) but I was totally freaked out over how slow the dash seems now :(

OTOH Lubuntu looks pretty good other than a still borked power management icon in the panel :D

---

### Post by alphacrucis2 on 2011-10-05
Dash is going like a scalded ocelot for me.

---

