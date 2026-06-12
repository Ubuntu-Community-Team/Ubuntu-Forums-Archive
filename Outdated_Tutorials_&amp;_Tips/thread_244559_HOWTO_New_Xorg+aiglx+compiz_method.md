---
title: "HOWTO: New Xorg+aiglx+compiz method"
date: 2006-08-26
forum: Outdated Tutorials &amp; Tips
---

### Post by skroll on 2006-08-26
Well, the other HOWTO by gandalfn was an excellent guide, but it doesn't work anymore due to the changes in the compiz packages.  I am going to borrow a bit from his guide, but this one works.

So, here we go!

1. Download packages

I used these repos, which is recommended on the compiz forums, so add them to your sources.list
```

deb http://www.beerorkid.com/compiz dapper main aiglx
deb http://media.blutkind.org/xgl/ dapper main aiglx
deb http://ubuntu.compiz.net/ dapper main aiglx

```

and now you need to update everything so...
```

sudo apt-get update
sudo apt-get dist-upgrade

```

lets get all those DRI packages
```

sudo apt-get install linux-dri-modules-common linux-dri-modules-`uname -r`

```

Now I've never had this problem, but some have, so if you have a problem at this point, regenerate your module deps.
```

sudo /sbin/ldm-manager

```

Ok, now to fetch what we wanted:
```

sudo apt-get install cgwd compiz compiz-core compiz-gnome xserver-xorg-air-core

```

2. Set up your xorg server!

Open up /etc/X11/xorg.conf and make sure modules looks like:
```

Section "Module"
# Load "GLcore"
Load "bitmap"
Load "ddc"
Load "dbe"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

```

and you need to add the Option "XAANoOffscreenPixmaps" to your device section like:
```

Section "Device"
Identifier "Intel Corporation Intel Default Card"
Driver "i810"
[COLOR="Red"]Option "XAANoOffscreenPixmaps"[/COLOR]
BusID "PCI:0:2:0"
EndSection

```

and add AIGLX to your ServerLayout:
```

Section "ServerLayout"
[COLOR="Red"]Option "AIGLX" "true"[/COLOR]
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "Synaptics Touchpad"
EndSection

```

Uncomment out the "DRI" section if it is:
```

[COLOR="Red"]Section "DRI"
Mode 0666
EndSection[/COLOR]

```

