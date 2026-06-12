---
title: "Ccsm"
date: 2013-02-02
forum: New to Ubuntu
---

### Post by johnnyflips on 2013-02-02
Hi everyone,
     I need help....lol  I am trying to setup compiz settings manager to enable the cube on my desktop and getting nowhere. I have followed several sets of instructions and the problem I'm having is that the options they are telling me to choose simply aren't there. I'm not exactly sure what version of Ubuntu I was using before but 12.10 is very different. That shouldn't mean that the programs should work any differently though, correct? I can get as far as choosing the number of desktops, etc but then it says to check enable cube but it's just not there. In one post there was a screenshot and there are several of the options that are available like desktop wall but nothing about a cube. .It's almost like I installed a "stripped down" version of ccsm or something. I know it has to be something simple that I'm missing but not mentioned in the other threads. I would appreciate any thoughts anyone may have on the subject. I look forward to hearing from you.

---

### Post by howefield on 2013-02-02
> **johnnyflips said:**
> It's almost like I installed a "stripped down" version of ccsm or something.

That is what you have. The other ccsm options are unsupported but I believe available if you install the package compiz-plugins.

However as unsupported plugins, you are on your own :-)

---

### Post by coldcritter64 on 2013-02-02
Another guide link in case you only got older release details, this is for 12.10 specifically,
[http://ubuntuguide.net/enable-desktop-cube-in-ubuntu-12-10](http://ubuntuguide.net/enable-desktop-cube-in-ubuntu-12-10)

If some plugins are missing ensure you have them all installed, the link also has you install the compiz-plugins-extra package. It is possible if it is not installed, that could possibly account for some of the differences you note between your install and any previous instructions used.

---

### Post by deadflowr on 2013-02-02
The cube effects are part of the compiz-plugins extras.
It is not part of the base install of the ccsm.
For me, the easiest way to install is to first install synaptic, then locate the plugins there.( I do this because I tend to forget the full name)

When setting up:
1)open general option>desktop size horizontal 4 vertical 1.

2)disable unity plugin.

3)enable desktop cube.(disable wall)

4)enable rotate cube.(I like to set the zoom to 50 or 60)

5)enable 3d windows. Here is the part which from 12.10 onward has been problematic. When this has been set the cube gets distorted. My workaround has been to click on the plus sign next to window match and add window type = desktop.(Just switch the setting from window class to window type, use the grab and grab the desktop).

6) re-enable unity plugin.

7)tweak to your own liking.

---

### Post by monkeybrain2012 on 2013-02-02
> **deadflowr said:**
> The cube effects are part of the compiz-plugins extras.
It is not part of the base install of the ccsm.
For me, the easiest way to install is to first install synaptic, then locate the plugins there.( I do this because I tend to forget the full name)

When setting up:
1)open general option>desktop size horizontal 4 vertical 1.

2)disable unity plugin.

3)enable desktop cube.(disable wall)

4)enable rotate cube.(I like to set the zoom to 50 or 60)

5)enable 3d windows. Here is the part which from 12.10 onward has been problematic. When this has been set the cube gets distorted. My workaround has been to click on the plus sign next to window match and add window type = desktop.(Just switch the setting from window class to window type, use the grab and grab the desktop).

6) re-enable unity plugin.

7)tweak to your own liking.

3d windows does not work properly.
[https://bugs.launchpad.net/compiz/+bug/1024208](https://bugs.launchpad.net/compiz/+bug/1024208)

---

