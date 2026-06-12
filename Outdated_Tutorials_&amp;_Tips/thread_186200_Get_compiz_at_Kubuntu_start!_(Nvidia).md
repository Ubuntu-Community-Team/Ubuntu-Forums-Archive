---
title: "Get compiz at Kubuntu start! (Nvidia)"
date: 2006-06-01
forum: Outdated Tutorials &amp; Tips
---

### Post by chadwick359 on 2006-06-01
Hey there, all After a long break due to school and other concerns, I had to ditch any hope of keeping this HowTo up to date, but now i should be able to make sure it doesn't fall so woefully behind as it has this time. For discussions about configuring compiz, plugins, and the such, i would suggest goint over to [http://compiz.net](http://compiz.net) it's a good forum, and almost always up to date.

[COLOR="Red"]NOTICE[/COLOR]: ATI users, as of right now, I am (still) suggesting that you do not attempt to use this guide. I have left the Ati apecific tags on the howto, but if you use them, don't expect them to work. However, if any Ati users are feeling brave and would like to try this, I would appreciate having the extra info to determine what your hardware has a problem with.

(NOTE: This first part is for nVidia users ONLY. For ATI, you guys are on your own for actually installing the driver untill i get this up to speed for you)

First off, let's get all the sources we are going to need, as well as QuinnStorm's gpg key. Add

```
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main
```

and 

```
deb http://www.beerorkid.com/compiz/ dapper main
```

To your /etc/apt/sources.list file. Note, you will have to edit this as root, so use 'kdesu kate' from a terminal. (without the quotes) After that is done, make sure to run 

```
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
```

to get  Quinn's key. After all of this is done, make sure to run 'sudo apt-get  update' to make sure all the repos you need are in correctly and available.

Next, install the latest nVidia drivers, as well as XGL and compiz from the repos, with 

```
sudo apt-get install nvidia-kernel-common nvidia-glx compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome gconf-editor gset-compiz
```

