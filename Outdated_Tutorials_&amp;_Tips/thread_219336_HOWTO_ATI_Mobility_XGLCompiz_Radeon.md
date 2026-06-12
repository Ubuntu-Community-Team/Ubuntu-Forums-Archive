---
title: "HOWTO: ATI Mobility XGL/Compiz Radeon"
date: 2006-07-19
forum: Outdated Tutorials &amp; Tips
---

### Post by Paerez on 2006-07-19
[size="4"]Not Doing So Well[/size]
This guide is pretty broken right now since edgy and various updates, including the move to beryl.

I was able to get beryl running by using Ubuntu Edgy's fglrx driver (not the one from ati.com, the one from the repos). Here is the guide:
[http://www.ubuntuforums.org/showthread.php?t=291464](http://www.ubuntuforums.org/showthread.php?t=291464)


Here is the old guide, in case any of the info is still useful.


Hey all this is my first howto, and a lot of blood, sweat, tears, microwave burritos, diet cola, chips, missed sleep, forum searching, google searching, soul searching, company time, and head scratching went into this.

First off I'd like to thank the guys at [Kororaa]("http://www.kororaa.org") for showing me that it was possible to get xgl compiz working with decent performance on my computer. Also thanks to Remix_88 for fixing the 1024x768 issue!

I'd also like to thank gruvsyco for his thread, on which a lot of my progress came from.

Second, who is this guide for? This guide is for people with an **ATI Mobility card** who **cannot get XGL/Beryl to work with the fglrx driver**, and would like to use the **open source xorg radeon** driver for acceleration.

OK now its go time.

First, off, if you have installed ubuntu clean and have not set up fglrx, and "glxinfo | grep rendering" gives you "Yes", and "lsmod | grep radeon" lists "radeon", skip to step 2.

[SIZE="4"]1. Get Radeon Going[/SIZE]
First, we need to remove xorg-driver-fglrx
```
sudo aptitude remove xorg-driver-fglrx
```

OK now lets grab the newest radeon driver from the compiz/beryl repos.
```
gksudo gedit /etc/apt/sources.list
```
And add this to the end:
```
deb http://www.beerorkid.com/compiz dapper main aiglx
deb http://media.blutkind.org/xgl/ dapper main aiglx
```
now add in the right stuff for the radeon driver:
```
sudo aptitude update
sudo aptitude dist-upgrade
sudo aptitude reinstall libgl1-mesa libgl1-mesa-dri
```

OK now we need our Xorg.conf to be ready
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf
```
Here are the areas of interest:
```
Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

#...

# Leave the identifier and BusID alone, but add the options
Section "Device"
	Identifier	"YOURS HERE"
	Driver		"radeon"
	BusID		"YOURS HERE"
	Option	  "backingstore" "true"
	Option	  "EnablePageFlip" "true"
	Option	  "SubPixelOrder" "none"
	Option	  "AccelMethod" "XAA"
	Option	  "RenderAccel" "true"
	Option	  "AGPMode" "4"
	Option	  "ColorTiling"   "on"
	Option	  "DynamicClocks" "on"
	Option	  "mtrr" "on"
	Option	  "VideoOverlay" "on"
	Option	  "OpenGLOverlay" "off"
EndSection

#...

Section "Screen"
	Identifier	"YOURS"
	Device		"YOURS"
	Monitor		"YOURS"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		# You can put your modes below, for your own resolutions, these are mine:
		Modes		"1400x1050" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

#...

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection
```
 
Now set up the modules to get the right ones at boot:
```
gksudo gedit /etc/modules
```
Make sure that you have these lines:
```
#agpgart # you dont need these two lines, just make sure they are NOT there
#fglrx
drm
radeon
```

Add a little something to your .drirc to get full resolution support:
```

gedit ~/.drirc

```

contents:
```

<driconf>
    <device screen="1" driver="r200">
        <application name="Default">
            <option name="allow_large_textures" value="2" />
        </application>
    </device>
</driconf>

```

Now reboot to get the modules to load.

If this didn't work and you got a text login, login and do "sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf" and then "sudo /etc/init.d/gdm restart". If you had to do this, you should stop now, you won't be able to get farther.

For the rest of you, log in to gnome and open a terminal and type:
```
glxinfo | grep rendering
```
and make sure you get a Yes.

OK Part 1 is done.

[SIZE="4"]2. XGL Time![/SIZE]
So Compiz-quinnstorm forked to Beryl, which is what this howto will now cover.

First, lets install xgl and Beryl:
```
sudo aptitude install xserver-xgl beryl emerald-themes
```

Now I dont know about you guys, but I hate switching GDM to XGL, because if it messes up I have to use the text console, so we are going to make our own xgl session.
```
sudo gedit /usr/share/xsessions/xgl.desktop
```
Here is the content:
```
[Desktop Entry]
Encoding=UTF-8
Name=XGL
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application

```
OK now we need to make /usr/bin/startxgl.sh:
```
sudo gedit /usr/bin/startxgl.sh
```
contents:
```
Xgl -fullscreen :1 -ac -accel xv -accel glx:pbuffer &
DISPLAY=:1
# Start GNOME
exec gnome-session
```
now make it executable:
```
sudo chmod +x /usr/bin/startxgl.sh
```

OK now log out and press CTRL+ALT+BACKSPACE. Click Options and then Select Session. Choose XGL. Log in and click "Just for this session" just in case it messes up.

To edit beryl related settings, run csm. To edit the window manager themes, run "beryl-settings".

Version 0.9 10/17/2006 11:41 EST
Switched from Compiz to Beryl. I haven't tested the changes so feedback would be helpful!

Version 0.8 09/06/2006 17:22 EST
Removed gnome-compiz-manager from the guide, since it no longer affects the current compiz version. Use csm to edit plugins and "compiz-start" to run compiz.

Version 0.7 08/30/2006 16:13 EST
Added Remix_88's fix for resolutions, and change installation commands to use the newer quinn packages instead of the vanilla ones.

Version 0.6 08/29/2006 17:13 EST
Fixed a typo (added 'install' to 'sudo aptitude')

Version 0.5 08/09/2006 11:24 CDT
Added the note to tell people to skip step 1 if they have a working default install.

Version 0.4 08/06/2006 14:03 CDT
Re-organized the radeon section to do things in a better order and more simply. Thanks Flavian.

Version 0.3 07/25/2006 11:29 CDT
Forced reinstall of Mesa packages

Version 0.2 07/24/2006 15:08 CDT
Added note about removing fglrx module

Version 0.1 07/19/2006 19:45 CDT

---

### Post by kaamos on 2006-07-21
It actually worked!

This is the first time I've been able to use xgl on my mobility radeon 9000. Thank you very much! :) Seems a bit unstable and scrolling web pages is slow as hell but hey, it works.

---

### Post by Paerez on 2006-07-21
Cool! This was mostly from memory, so I am glad it worked out for you. I don't use it since 1024x768 is sucky (my screen goes to 1400x1050) but it is nice to be able to log in to the XGL session to show off, then log in to my normal session to do my normal stuff.

---

### Post by MiniZiper on 2006-07-21
Ok, is there a public key, cuz knsole gives me this:
[COLOR="DarkOrange"]Reading package lists... Done
W: GPG error: [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: You may want to run apt-get update to correct these problems[/COLOR]

---

### Post by xtacocorex on 2006-07-21
I've been trying to get XGL working on my Mobility M6 for a while and gave up. I was annoyed that it worked when I ran the Kororaa LiveCD and couldn't get it working under Dapper.

I'm trying this when I get home and will report back when I get it working.

Any reason why it won't work for 1400x1050?

---

### Post by kaamos on 2006-07-21
> Any reason why it won't work for 1400x1050?

Works fine in all tested resolutions here, 1400x1050 is the native on my laptop as well. The scrolling is actually the only thing that sucks once you work around the xgl bugs that apply with other drivers as well.

---

### Post by MiniZiper on 2006-07-21
My OpenGL driver renderer is "Mesa GLX Indirect" So, I am using mesa, but the indirect version. SO i just need to get the cpmpiz repositiory running to get the DRI one. I don't think just becuase I'm using KDE and not GNOME Im not getting DRI.

---

### Post by Paerez on 2006-07-21
you may need this key:
```
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
```

---

### Post by Paerez on 2006-07-21
@xtacocorex
You can get kororaa to run, just follow this bugfix:
[http://kororaa.org/static.php?page=bugs](http://kororaa.org/static.php?page=bugs)

---

### Post by MiniZiper on 2006-07-21
Its like im cursed with problems  ](*,)  when I try to add the key in konsole.. it downloads everything but then it gets stuck there doign nothing... i looked the key on google and its the same one. well im gonna leave it there for a while to see if it works...

---

### Post by MiniZiper on 2006-07-21
wait, no, it automaticaly entered a wrong password for some odd reason...

---

### Post by MiniZiper on 2006-07-21
Oh well, i guess i have no DRI future... I am using mesa, with all the packages and stuff... I have never had fglrx drivers in here, I really don't know whats wrong with this. Its probably the diffrence that I have kubuntu and u Ubuntu?

---

### Post by Paerez on 2006-07-21
kubuntu/ubuntu should make no difference. Can you post an archive containing your /etc/X11/xorg.conf?

---

### Post by MiniZiper on 2006-07-21
I did on th other forum we were on... but here you go

---

### Post by Paerez on 2006-07-21
do you have the radeon modules loaded?
```
lsmod | grep radeon
```
and did you restart gdm?

---

### Post by MiniZiper on 2006-07-21
miniziper@miniziper-kubuntu:~$ lsmod | grep radeon
radeon                116000  0
drm                    73236  1 radeon
miniziper@miniziper-kubuntu:~$            

i got that, i dont know what that is...

---

### Post by MiniZiper on 2006-07-21
everytime i do something major i log out and restart x server..

---

### Post by Paerez on 2006-07-21
that is correct and it means that the radeon driver loaded successfully. Log out to gdm, then press CTRL+ALT+BACKSPACE, log in, and then send me /var/log/Xorg.0.log.

EDIT: if you already restarted just send me the log

---

### Post by MiniZiper on 2006-07-21
here it is. I just restarted

---

### Post by MiniZiper on 2006-07-21
found this in the log....

(WW) RADEON(0): Direct rendering disabled

---

### Post by xtacocorex on 2006-07-21
> **Paerez said:**
> @xtacocorex
You can get kororaa to run, just follow this bugfix:
[http://kororaa.org/static.php?page=bugs](http://kororaa.org/static.php?page=bugs)


Kororaa ran fine for me, I just couldn't get Dapper to run XGL and therefore got sad because I really wanted to get it working.

Thanks for the info on the resolutions kaamos.

---

### Post by Paerez on 2006-07-21
I think its this:
(EE) RADEON(0): Static buffer allocation failed.  Disabling DRI.

Google says to try this:
Reboot and go into your bios and increase your AGP aperture size. Only go up a little. I would suggest 8mb or 16mb. If it is already at those, try 32mb.

---

### Post by Paerez on 2006-07-21
Yeah I gotta try the 1400x1050! I can't live without it. Heheh I must not have restarted gdm or something when I tried. I will give it a shot tonight.

---

### Post by MiniZiper on 2006-07-21
uh yea... this is a compaq... and they, dont let you do freaky thing with their BIOS! But why BIOS? with WinXP, I can play 3D games very smoothly with fast write and all of that enabled... I'll try though...

---

### Post by MiniZiper on 2006-07-21
I'm doing online support with them.. so they can tell me how to get to advance settings

---

### Post by MiniZiper on 2006-07-21
Damn Compaq, all they let you do is change boot priority and date... Whats kind of BIOS is that?!
But what I did find out is that the normal AGP aperture size is 256MB... a little high, but thats what a guy got when he analyzed his system with everest. Sigh.... never get a Compaq

---

### Post by Paerez on 2006-07-21
Yeah I don't know then, sorry I can't help you anymore, but we have reached the limit of my knowledge on the subject.

---

### Post by xtacocorex on 2006-07-21
So close to getting this working.

Here is the output of /var/log/Xorg.0.log
```

>: cat /var/log/Xorg.0.log | grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) RADEON(0): LCD DDC Info Table found!
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0x89ff8800 is: 0x89ff8800
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xe07fe000
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0x89ff8800 is: 0x89ff8800
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xe07fe000
>: cat /var/log/Xorg.0.log | grep EE
Current Operating System: Linux tinman-edi 2.6.15-26-686 #1 SMP PREEMPT Mon Jul 17 20:14:14 UTC 2006 i686
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER

