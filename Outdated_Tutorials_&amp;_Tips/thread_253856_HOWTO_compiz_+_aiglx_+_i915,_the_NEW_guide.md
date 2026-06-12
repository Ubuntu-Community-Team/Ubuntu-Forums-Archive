---
title: "HOWTO: compiz + aiglx + i915, the NEW guide"
date: 2006-09-09
forum: Outdated Tutorials &amp; Tips
---

### Post by reacocard on 2006-09-09
This guide is designed for i915 graphics, but should work with any intel card that uses the i810 driver.

First, open your sources.list file

```

gksudo gedit /etc/apt/sources.list

```

and add these lines

```

## Compiz
deb http://xgl.compiz.info/ dapper main aiglx
deb http://www.beerorkid.com/compiz dapper main aiglx
deb http://ubuntu.compiz.net/ dapper main aiglx
deb http://media.blutkind.org/xgl/ dapper main aiglx
deb-src http://xgl.compiz.info/ dapper main aiglx
deb-src http://www.beerorkid.com/compiz dapper main aiglx
deb-src http://ubuntu.compiz.net/ dapper main aiglx
deb-src http://media.blutkind.org/xgl/ dapper main aiglx

```

now, make sure everything is up-to-date:

```

sudo apt-get update
sudo apt-get dist-upgrade

```

Install DRI:

```

sudo apt-get install xserver-xorg-air-core linux-dri-modules-common linux-dri-modules-`uname -r`

```

now, there are two major kinds of compiz. quinn, and vanilla. vanilla is the generic compiz from cvs, and quinn includes quinnstorm's custom patches and plugins. You can only install one of the two. I reccommend quinn's.

For vanilla
```

sudo apt-get install compiz-vanilla compiz-vanilla-gnome

```


For quinn's you have the choice of several window decorators, the thing that draws the borders and titlebars of your windows. here are the apt-get lines for two of them.

