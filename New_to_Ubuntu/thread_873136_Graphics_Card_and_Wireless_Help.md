---
title: "Graphics Card and Wireless Help"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by ergonomicdesign on 2008-07-28
So, I'm not sure exactly how to begin. I stopped using Ubuntu (Hardy Heron, 8.04) for about 3 months because I just couldn't get the graphics card or the wireless card to work on my laptop but wanted to give it a second go before school began. 

Right now, I'm on a Toshiba Satellite (A205-S5803) with the following features: 
Intel Pentium dual-core processor T2330 operating at 1.6GHz
Operating System – Windows Vista Home Basic
1 MB L2 cache
Up to 533 MHz Frontside bus
1GB of PC2-5300 DDR2 SDRAM memory (2 x 512MB); maximum memory capacity: 2GB
Realtek® 802.11b/g wireless LAN
ExpressCard/54 slot: also compatible with ExpressCard/34
Intel Graphics Media Accelerator X3100 with from 128MB to 251MB shared memory

Out of box, Ubuntu does work for the most part. I can surf the internet (I'm using it right now after all) but only through a hard-wired ethernet cord. The wireless doesn't work. I remember I tried to find the windows version of the driver for the Realtek Wireless card, but couldn't (it came as an .exe file) and when I tried extracting it, and using "Windows Wireless Drivers," it detected that the right driver was present, but I couldn't connect to any networks because none would be detect. (There are 5 networks around my house, and the router for my personal one is 3 feet from my computer). That's my first problem. 

But the more challenging one for me is that there's something wrong with my graphics card. If I play a video, only half the video would be displayed (if the player is in windowed mode) or (if the player is in maximized mode) the entire system would crash. I just don't know where to start with this problem. Flash based videos (i.e. youtube) would play fine more or less, but .avi or dvd's would cause a crash. 

What to do? Where to begin? Any help would be greatly appreciated!

Thank you.

---

### Post by anewguy on 2008-07-28
Let's start with a few questions:

(1) Can you "lspci" in a terminal window and paste the output back here?

(2) Have you ever installed any drivers for your video?

(3) If the screen is fine except when playing videos, have you installed VLC, gstreamer and ALL of it's associated codec packages (I think they are named something like "bad" and "ugly", but it's been a while since I installed those)?

(4) If you were able to extract the Windows XP (Vista's are a no-go) drivers for your wireless, did you try using ndiswrapper?

(5) Do you have wireless as an entry under System/Administration/Network?

(6) If the answer to (5) is yes, do you have it set to roaming mode?

(7) Try a search in this forum for your model - I seem to remember seeing at least 1 how-to for it.

(8) Try a Yahoo! or Google search of:
ubuntu Toshiba Satellite A205-S5803 wireless

and

ubuntu Toshiba Satellite A205-S5803 video


You will probably be able to find your answers just following (8).

Post back and we'll go from there.  :)

---

### Post by bobnutfield on 2008-07-28
I believe you will find that your wireless chipset is probably the Realtek 8187B, which is common in many newer Toshiba Laptops.  There is extensive coverage in getting it to work on this forum.  Just search "Realtek 8187B.

Bob

---

### Post by ergonomicdesign on 2008-07-28
(1)

lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)


(2) I don't think I have installed anything, but I just tried what was stated in some other guide concerning this same graphics card (the X3100), and it came up with the driver was aleady installed. Intel i810? I can't remember what I read ><

(3) I have VLC Installed, and I just ran this command: "
sudo apt-get remove gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar" that I found in a stickie somewhere else. (It'll take a little bit to download/install, so I'll update about that a little later). 



(4) I didn't try ndiswrapper...wasn't aware of its existence. =( I'll do that next. (I found this guide, [http://en.opensuse.org/Wireless_Network_Card_Installation](http://en.opensuse.org/Wireless_Network_Card_Installation), which I will follow). 



(5) I just have wired connection and point to point connection, not wireless. 

(6) N/A

(7) I'll try that!

Thanks again, anewguy!

---

### Post by ergonomicdesign on 2008-07-28
Thanks bobnutfield, I like that you were the one who wrote the guide =)

So, now all that is left is getting my Graphics card thingy to work. But, I'll have an update about that shortly!

---

### Post by ergonomicdesign on 2008-07-28
bob, you said to use the Win98 drivers from the Realtek site. After searching their site, I found the download ([http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false](http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false)) where it had "Window Driver (support Win98/WinME/Win2K/WinXP/Vista),vista driver ver.6.1135,xp/2000 driver 5.1135" for download for 8187B. I got it, but only found 5 folders, VistaX64, Vistax86, Win2000, WinXP, and X64. None sound right. What do I do now =( 

I tried googling to download the windows 98 realtek driver, but all I found were some rather shady sites. Did you find the driver you used off their site? or somewhere else?

---

### Post by papsynot on 2008-07-28
Note - my Ubuntu and Gnu/Linux's know-how rank: amateur

I got mad after a month of on and off testing with Linux distros.
However I found how to make my Intel video card ( GMA 950 ) working great!

First, disable Compiz-Fusion then update Intel drivers with this package (I still don't realize I was able to make one - lol)
[http://spazioinwind.libero.it/densou/xf86-video-intel_2.3.2-1_i386.deb](http://spazioinwind.libero.it/densou/xf86-video-intel_2.3.2-1_i386.deb)
(please download with Right Click + Save As... or it won't start) and replace your xorg.conf with [mine](http://spazioinwind.libero.it/densou/xorg.conf) (before doing it check that your /etc/modules contains "agpgart", "intel-agp", "drm" and "i915" they should be all built inside the kernel but I also add them in that modules list)

well, maybe skip to paste my monitor section because I customized it for an old CRT and I'm not sure how to set up for a laptop screen :(


Plus, this afternoon I tried to compile and to create a .deb for the new Intel 2.4.0 release but I had no luck. Checkinstall gave me an error output similar to "Error on Debian compiling policy, package creation failed". I heard that this version needs Xorg 1.4.x only but why worrying, my desktop pc works fine now ;) :p

---

### Post by bobnutfield on 2008-07-28
Very sorry, I have had to leave for a while.  I will pick this up when I get back and follow through with you.

Bob

---

### Post by bobnutfield on 2008-07-29
Sorry that I could not get back to you quicker.  It appears as though they have the Win98 Driver in the Win2000 folder.  I believe it will be fine if you use the .inf file from that folder.  Also you may have found that there are other means by which others have set this chipset up, namely with a modified driver.  You can find that driver here:

[http://www.datanorth.net/~cuervo/rtl8187b/]("http://www.datanorth.net/~cuervo/rtl8187b/")

I got better results from using ndiswrapper, but others have claimed that this driver is the best solution.  Post back if you need any further help.

Bob

---

### Post by ergonomicdesign on 2008-08-04
Thanks Bob, I got the wireless driver working using the win2000 driver, adding your line the inf, and then using windows driver thingy (instead of ndiswrapper). ndiswrapper, for some reason, wouldn't display wlan0, and I gave up...worked with the other program. Anyway, turns out my router doesn't suppert linux connecting....which is weird. 

I'm assuming the password for the router (2wire) is 10 digit hexadec. and...I can't connect, it'd work for about 5-10 minutes, then say it's failed. So, I guess it's not meant to be. =(

Oh well, all that is left is the graphics problem. 

It's definitly not related to having things installed (i.e. totem, vlc, etc.) since I have everything installed and up-to-date. I still crash if I play a video in maximized form.

---

