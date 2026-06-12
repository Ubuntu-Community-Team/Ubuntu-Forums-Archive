---
title: "HOW TO: Have a neat Gimp interface"
date: 2007-05-20
forum: Outdated Tutorials &amp; Tips
---

### Post by BLTicklemonster on 2007-05-20
Lots of people complain that Gimp has too many little windows in the way.

Here's a nice way to clean that up and have just the main panel and the canvas:

[IMG]http://img511.imageshack.us/img511/4279/cleangimpguihf1.png[/IMG]

Enjoy.

---

### Post by kbf on 2007-05-20
Hi

Thanks for your tip.
I jus tried it with Gimp 2.2.13 but it did not work, anything to look out for??

---

### Post by Steveway on 2007-05-20
I think you need the new development release 2.3.
It works here with gimp 2.3.16.

---

### Post by an93l on 2007-05-20
thanks for the tip BLTicklemonster. i tried this with the gimp version 2.2.13 and it worked a charm. if you put the mouse pointer between the colour chooser and the tool properties it should say "you can drop dockable dialogs here" this is where you need to drag the title bar to. so i would try again kbf

---

### Post by kbf on 2007-05-20
I get the message popping up but when i drag it over it just sits on top without docking itself.

---

### Post by BLTicklemonster on 2007-05-20
Make sure you're dragging it to the right place. Look at the picture carefully. If you drag it to the wrong one, it won't do anything.

Hopefully that's all it is. I've been doing this with every release I've had since like about 2 years ago I believe.

---

### Post by kbf on 2007-05-20
You were right, i had a few dialogs already bundled and tried to grab them on top, but you have to grab each seperate. IT WORKS. Thanks

---

### Post by BLTicklemonster on 2007-05-20
Wheeee!!! :D

---

### Post by eddyverl on 2007-05-23
In addition to this I want to give some advice on wich dialogs are important and how you  can  divide them over the dockings.

The most important dialogs, the ones that always should be fully visible are:
- the toolbox
- the toolbox options
- the layers dialog

The following dialogs also are used a lot and they must be easily accessible but not ongoing visible
- the channels dialog
- the paths dialog
- the undo history dialog

The dialogs of the brushes, gradients and patterns are not necessary because you can easily pop them up by clicking in the indicator area (in the toolbox)