([COLOR="#ff0000"]ATI[/COLOR] users: use this same command but don't include nvidia-kernel-common or the nvidia-glx)

Next, we need to make sure that the driver is working, so fire up 

```
kdesu kate 
```

and open your /etc/X11/xorg.conf file.First we need to comment out the 'GLcore' and 'dri' modules with the trusty #, and make sure that the 'glx' module is loading.

```
#       Load    "GLcore"
#       Load    "dri" 
          Load "glx"
```

IMPORTANT: [COLOR="#ff0000"]ATI[/COLOR] users, do NOT comment out 'dri', you'll need it.

Next, we have to move down to the device entry for your graphics card, where we are going to tell it to use the newly installed driver, as well as enable acceleration and compositing. Basically, edit it to look like this. (Thanks PoofyHairGuy, I started using this from one of your earlier eye candy threads)

```
Section "Device"
	Identifier          "YourCardHere" <-- Don't change me!
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option 		"RenderAccel" 		"true"
	Option 		"AllowGLXWithComposite" "true" 
EndSection
```

For [COLOR="#ff0000"]ATI[/COLOR]: insert fglrx instead of nvidia,and ignore the RenderAccel and AllowGLX lines alltogether

Next, we need to make sure that the default color depth is set to 24, (16 makes compiz freak out pretty bad) so scroll on down to the "Screen section" and change the DefaultDepth to 24


Users, you may want to experement with the this both enable and commented out, as this howto is aimed at getting everybody's XGL up right away, I've included it as a step.

Okay, now that your machine nows to use the right driver, it's time to get XGL to load with KDM. open your /etc/kde3/kdm/kdmrc file edit the ServerCmd line (line 464 in my fresh Flight 5 instal) to read 

```
ServerCmd=/usr/bin/Xgl -br -ac -accel glx:pbuffer -accel xv:pbuffer
```

For nVidia, or 

```
ServerCmd=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer 

```

for [COLOR="#ff0000"]ATI[/COLOR] fans in the crowd.

Note: For safety's sake, you may want to want to merely comment out the original ServerCmd and place the new command a line below it, just to make it easy to edit in case something goes wrong.

After making that change, proceede to edit /usr/bin/displayconfig-restore (as root) and place a comment in the last line, making

```
#main()
```

the last line.

Now we're in the home stretch, fire up kate (without kdesu or sudo), and paste the following into it

```
[Desktop Entry]
Encoding=UTF-8
Exec=compiz --replace decoration wobbly fade switcher minimize cube rotate zoom scale move resize place & gnome-window-decorator &xmodmap -e "keycode 22 = BackSpace" &
GenericName[en_US]=
StartupNotify=false
Terminal=false
TerminalOptions=
Type=Application
X-KDE-autostart-after=kdesktop"
```

dock or miniwin can also be active, but make sure not to try and use both at the same time, they don't play very well together. This command will initialize all the plugins for compiz. After running  this for the first time, I suggest going back and commenting out everything after the gconf entry with a pound sign. (#)

save this file in your /home/USERNAME*/.kde/Autostart folder as compiz.desktop

* make sure to put your username instead of USERNAME


Now, restart you session (making sure to restart X with a ctrl+alt+backspace) and login as normal, have a great time playing with compiz!

Well, there you go! XGL should load instead of X, and after kde starts up, you should have wobbly windows, and tons other neat effects! Again i suggest heading over to The Compiz Forums to get great advice on configuring compiz with both gconf-editor and the handy gset-compiz tool


TODO:
Do a fresh install of Dapper and try this updated version from the beginning! (Done! And it worked just fine)

---

### Post by watje on 2006-06-02
```
#!/bin/bash
compiz --replace gconf decoration dock wobbly fade minimize cube rotate zoom scale move resize place state switcher trailfocus water bs widget 
& gnome-window-decorator
```

Isn't this for gnome users?

---

### Post by parsival on 2006-06-03
Hi chadwick359,

nice FAQ. 

I followed all the directions except I added
 sudo nvidia-glx-config enable
after the download. X come up OK but I cant drag windows
plus a few other oddities. So close! But not there yet

Fortunately
/etc/init.d/kdm stop
startx
kwin --replace

gets me back to X with kwin.

Any hints?

Bye
PArsival

---

### Post by chadwick359 on 2006-06-05
[QUOTE=parsival]

I followed all the directions except I added
 sudo nvidia-glx-config enable
after the download. X come up OK but I cant drag windows
plus a few other oddities. So close! But not there yet

PArsival[/QUOTE]

When the windows come up, and you cant drag them, do they have title bars at the top? To me it sounds like Compiz is crashing at KDE startup, which happens from time to time, as updates are applied. I would suggest making a copy or  a link to the file the HowTo tells you to put into your autostart folder, and try clicking that if windows are borderless and immoble. I keep a link right on my desktop, because it's almost impossible to do anything without being able to focus keyboard input or move windows.

---

### Post by xinix on 2006-06-07
How do I change the compiz font?  It's rather small for me.  Also, is there any way to set compiz as a session option in kdm?  This way I can use a non compiz session as the same user. They way it is working now, you load kde and then kill kwin and start compiz.  Is it possible to set compiz to start instead of kwin at startup?

---

### Post by chadwick359 on 2006-06-19
The font is changeable in the normal system settings dialouge for Kubuntu.

---

### Post by ErikTheRed on 2006-06-26
Anyone know if kde-window-decorator is working yet? I know it was missing from the CVS up until recently. I'm gonna see if I can get it to work tonight. I'll definitely let you guys know how it goes.

UPDATE: Looks like kde-window-decorator is still broken. Wah.

---

### Post by chadwick359 on 2006-06-27
Yeah, I don't plan on seeing a working Kde decorator until much later in the dev cycle, which is strange, because it seems that KDE has always been the DE for the eyecandy obsessed.

---

### Post by misguided on 2006-06-27
This is seriously odd to me:
I followed the Ubuntu (GNOME) Xgl+compiz tutorial for ATI cards (which lies [here]("http://www.ubuntuforums.org/showthread.php?t=168618")) and used the set of instructions to give Xgl its own GNOME X session.  It works beautifully.  I had some initial problems that were corrected by the latest quinn that came out over the weekend.  It's perfect now, or near it at least.
I decided, however, that GNOME might not be for me, and I wanted to switch to KDE.
I tried using the ServerCmd and compiz launch script from this tutorial, and nothing changed...  running that compiz script from a terminal window returns "compiz.real: No composite extension".
So I tried using the ServerCmd from my GNOME session's startxgl.sh, and the startcompiz script from the same, and it does the same.
If I try putting the option composite enable in the extensions section of xorg.conf, it screws up (as in, no title bars or ability to control my windows whatsoever) not only my KDE session, and not only the Xgl GNOME session, but also the non-xgl GNOME session.  So clearly that's not the answer.
I'm obviously missing something, but I'm having trouble understanding why the same X command and compiz command would work on GNOME and not on KDE.
How can I tell if I'm running Xgl rather than X?  (I don't know how X would get launched instead, but it would be one less problem to try to figure out if I knew for sure)

