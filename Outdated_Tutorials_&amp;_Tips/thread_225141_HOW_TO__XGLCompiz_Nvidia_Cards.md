---
title: "HOW TO : XGL/Compiz Nvidia Cards"
date: 2006-07-29
forum: Outdated Tutorials &amp; Tips
---

### Post by chokes on 2006-07-29
Hello,

For those who have nVidia cards and Ubuntu, here is a small howto. This howto configure your gdm to use Xgl. Xgl is run by root, not the user. (not startxgl.sh script). This howto is based on RacerII and mstlyevil howto.

1. Configure nVidia acceleration

If you do not have nVidia 3D acceleration enable, follow this steps :

1.1. Install packages

You must install restricted modules for your kernel to have the nVidia blob. You may prefer use linux-686, linux-686-smp (for core duo) or linux-k7 to optimise with your cpu. Be sure you have restricted repo enable. You might also want to install nvidia-glx-legacy for no more supported nVidia cards.

Do it with System->Adminitration->Synaptic Package Manager or with the following cmd line :

```

sudo apt-get install nvidia-glx nvidia-kernel-common linux-386
``` 

1.2. Configure Xorg

```
sudo gedit /etc/X11/xorg.conf
``` 

Then do the following changes :

1.2.1 Modules

Int the "Module" section comment lines for GLcore and dri and set the glx directive.

```
Section "Module"
 Load "bitmap"
 Load "ddc"
# Load "dri"
 Load "extmod"
 Load "freetype"
 Load "glx"
 Load "int10"
 Load "type1"
 Load "vbe"
EndSection
``` 
1.2.2 nVidia's driver

In the "Device" section set :

```
 Driver "nvidia"
 Option "NoLogo" # This option disable the startup logo. optional.
 Option "RenderAccel" "true"
 Option "Triplebuffer" "true"
``` 
1.2.3 Screen depth

In the "Screen" section set :

 ```
DefaultDepth 24
``` 
Done.

2 Install great stuffs

2.1 Enable extra repos

```
sudo gedit /etc/apt/sources.list
``` 
Add this:
```
deb http://www.beerorkid.com/compiz dapper main aiglx
deb http://media.blutkind.org/xgl/ dapper main aiglx
deb http://ubuntu.compiz.net/ dapper main aiglx
``` 
Receive quinn GPG key for package check. You may do it with System->Administration->Software Properties. Download Quinn key file at [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) and add it with the "Import Key File" button. Or simply do :

```
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
wget http://media.blutkind.org/xgl/quinn.key.asc -O - | sudo apt-key add -
wget http://ubuntu.compiz.net/quinn.key.asc -O - | sudo apt-key add -
``` 
Update package list, Reload with synaptic or do :

```
sudo apt-get update

``` 
2.2 Install the packages

Now you need to install those packages :

```
sudo apt-get install xserver-xgl compiz compiz-core compiz-plugins compiz-gnome gnome-compiz-manager cgwd cgwd-themes
``` 
Remember to keep your packages up to date.

2.3 Keep up to date

Upgrade all packages using Synaptic, update-manager or :
```

sudo apt-get dist-upgrade
``` 
3. Configure GDM

```
sudo gedit /etc/gdm/gdm.conf-custom
``` 
And complete the servers section 

```
[servers]
0=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true
``` 
Now restart your computer.

GDM should launch normally. Alt Gr might not work on some keyboard (e.g. french keyboard). If you need Alt Gr to type your password, you'd better change your passowrd. To do so, switch to VT1 with Ctrl+Alt+F1. Login. Change your password with

```
passwd
``` 
answer questions and switch back to VT7 with Alt+F7.

4. Launch compiz

Once you're logged in, metacity is still your window manager. You may want to reconfigure your keyboard layout with System->Preference->Keyboard , tab Layout. You'll have an icon im notification aera right click on it and select : GL Desktop
_[IMG]http://ubuntuforums.org/attachment.php?attachmentid=15059&stc=1&d=1156928069[/IMG]_
Now you can start and stop compiz as you wish :)
You have more option in preferences you can set plugins and change windows decoration :) 

That's all guys.&

Thanks to all people that made it possible. First David Reveman and QuinnStorm.

I run this on Athlon 64 3000+ with 1GB of ram and a 7800GT

Review and comments are very welcomes.

Here the link that i have taken the sources to make the HOWTO :)
[http://www.compiz.net/viewtopic.php?id=652](http://www.compiz.net/viewtopic.php?id=652)
i just wanted to make it more easy ;)

Here A link to the wiki page for configuring Compiz in Gconf-editor:)
[https://help.ubuntu.com/community/CompositeManager/ConfiguringCompiz#xprop](https://help.ubuntu.com/community/CompositeManager/ConfiguringCompiz#xprop)

Edit: (Friday, 25 August 2006) : Big update!!!! I modified the sources for more package and aiglx(not tested) and removed The compiz-start script an replaced it with gnome-compiz-manager so no need to have a script! 

Have Fun!!!

---

### Post by wate on 2006-08-10
Thank you, it was very helpful to me so everything works now.

---

### Post by Sammi on 2006-08-10
Yeah I followed a similar HOWTO I found somewhere else. This is the right way to do it ;)

