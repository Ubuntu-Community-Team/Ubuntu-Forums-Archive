---
title: "Installing Nvidia drivers"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by sisyphus10 on 2008-06-28
I am uncertain as to netiquette here and whether it is acceptable to add another post to this thread. But I am a total Ubuntu novice having trouble installing the latest NVidia driver to a new first time install of Ubuntu 8.04. I installed it nearly 24 hours ago on a P4 3.0 GHz with HT, 2 GB RAM, NVidia 7600 with 512 MB RAM, and apart from a restless sleep, have spent the intervening hours trying to sort this out!

My first intention was to use Envy and I printed out the instructions from the Envy website (even though they don't appear to relate directly to 8.04 but to an earlier version with different screens). But I got to the point where I had envyng 1.1.1 showing as an option for installation. I hit the reload button and my wireless connection started downloading files. But then stopped. Anyway, that is a separate problem which I will probably need to start a separate thread on since the wireless/ network connection works, and I can open a web page in Firefox. But as soon as I try to change the page, the internet connection drops out there as well. I have stopped Firestarter to no effect.

But getting back to NVidia, I then logged on to this Forum and found this thread. I printed out your instructions for manual install though I noted it was for NVidia GEForce 6200. My own version is 7600 GT. But this was all I had to go on...

I might also note that in that separate thread, you recommend first going to 'System->Administration->Restricted Drivers Manager'. However, in the 8.04 I installed, there is no 'Restricted Drivers Manager' under System > Administration.

I typed in your first line with no trouble. But when I typed in the second line exactly as is, I got the reply that the 'build-essential file or foldr does not exist'. End of yet another attempt to load this new driver...

So I am wondering whether there is a separate method of installation for Ubuntu 8.04 or for later NVidia drivers?

Can you also please confirm that in that second line '(uname -r)' should be typed exactly as is, or whether I should type my own username in place of 'uname'...?

I might also note that in that other thread, you first recommend going to 'System->Administration->Restricted Drivers Manager'. However, in the 8.04 I installed, there is not Restricted Drivers Manager under System > Administration.

---

### Post by drs305 on 2008-06-28
sisyphus10,

I have the nvidia 7600 GT. I am running a 64 bit system. I installed envyng-gtk and it installed the nvidia drivers without any problems. It works great and was painless. Install it with "sudo aptitude install envyng-gtk" and then run it with the "envyng-gtk" or via the System Tools menu.

In fact I just ran the program again to make sure it hadn't changed. No problems for me.

---

### Post by sisyphus10 on 2008-06-28
Thanks. As I said, though, my primary intent was to use envy, but the problem with that is that I cannot get a stable internet connection to install envy in the first place! That is why I was looking at a manual alternative...

---

### Post by PmDematagoda on 2008-06-28
About your post, you say that you didn't try using the Restricted Drivers Manager, well that has been renamed and is now Hardware Drivers which can be found in System>Administration.

---

### Post by sisyphus10 on 2008-06-29
Thank you. I had already found Hardware Drivers, but never having used any previous versions of Ubuntu, I had not idea is was the Restricted Drivers Manager, renamed! 

Since I was last here, I totally removed Ubuntu and - despite severe temptation not to -- reinstalled it. To keep it brief, after a lot of mucking around I got the internet connection stable enough (though still not perfect) to get Envy )both envyng and envygtk) installed. And after 4 times trying to install the new NVidia driver with that, including 4 reboots, I finally got it to say the process of installation of the new driver was complete. As far as I am aware,though, it installed version 173.14.05 instead of the absolutely latest 173.14.09 (which I had downloaded separately and copied to the Ubuntu Home page). But at this stage, I was just happy to have anything...

However, I rebooted, and now seem to be in a worse situation than before. Hardware Drivers tells me the driver is there and enabled but 'Not In Use', whatever that means. And when I go to System > Specifications > Screen Resolution, the only choices I am presented with are 640 x 480 or (ha!) 320 x 240. I have a 19 inch widescreen LCD monitor attached to this particular computer whose native resolution is 1440 x 900. But now I have Ubuntu looking about as bad as Windows in Safe Mode!!! Before installing the new driver, I at least had the choice between 800 x 600 and 640 x 480.

Is there anything obvious that I have overlooked or need to do?

---

### Post by sisyphus10 on 2008-06-29
For what it is worth, I changed the monitor on the computer from its existing 19 inch Chimei to a 19 inch LG with the same resolution (1440 x 900). On rebooting, the correct display settings were found and Ubuntu now appears in the monitor at 1440 x 900. 

Can I deduce from that that Ubuntu has a databased hidden somewhere of what monitors it will or won't accept? Is a special driver required for monitors that Ubuntu cannot "see"? (It is strange that Vista on the same computer had no difficulty at all seeing the Chimei monitor at its proper resolution.) I ask these questions since I don't really want to use the LG with this particular computer as it has a much more flexible stand which I can place in a difficult position for another computer...

Now if I can only find out why my wireless internet works intermittently under Ubuntu but perfectly well and continuously under Vista on the same computer...!

---

### Post by hopelessone on 2008-06-29
> I hit the reload button and my wireless connection started downloading files. But then stopped. Anyway, that is a separate problem which I will probably need to start a separate thread on since the wireless/ network connection works, and I can open a web page in Firefox. But as soon as I try to change the page, the internet connection drops out there as well. I have stopped Firestarter to no effect.

Hi try System >> Admin >> Network then "Unlock" click Your connection type and hit "Properties" Unclick "Roaming Mode" and set it to "DCHP" like shown in picture...

It's reversible to change it back if it don't work, but this should stop your dropout internet connections...

Hope this might help...

---

### Post by hopelessone on 2008-06-29
I got my envy from :

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