---

### Post by XiN-eViL on 2006-06-27
Hello,

I followed this guide, and everything worked, but when a kde window wants attention (i.e. flashing in the panel), it keeps flashing (it won't stop). Does anyone know how to fix this :) ?

---

### Post by chadwick359 on 2006-06-28
I would be tempted to blame that on the latest compiz packages, but as my laptop drive with linux on it was recently stolen, I can't help. Until I can get this worked out, I won't be able to update the guide with the other fun new things I have learned recently.

---

### Post by geearf on 2006-07-02
Hello,

I'm trying to give another go at XGL now.

Since the last time I tried, there were great improvements, now I can watch a video with xv and no slowdown at all. But I cannot start compiz anymore

again with the 
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0

I tried to copy /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.2.xlibmesa, but it does not work anymore (it used to be something I had to do to prevent this error from happening).

What should I try ?

Thanks

---

### Post by geearf on 2006-07-03
Ok I got it working, someone might be interested, so maybe something to add : 

For someone using nvidia binaries, we need to install libgl1-mesa, then save /usr/lib/libGL.so.1 somewhere. After that we need to install the nvidia driver.
Then we will install (or reinstall) xserver-xgl.
Then we have to copy the libGL.so.1 we saved earlier to /usr/lib/nvidia/libGL.so.1.2.xlibmesa

Then it works :)

---

### Post by blip on 2006-07-11
> **parsival said:**
> Hi chadwick359,

nice FAQ. 

I followed all the directions except I added
 sudo nvidia-glx-config enable
after the download. X come up OK but I cant drag windows
plus a few other oddities. So close! But not there yet


I've got the exact same problem, parsival... Did you ever get it solved?  Basically everything comes up just fine except my windows have no titles and they cannot be dragged around the screen.

---

### Post by chadwick359 on 2006-07-11
That actually sounds like the WM isn't loading, blip, what happens if you type gnome-window-manager into a terminal?

---

### Post by chadwick359 on 2006-07-19
Okay, the guide has been updated with some performance tweaks from the guys over at the compiz forums, enjoy!

---

### Post by purpstin on 2006-07-27
Hi!

I just installed Kubuntu and I would like to give compiz a try. This is my first Linux experience so you see I'm a fully qualified newbie.

I tried to follow your guide but failed at "Code:" #4. I've already managed to install the nvidia drivers (nvidia-kernel-common and nvidia-glx) so I tried to install the rest througt Adept manager.

When I request install for Compiz Adept says BREAK (install) and wont let me install it. And I can't find gset-compiz.