```

I had to change 0=Standard in /etc/gdm/gdm.conf to 1=Standard.

I'm attaching my xorg.conf file, I may have missed something in there.

It was also saying that I don't have gnome-window-decorator. 

I'm going to keep at this for a while to see if I can hash it out.

---

### Post by Squalor on 2006-07-22
I get this when I try to start compiz (with the startcompiz command):

```
gnome-window-decorator: no process killed
```

And no compiz...

---

### Post by Paerez on 2006-07-22
Hey Kaamos, did you get it working fine in 1400x1050 by following my guide? Or did you change it a little? (Obviously you would have to change the lines in xorg). I can't seem to get 1400x1050 to work. How'd you do it?

---

### Post by misha680 on 2006-07-24
Ok, I'm not sure this is the right thread, but I'm curious. I actually am trying to use XGL/Compiz with a Mobility Radeon 9000 using ATI's fglrx drivers, and the weird thing is IT WORKS but only maybe 1 out of 20 times that I run compiz, the other times Xgl starts fine but the compiz command just doesn't seem to do anything, doesn't give me any errors or anything. It's quite strange. Anyone had this problem?

I am assuming that since it does in fact work every once in a while, my general settings have to be correct.

Thanks
Misha

---

### Post by cptnapalm on 2006-07-25
Misha, I don't know if this will help but this is something which was said to be important for ATI cards.

Check your /etc/gdm/gdm.conf-custom file and look for a line that looks like this: GdmXserverTimeout=10.  If it is 10, change it to 50.

Patrick

---

### Post by misha680 on 2006-07-26
I posted the question on the compiz forums and got a reply. I downloaded an older Xgl server and   that fixed it. Here's the link:

[http://ubuntu.compiz.net/pool/main/x/xserver-xgl/xserver-xgl_7.0.0-0ubuntu28_i386.deb](http://ubuntu.compiz.net/pool/main/x/xserver-xgl/xserver-xgl_7.0.0-0ubuntu28_i386.deb)

Misha

---

### Post by shoyer on 2006-07-26
When I run startcompiz, I get this out:

```
gnome-window-decorator: no process killed
compiz.real: Root visual is not a double buffered GL visual
compiz.real: Failed to manage screen: 0
```Then the gnome session restarts.

The only difference from this guide is that I'm using the compiz packages, not compiz-vanilla. Everything else checks out in the guide until here.

I'm running a Dell Latitude D600 with a ATI Radeon Mobility 9000.

---

### Post by ellion on 2006-07-26
> **shoyer said:**
> When I run startcompiz, I get this out:

```
gnome-window-decorator: no process killed
compiz.real: Root visual is not a double buffered GL visual
compiz.real: Failed to manage screen: 0
```Then the gnome session restarts.


I have exactly the same problem. It restarts because of the Composite extension. When I have it loaded and start any OpenGL app, X restarts. Though XGL should do fine without the extension, he can't find any managable screens when I disable it, evne with the DISPLAY variable set :/ OpenGL in general without Composite runs fine.

@shoyer: Are you sure it is a radeon 9000? I have a Thinkpad T30 with a radeon 7500, which X recognizes as a 9000.

---

### Post by Paerez on 2006-07-26
It seems like you are trying to run XGL on :0, did you try the way my guide says, and use XGL on :1 and set the display variable to :1?

---

### Post by shoyer on 2006-07-26
> **Paerez said:**
> It seems like you are trying to run XGL on :0, did you try the way my guide says, and use XGL on :1 and set the display variable to :1?
I did everything other than reinstalling compiz as in your guide. I double checked, and XGL and the display variable are both on :1.

The only thing I can think of is that maybe it has something to do with me setting up x11vnc the other day. I followed instructions from [this site]("http://64.233.161.104/search?q=cache:Sy2ozhwLFIIJ:www.odrakir.com/blog/%3Fp%3D201+ubuntu+vnc&hl=en&gl=us&ct=clnk&cd=7&client=firefox") (currently offline: link is to google cache).

ellion - I'm not sure what you're talking about with regards to the Composite extension. I don't know how to disable that. glxgears, at least, runs fine in the XGL session.

It's also definitely a Radeon Mobility 9000. That's from the specs for my computer, not just X.

----

I'm pretty new to Ubuntu so I appreciate all of your help. Thanks.

---

### Post by suloku on 2006-07-27
Here's another with a big problem: I can't enable direct rendering.

I have an ATI RADEON 9200. In the gentoo wiki card compatibilty list mine seems to be incompatible, it sais that a "distorted screen" appears, I tested it with kororaa and that was it.

Then I found this thread and tried the bugfix from kororaa, using the radeon drivers and it worked!

So I tried to enable all this following this howto, but it isn't working...

The worst thing is that the ubuntu installation recognized my card and enabled 3d rendering, but I installed fglrx drivers following another howto and there's no mo direct rendering.

By now, I have no fglrx driver on my system, any ideas¿?

---

### Post by Paerez on 2006-07-27
this howto is to get it working the same way the kororaa does- through the radeon driver. This involves completely removing fglrx and reinstalling the mesa stuff to get the radeon libGL.so.1.2.

---

### Post by suloku on 2006-07-27
Then the stuff is in that library...I once enabled direct rendering wth another how to form here, the trick was to install the propietary drivers ad then change the library to the one on the 8.24.8 driver package...

I'm gona try to change it, and lets see if I can enable 3d rendering with the radeon stuff.

EDIT:

I have done:
suloku@ubuntu:/etc/X11$ sudo updatedb
suloku@ubuntu:/etc/X11$ locate libGL.so
/usr/lib/libGL.so.1
/usr/lib/libGL.so.1.2.orig
/usr/X11R6/lib/FGL.renamed.libGL.so.1.2

the one named .orig is the one I changed when i enabled direct rendering with fglrx, it seems i don't have te fuckin library in my sistem, maybe that's why I can't enable direct rendering with the radeon driver

---

### Post by Paerez on 2006-07-27
then you need to downgrade then upgrade libgl1-mesa to get the radeon one back.

---

### Post by suloku on 2006-07-27
Excuse me, how can I downgrade? It's something i've never done, I just have been a cuple of months since I definitely drop away windows.

Anyway I'll search about downgrading packages.

I think something happened to my ubuntu installation since I installed fglrx drivers, beacause starting with a kubuntu live cd I have direct rendering, so I exported the xorg.conf from the live cd (using the ati drivers) to my ubuntu installation, but instead of what I was specting I had no direct rendering.

I thought about erasing the / partition and installing all the stuff again, but I don't want to do it beacause I think this is only needed in windows.

---

### Post by Paerez on 2006-07-27
in synaptic I think it's "Package->Force Version". Just force it down a version, Apply, then mark it to be updated, Apply.

---

### Post by suloku on 2006-07-27
I think I can't do this with synaptic, i tells me to eliminate almost all X-window environment packages

---

### Post by Paerez on 2006-07-27
hmm. I was able to do it in aptitude. 

EDIT: Removed the keys, don't want anyone breaking their system

---

### Post by suloku on 2006-07-27
omg, i think i've just brokened something, I sitll can't downgrade the lib, it says that fails simbolic linking to libgl.so.1 in /usr/lib.

I checked the usr/lib dir and I have no mor libLG.so files.

And the worst is that all ubuntu desktop stuff isn't working properly, sending me corba errors (I installed kubuntu-desktop some weeks ago and im mostly using kde)

jezz, seems I'll have to backup config files and erase / partition :S

---

### Post by manro on 2006-07-27
> **shoyer said:**
> When I run startcompiz, I get this out:

```
gnome-window-decorator: no process killed
compiz.real: Root visual is not a double buffered GL visual
compiz.real: Failed to manage screen: 0
```Then the gnome session restarts.

The only difference from this guide is that I'm using the compiz packages, not compiz-vanilla. Everything else checks out in the guide until here.

I'm running a Dell Latitude D600 with a ATI Radeon Mobility 9000.

Same here :sad: but I'm using compiz-vanilla!

I'm running a Dell Latitude D610 but I think it have a Radeon Mobility 9000 too.

Some help here!

---

### Post by suloku on 2006-07-28
nevermind obout the gnome apps errors, after a reboot all seems to be ok.

But still haven't the libGL files, I dunno wich ubuntu package installs them :'(

---

### Post by Paerez on 2006-07-28
libgl1-mesa installs them, but you have to downgrade/upgrade to get them to appear. It is tricky to do the downgrade/upgrade because aptitude is the only program (I think) that's smart enough to do it.

I did it last night to check and it replaced my libGL.so.* files.

---

### Post by negatory on 2006-07-28
It worked but not in my laptop screen native resolution of 1280x800.In (wonderfull) 1024x768 it worked fine but I just can't work in that resolution.
Thanks

---

### Post by Paerez on 2006-07-28
if you want to try it in 1280x800, you can try using this line in your xorg.conf:
```
Modes		"1280x800" "1024x768" "800x600" "640x480"
```

---

### Post by Beach on 2006-07-28
First of all, thanks so much for writing this howto.  I think I am close but I do not get the Xgl/Compiz eye candy when I run run 'startcompiz'. I know I am good with the 3D because the 3D screen savers work now.  Also, I receive an "ok" when I do 'glxinfo | grep rendering'.

I followed the installation steps and did not notice any errors when loading the packages.  When I tried to do the XGL session (after a ctrl+alt+backspace) and I got a message that the session only lasted 10 seconds.  I logged in normally and created the 'startcompiz' in the next steps.   When I try to run 'startcompiz' the desktop top crashes and I am back at the GDM login screen.   I then tried each command in 'startcompiz' manually and here are the results:

```

$ killall gnome-window-decorator

gnome-window-decorator: no process killed

$ compiz --replace gconf &
[1] 8930
beach@Ewa:~$ compiz.real: Root visual is not a double buffered GL visual
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
[1] Done compiz --replace gconf 