and add the Composite extension (because that's why we did this, right?)
```

[COLOR="Red"]Section "Extensions"
Option "Composite" "Enable"
EndSection[/COLOR]

```


3. Configure gdm

Now we need to tell gdm we want to start the xorg-air server

Modify /etc/gdm/gdm.conf-custom so you have these lines:
```

[servers]
0=aiglx

[server-aiglx]
name=aiglx server
command=/usr/bin/Xorg-air :0
flexible=true

```

Now, all **SHOULD** be well, but it's **NOT**.  When I installed xorg-air-core, it doesn't seem to copy over your modules from xorg, so you need to do this.  I thought of doing a symbolic link, but it didn't seem to work (in fact, browsing to the dir gave me a 'too many levels deep' error, any fix for this?) so in the mean time I simply copied everything from:

```

cp /usr/lib/xorg/modules/drivers/* /usr/lib/xorg-air/modules/drivers
cp /usr/lib/xorg/modules/input/* /usr/lib/xorg-air/modules/input

```

And that seemed to work.  Like I said, if anyone knows a fix for this inconvenience let me know.  However, restart your machine (or just gdm, but I found it to be a problem) and you should have those fancy effects.

However, just to note, you now have the ability to turn on/off the GL desktop in the icon, and no longer have detailed settings in your compiz icon.  This is because gset-compiz is **GONE**.  You now use gconf-editor to change your settings.  In gconf-editor browse to: apps/compiz/plugins to change settings, see my screenshot for an example.  

If you have any improvements to this guide, let me know!

---

### Post by Mr_Hulot on 2006-08-29
Thanx a lot guy, i've been looking around for a week for some solution,
every HowTo crash my x server, but thanks to yours, it work so f** fine!

--> i'd like to "te serrer la main" (en français)!

Thanks again, cheers!!!

---

### Post by ronmarley1 on 2006-08-29
Hi skroll,
Thanks for the How-To.  However, "However, just to note, you now have the ability to turn on/off the GL desktop in the icon."
I did not get the icon.  Any ideas?

---

### Post by ronmarley1 on 2006-08-29
Nevermind!  Works great!  Thanks!

---

### Post by kebabtomten on 2006-08-29
I dont see an icon for turn it off/on, where should it be?

---

### Post by ronmarley1 on 2006-08-29
> **kebabtomten said:**
> I dont see an icon for turn it off/on, where should it be?
Look in the panel up by the clock.  It's a 3D red cube.  See my screen capture attached below.

---

### Post by kebabtomten on 2006-08-29
Yeah i have found that. I have selected the trueglass engine but shouldnt i be abel to switch workspace in 3d and stuff like that?

---

### Post by Hotaru on 2006-08-29
I got it working with no problems... but it's sooo much slower than my compiz-vanilla aiglx... :(

---

### Post by ronmarley1 on 2006-08-29
Right-click the icon and click on GL Desktop to turn it on.  Check this link for different keyboard shortcuts to the different plugins: [http://en.opensuse.org/Compiz#Default_plugin_keyboard_shortcuts](http://en.opensuse.org/Compiz#Default_plugin_keyboard_shortcuts)

---

### Post by kebabtomten on 2006-08-29
Where should i right-click? On the icon in the panel? If i dont get any options there.

---

### Post by ronmarley1 on 2006-08-29
> **kebabtomten said:**
> Where should i right-click? On the icon in the panel? If i dont get any options there.
You should be able to rt. click on the icon to get the GL Desktop selection.  Not sure why you don't.

---

### Post by kebabtomten on 2006-08-29
Is the what i should have open or?

---

### Post by waldorf on 2006-08-29
Thanks for the Howto! I thought I did everything right but somethings not right and the X server didn't start.

Not sure what happened. Any suggestions?

---

### Post by pepitogrillo37 on 2006-08-29
Excellent Thread! aixgl and compiz work again! Although I prefer my last configuration with my deprecated gnome-vanilla-aiglx (Does anybody have the deprecated packages?) The reason is very easy: with my modest i915 integrated graphic is the best solution a have tested from xgl, aiglx+quinn or my favorite aiglx-vanilla. Actually, with the new gnome-compiz-manager the windows border have disappear though others effect works ok (if you have the same problem this doesn't happen with the quinn's pack) 

One Question: Does anybody know why the borders dissapear with the compiz-vanilla & compiz-vanilla-gnome? I will put a few candles for any Saint to use again the compiz-vanilla.

---

### Post by ronmarley1 on 2006-08-31
> **kebabtomten said:**
> Is the what i should have open or?
No, that's the theme tool.  Right click on the icon in the panel.  The arrow in the attached screen capture shows which one.

---

### Post by rodrigo666 on 2006-08-31
> **waldorf said:**
> Thanks for the Howto! I thought I did everything right but somethings not right and the X server didn't start.

Not sure what happened. Any suggestions?

Same here.

I done this on a fresh install of Dapper with ATI properly installed (I mean, fglrxinfo getting ATI and OpenGL, no mesa3d) and followed the steps one by one.

But, my X session got broke all the time. I got to do a "startx" in this session to came here tell you this.

Something must be missing on your how-to man.

---

### Post by coulix on 2006-08-31
Hello,
I followed exactly the process.
Here is my card
  "Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics 

But when i launch gl desktop from the red top right compiz icon,
all my borders goes off, and all windows stack on desktop 1.


if i try to force a gnome-window-decorator i get a xwindow error.

Help :'(

---

### Post by Cl1mh4224rd on 2006-08-31
> $ sudo apt-get update
[snip]
W: GPG error: [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: GPG error: [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: GPG error: [http://media.blutkind.org](http://media.blutkind.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: [color=red]You may want to run apt-get update to correct these problems[/color]
Genius, Ubuntu... Genius...

Needless to say, this didn't work for me...

---

### Post by ericesque on 2006-08-31
heh.  yeah.  I've been getting that 'you may want too run apt-get' message as well.  It never made any sense to me either.

---

### Post by pepitogrillo37 on 2006-08-31
> **coulix said:**
> Hello,
I followed exactly the process.
Here is my card
  "Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics 

But when i launch gl desktop from the red top right compiz icon,
all my borders goes off, and all windows stack on desktop 1.


if i try to force a gnome-window-decorator i get a xwindow error.

Help :'(


HI! I supposed you are using the compiz-vanilla. You can use the compiz-quinn or put a 16 defaultPath (the color range) in your xorg.conf and voila! the borders appear again. Personally I prefer the second solution!

---

### Post by pepitogrillo37 on 2006-08-31
> **Cl1mh4224rd said:**
> Genius, Ubuntu... Genius...

Needless to say, this didn't work for me...

add this as root or as sudo:
wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O - | sudo apt-key add -
wget [http://media.blutkind.org/xgl/quinn.key.asc](http://media.blutkind.org/xgl/quinn.key.asc) -O - | sudo apt-key add -
wget [http://ubuntu.compiz.net/quinn.key.asc](http://ubuntu.compiz.net/quinn.key.asc) -O - | sudo apt-key add -

---

### Post by Yerakon on 2006-09-01
[http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card]("http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card")

Perfect! 24 bit and borders!;) 

If dont like the "zooming" when rotate the cube then run
"gconf-editor":  apps->compiz->rotate and set "zoom" to "0"

---

### Post by Yerakon on 2006-09-01
[http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card]("http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card")

Perfect! 24 bit and borders!;) 

If dont like the "zooming" when rotate the cube then run
"gconf-editor":  apps->compiz->rotate and set "zoom" to "0"...

---

### Post by KageKeeper on 2006-09-01
Hmm.

I followed the HOW TO and all seems to be ok for the most part, however I do not have the icon you are referring too.

Is there something I must enable for it to appear?

Thanks for the help. :)

---

### Post by Hotaru on 2006-09-01
> **Yerakon said:**
> If dont like the "zooming" when rotate the cube then run
"gconf-editor":  apps->compiz->rotate and set "zoom" to "0"...
Thanks! That zooming started irritating me a little. I also spent some time configuring wobbly plugin and it is a little better now. But I'm still hoping the performance from vinilla packages will return with the next update ;).

---

### Post by kebabtomten on 2006-09-01
> **ronmarley1 said:**
> No, that's the theme tool.  Right click on the icon in the panel.  The arrow in the attached screen capture shows which one.
As you can see i do not have that icon, should i autostart something when gnome starts?

---

### Post by xhaan on 2006-09-02
This didn't work for me, xorg fails to start and complains about mismatched xorg version and missing fglrx drivers.

Luckily I backed up my config files and was able to get my old display back.

---

### Post by facejeans on 2006-09-03
Hey all,

I'm wondering if this is why some people don't see the icons...I followed the HOW-To exactly...but didn't get aiglx...although at least the x started, which is more than i can for the last 8 times i've tried to make it work.  anyway, when i ran $ compiz from the terminal, this is what i got:

compiz.real: SmcOpenConnection failed: Authentic ation Rejected, reason : None of the authentication protocols specified are supp orted and host-based authentication failed
compiz.real: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz.real: No manageable screens found on display :0.0


Any ideas on what this means?

---

### Post by facejeans on 2006-09-03
OK...

figured it out:  The tutorial is missing one program: gnome-window-manager.  That will pop the icon up and make aiglx work when you right click and hit GL  desktop.

HOWEVER, water and Rain still don't work...does anyone have any ideas on how to make this work?  I have a 855GME if that helps.

---

### Post by centraspike on 2006-09-04
@facejeans

I think you mean gnome-compiz-manager. I noticed it was missing from the how-to but wondered if it might be a dependency of one of the other packages (i don't think it was when i installed it though).

Anyway, everything has been working fine for me for days but i just had an update for compiz-plugins and csm this morning and now my window borders have gone away :(

---

### Post by stuart.crouch on 2006-09-04
Same here.

Was a happy bunny for weeks, with my desktop on Xgl and my laptop on aiglx.  I let ubuntu install the updates, and it killed my desktop on Wednesday, and my laptop today with the new cwm (or is it csm?). I didnt check what I was installing :(, the thing didnt have a description of what it was.

Hopefully someone who knows whats going on will explain how to get things back.
BTW I've actually lost all acceleration features, rather than just window borders.

Cant change desktop, no wobbly help/menu dropdowns, no transparency and no window borders. Its more like compiz isnt loading at all.

Thanks
--
Stuart

---

### Post by centraspike on 2006-09-04
well. i just forced the version of compiz-plugins back to the previous version (0.10-0ubuntu1 (dapper)) in the synaptic package manager (select the compiz-plugins package then go to package->force version in the menu).
This removed csm which appears to be some new dependency of compiz-plugins and after restarting gdm everything seems fine (interestingly though i had to restart gdm after switching off GLdesktop in order to get borders back when starting GLdesktop again)

---

### Post by centraspike on 2006-09-04
OK, now i've been checking out the compiz forums and have found this new thread:

[http://www.compiz.net/topic-3862-quinn-compiz-with-latest-compiz-plugins-update]("http://www.compiz.net/topic-3862-quinn-compiz-with-latest-compiz-plugins-update")

From here i determined that more than just compiz-plugins had been updated and in fact the version of compiz-core had also gone up from 41 to 42.
It appeared that the auto update in ubuntu had not spotted this so i opened the auto update dialog again and pressed the check button. 
This time lots of compiz and cgwd packages came up (a total of 7) including the new version of compiz-core.
So, naturally, I updated them all.

This did not provide an instant fix, however. I also noted from the linked thread that compiz-start should now be used to start compiz and when i look in the system->preferences->sessions dialog under startup programs there is both compiz-start and compiz-tray-icon listed. Disabling compiz-tray-icon and restarting gdm now fixes things (kinda).

Unfortunately now the performance is pretty much unbearable when previously it was great. So maybe that can be fixed through some configuration. But for now i have compiz turned off ("metacity --replace" at the console)

Also i can no longer use the tray icon which is  pretty annoying.

---

### Post by centraspike on 2006-09-04
good news, i've fixed everything :)

It seems that the csm package is a new compiz settings manager. Unfortunately though it cannot save settings unless you also do this in the console: 

```
chmod 755 ~/.compiz -R

```

So then i launched it by typing csm in the console and started playing around with the settings. I solved my performance issues by turning off the blur plugin.

I also removed the gnome-compiz-manager package and deleted the compiz-tray-icon entry from the startup programs under preferences->sessions just to keep things tidy.

NB. compiz seems to crash a lot when changing settings in csm so to get it going again do the following:

```
metacity --replace &
compiz-start
```

---

### Post by facejeans on 2006-09-04
So I've updated everything with what other people have been saying, and i think now i have all 7 packages updated.

However, nothing is working still...and i'm afraid to test the removal of stuff from sessions becuase of the crashing and whatnot that's been happening.  

But even with the updated packages, not working at all...sucks.

If someone figures it out, please post here again!

---

### Post by facejeans on 2006-09-04
here's an update from my end.

i did compiz-start at the terminal, and compiz and aiglx loads...but its INCREDIBLY slow.

nothing big, but i thought i should let people know in case it helps.

---

### Post by facejeans on 2006-09-04
i used this suggestion from the compiz.net forums on this thing...

hokes wrote:

how can i say that.......53 Its awesome! its working in a charm! (but gnome-compiz-preference dont....) i used a script to stard compiz

Here a temporary alternative:

Code:

sudo gedit /usr/local/bin/compiz-start

and paste this in the empty file:
Code:

#!/bin/sh 
killall gnome-window-decorator 
wait

gnome-window-decorator & 
compiz --replace dbus csm &
cgwd --replace &

save it and type in the terminal:

Code:

sudo chmod +x /usr/local/bin/compiz-start

now press Alt + F2 and type:

Code:

compiz-start

you can add it in system-preference-sessions  startup programs

Compiz seems to work this way...but its still real slow, although once you get it going, it works better.  LIke, wobbly is real laggy, but for instance, when you drag cube around, once it zooms out, it works like it did before!  I typed in compiz-start, and this was what i got:



compiz: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.

** (cgwd:5623): WARNING **: Cannot open pixmap: menu

** (cgwd:5623): WARNING **: Cannot open pixmap: shade

** (cgwd:5623): WARNING **: Cannot open pixmap: unshade

** (cgwd:5623): WARNING **: Cannot open pixmap: above

** (cgwd:5623): WARNING **: Cannot open pixmap: unabove

** (cgwd:5623): WARNING **: Cannot open pixmap: sticky

** (cgwd:5623): WARNING **: Cannot open pixmap: unsticky
gnome-window-decorator: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.
Switching to using non-fbo path
compiz: water: GL_ARB_fragment_program is missing


Man, why can't we just go back to the compiz from yesterday!!!! :) :(

---

### Post by facejeans on 2006-09-04
The mix of those centraspike and the other compiz.net thing works real well...the compiz gets back to normal, but i took out blur without testing it...

However, when i start compiz, it renders my keyboard and mouse useless...like i can't type, and nothing is highlighted or selected.  Actually, the only thing that works is the windows..haha.

Any ideas?

---

### Post by iseebluuue on 2006-09-05
ok, i've followed the steps in this tutorial and everything seemed to install fine. i have the gnome compiz preferences  and cgwd themer links under system->preferences 

however, when i open the compiz prefences window and check to enable gl desktop, the titlebars and borders disappear, and sometimes the system locks up. even if the system doesn't lock up, the enable gl desktop box is unchecked when i open the compiz preferences again. anyone have a solution? please keep in mind that i'm new to linux, so you'll need to be very specific.

thanks

---

### Post by Freedreamer on 2006-09-05
a question: why using compiz vanilla ( this would be more stable ...) i must using 16 bit ( very very bad ) and not 24 ? if i put 24 in xorg.conf i lose window's edge but all other plugins runs ok.

any idea?

---

### Post by encompass on 2006-09-06
Works great thanks...

---

### Post by skroll on 2006-09-06
I'm not sure what happened to your guys installations, but I'm sorry to say that the directions have changed radically yet again.

---

### Post by iseebluuue on 2006-09-08
after many hours of frustration i followed the instructions closely again and got this to work! i'm lovin' it! thank you!

---

### Post by Hotaru on 2006-09-08
I've uninstalled everything compiz-related and installed again using this how-to: [http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card]("http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card")

It's working fine now. :)

EDIT:
Not entirely... the window where you can choode wether to sut dowm / hibernate / reboot etc. isn't rendered... :/

---

### Post by facejeans on 2006-09-09
Skroll, How did the directions change now?

---

### Post by tonydm on 2006-09-09
Would like to see this for myself.  What is the basic/best needed video card to use this eye candy? :)

Tony D

---

### Post by viraldhimar on 2006-09-10
Hi, I have tried just about everything to get aiglx+compiz working, even followed that howto by hotaru but it doesn't seem to work. I get the following errors when running comiz-start from terminal:

dhimarvi@dainself:~$ compiz-start
nohup: appending output to `nohup.out'
dhimarvi@dainself:~$ more nohup.out

** (cgwd:5556): WARNING **: Cannot open pixmap: shade

** (cgwd:5556): WARNING **: Cannot open pixmap: unshade

** (cgwd:5556): WARNING **: Cannot open pixmap: above

** (cgwd:5556): WARNING **: Cannot open pixmap: unabove

** (cgwd:5556): WARNING **: Cannot open pixmap: sticky

** (cgwd:5556): WARNING **: Cannot open pixmap: unsticky
The application 'cgwd' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
Couldn't load settings.  Reverting to defaults.

** (cgwd:7441): WARNING **: Cannot open pixmap: unshade

** (cgwd:7441): WARNING **: Cannot open pixmap: above

** (cgwd:7441): WARNING **: Cannot open pixmap: unabove

** (cgwd:7441): WARNING **: Cannot open pixmap: sticky

** (cgwd:7441): WARNING **: Cannot open pixmap: unsticky
Couldn't load settings.  Reverting to defaults.

what am I doing wrong?

---

### Post by Hotaru on 2006-09-10
Is there any fix to make shut-down dialog screen  come back? It gets on my nerves that I have to type a command in the terminal each time I want to shut-down or restart my Ubuntu... :(

[EDIT]
Today's plugins' update seems to have solved the problem.

[EDIT 2]
It's gone again... I've rebooted a couple of times and it's gone for good, damnit. ><

---

### Post by irlkersten on 2006-09-10
I have the same problem.
I've just set up compiz and aixgl and all works fine, except for the shutdown screen. It seems to disable everything like it would normally, but it doesn't show. Once I cancel it (by pressing ESC) I can access the desktop again.

---

### Post by eeclark on 2006-09-12
So can anyone tell me straight out if AIGLX will work on an R300, specifically my ATI 9600? I read out there that some people have gotten it to work but I cannot track down the steps. I see all the Intel chipset stuff but nothing on "This is how I got my ATI 9600 to work with AIGLX"...

Any help is appreciated.

Thanks

---

### Post by latuss on 2006-09-12
Hi, I was with the problem when the aiglx is activated, the window borders dissapear and maybe no effects at all, I think I have a solution, not optimal, but works...
I have an Intel crappy video card... 
```

Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

```
ok, the important thing
edit the compiz-start, located in /usr/bin/compiz-start
Original file
```

#!/bin/sh
if ps -e | grep Xgl > /dev/null
then
    nohup compiz --replace dbus csm > /dev/null &
else
    nohup compiz --strict-binding --indirect-rendering --replace dbus csm > /dev/null &
fi

sleep 2

if [ -f /usr/bin/cgwd ]
then
    nohup cgwd --replace &
else
    nohup gnome-window-decorator --replace &
fi



```


File with the modification

```

#!/bin/sh
if ps -e | grep Xgl > /dev/null
then
    nohup compiz --replace dbus csm > /dev/null &
else
    nohup compiz --strict-binding --indirect-rendering --replace dbus csm > /dev/null &
fi

sleep 2

if [ -f /usr/bin/cgwd ]
then
    nohup cgwd --replace &
else
    nohup gnome-window-decorator --replace gconf & 
fi


```


after that.. all works perfect.. ok.. almost.. the compiz setting manager (the one in the tray icon dont work) but.. I installed another compiz manager, I think is an older one... the version is the 0.12 and that one allow me to change the preferences....
ok.. that is... 

have fun and good luck :D

---

### Post by Cl1mh4224rd on 2006-09-16
> **pepitogrillo37 said:**
> add this as root or as sudo:
wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O - | sudo apt-key add -
wget [http://media.blutkind.org/xgl/quinn.key.asc](http://media.blutkind.org/xgl/quinn.key.asc) -O - | sudo apt-key add -
wget [http://ubuntu.compiz.net/quinn.key.asc](http://ubuntu.compiz.net/quinn.key.asc) -O - | sudo apt-key add -
Thanks. That got me past that part. Now...

> $ sudo cp /usr/lib/xorg/modules/drivers/* /usr/lib/xorg-air/modules/drivers
cp: target `/usr/lib/xorg-air/modules/drivers' is not a directory
Can I just create the directory, or is this (the directory not existing) a sign that something's wrong?

Edit: It's the "drivers" and "input" directories that don't exist.

Edit #2:
Yeah, OK, so... I just went ahead and created the directories. After copying everything, I rebooted. Then I get the BSoD complaining about a misconfigured X server, or something. I check the log and apparently it could no longer load the fglrx drivers (I have an Radeon X800 GTO).

Sooo... am I just out of luck?

Edit #3:
I took a closer look at the error log. The fglrx driver is failing to load because it's expecting Xorg 7.0, but Xorg-air is 7.1...

---

### Post by IDeus on 2006-09-16
When I try to update I get

W: GPG error: [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97F ED8A569E


I did everything else on listed and I get no icon??

Please help

---

### Post by IDeus on 2006-09-16
Ok, I now have the icon but I am unable to set compiz as the window manager.  When I try to start compiz from the console window I get 

meman@HOMER:~$ sudo compiz
XGL Absent, assuming AIGLX
compiz: GLX_EXT_texture_from_pixmap is missing
compiz: Failed to manage screen: 0
compiz: No manageable screens found on display :0.0
meman@HOMER:~$ sudo gedit /usr/bin/compiz-start

---

### Post by Tris2006 on 2006-09-17
Ok question, since im a noob to linux and ubuntu still, I have tryed getting aiglx set up on my laptop twice now. and both times my X server would not start. I would try it again, but first I want to know how I can return back to normal settings with out having to reinstall ubuntu.
I saw some one say they used "startx" Does this work?:confused:

---

### Post by Jingo on 2006-09-17
I am having troubles getting DRI working.

Until recent kernel update everything worked. But now the "radeon" and "drm" module won't load.

I tried reinstalling linux-dri-modules-common and the specific dri-modules... but didn't help.

I'am using the open source driver "radeon" and aiglx.

Anyone else having troubles loading the modules and getting direct rendering working?
Help would be very much appreciated.

---

### Post by seshomaru samma on 2006-09-17
Thank you for a good How-to
I manage to get it working , but I don't get an icon
I can only start it with a command compiz-start
so how do I stop it?
and how do I change themes?

---

### Post by thecresta on 2006-09-17
Hey All

Just followed this guide - but now xserver errors on bootup, saying cant find nvidia module, amongst others. :roll: 

Can't boot to gnome now. Can anybody help?

---

### Post by mjpatey on 2006-09-17
Well, I tried this, and there were some errors along the way, but I defiantly pressed forward knowing I might cause a splosion, and I did; X broke.

I did backup my xorg.conf file (and have since reverted to the backup), but not so for my sources.list or my gdm.conf-custom file.

For these two files without backup, can I just remove the edits I made to restore my system?  Or am I beyond hosed at this point due to changes made outside these files (all that updating and copying we did directly from the terminal prompt)?

-Mark

---

### Post by joFo on 2006-09-17
Thanks for this gude! 

One thing you might add is that you have to use sudo for this: 
cp /usr/lib/xorg/modules/drivers/* /usr/lib/xorg-air/modules/drivers
cp /usr/lib/xorg/modules/input/* /usr/lib/xorg-air/modules/input"

I guess most ppl figure this out by them self :)

//joFo

---

### Post by prince_niceguy on 2006-09-18
will this work with (in)famous SiS 760 graphics card???

please tell me yes... :-)... if so I will try this out... else will  not experiment with it...

i can see glxgears using Mesa... just FYI in case it helps...

---

### Post by chaosgeisterchen on 2006-09-19
Hi there.

I am using a Radeon X300 with XOrg 7.1-ati-opensource-drivers, which should work according to Fedora Wiki.

I followed your guide but the last 2 actions do not work for me.

On the one hand I cannot copy the files as there is no xorg-air-driver-directory and on the other hand, as I am using KDE, I have to change the settings for KDM. Can anyone help me getting farther :)?

Thanks in advance.

~cg

---

### Post by StayPuft on 2006-09-19
E: Couldn't find package linux-dri-modules-2.6.15-27-386

Why so many problems with Repositories? Last time there was an AIGLX version that worked for everyone they promptly removed the gset-compiz package. Are people TRYING to scare users away from Linux? Everyday Vista seems like a more viable solution....

---

### Post by chaosgeisterchen on 2006-09-20
I did not even know that a 2.6.15-27 - Kernel is already out...

could be the reason why there are no DRI-modules for it yet.

---

### Post by StayPuft on 2006-09-20
I didnt specify that Kernel, I used this command to get that output:
```
sudo apt-get install linux-dri-modules-common linux-dri-modules-`uname -r`
```

Simply following the tutorial in the first post of this thread.... Any ideas?

---

### Post by Cl1mh4224rd on 2006-09-20
> **Cl1mh4224rd said:**
> Edit #3:
I took a closer look at the error log. The fglrx driver is failing to load because it's expecting Xorg 7.0, but Xorg-air is 7.1...
A number of days ago I came to the realization that I'm just in the wrong thread.

AIGLX doesn't work with ATI's proprietary drivers. D'oh. So, I went to GLX and it's all purty. :)

---

### Post by dubbreak on 2006-09-20
> **Yerakon said:**
> [http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card]("http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card")

Perfect! 24 bit and borders!;) 

If dont like the "zooming" when rotate the cube then run
"gconf-editor":  apps->compiz->rotate and set "zoom" to "0"

The extra bits in that got me going. There is an extra repo, and a few other packages (including themes):
```
 sudo apt-get install cgwd cgwd-themes csm
```

Running pretty well on my craptastic intel onboard video (855GM). Rain and water don't work :P, and I definitely can't run the blur effects but other than that it's pretty darn cool.

---

### Post by dubbreak on 2006-09-20
> **StayPuft said:**
> I didnt specify that Kernel, I used this command to get that output:
```
sudo apt-get install linux-dri-modules-common linux-dri-modules-`uname -r`
```

Simply following the tutorial in the first post of this thread.... Any ideas?

I installed the version for the last most recent kernel (26 vs 27) and it seems to be working fine (plus I'm sure an updated version will come soon).

So you can try (change 386 so it is appropriate for your system of course):
```
sudo apt-get install linux-dri-modules-common linux-dri-modules-2.6.15-26-386
```

---

### Post by justinflavin on 2006-11-03
thats good to know - thanks.

i was having the same .27 dri-module issue as well.  

i'll give .26 a try.

---

### Post by krypto_wizard on 2006-11-04
Thanks, it was a help to me and my gf.

---

### Post by electroconvulsive on 2006-11-16
> **dubbreak said:**
> I installed the version for the last most recent kernel (26 vs 27) and it seems to be working fine (plus I'm sure an updated version will come soon).

So you can try (change 386 so it is appropriate for your system of course):
```
sudo apt-get install linux-dri-modules-common linux-dri-modules-2.6.15-26-386
```

So is this actually safe to do if you have the v27 kernel installed?

---

### Post by prince_niceguy on 2007-04-18
any idea if x1300 ATI supports aiglx???

---