I tried to run "sudo apt-get install compiz xserver-xgl libglitz-glx1 compiz-gnome gconf-editor gset-compiz" from the console (to install the packages that aren't already installed) but I get an error:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gset-compiz

What should I do to fix this problem?

*** Edit ***
I tried "sudo apt-get install compiz" in the console and recieved this error:

The following packages have unmet dependencies:
  compiz: Depends: libsvg-cairo (>= 0.1.6) but it is not going to be installed
E: Broken packages

Adept manager will only let me install 0.1.5-0

---

### Post by chadwick359 on 2006-07-28
What happens if you try the longer apt-get without gset-compiz?

---

### Post by purpstin on 2006-07-28
> **chadwick359 said:**
> What happens if you try the longer apt-get without gset-compiz?

```

sudo apt-get install compiz xserver-xgl libglitz-glx1 compiz-gnome gconf-editor
Password:
Reading package lists... Done
Building dependency tree... Done
gconf-editor is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: libsvg-cairo (>= 0.1.6) but 0.1.5-0 is to be installed
E: Broken packages

```

No luck there.

I'm running Kubuntu 6.06 amd64. That wouldn't be the cause of this, right?

---

### Post by tymek666 on 2006-07-29
> **purpstin said:**
> ```

The following packages have unmet dependencies:
  compiz: Depends: libsvg-cairo (>= 0.1.6) but 0.1.5-0 is to be installed
E: Broken packages

```

No luck there.

I'm running Kubuntu 6.06 amd64. That wouldn't be the cause of this, right?

here's package you need:
[http://home.comcast.net/~psyberone/compiz/libsvg-cairo_0.1.6-1_amd64.deb]("http://home.comcast.net/~psyberone/compiz/libsvg-cairo_0.1.6-1_amd64.deb")

Good luck! :)

---

### Post by purpstin on 2006-07-30
tymek666 thanks for the package.

I followed the guide through and everything seemed to install fine. But when I had restarted everything and logged in there were no borders on the windows. So I couldn't move or resize them. I had also lost my swedish keyboard map (I think the new one was american, but I'm not really sure about that). Repainting windows was terribly slow (several seconds) and cpu usage was really high every time a new window got focus. There was something else that looked strange. I couldn't really tell what it was. It might just have been the fonts.

I undid all changes but I haven't given up on Xgl and compiz. Any ideas what I should do to make it work?

---

### Post by darknight74 on 2006-07-31
Hi!
I tried to use compiz with my kubuntu dapper distro following the instructions reported in this topic.

All goes ok, except when i try to execute compiz,'cause it complains about 
GLX_EXT_texture_from_pixmap is missing

I use 87.62 NVidia drivers and i tried also to use libGL.so.1.2 as shipped with libgl1-mesa (linking to it libGL.so.1 instead of using liGL shipped with NVidia drivers), but it doesn't work.

Any clue?

Thanx in advance

---

### Post by d351GuJu on 2006-07-31
> tymek666 thanks for the package.

I followed the guide through and everything seemed to install fine. But when I had restarted everything and logged in there were no borders on the windows. So I couldn't move or resize them. I had also lost my swedish keyboard map (I think the new one was american, but I'm not really sure about that). Repainting windows was terribly slow (several seconds) and cpu usage was really high every time a new window got focus. There was something else that looked strange. I couldn't really tell what it was. It might just have been the fonts.

I undid all changes but I haven't given up on Xgl and compiz. Any ideas what I should do to make it work?


You might want to read [this]("http://www.ubuntuforums.org/showthread.php?t=224892") thread.

---

### Post by xtalman on 2006-07-31
The guide works great!  Except for one annoying problem I'm having.

I can't use the cube or multiple desktops.  From reading the forums, it looks like I should be able to hit Ctrl-Alt-Left or -Right and switch workspaces.  Or use Ctrl-Alt-Left Mouse-Drag.  But none of these work.

I'm using KDE.  Any ideas?

---

### Post by Flame0001 on 2006-08-01
I've followed your instructions to the dot, and figured that getting XGL getting setup in KDE would be as simple as it was in Gnome, so I didn't need to install the video card drivers (I have an Nvidia by the way) or any packages (Other than compiz-kde). I followed the rest of the instructions perfectly, but I got no luck. Not even any errors that XGL would normally give on a bad install (Like the borderless/dragless windows, choppy animations). Just regular KDE.