$ gnome-window-decorator &
```

Thats when it crashes and I can not see any errors.  Is there a log of some sort that might help me tell you what is going on?

Thanks!

-Beach

---

### Post by Paerez on 2006-07-28
/var/log/Xorg.0.log is good. Also, is the "dbe" module enabled in your xorg.conf? Also try :0 and :1 for your display.

---

### Post by Beach on 2006-07-28
Thanks for the quick reply!  I'm watching Stargate or I would have responded sooner myself...  Anyway, I checked and I am running 'bde', at least it is listed in my "modules" section.  The log file is attached.

---

### Post by Paerez on 2006-07-28
Hmm I searched around on google and stuff and I couldn't find much other than making sure dbe comes before dri in the modules section.

---

### Post by Beach on 2006-07-28
> **Paerez said:**
> /var/log/Xorg.0.log is good. Also, is the "dbe" module enabled in your xorg.conf? Also try :0 and :1 for your display.
Sorry, how do I set the display to :0 or :1?

Thanks again.

---

### Post by Paerez on 2006-07-28
your /usr/bin/startxgl.sh should be like this for :1
```
Xgl -fullscreen :1 -ac -accel xv -accel glx:pbuffer &
DISPLAY=:1
# Start GNOME
exec gnome-session
```

for :0, do:
```
Xgl -fullscreen :0 -ac -accel xv -accel glx:pbuffer &
# Start GNOME
exec gnome-session
```

---

### Post by Beach on 2006-07-29
I can start the session with :0 but executing "startcompiz" does the same thing - crashes the desktop.  I looked in my processes after starting the XGL session again and it states that XGL is defunct - maybe that is the problem.

Durn, I really wanted this to work.  I have it working perfectly on my desktop which has a Nvidia card.

Not sure what else to try.

---

### Post by Paerez on 2006-07-29
yeah i wasn't satisfied with 1024x768 anyways so now I am working on getting aiglx to work, but I don't think it will. Its not so great with ati mobility, it was more of a "it can be done, but is it worth it?" guide.

---

### Post by pksings on 2006-07-30
Un-believable.

I completely re-installed from scratch to get 3D to work and finally did using this radeon Howto and the radeon driver. But compiz has the exact same problem, it just kills the xserver.   Xgl will run on screen 0 but compiz will not, it just restarts the server. On screen 1 Xgl never starts at all.

So close, and yet still so far....  
3 months, 3 re-installs, who knows how many attempts to get fglrx working, I lost count and ultimately gave up.

Never again ATI....

My son bought an Nvidia card and it took him less than an hour to have compiz working perfectly.

---

### Post by btn21 on 2006-07-30
Hi,


Getting XGL/Compiz to work with the latest ATI drivers should be fairly straight forward. They've fixed the issue where you have to run on display 1.
I couldn't get XGL/Compiz to work at all before they fixed this, but now it works like a charm.

btw, the latest version of the ATI linux drivers is 8.27.10

---

### Post by Paerez on 2006-07-30
I am gonna spend all day today on that!

EDIT: OK I spent an hour trying to get it to work but it still seems to be the same for those of us with mobility cards. And a lot of people complain saying that the :0 :1 problem is not fixed.

---

### Post by dmo580 on 2006-08-04
Bleh, no composite extension error for me still

---

### Post by Paerez on 2006-08-04
that is because either you don't have the composite extension thing in your xorg (but I'm sure you do) or there is something going wrong when it loads xorg. Check your /var/log/Xorg.0.log for lines that start with (EE) or (WW), then post them here.

---

### Post by Flavian on 2006-08-05
sudo aptitude install --reinstall libgl1-mesa libgl1-mesa-dri

only works for me if I put:
sudo aptitude install libgl1-mesa libgl1-mesa-dri
or
sudo aptitude reinstall libgl1-mesa libgl1-mesa-dri

and

sudo rmmod fglrx
gives me this:

ERROR: Module fglrx is in use


What am I supposed to do from this point on?
I did everything like you explained in your Howto...
I am afraid to reboot, since I removed the drivers, I am afraid it might not work anymore at all :/

Please help
Flo

---

### Post by Paerez on 2006-08-05
we are switching you over from fglrx to radeon. So as long as you have libgl1-mesa installed, and you are using radeon in your xorg.conf's device section, then you will be fine.

Thanks for the tip on aptitude, I am going to fix the howto.

---

### Post by Flavian on 2006-08-05
Now I got it, but if I boot up my system I get a black screen, it i running, I can see, but it is black. I hear the drums, of ubuntu and also can log in blindly, but the screen is black.

I think it is because of my xorg.conf!
Can someone post his xorg.conf that works with compiz
My Graphics card is an ATI Mobility Radeon X700

Thanks
Flo

---

### Post by Paerez on 2006-08-05
here is the xorg.conf I use for doing xgl.

Keep in mind you'll have to change the device section to be your device.

---

### Post by Flavian on 2006-08-05
I think I am too much of a newbie to get this straight, sorry :(
First of all when I first set up my Laptop the Xserver did not work, I finally got it to work with THIS Xorg.conf file below.
The reason was, because aticonfig did not work on my laptop, so I simply had to replace my xorg.conf with a xorg.conf posted here in the forum.
Now, changing my settings for XGL/Compiz I encountered the following problem.
There is more than one "device" section for the graphics card and so on.
Can someone help me, what should I change, what should I leave, to get XGL/Compiz to work ??

This is my xorg.conf:
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
Identifier     "Default Layout"
Screen      0  "aticonfig Screen 0" 0 0
InputDevice    "Generic Keyboard"
InputDevice    "Configured Mouse"
InputDevice    "stylus" "SendCoreEvents"
InputDevice    "cursor" "SendCoreEvents"
InputDevice    "eraser" "SendCoreEvents"
InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

# path to defoma fonts
FontPath     "/usr/share/X11/fonts/misc"
FontPath     "/usr/share/X11/fonts/cyrillic"
FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath     "/usr/share/X11/fonts/Type1"
FontPath     "/usr/share/X11/fonts/100dpi"
FontPath     "/usr/share/X11/fonts/75dpi"
FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load  "bitmap"
Load  "ddc"
Load  "dri"
Load  "extmod"
Load  "freetype"
Load  "glx"
Load  "int10"
Load  "type1"
Load  "vbe"
EndSection

Section "InputDevice"
Identifier  "Generic Keyboard"
Driver      "kbd"
Option    "CoreKeyboard"
Option    "XkbRules" "xorg"
Option    "XkbModel" "pc104"
Option    "XkbLayout" "es"
EndSection

Section "InputDevice"
Identifier  "Configured Mouse"
Driver      "mouse"
Option    "CorePointer"
Option    "Device" "/dev/input/mice"
Option    "Protocol" "ExplorerPS/2"
Option    "ZAxisMapping" "4 5"
Option    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier  "Synaptics Touchpad"
Driver      "synaptics"
Option    "SendCoreEvents" "true"
Option    "Device" "/dev/psaux"
Option    "Protocol" "auto-dev"
Option    "HorizScrollDelta" "0"
Option    "SHMConfig" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
Identifier  "stylus"
Driver      "wacom"
Option    "Device" "/dev/wacom"          # Change to 
Option    "Type" "stylus"
Option    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
Identifier  "eraser"
Driver      "wacom"
Option    "Device" "/dev/wacom"          # Change to 
Option    "Type" "eraser"
Option    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
Identifier  "cursor"
Driver      "wacom"
Option    "Device" "/dev/wacom"          # Change to 
Option    "Type" "cursor"
Option    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
Identifier   "Generic Monitor"
HorizSync    28.0 - 64.0
VertRefresh  43.0 - 60.0
Option    "DPMS"
EndSection

Section "Monitor"
Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
Driver      "ati"
Option    "UseFBDev" "true"
BusID       "PCI:1:0:0"
EndSection

Section "Device"
Identifier  "ATI Graphics Adapter 0"
Driver      "fglrx"
Option    "(null)"
Option    "VideoOverlay" "on"
Option    "OpenGLOverlay" "off"
BusID       "PCI:3:0:0"
EndSection

Section "Screen"
Identifier "Default Screen"
Device     "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
Monitor    "Generic Monitor"
DefaultDepth     24
SubSection "Display"
Depth     1
Modes    "1280x800"
EndSubSection
SubSection "Display"
Depth     4
Modes    "1280x800"
EndSubSection
SubSection "Display"
Depth     8
Modes    "1280x800"
EndSubSection
SubSection "Display"
Depth     15
Modes    "1280x800"
EndSubSection
SubSection "Display"
Depth     16
Modes    "1280x800"
EndSubSection
SubSection "Display"
Depth     24
Modes    "1280x800"
EndSubSection
EndSection

Section "Screen"
Identifier "aticonfig Screen 0"
Device     "ATI Graphics Adapter 0"
Monitor    "aticonfig Monitor 0"
DefaultDepth     24
SubSection "Display"
Viewport   0 0
Depth     24
EndSubSection
EndSection

Section "DRI"
Mode         0666
EndSection


```

Thanks in advance
Flo

---

### Post by Paerez on 2006-08-05
OK I did my best to fix yours, try this:

---

### Post by Flavian on 2006-08-05
Thanks man!
But this gives me the exact same error message I got when I tried it myself :(

Error, no screens found.
There must be something with the double entry...

Can you think of something that would work for me?
Flo

---

### Post by Paerez on 2006-08-05
I removed your double entry. Something else is wrong. The "no screens found" error is pretty general.

send me your /var/log/Xorg.0.log

---

### Post by Flavian on 2006-08-05
Thank you very much for your effort and time you put in!
I would be lost without you... ;)

It would be nice if you could change the xorg.conf I posted already and just put it on here, if you can find out what is wrong.

---

### Post by Paerez on 2006-08-06
I replied to your PM, but I wanted to comment on the thread as well.

Your log shows that you are using the fglrx driver. This howto is meant to use the radeon driver and not the fglrx driver, because I had no success with the fglrx driver. So please post to other threads regarding getting XGL to work with fglrx.

If you want to use the radeon driver, follow the howto in full, and then post if you have problems.

---

### Post by suloku on 2006-08-08
Yeah, at last got it, I have direct rendering with the ATI/RADEON drivers.

The prob gone away with a simple :

> $ sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri

Now let's see if I can run XGL at last

---

### Post by Paerez on 2006-08-08
Good luck!

Also, if anyone is able to run a Mobility 9x000 card at >1024x768 resolution, please let us know.

---

### Post by suloku on 2006-08-08
Ok, I followed your howto but it seems that in the xgl session I have no direct rendering anymore, it's a pain to open a gnome-terminal and glxgears drops a nice 100 fps. If I start compiz I get the "distorted screen" (the error of my card in the gentoo wiki of xgl)

I'll try getting the xorg.conf produced by kororaa using the radeon driver, hope that with this I'll be able to run compiz...

---

### Post by Paerez on 2006-08-08
Yeah make sure you get dri before you try to run compiz, it will just mess up.

I had this issue when there was leftover fglrx stuff. Make sure you removed fglrx and that in your /usr/lib/dri there is nothing with "fglrx" in the name. Also make sure you're using 1024x768 resolution in your xorg.conf, not just your user setting.

---

### Post by suloku on 2006-08-08
these are the contents of /usr/lib/dri
> ffb_dri.so   mach64_dri.so  r200_dri.so    s3v_dri.so     tdfx_dri.so
i810_dri.so  mga_dri.so     r300_dri.so    savage_dri.so  trident_dri.so
i915_dri.so  r128_dri.so    radeon_dri.so  sis_dri.so     unichrome_dri.so


I'll get the xorg.conf from kororaa now and try again

---

### Post by nihilocrat on 2006-08-08
Okay, I got my Mobility Radeon 7500 working with this, but when I started using Xgl, I was presented with a mangled desktop with no visible text, just a bunch of gray boxes. Okay. I thought things might get better once I enabled compiz, so I was able to blindly open up a terminal and start it and... viola! Everything works! But wait! What the hell? Direct rendering suddenly stops working? Am I missing something? Pre-Xgl direct rendering was fine, but now, when it's needed the most, it doesn't. Thus, I'm presented with a pretty, yet unusably-slow desktop. How do I get DRI working again? Is there a special radeon driver for Xgl I'm missing or something?

edit: After reading a little closer, I guess my problem is the same as the guy above... I symlinked the DRI modules but no luck.

---

### Post by Paerez on 2006-08-08
can you guys post your "/var/log/Xorg.0.log" file after trying an XGL login? That will give any errors regarding dri, etc...

---

### Post by suloku on 2006-08-08
okay, a reboot IS needed to get the stuff work...here are my tries:

1.- After getting kororaa xorg.conf in my pc in the right place I start the xgl session, then startcompiz and...yeah! It works at last!

2.- So I thought theproblem was that I didn't reboot the sistem after the xorg.conf stuff, so I put again the radeon xorg.conf I edited before and rebooted...now I got the damn distorted screen error, so:

3.- I replaced again the xorg.conf (without rebooting) with kororaa's, started the session again (with the alt+control+backspace) and I got distorted screen again.

So to enable it a reboot is needed, and I have something missing in my xorg.conf, I'm gonna see if I get it.

Posting the kororaa's generated xorg.conf with radeon driver for "ATI Technologies, Inc. RV280 [Radeon 9200]

> 
Section "ServerLayout"
	Identifier	"X.Org Configured"
	Screen	0	"Screen0" 0 0
	InputDevice	"Keyboard0" "CoreKeyboard"
# PS/2 Mouse not detected
# Serial Mouse not detected
	InputDevice	"USB Mouse" "AlwaysCore"
#No Synaptics touchpad found
EndSection

Section "ServerFlags"
	Option	"AllowMouseOpenFail" "true"
	
EndSection