---

### Post by MikeEnIke on 2006-08-11
mike@mike:~$ sudo apt-get install xserver-xgl compiz-gnome gset-compiz
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gset-compiz
mike@mike:~$


?? Can't find it?


EDIT: Nevermind, I went and found another mirror that had the file. It's all installed except for the decorations, anyone have an idea? ```
mike@mike:~$ sudo apt-get install cgwd gcompizthemer gcompizthemer-themes
Reading package lists... Done
Building dependency tree... Done
cgwd is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  cgwd: Conflicts: gcompizthemer
  gcompizthemer-themes: Depends: gcompizthemer (>= 0.18)
E: Broken packages

```

---

### Post by chokes on 2006-08-11
oh! sorry you have to install the package : cgwd-themes ;)i didnt edit the tread sice they merge gcompizthemer directly in cgwd

---

### Post by Intangir on 2006-08-12
how do i set it to allow full screen 3d apps to have direct rendering?

isnt there a way?

---

### Post by Alan_Hill on 2006-08-12
hic.
I've got my X Desktop crashed

---

### Post by MikeEnIke on 2006-08-12
> **Intangir said:**
> how do i set it to allow full screen 3d apps to have direct rendering?

isnt there a way?

[http://ubuntuforums.org/showthread.php?t=176636&highlight=xgl%2Fcompiz](http://ubuntuforums.org/showthread.php?t=176636&highlight=xgl%2Fcompiz)

Doing that should should work. Worked fine for me.

---

### Post by mattlach on 2006-08-12
> **MikeEnIke said:**
> mike@mike:~$ sudo apt-get install xserver-xgl compiz-gnome gset-compiz
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gset-compiz
mike@mike:~$


?? Can't find it?


EDIT: Nevermind, I went and found another mirror that had the file.

I am having this same problem, but I can't seem to find the gset-compiz deb anywhere.   How did you find it?

Thanks,
Matt

---

### Post by Sammi on 2006-08-12
Did you enable the extra repositories like decribed in step 2.1 in the howto?

---

### Post by chokes on 2006-08-12
here some new repositories :) 

```
deb http://www.beerorkid.com/compiz dapper main
deb http://media.blutkind.org/xgl/ dapper main
deb http://ubuntu.compiz.net/ dapper main
```

---

### Post by mattlach on 2006-08-12
> **chokes said:**
> here some new repositories :) 

```
deb http://www.beerorkid.com/compiz dapper main
deb http://media.blutkind.org/xgl/ dapper main
deb http://ubuntu.compiz.net/ dapper main
```

I appreciate your help, but even after adding these new sources to sources.list I still get the same error, and I can't seem to find the gset-compiz deb myself anywhere else :(

```
# sudo apt-get install xserver-xgl compiz-gnome gset-compiz
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gset-compiz
```

Could it be because I am running an AMD64 install?  Is the gset-compiz deb marked i386 only, maybe?


Appreciate any help!

Thanks,
Matt

---

### Post by chokes on 2006-08-12
this How to i only for i386 sorry... anyway you can change setting in gconf-editor In: apps/compiz/plugins/

---

### Post by mattlach on 2006-08-12
> **chokes said:**
> this How to i only for i386 sorry... anyway you can change setting in gconf-editor In: apps/compiz/plugins/

Ahh..  That would explain it then.  Thanks for the help!

--Matt

---

### Post by chokes on 2006-08-13
> **Alan_Hill said:**
> hic.
I've got my X Desktop crashed

You can always press ALT+F2 and type:
```
compiz-start
```

This will restart compiz
you can enter this line in a terminal:)

---

### Post by aussiedini on 2006-08-14
Thanks Chokes. This seems to be the only tutorial on this subjectthat worked for me. Got to love eye candy. 

Thanks again.

---

### Post by chokes on 2006-08-14
nice to know that :)

---

### Post by Boomy on 2006-08-14
I got everything installed and working, but it won't keep settings and I get this error. 

Couldn't load settings.  Reverting to defaults.
Couldn't load theme.  Reverting to defaults.

---

### Post by Boomy on 2006-08-14
BTW, how to I switch to Xorg, I don't see the option in "sessions"

---

### Post by chokes on 2006-08-14
> **Boomy said:**
> BTW, how to I switch to Xorg, I don't see the option in "sessions"
you have to add it in session :
```
compiz-start
```
and restart x after ;)

---

### Post by Boomy on 2006-08-14
I don't know much. You are saying to restart x after starting compiz? How do I restart x? It says command not found when I type it in the terminal.

---

### Post by Boomy on 2006-08-14
Shit my window decoration is gone. I've switched back to booting to xorg by undoing the changes to xorg.conf, etc. How can it back to normal?

---

### Post by chokes on 2006-08-14
follow the guide closer ;) you have just to copy and paste the text```
5. Launch compiz

