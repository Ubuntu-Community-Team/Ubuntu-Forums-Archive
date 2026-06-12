---
title: "[SOLVED] GeForce 7900GT nvidia-glx-new error - defaults back to safe mode"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by fatality_uk on 2008-08-02
After install 3 I'm at a loss!! Fresh installs...

I have a Dell Inspiron 530 and I have inserted my old nvidia 7900GT in there. This card performed perfectly in the last machine but wont have any joy in the Dell box.

I have tried to enable the restricted drivers. It seems to install them ok but on restart, the screen default to safe mode and im left @ 800x600. I have tried Envy and exactly the same thing happens. It confirms a good install and then starts in safe mode.

On start up, it displays
```
Running local boot script /etc/rc.local
```
Hangs there for a second and then logs into safe mode.

**lspci** sees the card in the same way it did in the other machine.
> 01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GT/GTO] (rev a1)


Here's the output from xorg.conf

> Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"nVidia 7900GTX 512MB"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"RenderAccel"	"true"
	Option		"NoLogo"	"false"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb-uk"
	Option		"XkbVariant"	"Dell"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

All seems fine to me. Would anyone have an idea as to what on Earth is going on here? I know the card is functioning. I first setup a dual boot with Visa and the card worked there, after a driver download and install ;) Since then I have wiped Visa and done a complete install onto a clean disc.

Forgot to mention, i am running Hardy. Albeit @ 800x600 ;)

Any help appreciated.

---

### Post by fatality_uk on 2008-08-02
Could it be a conflict with the onvoard graphics?
If so, does anyone know how to diable the on gfx?

---

### Post by eightmillion on 2008-08-02
Could you post the output of **cat /var/log/Xorg.0.log** ?

---

### Post by fatality_uk on 2008-08-02
Sadly I had to stick Vista on so I could get on. So no Ubuntu install right now. Will do tomorrow.

---

### Post by fatality_uk on 2008-08-04
Can't access that!! Odd, odd, odd. Try and view that and it hangs. :(
I have seen a few posts regarding SATA drives and rc.local but I sure it's not that seeing as this only happens after I install the nVidia drivers, either from the repos, envy or the binary from the nVidia site.

Can anyone with a nVidia card please post their rc.local file? I might see something in there I can use.

---

### Post by AdamWood on 2008-08-04
I'm using a Nvidia GEForce 8600 without many problems. I only have problems when new kernel versions are released. So I always make sure I reboot with a new kernel before upgrading my nvidia drivers.

I don't think the problem is in your /etc/rc.local file but maybe you can post it anyway so we can take a look. There's usually very little in that file.

What would really help is a copy of your /var/log/Xorg.0.log file.

---

### Post by fatality_uk on 2008-08-06
I have output the content to a txt file and attached!!
Obviously too big to fit into the reply box.

Really hoping someone has a good idea here!!

---

### Post by fatality_uk on 2008-08-06
Just tried to install the *.run nvidia drivers
Stoped GDM.
Lauched the driver app
Got an odd message.
> [B]No precompiled kernel interface for...
Do you want to download it from the nvidiai ftp site[/B]
Then went dead :(

---

### Post by suprfish on 2008-08-06
Your xorg.conf looks funky, specifically the 'screen' and 'monitor' sections. Try

```

sudo dpkg-reconfigure xserver-xorg

```

Then repost your xorg.conf (cat /etc/X11/xorg.conf)

> **fatality_uk said:**
> I have output the content to a txt file and attached!!
Obviously too big to fit into the reply box.

Really hoping someone has a good idea here!!

I don't see any attachment, please post it and also the outputs of

```
lsmod | grep nvidia
```
```
glxinfo
```

---

### Post by fatality_uk on 2008-08-06
Here it is :|


> sudo dpkg-reconfigure xserver-xorg done that no joy doesnt get to video editing sectipn bombs out at keyboard section

> xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080806222412


grep result
> nvidia               7825536  0 
i2c_core               24832  1 nvidia
agpgart                34760  2 nvidia,intel_agp

lspci 
> 01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GT/GTO] (rev a1)


Its there!!!


glxinfo wont work as the drivers havent been installed have they!

> name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x3a 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None


I'll diggin jsut a shame I have to dig in FF under Vista :|

---

### Post by fatality_uk on 2008-08-06
More digging and it looks like this combination isnt going to work Dell Inspiron 530 & GF 7900gt :(

Oh well only 8 weeks till 8.10 comes out ;)

---

### Post by littlejborn on 2008-08-06
I'm also having problems getting the official nvidia drivers to work with my 7900GT. :confused:

I am able to use Ubuntu on a single monitor at 1600x1200 using the original (generic?) drivers that installed with Ubuntu (without 3D support), but when I try to install nvidia drivers using synaptic, apt-get, envyng, or the .run installer from nvidia's website none of them work.  For any of the installation attempts the same thing happens:  When I start up gdm it goes to a video configuration menu.  I can pick the resolution for both my monitors (I really want my dual monitor setup to work as well as Compiz Fusion and AWN) and change the graphics card from the generic VESA driver to the "nvidia" driver but then after closing that menu the screen goes black and eventually comes up to the GDM login screen running at 800x600.  I've also tried leaving it at the VESA driver and specifying "nvidia" as my driver in the xorg.conf file but after restarting X it did the same thing.  Also, if I go into the screen resolution app I am only given the options of 800x600 and 640x480, even when my xorg.conf file has the higher resolutions specified in it from the video configuration that I changed after starting up gdm.

Help?!

---

### Post by fatality_uk on 2008-08-06
littlejborn, post a new thread about your problem which is different to mine. Please leave this thread open to solutions to THIS problem!

---

### Post by suprfish on 2008-08-06
> **fatality_uk said:**
> 
glxinfo wont work as the drivers havent been installed have they!

Assumed that you still had a driver enabled. Your log file shows it loading... Enable the driver that is suggested (nvida-glx-new) instead of vesa, let it go into safe mode, then repost 

```
cat /var/log/Xorg.0.log
```
```
cat /etc/X11/xorg.conf
```

What I suspect is that it's not "safe mode", its just that the correct resolutions aren't being determined for your monitor fer some reason.

---

### Post by fatality_uk on 2008-08-09
Still no joy.

Here's the outputs for anyone to trawl over, but I am resigned to not getting this box working :(

After 7 days of searching, I am no closer to an answer :(

---

### Post by phidia on 2008-08-09
I've been seeing a lot of nvidia problems-it may not help but have you used the dpkg command with phigh: > sudo dpkg-reconfigure -phigh xserver-xorg

Also see this note from the [Ubuntu video wiki]("https://help.ubuntu.com/community/Video"): > Note: As of Ubuntu 8.04 and Xorg 7.3, the setup and configuration of /etc/X11/xorg.conf has changed. Please see the [Xorg in Ubuntu 8.04]("https://help.ubuntu.com/community/XORGHardy") for more information.

For additional troubleshooting resources, please also see the [Ubuntu X Team wiki]("https://wiki.ubuntu.com/X")

I'm also providing a link to [this thread]("http://ubuntuforums.org/showthread.php?t=881314") because it's possible the 7900 card is like the 8 series cards and 8 & 9 series have also had set up problems/symptoms similar to what's described here.

Hope something works-and btw intrepid does work with my 7600 card right now. Separate install though may not be worth the risk.

---

### Post by fatality_uk on 2008-08-09
Hmmm
Run it again!
> xserver-xorg postinst warning: overwriting possibly-customised configuration

---

### Post by fatality_uk on 2008-08-09
Just installed Suse11.0, LinuxMint & Fedora9 and nVidia drivers on each and no joy. So I sure now that it's a Linux hardware compatibility issue. Have to say Vista works like a charm :( *humph*

I have found an interesting link:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.04#Download_Dell_Ubuntu_Image](http://linux.dell.com/wiki/index.php/Ubuntu_7.04#Download_Dell_Ubuntu_Image)
This claims to be a specific Ubuntu image for Dell Inspiron 530. Might download it tomorrow and see if that can solve this issue.

I can't be the ONLY person in the World with this setup!!

---

### Post by phidia on 2008-08-09
Since you're trying all those distros what about [Sabayon]("http://distrowatch.com/table.php?distribution=sabayon")? If it recognizes your card Sabayon will auto configure it.

---

### Post by fatality_uk on 2008-08-09
Will do, but not holding my breath ;) It's a Linux/My PC thing :|
Thanks for the help by the way.

---

### Post by fatality_uk on 2008-08-14
Im back baby, yeah!!!

Well, kind of! :D Just borrowed an nVidia 8500gt card from a PC at work and booted up and the nvidia-glx-new appears to be working ;) Odd.

Im just installing envy and latest nvidia drivers and will reboot. I hope it's not as silly a card/motherboard incompatibility

Post back in a sec...

---

### Post by fatality_uk on 2008-08-14
Marked as solved, but solution was to change the gfx card ;) I created a bug report for this.
[SIZE="3"][B][COLOR="Red"]
WARNING: Dell Inspiron 530 = nvidia 7900gt == trouble :([/COLOR][/B][/SIZE]

Im off to buy a 8 or 9 series nvidia card so I can play ETQW in UBUNTU :)

---