Section "Files"
	FontPath	"/usr/share/fonts/util"
	FontPath	"/usr/share/fonts/encodings"
	FontPath	"/usr/share/fonts/misc"
	FontPath	"/usr/share/fonts/local"
	FontPath	"/usr/share/fonts/terminus"
	FontPath	"/usr/share/fonts/corefonts"
	FontPath	"/usr/local/share/fonts"
	FontPath	"/usr/share/fonts"
	FontPath	"/usr/share/fonts/default"
	FontPath	"/usr/share/fonts/TTF"
	FontPath	"/usr/share/fonts/arphicfonts"
	FontPath	"/usr/share/fonts/jisx0213"
	FontPath	"/usr/share/fonts/shinonome"
	FontPath	"/usr/share/fonts/baekmuk-fonts"
	FontPath	"/usr/share/fonts/kacst-fonts"
	FontPath	"/usr/share/fonts/sgi-fonts"
	FontPath	"/usr/share/fonts/unfonts"
	FontPath	"/usr/share/fonts/default/ghostscript"
	FontPath	"/usr/share/fonts/xfonts-cronyx-100dpi:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-75dpi:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-misc:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-100dpi"
	FontPath	"/usr/share/fonts/xfonts-cronyx-75dpi"
	FontPath	"/usr/share/fonts/xfonts-cronyx-misc"
	FontPath	"/usr/share/fonts/xfonts-cronyx-cp1251-100dpi:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-cp1251-75dpi:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-cp1251-misc:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-cp1251-100dpi"
	FontPath	"/usr/share/fonts/xfonts-cronyx-cp1251-75dpi"
	FontPath	"/usr/share/fonts/xfonts-cronyx-cp1251-misc"
	FontPath	"/usr/share/fonts/xfonts-cronyx-isocyr-100dpi:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-isocyr-75dpi:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-isocyr-misc:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-isocyr-100dpi"
	FontPath	"/usr/share/fonts/xfonts-cronyx-isocyr-75dpi"
	FontPath	"/usr/share/fonts/xfonts-cronyx-isocyr-misc"
	FontPath	"/usr/share/fonts/xfonts-cronyx-koi8r-100dpi:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-koi8r-75dpi:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-koi8r-misc:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-koi8r-100dpi"
	FontPath	"/usr/share/fonts/xfonts-cronyx-koi8r-75dpi"
	FontPath	"/usr/share/fonts/xfonts-cronyx-koi8r-misc"
	FontPath	"/usr/share/fonts/xfonts-cronyx-koi8u-100dpi:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-koi8u-75dpi:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-koi8u-misc:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-koi8u-100dpi"
	FontPath	"/usr/share/fonts/xfonts-cronyx-koi8u-75dpi"
	FontPath	"/usr/share/fonts/xfonts-cronyx-koi8u-misc"
EndSection

Section "Module"
	Load	"ddc"
	Load	"vbe"
	Load	"dbe"
	Load	"dri"
	Load	"extmod"
	Load	"glx"
	Load	"bitmap"
	Load	"speedo"
	Load	"type1"
	Load	"freetype"
	Load	"record"
EndSection

Section "InputDevice"
	Identifier	"Keyboard0"
	Driver	"kbd"
	Option	"CoreKeyboard"
	Option	"XkbRules" "xorg"
	Option	"XkbModel" "pc105"
	Option	"XkbOptions" "grp:toggle,grp_led:scroll"
	Option	"XkbVariant" ",winkeys"
EndSection

Section "InputDevice"
	Identifier	"Serial Mouse"
	Driver	"mouse"
	Option	"Protocol" "Microsoft"
	Option	"Device" "/dev/ttyS0"
	Option	"Emulate3Buttons" "true"
	Option	"Emulate3Timeout" "70"
	Option	"SendCoreEvents"  "true"
EndSection

Section "InputDevice"
	Identifier	"PS/2 Mouse"
	Driver	"mouse"
	Option	"Protocol" "IMPS/2"
	Option	"Device" "/dev/misc/psaux"
	Option	"Emulate3Buttons" "true"
	Option	"Emulate3Timeout" "70"
	Option	"SendCoreEvents"  "true"
	Option	"ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier	"USB Mouse"
	Driver	"mouse"
	Option	"Device" "/dev/input/mice"
	Option	"SendCoreEvents" "true"
	Option	"Protocol" "IMPS/2"
	Option	"ZAxisMapping" "4 5"
	Option	"Buttons" "5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics"
	Driver	"synaptics"
	Option	"Protocol" "event"
	Option	"Device" ""
	Option	"LeftEdge" "1900"
	Option	"RightEdge" "5400"
	Option	"TopEdge" "1900"
	Option	"BottomEdge" "4000"
	Option	"FingerLow" "25"
	Option	"FingerHigh" "30"
	Option	"MaxTapTime" "180"
	Option	"MaxTapMove" "220"
	Option	"VertScrollDelta" "100"
	Option	"MinSpeed" "0.02"
	Option	"MaxSpeed" "0.10"
	Option	"AccelFactor" "0.0010"
	Option	"SHMConfig" "on"
EndSection

# Auto-generated by mkxf86config

Section "Monitor"
	Identifier   "Monitor0"
	HorizSync    28.0 - 96.0
	VertRefresh  50.0 - 75.0
EndSection

Section "Device"
	### Available Driver options are:-
	# sw_cursor is needed for some ati and radeon cards
	#Option     "sw_cursor"
	#Option     "hw_cursor"
	#Option     "NoAccel"
	#Option     "ShowCache"
	#Option     "ShadowFB"
	#Option     "UseFBDev"
	#Option     "Rotate"
	Identifier  "Card0"
	# The following line is auto-generated by x11-misc/mkxf86config
	Driver      "radeon"
	VendorName  "All"
	BoardName   "All"
#	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device	"Card0"
	Monitor	"Monitor0"
	DefaultColorDepth 24
	SubSection "Display"
		Depth	1
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	32
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode 0666
EndSection



---

### Post by Paerez on 2006-08-08
if rebooting fixes stuff, check your '/etc/modules' file and remove agpgart and fglrx from the list, that may help.

---

### Post by nihilocrat on 2006-08-08
> **Paerez said:**
> if rebooting fixes stuff, check your '/etc/modules' file and remove agpgart and fglrx from the list, that may help.

Does that mean that agpgart shouldn't show up when I run "lsmod | grep agpgart"? I don't have it in my /etc/modules file, so I'm not sure how I would keep it from loading.

---

### Post by Paerez on 2006-08-08
I may be thinking of another one. The key is to make sure that drm and radeon are in lsmod, and fglrx is not. Agpgart is fine as long as drm and radeon are there too.

---

### Post by suloku on 2006-08-08
Ok..It seems that the problem isn't in the xorg.conf, only once I got xgl working from the start.

Its like a problem with the /etc/modules file, because if I:

-Reboot, start an xgl session and start compiz: distorted screen

-Reboot, start in xterm session, do a modprobe drm && modprobe radeon, then alt+control+backspace, start xgl session and start compiz...SUCCES!

Well, I got an error in compiz ( compiz.real: water: GL_ARB_fragment_program is missing), I think it's about a pluggin, i'll check later.

I have the agpart module loaded (depending on radeon driver) when I do lsmod, but it isn't in the /etc/modules file (actually i have it, but commented)

---

### Post by Paerez on 2006-08-08
OK, put drm and radeon in your /etc/modules (you probably already have it).

Then reboot.

Then run:
```
lsmod | grep radeon
```