Once you're logged in, metacity is still your window manager. You may want to reconfigure your keyboard layout with System->Preference->Keyboard , tab Layout. Launch a terminal and exécute compiz-start

Code:

compiz-start


Try compiz. Configure it with Applications->Accessories->Gset Compiz. Enable all plugins except gconf-dump, miniwin and dock (miniwin an dock seems very buggy for 0.0.10-0ubuntu8 version and earlier).

If all work, you may want to launch compiz for each session. Launch System->Preferences->Sessions in tab "Startup Programms" add:
Code:

compiz-start


```

---

### Post by Boomy on 2006-08-14
Ok I'm back to normal. It says if it all works add that. It all wasn't working. :)

---

### Post by chokes on 2006-08-14
follow the guide ;)

```
6. Get the new decorations

Code:

sudo apt-get install cgwd cgwd-themes

Now type in a terminal :

Code:

cgwd --replace

To enable the new decoration and use compiz themer in: System - preferences to change the themes.
It' possible that you dont see the buttons on the titlebar if it does that go in compiz themer again and click on the arrow at the botom of the window
then go to the tab: shadow/titlebar at the title bar layout select: Normal layout

```

---

### Post by chokes on 2006-08-14
on witch architechture are you?

---

### Post by eljaco on 2006-08-15
I have a really annoying problem: whenever I turn my computer on, I get the command line login, instead of the Ubuntu GUI login. In order for me to get to the GUI, I have to go into /etc/init.d and then run > sudo gdm stop so that X will start. Everything except for water seems to be working after that. I would like to know how to solve this problem and what may be causing it. I am using Dapper (x86) with a NV GeForce 4400 Go AGP x8.
If you need anything else, let me know.

Thanks!

---

### Post by slimdog360 on 2006-08-15
works a treat

---

### Post by chokes on 2006-08-15
> **eljaco said:**
> I have a really annoying problem: whenever I turn my computer on, I get the command line login, instead of the Ubuntu GUI login. In order for me to get to the GUI, I have to go into /etc/init.d and then run  so that X will start. Everything except for water seems to be working after that. I would like to know how to solve this problem and what may be causing it. I am using Dapper (x86) with a NV GeForce 4400 Go AGP x8.
If you need anything else, let me know.

Thanks!

are you shu you have configured GDM correctly?

```
3. Configure GDM

Code:

sudo gedit /etc/gdm/gdm.conf-custom


And complete the servers section

Code:

[servers] 0=Xgl
 
[server-Xgl] name=Xgl server command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer 
flexible=true


```
You have to do exactly as it seen ;)

---

### Post by eljaco on 2006-08-15
This is my gdm.conf-custom file:
```
# GDM Configuration Customization file.
#
# This file is the appropriate place for specifying your customizations to the
# GDM configuration.   If you run gdmsetup, it will automatically edit this
# file for you and will cause the daemon and any running GDM GUI programs to
# automatically update with the new configuration.  Not all configuration
# options are supported by gdmsetup, so to modify some values it may be
# necessary to modify this file directly by hand.
# 
# To hand-edit this file, simply add or modify the key=value combination in
# the appropriate section in the template below.  Refer to the comments in the
# gdm.conf file for information about each option.  Also refer to the reference
# documentation.
# 
# If you hand edit a GDM configuration file, you should run the following
# command to get the GDM daemon to notice the change.  Any running GDM GUI
# programs will also be notified to update with the new configuration.
#
# gdmflexiserver --command="UPDATE_CONFIG <configuration key>"
#
# For example, the "Enable" key in the "[debug]" section would be specified by
# "debug/Enable".
#
# You can also run gdm-restart or gdm-safe-restart to cause GDM to restart and
# re-read the new configuration settings.  You can also restart GDM by sending
# a HUP or USR1 signal to the daemon.  HUP behaves like gdm-restart and causes
# any user session started by GDM to exit immediately while USR1 behaves like
# gdm-safe-restart and will wait until all users log out before restarting GDM.
# 
# For full reference documentation see the gnome help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# [http://www.gnome.org/projects/gdm/](http://www.gnome.org/projects/gdm/)
# 
# NOTE: Lines that begin with "#" are considered comments.
# 
# Have fun!

[daemon]

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]# Override display 1 to use Xgl
0=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true