for cgwd: (most advanced, supports lots of theming, has a few bugs. doesn't work on vanilla)
```

sudo apt-get install cgwd cgwd-themes compiz-core compiz-plugins csm

```

for gnome-window-decorator: (least advanced, no theming, but works very well. used by vanilla compiz as well.)
```

sudo apt-get install compiz-gnome compiz-core compiz-plugins csm

```

or for both:
```

sudo apt-get install cgwd cgwd-themes compiz-gnome compiz-core compiz-plugins csm

```

Edit your Xorg config:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
gksudo gedit /etc/X11/xorg.conf

```

BE VERY CAREFUL WHEN EDITING THIS FILE

make sure the following sections/options are like this. the most important changes are highlighted in red.

Needs to be in the Screen section:
```

          DefaultDepth 24

```

Make sure these are all there, and GLcore is commented out:
```


    Section "Module"

    [COLOR="Red"]# Load "GLcore"[/COLOR]

    Load "i2c"

    Load "bitmap"

    Load "ddc"

    Load "dbe"

    [COLOR="Red"]Load "dri"[/COLOR]

    Load "extmod"

    Load "freetype"

    [COLOR="Red"]Load "glx"[/COLOR]

    Load "int10&#8243;

    Load "type1&#8243;

    Load "vbe"

    EndSection


```


EXACTLY like this:
```


    Section "Device"

    Identifier "Intel Corporation Intel Default Card"

    Driver "i810&#8243;

    [COLOR="Red"]Option "XAANoOffscreenPixmaps"[/COLOR]

    BusID "PCI:0:2:0&#8243;

    EndSection


```

MUST have this:
```


    Section "Extensions"

    [COLOR="Red"]Option "Composite" "Enable"[/COLOR]

    EndSection


```

and this:

```


    Section "DRI"

    [COLOR="Red"]Mode 0666[/COLOR]

    EndSection


```

Now modify gdm's config to use AIGLX:

```

gksudo gedit /etc/gdm/gdm.conf-custom

```

make it look like this:
```


    [servers]

    0=aiglx

    [server-aiglx]

    name=aiglx server

    command=/usr/bin/Xorg-air :0

    flexible=true


```

Now let's add a tray icon to simplify turning compiz on/off and configuring it. Grab compizswitch.tar.gz from the end of this guide and extract it somewhere. /opt works well if want to use it systemwide, but if its just for you you home directory also works (I use ~/Software/compizswitch)

Now let's make sure everything works. reboot the computer, then goto wherever you extracted compizswitch are run compizswitchicon.

Compiz will start. Notice the little red box on your panel? Click that and you'll get a menu letting you restart compiz, switch back to metacity, and change compiz's preferences or themes.

Now that that's working, let's add compiz to your startup so it'll launch automatically. Go to System -> Preferences -> Sessions, and under the Startup Programs tab, click add, browse to whereever you put compizswitch, and use compizswitchicon.

END

POST INSTALL TIPS:

Optimize Totem's video playback.

```

gksudo gedit ~/.gnome2/totem_config

```

replace this line
```

#video.driver:auto

```

with this:
```

video.driver:xshm

```

---

### Post by MadCowBoy on 2006-09-10
reacocard  Thanks for the How To, I had  couple questions, 

Please Clarify the apt-get line in your post:
sudo apt-get install linux-dri-modules-common linux-dri-modules-`uname -r`

I did them seperatly, the first "linux-dri-modules-common" had no problems,  and I tried variations on the linux-dri-modules-`uname -r` please clarify that line...

Also the Module section of my xorg.conf did not load "GLcore" but instead "i2c", should that be commented out in place of "GLcore" or left alone. 

Regards,

---

### Post by argash on 2006-09-11
Something in the config files concked out my X when I rebooted and I had to revert them back to get back into gnome.  I'm gonna try it again later when I get home but I wanted to thank you for all the work you put into this.

---

### Post by reacocard on 2006-09-11
> Please Clarify the apt-get line in your post:
sudo apt-get install linux-dri-modules-common linux-dri-modules-`uname -r`

I did them seperatly, the first "linux-dri-modules-common" had no problems, and I tried variations on the linux-dri-modules-`uname -r` please clarify that line...
How should I clarify it? that's exactly what you need to type. "uname-r" will automaically be replaced with your kernel version. doing it this way saves me the trouble fo having to put "if you installed kernel-XX then you need YY" for each possibility.

> Something in the config files concked out my X when I rebooted
Yeah, you have to be really careful with that part. make sure you have "Option "XAANoOffscreenPixmaps"", otherwise it won't work at all.

---

### Post by kalbir on 2006-09-11
I just went through this HOWTO on a fresh dapper install and the X server did not restart after my reboot. I got the following error:

> X Server not found:
/usr/bin/Xorg-air :0 :0 -auth
/var/lib/gdm/ :0Xauth-nolistentep vt7
Error command could not be executed

(I think that's it- I scrawled it down and can't make out everything I wrote!)

Any ideas what went wrong? 

Many Thanks,

Kalbir

---

### Post by argash on 2006-09-11
that sounds similar to what i was getting as well

---

### Post by kalbir on 2006-09-11
I sorted this out by using the tutorial here:

[http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card](http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card)

and mashing it in with bits and pieces from this one! Basically, I did the "union" of the two tutes. Everything is working now!

Kalbir

---

### Post by MadCowBoy on 2006-09-11
Everthing went smoothly except whn you asked to comment out 
this following line in Modules, 

# Load  "GLcore"

My System did not have this in the first place, 

Instead it has: 

Load     "i2c"

Should THAT be commented out instead?  
Or am I missing some package I should have previously installed on my system that would have inserted the Load "GLcore"? 

Thanks for the How To,

---

### Post by argash on 2006-09-12
Ok after reading the error messages carfully it looks like it doesnt like the following line in /etc/X11/xorg.conf wich was already in my screen section:

```
Device     "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
```

The error I'm getting referes to that line and says call to unspecified device.

Strange thing is that line was already there before I made any edits and now it hangs on it.  If I restore the original files I can boot into gnome just fine.

Here's the full error message:
```

Data incomplete in file /etc/X11/xorg.conf
	Undifined Device "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller" referenced by Screen "Default Screen".
(EE) Problem parsing the config file
(EE) Error parsing the config file

```

---

### Post by argash on 2006-09-12
Ok I seem to have fixed that issue now when i start compiz i get this:
```

argash@argash-laptop:~$ compiz-start.py
/usr/bin/compiz-start.py:271: GtkWarning: Can't set a parent on widget which has a parent

  menu.append(item)
compiz: GLX_EXT_texture_from_pixmap is missing
compiz: Failed to manage screen: 0
compiz: No manageable screens found on display :0.0
The program 'cgwd' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 657 error_code 8 request_code 153 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
compiz: GLX_EXT_texture_from_pixmap is missing
compiz: Failed to manage screen: 0
compiz: No manageable screens found on display :0.0

```

---

### Post by kendals on 2006-09-12
My X server failed, and I had to restore after huge issues. I'll wait for this guide to be updated to resolve these problems before I try again :P

argash- that compiz wiki for the 915- did that work following it exactly, for you?

I have a GMA900....hmm.

---

### Post by argash on 2006-09-12
yes like i said though there was a problem with my xorg.conf file that was completely unrelated that was causing me trouble. Now though I have the trouble that I just posted above, I'm searching google for answers now. In the mean time here is my xorg.conf file for ya'll to look at and see if you can spot the problem.

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

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
 	# Load  "GLcore"
	Load     "i2c"
	Load     "bitmap"
	Load     "ddc"
	Load     "dbe"
	Load     "dri"
	Load     "extmod"
	Load     "freetype"
	Load     "glx"
	Load     "int10"
	Load     "type1"
	Load     "vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier   "Intel Corporation Intel Default Card"
        Driver       "i810"
        BusID        "PCI:0:2:0"
        Option       "XAANoOffscreenPixmaps"
        VideoRam     131072
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Intel Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
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
	InputDevice	"Synaptics Touchpad"
    	Option 		"AIGLX" "true"
EndSection

Section "DRI"
       	Mode    	0666
EndSection

Section "Extensions"
   	Option    	"Composite" "Enable"
EndSection

```

---

### Post by kendals on 2006-09-12
Okay, I tried following the guide, and X Server failed for me. Not sure why- followed both guides to the T :(

I really want this eye-candy! *sniff* lol. Any ideas? Compiz manager started fine, but the Xorg.conf and gdm stuff wasn't liked by X Server...

---

### Post by argash on 2006-09-12
Again fixed my problem and now everything is working I had to stop gdm make the changes to gdm.conf-custom and restart gdm and now its all working!

---

### Post by iLoVe.cF- on 2006-09-12
hmm i get like glibc 2.4 is needed when i do compiz --replace & :S

---

### Post by anubhavrocks on 2006-09-12
if your X does not start up after making the changes try this

sudo cp -r /usr/lib/xorg/modules/input     /usr/lib/xorg-air/modules
sudo cp -r /usr/lib/xorg/modules/drivers   /usr/lib/xorg-air/modules

which basically copies the missing modules from xorg to xorg-air

---

### Post by skattman83 on 2006-09-13
I can't boot into gdm.  I get the following error message:
```
GDM: Xserver not found: /usr/bin/Xorg-air :0 :0 -auth
/var/lib/gdm/:0.Xauth -nolisten tcp vt7
Error: Command could not be executed!
Please install the X server or correct GDM configuration and restart GDM
```
I followed the guide, I left i2c uncommented in my xorg.conf file, and I copied the files over to the modules folder like one of the other posts recommnended.  Any ideas on where I went wrong?  Its an intel i845 chipset, or i855...Something like that, it uses the i810 driver though.

---

### Post by reacocard on 2006-09-13
> **skattman83 said:**
> I can't boot into gdm.  I get the following error message:
```
GDM: Xserver not found: /usr/bin/Xorg-air :0 :0 -auth
/var/lib/gdm/:0.Xauth -nolisten tcp vt7
Error: Command could not be executed!
Please install the X server or correct GDM configuration and restart GDM
```
I followed the guide, I left i2c uncommented in my xorg.conf file, and I copied the files over to the modules folder like one of the other posts recommnended.  Any ideas on where I went wrong?  Its an intel i845 chipset, or i855...Something like that, it uses the i810 driver though.

Sounds like the AIGLX X server didn't get installed. try

```
sudo apt-get install xserver-xorg-air-core
```

---

### Post by reacocard on 2006-09-13
Updated the guide. most important X changes are now highlighted in red. Also I've added a replacement I've been working on for the tray icon script, so you may want to grab that even if you already have compiz working.

---

### Post by skattman83 on 2006-09-13
@reacocard:

That did the trick, thanks for your help!

---

### Post by mrojas73 on 2006-09-13
I had everything working pretty good, and a couple of updates got my gnome session messed up.  When I loggin everithing is in reverse, the toolbars..everything. What could that be?

I know that cgwd got updated, but I can't remember what else.

So, these last updates may be bad.

---

### Post by routerstu on 2006-09-13
i had issues but did this


"sudo cp -r /usr/lib/xorg/modules/input /usr/lib/xorg-air/modules
sudo cp -r /usr/lib/xorg/modules/drivers /usr/lib/xorg-air/modules"



i have i2c as well.  i am very excited this works!!!!

thanks everyone!

---

### Post by routerstu on 2006-09-13
i spoke too soon, when i "compiz-manager" in the command line everything is flipped, mirrored or reversed.  any ideas?

---

### Post by mrojas73 on 2006-09-13
Yes, read my post above yours....it was an update that came as you were typing your message...I bet you restarted your computer and got what I got!

Is there a way to uninstall updates?

---

### Post by routerstu on 2006-09-13
thanks man, damn, thought i was losing it.  ill stay tuned for a solution

thanks again

---

### Post by routerstu on 2006-09-14
i joined #ubuntu-xgl and this is a known problem.  they are working on it.  when complete run update and dist-upgrade

---

### Post by routerstu on 2006-09-14
fixed.


sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by skattman83 on 2006-09-14
I have this problem when I select quit from the menu.  the exit menu doesn't come up, and I can't select any open windows or menus, but I can still move the mouse.  How can I fix this?

---

### Post by reacocard on 2006-09-14
> **skattman83 said:**
> I have this problem when I select quit from the menu.  the exit menu doesn't come up, and I can't select any open windows or menus, but I can still move the mouse.  How can I fix this?

This is a known bug with AIGLX and compiz. Currently there is no fix. Easiest workaround is to put a launcher on your panel for this command:

```
gnome-session-save --kill --silent --gui
```

that will log you out, and then you can shutdown from the login screen.

FYI, the exit menu is still there, you just can't see it. if you click in the right spot you can still shutdown/reboot/etc.

---

### Post by sydbarrett on 2006-09-14
> **argash said:**
> Again fixed my problem and now everything is working I had to stop gdm make the changes to gdm.conf-custom and restart gdm and now its all working!

Just curious as to how you were able to stop gdm and then change the file, you seem to have had the problem I am having now.

---

### Post by Milyardo on 2006-09-14
I'm getting a error with my X server startup.
It says it cannot load the driver "i810", that the module doesn't exist. Before installing Compiz or editing X11 at all it said that "vesa" was my driver, now I changed that to "i810" knowing that my card was actualy a Intel i845. I tried changing it back to vesa from i810 but now the vesa module doesn't exist either!!! So I'd really really like to know what happened, but more importantly how can I reinstall these modules if necessary. :frown:

---

### Post by reacocard on 2006-09-14
Milyardo, did you try this?

```

sudo cp -r /usr/lib/xorg/modules/input /usr/lib/xorg-air/modules
sudo cp -r /usr/lib/xorg/modules/drivers /usr/lib/xorg-air/modules

```

---

### Post by Milyardo on 2006-09-14
You know now that I think about it I knew about the bug from another tutorial and it said to use the command
```
sudo ln -s /usr/lib/xorg/modules/drivers/ /usr/lib/xorg-air/modules/

sudo ln -s /usr/lib/xorg/modules/input/ /usr/lib/xorg-air/modules/ 
```

So is there any real technical difference between the two commands?

EDIT:That tutorial came from the wiki on compiz.net

---

### Post by Milyardo on 2006-09-14
Ok So I tried copyingthe modules and it worked :) However GDM started but I'm not in compiz, but rather metacity with a rather low resolution (640x480) :(

---

### Post by reacocard on 2006-09-14
> **Milyardo said:**
> You know now that I think about it I knew about the bug from another tutorial and it said to use the command
```
sudo ln -s /usr/lib/xorg/modules/drivers/ /usr/lib/xorg-air/modules/

sudo ln -s /usr/lib/xorg/modules/input/ /usr/lib/xorg-air/modules/ 
```

So is there any real technical difference between the two commands?

EDIT:That tutorial came from the wiki on compiz.net

Been looking for that. These commands create a link between the folders, so when one is updated, the same changes appear in the other. This is generally better to use than the copy method.

No idea why the resolution changed. :-k As for compiz, did you try running the script from the first post? compiz doesn't start by default, that's why you need the script.

---

### Post by foxy123 on 2006-09-15
I've got a problem to switch between users' account with aiglx. I can switch frm one to another account but I cannot find how to switch back. Does anyone use aiglx successfully in multi-user environment? So far I use xnest to have another account in a nested window but it is not always convenient.

---

### Post by catalasan on 2006-09-15
hi all,

just installed aiglx/compiz on my toshiba satellite m45-s331.

everything seems to be working fine except when i select "system->quit" from the mainmenu that the system freezes. i have to do "ctrl+alt+backspace" to restart it.

did any of you guys encounter this problem?

---

### Post by Milyardo on 2006-09-15
OK I have compiz working perfectly but I'm still stuck in the lowest possible resolution :( I don't think this is Compiz related however, I think its because I switched from that vesa driver in X to the i810 one.

I'm going to look elsewhere for answers, but if you guys have any ideas I'll listen.

---

### Post by reacocard on 2006-09-15
[QUOTE=catalasan]everything seems to be working fine except when i select "system->quit" from the mainmenu that the system freezes. i have to do "ctrl+alt+backspace" to restart it.

did any of you guys encounter this problem?[/QUOTE]
See this post: [http://ubuntuforums.org/showpost.php?p=1497886&postcount=29](http://ubuntuforums.org/showpost.php?p=1497886&postcount=29)

[QUOTE=Milyardo]OK I have compiz working perfectly but I'm still stuck in the lowest possible resolution  I don't think this is Compiz related however, I think its because I switched from that vesa driver in X to the i810 one.

I'm going to look elsewhere for answers, but if you guys have any ideas I'll listen.[/QUOTE]
Try 915resolution. It might help.

---

### Post by hunter186 on 2006-09-21
Having the same (first) problem that you had.  I'm getting the "Error parsing the config file" error, and the undefined device error that you got.  I'm just wondering how you fixed that?

---

### Post by pranith on 2006-09-23
hi,
   I tried following ur guide and I get the following error

chinna-laptop% sudo apt-get install linux-dri-modules-`uname -r`
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-dri-modules-2.6.15-27-386

please tell me wat the problem is 
thanks in anticipation
pranith

---

### Post by pranith on 2006-09-23
hi,
   u might also need to change the how-to since csm and cgwd have changed their names to emerald beryl I guess so the apt-get install lines need to be changed. I donno wat they are. Hope u could help in the changes we have to make
thanks in anticipation
pranith

---

### Post by qinhengsi on 2006-09-23
can you tell the new name of csm?
I tried a few minutes earlier with error saying csm is not found.
thank you

---

### Post by reacocard on 2006-09-23
[QUOTE=pranith]hi,
   u might also need to change the how-to since csm and cgwd have changed their names to emerald beryl I guess so the apt-get install lines need to be changed. I donno wat they are. Hope u could help in the changes we have to make
thanks in anticipation
pranith[/QUOTE]

That hasn't happened yet. When it does, this guide will be completely outdated and will not be maintained. I may make a new one though.

[QUOTE=qinhengsi]can you tell the new name of csm?
I tried a few minutes earlier with error saying csm is not found.
thank you[/QUOTE]

See above^. For some reason, some things like csm are missing from the compiz repos. I have the packages though, so just send me your e-mail and I'll get the missing packages to you.

---

### Post by sunny_nwho on 2006-09-23
I guess it has happened now I cannot install I tried this
sudo apt-get install linux-dri-modules-`uname -r`

and got this
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-dri-modules-2.6.15-27-386


Similarly I tried this
sudo apt-get install compiz compiz-core compiz-plugins compiz-gnome compiz-manager

and got this
Reading package lists... Done
Building dependency tree... Done
Package compiz-manager is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package compiz-manager has no installation candidate

would be great if anyone can give a solution thanks u so far anyways for the guide

---

### Post by Darell on 2006-09-23
they deleted their packages from their servers! :( we will have to wait till Beryl is out i'm afraid..it really sucks cause i had Compiz + XGL fully running 2 days ago, but now after a complete reinstall of Ubuntu i cant install it anymore :(

---

### Post by reacocard on 2006-09-23
As I said above, I have the missing packages. Just email me and I'll get them to you. It's probably a good idea to wait for beryl though.

---

### Post by qinhengsi on 2006-09-24
firstly, thanks to reacocard for the pack

I follows this howto. But I got error in the final step. when i run compizswitch, I got the following msg:

cgwd: error while loading shared libraries: libdbus-1.so.3: cannot open shared object file: No such file or directory
compiz: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by compiz)
Traceback (most recent call last):
  File "./compizswitchicon", line 178, in ?
    pixbuf = gtk.gdk.pixbuf_new_from_file("/usr/share/compiz/logo24.png")
gobject.GError: “/usr/share/compiz/logo24.png”&#65306;No such file or directory

what is going wrong? thanks

---

### Post by pranith on 2006-09-25
same problem here too

---

### Post by iam_foo on 2006-09-25
thanks reacocard for sending me those packages.
they didn't work, version issues..but i really appreciate the help.
i'll wait for beryl.
:twisted:

---

### Post by reacocard on 2006-09-25
Yeah, sorry, I should have been more specific: I have the _Edgy_ packages for compiz, not the Dapper ones. I recall seeing Dapper packages posted somewhere else on these forums, so maybe you can find those.

---

### Post by booza on 2006-09-25
Hi mates , try this howto [http://gandalfn.wordpress.com/howto-compiz-aiglx-on-dapper/](http://gandalfn.wordpress.com/howto-compiz-aiglx-on-dapper/)

It works 100 % on my laptop :) 

Trust me .... good luck :cool:

---

### Post by reacocard on 2006-09-25
> **booza said:**
> Hi mates , try this howto [http://gandalfn.wordpress.com/howto-compiz-aiglx-on-dapper/](http://gandalfn.wordpress.com/howto-compiz-aiglx-on-dapper/)

It works 100 % on my laptop :) 

Trust me .... good luck :cool:

I've seen that one, and my guide is largely based off it. Of course, now that the repos are offline til beryl, there's little point in any of these howtos.

---

### Post by gray380 on 2006-09-29
Hi there!

Repos are down???

Is this a reson why I can't reinstall the following?

sudo apt-get install cgwd cgwd-themes compiz-core compiz-plugins csm

brg,
Serhiy.

---

### Post by reacocard on 2006-09-29
> **gray380 said:**
> Hi there!

Repos are down???

Is this a reson why I can't reinstall the following?

sudo apt-get install cgwd cgwd-themes compiz-core compiz-plugins csm

brg,
Serhiy.

Yes, the repos are down, in anticipation of Beryl. Your best bet is to just wait a few days til Beryl is released, then follow a guide for that.

---

### Post by foxy123 on 2006-09-29
> **reacocard said:**
> Yes, the repos are down, in anticipation of Beryl. Your best bet is to just wait a few days til Beryl is released, then follow a guide for that.

Beryl is already in Dapper's repos. I am not sure how stable it is but I've just replaced compiz with it. Beryl's splash screen is work or art really!

This is my list of repos:

```
##AIGLX-Compiz
deb http://xgl.compiz.info/ dapper main aiglx
deb http://www.beerorkid.com/compiz dapper main aiglx
deb http://ubuntu.compiz.net/ dapper main aiglx
deb http://media.blutkind.org/xgl/ dapper main aiglx

deb-src http://xgl.compiz.info/ dapper main aiglx
deb-src http://www.beerorkid.com/compiz dapper main aiglx
deb-src http://ubuntu.compiz.net/ dapper main aiglx
deb-src http://media.blutkind.org/xgl/ dapper main aiglx

```

---

### Post by reacocard on 2006-09-29
> **foxy123 said:**
> Beryl is already in Dapper's repos. I am not sure how stable it is but I've just replaced compiz with it. Beryl's splash screen is work or art really!

This is my list of repos:

```
##AIGLX-Compiz
deb http://xgl.compiz.info/ dapper main aiglx
deb http://www.beerorkid.com/compiz dapper main aiglx
deb http://ubuntu.compiz.net/ dapper main aiglx
deb http://media.blutkind.org/xgl/ dapper main aiglx

deb-src http://xgl.compiz.info/ dapper main aiglx
deb-src http://www.beerorkid.com/compiz dapper main aiglx
deb-src http://ubuntu.compiz.net/ dapper main aiglx
deb-src http://media.blutkind.org/xgl/ dapper main aiglx

```

Sweet! thanks for the tip. Upgrading now, will post a HOWTO for upgrading/installing sometime this weekend.

EDIT: argh, beaten. someone else already made a guide: [http://ubuntuforums.org/showthread.php?t=267232](http://ubuntuforums.org/showthread.php?t=267232)

---

### Post by gray380 on 2006-10-02
> **reacocard said:**
> Yes, the repos are down, in anticipation of Beryl. Your best bet is to just wait a few days til Beryl is released, then follow a guide for that.

Is there any guide for Beril + aiglx + i915?

---

### Post by foxy123 on 2006-10-02
> **gray380 said:**
> Is there any guide for Beril + aiglx + i915?
use this one [http://www.ubuntuforums.org/showthread.php?t=267232](http://www.ubuntuforums.org/showthread.php?t=267232) but see the repositories list in my post here [http://www.ubuntuforums.org/showpost.php?p=1559418&postcount=4](http://www.ubuntuforums.org/showpost.php?p=1559418&postcount=4)

---

### Post by christhemonkey on 2006-10-04
Are there any guides around for Beryl+ Nvidia beta drivers + Dapper?

Had a few searches and they havent produced anything.

---