and see if they are loading at boot. If they haven't loaded at boot, try this:
```
dmesg | grep radeon
dmesg | grep drm
```
and see if you see any errors. (Note: dmesg is the log of your computer's boot and any hardware events).

---

### Post by suloku on 2006-08-09
Mmm...after testing i've come to the conclusion that xgl in kde works, but if I don't do the modprobe things before starting compiz in gnome i got the distorted screen stuff

The prob is that in kde the keymapping goes a little crazy

---

### Post by spirilis on 2006-08-11
Well, got it running on a Dell Latitude D600.  Xgl refuses to run at the native 1400x1050, but it's working at 1024x768.  Not my favorite resolution but good for playing around.

I noticed a lot of scrolling has become slower; Firefox's scrolling is jumpy, xterm's scrolling was dog slow until I started compiz (and now it's acceptable).  The 3D effects are awesome though :D

I am also getting this message:
compiz.real: water: GL_ARB_fragment_program is missing

Any ideas on getting 1400x1050 and/or smoother scrolling working?

---

### Post by Paerez on 2006-08-11
I wish I knew how to get 1400x1050 working (but it would probably be much slower). I think we'll have to wait until the fglrx drivers can handle AIGLX on our Mobility cards.

---

### Post by dragonracer on 2006-08-13
Thanks for the guide. I got it to work on my Compaq nx7010 laptop
which has a radeon mobility 9200. I can get higher than 1024x768 as mine is running at the screens native resolution of 1280x800; I followed your instructions completely so I don't know why I can get a higher resolution.

Just one more thing, when I try to upgrade compiz to the latest quinn build;
ubuntu quits the session after about 8 seconds. Is there a way to get quinn working aswell?

Mark

---

### Post by Paerez on 2006-08-13
I dunno I never tried quinn. The reason you can use a higher resolution is probably because you have a 9200 and I have a 9000 >.<

---

### Post by dragonracer on 2006-08-13
I use quinn on my desktop pc and I think that it has better animations; for example the rotation of the cube also has a zoom effect. I can't get it working on my laptop so I guess it requires different settings.

Mark

---

### Post by jh0 on 2006-08-16
Hey, this guide looks great so far. I have an ATI Radeon 7000. I've been using the radeon driver for a while now with no problems. Everything works fine up until the point where I restart and try to log in with the new XGL session. I receive the following errors in the Xorg log file:

(EE) Unable to find a valid framebuffer device.
(EE) RADEON(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
(WW) RADEON(0): fbdevHwInit failed, not using framebuffer device

Later on in the file:

(EE) RADEON(0): [dri] DRIScreenInit failed.  Disabling DRI.

Manually launching Xgl to view messages results in a "no screens available" error at the end of the rest.

Any assistance would be greatly appreciated. Thanks!

---

### Post by mrojas73 on 2006-08-16
I have a compaq Presario V2000 with the ati xpress 200m graphics card.  XGL usually crashes a couple of times at logon.  After a couple of re-starts I am usually able to logon.

Anybody experiencing a similar issue?

---

### Post by kaamos on 2006-08-16
> Hey Kaamos, did you get it working fine in 1400x1050 by following my guide? Or did you change it a little? (Obviously you would have to change the lines in xorg). I can't seem to get 1400x1050 to work. How'd you do it?

I just went with your guide. Might have had some old configs from attempts to run Xgl with fglrx, but I dont think so.

---

### Post by Remix_88 on 2006-08-23
Hi,

I can confirm that I have used this guide and have my Dell D600 working with Xgl and compiz at 1280x1024 on my external LCD and 1440x1050 on the laptop's LCD.

The only differences is my xorg.conf Drivers section and I have a ~/.drirc file.

**xorg.conf**

```

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        Option          "backingstore" "true"
        Option          "EnablePageFlip" "true"
        Option          "SubPixelOrder" "none"
        Option          "AccelMethod" "XAA"
        Option          "RenderAccel" "true"
        Option          "AGPMode" "4"
        Option          "ColorTiling"   "on"
        Option          "DynamicClocks" "on"
        Option          "mtrr" "on"
        Option          "VideoOverlay" "on"
        Option          "OpenGLOverlay" "off"
EndSection

```

**~/.drirc**

These .drirc settings were taken from another topic here. They may not be suitable for everyone but you can use 'driconf' to create your own .drirc file.

[http://www.ubuntuforums.org/showthread.php?t=159252](http://www.ubuntuforums.org/showthread.php?t=159252)

```

<driconf>
    <device screen="0" driver="r200">
        <application name="Default">
            <option name="force_s3tc_enable" value="true" />
            <option name="no_rast" value="false" />
            <option name="fthrottle_mode" value="2" />
            <option name="tcl_mode" value="1" />
            <option name="texture_depth" value="0" />
            <option name="def_max_anisotropy" value="1.0" />
            <option name="texture_level_hack" value="true" />
            <option name="texture_units" value="4" />
            <option name="dither_mode" value="0" />
            <option name="hyperz" value="true" />
            <option name="round_mode" value="0" />
            <option name="arb_vertex_program" value="false" />
            <option name="allow_large_textures" value="2" />
            <option name="nv_vertex_program" value="false" />
            <option name="no_neg_lod_bias" value="false" />
            <option name="color_reduction" value="1" />
            <option name="vblank_mode" value="1" />
            <option name="texture_blend_quality" value="1.0" />
        </application>
    </device>
    <device screen="1" driver="r200">
        <application name="Default">
            <option name="force_s3tc_enable" value="true" />
            <option name="no_rast" value="false" />
            <option name="fthrottle_mode" value="2" />
            <option name="tcl_mode" value="1" />
            <option name="texture_depth" value="0" />
            <option name="def_max_anisotropy" value="1.0" />
            <option name="texture_level_hack" value="true" />
            <option name="texture_units" value="4" />
            <option name="dither_mode" value="0" />
            <option name="hyperz" value="true" />
            <option name="round_mode" value="0" />
            <option name="arb_vertex_program" value="false" />
            <option name="allow_large_textures" value="2" />
            <option name="nv_vertex_program" value="false" />
            <option name="no_neg_lod_bias" value="false" />
            <option name="color_reduction" value="1" />
            <option name="vblank_mode" value="1" />
            <option name="texture_blend_quality" value="1.0" />
        </application>
    </device>
</driconf>

```

Edit - since posting this I have found that just using the following~/.drirc is sufficient.

```

<driconf>
    <device screen="0" driver="r200">
        <application name="Default">
            <option name="allow_large_textures" value="2" />
        </application>
    </device>
</driconf>

```

I have noticed that when I use the XGL session from GDM glxinfo report that I have no direct rendering, but using the regular Gnome session glxinfo reports that I do have direct rendering. Is this normal?

---

### Post by huygens on 2006-08-25
> **Remix_88 said:**
> I can confirm that I have used this guide and have my Dell D600 working with Xgl and compiz at 1280x1024 on my external LCD and 1440x1050 on the laptop's LCD.

Cool :-) is it also usable for desktop use, or just as a demonstration for friends? (I also do have a D600)

---

### Post by didit on 2006-08-25
> **spirilis said:**
> Well, got it running on a Dell Latitude D600.  Xgl refuses to run at the native 1400x1050, but it's working at 1024x768.  Not my favorite resolution but good for playing around.

I noticed a lot of scrolling has become slower; Firefox's scrolling is jumpy, xterm's scrolling was dog slow until I started compiz (and now it's acceptable).  The 3D effects are awesome though :D

I am also getting this message:
compiz.real: water: GL_ARB_fragment_program is missing

Any ideas on getting 1400x1050 and/or smoother scrolling working?

Maybe you can change color depth from 24 bit to 16 bit in xorg.conf. It helps a lot for my acer TM800 while running AIGLX and solves partly the problem with slow scrolling in Firefox.

---

### Post by dennis2681 on 2006-08-25
i'm about halfway through your tutorial and am trying to get the compiz-vanilla package but i'm getting errors.

when i run: sudo aptitude compiz-vanilla compiz-vanilla-gnome gset-compiz xserver-xgl


i get the following error -- 
Unknown command "compiz-vanilla"
aptitude 0.4.0


any thoughts? i did have this running with the kororaa live CD so i know in theory it CAN work.... please advise.

thanks!!

---

### Post by ephraste on 2006-08-26
Hi,

i think it's just a typo try this instead:

sudo aptitude **install** compiz-vanilla compiz-vanilla-gnome gset-compiz xserver-xgl


> **dennis2681 said:**
> i'm about halfway through your tutorial and am trying to get the compiz-vanilla package but i'm getting errors.

when i run: sudo aptitude compiz-vanilla compiz-vanilla-gnome gset-compiz xserver-xgl


i get the following error -- 
Unknown command "compiz-vanilla"
aptitude 0.4.0


any thoughts? i did have this running with the kororaa live CD so i know in theory it CAN work.... please advise.

thanks!!

By the way, thanks for this great howto !!!

Just for info, for my own config
It didn't work for the Part 1, since after reboot Xorg was unable to find "radeon" driver, which was launched as said LSMOD command.:confused: 
Back to the previous config wich use "fglrx" (rendering ok) but not "radeon" driver.
Followed Part 2 and everything is fine !

Note :
i don't think its due to XGL but some times when i logout from X sessions i get a black screen and no way to reach a console :( 

Thanks again & keep the pressure

---

### Post by tjvdberg on 2006-08-26
I have a problem with the ati powersaving.

When i enter ```
aticonfig --set-powerstate=1
``` I get Error: Unable to obtain POWERplay information.

This is, I think, because of the XGL/Compiz is running on display :1 instead of :0

How can i get aticonfig to excecute on :1 ?

---

### Post by misha680 on 2006-08-27
Just type:

```
DISPLAY=:0 aticonfig --set-powerstate=1
```

works like a charm for me.

Misha

> **tjvdberg said:**
> I have a problem with the ati powersaving.

When i enter ```
aticonfig --set-powerstate=1
``` I get Error: Unable to obtain POWERplay information.

This is, I think, because of the XGL/Compiz is running on display :1 instead of :0

How can i get aticonfig to excecute on :1 ?

---

### Post by joemastro67 on 2006-08-27
After installing the radeon driver I get a "No" when I run glxinfo | grep rendering. Everything installed without error. Any suggestions on what I should check?

---

### Post by tjvdberg on 2006-08-28
> **misha680 said:**
> Just type:

```
DISPLAY=:0 aticonfig --set-powerstate=1
```

works like a charm for me.

Misha

mmm i just get ```
Error: Unable to open display `:0'.
```

Weird maybe my problem is something else.
At least I'm sure the ati drivers are loaded propperly, because of the good performace I get with compiz/XGL

---

### Post by grivad on 2006-08-30
> **Remix_88 said:**
> Hi,

I can confirm that I have used this guide and have my Dell D600 working with Xgl and compiz at 1280x1024 on my external LCD and 1440x1050 on the laptop's LCD.

The only differences is my xorg.conf Drivers section and I have a ~/.drirc file.

**xorg.conf**

```

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        Option          "backingstore" "true"
        Option          "EnablePageFlip" "true"
        Option          "SubPixelOrder" "none"
        Option          "AccelMethod" "XAA"
        Option          "RenderAccel" "true"
        Option          "AGPMode" "4"
        Option          "ColorTiling"   "on"
        Option          "DynamicClocks" "on"
        Option          "mtrr" "on"
        Option          "VideoOverlay" "on"
        Option          "OpenGLOverlay" "off"
EndSection

```

**~/.drirc**

These .drirc settings were taken from another topic here. They may not be suitable for everyone but you can use 'driconf' to create your own .drirc file.

[http://www.ubuntuforums.org/showthread.php?t=159252](http://www.ubuntuforums.org/showthread.php?t=159252)

```

<driconf>
    <device screen="0" driver="r200">
        <application name="Default">
            <option name="force_s3tc_enable" value="true" />
            <option name="no_rast" value="false" />
            <option name="fthrottle_mode" value="2" />
            <option name="tcl_mode" value="1" />
            <option name="texture_depth" value="0" />
            <option name="def_max_anisotropy" value="1.0" />
            <option name="texture_level_hack" value="true" />
            <option name="texture_units" value="4" />
            <option name="dither_mode" value="0" />
            <option name="hyperz" value="true" />
            <option name="round_mode" value="0" />
            <option name="arb_vertex_program" value="false" />
            <option name="allow_large_textures" value="2" />
            <option name="nv_vertex_program" value="false" />
            <option name="no_neg_lod_bias" value="false" />
            <option name="color_reduction" value="1" />
            <option name="vblank_mode" value="1" />
            <option name="texture_blend_quality" value="1.0" />
        </application>
    </device>
    <device screen="1" driver="r200">
        <application name="Default">
            <option name="force_s3tc_enable" value="true" />
            <option name="no_rast" value="false" />
            <option name="fthrottle_mode" value="2" />
            <option name="tcl_mode" value="1" />
            <option name="texture_depth" value="0" />
            <option name="def_max_anisotropy" value="1.0" />
            <option name="texture_level_hack" value="true" />
            <option name="texture_units" value="4" />
            <option name="dither_mode" value="0" />
            <option name="hyperz" value="true" />
            <option name="round_mode" value="0" />
            <option name="arb_vertex_program" value="false" />
            <option name="allow_large_textures" value="2" />
            <option name="nv_vertex_program" value="false" />
            <option name="no_neg_lod_bias" value="false" />
            <option name="color_reduction" value="1" />
            <option name="vblank_mode" value="1" />
            <option name="texture_blend_quality" value="1.0" />
        </application>
    </device>
</driconf>

```

Edit - since posting this I have found that just using the following~/.drirc is sufficient.

```

<driconf>
    <device screen="0" driver="r200">
        <application name="Default">
            <option name="allow_large_textures" value="2" />
        </application>
    </device>
</driconf>

```

I have noticed that when I use the XGL session from GDM glxinfo report that I have no direct rendering, but using the regular Gnome session glxinfo reports that I do have direct rendering. Is this normal?

Thanks for the tips.. I have a Latitude D600 (ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]) as well and have been struggling to get compiz to work.

I have gotten XGL to work by changing the display to :0 in startxgl.sh.  My glxinfo spits out:

```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control,
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control,
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x TCL
OpenGL version string: 1.3 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix,
    GL_ARB_vertex_buffer_object, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_equation_separate,
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution,
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord,
    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_polygon_offset,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate,
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once,
    GL_ATI_fragment_shader, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
    GL_MESA_pack_invert, GL_MESA_window_pos, GL_NV_blend_square,
    GL_NV_light_max_exponent, GL_NV_texture_rectangle,
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix,
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x4b 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

I have tried your settings as well as the settings in the original walkthrough, however, when I run 'startcompiz', the terminal spits out an error (that I can't read cause it's too fast), gnome crashes, and it kicks me out to login again.

Could you post your 'startcompiz'?

---

### Post by Paerez on 2006-08-31
Hey I updated the guide to include the drirc stuff, and I have it successfully running at 1400x1050 on my inspiron 600m (very similar to latitude 600) with the Radeon Mobility 9000, same as you. All of my settings are described in the guide. I would give the guide another shot, since there have been some pretty solid changes in the past month.

---

### Post by grivad on 2006-08-31
Yeh, thanks!  I got it to work at all resolutions, actually, right after my last post, albeit with issues.  Basically, opening certain programs or windows causes the screen to "blank out" or fill with garbage of a solid color around said opened window, until I basically rotate the box or make it do something else that involves the full screen.  Anyone else have this issue?

---

### Post by Paerez on 2006-08-31
Yeah i have that too. Also, I found that going through the gconf-editor options for compiz and disabling mipmaps improved performance (at the cost of good-lookingness).

Also firefox destroys performance. I had to go through the gconf-editors to restore all my shortcuts, which was a bit annoying, but now I have it all going.

---

### Post by VCSkier on 2006-09-01
wonderful!  thanks so much.  this is the first guide i have been able to follow to get my mobility card working at all!  not to mention compiz is actually working.  my computer isn't powerful enough to run it smoothly by any means; its still not practical for daily use, but its fun to play with.  thanks a million times 2!  :)

---

### Post by Xeifer on 2006-09-01
Will this work with a Radeon Xpress 200M?

---

### Post by NoTiG on 2006-09-01
when i add the enable compositing extension in the xorg.conf file.. i cant even boot x anymore. it just keeps restarting. so i guessno xgl for me....... .

however im happy to have direct rendering now. my glxgears now actually works. im going to do some benchmarks .

---

### Post by proagg on 2006-09-02
I also get a BIG NO:mad:  to direct rendering after following the directions after a clean install. Help!! Help!! Help!!](*,)

Edit: I tried the symlink mentioned a few pages back with no change

Running dapper on Radeon 200m

my xorg.conf is exactly like the model.
also, I CREATED the ~/.drirc file, not edited as described. I don't know if this is good or bad.

---

### Post by shoyer on 2006-09-02
> **Paerez said:**
> Hey I updated the guide to include the drirc stuff, and I have it successfully running at 1400x1050 on my inspiron 600m (very similar to latitude 600) with the Radeon Mobility 9000, same as you. All of my settings are described in the guide. I would give the guide another shot, since there have been some pretty solid changes in the past month.
Well, it's not quite there yet for me. I have a Dell Latitude D600, quite similar to your 600m as mentioned, and I just installed Ubuntu from scratch tonight.

When I attempt to login to an XGL session, I see a brown background and then get an error message that my desktop failed to load in less than 10 seconds. The error is as follows:

```
Fatal server error:
no screens found

(gnome-session: 5203): Gtk-WARNING **: cannot open display
```

Thanks for your help.

---

### Post by mrojas73 on 2006-09-02
> **Xeifer said:**
> Will this work with a Radeon Xpress 200M?

Mine is somehow problematic, I get lockups when login to xgl, and I have used just about any trick I found on the web. 

The instructions on the following link are great,  I would do the second one which is halfway down the page.  

[http://www.compiz.net/topic-389-compiz-gnome](http://www.compiz.net/topic-389-compiz-gnome)

---

### Post by Personatech on 2006-09-03
Hi,
Thanks for this How-To:  it's the closest I've gotten to getting XGL to run on my Dell Latitude C610 (which has 16M Radeon Mobility 9000).  The problems I have are as follows:

1) Moving a window leaves echos on the background (very Daliesque and actually quite cool-looking, but not desired).
2) Gnome menu not displayed.
3) Gnome panels extend across only half the screen.  (Max resolution is set to 1024x768.)
4) Desktop background extends about halfway across sceen and 2/3 way down.