Based on a my experience it is best to put the channels dialog in another dock than the layers. (so you can  determine easily if there is a channel active or a layer.

Depending on the resolution of your screen I give two examples of how you can achieve this.

1280*1024 screen : Toolbox on top, then toolbox options and channels, then the others.

[IMG]http://users.telenet.be/ev1/gimpinterface1280x.jpg[/IMG]

1024 * 768 screen : Toolbox in the middle (as flat as possible), the others as in the previous example.

[IMG]http://users.telenet.be/ev1/gimpinterface1024x.jpg[/IMG]

---

### Post by Hairy_Palms on 2007-05-23
i personally install xnest and run gimp with this command
> Xnest :1 -ac -wr -name GIMP -geometry 1400x800 & metacity --display :1 & gimp-2.3 ~/Templates/PNG\ Image.png --display :1 & gnome-settings-daemon --display :1

looks like this 

> [http://four.fsphost.com/hairypalms/gim.png](http://four.fsphost.com/hairypalms/gim.png)

---

### Post by BLTicklemonster on 2007-05-23
Excellent!!! Keep them coming, this is great stuff, all in one place!

---

### Post by sirlancelot on 2007-05-24
> **Hairy_Palms said:**
> i personally install xnest and run gimp with this command

looks like this
Is it possible to achieve such a layout within KDE? I don't want to have to install metacity. I did however get GIMP running inside Xnest, but there's no window decoration...

---

### Post by BLTicklemonster on 2007-05-24
> **Hairy_Palms said:**
> i personally install xnest and run gimp with this command


looks like this

EEEK:

```
bill@bill-desktop:~$ Xnest :1 -ac -wr -name GIMP -geometry 1400x800 & metacity --display :1 & gimp-2.3 ~/Templates/PNG\ Image.png --display :1 & gnome-settings-daemon --display :1
[1] 15154
[2] 15155
[3] 15156
_XSERVTransSocketOpenCOTSServer: Unable to open socket for inet6
_XSERVTransOpen: transport open failed for inet6/bill-desktop:1
_XSERVTransMakeAllCOTSServerListeners: failed to open listener for inet6
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
bash: gimp-2.3: command not found
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
Window manager warning: Log level 32: could not find XKB extension.

** (gnome-settings-daemon:15157): WARNING **: numlock: XkbQueryExtension returned an error
xnest warning: unhandled event
xnest warning: unhandled event

** (gnome-settings-daemon:15157): WARNING **: Neither XKeyboard not Xfree86's keyboard extensions are available,
no way to support keyboard autorepeat rate settings
xrdb:  "*Label.background" on line 243 overrides entry on line 170
xrdb:  "*Text.background" on line 249 overrides entry on line 211
xrdb:  "*Label.foreground" on line 255 overrides entry on line 171
xrdb:  "*Text.foreground" on line 261 overrides entry on line 212
xrdb:  "*Label.background" on line 243 overrides entry on line 170
xrdb:  "*Text.background" on line 249 overrides entry on line 211
xrdb:  "*Label.foreground" on line 255 overrides entry on line 171
xrdb:  "*Text.foreground" on line 261 overrides entry on line 212
xrdb:  "*Label.background" on line 243 overrides entry on line 170
xrdb:  "*Text.background" on line 249 overrides entry on line 211
xrdb:  "*Label.foreground" on line 255 overrides entry on line 171
xrdb:  "*Text.foreground" on line 261 overrides entry on line 212
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
xnest warning: unhandled event
[1180004790,000,xklavier_xmm.c:xkl_xmm_actualize_group/]        Could not execute xmodmap: -1

** (gnome-settings-daemon:15157): WARNING **: Neither XKeyboard not Xfree86's keyboard extensions are available,
no way to support keyboard autorepeat rate settings

** (gnome-settings-daemon:15157): WARNING **: Neither XKeyboard not Xfree86's keyboard extensions are available,
no way to support keyboard autorepeat rate settings

** (gnome-settings-daemon:15157): WARNING **: Neither XKeyboard not Xfree86's keyboard extensions are available,
no way to support keyboard autorepeat rate settings
X connection to :0.0 broken (explicit kill or server shutdown).
The application 'gnome-settings-daemon' lost its connection to the display :1.0;
most likely the X server was shut down or you killed/destroyed
the application.
[3]+  Exit 127                gimp-2.3 ~/Templates/PNG\ Image.png --display :1
bill@bill-desktop:~$ Window manager warning: Lost connection to the display ':1';
most likely the X server was shut down or you killed/destroyed
the window manager.

[1]-  Exit 1                  Xnest :1 -ac -wr -name GIMP -geometry 1400x800
[2]+  Exit 1                  metacity --display :1
bill@bill-desktop:~$ 


```

I'm doing something wrong lol. (nautilus in icewm probably)

---

### Post by mintcoffee on 2007-05-24
Thanks for the tip! Even though this is not related to GIMP, i can use Xnest to start my acroread with the correct DPI settings in BigDesktop mode AND present on the correct xinerama desktop! woohoo!

---

### Post by Hairy_Palms on 2007-05-27
BLTickle, you probably dont have the image i was opening available, also if your resolution isnt big enough to fit 1440x800 inside it i think it gives an error too, so change these values accordingly :)

---

### Post by BLTicklemonster on 2007-06-05
So how would I open it in xnest "generically"?

---

### Post by Hairy_Palms on 2008-04-19
wow, i cant beleive i didnt respond to this, its been over a year now.... well, if anyones still interested the command is 
> Xnest :1 -ac -wr -name GIMP -geometry 1400x800 & **metacity** --display :1 & gimp-2.3 **/path/to/imageyouwanttoopen** --display :1 & gnome-settings-daemon --display :1

if your on kde replace it with kwm and xfce then use xfwm4

put the path to your image, or you can alternatively leave it blank and just open it with the gimps menu afterwards.

P.S. just confirmed it still works in gutsy, in hardy it works but this bug
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/188010](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/188010)
means it looks kinda crappy.

---

### Post by BLTicklemonster on 2008-09-23
Gimp 2.5 is out, unstable at present, but I just had to post this because so many people complain about the differences between Photoshop and Gimp.

Here's the stock startup for both Photoshop CS and Gimp compared. Notice how many dialog windows each has. 

The new GIMP will dock dialogs for you automatically, making this thread obsolete.

:)

---