Here's my xorg.conf if that helps:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon May 15 13:23:42 PDT 2006

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
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
#   Load           "GLcore"
#   Load           "dri"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "false"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Option         "RenderAccel"           "true"
    Option         "AllowGLXWithComposite" "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


```

---

### Post by chadwick359 on 2006-08-09
Sounds to me like your problem is actually just kwin running instead of compiz/gnome-window-decorator. Try launching 'gnome-window-decorator --replace' (no quotes) in a terminal.

---

### Post by Buelldozer on 2006-08-09
Pardon me,

I don't think you should be using gnome-window-decorator. According to Quinn it has been superceded by cdgw.

I just re-installed according to these direction this morning but instead of using g-w-d I used cdgw and it works fine.

---

### Post by haffe on 2006-08-23
I followed this howto and encounterd a couple of problems. The firs one is that I seem to have lost the ability to use the Alt Grkey, i.e. Alt Gr + 2 no longer produces a @. 
The second problem is that Konversation no longer changes the colour of tabs to notify when somebody has typed in the channel.(This problem is solved, turned out it wasn't Xgl that was the problem, it was the Tuxintosh theme).

---

### Post by BerlinOliver on 2006-08-24
HI there,

I tried to install ompiz and xgl too. But I got some prolems:

When I try > sudo apt-get install nvidia-kernel-common nvidia-glx compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome gconf-editor gset-compiz

I got the following message:
```
olli@Venusfalle:~$ sudo apt-get install nvidia-kernel-common nvidia-glx compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome gconf-editor gset-compiz
Reading package lists... Done
Building dependency tree... Done
nvidia-kernel-common is already the newest version.
nvidia-glx is already the newest version.
compiz is already the newest version.
xserver-xgl is already the newest version.
libgl1-mesa is already the newest version.
xserver-xorg is already the newest version.
libglitz-glx1 is already the newest version.
compiz-gnome is already the newest version.
gconf-editor is already the newest version.
E: Couldn't find package gset-compiz
```

I tried to install further without this package, but the Server wont start.

Any help is very appreciated.

---

### Post by thiag777 on 2006-08-31
Hi everyone,
Sounds like I'm the only one having big trouble with X server here..

I thought about giving Xgl a try but all I got was a non-working-x-server system. Sorry but I'm a newbie in this area.

I tried to undo everything but still my X wont go up. I get these error messages:

> 
(EE) No devices detected
Fatal server error:
no screens found

Xauth: error in locking authority file /home/hunter/.Xauthority


any ideas?!:confused: 
I really need my kubuntu Xorg working (Xgl would be fine also) `cause I need to expose a project in it.

thanks in advance,
Thiago.

---

### Post by cdr377 on 2006-09-01
Hi, I've got both Kubuntu and Ubuntu desktops installed. I followed your guide for installing compiz for Kubuntu and then whent to the wiki ubuntu guide and followed their instructions for Ubuntul. When I logged back into Kubuntu I've lost my task bar or panel. I can't figure out how to get it back. I've been using right click to get every where it seems to work perfectly on kubuntu but the task bar is gone. What's up with that? Could it be the compiz.desktop file I created in /.kde directory? Thanks for your help!

---

### Post by cdr377 on 2006-09-01
Um, never mind I guess it works now. Must of just needed a hard restart. Everything's working now but I did get a new problem. In Kubuntu, I can't enable more then 1 desktop. I go to System Settings -> Desktop -> Multiple Desktops and I try to enable 4 but it keeps defaulting back to 1 so I can never get that cool cube thingy to work. It works in Ubuntu. I'm not quite sure what's going on here. Thanks again, look forward to your response!

---

### Post by thiag777 on 2006-09-01
I already got my problem solved ... I guess I missed a package.
the only thing now is .. that the multiple desktops aren't working.. is that normal??
thanks.

---

### Post by fildo on 2006-09-11
fildo@liberty:~$ compiz-start
nohup: appending output to `nohup.out'


i get this error can anyone help !

---

### Post by Jongi on 2006-11-10
I am wanting to install compiz for Edgy (using AIGLX). What would I need to change in the original post.

---