Any ideas on how to fix these?  

Tom Eisenmenger

---

### Post by corpse89 on 2006-09-04
Thankyou so much for posting a easy to follow guide that actually works on my ati mobility 9000.

---

### Post by Paerez on 2006-09-04
> **Personatech said:**
> Hi,
Thanks for this How-To:  it's the closest I've gotten to getting XGL to run on my Dell Latitude C610 (which has 16M Radeon Mobility 9000).  The problems I have are as follows:

1) Moving a window leaves echos on the background (very Daliesque and actually quite cool-looking, but not desired).
2) Gnome menu not displayed.
3) Gnome panels extend across only half the screen.  (Max resolution is set to 1024x768.)
4) Desktop background extends about halfway across sceen and 2/3 way down.

Any ideas on how to fix these?  

Tom Eisenmenger

So basically what you are saying is that your screen is 1400x1050, but there is a 1024x768 screen in the top left, and everything beyond the border of the 1024x768 section is really weirded out.

This is what happened to me until I added the radeon stuff in the xorg.conf (all the Options) and created my .drirc.

If you edit your xorg.conf and remove all resolutions above 1024x768, and then log in and set your resolution to 1024x768, then log out and back in, does the problem still exist?

---

### Post by misha680 on 2006-09-05
Hmm... you know this might be because I start mine from a .Xsession file, not sure though. But that would be one option if you really want to be able to use powerplay, etc.

Misha

> **tjvdberg said:**
> mmm i just get ```
Error: Unable to open display `:0'.
```

Weird maybe my problem is something else.
At least I'm sure the ati drivers are loaded propperly, because of the good performace I get with compiz/XGL

---

### Post by Quickdood on 2006-09-05
Hi, I followed the steps outlined by the how to.  I started to follow the steps from step 2 because I had a fresh install and I did the tests to see if I could start from step 2 and it worked.

Everything went well, but when I log onto the XGL session, it crashes.  It says something about a xsession error.  There is an error log that is displayed but I have no Idea how to copy it because I have to restart ubuntu.  Does anyone know how to access an error log file after a reboot?

When I log into the normal session I see compiz is working in my task bar but it won't enable.  I am new to linux so if you choose to help me please be very detailed in your answer.  Thanks!

---

### Post by LordCK on 2006-09-06
Yet another Dell Latitude D600!

I have tried and tried this thing all day, and this is where I am right now.

- I run my X.org at 1400x1050 (If I try a lower resolution, the only result is a blank screen) with DefaultDepth 24 - Then I'm able to start Xgl with -screen 1024x768 so I get the "desktop" in the upper left corner of the screen. If I try to increase the resolution (e.g. 1025x768, 1280x1024 or fullscreen), I get "No screens found" in the Logfiles. If I try to decrease this value (like 1023x768 ), it works perfectly so it seems like this is some kind of a maximum.

- I start the X.org at 1400x1050 with DefaultDepth 16 - I am able to start  Xgl with the -fullscreen switch, but now all I see is black fields all over the desktop... I see the effects of desktop-switching, but since the menu etc is black, I can't use this settings.

Anyone of you guys got this thing working with the radeon 9000 have any tips?

---

### Post by VCSkier on 2006-09-08
which of the steps from part one of your guide are xgl/compiz specific, and which are recommended for simply setting up the ati mobility radeon drivers?  i am currently no longer interested in installing compiz, but would still like my gpu's latest drivers installed properly.  fglrx does not work on my system for some reason.

---

### Post by bartman on 2006-09-08
Try this script:[http://www.ubuntuforums.org/showthread.php?t=235145"]("http://www.ubuntuforums.org/showthread.php?t=235145). 
It worked wonders for my FireGL V5000 (X700).

---

### Post by huygens on 2006-09-08
Great day :-) this is working for my laptop, while all that I tried before did not work (including Kororaa!)
Thanks a lot :D

Huygens

---

### Post by huygens on 2006-09-11
> **LordCK said:**
> Yet another Dell Latitude D600!
[...]
Anyone of you guys got this thing working with the radeon 9000 have any tips?


I have a Dell Latitude D600 with an ATI Radeon Mobility 9000, and I manage to make it work thanks to this how-to. However, eventhough I had the prerequist that said "skip to step 2", I had to do most parts of step 1 to make it work, because you do not get the correct repository, you do not have the correct xorg.conf and modules loaded.
So try to do all the steps mentionned eventhough it is specified to skip them or that in most case it is done automatically, because with our hardware, it is a hardwork ;-) and does not do much magic. So for instance, you need to manually launch compiz, won't start by itself.

After that I have Xgl working, with some bogus display from time to time like the title bar disapearing, but if you put the mouse over, it come back to display, etc. Also, when I get notified of an update the computer is completly stuck! Not a single key event is executed by the system, so no soft reboot possible, only power off power on :-(
But the rest is OK, usable eventhough you can see that this is still under development.

Huygens

---

### Post by daan_franken on 2006-09-12
I solved the Radeon Mobility issue (the half screen issue) on my latitude c610 (radeon m6 LY) by entering 
Option   "AGPSize" "32"
in the "Device" section of xorg.conf, along with the other options listed in the tutorial. 
Thanks for the tutorial!

---

### Post by des4ij on 2006-09-21
hey how come i get direct rendering in default gnome session but not in xgl session... is there something i need to add to the xgl.desktop file...

---

### Post by kikos on 2006-09-26
I used this guide to get Compiz working on my Thinkpad X31 with ATI Radeon Mobility M6 LY.  The card only has 16MB of RAM.

I have two issues that hopefully someone can shed some light on:

1)  If I attempt to login to an XGL session, the session appears to begin, but abruptly terminates and reloads the login screen.  Does anyone know what the problem is?  What log file would I look at for clues?

2)  While running the normal Gnome (non-XGL) session, I can open up the terminal and compiz-start.  Compiz starts and looks pretty good.  However, window creation, movement, and termination is very slow.  This might be due to my very little 16MB of video RAM.  However, is this slowness possibly due to not running Compiz in an XGL session?

Thanks

---

### Post by kikos on 2006-09-26
By reading some discussions, I discovered that the sluggishness of compiz was due to a high CPU load.  At idle, my CPU load was 90% !!

My CPU load is now at 10% because I disabled two compiz plugins:  1) The "crash handler" & 2) "Blur"

Compiz now runs fairly smooth on my laptop

---

### Post by Paerez on 2006-09-26
I turn off blur too. I can't see the difference and it makes things go way faster.

---

### Post by pau on 2006-09-29
Hi,

I followed your instructions step by step, have 3d acceleration but when I choose the gnome-xgl session get no xgl effects and all X applications are increeeeedibly sloooooooooow... Any hint???

---

### Post by pau on 2006-10-01
I don't understand anything... I followed the instructions but now apt-get doesn't find cgwd cgwd-themes... When I do

```
sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome cgwd cgwd-themes
```

then I get 

```
Reading package lists... Done
Building dependency tree... Done
xserver-xgl is already the newest version.
libgl1-mesa is already the newest version.
xserver-xorg is already the newest version.
libglitz-glx1 is already the newest version.
Note, selecting emerald instead of cgwd
Package cgwd-themes is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  emerald-themes
E: Package cgwd-themes has no installation candidate
```

My sources.list looks like this

```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/plf dapper free non-free
deb-src http://packages.freecontrib.org/plf dapper free non-free
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main

## AUTOMATIX
deb http://www.getautomatix.com/apt dapper main

## SKYPE
deb http://download.skype.com/linux/repos/debian/ stable non-free

# Repository for wine
deb http://wine.budgetdedicated.com/apt dapper main
deb-src http://wine.budgetdedicated.com/apt dapper main

# engage
deb http://soulmachine.net/breezy/ unstable/

# XGL
deb http://www.beerorkid.com/compiz dapper main
deb http://media.blutkind.org/xgl/ dapper main
deb http://compiz-mirror.lupine.me.uk/ dapper main
deb http://ubuntu.compiz.net/ dapper main


# Moblock
deb http://moblock-deb.sourceforge.net/debian unstable main
deb-src http://moblock-deb.sourceforge.net/debian unstable main
```

and I believe this is the problem. Without cgwd xgl seems not to work. When I select the session gnome-xgl I just get a blank screen and the famous "your session has lasted more than 10 sec" and then I am logged out

What can I do?

---

### Post by pau on 2006-10-01
By the way, I solved the 3d acceleration issue...

---

### Post by Dangling on 2006-10-01
Thanks for the guide. I always wanted to try out xgl/compiz, but I'm having some problems. For some reason, compiz doesn't install. It says that the compiz-plugins package is broken. I get the following :
```

```
```
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  compiz-plugins
The following NEW packages will be automatically installed:
  compiz-core compiz-gnome
The following NEW packages will be installed:
  compiz compiz-core compiz-gnome
0 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 1709kB of archives. After unpacking 4078kB will be used.
The following packages have unmet dependencies:
  compiz-plugins: Depends: compiz-core (>= 0.0.13.54) but 0.0.13.38-0ubuntu3 is to be installed.
                  Depends: csm (>= 0.5) which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
compiz [Not Installed]
compiz-plugins [Not Installed]

Score is 8

Accept this solution? [Y/n/q/?]

