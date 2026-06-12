---
title: "Major issues getting ati drivers to work and launch steam linux client"
date: 2013-01-09
forum: New to Ubuntu
---

### Post by Sehnder on 2013-01-09
First time user for all of 24 hours. Definitely had some issues I wasn't expecting!

The goal: Get the steam linux client running so I can try out a few of my games on linux there.

The result: Had to reinstall linux three times, still no luck getting there.

I have tried four different version of the ATI drivers for my radeon 7970, none of which have worked. All don't let steam launch, but they are different flavors of not working:
1. Default- system works normally except steam won't launch (nor any games from humble bundle it seems.)There is a little blip of... something (a very tiny blank box) when I try to launch the steam client but it immediatly goes away. Does not show up in the system monitor aftewards.
2 and 3. Alternate installs from the "system applications" remove the sidebars and other items from the desktop when I restart. That means I can't recall explore things (not knowing the shortcuts yet). Steam won't launch.
4. Direct install from the AMD website. Stuck the monitor in 800 x 600 mode. Unable to uninstall the drivers. Steam won't launch.

I had to reinstall the first time to fix the 800 x 600 issue (since I couldn't revert it and the sidebars were all hidden), and the second time because after doing a hard reset (couldn't see the button to restart normally) I got some rather unpleasant Kernel panic errors and ramdisc 0 something something which put a bit of damper on my day.

So, for try #3, fresh install of Ubuntu 12.10, what exactly should I do? Any advice would be appreciated. If I have this much fun getting the video drivers to work, I can only imagine the joy I'll have in getting my titanium HD sound card functional!

---

### Post by QIII on 2013-01-09
Please have a look at the ATI link in my signature.  I will confess that there is some stuff there I probably need to update.  But read through it.  You will probably have the best luck installing from the repo using the terminal.

Here's the short version.

```
sudo apt-get install fglrx fglrx-amdcccle
``````
sudo amdconfig --initial
```Reboot.

Sometimes the driver does not install properly using the graphical tools.  Also, the "Updates" version usually does not work, so I usually recommend against even bothering to try.  Installing via the terminal seems to work more often.

Supposedly the amdconfig step is no longer needed, but with the number of people who end up having problems, I still recommend doing it.  That is what sets up your initial "instructions" for the driver.

After you reboot, you need to open the Catalyst Control Center in administrative mode and make your fine adjustments.  If it doesn't open from the menu, go back to the terminal

```
gksudo amdcccle
```If all goes south, get to a terminal and do

```
sudo apt-get purge fglrx fglrx-amdcccle
```then reboot to get back to the default Radeon driver (the one Ubuntu uses when you first install).  If need be, we'll try to figure it out again from there.

Driver support for Linux has come a long way from the 90's.  But it's still not always the easiest thing.  Look at it from the OEM's point of view:  You have one OS that 95% of your customers use.  Are you going to spend your time addressing them, or the 2% of the market that uses Linux?

After all that, there's no guarantee that Steam, or your particular game, will work.  Remember that Steam for Linux is still in its infancy.

---

### Post by Sehnder on 2013-01-09
I was able to fix the problem by installing the 12.04 release. It fixed virtually every issue that I had so I am a happy camper. Thank you very much for your help! The lesson I learned is to stick with the stable release.

---

