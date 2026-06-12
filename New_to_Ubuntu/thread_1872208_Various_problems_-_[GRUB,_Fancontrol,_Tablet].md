---
title: "Various problems - [GRUB, Fancontrol, Tablet]"
date: 2011-10-30
forum: New to Ubuntu
---

### Post by rawrmarkie on 2011-10-30
Hi, I've got a few random problems which I would like to seek help for :) I have tried to upgrade to 11.10 a couple of weeks ago and it kind of mucked up my whole system so I formatted everything and have re-installed 11.04 since. Curiously, a few things that used to work just fine stopped working.

First of all, my grub bootloader thingy does not show up anymore. It goes purple, then black, and then the system starts. I have installed startup-Manager, and have also tried changing the resolution but nothing seems to work. Does anyone know why? I've checked the log files and I think it may relate to my graphics driver. I've got an old NVIDIA card (128mb GeForce FX5200, I think), and the computer sometimes freezes anyway. So I suppose it may be a graphics thing. (*It does not crash too often, but it does happen. But that has always been the case. It was worse in Windows, which is why I switched to Ubuntu which seems more stable.*) Does anyone know what I could do to get GRUB back? I suppose it's not the most important thing but it does strike me as odd as it has always worked just fine!

Secondly, I configured fancontrol using [this guide]("http://ubuntuforums.org/showthread.php?t=42737"). It used to work fine, including on startup. But now, I must have gone wrong somewhere, because it does not start anymore. I always have to remove /var/run/fancontrol.pid and then have to manually start fancontrol. Does anyone know why this could be? Any ideas would be greatly appreciated.

Lastly, I own an Aiptek 6000U tablet. The computer does recognise it **but** without pressure settings and that is the most important thing for me. I have tried to configure it using [this guide]("https://help.ubuntu.com/community/AiptekTablet"). However, when I try 'xinput get-button-map Aiptek', no such device is found. I have read the whole guide and I am aware of the fact that the 6000U seems to use Wacom drivers, but I thought I'd try the alternative anyway since it just does not seem to register pressure sensitivity!

Any help would be greatly appreciated. Thank you. :)

---

### Post by rawrmarkie on 2011-10-31
Sorry about the bump but the thread went back to page 5ish, so yeah.

Anyone got any ideas? Any help/suggestions would be greatly appreciated. Thanks for reading this =)

---

### Post by Favux on 2011-10-31
Hi rawrmarkie,

Are you using the OSS Nouveau drivers or the proprietary Nvidia driver (Additional Drivers)?

So it is a Waltop?  What's the output of?
```
xinput list
```

---

### Post by rawrmarkie on 2011-11-01
Hi Favux,

Thank you for your reply.

Wow. Now this is interesting. I was not using any driver at all, so it seems. I have now activated the proprietary Nvidia driver (NVIDIA accellerated graphics driver (version 173)). There's no option for OSS Nouveau, and I have never heard of that before, sorry. Unless that is the 'experimental 3D support for NVIDIA cards' option?
*Anyway, after a restart I still did not see the boot loader. However, there was an improvement as I now got to see the splash screen thing (which, funnily enough says 'Stopping Fancontrol Daemon'; I wonder why!).*

Below is my xinput list. You were right; it is a WALTOP.
> &#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Comfort Optical Mouse 1000        id=10    [slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Slim Tablet      id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; CHESEN USB Keyboard                         id=8    [slave  keyboard (3)]
    &#8627; CHESEN USB Keyboard                         id=9    [slave  keyboard (3)]
I wonder why it doesn't register pressure sensitivity then even though it is recognised as a tablet. Perhaps I'm using the wrong program (SAI on WINE...I know it's not everyone's favourite but I'm a SAI addict).

---

### Post by Favux on 2011-11-01
Right, the Waltop tablet should work out of the box in Oneiric.  That's because it should be on the Wacom X driver xf86-input-wacom.  You can confirm that by running in a terminal:
```
xsetwacom list
```
You should see at least your stylus.  Other input tools like eraser and cursor are spurious and are there because of the specific logic (code) the Wacom driver is using to support your Waltop.

With Oneiric's default xf86-input-wacom-0.11.0 the Waltop's have been re-added to the 50-wacom.conf in xorg.conf.d (/usr/share/X11/xorg.conf.d/50-wacom.conf).  They were commented out in earlier versions because the kernel's Waltop USB driver didn't work with xf86-input-wacom but recent kernels have fixed that.

See the Waltop HOW TO:  [http://ubuntuforums.org/showthread.php?t=1595648](http://ubuntuforums.org/showthread.php?t=1595648)
Linux Wacom Project mediawiki HOWTO page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)
Mediawiki Waltop tablet setup page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Waltop_Tablet_Set_Up](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Waltop_Tablet_Set_Up)

With Wine, pressure sensitivity is a perennial complaint/request.  Some versions support it with some versions of PhotoShop etc.  So you could look at some threads on the forum about Wine and pressure or checkout the Wine forums.  My impression is it is kind of hit or miss and you may have to change or set up some configurations.

I'm tempted to tell you to try:
```
sudo update-grub
```
but I'm concerned because I don't understand what's going on.  Grub is there somewhere it appears since you are booting into Linux.  Maybe that would fix a broken config but I'd hate to break things even worse.  You should probably post on one of the grub guru threads.

---

### Post by rawrmarkie on 2011-11-01
Hi Favux, thanks again for helping! I'm actually using Natty - the Oneiric update did not work for me (due to graphics/grub problems, too), unfortunately. Anyway, with the help of your howto I have now worked it all out. SAI doesn't work but MyPaint does so that'll do.

As for grub, I think I'll try posting in one of the guru threads then; thanks for helping. But yeah, it is indeed quite strange. Boot works fine, it just does not display. My screen goes from the motherboard (ASUS) bootscreen to black, purple, black, then splash+log-on screen, but it skips the Grub screen. 

Now all that's left is the weird fancontrol issue. :O

---