```

Thanks in advance.

---

### Post by edemark on 2006-10-03
I too have problems with installing compiz it sais that compiz depends on compiz-plugins that is not installable as csm is not installable 

What am i doing wrong?
thanks for the help

---

### Post by kuriharu on 2006-10-16
Same issue here. Compiz needs version 0.0.13.54 of compiz-plugins, but it's not available.

The point of using apt-get is so it can meet dependencies, but this package doesn't seem to be avaialble for Ubuntu.

Fun.](*,)

---

### Post by Dangling on 2006-10-17
I gave up on compiz and switched to Beryl... It seems more actively supported in the Ubuntu community and there's plenty of threads on it. It's not that difficult.

Although I did get Beryl to work, it wasn't very pretty since I have a ATI card. Still, it was fun to play around with it for a while.

---

### Post by Paerez on 2006-10-17
Sorry I haven't been much help recently guys. I don't use compiz on my laptop anymore since I have been taking it to school and I need it to have good battery life.

Beryl seems like the best route right now, and I am going to update the howto to mention it.

---

### Post by lifemaximum on 2006-10-18
Dude i used your howto to install beryl... i did the first part now my xserver everytime it loads it shuts down...i mean i can see the desktop and all the icons after the load and than suddenly xserver shuts down.

 i tried 

```
sudo dpkg-reconfigure xserver-xorg
``` to reconfigure it .... no luck ...

what should i do now??? help ](*,)

---

### Post by Paerez on 2006-10-18
run:
```
sudo aptitude remove beryl
```
that should put you back to normal, then we can try to figure out whats wrong.

---

### Post by lifemaximum on 2006-10-19
i dun think it is beryl
i think it mite have something to do with gdm file which i modified ....how can i get it back again ???

---

### Post by gstevens on 2006-10-19
I am new to linux, and I followed all the steps according to this thread  (and checked for errors many times),  and when I try logging in via xgl session, I get the following error message, "No Exec line in session file .xgl"  and it proceeds to run gnome failsafe.  What should I do to fix this and get xgl running?  Any help would be greatly appreciated.

---

### Post by Paerez on 2006-10-20
lifemaximum: the fact that it gets all the way to the desktop means that gdm has successfully run X, and also gnome is running too. But then it tries to load beryl automatically, which crashes X. Did you try removing beryl?

gstevens: this guide isn't doing so well since the switch to beryl, and I haven't checked it in a while since I don't use it. That said, here is my suggestion:

make sure that "/usr/share/xsessions/xgl.desktop" contains exactly this:
```
[Desktop Entry]
Encoding=UTF-8
Name=XGL
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application
```
see the Exec line? Thats what it is complaining about, so make sure it is correct.

---

### Post by Personatech on 2006-11-01
> **Paerez said:**
> So basically what you are saying is that your screen is 1400x1050, but there is a 1024x768 screen in the top left, and everything beyond the border of the 1024x768 section is really weirded out.

This is what happened to me until I added the radeon stuff in the xorg.conf (all the Options) and created my .drirc.

If you edit your xorg.conf and remove all resolutions above 1024x768, and then log in and set your resolution to 1024x768, then log out and back in, does the problem still exist?
Actually, my screen is 1024x768 (Dell's "bargain" LCD) and xorg.conf seems to be configured properly.  I'd also set the options as described in the HOWTO and switched to the "radeon" driver.  I do suspect that it may be an options issue - I may have to fiddle with those a bit...

---

### Post by edemark on 2006-11-01
Hi all 

So I was able to install beryl (while i was unable to install compiz because of some missing files). I followed the tutorial from the second part, as i have always used the radeon driver. Now when I log in to the xgl session everything is black or almost black. I can open the menu (I see it is opening) but i cannot read the items as they all black. In the same way i see that there is a splash screen but it is also black. 
Any ideas how can i make it work properly? 
thanks

Ok I have tried out with switching to screen 0 from screen 1. Now when i log in i do not get the black screen as on screen 1 but, even though i do not get any error messages, i just do not see any xgl effect working,

any ideas?

---

### Post by edemark on 2006-11-02
I have tried to run beryl when in the xgl sesion on screen 0 (which is not black) and i get the following message:
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension

any ideas? please

---

### Post by Paerez on 2006-11-02
That means either you are not running XGL. Try the new guide I linked to at the top of the guide.

I am currently running Beryl beatifully and fast on my Dell 600m with a 9000 Mobility card with edgy's fglrx driver. I may write a guide for that too.

---

### Post by ofir_k on 2006-11-02
Hello,

If I run "glxinfo | grep rendering" and it gives me "Yes", but "lsmod | grep radeon" doesn't list anything, what I need to do?

Regards,
Ofir

---

### Post by edemark on 2006-11-02
OK but my problem would be that my graphic card is not supported by the fglrx driver. So what next? Is there any way to get xgl work? In Kororaa it was working.
thanks anyway

---

### Post by Paerez on 2006-11-02
Were you able to get it to say "Direct Rendering: Yes" with the radeon driver in normal X? If so, then you need to make sure you are running XGL using the session.

---

### Post by edemark on 2006-11-02
Yes i have direct rendering working in normal x session. 
Might there be anything i shall check from the first part of the how to?
thanks

---

### Post by Paerez on 2006-11-03
The problem is that I dont even know if this guide works any more. I got beryl to work on my Mobility 9000 using this guide:
[http://www.ubuntuforums.org/showthread.php?t=291464](http://www.ubuntuforums.org/showthread.php?t=291464)

---

### Post by edemark on 2006-11-03
Thanks anyway

I shall then search all around if there is any resolution for my problem. Sadly the other guide will not help me as my card is not supported by the fglrx driver (I have an ati radeon igp 345M)
thanks anyway ( I feel that I am not so far from gwtting xgl to work)

---

### Post by Fittersman on 2006-11-09
undo the effects?!?!? how can i? i started another thread 

[http://ubuntuforums.org/showthread.php?p=1734325#post1734325](http://ubuntuforums.org/showthread.php?p=1734325#post1734325)

PLEASE HELP!!!

---

### Post by dayoflayo on 2006-11-10
Hi, i've tried to install the radeon driver but i don't get the direct rendering.
here's my xorg.conf and xorg.0.log

**xkorg.conf**

```


Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver "radeon"
	Option	  "backingstore" "true"
	Option	  "EnablePageFlip" "true"
	Option	  "SubPixelOrder" "none"
	Option	  "AccelMethod" "XAA"
	Option	  "RenderAccel" "true"
	Option	  "AGPMode" "4"
	Option	  "ColorTiling"   "on"
	Option	  "DynamicClocks" "on"
	Option	  "mtrr" "on"	
	Option "VideoOverlay" "on"
        Option "OpenGLOverlay" "off"
	EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
 	Option "Composite" "Enable"
EndSection

```

**xorg.0.log**

```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux dayoflayo-laptop 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Nov 10 10:53:59 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7


