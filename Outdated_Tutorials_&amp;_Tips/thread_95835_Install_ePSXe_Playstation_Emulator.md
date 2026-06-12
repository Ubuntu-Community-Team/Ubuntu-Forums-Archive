---
title: "Install ePSXe Playstation Emulator"
date: 2005-11-27
forum: Outdated Tutorials &amp; Tips
---

### Post by johannes on 2005-11-27
[SIZE="4"]This guide is outdated and will not be updated anymore.[/SIZE]
Try using one of these instead:
[http://ubuntuforums.org/showthread.php?t=612021](http://ubuntuforums.org/showthread.php?t=612021)
[http://ubuntuforums.org/showthread.php?t=550304]](http://ubuntuforums.org/showthread.php?t=550304])

This is a guide to install the freeware Playstation 1 emulator [ePSXe]("http://www.epsxe.com/") in Ubuntu. It is based on [this guide]("http://terror.snm-hgkz.ch/gaming/linux/epsxe_howto/"), which I found a bit outdated.

ePSXe is made for x86 (common pc) only. If you use powerpc it probably won't work. You might want to try another emulator instead, for example [PCSX]("http://www.pcsx.net/"). An installation guide can be found in [this link]("http://ubuntuforums.org/showthread.php?t=159987"). Apparently it is possible to run it using an amd64 system, but to do that you need to install some 32 bit libraries, see [this]("http://ubuntuforums.org/showpost.php?p=1392699&postcount=84") post.

**Legal note:** The installation and use of this emulator requires a Sony Playstation BIOS file. You may not use such a file to play games in a PSX emulator if you do not own a Sony Playstation, Sony PSOne or Sony Playstation 2 console. Owning the BIOS image without owning the actual console is a violation of copyright law. You have been warned.

[SIZE="3"]Installation[/SIZE]

First, open a terminal and install the packages that you will need:
```
sudo apt-get install unzip libgtk1.2-common libgtk1.2
```

Get the ePSXe base package:
```
wget http://www.epsxe.com/files/epsxe160lin.zip
```

Make the installation folder by typing:
```
sudo mkdir /usr/local/games/epsxe
```

Since typing this whole path we just added is tedious and clutters up this text, we will store it in a shell variable using the export command. That way, we can call it up by typing $varname, which we'll have to do a few more times...
```
export EPSXE='/usr/local/games/epsxe'
```

Extract the ePSXe package and set up permissions:
```
sudo unzip -d $EPSXE ~/epsxe160lin.zip
cd $EPSXE
sudo chmod 777 cfg sstates snap memcards
sudo touch memcards/epsxe000.mcr memcards/epsxe001.mcr .epsxerc
sudo chmod 666 memcards/*
sudo chmod 666 .epsxerc
```

If you own a Playstation system, get the PSX Bios _somewhere.around.the.internet_:
```
sudo mv ~/SCPH1001.BIN $EPSXE/bios/
```

You can run the emulator with either software render or hardware acceleration plugin. The latter requires a NVIDIA, ATI, or similar card with working OpenGL drivers. You can install both and use the one that works best for you. The hardware acceleration plugin in this how-to apperantly requires a quite new card (I don't know how new though). If it doesn't work there is an older plugin that uses MesaGL. Look [here]("http://www.pbernert.com/html/gpu.htm"). The installation is quite similar, but I don't care to include it in this guide.  

Install hardware acceleration plugin:
```
cd ~
wget http://www.pbernert.com/gpupetexgl208.tar.gz
sudo tar xfz ~/gpupetexgl208.tar.gz -C $EPSXE/plugins/
sudo mv $EPSXE/plugins/cfgPeteXGL2 $EPSXE/cfg/
sudo mv $EPSXE/plugins/gpuPeteXGL2.cfg $EPSXE/cfg/
sudo chmod 666 $EPSXE/cfg/gpuPeteXGL2.cfg
```

Install software render plugin: 
```
cd ~
wget http://www.pbernert.com/gpupeopssoftx117.tar.gz
sudo tar xfz ~/gpupeopssoftx117.tar.gz -C $EPSXE/plugins/
sudo mv $EPSXE/plugins/cfgPeopsSoft $EPSXE/cfg/
sudo mv $EPSXE/plugins/gpuPeopsSoftX.cfg $EPSXE/cfg/
sudo chmod 666 $EPSXE/cfg/gpuPeopsSoftX.cfg
```

Install audio plugin (uses the OSS sound daemon):
```
cd ~
wget http://www.pbernert.com/spupeopsoss109.tar.gz
sudo tar xvfz ~/spupeopsoss109.tar.gz -C $EPSXE/plugins/
sudo mv $EPSXE/plugins/cfgPeopsOSS $EPSXE/cfg/
```

Create a shell script that will start ePSXe:
```
sudo gedit /usr/local/bin/epsxe
```
and paste this:
```
#!/bin/bash

export EPSXE='/usr/local/games/epsxe'
export LD_LIBRARY_PATH=$EPSXE
cd $EPSXE
./epsxe
chmod 666 $EPSXE/cfg/*.cfg $EPSXE/sstates/* \
$EPSXE/memcards/*.mcr $EPSXE/snap/* 2>/dev/null
```

Save it and change permissions for the new file:
```
sudo chmod 755 /usr/local/bin/epsxe
```

You can now start by typing "epsxe" in the terminal (without "").

[SIZE="3"]Configuration[/SIZE]

[LIST]
[*]In the menu, open "Config -> BIOS", and set it to /usr/local/games/epsxe/bios/SCPH1001.BIN, click OK.


[*]Open "Config -> Video", and select either "Pete's XGL2 Driver 2.8" or "P.E.Op.S. Softx Driver 1.17". Click configure, then OK to write a config file. Verify that it is working by clicking the Test button, then OK. 


[*]In "Config -> Sound" select "P.E.Op.S. OSS Audio Driver", Configure, then OK. Verify that it is working by clicking the Test button, then OK.


[*]In Config -> CDROM, set the path to your CD/DVD-ROM. In most cases it should be /dev/cdrom but in my case /dev/hdc. You can check your path by typing "mount |grep cd" in a console.


[*]In Config -> Game Pad -> Pad 1 menu, you can set up the controls. If you want to use a real PSX Joypad to play with, you have to search for a advices elsewhere, since I don't have one that I can use with my computer or any experience using them in Linux. There is a guide in the original howto, referred to in the beginning of this text, but as said, I haven't tried it.[/LIST]

Now you should be all set. If you want to use an original PSX CD-ROM, insert it and select "File -> Run CDROM" It might take a while for the game to load, so be patient. You can also load backup ISO:s from your hard disk with "File -> Run ISO. When you are running your game you can press Esc any time to exit, save/load game states, or change discs. To get back, select Run -> Continue.

[SIZE="3"]Troubleshooting[/SIZE]
[LIST]
Problems with segmentation faults using PeteXGL2 plugin, See [this]("http://ubuntuforums.org/showpost.php?p=983473&postcount=63") reply.
e.g:[/LIST]
```
[I]* Init gpu[0][libgpuPeteXGL2.so.2.0.8]
/usr/local/bin/epsxe: line 6: 25248 Segmentation fault ./epsxe[/I]
```

[LIST]Problems with Chrono Cross and possibly others might be solved by using an older version of Epsxe. See [here]("http://ubuntuforums.org/showpost.php?p=1095913&postcount=77").
[/LIST]

If you have other problems with plugins that you can't solve by reading the discussions/replies in this thread, check out [Pete&#8217;s Domain]("http://www.pbernert.com/html/gpu.htm") and try using some of the other plugins not covered by this guide.

Have fun, and if you run into problems, post here and hopefully you will get help...

The mandatory howto screenshot. :)  The game is Final Fantasy 7:

[[IMG]http://img168.imageshack.us/img168/3593/screenshotlu6.th.jpg[/IMG]](http://img168.imageshack.us/my.php?image=screenshotlu6.jpg)

---

### Post by bored2k on 2005-11-28
Note: **No** posting download links for any of the PSX Bios files.

---

### Post by johannes on 2005-11-28
Okay. Yeah, that might be a good idea.

---

### Post by Havoc on 2005-12-03
Yup, this howto works great.Just waht I was looking for!

You can find more linux plugins [Here]("http://www.ngemu.com/psx/plugins.php?cat=1&os=linux").
Be carefull though, some crash epsxe, because they depend on libraries that either do not exist, or are outdated.So, either prefer the open-source ones, and compile them on you system, or just stick to the ones mentioned here.
I just have to say that Pete's MesaGL plugin worked great for me, along with Omnijoy, which I compiled (No big deal).The only one that did not work was Eternal SPU.

Keep it up!:cool:

---

### Post by yaztromo on 2005-12-21
Brilliant guide thank you.

On my system the xgl2 driver causes a "couldn't get fbconfig" error. I changed to the mesa plugin mentioned above and is working okay for me.

---

### Post by poofyhairguy on 2005-12-21
Wow! I can't wait to try this! For the life of me I could not get it to work in Breezy before, but I could with Hoary.

Thanks a lot! Perfect timing (I was learned how to chroot Hoary to fix this problem previously).

---

### Post by akurashy on 2005-12-21
Wow! I can't wait too eeeep, going to try it soon :D

---

### Post by akurashy on 2005-12-21
This is one of the greatest how-to i ever readed!, great work [johannes]("http://ubuntuforums.org/member.php?u=25578")

Here is a screeny of me playing final fantasy 7 D:
*link broken*

---

### Post by johannes on 2005-12-21
I'm glad it was a benefit to you. :)

---

### Post by benplaut on 2005-12-22
n64 0\/\/N5 j00!!!!111!!1

(sorry, i had to :P )

---

### Post by zi99y on 2005-12-23
very good howto, thanks!

I only had the one video renderer available, does anyone know if any hardware renderers work that use opengl - hope this isn't a stupid question!!

:D

---

### Post by rickwood on 2005-12-23
Awesome howto!  Thanks very much!  All is working good now.  The only problem I had is that none of my joypads seemed to work.  I had set them up previously using Automatix, and Linux sees them fine, but they didn't work in ePSXe.  Fixed this by installing padjoy.  It can be found here:

[http://http://members.chello.at/erich.kitzmueller/ammoq/padJoy082.tgz]("http://http://members.chello.at/erich.kitzmueller/ammoq/padJoy082.tgz")

---

### Post by NMUrugbysteve on 2005-12-23
I get this error when trying to run this.

./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

any hints? I have all the libgtk stuff from apt installed

*edit*

Nevermind, apt-cache search sucks nuts, I searched synaptic and found my stuff immediately.

---

### Post by sapo on 2006-01-01
[QUOTE=akurashy]This is one of the greatest how-to i ever readed!, great work [johannes]("http://ubuntuforums.org/member.php?u=25578")

Here is a screeny of me playing final fantasy 7 D:
[http://davidgonz.com/wp-content/finalfantasy.png](http://davidgonz.com/wp-content/finalfantasy.png)[/QUOTE]
Nice, i aways had epsxe here, since i installed once i just copy it when i format my pc.

Now i m playing Final Fantasy Tactics, last time i finished FFVII it was in 27 hours, how many did you spent in it akurashy? xD

---

### Post by Akkarin on 2006-01-06
[QUOTE=NMUrugbysteve]I get this error when trying to run this.

./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

any hints? I have all the libgtk stuff from apt installed

*edit*

Nevermind, apt-cache search sucks nuts, I searched synaptic and found my stuff immediately.[/QUOTE]

Can you please tell me how to install it, I searched synaptic but I can't find "libgtk-1.2.so.0" Only "libgtk.....". Thanks for your time!

---

### Post by Denurb on 2006-01-08
Hi, thanks for the HOW-TO
However when I come to config my video or sound it crashes and I get the following error message:
Gdk-WARNING **: can not set locale modifiers
/usr/local/bin/epsxe: line 6:  9743 Segmentation fault      ./epsxe
Any suggestions?

---

### Post by nerval on 2006-01-08
great howto; thanks !

---

### Post by eddymacuser on 2006-01-08
hi, I'm a Linux newbie...

Thx for this How-To...

However when I try to run the script says: "cannot execute binary file". :( 

can someone help me?


p.s. How it runs with FF7?

---

### Post by johannes on 2006-01-08
[QUOTE=Akkarin]Can you please tell me how to install it, I searched synaptic but I can't find "libgtk-1.2.so.0" Only "libgtk.....". Thanks for your time![/QUOTE]

I'm not totally sure which package you need since I didn't get this message, but try installing libgtk1.2 and libgtk1.2-common.

---

### Post by johannes on 2006-01-08
[QUOTE=Denurb]Hi, thanks for the HOW-TO
However when I come to config my video or sound it crashes and I get the following error message:
Gdk-WARNING **: can not set locale modifiers
/usr/local/bin/epsxe: line 6:  9743 Segmentation fault      ./epsxe
Any suggestions?[/QUOTE]

It seems to me like there is some problems with your language settings, locales. I don't know how to fix it, but you could try searching for "locales" around the forum to get more info. Or maybe someone else knows how to solve it?

---

### Post by johannes on 2006-01-08
[QUOTE=eddymacuser]hi, I'm a Linux newbie...

Thx for this How-To...

However when I try to run the script says: "cannot execute binary file". :( 

can someone help me?


p.s. How it runs with FF7?[/QUOTE]

Are you sure you followed all the steps? What hardware do you use? Note that epsxe is made for i386 (common pc). If you use amd64 or powerpc it might not work.

---

### Post by eddymacuser on 2006-01-08
[QUOTE=johannes]Are you sure you followed all the steps? What hardware do you use? Note that epsxe is made for i386 (common pc). If you use amd64 or powerpc it might not work.[/QUOTE]

Yes, unfortunatly I'm using PPC... :( 
Thx a lot

Maybe there is a workaround to run the program anyway?

---

### Post by johannes on 2006-01-08
I don't think there is, but you can always try searching google for it.

A little sad thing about epsxe is that it's closed source, an executable file that only run on the platform it was compiled on.

There is another linux psx emulator, [PCSX]("http://www.pcsx.net/"), that is open source. If you have the time you can try compile and run it. The reason I haven't tried it is because I'm used to epsxe from when using windows and it works nice on my computer.

---

### Post by eddymacuser on 2006-01-08
[QUOTE=johannes]I don't think there is, but you can always try searching google for it.

A little sad thing about epsxe is that it's closed source, an executable file that only run on the platform it was compiled on.

There is another linux psx emulator, [PCSX]("http://www.pcsx.net/"), that is open source. If you have the time you can try compile and run it. The reason I haven't tried it is because I'm used to epsxe from when using windows and it works nice on my computer.[/QUOTE]

ok thx a lot

I've alredy try to use PCSX, but without good result with my 867 PowerBook...

...so maybe I can use my old psx...:???: :D

---

### Post by Denurb on 2006-01-10
[QUOTE=johannes]It seems to me like there is some problems with your language settings, locales. I don't know how to fix it, but you could try searching for "locales" around the forum to get more info. Or maybe someone else knows how to solve it?[/QUOTE]
Thanks for the reply - I'll have a look around

---

### Post by Twizz on 2006-01-11
Hi, is there a way for me to get my own Bios File from my PS2?  I have the SCPH-30001(Camped out for it on release day)  I also have a PSOne.  My PS2 is hooked up with a Network Adaptor trew my router.  I'm really wanteing to Play Xenogears again hehe.

---

### Post by Dark Damo on 2006-01-13
Nice i like the guide and was very easy to follow. I even found the bios files pretty easy too!

---

### Post by TFleck on 2006-01-28
Oh my! Its working perfectly! thank you!
Here is my screen:
[[IMG]http://img300.imageshack.us/img300/892/capturadatela7fb.th.png[/IMG]](http://img300.imageshack.us/my.php?image=capturadatela7fb.png)

---

### Post by jackwhite on 2006-02-03
Wow, this is really cool, think i'll try it when i get home. 
I am a bit concerned my computer won't be up to it though... 850 mHz processor and 512 MB PC 133 memory. Would that be enough to run PS2 or even PS1 games?

And what do you do about joypads?

---

### Post by ninocass on 2006-02-03
Does this support PS2 games? i tried it but it just stalled, do i need the PS2 bios?

i own both PS1 and PS2, i fancy a bit of Grand theft auto on the move :)

thanks

Nino

---

### Post by bored2k on 2006-02-03
[QUOTE=ninocass]Does this support PS2 games? i tried it but it just stalled, do i need the PS2 bios?

i own both PS1 and PS2, i fancy a bit of Grand theft auto on the move :)

thanks

Nino[/QUOTE]
It doesn't.

---

### Post by ninocass on 2006-02-03
ach no :(  could anyome recomend an emulator for PS2?

sorry to go off topic :)

Nino

---

### Post by bored2k on 2006-02-04
[QUOTE=ninocass]ach no :(  could anyome recomend an emulator for PS2?

sorry to go off topic :)

Nino[/QUOTE]
No no, read the guidelines. We don't  allow drift-offs.

---

### Post by Twizz on 2006-02-06
Hi, I keep getting this error.
/usr/local/bin/epsxe: line 6: 13693 Segmentation fault      ./epsxe

How do I fix that?

EDIT: nm I kinda fixed it..

---

### Post by anath3ma on 2006-02-21
the cdda from my wipeout XL cd works when its in the drive but not from an iso image.  any way to fix this?

---

### Post by zi99y on 2006-02-22
Is WipeoutXL a PS2 game? and if so does it work? I might buy it because I loved Wipeout 2097, and was a bit of a master too...

I wasn't sure that PS2 games worked on this emu

Sorry can't help with your iso issue though.

---

### Post by grte on 2006-02-22
I followed the guide, and it installed just fine, I can open it and all.  But when I try go run a game, I get a segmentation fault.

Here's the terminal output:

```
 * Running ePSXe emulator version 1.6.0.
 * Memory handlers init.
 * ePSXe: PSX BIOS loaded [/usr/local/games/epsxe/bios/SCPH1001.BIN].
 * Init internal cdrom ... ok
 * First/Last track: 1 1
 * Track 1:  (DATA) - Start 0: (00,02,00)
 * NTSC cdrom detected.
 * Init gpu[0][libgpuPeteXGL2.so.2.0.7]
Error: couldn't get fbconfig
Missing ATI render-texture extension!NVIDIA Corporation
unknown board/AGP/SSE2/3DNOW!
 * Open gpu[0]
 * Init spu[0][libspuPeopsOSS.so.1.0.9]
 * Open spu[0]
OmniJoy Init: You are using v1.0.0 build 8
 * Init pad[0][libpadOmniJoy.so]
OmniJoy: Using Joystick Logitech Logitech Dual Action for controller 1
Error OmniJoy Controller 2: No such file or directory
OmniJoy: Disabling controller 2 * Open pad[0]
/usr/local/bin/epsxe: line 6:  8933 Segmentation fault      ./epsxe

```

Anyone have any ideas?

---

### Post by grte on 2006-02-22
By the way, my video card is an Asus GeForce 6800 XT, so I have no idea why it  would say anything about ATI texture renderer.

---

### Post by grte on 2006-02-22
Nevermind, I got it.  If anyone is having a similiar issue, I fixed it by opening up /usr/local/games/epsxe/cfg/gpuPeteXGL2.cfg and changing the NoRenderTexture value to 1.

---

### Post by anath3ma on 2006-02-22
[QUOTE=zi99y]Is WipeoutXL a PS2 game? and if so does it work? I might buy it because I loved Wipeout 2097, and was a bit of a master too...

I wasn't sure that PS2 games worked on this emu

Sorry can't help with your iso issue though.[/QUOTE]


wipeout xl is a ps1 game.  i play it often using epsxe.  problem is, when you use a cd image, you get none of the background audio tracks.

---

### Post by LordBug on 2006-02-23
Is there a *working* ALSA sound module for EPSXE or how to fix the spu Eternal to work?  Spu Eternal craps itself with "libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory" if you try to configure sound or video.

---

### Post by makisupa123 on 2006-03-08
along the lines of the last question asked....how do i get sound working?

when the program attempts to open "spu[0]" i get a no device.  running it under aoss yields no joy and esddsp freezes it.  My sound is prmarily alsa...how should i set this up?

Thanks,

Mak

---

### Post by n1tro on 2006-03-09
Great tutorial. Got mine working in a few minutes! Here's a screenshot for encouragement. Playing Tenchu Steath Assasins off a cd and it loads fast!

[IMG]http://www.mad-mods.com/vietnam/psx.png[/IMG]

---

### Post by grte on 2006-03-10
[QUOTE=makisupa123]along the lines of the last question asked....how do i get sound working?

when the program attempts to open "spu[0]" i get a no device.  running it under aoss yields no joy and esddsp freezes it.  My sound is prmarily alsa...how should i set this up?

Thanks,

Mak[/QUOTE]

Do you have two sound cards?  ePSXe will send it to one by default, and I haven't a clue how to change it.  But I can get sound if I switch my speakers from my audigy 2 to the built in soundcard on the mobo.

---

### Post by wesman83 on 2006-03-13
I can get FF7 running with the MesaGL plugin (which works ok, but still a bit slow when its going to a fight scene) but when i try to use Pete's XGL 2.8 or 2.7 plugins i get this error:

 * Init gpu[0][libgpuPeteXGL2.so.2.0.8]
/usr/local/bin/epsxe: line 6: 20287 Segmentation fault      ./epsxe

and epsxe crashes... has anyone fixed this issue?

if not what are your settings for running Final Fantasy 7 with the Mesa plugin if you're using it?

Thanks for any help you can provide!

---

### Post by xiaoxin on 2006-03-19
Hi

Has anyone gotten FFIX to run?

If you did please tell me your settings, i can't get it to run.

---

### Post by johannes on 2006-03-19
[QUOTE=wesman83]I can get FF7 running with the MesaGL plugin (which works ok, but still a bit slow when its going to a fight scene) but when i try to use Pete's XGL 2.8 or 2.7 plugins i get this error:

 * Init gpu[0][libgpuPeteXGL2.so.2.0.8]
/usr/local/bin/epsxe: line 6: 20287 Segmentation fault      ./epsxe

and epsxe crashes... has anyone fixed this issue?

if not what are your settings for running Final Fantasy 7 with the Mesa plugin if you're using it?

Thanks for any help you can provide![/QUOTE]

What kind of a graphics card do you have and what drivers are you using with it? You need to have the proprietary ati/nvidia drivers installed and working to use the XGL2 plugin.

---

### Post by Kurt` on 2006-03-20
Hi,

I followed your guide, and it worked fine, except for one thing. It complained that libspu.so was missing when I launched either the bios or cd-rom, so I symlinked libspu.so to libspuPeopsOSS.so.1.0.9 and then it worked fine. :)

However, I am having a problem playing games from the cd-rom drive. (I can launch into the bios fine with sound) The game I am testing is Metal Gear Solid (original NTSC discs). Here is the output from when I try to run it:

```
kurt@spark:~$ epsxe
 * Running ePSXe emulator version 1.6.0.
**--- here i click file->run cdrom ---**
 * Memory handlers init.
 * ePSXe: PSX BIOS loaded [/usr/local/games/epsxe/bios/SCPH1001.BIN].
 * Init internal cdrom ... ok
CD read toc header failed (25)
 * First/Last track: 7 2
 * Track 1: CD get track start failed (25)
 (AUDIO) - Start 0: (00,00,00)
 * Track 2: CD get track start failed (25)
 (AUDIO) - Start 1: (00,00,00)
CD(0,2,16) read ioctl failed (25)
CD(241,40,71) read ioctl failed (25)
CD(241,40,72) read ioctl failed (25)
 * NTSC cdrom detected.
 * Init gpu[0][libgpuPeteXGL2.so.2.0.8]
NVIDIA Corporation
GeForce FX 5600/AGP/SSE/3DNOW!
 * Open gpu[0]
 * Init spu[0][libspu.so]
 * Open spu[0]
CD(0,2,16) read ioctl failed (25)
CD(0,2,0) read ioctl failed (25)
```

Then it simply freezes til I kill it. I've set Config->Cdrom to "/dev/cdrom0" and "/media/cdrom0" with no success. I know you can't simply rip an ISO of the game-cd and launch it, so I'm not sure what to do. :p This is on Ubuntu Breezy

Thanks in advance

Edit:

2 minutes after I posted this, I tried /dev/cdrom instead. And it works!

Screenshot: [http://xs73.xs.to/pics/06121/mgs.jpg](http://xs73.xs.to/pics/06121/mgs.jpg)

---

### Post by xiaoxin on 2006-03-20
well in fact you can easily make an image of a cd and run it

```
cdrdao read-cd --read-raw --datafile gamename.bin --driver generic-mmc-raw gamename.toc
```




ps

ignore my previous message about ffix, got it running now

---

### Post by Kurt` on 2006-03-20
Excellent, I'm going to write that into a simple bash script later to basically automate cd-ripping into the background. Thanks!

---

### Post by rbenchley on 2006-03-20
I just wanted to say thank you for the wonderful guide.  I'm an Ubuntu newbie, so guides like this are a wonderful resource.

---

### Post by n1tro on 2006-03-25
I'm getting the same segmentation error. On my previous laptop ZD7000, I installed everything fine and was using the hardware acceleration (see snapshot in previous post). Now with my current laptop Compaq R3000, I can only use the software acceleration to get it going. Both laptops have Nvidia based graphics boards and I used the drivers off of the AutoMatrix utility. So I'm puzzled. Do you think it has to do with the fact that my R3000 is a AMD64 (running 32bit Ubuntu with K7 kernel) versus the P4 3.02ghz HT (running 32bit Ubuntu with i686-smp kernel)?

[QUOTE=johannes]What kind of a graphics card do you have and what drivers are you using with it? You need to have the proprietary ati/nvidia drivers installed and working to use the XGL2 plugin.[/QUOTE]

---

### Post by amunimanghi on 2006-03-29
i did the steps correctly but i get this when i try to run it
```
******@ubuntu:~$ epsxe
/bin/bash: export EPSXE='/usr/local/games/epsxe' export LD_LIBRARY_PATH=$EPSXE cd $EPSXE ./epsxe chmod 666 $EPSXE/cfg/*.cfg $E: No such file or directory

```

---

### Post by amunimanghi on 2006-04-05
never mind i fixed it

---

### Post by jon_benge on 2006-04-14
This is an AWESOME guide! Thanks!

I've just got one little problem however! I need to install the CDRMOOBY plugin but I don't know how to!

I tried copying it to the ePSXe plugins folder, but somethings gone wrong and now ePSXe wont start. I get this error message:

```
plugins/libcdrmooby-2.8.so: undefined symbol: XftDrawSetCli
```

How should I go about installing this plugin?

---

### Post by KevNice on 2006-04-20
n@softbank221079077024:~$ epsxe
 * Running ePSXe emulator version 1.6.0.
 * Memory handlers init.
 * ePSXe: PSX BIOS loaded [/usr/local/games/epsxe/bios//SCPH1001.BIN].
 * Init internal cdrom ... ok
 * First/Last track: 1 1
 * Track 1:  (DATA) - Start 0: (00,02,00)
 * NTSC cdrom detected.
 * Init gpu[0][libgpuPeopsSoftX.so.1.0.17]
 * Open gpu[0]
plugins/libspu.so: cannot open shared object file: No such file or directory

What is this libspu.so file? I couldnt find it on synaptic..

---

### Post by nchase on 2006-04-28
How can I get sound working? I get this message:

 * Init spu[0][libspuPeopsOSS.so.1.0.9]
Sound device not available!
 * Open spu[0]


Also, how can I get a joypad working with this?

---

### Post by Chris Tucker on 2006-04-28
Wish there was a fully working PS2 emulator, my ps2 fried, and im dying to play my games >.< snes games are getting old. :(

---

### Post by bluevoodoo1 on 2006-04-28
This guide is the best!

Here's a screenshot (love the typo!)

---

### Post by nchase on 2006-04-28
Ok, I got my joypad problem solved (copied the config and plugin files from the padjoy package available on synaptic), and sound only seems to work when I don't have another program that uses audio open. Similar to my problem in Firefox.

Anyone know why it might be slow at resolutions higher than 640x480? My computer is very good.

[QUOTE=nchase]How can I get sound working? I get this message:

 * Init spu[0][libspuPeopsOSS.so.1.0.9]
Sound device not available!
 * Open spu[0]


Also, how can I get a joypad working with this?[/QUOTE]

---

### Post by Doat on 2006-04-30
Mega Man 8 runned perfectly until I beat my first boss, which caused epsxe to crash with:

```
/usr/local/bin/epsxe: line 6: 32117 Muistialueen ylitys     ./epsxe
```

Muistialueen ylitys is Finnish and means something like "Excess of memory".

This has happened for Frost Man and Grenade Man so I assume it happens for all the bosses. The crash happens a while after that purple thing appears on the floor after the boss has exploded. Does anyone happen to know how to fix this?

---

### Post by Clazziquai on 2006-05-02
A bit of a problem...
[INDENT] kuja@shugotenshi:~$ epsxe
 * Running ePSXe emulator version 1.6.0.
 * Memory handlers init.
 * ePSXe: PSX BIOS loaded [/usr/local/games/epsxe/bios/Scph1001.bin].
 * Init internal cdrom ... ok
CD read toc header failed (25)
 * First/Last track: 7 2
 * Track 1: CD get track start failed (25)
 (AUDIO) - Start 0: (00,00,00)
 * Track 2: CD get track start failed (25)
 (AUDIO) - Start 1: (00,00,00)
CD(0,2,16) read ioctl failed (25)
CD(13,1,23) read ioctl failed (25)
CD(13,1,24) read ioctl failed (25)
 * NTSC cdrom detected.
 * Init gpu[0][libgpuPeteXGL2.so.2.0.8]
/usr/local/bin/epsxe: line 6: 25248 Segmentation fault      ./epsxe
[/INDENT]My card is an NVIDIA TNT2.

I hope someone knows what's up, thanks.

---

### Post by ljubomir on 2006-05-04
[QUOTE=Clazziquai]A bit of a problem...
[INDENT] kuja@shugotenshi:~$ epsxe
 * Running ePSXe emulator version 1.6.0.
 * Memory handlers init.
 * ePSXe: PSX BIOS loaded [/usr/local/games/epsxe/bios/Scph1001.bin].
 * Init internal cdrom ... ok
CD read toc header failed (25)
 * First/Last track: 7 2
 * Track 1: CD get track start failed (25)
 (AUDIO) - Start 0: (00,00,00)
 * Track 2: CD get track start failed (25)
 (AUDIO) - Start 1: (00,00,00)
CD(0,2,16) read ioctl failed (25)
CD(13,1,23) read ioctl failed (25)
CD(13,1,24) read ioctl failed (25)
 * NTSC cdrom detected.
 * Init gpu[0][libgpuPeteXGL2.so.2.0.8]
/usr/local/bin/epsxe: line 6: 25248 Segmentation fault      ./epsxe
[/INDENT]My card is an NVIDIA TNT2.

I hope someone knows what's up, thanks.[/QUOTE]


For all peope having troubles with **SEGMENTATION FAULT** and PeteXGL2 plugin:

**vi /usr/local/games/epsxe/cfg/gpuPeteXGL2.cfg**

and play with settings named:

[B]NoRenderTexture
TexFilter[/B]

and maybe others. If nothing works, you can always try with Pete's Mesa plugin.

---

### Post by mikemn84 on 2006-05-20
First of all, great howto.  I got up and running in no time.  I even got my gamepad working.  

My problem was with creating an iso image from a game.  I was going to try this:

```
cdrdao read-cd --read-raw --datafile gamename.bin --driver generic-mmc-raw gamename.toc
```

This didn't work as it is written, so I assume some of this stuff I am supposed to adapt for my own situation.  But I don't know what to put in for some of the things.  For i.e. where can I find the exact gamename the disk has? (or am I just supposed to name it what I want).  Any suggestions?

Thanks.

---

### Post by gommle on 2006-05-23
Anybody got FF IX working? I know one dude got it working, but he didnt tell how :P

Also now epsxe crashes on start just because i put some plugins in the /plugins folder. Ill just have to test which one does it.

Edit: Nvm, a reboot and some files in the $EPSXE/patches folder fixed it.

---

### Post by grte on 2006-05-23
[QUOTE=mikemn84]First of all, great howto.  I got up and running in no time.  I even got my gamepad working.  

My problem was with creating an iso image from a game.  I was going to try this:

```
cdrdao read-cd --read-raw --datafile gamename.bin --driver generic-mmc-raw gamename.toc
```

This didn't work as it is written, so I assume some of this stuff I am supposed to adapt for my own situation.  But I don't know what to put in for some of the things.  For i.e. where can I find the exact gamename the disk has? (or am I just supposed to name it what I want).  Any suggestions?

Thanks.[/QUOTE]

To make an exact duplicate, try this command:

cat (path/to/your/disc/drive) > image.iso

The path to your disc drive will change depending on what it is.  For example, I've got a DVD+-RW, which resides at /dev/dvdrw.

---

### Post by RavenOfOdin on 2006-05-23
Final Fantasy IX always freezes for me around the Dali cutscene, not sure why.

---

### Post by Khaotik on 2006-05-24
Thx for the howto. I used the PeteXGL2 hardware render. My gfx card is a ATi Radeon 9200. I get this error when running from disk. 

 * Memory handlers init.
 * ePSXe: PSX BIOS loaded [bios/SCPH1001.BIN].
 * Init internal cdrom ... ok
 * First/Last track: 1 1
 * Track 1:  (DATA) - Start 0: (00,02,00)
 * NTSC cdrom detected.
 * Init gpu[0][libgpuPeteXGL2.so.2.0.8]
Gdk-ERROR **: GLXUnsupportedPrivateRequest
  serial 37 error_code 163 request_code 143 minor_code 16
Missing ATI render-texture extension!Missing shader extensions!

Please help, I know this is an old thread.

---

### Post by gommle on 2006-05-24
[QUOTE=RavenOfOdin]Final Fantasy IX always freezes for me around the Dali cutscene, not sure why.[/QUOTE]

Install ePSXe version 1.5.2 or everything except version 1.6 and it should work.

---

### Post by RavenOfOdin on 2006-05-24
[QUOTE=gommle]Install ePSXe version 1.5.2 or everything except version 1.6 and it should work.[/QUOTE]

I think I have 1.5.2 . . .I'll check that.

---

### Post by gommle on 2006-05-25
I used version 1.6 when doing the Dali stuff. Im already in Lindblum, and no crash yet. Im using XGL2 2.8 and  OSS Audio driver 1.9.

Maybe its only for some people :S
Nothing to do with Linux i think, since the bug applies to Windows too.

---

### Post by RavenOfOdin on 2006-05-25
Nope, 1.6. >.<

Guess I'm gonna have to switch versions when the intarweb comes back up on my n*x.

---

### Post by gommle on 2006-05-25
[QUOTE=RavenOfOdin]Nope, 1.6. >.<

Guess I'm gonna have to switch versions when the intarweb comes back up on my n*x.[/QUOTE]

Oh, and since version 1.52 isnt in the ePSXe site ill post the link:

> [http://www.epsxe.com/files/epsxe152lin.zip](http://www.epsxe.com/files/epsxe152lin.zip)

Just install it as in the howto, just change directory and rename the file in /usr/bin.

---

### Post by ace2005 on 2006-05-25
All i did to install epsxe was add this to my sources.list

deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper main dupdate french

Reload and install it via synaptic. Then i got the bios and stuck it in ~/.epsxe/bios/ The bios i use is called scph7502. The version in this repo is 1.6, i tested it with Tony Hawk's Pro Skater 2 and it worked fine.

---

### Post by Drakwen on 2006-05-27
Hello im new to this and i am sorry to bother you, i followed every step of the guide but it seems epsxe refuses to work. Everything seems fine, but when it comes to configure the video and sound :

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 

> drakwen@central:~$ epsxe
 * Running ePSXe emulator version 1.6.0.
/usr/local/bin/epsxe: line 6:  8310 Violación de segmento  ./epsxe

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 

**Translation would be:**

> drakwen@central:~$ epsxe
 * Running ePSXe emulator version 1.6.0.
/usr/local/bin/epsxe: line 6:  8310 **Segment Fault** ./epsxe

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 

If i try to configure the sound line 6 keeps appearing but the number 8310 changes everytime to a different one.

I would appreciate any kind of help.

*BTW: i installed the epsxe in the /home/drakwen/epsxe folder.*

---

### Post by gommle on 2006-05-29
Try with other plugins. Mine crashes too on certain plugins. Plugins can be downloaded on ngemu.

[http://www.ngemu.com/plugins.php?cat=1&os=linux](http://www.ngemu.com/plugins.php?cat=1&os=linux)

---

### Post by canci on 2006-06-05
Hi!

[COLOR="Red"]**!!THIS IS VERY IMPORTANT!!**[/COLOR]

I dunno if anyone mentioned it, but ePSXe 1.6 might have issues on
some configurations with certain games, like my PC had w/Chrono Cross.
This is true for Windows, dunno if it is for Linux.

Anyway, if you should encounter such a problem, w/Chrono Cross maybe,
just try the older version, 1.5.2.

If you browse the download section on epsxe.com, the Linux version won't be there linked, but it is on the site!
Just do: 

```
wget http://www.epsxe.com/files/epsxe152lin.zip
```

or enter the URL into a browser to download it!

For any emu q's, try: 
**http:/forum.ngemu.com/**

;D enjoy!

---

### Post by akurashy on 2006-06-11
[quote=canci]Hi!

[COLOR=Red]**!!THIS IS VERY IMPORTANT!!**[/COLOR]

I dunno if anyone mentioned it, but ePSXe 1.6 might have issues on
some configurations with certain games, like my PC had w/Chrono Cross.
This is true for Windows, dunno if it is for Linux.

Anyway, if you should encounter such a problem, w/Chrono Cross maybe,
just try the older version, 1.5.2.

If you browse the download section on epsxe.com, the Linux version won't be there linked, but it is on the site!
Just do: 

```
wget http://www.epsxe.com/files/epsxe152lin.zip
``` 
or enter the URL into a browser to download it!

For any emu q's, try: 
**http:/forum.ngemu.com/**

;D enjoy![/quote]

Also to add, people who are stuck playing FF9 need 1.5.2 version, 

Best optimization im using , i have a Geforce FX 5200, 
If your music is a bit slow, use eternal SPU, to install just do like you with the other plugins, nothing hard

If you feel the game is slow, use Pete's MesaGL Plugin, this little baby helped me in performance so much it feels like a normal game now

You can get this plugins in [http://www.ngemu.com/psx/pcsx.php?action=plugins](http://www.ngemu.com/psx/pcsx.php?action=plugins)
[SIZE=5]**(Note: LOOK IN THE LINUX SECTION BELOW) *just find "Linux" * **[/SIZE]

---

### Post by TristanMike on 2006-07-18
Hi, thanx, great guide. With some small tweaking and some frustration, I've got it running on Dapper now, even with my Logitech Rumblepad 2 working (more or less, well, maybe a little less :P).

I have just one (maybe two) small issues. First I can't create a shortcut to epsxe, for some reason it wont start when I click it. Can anyone tell me what I'm probably obviously forgetting ?

Second, and more importantly, when I end my ePSXe session, I loose the ability to type in the teminal and when it goes back to the prompt my working directory is skewed, I have to close it and open a new one, in most cases this isn't a huge issue, but occasionally it will lock the entire system up and I have to hard reboot. It doesn't matter how I end the program, be it the "X" or File-Quit or "Ctrl-C", it all leads to the same thing. [Here's](http://www.ubuntuforums.org/attachment.php?attachmentid=12917&stc=1&d=1153236476) a screenie.

[Here's ](http://www.ubuntuforums.org/attachment.php?attachmentid=12918&stc=1&d=1153236476)a screenie of FF9 =)....Xenogears, here I come!

---

### Post by qrazi on 2006-07-18
I cannot select plugins. I installed fopr example PeteMesaGL and PeteXGL2, but epsxe only show Petesmesagl. And i also cannot configure de video part.

---

### Post by junaediabdillah on 2006-08-05
This is the error message, when I try epsxe in my Dapper. so, what can I do to fix this?
TIA
Junaedi Abdillah

---

### Post by Hairy_Palms on 2006-08-05
what i had to do when i installed psxe, (not from this guide i should add as a disclaimer)
i had to link whicher sound/graphics plugin i was using to 
so if you use petes mesagl plugin and PeopsOss plugin then u need to run
```

sudo ln -s ~/epsxe160lin/plugins/libgpuPeteMesaGL.so.1.0.76 ~/epsxe160lin/plugins/libgpu.so
sudo ln -s ~/epsxe160lin/plugins/libspuPeopsOSS.so.1.0.8 ~/epsxe160lin/plugins/libspu.so
```

---

### Post by nrayever on 2006-08-18
nice howto!!! it really works!! but i still have some doubts, maybe later i will post them. thanks a lot!! :D :D

---

### Post by Angafirith on 2006-08-18
> **johannes said:**
> 
ePSXe is made for x86 (common pc) only. If you use amd64 or powerpc it probably won't work.

I have it running on my amd64 using the 32 bit libraries. There's a 32 bit ncurses library available in the repositories, but the gtk1.2 and glib1.2 were not. I downloaded the i386 debs manually, extracted them, and put the appropriate files in the /usr/lib32 directory.

---

### Post by devalanteriel on 2006-08-20
First of all: stort tack för guiden, Johannes! :)

Now, I've got it all up and running with no error messages - but also with no sound. According to the configuration, the "Plugin [is] working correctly." The plugin is Pete's P.E.Op.S OSS Audio Driver 1.9 and I'm using onboard nForce 2 sound.

Any help greatly appreciated, I don't even know where to start.

Edit: Boy, do I feel sheepish. I thought I'd tried everything... everything except unmuting the sound. Gah! Sorry for my stupidity. :)

---

### Post by k3v!n on 2006-08-28
ok............ but is this a ps2 or ps1 emulator??????? PLZ reply soon!!!!

---

### Post by grte on 2006-08-29
> **k3v!n said:**
> ok............ but is this a ps2 or ps1 emulator??????? PLZ reply soon!!!!

PS1.  Sadly, there aren't any PS2 emulators that'll play any games for Linux, far as I can tell.  The windows scene isn't much better on that front, come to think of it.

---

### Post by declaration on 2006-08-29
great guide. Worked fine for me and am now enjoying a bit of FF7.
Cheers.

---

### Post by R3linquish3r on 2006-08-30
I get this error when trying to play a game. The program starts fine I can select my plugins and all but when I go to start the game it crashes with this:

```
ed@ubuntu:~$ epsxe
 * Running ePSXe emulator version 1.6.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/usr/local/games/epsxe/bios//SCPH1001.BIN]. 
 * Loading ISO Format [BIN/IMG2352] ok
 * Force NTSC cdrom detected. 
 * Init gpu[0][libgpuPeteXGL2.so.2.0.8] 
NVIDIA Corporation
GeForce 7800 GS/AGP/SSE2/3DNOW!
 * Open gpu[0] 
 * Init spu[0][libspuPeopsOSS.so.1.0.9] 
 * Open spu[0] 
 * Closing spu ... done
 * Closing gpu ...
 * Shutdown gpu [0]  
 * Closing ISO system. 
 ePSXe (error) recompile block too large 

```

Would anyone have any idea's? Im running an NVIDIA 7800 GS BTW.

---

### Post by R3linquish3r on 2006-09-01
Bump.. still tryin to find a way to fix this.

---

### Post by Brunellus on 2006-09-06
Just a note to the author/maintainer of this howto:  I note that you have used a shell variable to simplify things in  your install instructions.

This is not a bad idea, but please tell people what you are doing when you use the variable.  A comment to the effect of 

"...but typing all of this out is tedious, so we will store the path in a shell variable by doing this..." (CODE EXAMPLE) "that way, we can call it up by typing $varname, which we'll have to do a few more times..."

Might make things a little more manageable.

---

### Post by johannes on 2006-09-12
I have now updated the guide slightly, mostly some formatting stuff and added a small troubleshooting section with what seems to be common problems. I don't really have the time to read trough all the 90 replies at this moment, but I might do that in the future.

Also, I migrated to Arch Linux a while ago and have not used Dapper much, and not at all epsxe with it... I still check this forum occationally though. But reading the latest replies here the guide seems to be working kind of all right except for the problems some people are having with the plugins. I have no idea how to solve most of them though... :-/

I don't know if /usr/local/games/epsxe is the most appropriate place anymore to install the app, maybe /usr/share/epsxe would conform better?

---

### Post by bratsplash on 2006-09-27
i dont have any idea how to run a ePSXe emulator... T_T can anyone who has a kind heart send me a complete working ePSXe ready to use emulator... please help me... T_T i'm a poor little girl that very poor in programs in other word {dumbass} please help me!... send it to my e mail add... [email]kuwki@yahoo.com[/email] thank you for your kindness! Y_Y

---

### Post by Josh_b on 2006-09-30
Hey, I installed epsxe fine (albeit to my home directory, rather than /usr/local/). It configured properly and everything, then I went to run a game and it says

ePSXe is NOT completely configurated go to config->bios to configure it

Any help? I'm using the bios file that I use in windows, so it should work, shouldn't it?

Josh

---

### Post by Josh_b on 2006-09-30
don't worry, it was to do with permissions.:(

But I don't get any sound. Any advice?

Also is there any way to get the netplay working?

Also, all my games work fine, 'cept for Crash Team Racing. The menus work fine, but when I go into a race, it will crash straight after the loading screen. It has the following error
>  * Running ePSXe emulator version 1.6.0.
 * Memory handlers init.
 * ePSXe: PSX BIOS loaded [/home/josh/games/epsxe/bios/SCPH1001.BIN].
 * Init internal cdrom ... ok
 * First/Last track: 1 1
 * Track 1:  (DATA) - Start 0: (00,02,00)
 * PAL cdrom detected.
 * Init gpu[0][libgpuPeteXGL2.so.2.0.8]
NVIDIA Corporation
GeForce 7900 GT/PCI/SSE2/3DNOW!
 * Open gpu[0]
 * Closing gpu ...
 * Shutdown gpu [0]
 Opcode 27 UNK (PC 000ac40c) (2951,34)


Please Help

Josh

---

### Post by ielliott on 2006-10-18
What is everyone using to get there Game Pads working?


What about ISOs?

Thanks :)

I'm having trouble with the game pad thing and the isos :(

---

### Post by kopilo on 2006-10-29
> **Akkarin said:**
> Can you please tell me how to install it, I searched synaptic but I can't find "libgtk-1.2.so.0" Only "libgtk.....". Thanks for your time!
ok what you need is, libgtk1.2_1.2.10-18_i386.deb and
libglib1.2_1.2.10-10.1build1_i386.deb.

I tried this on a Ubuntu 64 install, I could get ePSXe to open up, select a bios file but the video and sound  config crashed.
"libGL.so.1: cannot open shared object file: No such file or directory".

---

### Post by mokmoki on 2006-10-29
i have a problem here... i am trying to play with an ISO file, but epsxe just shows a black screen. it seems the game is not loading... any idea why?

---

### Post by kopilo on 2006-10-29
I've had this issue before as well but it was in windows, I fiddled with different display plugins and eventually got different games to work. There is also the possibility that you may need to apply a patch to the game.

Could you specify what game you are trying to get to work?

---

### Post by mokmoki on 2006-10-29
final fantasy 8... well, my emu is now working (i ditched the idea of running an iso, ill try to run it from the drive first)...

now my problem is, i can't hear any sound...

---

### Post by kopilo on 2006-10-29
Ahh FF8 is difficult, I could only get it running under ePSXe believe it or not.

In that case it's probably something to do with your sound plugin, not your game.

Also there is an awesome windows program for ripping PSX games to isos, it is called isoproducer, you can get it off megagames. It's slower then other programs and only runs in windows to my knowledge but it works. 

I'm sure you have to patch it if you rip it (due to the protection on it), that is why you got the black screen, see [here]("http://www.megagames.com/psx/psx_patches.shtml") for more info.

I have a question though, does running ePSXe under Linux still take up all of your processor resources?

---

### Post by PARO on 2006-10-30
Video works great only I have a problem with the sound. I've tried a couple Final Fantasy games and Metal Gear Solid and theres a whole lot of double and triple talk/sound going on. It sounds like:
"this is snake, this is snake, snake"  
"cornel, cornel, cornel"
"can you hear me, can you hear me, hear me"

For a short time this was funny, but I can't figure out how to fix it.
Do I need to change something in the settings? Has anyone else had this problem? I tried using the other linux sound plugin but it crashed epsxe. Video playback is fine, very nice even. I have a SiS SI7012 sound card, or sound or whatever.

EDIT:
I just checked all options and that seemed to cure the problem in MGS, but not in the FF games...

---

### Post by mokmoki on 2006-10-31
i don't know, but my sound in ff8 just started working for some reason. thanks for the help.

next question: can anybody confirm if the .mcr files for windows will work on the linux version? it's a pity if i can't play my save files from windows just because i started playing it on linux...

---

### Post by kopilo on 2006-10-31
There is a program called [memoryconverter]("http://forums.ngemu.com/epsxe-archive/13475-possible-use-gme-save-files-dex-emulators.html"), hopefully you can run it under something like wine in order to convert the mcrs.

But that is only to convert them from mcr to any other type, to my knowledge they should work fine because in theory they are an independent file of the operating system.

---

### Post by big z on 2006-10-31
um i have a weird proble on my windows pc if insert a ps1 cd i can read and play it . but on my linux pc i cant any fixs?

---

### Post by svzy on 2006-11-05
Ok, so I get up to this step:```
sudo tar xvfz ~/spupeopsoss109.tar.gz -C $EPSXE/plugins/
``` and then I get this message```
tar: /plugins: Cannot chdir: No such file or directory
tar: Error is not recoverable: exiting now

``` So I checked to see if the directory exists and it does... What do I do?

---

### Post by kopilo on 2006-11-06
try typing,
```
 echo $EPSXE
```
into terminal, if it outputs a blank line then your EPSXE system variable is blank.

You want $EPSXE to point to your epsxe directory, it is shown in the OP by the following command line.
```
export EPSXE='/usr/local/games/epsxe'
``` either then that your plugin directory may have a capital or something.

---

### Post by gezzabob on 2006-11-12
Unable to get ePSXe working have followed th instructions on here but when I try to run ps game get an error plugins/libspu.so: cannot open shared object file: No such file or directory

here is what I get.
geoffl@geoffl-desktop:~$ epsxe
 * Running ePSXe emulator version 1.6.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/home/geoffl/Desktop/SCPH1001.BIN]. 
 * Init internal cdrom ... ok
CD read toc header failed (25)
 * First/Last track: 7 2
 * Track 1: CD get track start failed (25)
 (AUDIO) - Start 0: (00,00,00) 
 * Track 2: CD get track start failed (25)
 (AUDIO) - Start 1: (00,00,00) 
CD(0,2,16) read ioctl failed (25)
CD(226,55,35) read ioctl failed (25)
CD(226,55,36) read ioctl failed (25)
 * NTSC cdrom detected. 
 * Init gpu[0][libgpuPeopsSoftX.so.1.0.17] 
 * Open gpu[0] 
plugins/libspu.so: cannot open shared object file: No such file or directorygeoffl@geoffl-desktop:~$ 

Anybody help me out with this one I have searched for info on libspu.so but no avail.

---

### Post by gezzabob on 2006-11-12
Not got passed the plugins/libspu.so: cannot open shared object file problem but it seems to be something to do with cd/dvd drive ?  I have ripped a final fantacy 7 disc to harddrive as an image used the...

cdrdao read-cd --read-raw --datafile ff7.bin --driver generic-mmc-raw ff7.toc

...command and ran the iso in ePSXe and it seems to run, although only a small screen but at least its working for now.

---

### Post by matemargo on 2006-11-13
I'm having a problem that I had already posted, but maybe this thread is more appropiate.

When I open the video config dialog (the same happens with audio), I only get and empty list of plugins with the word "DISABLED" as the only option in the dropdown.

Does anyone know why?

Thanks.

---

### Post by kopilo on 2006-11-14
> **matemargo said:**
> I'm having a problem that I had already posted, but maybe this thread is more appropiate.

When I open the video config dialog (the same happens with audio), I only get and empty list of plugins with the word "DISABLED" as the only option in the dropdown.

Does anyone know why?

Thanks.
Generally that means the plugin directory the program is pointing to (I think you can set it in settings, can't remember off the top of my head) is empty.

---

### Post by matemargo on 2006-11-14
This weird thing is that I had to rename the **plugin** directory in order to avoid the ePSXe crashing every time I open the configuration dialogs.
The plugin directory is now called **lib**.

Can I change that reference?

---

### Post by kopilo on 2006-11-15
I'm not sure, I haven't used ePSXe in a long time but I'd say that's the reason why you aren't finding any plugins, is because it looks for the plugin folder and doesn't find any..

Maybe what you could do is create an empty folder called plugin and see if it still crashes and then move over one plugin at a time testing to see if ePSXe still loads.

Tidious but you may be able to find some plugins that work this way, thus giving you sound and/or video.

---

### Post by Coldbird on 2006-12-02
The Thread seems kind of old but... I thought I would share my Knowledge aswell...

1. To get it running on 64bit Systems... (Dapper, Edgy) - you will have to manually get ur hands on the i386 Packages and manually extract ALL needed Libraries...

This Takes a ASSLOAD of Time... I know it... cause I did it... xD

2. For Peaple who are interested... I did a Fullpack... especially for 64bit Users... ^^ - Which got all the needed Modules aswell as a properly configured ePSXe without BIOS... It can be found in the Board... a search should deal some good results...

3. Peaple might wanna update the Tutorials... some are really... eh... out of date...

---

### Post by nscott on 2006-12-03
Does anyone have the 1.52 version laying around? I'm encountering the dreaded MDEC (fmv) that crashes Final Fantasy IX on disc one. Word is that 1.52 doesnt crash at this scene. PLEASE I've tried everyother method and the only 1.52 version I can find on the net is for windows.. Im desperate!

---

### Post by sshyperion on 2006-12-04
I have an ATI mobility Radeon 9000 32 MB video card on my laptop and had to install the software render drivers and the walk-thru posted on page one works excellently :) Thanks! and hopefully I don't come across that FF9 crash 'cause funnily enough, I'm playing FF9 of all games first in Kubuntu (6.06 Dapper).

---

### Post by Coldbird on 2006-12-04
Well... I highly suggest installing the fglrx Drivers for ATI Cards... Cause else you are busted...

I also found a good... AND PROPER WORKING - Guide aswell... ^_^

I doubt you could enjoy PSX Emulation without proper drivers anyway... Meh...

---

### Post by nscott on 2006-12-04
If you are using the latest version of epsxe or even pcsx you WILL encounter the crash on disc one in the city of Dali when you attempt to board the airship after fighting the Black waltz. I had to use a friends windows computer to get past it.

---

### Post by esaym on 2006-12-05
Are FMV's playing smoothly?  I tried to play ff7 with epsxe a few yearas ago on windows but I had to quit because I never could get the in game movies to play smoothly :(

---

### Post by realtiger on 2006-12-07
I can't run ff9. Anyone here can run ff9 using epsxe?

I mount ff9cd1.iso (converted from img file using ccd2iso).
Then run it and this is what I get:
```
tiger@tiger-lab:~/games/epsxe160$ ./epsxe 
 * Running ePSXe emulator version 1.6.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/home/tiger/games/epsxe160/bios/SCPH-1001.bin]. 
 * Init internal cdrom ... ok
CD read toc header failed (25)
 * First/Last track: 7 2
 * Track 1: CD get track start failed (25)
 (AUDIO) - Start 0: (00,00,00) 
 * Track 2: CD get track start failed (25)
 (AUDIO) - Start 1: (00,00,00) 
CD(0,2,16) read ioctl failed (25)
CD(89,1,41) read ioctl failed (25)
CD(89,1,42) read ioctl failed (25)
 * Force NTSC cdrom detected. 
 * Init gpu[0][libgpuPeteMesaGL.so.1.0.76] 
NVIDIA Corporation
GeForce PCX 5300/PCI/SSE2
 * Open gpu[0] 
 * Init spu[0][libspuPeopsOSS.so.1.0.9] 
 * Open spu[0] 
CD(0,2,16) read ioctl failed (25)
CD(0,2,0) read ioctl failed (25)

```

When I tried to run iso file directly without mounting, I got this:
```
tiger@tiger-lab:~/games/epsxe160$ ./epsxe 
 * Running ePSXe emulator version 1.6.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/home/tiger/games/epsxe160/bios/SCPH-1001.bin]. 
 * Loading ISO Format [BIN/IMG2352] ok
 * Force NTSC cdrom detected. 
 * Init gpu[0][libgpuPeteMesaGL.so.1.0.76] 
NVIDIA Corporation
GeForce PCX 5300/PCI/SSE2
 * Open gpu[0] 
 * Init spu[0][libspuPeopsOSS.so.1.0.9] 
 * Open spu[0] 
```

I always see a black screen.

Is there something wrong with the iso file? This is the content of ff9cd1.iso:
```
ff9.img  opening  seq01  seq02  seq03  slus_012.51  system.cnf
```

Anyone here knows a solution?

---

### Post by nscott on 2006-12-14
EDIT:
Whoops didn't see the links to 1.52 in the first post and the FFIX discussion earlier..

---

### Post by Tekovro on 2006-12-16
ePSXe is NOT completely configurated go to config>bios to configure it.

i got my video, audio plugins nicely configured. 
i got the SCPH1001.bin in the right directory with epsx set to it.
ive tried both /dev/cdrom and /dev/hdc for my cdrom setup.

WHY AM I GETTING THIS PROBLEM!?

---

### Post by oroboro on 2006-12-19
Wow, nice job plagiarizing this from [http://terror.snm-hgkz.ch/gaming/linux/epsxe_howto/](http://terror.snm-hgkz.ch/gaming/linux/epsxe_howto/).
You didn't even give any credit...

---

### Post by tarobs on 2006-12-21
I have a problem. For some reason, my PC can't read the PSX CD's now that I am in Ubuntu Edgy 6.10. I installed ePSXe before when I had Ubuntu Dapper 6.06 (but I reformatted my CD's and installed Edgy. I was having problems with the upgrade). 

When I try other CD's, my computer seem to be able to read them.

I dunno if this would help, but I get this error when I try to play:

* Running ePSXe emulator version 1.6.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [bios/scph1001.bin]. 
 * Init internal cdrom ... ok
CD read toc header failed (25)
 * First/Last track: 7 2
 * Track 1: CD get track start failed (25)
 (AUDIO) - Start 0: (00,00,00) 
 * Track 2: CD get track start failed (25)
 (AUDIO) - Start 1: (00,00,00) 
CD(0,2,16) read ioctl failed (25)
CD(194,36,52) read ioctl failed (25)
CD(194,36,53) read ioctl failed (25)
 * NTSC cdrom detected. 
 * Init gpu[0][libgpuPeteMesaGL.so.1.0.76] 
NVIDIA Corporation
GeForce4 MX 440/AGP/SSE2
 * Open gpu[0] 
 * Init spu[0][libspuPeopsOSS.so.1.0.9] 
 * Open spu[0] 
CD(0,2,16) read ioctl failed (25)
CD(0,2,0) read ioctl failed (25)

does anybody know what's wrong?

---

### Post by zappa420 on 2006-12-21
Okie all,  this is how I fixed the sound on my system after following the original posters directions.


Grab the Eternal SPU Plugin 1.41  from here:
[http://files.ngemu.com/psx/plugins/linux/spu/spuEternal141_linux.tgz]("http://files.ngemu.com/psx/plugins/linux/spu/spuEternal141_linux.tgz")

Extract the archive and drop this file: libspuEternal.so.1.41 into the epsxe/plugins directory.

Using apt-get, adept or synaptic install libsdl1.2-dev.  (Thats the version for Edgy atleast, dunno if it would have a different number for Dapper, Breezy or Feisty.) 

Start up epsxe and go to Config->Sound. Select the Eternal SPU Plugin 1.41. Click configure and change the Audio Device from OSS to SDL.  Cilck OK to close the plugin options. Click Test and it should be ok.

I also selected all 5 options available on the main Sound form, but, I'm not sure you need all those.  I guess for some games you do some games you don't.  The only game I have tested is FFVII and it works great with all 5 checked.

Have Fun & Good Luck

Zappa

---

### Post by korosunoii on 2007-01-06
I'm new to Ubuntu and I've recently installed Kubuntu 6.10
I've performed all the instructions except one.  That's the apt-get libgtk1.2 because when I perform I already have an updated version

kazuma@kazuma-laptop:~$ sudo apt-get install unzip libgtk1.2-common libgtk1.2
Reading package lists... Done
Building dependency tree
Reading state information... Done
unzip is already the newest version.
E: Couldn't find package libgtk1.2-common

When I run epsxe I get this message:

kazuma@kazuma-laptop:~$ epsxe
./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

How will I run it?  I can't run it with the new library?

---

### Post by ramasdf123 on 2007-02-08
blah i am getting this error and its going to drive me nuts!!

I got up to installing the hardware part and it messes up here

sudo mv $EPSXE/plugins/cfgPeteXGL2 $EPSXE/cfg/


$ sudo mv $EPSXE/plugins/cfgPeteXGL2 $EPSXE/cfg/
mv: target `/cfg/' is not a directory: No such file or directory

not sure what to do but could some1 help me out!!

---

### Post by adamJ5 on 2007-02-21
I got it working thanks to this great tut, but the game runs REALLY slow. I'm getting 1 fps at the startup-screen, with Gran Turismo 2. 

Any help?

---

### Post by dfreer on 2007-02-26
> I got it working thanks to this great tut, but the game runs REALLY slow. I'm getting 1 fps at the startup-screen, with Gran Turismo 2.

Any help?

Either you have the graphics set REALLY high in ePSXe (I think there is an "Fast but low Quality" Setting in the video config), or most likely you don't have your video card driver properly installed. To find out, type this into terminal:

```
glxinfo | head
```

If it says "Direct Rendering = No" your graphics card driver is not installed correctly.

---

### Post by dfreer on 2007-03-07
BTW, on an x86_64 Ubuntu Edgy install (with Nvidia drivers installed correctly) I was also having problems getting ePSXe to run right. Try pSX, it runs really well too and it just released a linux client (you might need to install 32-bit libraries, I'm going to put up a howto soon).

---

### Post by whitewolfshield on 2007-04-11
has anyone gotten a logitech dual action gamepad (looks exactly like a psx controller) to work on epsxe? Every time I go to configure it, I the d-pad is null; jscallibrate works perfectly, it's just the plugins that don't seem to work.

---

### Post by Dirtycash on 2007-04-21
Yes.  

I am using a Logitech Dual Action with success.

I am using ammoQ's padJoy Joy Device Driver 0.8 and after some configuration it works perfectly.

I don't think I had to do anything special besides that.

---

### Post by the_master on 2007-05-09
man this totally messed up my computer, i can't even log in now.  when i try to log in it says ```
"
User's %HOME/.dmrc file  is being ignored.  This prevents the default session and language from being saved file should be owned by user and have 644 permissions.  User's $HOME directory must be owned by user and not writeable by other users."
```

then when i hi ok(the only option) is says
```
Your session only lasted less than 10 seconds if you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disspace.  Try logging in with one of the failsafe sesions to see if you can fix this problem.
```

Then asks if i want to "View details (~/.xsession-errors file)"

---

### Post by jjaramillo on 2007-05-13
It worked pretty fine for me :P :
[[IMG]http://i65.photobucket.com/albums/h229/jjaram41/Geekorito/sotnUbuntu704screen01small.jpg[/IMG]]("http://i65.photobucket.com/albums/h229/jjaram41/Geekorito/sotnUbuntu704screen01.jpg")
Btw the joydpad also worked
PadJoy 0.82 + Psx2 Controller

---

### Post by jp01 on 2007-05-16
nice guide, im quite new to the who ubuntu experience and trying to get epsxe running, so far everything is working fine but whenever i try and load iso of a game it comes up with this message:
chmod: cannot access ` ': No such file or directory

any idea on wtf that is or how to work around that, sorry if a total noob question.

---

### Post by thehuman on 2007-05-20
Great guide. I could never get PCSX configured, but I prefer ePSXe anyway, and this made it so easy. Thanks.

---

### Post by RockTonic3 on 2007-06-04
everything was going well, till i actually put castlevania in and tried to start it up.  terminal did the following:

christopher@chris-voltaire:~$ epsxe
 * Running ePSXe emulator version 1.6.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/usr/local/games/epsxe/bios//scph1001.bin]. 
 * Init internal cdrom ... ok
 * First/Last track: 1 1
 * Track 1:  (DATA) - Start 0: (00,02,00) 
 * NTSC cdrom detected. 
 * Init gpu[0][libgpuPeteXGL2.so.2.0.8] 
Gdk-ERROR **: GLXUnsupportedPrivateRequest
  serial 36 error_code 161 request_code 142 minor_code 16


any idea what i'm doing wrong? problem with the video driver maybe?

---

### Post by zariuq on 2007-06-07
I have pretty much the same error except with slightly different numbers in the last line...

Gdk-ERROR **: GLXUnsupportedPrivateRequest
     serial 40 error_code 163 request_code 143 minor_code 16

eh, it works when I go to the other graphics plug-in... (time to try that other one ye linked to)

---

### Post by jdbausch on 2007-06-09
Don't know if anyone knows the answer, but...

I've got it all working, except that my game pad's direction buttons do not respond using either the omnijoy or padjoy plugins.

all other buttons work fine, and all buttons including direction work in the OS joystick calibrator.

the gamepad is branded dinogame, but shows up in the hardware information as a dragonrise inc generic gamepad.

if anyone has any input, please help!

---

### Post by jdbausch on 2007-06-10
> **jdbausch said:**
> Don't know if anyone knows the answer, but...

I've got it all working, except that my game pad's direction buttons do not respond using either the omnijoy or padjoy plugins.

all other buttons work fine, and all buttons including direction work in the OS joystick calibrator.

the gamepad is branded dinogame, but shows up in the hardware information as a dragonrise inc generic gamepad.

if anyone has any input, please help!

I was able to solve my own issue by using jscal to calibrate instead of jscalibrator

---

### Post by theovercoat on 2007-06-10
i am using epsxe 1.6 in feisty 32 bit.  thanks to the first page of this howto and previous experience with emulators in windows and linux i successfully configured and ran final fantasy 9.  everything looks great in higher res and shader model smoothing.  btw 7900gs for vga.  anyway, here is where i need help...  if anyone is usuing shader model effects for the xgl2 plugin what exactly does your custom shader dir line look like in your config?  i cant get my shader directory to be seen =[  

imo pc ratio and FBO are best options.  and just in case, dont use sal for ff 7-9

---

### Post by theovercoat on 2007-06-11
just in case...

those of you wanting to run epsxe primarily for square games should seriously consider 1.5.2 over 1.6  as 1.6 did indeed lock up during a disk 4 mdec but not in 1.5.2.  this has been mentioned before but it was worth saying again.

---

### Post by theovercoat on 2007-06-13
ANYONE HAVING SHADER TROUBLE IN LINUX!

here is the solution...

first, make sure you have a folder called, "shaders" in your epsxe dir. 
second, place both shader files in that dir (gpuPeteOGL2.slf, gpuPeteOGL2.slv for example)
third, open each of these files and make sure there is an **empty** line at the end.

here is a thread on one of petes forums relating to the topic...

[http://www.razyboard.com/system/morethread-shadersunderlinux-pete_bernert-266904-4528073-0.html](http://www.razyboard.com/system/morethread-shadersunderlinux-pete_bernert-266904-4528073-0.html)

---

### Post by TreeFinger on 2007-06-17
I do not have a card compatible with dx9. I am running a radeon 9200 LE. Whenever I try to load up a PSX cd I get the error, "Missing Shader Extensions!". Is there any way around this.. I really wanna play some final fantasy.

---

### Post by theovercoat on 2007-06-21
as long as your card supports sm 2.0 you can use the special shaders under petess xgl2 plugin, otherwise you should consider pete's mesa gl (sounds good for the 9200 le).  try disabling the "shader for psx  texture window" option and all other shader options.

---

### Post by mfolnovic on 2007-06-29
* Running ePSXe emulator version 1.5.2.
 * Memory handlers init.
 * ePSXe: PSX BIOS loaded [/usr/local/games/epsxe/bios//SCPH1001.bin].
 * Init internal cdrom ... ok
CD read toc header failed (25)
 * First/Last track: 0 1
 * Track 1: CD get track start failed (25)
 (AUDIO) - Start 0: (20,23,241)
CD(0,2,16) read ioctl failed (25)
CD(149,18,9) read ioctl failed (25)
CD(149,18,10) read ioctl failed (25)
 * NTSC cdrom detected.
 * Init gpu[0][libgpuPeopsSoftX.so.1.0.17]
 * Open gpu[0]
 * Init spu[0][libspuPeopsOSS.so.1.0.9]
Sound device not available!
                            * Open spu[0]
CD(0,2,16) read ioctl failed (25)
CD(0,2,0) read ioctl failed (25)

what should I do ?

---

### Post by Adam_GUI on 2007-07-05
> **gezzabob said:**
> Unable to get ePSXe working have followed th instructions on here but when I try to run ps game get an error plugins/libspu.so: cannot open shared object file: No such file or directory

here is what I get.
geoffl@geoffl-desktop:~$ epsxe
 * Running ePSXe emulator version 1.6.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/home/geoffl/Desktop/SCPH1001.BIN]. 
 * Init internal cdrom ... ok
CD read toc header failed (25)
 * First/Last track: 7 2
 * Track 1: CD get track start failed (25)
 (AUDIO) - Start 0: (00,00,00) 
 * Track 2: CD get track start failed (25)
 (AUDIO) - Start 1: (00,00,00) 
CD(0,2,16) read ioctl failed (25)
CD(226,55,35) read ioctl failed (25)
CD(226,55,36) read ioctl failed (25)
 * NTSC cdrom detected. 
 * Init gpu[0][libgpuPeopsSoftX.so.1.0.17] 
 * Open gpu[0] 
plugins/libspu.so: cannot open shared object file: No such file or directorygeoffl@geoffl-desktop:~$ 

Anybody help me out with this one I have searched for info on libspu.so but no avail.

I'm having this same problem.  I haven't seen it addressed yet.  Any docs out there that could help?
EDIT:
Renamed the spu plugin and now I get a blank fullscreen window.  :(

---

### Post by tenjadedragons on 2007-07-12
hi, someone already posted my problem up, the one that goes: ePSXe is nNOT completely configurated go to config->bios to configure it.  Then he said that it was all ok, it was just something to do with the permissions.

As a total noob, I have no idea what he was on about or how to put it right.  If someone could help me I would be very grateful, as my son is...a little eager to start playing.

---

### Post by crsd36 on 2007-07-15
I have followed the steps from the first post twice and am still getting the same error, when I try to load the ISO for FFXIII.  Any suggestions would be greatly appreciated!

>  * Running ePSXe emulator version 1.6.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/usr/local/games/epsxe/bios//SCPH1001.BIN]. 
 * Loading ISO Format [BIN/IMG2352] ok
 * NTSC cdrom detected. 
plugins/libgpu.so: cannot open shared object file: No such file or directory

---

### Post by le_vainqueur on 2007-07-24
Overall a good guide, but I had to do a little tweeking to get it to work right for me

1. The emulator zip file didn't seem to be accurate.  It did not insert any of the folders such as "cfg" or "plugins."  I downloaded it myself and manually extracted it to the given folder

2. In many of the commands that include "$/EPSXE/..." I had two problems
i. the folder I created was epsxe, and the command terminal recognized this difference.  All I had to do is adjust the directory
ii. The directory was never changed back to "/usr/local/games/epsxe" so I had to either change my directory, or include the full path in the command before following your directions.

I haven't configured it yet, but it started up fine.  Thanks for the guide!

---

### Post by matemargo on 2007-07-24
I have ePSXe working just fine.

The main problem I had was with the graphic plugin (because my ATI driver wasn't correctly installed).

A tip for using with fullscreen: In the graphic plugin configuration, besides marking "Fullscreen" checkbox you have to change the resolution (640x480 by default) to your actual screen resolution (mine is 1280x1024).

---

### Post by adammw on 2007-07-30
I installed everything really easily.. great howto!

One Problem though: **It doesn't work!**
I get this error: 
```
./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```

And i do have libgtk1.2 installed...
:confused:
P.S. I'm running Ubuntu 7.04 amd64 on Dell M12something or other

---

### Post by goonies on 2007-08-10
OK.  How do I do a clean uninstall of this?

---

### Post by Nevermore Burning on 2007-09-20
Problems with FF9- graphics, I think. Running Feisty on a adbent lappy, rns games okay on windows but with which plug-ins I can't remember.

Got 4 plugins-

Peops SoftSDl plugin- crashes epsxe when run with any game.

Error log:
```
 * Running ePSXe emulator version 1.6.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/usr/local/games/epsxe/bios/SCPH1001.BIN]. 
 * Loading ISO Format [BIN/IMG2352] ok
 * Force PAL cdrom detected. 
 * Init gpu[0][libgpuPeopsSDL.so.1.0.16] 
/usr/local/bin/epsxe: line 6:  9157 Segmentation fault      (core dumped) ./epsxe

```

Peops SoftX plugin- seems to run other games okay. Runs FF9 iso, gets to the "trainer" screen added by the .ppf makers, but when I try to load the game, it crashes-
```
 * Running ePSXe emulator version 1.6.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/usr/local/games/epsxe/bios/SCPH1001.BIN]. 
 * Loading ISO Format [BIN/IMG2352] ok
 * Force PAL cdrom detected. 
 * Init gpu[0][libgpuPeopsSoftX.so.1.0.17] 
 * Open gpu[0] 
 * Init spu[0][libspuPeopsOSS.so.1.0.9] 
 * Open spu[0] 
 * Init pad[0][libpadJoy-0.8.so] 
padJoy: trying to start a thread; if it hangs, you must disable multithreading
 * Open pad[0] 
 * Patching game ... ppf file v.2.0 done.
/usr/local/bin/epsxe: line 6:  9279 Segmentation fault      (core dumped) ./epsxe

```

Pete's MesaGL plugin-
runs all games, buggy, slow FPS rate. runs ff9, but buggy like rest of games.

Petles XGL plugin- logs me out of X. I see boot screen for a moment, then see graphical login prompt.

this-
```
glxinfo | head
```

does same thing so I suspect this is a problem with my vid card. I think i have integrated graphics, anyway.

All cfg files are defaults.

---

### Post by Nevermore Burning on 2007-10-01
Err.. I'm still having this problem. Should I take it elsewhere?

---

### Post by dynamethod on 2007-10-02
im only having trouble with padjoy installation everytime i try to compile it with make i get this:

make: gtk-config: Command not found
cc -fPIC -Wall -O2 -fomit-frame-pointer -D_REENTRANT  -DVERSION=0 -DBUILD=8   -c -o pad.o pad.c
make: gtk-config: Command not found
rm -f libpadJoy-0.8.so
gcc -shared -Wl,-soname,libpadJoy-0.8.so -fPIC -Wall -O2 -fomit-frame-pointer -D_REENTRANT  -DVERSION=0 -DBUILD=8 pad.o -o libpadJoy-0.8.so -lpthread
strip --strip-unneeded --strip-debug libpadJoy-0.8.so
make: gtk-config: Command not found
cc -fPIC -Wall -O2 -fomit-frame-pointer -D_REENTRANT  -DVERSION=0 -DBUILD=8   -c -o cfg.o cfg.c
cfg.c:36:21: error: gdk/gdk.h: No such file or directory
cfg.c:37:21: error: gtk/gtk.h: No such file or directory
cfg.c: In function ‘getPendingEvents’:
cfg.c:172: error: ‘GdkEvent’ undeclared (first use in this function)
cfg.c:172: error: (Each undeclared identifier is reported only once
cfg.c:172: error: for each function it appears in.)
cfg.c:172: error: ‘ge’ undeclared (first use in this function)
cfg.c:308: warning: implicit declaration of function ‘gdk_event_get’
cfg.c:309: error: ‘GDK_KEY_PRESS’ undeclared (first use in this function)
cfg.c:312: error: ‘GdkEventKey’ undeclared (first use in this function)
cfg.c:312: error: expected expression before ‘)’ token
cfg.c:317: error: ‘GDK_KEY_RELEASE’ undeclared (first use in this function)
cfg.c:320: error: expected expression before ‘)’ token
cfg.c:325: warning: implicit declaration of function ‘gdk_event_free’
cfg.c: At top level:
cfg.c:779: error: expected specifier-qualifier-list before ‘GtkWidget’
cfg.c: In function ‘showPadConfiguration’:
cfg.c:833: warning: implicit declaration of function ‘gtk_entry_set_text’
cfg.c:833: warning: implicit declaration of function ‘GTK_ENTRY’
cfg.c:833: error: ‘struct <anonymous>’ has no member named ‘filename_entry’
cfg.c:836: warning: implicit declaration of function ‘gtk_label_set’
cfg.c:836: warning: implicit declaration of function ‘GTK_LABEL’
cfg.c:836: error: ‘struct <anonymous>’ has no member named ‘label’
cfg.c:840: error: ‘struct <anonymous>’ has no member named ‘macro_label’
cfg.c: In function ‘OnConfCancel’:
cfg.c:846: warning: implicit declaration of function ‘gtk_widget_hide’
cfg.c:846: error: ‘struct <anonymous>’ has no member named ‘config_window’
cfg.c:847: warning: implicit declaration of function ‘gtk_widget_destroy’
cfg.c:847: error: ‘struct <anonymous>’ has no member named ‘config_window’
cfg.c:848: warning: implicit declaration of function ‘gtk_main_quit’
cfg.c: In function ‘OnConfOk’:
cfg.c:853: error: ‘struct <anonymous>’ has no member named ‘config_window’
cfg.c:854: error: ‘struct <anonymous>’ has no member named ‘config_window’
cfg.c: At top level:
cfg.c:858: error: expected ‘)’ before ‘*’ token
cfg.c:949: error: expected ‘)’ before ‘*’ token
cfg.c:1016: error: expected ‘)’ before ‘*’ token
cfg.c:1086: error: expected ‘)’ before ‘*’ token
cfg.c:1090: error: expected ‘)’ before ‘*’ token
cfg.c:1094: error: expected ‘)’ before ‘*’ token
cfg.c:1098: error: expected ‘)’ before ‘*’ token
cfg.c:1102: error: expected ‘)’ before ‘*’ token
cfg.c:1113: error: expected ‘)’ before ‘*’ token
cfg.c: In function ‘CreateConfigWindow’:
cfg.c:1120: error: ‘GtkWidget’ undeclared (first use in this function)
cfg.c:1120: error: ‘hbox’ undeclared (first use in this function)
cfg.c:1121: error: ‘fixed’ undeclared (first use in this function)
cfg.c:1123: error: ‘struct <anonymous>’ has no member named ‘config_window’
cfg.c:1123: warning: implicit declaration of function ‘gtk_window_new’
cfg.c:1123: error: ‘GTK_WINDOW_DIALOG’ undeclared (first use in this function)
cfg.c:1124: warning: implicit declaration of function ‘gtk_widget_set_usize’
cfg.c:1124: error: ‘struct <anonymous>’ has no member named ‘config_window’
cfg.c:1125: warning: implicit declaration of function ‘gtk_window_set_title’
cfg.c:1125: warning: implicit declaration of function ‘GTK_WINDOW’
cfg.c:1125: error: ‘struct <anonymous>’ has no member named ‘config_window’
cfg.c:1126: warning: implicit declaration of function ‘gtk_window_set_position’
cfg.c:1126: error: ‘struct <anonymous>’ has no member named ‘config_window’
cfg.c:1126: error: ‘GTK_WIN_POS_CENTER’ undeclared (first use in this function)
cfg.c:1127: warning: implicit declaration of function ‘gtk_container_set_border_width’
cfg.c:1127: warning: implicit declaration of function ‘GTK_CONTAINER’
cfg.c:1127: error: ‘struct <anonymous>’ has no member named ‘config_window’
cfg.c:1128: warning: implicit declaration of function ‘gtk_signal_connect’
cfg.c:1128: warning: implicit declaration of function ‘GTK_OBJECT’
cfg.c:1128: error: ‘struct <anonymous>’ has no member named ‘config_window’
cfg.c:1128: warning: implicit declaration of function ‘GTK_SIGNAL_FUNC’
cfg.c:1130: warning: implicit declaration of function ‘gtk_fixed_new’
cfg.c:1131: warning: implicit declaration of function ‘gtk_container_add’
cfg.c:1131: error: ‘struct <anonymous>’ has no member named ‘config_window’
cfg.c:1133: warning: implicit declaration of function ‘gtk_hbox_new’
cfg.c:1133: error: ‘FALSE’ undeclared (first use in this function)
cfg.c:1134: warning: implicit declaration of function ‘gtk_fixed_put’
cfg.c:1134: warning: implicit declaration of function ‘GTK_FIXED’
cfg.c:1135: warning: implicit declaration of function ‘gtk_box_pack_start’
cfg.c:1135: warning: implicit declaration of function ‘GTK_BOX’
cfg.c:1135: warning: implicit declaration of function ‘gtk_label_new’
cfg.c:1135: error: ‘TRUE’ undeclared (first use in this function)
cfg.c:1137: error: ‘struct <anonymous>’ has no member named ‘padnogroup’
cfg.c:1141: error: ‘struct <anonymous>’ has no member named ‘padno_radio’
cfg.c:1141: warning: implicit declaration of function ‘gtk_radio_button_new_with_label’
cfg.c:1141: error: ‘struct <anonymous>’ has no member named ‘padnogroup’
cfg.c:1142: error: ‘struct <anonymous>’ has no member named ‘padno_radio’
cfg.c:1143: error: ‘struct <anonymous>’ has no member named ‘padnogroup’
cfg.c:1143: warning: implicit declaration of function ‘gtk_radio_button_group’
cfg.c:1143: warning: implicit declaration of function ‘GTK_RADIO_BUTTON’
cfg.c:1143: error: ‘struct <anonymous>’ has no member named ‘padno_radio’
cfg.c:1144: error: ‘struct <anonymous>’ has no member named ‘padno_radio’
cfg.c:1144: error: ‘OnPadnoRadio’ undeclared (first use in this function)
cfg.c:1149: error: ‘struct <anonymous>’ has no member named ‘pcsxgroup’
cfg.c:1150: error: ‘struct <anonymous>’ has no member named ‘pcsx_radio’
cfg.c:1150: error: ‘struct <anonymous>’ has no member named ‘pcsxgroup’
cfg.c:1151: error: ‘struct <anonymous>’ has no member named ‘pcsx_radio’
cfg.c:1152: error: ‘struct <anonymous>’ has no member named ‘pcsxgroup’
cfg.c:1152: error: ‘struct <anonymous>’ has no member named ‘pcsx_radio’
cfg.c:1153: error: ‘struct <anonymous>’ has no member named ‘pcsx_radio’
cfg.c:1153: error: ‘OnPcsxRadio’ undeclared (first use in this function)
cfg.c:1154: warning: implicit declaration of function ‘gtk_toggle_button_set_active’
cfg.c:1154: warning: implicit declaration of function ‘GTK_TOGGLE_BUTTON’
cfg.c:1154: error: ‘struct <anonymous>’ has no member named ‘pcsx_radio’
cfg.c:1155: error: ‘struct <anonymous>’ has no member named ‘epsxe_radio’
cfg.c:1155: error: ‘struct <anonymous>’ has no member named ‘pcsxgroup’
cfg.c:1156: error: ‘struct <anonymous>’ has no member named ‘epsxe_radio’
cfg.c:1157: error: ‘struct <anonymous>’ has no member named ‘pcsxgroup’
cfg.c:1157: error: ‘struct <anonymous>’ has no member named ‘epsxe_radio’
cfg.c:1158: error: ‘struct <anonymous>’ has no member named ‘epsxe_radio’
cfg.c:1158: error: ‘OnEpsxeRadio’ undeclared (first use in this function)
cfg.c:1159: error: ‘struct <anonymous>’ has no member named ‘epsxe_radio’
cfg.c:1164: error: ‘struct <anonymous>’ has no member named ‘filename_entry’
cfg.c:1164: warning: implicit declaration of function ‘gtk_entry_new’
cfg.c:1165: error: ‘struct <anonymous>’ has no member named ‘filename_entry’
cfg.c:1165: error: ‘gchar’ undeclared (first use in this function)
cfg.c:1165: error: expected expression before ‘)’ token
cfg.c:1166: warning: implicit declaration of function ‘gtk_entry_set_max_length’
cfg.c:1166: error: ‘struct <anonymous>’ has no member named ‘filename_entry’
cfg.c:1167: error: ‘struct <anonymous>’ has no member named ‘filename_entry’
cfg.c:1168: error: ‘struct <anonymous>’ has no member named ‘filename_entry’
cfg.c:1168: error: ‘OnFilenameEntry’ undeclared (first use in this function)
cfg.c:1171: error: ‘struct <anonymous>’ has no member named ‘thread_check’
cfg.c:1171: warning: implicit declaration of function ‘gtk_check_button_new_with_label’
cfg.c:1172: error: ‘struct <anonymous>’ has no member named ‘thread_check’
cfg.c:1173: error: ‘struct <anonymous>’ has no member named ‘thread_check’
cfg.c:1173: error: ‘OnThreadCheck’ undeclared (first use in this function)
cfg.c:1174: error: ‘struct <anonymous>’ has no member named ‘thread_check’
cfg.c:1177: error: ‘struct <anonymous>’ has no member named ‘analog_check’
cfg.c:1178: error: ‘struct <anonymous>’ has no member named ‘analog_check’
cfg.c:1179: error: ‘struct <anonymous>’ has no member named ‘analog_check’
cfg.c:1179: error: ‘OnAnalogCheck’ undeclared (first use in this function)
cfg.c:1180: error: ‘struct <anonymous>’ has no member named ‘analog_check’
cfg.c:1185: error: ‘struct <anonymous>’ has no member named ‘button’
cfg.c:1185: warning: implicit declaration of function ‘gtk_button_new_with_label’
cfg.c:1186: error: ‘struct <anonymous>’ has no member named ‘button’
cfg.c:1188: warning: implicit declaration of function ‘gtk_object_set_user_data’
cfg.c:1188: error: ‘struct <anonymous>’ has no member named ‘button’
cfg.c:1189: error: ‘struct <anonymous>’ has no member named ‘button’
cfg.c:1189: error: ‘OnConfBtn’ undeclared (first use in this function)
cfg.c:1190: error: ‘struct <anonymous>’ has no member named ‘label’
cfg.c:1191: error: ‘struct <anonymous>’ has no member named ‘label’
cfg.c:1199: error: ‘struct <anonymous>’ has no member named ‘macro_button’
cfg.c:1200: error: ‘struct <anonymous>’ has no member named ‘macro_button’
cfg.c:1201: error: ‘struct <anonymous>’ has no member named ‘macro_button’
cfg.c:1202: error: ‘struct <anonymous>’ has no member named ‘macro_button’
cfg.c:1202: error: ‘OnMacroBtn’ undeclared (first use in this function)
cfg.c:1203: error: ‘struct <anonymous>’ has no member named ‘macro_label’
cfg.c:1204: error: ‘struct <anonymous>’ has no member named ‘macro_label’
cfg.c:1205: error: ‘struct <anonymous>’ has no member named ‘macro_def_button’
cfg.c:1206: error: ‘struct <anonymous>’ has no member named ‘macro_def_button’
cfg.c:1207: error: ‘struct <anonymous>’ has no member named ‘macro_def_button’
cfg.c:1208: error: ‘struct <anonymous>’ has no member named ‘macro_def_button’
cfg.c:1208: error: ‘OnMacroDefineBtn’ undeclared (first use in this function)
cfg.c:1216: error: ‘struct <anonymous>’ has no member named ‘ok_button’
cfg.c:1217: error: ‘struct <anonymous>’ has no member named ‘ok_button’
cfg.c:1218: error: ‘struct <anonymous>’ has no member named ‘ok_button’
cfg.c:1219: warning: implicit declaration of function ‘GTK_WIDGET_SET_FLAGS’
cfg.c:1219: error: ‘struct <anonymous>’ has no member named ‘ok_button’
cfg.c:1219: error: ‘GTK_CAN_DEFAULT’ undeclared (first use in this function)
cfg.c:1221: error: ‘struct <anonymous>’ has no member named ‘cancel_button’
cfg.c:1222: error: ‘struct <anonymous>’ has no member named ‘cancel_button’
cfg.c:1223: error: ‘struct <anonymous>’ has no member named ‘cancel_button’
cfg.c:1224: error: ‘struct <anonymous>’ has no member named ‘cancel_button’
cfg.c: In function ‘PADconfigure’:
cfg.c:1232: warning: implicit declaration of function ‘gtk_widget_show_all’
cfg.c:1232: error: ‘struct <anonymous>’ has no member named ‘config_window’
cfg.c:1234: warning: implicit declaration of function ‘gtk_main’
cfg.c: At top level:
cfg.c:1244: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cfg.c: In function ‘OnAboutOk’:
cfg.c:1247: error: ‘AboutDlg’ undeclared (first use in this function)
cfg.c: In function ‘PADabout’:
cfg.c:1253: error: ‘GtkWidget’ undeclared (first use in this function)
cfg.c:1253: error: ‘Label’ undeclared (first use in this function)
cfg.c:1254: error: ‘Ok’ undeclared (first use in this function)
cfg.c:1255: error: ‘Box’ undeclared (first use in this function)
cfg.c:1255: error: ‘BBox’ undeclared (first use in this function)
cfg.c:1255: warning: left-hand operand of comma expression has no effect
cfg.c:1260: error: ‘AboutDlg’ undeclared (first use in this function)
cfg.c:1260: error: ‘GTK_WINDOW_DIALOG’ undeclared (first use in this function)
cfg.c:1263: error: ‘GTK_WIN_POS_CENTER’ undeclared (first use in this function)
cfg.c:1266: warning: implicit declaration of function ‘gtk_vbox_new’
cfg.c:1268: warning: implicit declaration of function ‘gtk_widget_show’
cfg.c:1271: error: ‘FALSE’ undeclared (first use in this function)
cfg.c:1274: warning: implicit declaration of function ‘gtk_hbutton_box_new’
cfg.c:1281: error: ‘GTK_CAN_DEFAULT’ undeclared (first use in this function)
cfg.c: In function ‘main’:
cfg.c:1294: warning: implicit declaration of function ‘gtk_set_locale’
cfg.c:1295: warning: implicit declaration of function ‘gtk_init’
cfg.c:1304: warning: implicit declaration of function ‘gtk_exit’
make: *** [cfg.o] Error 1


i tried searching for a package called gtk-devel in synaptic but couldnt find it though :S

---

### Post by Innomen on 2007-10-14
This may be sort of off topic but this thread is a grand example.

Obviously you gentlemen know what you are doing, particularly the original author. My question/suggestion as a new user is this. Why not write a downloadable batch file or write an installer of some sort?

I think this ethic needs to be applied aross the board. Why force everyone to walk up hill both ways in the snow just because you had to? 

Isn't the point of ubuntu at its core doing work so the group (humanity) doesn't have to?

"linux for people" and all that would seem to fundamentally suggest a "we know so you don't have to" kind of feel. And as reprehensible and hard to imagine as it may be for some, not everyone has either the inclination or time to devote to learning the system and its guts.

Some people want it to "Just work" :) The goal should be that over time this OS gets easier to use, not just well documented.

*hops off soap box*

P.S.

I wanna play symphony of the night. :)

---

### Post by mekura on 2007-10-18
After upgrading from Feisty Fawn (7.04) to Gutsy Gibbon (7.10) via the update manager, opening ePSXe doesn't seem to do anything (the terminal ignores the command). Was a file deleted in the upgrade process, perhaps something I could quickly replace? I reinstalled ePSXE in desperate hopes that something went missing in the folder, but that ePSXe still doesn't respond. (If only it gave an error of some sort! I don't know whether it's libgtk, or hardware drivers, or ...)

More importantly, am I the only one affected by the upgrade? If not, I'll post a fix this weekend if I find one.

Otherwise, it's back to 7.04 for me. :(

---

### Post by Kevin92 on 2007-10-19
I'm having the same problem after upgrading.  I'm hoping someone comes up with a fix soon though.

---

### Post by mekura on 2007-10-19
I booted into the previous kernel using the GRUB loader, and was able to run ePSXe. The padjoy plugin was dysfunctional, and I had to set the graphics to the bare minimum in order to get any response. Therefore, I'm discounting that method as a possible quick fix.

---

### Post by @vijay@ on 2007-10-19
epsxe is not running in gutsy ....
i did a fresh insall of gutsy and tried to run epsxe but the terminal just dont do anything no error messages nothing and nothing is started....... the terminal just accepts the command

it used to work flawless in feisty

---

### Post by Hairy_Palms on 2007-10-21
> epsxe is not running in gutsy ....
i did a fresh insall of gutsy and tried to run epsxe but the terminal just dont do anything no error messages nothing and nothing is started....... the terminal just accepts the command

it used to work flawless in feisty

+1

---

### Post by matemargo on 2007-10-21
**@vijay@**: I'm having the same problem

---

### Post by @vijay@ on 2007-10-21
i got epsxe working but not completely :(
look my posting here

[http://ubuntuforums.org/showthread.php?p=3595768#post3595768](http://ubuntuforums.org/showthread.php?p=3595768#post3595768)

---

### Post by vlo on 2007-10-22
This seems to be related to the 2.6.22 kernel, since it is the one in Gutsy, and since you @vijay@ got it (partially) working by upgrading your kernel.

Also I found this thread, by a OpenSUSE 10.3 user who is experiencing the same problem. Guess what kernel version OpenSUSE 10.3 runs - 2.6.22!

[http://forums.ngemu.com/generic-epsxe-queries/94458-epsxe-opensuse-10-3-a.html](http://forums.ngemu.com/generic-epsxe-queries/94458-epsxe-opensuse-10-3-a.html)

[http://www.suseforums.net/index.php?showtopic=39362&pid=201520&st=0&#entry201520](http://www.suseforums.net/index.php?showtopic=39362&pid=201520&st=0&#entry201520)

At least, this is my theory.

---

### Post by s14sx on 2007-10-23
where do you guys get all the game images from??

---

### Post by alcatraz678 on 2007-10-24
> **@vijay@ said:**
> epsxe is not running in gutsy ....
i did a fresh insall of gutsy and tried to run epsxe but the terminal just dont do anything no error messages nothing and nothing is started....... the terminal just accepts the command

it used to work flawless in feisty

+2

---

### Post by mekura on 2007-10-24
> **s14sx said:**
> where do you guys get all the game images from??

Officially,  you make private backups from games you already own.

You can also find games on the internet, but if you don't own the originals, downloading them is piracy.

---

### Post by alcatraz678 on 2007-10-26
Any fix yet for the problem of Gutsy users?

---

### Post by vlo on 2007-10-26
> **alcatraz678 said:**
> Any fix yet for the problem of Gutsy users?

I wish I knew one. The only ones I can think of is going through the hassle of upgrading/downgrading your kernel manually or switching to  a distro with a different kernel. (Sabayon Linux PE 1.1 and Fedora 8 are running kernel 2.6.23)

I miss ePSXe, it's like an old friend of mine. Despite it's speed problems and difficult configuration, I liked it. Running pSX on my HDTV just isn't the same as running ePSXe in highres and with texture filtering.

---

### Post by Felson on 2007-10-26
More info on the gutsy ePSXe problem.
ePSXe is NOT staticly linked, it is compresses useing "upx"
if you install the upx package from the repositories, you can run
```

cp epsxe epsxe_bak
upx -d epsxe

```
an you will get the "real" executable.
now, if you run ldd the un-compressed file, you get
```

:-> ldd epsxe
        linux-gate.so.1 =>  (0xffffe000)
        libncurses.so.5 => /lib32/libncurses.so.5 (0xf7eb1000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7ead000)
        libXt.so.6 => /usr/lib32/libXt.so.6 (0xf7e5b000)
        libz.so.1 => /usr/lib32/libz.so.1 (0xf7e46000)
        libgtk-1.2.so.0 => not found
        libgdk-1.2.so.0 => not found
        libgmodule-1.2.so.0 => not found
        libglib-1.2.so.0 => not found
        libXi.so.6 => /usr/lib32/libXi.so.6 (0xf7e3d000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7e2f000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7d3e000)
        libm.so.6 => /lib32/libm.so.6 (0xf7d19000)
        libc.so.6 => /lib32/libc.so.6 (0xf7bcf000)
        /lib/ld-linux.so.2 (0xf7f0c000)
        libSM.so.6 => /usr/lib32/libSM.so.6 (0xf7bc6000)
        libICE.so.6 => /usr/lib32/libICE.so.6 (0xf7bae000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7bab000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf7ba6000)

```
Now I thought that the ia32-libs had the gtk stuff in it, but it doesn't.
I haven't yet tried getting/extracting the i386 debs yet, but I am going to give that a shot. I searched through the libs, and didn't find a package that has the 32bit libs for those, if someone knows which lib it is, if there is one, please let me know.

---

### Post by Felson on 2007-10-26
WORKED!!!!
Well, I think it did anyway. epsxe loads, but I haven't run any games yet, because I am still at work....

The key things are:
1) It can't be run compressed. Some bug?? My guess, is 32bit compressed app on 64 bit OS.
2) You need the missing libs.

Anywho, here is a quick "how-to". As stated in the last post, If you know which lib these "should" be in in the Ubuntu 64bit distro, please let me know.

```

sudo aptitude install upx-ucl-beta
cd /path/to/epsxe
cp epsxe epsxe_bak
upx -d epsxe

```

It seems that some people have the libs already, so if you do, you don't need to do the second part. To check if you need the libs, us ldd.
```

ldd epsxe

```

If you see missing libs, keep reading, if not, you are done.

```

cd ~
mkdir tmp_libs
cd tmp_libs
wget http://mirrors.kernel.org/ubuntu/pool/universe/g/gtk+1.2/libgtk1.2_1.2.10-18_i386.deb
wget http://mirrors.kernel.org/ubuntu/pool/universe/g/glib1.2/libglib1.2_1.2.10-17build1_i386.deb
sudo dpkg -x libgtk1.2_1.2.10-18_i386.deb .
sudo dpkg -x libglib1.2_1.2.10-17build1_i386.deb .
cd usr/lib/

```

if you don't have a "/usr/lib32" dir run, else skip aptitude, and read on to the next block
```

sudo  aptitude install ia32-libs

```

```

sudo cp * /usr/lib32/
cd ../../../
sudo rm -rf tmp_libs

```

---

### Post by dfreer on 2007-10-26
> **Felson said:**
> 
```

:-> ldd epsxe
        linux-gate.so.1 =>  (0xffffe000)
        libncurses.so.5 => /lib32/libncurses.so.5 (0xf7eb1000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7ead000)
        libXt.so.6 => /usr/lib32/libXt.so.6 (0xf7e5b000)
        libz.so.1 => /usr/lib32/libz.so.1 (0xf7e46000)
[B]        libgtk-1.2.so.0 => not found
        libgdk-1.2.so.0 => not found
        libgmodule-1.2.so.0 => not found
        libglib-1.2.so.0 => not found
[/B]        libXi.so.6 => /usr/lib32/libXi.so.6 (0xf7e3d000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7e2f000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7d3e000)
        libm.so.6 => /lib32/libm.so.6 (0xf7d19000)
        libc.so.6 => /lib32/libc.so.6 (0xf7bcf000)
        /lib/ld-linux.so.2 (0xf7f0c000)
        libSM.so.6 => /usr/lib32/libSM.so.6 (0xf7bc6000)
        libICE.so.6 => /usr/lib32/libICE.so.6 (0xf7bae000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7bab000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf7ba6000)

```


Newer versions of these 32-bit libraries (specifically libgtk2.0-0 and libglib2.0) have been repackaged in the AMD64 package **ia32-libs**, available in the universe repository as seen here: [http://packages.ubuntu.com/gutsy/libs/ia32-libs](http://packages.ubuntu.com/gutsy/libs/ia32-libs)

AFAIK, they never repackaged the older version 1.2 libraries. In older versions of ubuntu like Dapper, ia32-libs and ia32-libs-gtk are separate packages btw. And ia32-libs-gtk only has libgtk2.0 and libglib2.0, as seen here:
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=ia32-libs-gtk&version=dapper&arch=amd64&page=2&number=50](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=ia32-libs-gtk&version=dapper&arch=amd64&page=2&number=50)

---

### Post by mekura on 2007-10-26
> **Felson said:**
> More info on the gutsy ePSXe problem.
ePSXe is NOT statically linked, it is compressed using "upx"
if you install the upx package from the repositories, you can run
```

cp epsxe epsxe_bak
upx -d epsxe

```
and you will get the "real" executable.

Installing the 'upx-ucl' package through Synaptic and running the above code from within the ePSXe folder worked perfectly for me - Wipeout and Gran Turismo 2 are all I've tested so far.

BONUS: the "Run > Continue" menu option now works for me, instead of segfaulting like in Feisty.

Great news to find on a Friday! Thanks, Felson!

---

### Post by timbobsteve on 2007-10-26
Hi All,

I downloaded the epsxe binaries and used the guide from the OP, the only modification was to use upx to extract the binary. Everything now works fine on my gutsy system!

-Timbobsteve

---

### Post by vlo on 2007-10-27
upx -d epsxe

Solved everything :D

---

### Post by dfreer on 2007-10-27
Looks like a good catch, Felson. How did you know to use that upx program to extract it?

---

### Post by @vijay@ on 2007-10-27
i have done 
udx -d epsxe 
----------------------------------
vijay@vijay-desktop:~/Desktop/ePSXe$ upx -d epsxe
                       Ultimate Packer for eXecutables
  Copyright (C) 1996,1997,1998,1999,2000,2001,2002,2003,2004,2005,2006,2007
UPX 3.00        Markus Oberhumer, Laszlo Molnar & John Reiser   Apr 27th 2007

        File size         Ratio      Format      Name
   --------------------   ------   -----------   -----------
    657368 <-    149019   22.67%    linux/386    epsxe

Unpacked 1 file.
----------------------------------------------
but still no fonts in the application

and here is my out put of         ldd ./epsxe
---------------------------------------
vijay@vijay-desktop:~/Desktop/ePSXe$ ldd ./epsxe
        linux-gate.so.1 =>  (0xffffe000)
        libncurses.so.5 => /lib/libncurses.so.5 (0xb7f58000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7f54000)
        libXt.so.6 => /usr/lib/libXt.so.6 (0xb7f02000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7eed000)
        libgtk-1.2.so.0 => /usr/lib/libgtk-1.2.so.0 (0xb7db2000)
        libgdk-1.2.so.0 => /usr/lib/libgdk-1.2.so.0 (0xb7d7c000)
        libgmodule-1.2.so.0 => /usr/lib/libgmodule-1.2.so.0 (0xb7d79000)
        libglib-1.2.so.0 => /usr/lib/libglib-1.2.so.0 (0xb7d53000)
        libXi.so.6 => /usr/lib/libXi.so.6 (0xb7d4b000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7d3c000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7c4b000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7c26000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7adc000)
        /lib/ld-linux.so.2 (0xb7fad000)
        libSM.so.6 => /usr/lib/libSM.so.6 (0xb7ad4000)
        libICE.so.6 => /usr/lib/libICE.so.6 (0xb7abc000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7ab8000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7ab3000)
------------------------------------------------
it looks like every dependencies are installed ,... whr is the problem???

---

### Post by Rinzwind on 2007-10-27
I followed this guide but when I type
epsxe
the command prompt just returns :(
No notice whatsoever.

AFAICT I checked all the settings and did it perfectly 

Any idea? :(

edit: it seems this is a +6 :D
sorry missed the 2nd page. Same problem as many others ... Gutsy.

Felson: your code words.

2 things:
1. the dpkg need a location to extract to. Added a ' .' at the end of both lines.
2. /usr/lib32/ does not exist. I used /usr/lib :)

---

### Post by dfreer on 2007-10-27
> **Rinzwind said:**
> 
2 things:
1. the dpkg need a location to extract to. Added a ' .' at the end of both lines.
2. /usr/lib32/ does not exist. I used /usr/lib :)

Ummm.... that isn't the greatest idea. Those are 32-bit libraries, and really don't belong in /usr/lib/. It may not cause you any problems right now, but it just isn't the proper solution (it's exactly what --force-architecture would've done). If you ever install the 64-bit versions of libgtk1.2 and libglib1.2, they will either overwrite the existing 32-bit libs, or won't install due to the existing files.

You can install ia32-libs, and that will install a majority of 32-bit libs in /usr/lib32/, both creating the directory for you and then running ldconfig properly. From the man page:
> ldconfig  creates,  updates,  and removes the necessary links and cache
       (for use by the run-time linker,  ld.so)  to  the  most  recent  shared
       libraries  found  in  the directories specified on the command line, in
       the file /etc/ld.so.conf, and in the trusted directories (/usr/lib  and
       /lib).

---

### Post by Felson on 2007-10-27
@dfreer
In a way, you solved it... :) I read your forum post for zsnes [here]("http://ubuntuforums.org/showthread.php?t=588744"), and you had a thing in there about prelink and execstack. I figured, what the heck, couldn't hurt to try it with ePSXe. execstack returned an error that it was a upx compressed executable. So I looked into that, and it solved my issues.

@Rinzwind
1) ya, read dfreer's reply, not a really good idea. I suggest installing some of the other 32bit libs anyway, and that will give you your lib32 directory. 
2) Thanks, I will fix that right after I finish this post.

---

### Post by dfreer on 2007-10-27
> **Felson said:**
> @dfreer
I a way, you solved it... :) I read your forum post for zsnes [here]("http://ubuntuforums.org/showthread.php?t=588744"), and you had a thing in there about prelink and execstack. I figured, what the heck, couldn't hurt to try it with ePSXe. execstack returned an error that it was a upx compressed executable. So I looked into that, and it solved my issues.

ROFL... wow :D

EDIT: BTW, for anyone who wants them... AMD64 .debs of lib32gtk1.2 and lib32glib1.2 are now available in my gutsy repository, or here if you just want the files:
[http://packages.dfreer.org/pool/gutsy/main/binary-amd64/lib32/](http://packages.dfreer.org/pool/gutsy/main/binary-amd64/lib32/)
Should help with the ePSXe installations ;)

---

### Post by snkmad on 2007-11-06
I need the following libs:
```
libgtk-1.2.so.0 => not found
libgdk-1.2.so.0 => not found
libgmodule-1.2.so.0 => not found
libglib-1.2.so.0 => not found

```
How do i get them all at once?

---

### Post by Felson on 2007-11-06
@dfreer
Sweet! Thanks! You rock.

@snkmad
See the post just before yours.... Add his repositories, and install the 2 he just listed from it. As for all at once, those 2 repositories are the closest yuo are going to get.

---

### Post by snkmad on 2007-11-06
Thanks, i didnt understand his post before. Now i get no missing libs!

---

### Post by dfreer on 2007-11-06
Does anyone know if there is a way to use a controller plugin with ePSXe, instead of the built-in one? Or, if that's not possible, is there anything special I need to do to get it to accept keypresses from my USB controller (logitech dual action, works perfectly in zsnes, pSX, PCSX, and other emulators)? I know it's located at /dev/input/js0, perhaps it's ePSXe is looking in a different location?

EDIT: Reading through this thread a little more carefully, it appears like it's definitely possible to use this controller, with a controller plugin like omnijoy or padjoy. The only issue is that ePSXe doesn't appear to let me choose which plugin to use, by default it uses the builtin plugin.

---

### Post by Felson on 2007-11-06
dfreer, just answered that in your amd64 thread. didn't know you were about to ask it here :) I literally must have been typing it as you were asking the question

---

### Post by snkmad on 2007-11-06
Im not getting sound. What should i do?
```
$ ./epsxe
 * Running ePSXe emulator version 1.6.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/home/snkmad/Downloads/epsxe160/bios/SCPH1001.BIN]. 
 * Init gpu[0][libgpuPeteXGL2.so.2.0.8] 
NVIDIA Corporation
GeForce 6150SE nForce 430/PCI/SSE2
 * Open gpu[0] 
 * Init spu[0][libspuPeopsOSS.so.1.0.8] 
Sound device not available!
 * Open spu[0] 

```

---

### Post by Felson on 2007-11-06
Do you have something else open that uses your sound card? If so, make sure that your doing "software mixing" in your Ubuntu sound configuration. Most sound cards don't do hardware mixing which means only 1 app can use it at a time without software mixing.

---

### Post by snkmad on 2007-11-06
No other program is open, only terminal.
Its set by default to do software mixing:
[[IMG]http://img225.imageshack.us/img225/6627/soundpreferencesyc2.th.png[/IMG]](http://img225.imageshack.us/my.php?image=soundpreferencesyc2.png)

EDIT: after i unchecked that, its working now.

---

### Post by Hartxenon on 2007-11-06
great tutorial mine works perfectly however i want  to add and external game pad plugin but i cant seem to add more plugins, i get an error that says ¨i do not have permission to write to this folder" I am going about it the copy paste/drag and drop method which is probably wrong, how do i remedy this situation??

---

### Post by .Ix on 2007-11-07
Followed all the steps in the OP and everything succeeded, but typing "epsxe" in the terminal doesn't work. nothing happens. there's no "unknown command" error. nothing at all happens even when i go to /usr/loca/games/epsxe and run epsxe from there. epsxe doesn't show up in the Processes tab in System Monitor either. 

using Pentium M 1.7ghz laptop with 1gb ram and intel Extreme Graphics 2, if that matters. thanks!

edit:

got it to work by upx -d epsxe, but it's very choppy.

---

### Post by KevNice on 2007-11-11
> **.Ix said:**
> Followed all the steps in the OP and everything succeeded, but typing "epsxe" in the terminal doesn't work. nothing happens. there's no "unknown command" error. nothing at all happens even when i go to /usr/loca/games/epsxe and run epsxe from there. epsxe doesn't show up in the Processes tab in System Monitor either. 

using Pentium M 1.7ghz laptop with 1gb ram and intel Extreme Graphics 2, if that matters. thanks!

edit:

got it to work by upx -d epsxe, but it's very choppy.


I have this same problem. Installed it but typing "epsxe" does nothing.

---

### Post by dfreer on 2007-11-11
I'm not entirely sure, but try this: change to the directory where epsxe is located, and then do the following:
```
upx -d ./epsxe
sudo chmod a+x ./epsxe
./epsxe
```

@Felson - If you can't get the OP of this thread to update with the newest method for installing ePSXe, you may want to consider making a new how-to to replace this one, considering the OP doesn't seem to watch this thread anymore:

> **johannes said:**
> I have now updated the guide slightly, mostly some formatting stuff and added a small troubleshooting section with what seems to be common problems. I don't really have the time to read trough all the 90 replies at this moment, but I might do that in the future.

Also, I migrated to Arch Linux a while ago and have not used Dapper much, and not at all epsxe with it... I still check this forum occationally though. But reading the latest replies here the guide seems to be working kind of all right except for the problems some people are having with the plugins. I have no idea how to solve most of them though... :-/

I don't know if /usr/local/games/epsxe is the most appropriate place anymore to install the app, maybe /usr/share/epsxe would conform better?

---

### Post by KevNice on 2007-11-13
> **dfreer said:**
> I'm not entirely sure, but try this: change to the directory where epsxe is located, and then do the following:

Tried it but this:

```
upx -d ./epsxe

```
 

doesnt seem to be a valid command?

---

### Post by .Ix on 2007-11-13
anyone got solutions for the choppiness though? i didn't even dare to use it with a game cause it was really slow with the bios. lol

epsxe works perfectly on this computer on windows with that Pete's plugin that doesn't use the videocard though.

---

### Post by dfreer on 2007-11-13
@KevNice - Did you install upx first? Also, make sure you are in the directory where epsxe is located.

---

### Post by Felson on 2007-11-13
@dfreer - ya, I was thinking of doing just that. I will put one together today. The last how-to I did took about 2 weeks to go live though, so could be a while before it's up.

Meantime, for those that are trying to get ePSXe to work, go[ here]("http://ubuntuforums.org/showthread.php?p=3639535#post3639535") will post this link again once he page flips.

Edit:
How-To posted, and waiting for moderation.

---

### Post by Felson on 2007-11-14
The new How-To is [here]("http://ubuntuforums.org/showthread.php?t=612021") Take a look and see if it's all good. :) There is no testing in Feisty, so if someone can double check that it works, that would be great.

---

### Post by dfreer on 2007-11-14
your link is bad felson, your missing the "h" in http ;)

---

### Post by Felson on 2007-11-14
:? oops. Thanks.

New How-To [here]("http://ubuntuforums.org/showthread.php?t=612021"). (Repost of page rollover)

---

### Post by JacksonDane on 2007-11-23
I'm getting black screens loading FFVII (Only game I've tried)

Terminal stops at "Open SPU" and it seems like nothing is happening after that. I've tried every configuration of every plugin it feels like.

Any ideas?

---

### Post by OvenMitt Bandit on 2007-11-26
I followed this guide exactly, and everything seemed to go alright. I got to the part where it said "just type epsxe to run", and nothing happened. Literally. Terminal shows nothing. I followed everything to the letter, what the heck?

---

### Post by dfreer on 2007-11-27
Did you uncompress the executable with upx, or try the newly updated guide provided by felson?

---

### Post by OvenMitt Bandit on 2007-11-30
I followed what the very first post said, which I assume is the "newly updated guide".

---

### Post by dfreer on 2007-12-01
It's not "newly updated", the OP doesn't seem to be around anymore. The problem seems to be that you have to uncompress the executable in gutsy first. For more information, just read the last couple pages of this thread, or follow the new guide created by Felson which is displayed right at the top of this page:
[http://ubuntuforums.org/showthread.php?t=612021](http://ubuntuforums.org/showthread.php?t=612021)

---

### Post by civilized on 2008-01-28
Hey guys I need a little help... Sorry if this has been solved I've been searching but couldn't find anything I installed epsxe loads up but when I start from CDROM I get an error

```

 * Running ePSXe emulator version 1.5.2.
 * Memory handlers init.
 * ePSXe: PSX BIOS loaded [/home/civilized/epsxe/bios/erase.me].
 * Init internal cdrom ... ok
 * First/Last track: 1 1
 * Track 1:  (DATA) - Start 0: (00,02,00)
 * NTSC cdrom detected.
 * Init gpu[0][libgpuPeteXGL2.so.2.0.8]
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
                                                         Error: couldn't get fbconfig
     Segmentation fault (core dumped)

```

any thoughts

---

### Post by Felson on 2008-01-28
Ya, You need a BIOS file.

---

### Post by civilized on 2008-01-28
i thought I had one... Can I download one from this thread??

---

### Post by Felson on 2008-01-28
> 
 * ePSXe: PSX BIOS loaded [/home/civilized/epsxe/bios/erase.me].

See my answer in the other epsxe thread about the BIOS. Should move this conversation there, as this thread is old and outdated.

---

### Post by adammw on 2008-01-29
Hi.
Although the emulator is Open Source, the BIOS is Sony "intellectual property" and therefore it is illegal to download. I think though, it is ok to dump the BIOS from a PlayStation you actually own, but even then, it's still painful. 
Considering the PlayStation is almost over a decade old, I don't think it matters much, because you can't even buy new PlayStation(s) if you wanted to. 
So just download them, do a google search on psx bios or SCPH1001 (also, the file name of the file you  want is SCPH1001.bin).
But that alone might not fix the problem, especially if it was a video graphics problem to start with....
:-\"
*Hope this Helps,*
**Adam**

---

### Post by GamingMazter on 2008-01-29
Thank You So Much! LOVE IT!

---

### Post by mercenaire on 2008-02-21
Hi everybody,

  I'm a french user so sorry if my english is not good.:lolflag:

I installed ePSXe according to the tutorial at the beginning of the topic. All is well configured (I know this software well because I used it before with windowsXP), the BIOS works well, but when I launch the ISO I have a black screen and absolutely nothing occurs then.

I try to launch FFVII with CD and The Legend of Dragoon with ISO.

I saw other people with this problem but I don't find the solution.

I have Ubuntu Gutsy Gibbon 7.10 32Bits, AMD64 Venux Core 3200+ (overclocked) Nvidia 7900 GTO with the last driver.

Thank You!

---

### Post by Felson on 2008-02-21
Hi 

This sounds like a problem that someone else is having. You should re-ask your question [here]("http://ubuntuforums.org/showthread.php?t=612021") at the replacement for this thread. This thread is a bit out of date.

---

### Post by humanizer on 2008-03-17
I don't know guys... IT's just NOT WORKING... 

I AM a BEGINNER, a NOOB if you will, but I did everything as posted, and still I cant make it work..

im on ubuntu 7.10 (gutsy)

---

### Post by Felson on 2008-03-17
Click the link in my last post, and use that How-To. This one is old, and out dated. If that one doesn't work for ya, post there and we will see what we can figure out.

---

### Post by wolffangalchemist on 2008-07-27
does this work on hardy 64 bit?

---

### Post by Felson on 2008-07-28
Switch to my how-to. This one is outdated.

---

### Post by strongfan on 2008-12-30
Hmm... I can't seem to configure any of the plugins!  I press the "configure" button, but no window pops up!  Also, it doesn't seem to be recognizing my USB Logitech Dual-Action controller...

---

### Post by Jake007g on 2010-07-05
Whenever I try loading "epsxe" it tells me it needs the shared libraries for libgtk-1.2.so.0, but whenever I try installing that, it tells me it cannot be found.

---

### Post by Senjey on 2010-09-09
I had the same problem.

./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

and when i want install the librarie...

sebastian@sebastian-desktop:~/Juegos/emulador_play$ sudo apt-get install unzip libgtk1.2-common libgtk1.2
 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
unzip ya está en su versión más reciente.
E: No se pudo encontrar el paquete libgtk1.2-common.
Anyone can share the librarie?

---

### Post by syred on 2010-11-10
bbbbbbbbbbbbbbbbbbbbbbb

---

### Post by syred on 2010-11-23
Here:

[URL="http://www.mediafire.com/?b5xl87kmqo06r88"]http://www.mediafire.com/?b5xl87kmqo06r88
[/URL] 
:o:o

---

### Post by joelstitch on 2010-12-03
> **syred said:**
> Here:

[URL="http://www.mediafire.com/?b5xl87kmqo06r88"]http://www.mediafire.com/?b5xl87kmqo06r88
[/URL] 
:o:o

I installed that file but I'm getting this error when I try to open it:

> ./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by muzikayise on 2010-12-08
> **Senjey said:**
> I had the same problem.

./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

and when i want install the librarie...

sebastian@sebastian-desktop:~/Juegos/emulador_play$ sudo apt-get install unzip libgtk1.2-common libgtk1.2
 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
unzip ya está en su versión más reciente.
E: No se pudo encontrar el paquete libgtk1.2-common.
Anyone can share the librarie?


i had the same problem but i fixed it by following this thread: [http://www.uluga.ubuntuforums.org/showthread.php?p=10212402#post10212402]("http://www.uluga.ubuntuforums.org/showthread.php?p=10212402#post10212402")

---

### Post by thecurseddevil on 2011-03-30
thanks dude

---

### Post by ewasdark on 2011-04-08
An error occurred, please help me

> .epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by dfreer on 2011-04-10
> **ewasdark said:**
> .epsxe: error while loading shared libraries: **libgtk-1.2.so.0**: cannot open shared object file: No such file or directory 

The file it is requesting belongs to the libgtk1.2 package, which only seems to be available for the Hardy and Jaunty releases. However, just looking at the contents of the package and I can see it just installs the library, so it should be just fine on any newer release. 

You can download the Hardy version here (for some reason the jaunty link on ubuntu packages seems to be broken temporarily):
[http://packages.ubuntu.com/hardy/libgtk1.2](http://packages.ubuntu.com/hardy/libgtk1.2)

Now, it should install just fine, but it might need some of those additional packages listed in that link to be installed along with it. I didn't bother to check to see if that's the case, or if those files will cause conflicts with your newer systems, but I don't think you need them. You can probably even get by just using dpkg force to force the libgtk1.2 package to install without those depenedecies, but your milage may very.

Hope this helps!

---

### Post by joelstitch on 2011-04-11
> **dfreer said:**
> The file it is requesting belongs to the libgtk1.2 package, which only seems to be available for the Hardy and Jaunty releases. However, just looking at the contents of the package and I can see it just installs the library, so it should be just fine on any newer release. 

You can download the Hardy version here (for some reason the jaunty link on ubuntu packages seems to be broken temporarily):
[http://packages.ubuntu.com/hardy/libgtk1.2](http://packages.ubuntu.com/hardy/libgtk1.2)

Now, it should install just fine, but it might need some of those additional packages listed in that link to be installed along with it. I didn't bother to check to see if that's the case, or if those files will cause conflicts with your newer systems, but I don't think you need them. You can probably even get by just using dpkg force to force the libgtk1.2 package to install without those depenedecies, but your milage may very.

Hope this helps!

I tried installing that (which I already had installed) but I'm still getting the same error:

> ./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by dfreer on 2011-04-12
Then it is either of the wrong type (32-bit on a 64-bit system, etc), or in the wrong place (ld only searches several locations by default), or ldconfig hasn't been run to update ld on the new library. You can also try placing the specified file within the same folder as your ePSXe binary, as I believe it ld will also search the current directory for shared libraries last.

---

### Post by joelstitch on 2011-04-13
> **dfreer said:**
> Then it is either of the wrong type (32-bit on a 64-bit system, etc), or in the wrong place (ld only searches several locations by default), or ldconfig hasn't been run to update ld on the new library. You can also try placing the specified file within the same folder as your ePSXe binary, as I believe it ld will also search the current directory for shared libraries last.

Well I have a 64bit system but I dont knwo what type of installation I installed.

---

### Post by dfreer on 2011-04-13
On that ubuntu packages site, there are two links: amd64 is for 64-bit computers, i386 is for 32-bit computers.
You also need to know whether or not ePSXe is a 32-bit binary or a 64-bit binary. 64-bit binaries will use the 64-bit library, and 32-bit binaries, even on a 64-bit system, will use 32-bit libraries. To find out what it is, use the file command on the binary:
```
file ./epsxe
```
To find out whether you are on a 64-bit install or a 32-bit install of ubuntu:
```
uname -a
```

---

### Post by joelstitch on 2011-04-13
> **dfreer said:**
> On that ubuntu packages site, there are two links: amd64 is for 64-bit computers, i386 is for 32-bit computers.
You also need to know whether or not ePSXe is a 32-bit binary or a 64-bit binary. 64-bit binaries will use the 64-bit library, and 32-bit binaries, even on a 64-bit system, will use 32-bit libraries. To find out what it is, use the file command on the binary:
```
file ./epsxe
```To find out whether you are on a 64-bit install or a 32-bit install of ubuntu:
```
uname -a
```

This is what i got:

> pag@pag-laptop:~$ file ./epsxe
./epsxe: ERROR: cannot open `./epsxe' (No such file or directory)
pag@pag-laptop:~$ uname -a
Linux pag-laptop 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64 GNU/Linux

---

### Post by dfreer on 2011-04-13
The file command needs to be run on your actual epsxe binary, you simply ran the command as I posted it. I do not know where your epsxe binary is on your system, you will need to either figure that out on your own and then run the file command on it, or link to whatever guide you used specifically to install epsxe and I might be able to figure it out.

If you absolutely cannot find it, one of these should help:
```
updatedb
locate epsxe
```
```
find / -type f -iname epsxe
```
```
whereis epsxe
```

As for the results of your system, you are running the 64-bit version of ubuntu. If your epsxe binary ends up being 64-bit, installing the library I originally linked to should work. If it's 32-bit, we will have to install the 32-bit version using dpkg --force-architecture.

EDIT: If you used this guide, it looks like it is in /usr/local/games/epsxe/ directory. There's a bash script that launches it at /usr/local/bin/epsxe. It also looks like that shell script sets the LD_LIBRARY_PATH to /usr/local/games/epsxe/, so you could probably place the libgtk-1.2.so.0 in /usr/local/games/epsxe/ without any fuss.

---