```

---

### Post by chokes on 2006-08-15
sorry i dont see nothing that should cause this trouble... so have you followed another howto before?

---

### Post by eljaco on 2006-08-15
So I'm pretty sure I used this one: [http://www.ubuntuforums.org/showthread.php?t=148351](http://www.ubuntuforums.org/showthread.php?t=148351)

Used the > Xgl/compiz on an Nvidia video card and also ran the things that I saw were different in Xgl/compiz on an Nvidia video card with KDE since I used to use KDE a lot before. Now that I am off that and using GNOME full time, I only care about XGL on GNOME. Could this have any effects? When I boot up, I get the blue KUBUNTU loading page, which I would like to change to the old UBUNTU one, but don't know how. This could potentially be the problem, but I don't see why. I ran Synaptic and tried to remove everything KDE and KUBUNTU and still got the blue KUBUNTU Loading thing when I booted up.

Thanks so much!

---

### Post by chokes on 2006-08-15
> **eljaco said:**
> So I'm pretty sure I used this one: [http://www.ubuntuforums.org/showthread.php?t=148351](http://www.ubuntuforums.org/showthread.php?t=148351)

Used the  and also ran the things that I saw were different in Xgl/compiz on an Nvidia video card with KDE since I used to use KDE a lot before. Now that I am off that and using GNOME full time, I only care about XGL on GNOME. Could this have any effects? When I boot up, I get the blue KUBUNTU loading page, which I would like to change to the old UBUNTU one, but don't know how. This could potentially be the problem, but I don't see why. I ran Synaptic and tried to remove everything KDE and KUBUNTU and still got the blue KUBUNTU Loading thing when I booted up.

Thanks so much!

The best way to use this how to is on a fresh install of ubuntu maybe something is entering in conflict with it....

---

### Post by eljaco on 2006-08-15
K, thanks, I'll ask the other thread to see if they know.

Thanks anyways!

---

### Post by chokes on 2006-08-15
i thinking of something... are you using KDM or GDM ? maybe your using KDM so that the problem ;) you have to switch to GDM

---

### Post by eljaco on 2006-08-16
I think I changed this already, but correct me if I am wrong.

(from /etc/X11/default-display-manager)

```
/usr/sbin/gdm
```

Is there something else that needs to be changed? It might just be the KUBUNTU image that replaced the UBUNTU one, but somehow I doubt it's that stupid - I am guessing there is still some KUBUNTU stuff in my computer...even though I searched for "KDE" and "KUBUNTU" in Synaptic and removed everything I didn't need.

---

### Post by michaelslarsen on 2006-08-16
That worked great- alot easier than on OpenSUSE. One question.. How do you get this to auto-start at login so that it just runs and you do not have to type "the future"

Thanks again!

---

### Post by eljaco on 2006-08-16
> **michaelslarsen said:**
> That worked great- alot easier than on OpenSUSE. One question.. How do you get this to auto-start at login so that it just runs and you do not have to type "the future"

Thanks again!

Go to System -> Preferences -> Sessions -> Startup Programs
Add "thefuture" or whatever it is you called it. That should do it.

---

### Post by starscalling on 2006-08-16
dam
this is great!
quite impressive....
though i would like to be able to have the window im not active on not darken so much as it makes my vids sux ~___~
using this with dual mons :D

---

### Post by chokes on 2006-08-16
> **starscalling said:**
> dam
this is great!
quite impressive....
though i would like to be able to have the window im not active on not darken so much as it makes my vids sux ~___~
using this with dual mons :D

you can exclude window for the trailfocus plugin in gset-compiz press add and just select the window ;)

---

### Post by erwinquita on 2006-08-16
is it possible to integrate this using xdm as my login manager and icewm as my window manager... I've already installed nvidia driver just fine... or this just works using GDM. Any help would be appreciated.

Thanks! :D

---

### Post by hill on 2006-08-16
Is there a way to disable the mouse gestures? I hate moving my mouse and all the windows move to the center. I dont know what the name of that thing is but its like the mac os epose.

---

### Post by ofimiano on 2006-08-16
This HOWTO was the only way I've been able to get this gorgeous program to work! Thanks a million!! :D :D :D

---

### Post by BKK on 2006-08-16
Hi, I have tried installing this before using a different HOW-TO. Now  When I go to edit my xorg.conf it is an empty file. How can I get it back?

SORRY I had a small x rather than a big X

Thanks

---

### Post by chokes on 2006-08-16
> **hill said:**
> Is there a way to disable the mouse gestures? I hate moving my mouse and all the windows move to the center. I dont know what the name of that thing is but its like the mac os epose.

look at the screenshot ;)

---

### Post by BKK on 2006-08-16
Pretty awesome HOWTO. It works great thank-you!

---

### Post by chokes on 2006-08-16
> **erwinquita said:**
> is it possible to integrate this using xdm as my login manager and icewm as my window manager... I've already installed nvidia driver just fine... or this just works using GDM. Any help would be appreciated.

Thanks! :D

sorry i never used XDM so.. i dont know if its possible maybe you can use gdm with a xubuntu skin :rolleyes:

---

### Post by redx666 on 2006-08-20
The latest update of compiz was a tad buggy on my system, the titlebar went missing after last night's update.  I found that it was the update coming from "deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main" that was causing the issue.        Disable that repository, do a reload, then upgrade all, which should upgrade 3 packages only related to compiz.  Then reboot or use ctrl+alt+backspace and try running compiz-start again.  I hope that helps anyone that had the missing titlebar after upgrading their packages.

---

### Post by jquintero on 2006-08-20
> **hill said:**
> Is there a way to disable the mouse gestures? I hate moving my mouse and all the windows move to the center. I dont know what the name of that thing is but its like the mac os epose.

you can disable the "scale" plugin or adjust to your liking in gconf-editor.

---

### Post by chokes on 2006-08-25
(Friday, 25 August 2006) : Big update!!!! I modified the sources for more package and aiglx(not tested) and removed The compiz-start script an replaced it with gnome-compiz-manager so no need to have a script! and you can stop compiz ;)

Have Fun!!!


P,S : sorry for the last days i lost my internet connection so i was unable to do some update on the tread:)

---

### Post by chokes on 2006-08-25
> **redx666 said:**
> The latest update of compiz was a tad buggy on my system, the titlebar went missing after last night's update.  I found that it was the update coming from "deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main" that was causing the issue.        Disable that repository, do a reload, then upgrade all, which should upgrade 3 packages only related to compiz.  Then reboot or use ctrl+alt+backspace and try running compiz-start again.  I hope that helps anyone that had the missing titlebar after upgrading their packages.

Maybe if you redo the how to i will solve the trouble ;)

---

### Post by nrayever on 2006-08-26
thanks a lot chokes!!! this works better than using automatixbleeder to install it. but i still have a doubt. why...... sorry now i know how to set the window border, hehehehe. sorry forget it.

nice how to!! these one really works!! :D :D 

nrayever

---

### Post by deanjm1963 on 2006-08-26
I must admit, it works a treat! I was a little sceptical, I've avoided trying out XGL until now. I'm reallly impressed, very easy to setup.

---

### Post by S1NGH on 2006-08-26
A very short Ubuntu XGL howto for ATI cards, Dapper 6.06 beta 2
---------------------------------------------------------------
I thought i'd make a howto as it took me a while to get it working on my laptop (with an M200 chipset)

ok, firstly, enable all the repositories and install xorg-server-xgl compiz, compiz-gnome and also make sure any packages such as mesa, glitz and cairo are up to date and that fglrx is installed and enabled in the xorg config

the easiest way to get it up and running without messing up anything is to do this

create a file in your /home/%user% folder called .Xsession (sudo gedit /home/%user%/.Xsession)

#!/bin/sh
# Start up Xgl, compiz, and GNOME
# Run Xgl server on :1, on top of normal X
Xgl :1 -fullscreen -ac -accel xv -accel glx:pbuffer &
# Tell subsequent X programs to access the Xgl server at :1
DISPLAY=:1
# Start Compiz window manager
gnome-window-decorator &
compiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher &
xmodmap /usr/share/xmodmap/xmodmap.us &
# Start GNOME 
exec gnome-session

next you must chmod +x .Xsession

you must next edit your xorg.conf (sudo gedit /etc/X11/xorg.conf)

add these lines under the "Device" section to stop the card randomly locking up
Option "OpenGLOverlay" "off" #this isn't necessary for me
Option "UseInternalAGPGART" "no"
Option "KernelModuleParm" "agplock=0"

log out and in again and Xgl will work, note: if something breaks you can log in with the failsafe session and remove the .Xsession to get back to normal X

I was having problems with my X randomly crashing, I assumed it was due to my Xgl/Compiz versions being old, this wasn't the case, it's simply that shift+backspace causes the Xgl server to shutdown, you can remedy this by adding xmodmap /usr/share/xmodmap/xmodmap.us to .Xsession as above

If you want to get the latest up to take debs try these two repositories (you need both as they both contain vital updates)

deb [http://xgl.compiz.info](http://xgl.compiz.info) dapper main
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main

-------------------------------------------------------------

NVidia users try this
/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo instead and change DISPLAY to 0
You also need the nvidia drivers installed

Z3r0
-------------------------------------------------------------
Dapper + XGL + ATI
-------------------------------------------------------------
**New Dapper Install**
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)
**ATi Drivers Installation**
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.25.18_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.25.18_drivers_in_Ubuntu_Dapper_Manually)
**How To: XGL** - *most likely the second one will work!*
[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)
-------------------------------------------------------------
> =============================================================
--------Kubuntu Xgl Compiz HowTo-----------By Michael Noiesen-------------------------------------02/06/2006
=============================================================

This is my HowTo get Xgl and Compiz working on Kubuntu Dapper. 

I feel this can be applied to ubuntu as well. The main thing is to have your Nvidia card configured correctly before trying to use Xgl/Compiz. 

ATI users please use the ATI guide below.

=============================================================

My system Spec.

AMD XP2500 CPU
512 MB DDR Ram
NVIDIA 6600GT 128MB DDR Video Card

=============================================================

Updated: 18/06/2006
Updated: 24/07/2006
Updated: 17/08/2006

To start I installed Kubuntu dapper, 

Then add the Univerise & Mulitverse Repositories this can be done via the commandline 

=========================================================

"sudo nano /etc/apt/sources.list"

or Thru

KDE Window System - "K -> System -> Adept -> Manage Repositories"

The next step was to update the repository information via commandline 

"sudo apt-get update" then do the system upgrade "sudo apt-get upgrade"

============================================================

The next step is to update to the NVIDIA Propritory Driver this is known as the "nvidia"

============================================================

sudo apt-get install nvidia-glx nvidia-kernel-common linux-restricted-modules-$(uname -r)


O.K. now edit the xorg.conf file

sudo nano /etc/X11/xorg.conf


Edit the "Module" section comment out the lines for GLcore and dri and set the glx directive.

Section "Module"
Load "bitmap"
Load "ddc"
# Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Now in the "Device" section adjust "Driver" Section

Driver "nvidia"
Option "RenderAccel" "true"
Option "AllowGLXWithComposite" "true"

If you want you can disable the NVIDIA startup logo.

Driver "nvidia"
Option "RenderAccel" "true"
Option "AllowGLXWithComposite" "true"
Option "NoLogo"


I found I had now Super key so I added the following to my xorg.conf file under the section InputDevice for Keyboard

Option "XkbOptions" "altwin:super_win"

Mine now looks like this

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
Option "XkbOptions" "altwin:super_win"
EndSection


O.K test your nvidia install to see if it worked, for this I just reboot my system,
you should now be able to login via kdm and you should now be running the nvidia driver.

To confirm do "lsmod | grep nvidia" you should see something like

nvidia 457032 63
agpgart 34888 2 nvidia,via_agp

Also check xorg.conf for the nvidia

To confirm do "cat /etc/X11/xorg.conf |grep nvidia" you should see something like

Driver "nvidia"

Thats it you are now using the NVIDIA propritary Driver :)

============================================================

O.K Now to install the neccessities for your EyE CaNdY.....

============================================================

I then add these repositories to your sources.list file and update your repository information

deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

Now grab Quinn's key.

wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O - | sudo apt-key add -

sudo apt-get update && sudo apt-get upgrade

Once the update and upgrade is complete do

sudo apt-get install compiz xserver-xgl libgl1-mesa libglitz-glx1 compiz-gnome cgwd cgwd-themes compizthemer gconf-editor

Use gconf-editor to change compiz settings and gcompizthemer to set your theme

Accept any package upgrades required.

******************************************************************************************
If you encounter a broken package issue with xserver-xgl do this

sudo dpkg-divert --package xserver-xorg-core --divert /usr/share/man/man1/Xserver.1x.gz.xgl --rename /usr/share/man/man1/Xserver.1x.gz

Now xserver-xgl will install

******************************************************************************************

O.K now we need to set things in place to have Compiz/xgl start automatically.

============================================================

Set-up KDM and Start Script.

============================================================

sudo nano /etc/kde3/kdm/kdmrc

find the line that reads ServerCmd=/usr/bin/X -br

Change it to read

ServerCmd=/usr/bin/xgl :0 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer

Then add the following in the [X-*-Core] section (thus after [X-*-Core]). If these line already exsist then comment them out.

OpenRepeat=5
OpenDelay=15
OpenTimeout=120
ServerTimeout=30

Now for the eyecandy file

sudo nano ~/.kde/Autostart/eyecandy

#!/bin/sh
# Start cgwd and log results
cgwd & > ~/cgdw-window.log 2>&1 &
#start compiz and log results
compiz --replace gconf & > ~/compiz.log 2>&1 &
#Map Keyboard
xmodmap /usr/share/xmodmap/xmodmap.us
#Fix Shift+BackSpace
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"


Set permissions on file

sudo chmod +x ~/.kde/Autostart/eyecandy

============================================================
For detailed information on the various plugin settings check this out

[https://wiki.ubuntu.com/CompositeManager/ConfiguringCompiz](https://wiki.ubuntu.com/CompositeManager/ConfiguringCompiz)

============================================================

O.K now its time to restart...Fingers crossed...

After the reboot login to kde.

If the set up and configuration completed was successfull then you should be running xgl/Compiz

============================================================

THE SECTION BELOW HAS NOT CHANGED AND WILL BE UPDATED SHORTLY


============================================================

The following are all related to entries in GCONF-EDITOR

If all went well you should be in the Compiz/Xgl Desktop now the first thing that I do is open
gconf-editor and check that the plugins are in the apps -> compiz listing. 

The next thing to do is check that the plugins are loaded and in the correct order.

apps -> compiz -> General -> allscreens -> options -> active_plugins the order needs to be
correct, you may need to add any missing plugins here.

This is the correct order at the time I wrote this HowTo

gconf,decoration,dock,wobbly,state,fade,minimize,cube,rotate,zoom,scale,move,
resize,place,switcher,water,bs, ** See Below New Plugin - - Neg

Miniwin goes out if using Dock, if using miniwin, you may put it before decoration.

Ideal order of things if there is too much buggy behaviour.

gconf,decoration,wobbly,fade,minimize,cube,rotate,zoom,scale,move,resize,place,switcher

I don't like Dock or Miniwin so I leave them out, they are also a bit buggy at the moment.

############################################################
Current order of my plugins (14/06/2006)

gconf,decoration,wobbly,fade,minimize,cube,rotate,zoom,scale,move,resize,place,state,
switcher,trailfocus,water,bs,widget,neg

############################################################
*******************************************************************************************

From : [http://www.compiz.net/viewtopic.php?id=569](http://www.compiz.net/viewtopic.php?id=569) 03/06/2006

gconf,decoration,dock,wobbly,fade,minimize,cube,rotate,zoom,scale,move,resize,place,state,
switcher,trailfocus,water,bs,widget,neg*

*neg is NEW (edit date : 13/6/2006)

Miniwin goes out if using Dock, if using miniwin, you may put it before decoration.

Ideal order of things if there is too much buggy behaviour.

gconf,decoration,wobbly,fade,minimize,cube,rotate,zoom,scale,move,resize,place,switcher

Moppsy has put it in a bit more poetic way.

Maybe this will help
-------------------------------
gconf must be before decoration, wobbly, fade, cube and scale
decoration must be before wobbly, fade, cube and scale
transset must be before wobbly and fade
wobbly must be before fade, cube and scale
state must be after place
fade must be before cube and scale
minimize must be before cube and scale
cube must be before scale
rotate must be after cube
zoom must be after cube

*******************************************************************************************
============================================================

You can also confirm the plugins exsist by looking in /usr/lib/compiz if you do "ls /usr/lib/compiz" it should return

libbs.so
libcube.so
libdecoration.so
libdock.so 
libfade.so
libgconf-dump.so
libgconf.so
libminimize.so
libminiwin.so
libmove.so
libneg.so * Added (13/6/2006) New Plugin
libplace.so
libresize.so
librotate.so
libscale.so
libstate.so
libswitcher.so
libtrailfocus.so
libwater.so
libwidget.so
libwobbly.so
libzoom.so

============================================================

To set up various options available from the plugins we use gconf-editor to adjust these

apps -> plugins -> 

Well this is the end of this howto at the moment I will leave it up to you to export the various changes that can be made to the plugins, this is mainly the key/mouse combinations used to activated the plugins.....

============================================================

NOTE: you do note need to restart X or compiz when you change plugin settings...

============================================================
Install xwinwrap

sudo apt-get install xwinwrap

Here are some xwinwrap examples

xwinwrap -ni -argb -fs -s -st -sp -b -nf -- /usr/lib/xscreensaver/glmatrix -window-id WID -delay 10000

xwinwrap -ni -argb -fs -s -st -sp -b -nf -- /usr/lib/xscreensaver/plasma -window-id WID &

xwinwrap -ni -argb -fs -s -st -sp -b -nf -- /usr/lib/xscreensaver/plasma -window-id WID --maxfps 25 --nice --speed 2 --resolution 20

xwinwrap -ni -argb -fs -s -st -sp -b -nf -- /usr/lib/xscreensaver/bubble3d -window-id WID -delay 10000

xwinwrap -ni -o 0.6 -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet /path/to/movie.mpg

============================================================
If you experience problems with key mapping add xmodmap

sudo apt-get install xmodmap

then add 

xmodmap /usr/share/xmodmap/xmodmap.us

to the eyecandy file after #Fix Shift+BackSpace
**_Additional links_**
[http://www.linuxjournal.com/node/1000081](http://www.linuxjournal.com/node/1000081)
[http://www.compiz.net/viewtopic.php?id=359](http://www.compiz.net/viewtopic.php?id=359)

I just though that this extra information might be helpful to all. If you want you can merge this post with the first and make a proper update so that we can have a sticky or something.

---

### Post by chokes on 2006-08-26
Hi S1GHT

I will be cool to make an howto tha ca take my reps in that way ... it should be the same things on Nvidia card And ATI cards so if someone have an ATI card it will be good to test it:) but with my repos!!!
vbmenu_register("postmenu_1424674", true);

---

### Post by deol on 2006-08-30
Thanks so much Chokes!  Your directions where easy to follow and I had it up and running in no time.  ;)

---

### Post by robio376 on 2006-08-30
Hey Chokes it worked great with my Nvidia 7300GT. But one question how do you make the window borders sticky?

---

### Post by chokes on 2006-08-30
you can disable the wobly plugin in the preferences of gnome-compiz-manager ;)

---

### Post by nrayever on 2006-09-03
hey chokes!!

i have some questions here. i was trying to play some games that need 3d acceleration. but cedega tells me that the test of opengl direct rendering fails!

so, do u know a method to play games using the installed version of xgl/compiz from your howto??

i hope you could help me with this. thanks a lot.

nrayever

---

### Post by chokes on 2006-09-04
for now XGL doesnt support gaming..... so youll have to wait after aiglx support from nvidia:(

---

### Post by abu_nawas on 2006-09-06
it doesn't work. my titlebar is gone. help pliz

---

### Post by Sleig on 2006-09-06
Hi there. I have a similar problem. Been using XGL/compiz for ages with no problems. Now i have installed gnome-compiz-manager but when i click GL Desktop I just lose the title bar etc. Compiz still starts fine with compiz-start. Any ideas?

---

### Post by S1NGH on 2006-09-06
check this:
[http://ubuntuforums.org/showpost.php?p=1460710&postcount=11](http://ubuntuforums.org/showpost.php?p=1460710&postcount=11)

---

### Post by blacksea on 2006-09-06
hi hi hi it work well thanks

---

### Post by Jammy_Stuff on 2006-09-16
I can't find gnome-compiz-manager.

Help!

---

### Post by ironfistchamp on 2006-09-16
I can't find it either. Well I got the source but dependencies I couldn't satisfy. Anyone got a deb?

Thanks

Ironfistchamp

---

### Post by hoagie on 2006-09-24
I got the new repos but cgwd and cgwd-theme has no installation candidate and compiz-plugins has broken dependecies. Em what's going on?

---

### Post by chokes on 2006-09-24
its because quinn is making the transition to beryl and for now the repos are down so we 'll have to wait for this

[http://www.compiz.net/topic-4591-beryl-informations-announcement](http://www.compiz.net/topic-4591-beryl-informations-announcement)

---

### Post by hoagie on 2006-09-24
Oh thank you for the reply. Ok then I'll try later

---

### Post by hoagie on 2006-09-24
I couldn't find the gnome-compiz-manager package. Is this because of beryl too is something going on with my system?

---

### Post by S1NGH on 2006-09-24
> **hoagie said:**
> I couldn't find the gnome-compiz-manager package. Is this because of beryl too is something going on with my system?
did you update? because i think that will cause problems, right now i am using aiglx, try to stay away from compix/xgl updates until beryl is finally out, otherwise you will be just messing up somewhere.

---

### Post by hoagie on 2006-09-24
No well I never did install the whole thing because the repositories are down. Just asking

---

### Post by Cronjob on 2006-09-24
The problem I have run into with this and all the other XGL tutorials is that all the compiz stuff is nowhere to be found, regardless of what apt-get sources I include. Either the compiz-plugin version it needs is too new for what is going ot be installed or the cgwd package isn't found or the compiz-manager one isn't found, etc.

I think I'll wait awhile on this one. Hopefully not so long that I have to wait until support is built into the next Ubuntu release, of course. :)

---

### Post by raven65az on 2006-09-24
my problem is driving me nuts...I have everything installed that the forums suggest, however when I type compiz start,I get this

root@raven-laptop:~# compiz start
xvinfo:  Unable to open display
XGL Absent, assuming AIGLX
compiz: Couldn't open display

Synaptic shows that XGL is installed...and I cant get anywhere with installing AIGLX...all the rep's seem depricated or just gone?

any suggestions?

Thanks, Scott

---

### Post by hoagie on 2006-09-25
I still can't find the packages. Does anyone else has the same problem or is it just me?

---

### Post by SagnaB on 2010-03-04
[SOLVED]

I have no "module" section in my xorg.conf file.

This is my conf file:

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder63)  Tue Oct 20 21:01:12 PDT 2009

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Tue Oct 20 21:00:15 PDT 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic E70-3"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 120.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
EndSection

Section "Screen"

# Removed Option "metamodes" "1280x1024 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1152x864 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```I am trying to enable visual effects and or compiz. When ever I try to enable them, it says it FAILS,  but doesn't explain why. I figured it'd be down to a drivers thing. I get stuck following these steps as my xorg.conf appears not to have a modules section.
What am I doing wrong?

Edit: I am running Ubuntu Studio 9.10, GeForce 7600 GS, ACER F89M board, P4 3.0Ghz cpu

EDIT x2: All fixed thanks to [http://ubuntuforums.org/showthread.php?t=481887](http://ubuntuforums.org/showthread.php?t=481887)

---

### Post by Sbtaz on 2011-01-01
I'm new to Linux. Anyway I would like to try to swap Nvidia drivers from 260.19.29 to
260.19.06. AMD 64 Geforce 6150SE.

My problem is, when I try to enable the "cube", my window grouping bar locks up. The 
wobbly works. I tried ctrl-Alt. but I never did get the cube to work. Any ideas? I don't
have the foggiest idea how.

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

