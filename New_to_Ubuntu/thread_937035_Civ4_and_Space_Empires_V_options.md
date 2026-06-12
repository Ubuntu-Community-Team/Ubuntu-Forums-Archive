---
title: "Civ4 and Space Empires V options"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by Eltern on 2008-10-03
I've been using Ubuntu for years now, but gaming has always been a difficulty. There are two games I want to be able to play: Civilization 4 and Space Empires V. The latter doesn't work in Wine at all, and the former theoretically works, but on my computer cries about below-recommended hardware (which is incorrect). I tried to use VirtualBox to play on Windows directly, but evidently VirtualBox doesn't support 3D graphics, which both games use.

The question is: What are my options? I've been hacking away with both games over the past few days, and my ideas have run dry. Are there other virtualization programs that do support 3D graphics? Is some other avenue more likely to succeed? 

Thanks!

---

### Post by Paqman on 2008-10-03
> **Eltern said:**
> Are there other virtualization programs that do support 3D graphics?

Unfortunately no. By far the best option for Windows games that don't run well through Wine is to dual-boot.

---

### Post by Eltern on 2008-10-03
I actually just figured out what the problem is with Civ 4 on my computer: I can't do fancy video effects at all. Compiz and the standard bells and whistles one can activate in System->Preferences->Appearance->Visual Effects do not work! I have the Intel 915 graphics controller, which I gather does not play too well with Linux. 

Installed packages:
915resolution
xserver-xorg-video-i810
xserver-xorg-video-intel

I have no options in System->Administration->Hardware Drivers, but I sure would love a 915 driver to activate to get 3D effects. I tried using the last released version I could find (found here: [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/) ), but no luck. Installation screwed up at the end, with the following message:

The script will now compile the DRM kernel modules for your machine.

Press ENTER to continue or CTRL-C to exit.

Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

So, any suggestions on what else I could do would be great. I'm not the first person to have this problem in the past few years, and I'm sure there's a solution somewhere.

---

### Post by Eltern on 2008-10-03
I removed xserver-xorg-video-i810, leaving X to only use the newer (I think) xserver-xorg-video-intel. Now Civ4 will at least run without crashing or even crying, but there are glitches all over the screen.

---

### Post by Eltern on 2008-10-03
More news on Civ4:

The first two opening videos run perfectly, then the Firaxis logo and intro sequence are choppy. In starting a game with "Play Now!" the rotating globe is a little jittery, but then at leader selection the game finally crashes. If the Random leader is selected, it takes until the game starts to crash, but if an individual leader is selected, the portrait window that would contain the animation instead contains junk. The program then freezes for a second and crashes.

This installation is a copy/pasted folder from a Windows VirtualBox install, with No-CD patches. I have native overrides for msxml3 and d3dx9_26, 31, 32, 33, and 36. I also used winetricks to get corefonts, vcrun2003, and dotnet11. 

Given that the folks on WineHQ are running the game fine, I fear that the crashing has to do with my graphics drivers. Again, I'm using xserver-xorg-video-intel. Any suggestions would be appreciated.

---

### Post by Eltern on 2008-10-05
::bump::

I know the nature of the request changed dramatically :-) Maybe I should make a different post.

---