```
sudo apt-get install envyng-gtk
```

for your new monitors resolution try to:

```
sudo dpkg-reconfigure xserver-xorg
```

as this will detect your new monitors settings...

reboot..

---

### Post by sisyphus10 on 2008-06-29
Thanks for both those responses. I too had gone to the albertomilone website, but in that it said that envyng was embedded in the restricted updates, which is where I found it and (eventually) downloaded and installed it it.

Re DCHP, I did that, and it seemed promising. It allowed me to open Firefox, and open a couple of tabs in that on different sites, and do things with those pages e.g. initiate a Google search. But when I went to the Update Manager and started a download of selected updates, a box would appear showing a download speed. After no more than 5 seconds, the speed would drop significantly, and two seconds later, no more, the download would stop completely, and I can no longer operate Firefox either. The only way of getting the internet connection back is by rebooting and going through it all again.

Using Roaming, if could at least get several minutes of downloads. But now I find I cannot change it back to Roaming. When I tick the Roaming box, the main wireless settings box shows a '-' sign, and will not allow me to tick it.

---

### Post by Miljet on 2008-06-29
Take a look at this old thread.
[http://ubuntuforums.org/showthread.php?t=603154&highlight=gilf](http://ubuntuforums.org/showthread.php?t=603154&highlight=gilf)

---

### Post by neurostu on 2008-06-29
You could always just go to the nvidia website and install the driver by hand. That is what envy does...

---

### Post by sisyphus10 on 2008-06-29
Thanks. But that thread covers actually getting connected via wireless. I have no trouble with that. From the first installation, Ubuntu connected to the internet via my wireless card. The trouble is that the connection drops out unexpectedly, particularly when trying to download Ubuntu updates. With the network set to Roaming, it will usually maintain downloads for around 3 minutes, sometimes a little more, sometimes less. The signal strength is good (minimum 65%, max 92%, usually 85%)and continues to show this. But the download speed from the Ubuntu archive site varies widely. It will start off relatively fast, then drop down to a few hundred bits per second, then jump to a high speed, and fall again. Sometimes the Download Speed drops to Unknown. If it does so soon after a download starts, it will usually restart after a second or two. But if it happens after two minutes, it never restarts...

If I change to DCHP, as noted above, the download will only last a few seconds and the connection to the internet is lost.

In Vista on the same computer, the same wireless card operates without problem and continuously.

---

### Post by jerome1232 on 2008-06-29
I've never messed with envy but the easiest (for me) way to install the latest nvidia drivers is:

goto Nvidia's website and download their drivers (32bit or 64bit)
if your not sure whether you are running 32 or 64 bit, type this in a terminal
```
uname -m
```
x86_64 is 64 bit
anything else will be 32 bit

I'm writing this assuming you downloaded the driver to firefox's default of your desktop
press crtl+alt+F1
for 64 bit
```
sudo /etc/init.d/gdm stop
sudo apt-get install build-essential
cd Desktop
sudo ./NVIDIA-Linux-x86_64-173.14.09-pkg2.run -a
sudo /etc/init.d/gdm start

```

for 32 bit
```
sudo /etc/init.d/gdm stop
sudo apt-get install build-essential
cd Desktop
sudo ./NVIDIA-Linux-x86-173.14.09-pkg2.run -a
sudo /etc/init.d/gdm start

```

now to keep from doing this every bloody reboot:
```

gksudo gedit /etc/default/linux-restricted-modules-common

```
mine looks like this, make your's the same

# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables the three nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES="nv nvidia"

now any time there's a kernel update and xorg updates, you'll have to redo a few steps:
```
sudo /etc/init.d/gdm stop
cd /directory/where/nvidia-driver/is-at
sudo ./NVIDIA-Linux-x86_64-173.14.09-pkg2.run -a
sudo /etc/init.d/gdm start

```

now there's some text file you have to edit to avoid doing this EVERY reboot, it basically blacklists the nvidia restricted drivers so they won't take over, having trouble remembering/googleing that config file, will update when I do find it.

---

### Post by sisyphus10 on 2008-06-30
Thanks. But the NVidia issue was resolved yesterday. My more recent posts relate to a cyclic drop-out in my wireless internet connection every 3 minutes or so.

---

### Post by jerome1232 on 2008-06-30
hmmm.. glad to hear you've got the video drivers sorted out. Have you checked out [http://ubuntuforums.org/showthread.php?t=370108]("http://ubuntuforums.org/showthread.php?t=370108") and other such posts? I'm still learning myself and I was lucky in that my wifi card works better in Linux than it does in Windows (Belkin only has a beta driver on website... (insert profanity)) So I don't have anything to offer with your wifi problem. Usually the forums have hidden gems of knowledge if you search hard enough.

---

### Post by sisyphus10 on 2008-06-30
Yes. The NVidia issue was resolved by sheer patience as I could only install the new drive on Ubuntu by installing Envy. And for that I needed a functioning internet connection. It took 4 goes before I finally got the Envy package downloaded and installed. Then it still didn't work after several reboots. By trial and error, I swapped the monitors, replacing the existing Chimei 19" widescreen LCD with an LG 19" widescreen LCD. And for some inexplicable reason, that worked right off. So that was major problem number one solved.

After quite literally 50 hours working on both that and the wireless problem, I finally resorted just now to going out and buying a long LAN cable. It was the last thing in the world I wanted -- a long ugly cable snaking down the corridor! But I just couldn't take it anymore!! And of course now it is working quite fine, downloading the remaining larger Ubuntu updates quite happily!! Now at least I will be able to look at what Ubuntu can do, instead of literally wasting even more time just trying to get the basics even working! And of course, get on with life... !!

---