(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000dfff (0x2000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0x90000000 - 0x9fffffff (0x10000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (0:16:0), (0,3,6), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[1] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0x42000000 - 0x43ffffff (0x2000000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0x40000000 - 0x41ffffff (0x2000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:25:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
	[4] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[5] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[6] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[7] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xb8000000 - 0xbfffffff (0x8000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x88000000 - 0x8fffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:30:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:5:0) ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE) rev 0, Mem @ 0x90000000/28, 0xc0000000/16, I/O @ 0xc000/8
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xd000c000 - 0xd000ffff (0x4000) MX[B]
	[1] -1	0	0x44003000 - 0x440030ff (0x100) MX[B]
	[2] -1	0	0xf8004000 - 0xf8004fff (0x1000) MX[B]
	[3] -1	0	0xf8003000 - 0xf8003fff (0x1000) MX[B]
	[4] -1	0	0xf8002000 - 0xf8002fff (0x1000) MX[B]
	[5] -1	0	0xd000a300 - 0xd000a3ff (0x100) MX[B]
	[6] -1	0	0x44000000 - 0x44001fff (0x2000) MX[B]
	[7] -1	0	0xd000a200 - 0xd000a2ff (0x100) MX[B]
	[8] -1	0	0xd000a100 - 0xd000a1ff (0x100) MX[B]
	[9] -1	0	0xd000a000 - 0xd000a0ff (0x100) MX[B]
	[10] -1	0	0xd0008000 - 0xd0009fff (0x2000) MX[B]
	[11] -1	0	0xd0004000 - 0xd0007fff (0x4000) MX[B]
	[12] -1	0	0xd0000000 - 0xd00007ff (0x800) MX[B]
	[13] -1	0	0xc0000000 - 0xc000ffff (0x10000) MX[B](B)
	[14] -1	0	0x90000000 - 0x9fffffff (0x10000000) MX[B](B)
	[15] -1	0	0x00001100 - 0x0000110f (0x10) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[17] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd000c000 - 0xd000ffff (0x4000) MX[B]
	[1] -1	0	0x44003000 - 0x440030ff (0x100) MX[B]
	[2] -1	0	0xf8004000 - 0xf8004fff (0x1000) MX[B]
	[3] -1	0	0xf8003000 - 0xf8003fff (0x1000) MX[B]
	[4] -1	0	0xf8002000 - 0xf8002fff (0x1000) MX[B]
	[5] -1	0	0xd000a300 - 0xd000a3ff (0x100) MX[B]
	[6] -1	0	0x44000000 - 0x44001fff (0x2000) MX[B]
	[7] -1	0	0xd000a200 - 0xd000a2ff (0x100) MX[B]
	[8] -1	0	0xd000a100 - 0xd000a1ff (0x100) MX[B]
	[9] -1	0	0xd000a000 - 0xd000a0ff (0x100) MX[B]
	[10] -1	0	0xd0008000 - 0xd0009fff (0x2000) MX[B]
	[11] -1	0	0xd0004000 - 0xd0007fff (0x4000) MX[B]
	[12] -1	0	0xd0000000 - 0xd00007ff (0x800) MX[B]
	[13] -1	0	0xc0000000 - 0xc000ffff (0x10000) MX[B](B)
	[14] -1	0	0x90000000 - 0x9fffffff (0x10000000) MX[B](B)
	[15] -1	0	0x00001100 - 0x0000110f (0x10) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[17] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd000c000 - 0xd000ffff (0x4000) MX[B]
	[5] -1	0	0x44003000 - 0x440030ff (0x100) MX[B]
	[6] -1	0	0xf8004000 - 0xf8004fff (0x1000) MX[B]
	[7] -1	0	0xf8003000 - 0xf8003fff (0x1000) MX[B]
	[8] -1	0	0xf8002000 - 0xf8002fff (0x1000) MX[B]
	[9] -1	0	0xd000a300 - 0xd000a3ff (0x100) MX[B]
	[10] -1	0	0x44000000 - 0x44001fff (0x2000) MX[B]
	[11] -1	0	0xd000a200 - 0xd000a2ff (0x100) MX[B]
	[12] -1	0	0xd000a100 - 0xd000a1ff (0x100) MX[B]
	[13] -1	0	0xd000a000 - 0xd000a0ff (0x100) MX[B]
	[14] -1	0	0xd0008000 - 0xd0009fff (0x2000) MX[B]
	[15] -1	0	0xd0004000 - 0xd0007fff (0x4000) MX[B]
	[16] -1	0	0xd0000000 - 0xd00007ff (0x800) MX[B]
	[17] -1	0	0xc0000000 - 0xc000ffff (0x10000) MX[B](B)
	[18] -1	0	0x90000000 - 0x9fffffff (0x10000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00001100 - 0x0000110f (0x10) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[23] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 4.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 6.6.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) ATI: ATI driver (version 6.6.2) for chipsets: ati, ativga
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (AGP?), ATI Rage 128 Pro GL PB (AGP?),
	ATI Rage 128 Pro GL PC (AGP?), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (AGP?), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (AGP?), ATI Rage 128 Pro VR PH (AGP?),
	ATI Rage 128 Pro VR PI (AGP?), ATI Rage 128 Pro VR PJ (AGP?),
	ATI Rage 128 Pro VR PK (AGP?), ATI Rage 128 Pro VR PL (AGP?),
	ATI Rage 128 Pro VR PM (AGP?), ATI Rage 128 Pro VR PN (AGP?),
	ATI Rage 128 Pro VR PO (AGP?), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (AGP?), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (AGP?), ATI Rage 128 Pro VR PT (AGP?),
	ATI Rage 128 Pro VR PU (AGP?), ATI Rage 128 Pro VR PV (AGP?),
	ATI Rage 128 Pro VR PW (AGP?), ATI Rage 128 Pro VR PX (AGP?),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (AGP?),
	ATI Rage 128 4X SF (AGP?), ATI Rage 128 4X SG (AGP?),
	ATI Rage 128 4X SH (AGP?), ATI Rage 128 4X SK (AGP?),
	ATI Rage 128 4X SL (AGP?), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (AGP?), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Radeon X800 (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 XTP (R430) (PCIE),
	ATI Radeon X850 5D4C (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(II) Primary Device is: PCI 01:05:0
(--) Assigning device section with no busID to primary device
(--) Chipset ATI Radeon XPRESS 200M 5955 (PCIE) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd000c000 - 0xd000ffff (0x4000) MX[B]
	[5] -1	0	0x44003000 - 0x440030ff (0x100) MX[B]
	[6] -1	0	0xf8004000 - 0xf8004fff (0x1000) MX[B]
	[7] -1	0	0xf8003000 - 0xf8003fff (0x1000) MX[B]
	[8] -1	0	0xf8002000 - 0xf8002fff (0x1000) MX[B]
	[9] -1	0	0xd000a300 - 0xd000a3ff (0x100) MX[B]
	[10] -1	0	0x44000000 - 0x44001fff (0x2000) MX[B]
	[11] -1	0	0xd000a200 - 0xd000a2ff (0x100) MX[B]
	[12] -1	0	0xd000a100 - 0xd000a1ff (0x100) MX[B]
	[13] -1	0	0xd000a000 - 0xd000a0ff (0x100) MX[B]
	[14] -1	0	0xd0008000 - 0xd0009fff (0x2000) MX[B]
	[15] -1	0	0xd0004000 - 0xd0007fff (0x4000) MX[B]
	[16] -1	0	0xd0000000 - 0xd00007ff (0x800) MX[B]
	[17] -1	0	0xc0000000 - 0xc000ffff (0x10000) MX[B](B)
	[18] -1	0	0x90000000 - 0x9fffffff (0x10000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00001100 - 0x0000110f (0x10) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[23] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Reloading /usr/lib/xorg/modules/drivers/radeon_drv.so
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd000c000 - 0xd000ffff (0x4000) MX[B]
	[5] -1	0	0x44003000 - 0x440030ff (0x100) MX[B]
	[6] -1	0	0xf8004000 - 0xf8004fff (0x1000) MX[B]
	[7] -1	0	0xf8003000 - 0xf8003fff (0x1000) MX[B]
	[8] -1	0	0xf8002000 - 0xf8002fff (0x1000) MX[B]
	[9] -1	0	0xd000a300 - 0xd000a3ff (0x100) MX[B]
	[10] -1	0	0x44000000 - 0x44001fff (0x2000) MX[B]
	[11] -1	0	0xd000a200 - 0xd000a2ff (0x100) MX[B]
	[12] -1	0	0xd000a100 - 0xd000a1ff (0x100) MX[B]
	[13] -1	0	0xd000a000 - 0xd000a0ff (0x100) MX[B]
	[14] -1	0	0xd0008000 - 0xd0009fff (0x2000) MX[B]
	[15] -1	0	0xd0004000 - 0xd0007fff (0x4000) MX[B]
	[16] -1	0	0xd0000000 - 0xd00007ff (0x800) MX[B]
	[17] -1	0	0xc0000000 - 0xc000ffff (0x10000) MX[B](B)
	[18] -1	0	0x90000000 - 0x9fffffff (0x10000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x00001100 - 0x0000110f (0x10) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[26] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[27] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[28] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) RADEON(0): RADEONPreInit
(II) RADEON(0): MMIO registers at 0xc0000000: size 64KB
(II) RADEON(0): PCI bus 1 card 5 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(**) RADEON(0): Option "AGPMode" "4"
(**) RADEON(0): Option "EnablePageFlip" "true"
(**) RADEON(0): Option "ColorTiling" "on"
(**) RADEON(0): Option "RenderAccel" "true"
(**) RADEON(0): Option "SubPixelOrder" "none"
(**) RADEON(0): Option "DynamicClocks" "on"
(**) RADEON(0): Option "AccelMethod" "XAA"
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(==) RADEON(0): X server will not keep DPI constant for all screen sizes
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(**) RADEON(0): Option "mtrr" "on"
(--) RADEON(0): Chipset: "ATI Radeon XPRESS 200M 5955 (PCIE)" (ChipID = 0x5955)
(--) RADEON(0): Linear framebuffer at 0x90000000
(II) RADEON(0): PCI card detected
(II) RADEON(0): Direct rendering broken on XPRESS 200 and 200M
(II) RADEON(0): Detected total video RAM=131072K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 131072 kByte (64 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules/libi2c.so
(II) RADEON(0): I2C bus "DDC" initialized.
(II) RADEON(0): Legacy BIOS detected
(II) RADEON(0): LVDS port is not in connector table, added in.
(WW) RADEON(0): Unknown DDCType 5 found
(WW) RADEON(0): LCD DDC Info Table found!
(II) RADEON(0): Connector0: DDCType-0, DACType-1, TMDSType--1, ConnectorType-1
(II) RADEON(0): Connector1: DDCType-4, DACType-0, TMDSType--1, ConnectorType-2
(II) RADEON(0): DDC Type: 4, Detected Type: 0
(II) RADEON(0): 
(II) RADEON(0): Primary:
 Monitor   -- LVDS
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- CRT2_DDC
(II) RADEON(0): Secondary:
 Monitor   -- NONE
 Connector -- Proprietary
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- NONE
 DDC Type  -- NONE
(II) RADEON(0): PLL parameters: rf=1432 rd=6 min=20000 max=40000; xclk=16600
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEON(0): Validating modes on Primary head ---------
(II) RADEON(0): Panel ID string: LP171W01                
(II) RADEON(0): Panel Size from BIOS: 1440x900
(II) RADEON(0): BIOS provided dividers will be used.
(II) RADEON(0): Total number of valid DDC mode(s) found: 0
(II) RADEON(0): Valid mode using on-chip RMX: 1440x900
(II) RADEON(0): Valid mode using on-chip RMX: 1024x768
(II) RADEON(0): Valid mode using on-chip RMX: 800x600
(II) RADEON(0): Valid mode using on-chip RMX: 640x480
(II) RADEON(0): Total number of valid FP mode(s) found: 4
(--) RADEON(0): Virtual size is 1440x900 (pitch 1472)
(**) RADEON(0): *Mode "1440x900": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 59.9 Hz
(II) RADEON(0): Modeline "1440x900"   96.21  1440 1504 1536 1760  900 903 906 912
(**) RADEON(0): *Mode "1024x768": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 59.9 Hz
(II) RADEON(0): Modeline "1024x768"   96.21  1024 1504 1536 1760  768 903 906 912
(**) RADEON(0): *Mode "800x600": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 59.9 Hz
(II) RADEON(0): Modeline "800x600"   96.21  800 1504 1536 1760  600 903 906 912
(**) RADEON(0): *Mode "640x480": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 59.9 Hz
(II) RADEON(0): Modeline "640x480"   96.21  640 1504 1536 1760  480 903 906 912
(**) RADEON(0):  Default mode "640x350": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 59.9 Hz
(II) RADEON(0): Modeline "640x350"   96.21  640 1504 1536 1760  350 903 906 912
(**) RADEON(0):  Default mode "640x400": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 59.9 Hz
(II) RADEON(0): Modeline "640x400"   96.21  640 1504 1536 1760  400 903 906 912
(**) RADEON(0):  Default mode "720x400": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 59.9 Hz
(II) RADEON(0): Modeline "720x400"   96.21  720 1504 1536 1760  400 903 906 912
(**) RADEON(0):  Default mode "1152x864": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 59.9 Hz
(II) RADEON(0): Modeline "1152x864"   96.21  1152 1504 1536 1760  864 903 906 912
(**) RADEON(0):  Default mode "832x624": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 59.9 Hz
(II) RADEON(0): Modeline "832x624"   96.21  832 1504 1536 1760  624 903 906 912
(**) RADEON(0):  Default mode "1280x768": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 59.9 Hz
(II) RADEON(0): Modeline "1280x768"   96.21  1280 1504 1536 1760  768 903 906 912
(**) RADEON(0):  Default mode "1280x800": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 59.9 Hz
(II) RADEON(0): Modeline "1280x800"   96.21  1280 1504 1536 1760  800 903 906 912
(**) RADEON(0):  Default mode "1152x768": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 59.9 Hz
(II) RADEON(0): Modeline "1152x768"   96.21  1152 1504 1536 1760  768 903 906 912
(==) RADEON(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(**) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xc0000000 - 0xc000ffff (0x10000) MX[B]
	[1] 0	0	0x90000000 - 0x9fffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xd000c000 - 0xd000ffff (0x4000) MX[B]
	[7] -1	0	0x44003000 - 0x440030ff (0x100) MX[B]
	[8] -1	0	0xf8004000 - 0xf8004fff (0x1000) MX[B]
	[9] -1	0	0xf8003000 - 0xf8003fff (0x1000) MX[B]
	[10] -1	0	0xf8002000 - 0xf8002fff (0x1000) MX[B]
	[11] -1	0	0xd000a300 - 0xd000a3ff (0x100) MX[B]
	[12] -1	0	0x44000000 - 0x44001fff (0x2000) MX[B]
	[13] -1	0	0xd000a200 - 0xd000a2ff (0x100) MX[B]
	[14] -1	0	0xd000a100 - 0xd000a1ff (0x100) MX[B]
	[15] -1	0	0xd000a000 - 0xd000a0ff (0x100) MX[B]
	[16] -1	0	0xd0008000 - 0xd0009fff (0x2000) MX[B]
	[17] -1	0	0xd0004000 - 0xd0007fff (0x4000) MX[B]
	[18] -1	0	0xd0000000 - 0xd00007ff (0x800) MX[B]
	[19] -1	0	0xc0000000 - 0xc000ffff (0x10000) MX[B](B)
	[20] -1	0	0x90000000 - 0x9fffffff (0x10000000) MX[B](B)
	[21] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[22] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[23] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[24] 0	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[27] -1	0	0x00001100 - 0x0000110f (0x10) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[29] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[30] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[31] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(**) RADEON(0): RADEONScreenInit 90000000 0
(**) RADEON(0): Map: 0x90000000, 0x08000000
(**) RADEON(0): Write-combining range (0x90000000,0x8000000)
(**) RADEON(0): RADEONSave
(**) RADEON(0): RADEONSaveMode(0x81fe0d0)
(**) RADEON(0): Read: 0x00180006 0x00040079 0x00000000
(**) RADEON(0): Read: rd=6, fd=121, pd=4
(**) RADEON(0): RADEONSaveMode returns 0x81fe0d0
(II) RADEON(0): Dynamic Clock Scaling Enabled
(**) RADEON(0): RADEONInitMemoryMap() : 
(**) RADEON(0):   mem_size         : 0x08000000
(**) RADEON(0):   MC_FB_LOCATION   : 0x3fff3800
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0): RADEONModeInit()
1440x900       96.21  1440 1504 1536 1760   900  903  906  912 (24,32)
1440x900       96.21  1440 1504 1536 1760   900  903  906  912 (24,32)
(**) RADEON(0): Pitch = 12058808 bytes (virtualX = 1440, displayWidth = 1472)
(II) RADEON(0): BIOS HotKeys Enabled
(**) RADEON(0): RADEONInit returns 0x81fea80
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81fea80)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0x3fff3800
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): GRPH_BUFFER_CNTL from 20004c4c to 20287c7c
(**) RADEON(0): RADEONSaveScreen(0)
(II) RADEON(0): Depth moves disabled by default
(**) RADEON(0): Setting up initial surfaces
(**) RADEON(0): Initializing fb layer
(**) RADEON(0): Setting up accel memmap
(II) RADEON(0): Memory manager initialized to (0,0) (1472,8191)
(II) RADEON(0): Reserved area from (0,900) to (1472,914)
(II) RADEON(0): Largest offscreen area available: 1472 x 7277
(**) RADEON(0): Initializing backing store
(**) RADEON(0): Option "BackingStore" "true"
(**) RADEON(0): Backing store enabled
(WW) RADEON(0): Direct rendering disabled
(**) RADEON(0): Setting up final surfaces
(**) RADEON(0): Initializing Acceleration
(II) RADEON(0): Render acceleration unsupported on Radeon 9500/9700 and newer.
(II) RADEON(0): Render acceleration disabled
(**) RADEON(0): EngineInit (32/32)
(**) RADEON(0): Pitch for acceleration = 184
(**) RADEON(0): EngineRestore (32/32)
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(**) RADEON(0): Initializing DPMS
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(**) RADEON(0): Initializing Cursor
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 914)
(II) RADEON(0): Largest offscreen area available: 1472 x 7274
(**) RADEON(0): Initializing color map
(**) RADEON(0): Initializing DGA
(**) RADEON(0): Initializing Xv
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia/theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(WW) RADEON(0): Option "VideoOverlay" is not used
(WW) RADEON(0): Option "OpenGLOverlay" is not used
(**) RADEON(0): RADEONScreenInit finished
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "fr"
(**) Generic Keyboard: XkbLayout: "fr"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
    xkb_keycodes             { include "xfree86+aliases(azerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+fr+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!

```

can someone help me please ?
thx
I removed some things because the message was to long

---

### Post by piggy on 2006-11-17
i have a ATI Radeon Mobility 9600. Rendering wasnt working but after this how-to guide it works. however, iam getting this error "libGL warning: 3D driver claims to not support visual 0x4b" what is this? and yeah can you guys tell us how to undo all this again?

---

### Post by piggy on 2006-11-17
berly seems to be very sluggish and jerky on my computer. iam assuming its because of my poor graphics card. what do you guys think?

---

### Post by Rob2687 on 2006-11-17
The open source driver is slow.

---

### Post by huygens on 2006-11-17
> **piggy said:**
> berly seems to be very sluggish and jerky on my computer. iam assuming its because of my poor graphics card. what do you guys think?

I won't assume that. I did not update recently my configuration on my laptop, but I have still compiz with Ubuntu 6.06 (Dapper Drake) and XGL configured using the Open Source driver for my ATI Radeon 9000 Mobility.
The system is heavily buggy, notifications (like new updates) are freezing the whole system for instance. But it is fluid. I am able to play videos at the corner of the spinning cube. It is a bit blinking because of the poor video card, but it works! Sometimes I have buggy display too.
So I guess with a Radeon 9600 Mobility it should rock! :-)

As for the libGL warning, I thought I was the only one having it, so welcome to the club :-) Until now I did not find an explanation for it...

Huygens

---

### Post by huygens on 2006-11-17
> **Rob2687 said:**
> The open source driver is slow.
I don't really agree. I have on my desktop a Radeon 9600 XT which I use with the Open Source driver, and I can't complain about performances.

Note: I don't play games, so that's maybe the reason...

Huygens

---

### Post by BingoTough on 2007-04-22
While this thread is old, people who hit it may find the following guide from the [ATI Linux Driver Wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") helpful.

I just went through the steps and my ATI Mobility 9600 works great on 7.04, including the OpenGL side.

---

### Post by Paerez on 2007-04-23
I am currently running Feisty 7.04, and you can install compiz through the ubuntu repos. I am using compiz and the open-source radeon driver which all works without any extra configuration, since radeon does AIGLX.

The only thing I changed was I made my bit-depth 16 instead of 24, which halves the graphics memory used and makes compiz way faster.

---

### Post by xflbret on 2007-05-23
confirmed NOT WORKING with a radeon mobility 9000

---

