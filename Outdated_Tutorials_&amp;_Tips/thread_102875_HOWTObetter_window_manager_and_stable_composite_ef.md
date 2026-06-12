---
title: "HOWTO:better window manager and stable composite effects."
date: 2005-12-13
forum: Outdated Tutorials &amp; Tips
---

### Post by codejunkie on 2005-12-13
Following the steps here will give you stable composite effects, like drop shadows and transparency effects and gives the desktop a new feel, like being able to move items to another workspace simply by dragging them to the side of the screen. and window opacity changing when moving and resizing windows.[B]
Parts of this were taken from different howto's that i've used and all credit goes there writers for there hard work.[/B]
Enabling the composite manager
[http://ubuntuforums.org/showthread.php?t=75527&highlight=transset]("http://ubuntuforums.org/showthread.php?t=75527&highlight=transset")
posted by **poofyhairguy**
&
Replace metacity with xfwm4
[http://ubuntuforums.org/showthread.php?t=88393&highlight=xfwm4]("http://ubuntuforums.org/showthread.php?t=88393&highlight=xfwm4")
posted by **theine**

step1:
change the default WM to xfwm4
first install the required packages.
```

sudo apt-get install xfwm4 xfce4-mcs-manager openbox

```
next add an entry for xfwm4 to the usr/bin/gnome-wm file.
```

sudo sed -i "s/openbox)/openbox|xfwm4)/" /usr/bin/gnome-wm

``` 
set the default window manager to xfwm4.
```

echo export WINDOW_MANAGER=/usr/bin/xfwm4 >> ~/.gnomerc

```
create an icon in System/Preferences menu to change the window manager themes and settings.
```
sudo gedit /usr/share/applications/xfwm4-themes.desktop
``` copy and paste this into the file
```

[Desktop Entry]
Encoding=UTF-8
Name=xfwm4 themes
Type=Application
Exec=xfce-setting-show xfwm4
Terminal=false
Icon=xfwm4
Categories=GNOME;Application;Settings;
OnlyShowIn=GNOME;

```save the file and exit.

step2:
now enable the composite extension in the /etc/X11/xorg.conf file like this
```

sudo gedit /etc/X11/xorg.conf

``` and add these lines to the end of the file
```

Section "Extensions"
        Option  "Composite" "Enable"
EndSection

``` 
For Nvidia cards:

look through the file. Find the section called &#8220;device.&#8221; Add these two lines to that section:
```

Option "RenderAccel" "true" 
Option "AllowGLXWithComposite" "true"

``` 
It should look something like this:

```

Section "Device"
    Identifier    "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
    Driver        "nvidia"
    BusID         "PCI:1:0:0"
    Option        "RenderAccel"           "true"
    Option        "AllowGLXWithComposite" "true"
EndSection

``` save and exit and restart the xserver by logging out and pressing ctrl+alt+backspace
Note:
for ATI & other video cards, i don't know what options to use for them so assuming if you can get xcompmgr to work by following poofy's excellent guide then this should work just fine but i can't say for sure. 

next xcompmgr and xfwm4 both suffer from the same bug in gnome, when you click on the logout button, it seems to freeze but what happens is the logout_prompt just isn't visible. 
a work around that is go into Applications/SystemsTools/Configuration editor. 
now navigate to apps/gnome-session/options rightclick on logout_option, click on edit key and set it to "logout" if it's already set to logout just skip this step, 
now uncheck the logout_prompt box and close the configuration editor. 
now when you click on the logout button it takes you to gdm instead of seeming to freeze up the system.

and finaly the lastthing were going to make some changes to our default xfwm4 WM theme by going into the /usr/share/themes dir
find the current theme were using and add these lines to the bottom of the "themerc" file.
```

resize_opacity=100
move_opacity=60
popup_opacity=90
show_frame_shadow=true
show_popup_shadow=true

``` 
save the file and exit, you must logout and back in for the changes to take affect.
 this will add transparency effects to your WM theme so when you move, drag, resize your windows, the opacity will change to the value you set in the "themerc" file.
for those of you that don't want to edit your "themerc" file i've attached a theme that has already been modified.
guys trust me the screenshots don't do it justice but i tried..

---

### Post by poofyhairguy on 2005-12-31
Neat Guide

---

### Post by juantxorena on 2005-12-31
I'm very confused about the diffs between desktop environment, windows manager, etc. I think I understand everything, but then I discover a new WM, or desktop environment, or "desktop shell" like Enlightenment 17, and I get my brains messed again.

With this guide, you can replace metacity with xfwm4, add transparency effects, blah blah. BUT, the gnome menu bars will be there? Could I use GDesklets? With kind of themes can I use (GTK, XFCe, Gnome, etc)? Gnome themes will affect windows? xfwm themes will affect menus and the like?

BTW, great guide.

---

### Post by codejunkie on 2006-01-03
[QUOTE=poofyhairguy]Neat Guide[/QUOTE]
Thanks poof,

---

### Post by codejunkie on 2006-01-03
[QUOTE=juantxorena]I'm very confused about the diffs between desktop environment, windows manager, etc. I think I understand everything, but then I discover a new WM, or desktop environment, or "desktop shell" like Enlightenment 17, and I get my brains messed again.

With this guide, you can replace metacity with xfwm4, add transparency effects, blah blah. BUT, the gnome menu bars will be there? Could I use GDesklets? With kind of themes can I use (GTK, XFCe, Gnome, etc)? Gnome themes will affect windows? xfwm themes will affect menus and the like?

BTW, great guide.[/QUOTE]
yes when you replace metacity with xfwm4 the gnome panel will still be there, you can use gdesklets, and xfce and gnome both use GTK themes, so the GTK themes change the controls, application color etc, and the xfwm and metacity themes change the window border theme only.

---

### Post by juantxorena on 2006-01-03
I installed it. It's great: faster (even when moving windows), integrates perfectly with my theme, more eyecany...

Just two things:
1.- I don't like very much logging aout to restart or shut down
2.- My aMSN tray icon dissapeared, instead there is a white tux (both in GTK icon and Free Desktop icon options).

Anyway, It's cool.

---

### Post by AndyAWS on 2006-01-03
Worked great for me, however I can't get it to save my resolution setting (1024x768) it always goes back to 1280x1024 when restarted. I tried saving the session...any other ideas?

---

### Post by Paulus on 2006-01-03
```
sudo gedit /etc/X11/xorg.conf
```

scroll down to **Section "screen"**, see where it says **DefaultDepth, **then scroll down till you see the subsection with your depth and simply delete "1280x1024"

---

### Post by AndyAWS on 2006-01-03
Thanks for the advice but if I do that I'll hose the other users (my kids) that do use 1280x1024. Is there a way to change the default just for my username?

---

### Post by codejunkie on 2006-01-03
[QUOTE=AndyAWS]Worked great for me, however I can't get it to save my resolution setting (1024x768) it always goes back to 1280x1024 when restarted. I tried saving the session...any other ideas?[/QUOTE]
install the xfce desktop with 
```
sudo apt-get install xfce4
```
logout of gnome, and under session choose xfce login, now logout and back into gnome. i know this step sounds kinda stupid but the display manager applet won't show up until you do it. now from the terminal run xfce-setting-show under the Display tab set the resolution you want and now it should stay between reboots hope this helps.

---

### Post by benplaut on 2006-01-03
why install openbox?

---

### Post by codejunkie on 2006-01-03
[QUOTE=benplaut]why install openbox?[/QUOTE]
i install it to use the "gnome-panel-control --run-dialog" keyboard shortcut because i like it better than xfrun4 other than that it's not needed.

---

### Post by juantxorena on 2006-01-04
You don't need to install Openbox in order to use that:
System -> Preferences -> xfwm 4 themes -> Keyboard tab
Add a new shortcut group (Add button). Then go to $HOME/.theme/name_of_the_shortcut_group/xfwm4/
Edit keythemerc file.
At the end of that file, there are some lines like:
> shortcut_1_key=none
shortcut_1_exec=none
shortcut_2_key=Alt+F2
shortcut_2_exec=gnome-panel-control --run-dialog
shortcut_3_key=Alt+Control+Delete
shortcut_3_exec=gnome-system-monitor
shortcut_4_key=Control+Alt+k
shortcut_4_exec=xkill It's quite obvious: shortcut_#_key has the key combination which executes the command in shortcut_#_exec with the same number. This way you can modify some default shortcuts, which cannot be modified in the xfwm 4 theme ap.

---

### Post by Mr_J_ on 2006-01-04
I have no idea where i made the mistake, but i can't get the windows to be semi transparent. Or less opaque as some might put it.

Here is where i think i might have gone wrong.
The very last step where i have to edit the themerc file in "/usr/share/themes/xfce/xfwm4/themerc" I got severely confused here and it took me a great big while to make this find.

A few things i have diferent that i have no idea if they influence this are:
I use InitNG, and just changed to use gdm instead of kdm just before the very last step about the themerc thing.

Tried to use the xfce4 themes thingy and change to the xfce svn default theme you added to this thread. It still doesn't work.

I tried using openbox, xfce, and Gnome so far none of them seem to make this opacity problem work. So i figure it's something i haven't done and can't seem to figure out.

I'm using two monitors so that might have something to do with it... Although I hope not.

---

### Post by MrRoboto on 2006-01-04
same problem here!
but everything seems ok.. i'm using the theme provided by codejunkie.. and of course composite is enabled into Xorg.

---

### Post by codejunkie on 2006-01-05
[QUOTE=Mr_J_]I have no idea where i made the mistake, but i can't get the windows to be semi transparent. Or less opaque as some might put it.

Here is where i think i might have gone wrong.
The very last step where i have to edit the themerc file in "/usr/share/themes/xfce/xfwm4/themerc" I got severely confused here and it took me a great big while to make this find.

A few things i have diferent that i have no idea if they influence this are:
I use InitNG, and just changed to use gdm instead of kdm just before the very last step about the themerc thing.

Tried to use the xfce4 themes thingy and change to the xfce svn default theme you added to this thread. It still doesn't work.

I tried using openbox, xfce, and Gnome so far none of them seem to make this opacity problem work. So i figure it's something i haven't done and can't seem to figure out.

I'm using two monitors so that might have something to do with it... Although I hope not.[/QUOTE]can you post your xorg.conf file and the themerc file of the current xfwm theme your using.

---

### Post by AndyAWS on 2006-01-05
[QUOTE=codejunkie]install the xfce desktop with 
```
sudo apt-get install xfce4
```
logout of gnome, and under session choose xfce login, now logout and back into gnome. i know this step sounds kinda stupid but the display manager applet won't show up until you do it. now from the terminal run xfce-setting-show under the Display tab set the resolution you want and now it should stay between reboots hope this helps.[/QUOTE]

When I logged into XFCE I set the res to 1024x768. Now gnome loads with that resolution. Thanks, the only problem I'm having now is that 50% of the time running Enigma kicks me out to GDM. That's probably just a problem between Enigma and the compositing.

---

### Post by Mr_J_ on 2006-01-06
[xorg.conf]("http://pastebin.com/493282")

This last one about the themerc file is a little harder.
I have two Theme in System>Preferences...

One refers to Xfce4 and the other to gnome.
In the Gnome one I chose...
Controls>Xfce, Window Border>Clearlooks, Icons>graphite.
The one referencing Xfce4 I chose Xfce.

[/usr/share/themes/Xfce/xfwm4/themerc]("http://pastebin.com/493292")

---

### Post by codejunkie on 2006-01-06
[QUOTE=Mr_J_][xorg.conf]("http://pastebin.com/493282")

This last one about the themerc file is a little harder.
I have two Theme in System>Preferences...

One refers to Xfce4 and the other to gnome.
In the Gnome one I chose...
Controls>Xfce, Window Border>Clearlooks, Icons>graphite.
The one referencing Xfce4 I chose Xfce.

[/usr/share/themes/Xfce/xfwm4/themerc]("http://pastebin.com/493292")[/QUOTE]
the links didn't work attach them to a new post here.

---

### Post by Mr_J_ on 2006-01-07
[http://pastebin.com/494748](http://pastebin.com/494748)

[http://pastebin.com/494749](http://pastebin.com/494749)

---

### Post by codejunkie on 2006-01-07
[QUOTE=Mr_J_][http://pastebin.com/494748](http://pastebin.com/494748)

[http://pastebin.com/494749](http://pastebin.com/494749)[/QUOTE]
your xorg.config file and themerc file both look ok. the themerc file is set to only change the window opacity when your moving a window, if you can see window shadows and click and hold on a window and move it around the screen and the opacity changes it's working. but to make windows stay transparent all the time you would have to install and use transset or you could add other options to the themerc file for different opacity effects. if you still can't see any composite effects it could be where your using a dual head setup i've never tried this using two monitors so i have no idea on that one.

---

### Post by Neo40 on 2006-01-07
Hi,

When I use a modified xfwm themerc, my system freezes. No k/b, nothing except mouse moving but not responding when I click somewhere. I think my old GeForce 2 video card does not work...???

---

### Post by codejunkie on 2006-01-07
[QUOTE=Neo40]Hi,

When I use a modified xfwm themerc, my system freezes. No k/b, nothing except mouse moving but not responding when I click somewhere. I think my old GeForce 2 video card does not work...???[/QUOTE]
i've had that problem it's a bug with saving your gnome-session and xfwm4 if you can't get to your desktop try the failsafe gnome session when you get to the desktop open a terminal and enter
```
rm ~/.gnome2/session
``` this will clear the saved gnome-session log out and log back in that should fix it, if by chance you can't get to the desktop by choosing a failsafe session try
pressing ctrl+alt+F1 to switch to a terminal, login with your normal username and run
```
rm ~/.gnome2/session
```
and restart gdm with
```
sudo /etc/init.d/gdm restart
```
hope this helps.

---

### Post by MrRoboto on 2006-01-07
[QUOTE=codejunkie]your xorg.config file and themerc file both look ok. the themerc file is set to only change the window opacity when your moving a window, if you can see window shadows and click and hold on a window and move it around the screen and the opacity changes it's working. but to make windows stay transparent all the time you would have to install and use transset or you could add other options to the themerc file for different opacity effects. if you still can't see any composite effects it could be where your using a dual head setup i've never tried this using two monitors so i have no idea on that one.[/QUOTE]

i'm also using dualhead and i don't have any shadows so i guess that's the problem.

---

### Post by Neo40 on 2006-01-07
[QUOTE=codejunkie]i've had that problem it's a bug with saving your gnome-session and xfwm4 if you can't get to your desktop try the failsafe gnome session when you get to the desktop open a terminal and enter
```
rm ~/.gnome2/session
``` this will clear the saved gnome-session log out and log back in that should fix it, if by chance you can't get to the desktop by choosing a failsafe session try
pressing ctrl+alt+F1 to switch to a terminal, login with your normal username and run
```
rm ~/.gnome2/session
```
and restart gdm with
```
sudo /etc/init.d/gdm restart
```
hope this helps.[/QUOTE]

I tried that but didnt help. Anyone has succes with a Geforce 2 card?

---

### Post by potrick on 2006-01-07
seriously, this guide rocks. Thank you so much. I'll probably get sick of my new drop shadows very fast, but they are cool.

---

### Post by Mr_J_ on 2006-01-07
Thanks for everything but i guessed it could happen.
It was a part of a series of warnings on the Howto.

So I'll try this again once I get rid of a monitor or something along those lines.

I know it's going to sound "corny", but I missed this kind of control over my desktop. Takes a bit of time before you see what you don't have with using windows. I guess it's a trade...

---

### Post by codejunkie on 2006-01-08
[QUOTE=Mr_J_]Thanks for everything but i guessed it could happen.
It was a part of a series of warnings on the Howto.

So I'll try this again once I get rid of a monitor or something along those lines.

I know it's going to sound "corny", but I missed this kind of control over my desktop. Takes a bit of time before you see what you don't have with using windows. I guess it's a trade...[/QUOTE]
sorry i couldn't me of more help since i don't use a dual monitor setup but have you tried poofy's guide here [http://ubuntuforums.org/showthread.php?t=75527&highlight=transset](http://ubuntuforums.org/showthread.php?t=75527&highlight=transset)
it uses xcompmgr and transset and metacity. those should work pretty good for you with the video card you have. i just use this setup because i have an older graphics card and it seems to work better on it.

---

### Post by codejunkie on 2006-01-08
[QUOTE=Neo40]I tried that but didnt help. Anyone has succes with a Geforce 2 card?[/QUOTE]
i don't know about the GeForce2 cards but the composite extension should still work  as long as you have it enabled in your /etc/X11/xorg.conf file could you post your xorg.conf file here so i could take a look at it.

---

### Post by Iandefor on 2006-01-08
Codejunkie: Most excellent! I had been playing around with xcompmgr and gave up today when it froze Ubuntu, which was a first. Literally, I have *never* had a Linux distro freeze on me, *ever*. It seems XFWM4 has all the features of xcompmgr that I like (ie, drop shadows and transparency) but it feels more stable and looks like it's less resource-intensive. Just one question: what are some other compositing options we can put into the themerc file? It's mightily cool to have a transparent window when you're moving it, but how about giving a window transparency if it doesn't have focus? What about any other cool things you might have found?

---

### Post by Stelmate on 2006-01-08
Okay, 
Well this is working for the most part on my dual-monitor setup (default nvidia driver with breezy and a Geforce 6600GT) now this is weird and I'm hoping someone can help me with this. When ubuntu first starts in the middle of my two screens is a wierd unrendered blob, when I move the cursor over it and highlight the section, it disappears and stays good for the rest of my login session.  Also xfwm4 seems to be messing with my gnome-panel upon login!  It moves it around or it taken a good while to start up?  Other than those minor details it works great.

-Stelmate

---

### Post by codejunkie on 2006-01-08
[QUOTE=Iandefor]Codejunkie: Most excellent! I had been playing around with xcompmgr and gave up today when it froze Ubuntu, which was a first. Literally, I have *never* had a Linux distro freeze on me, *ever*. It seems XFWM4 has all the features of xcompmgr that I like (ie, drop shadows and transparency) but it feels more stable and looks like it's less resource-intensive. Just one question: what are some other compositing options we can put into the themerc file? It's mightily cool to have a transparent window when you're moving it, but how about giving a window transparency if it doesn't have focus? What about any other cool things you might have found?[/QUOTE]
i don't know exactly anymore commands to add to the themerc file for different effects, but i've played with a bunch xfwm4 themes that i found on xfce-look.org and other places and they do different things. when you minimize, maximize, and resize windows etc windows opacity change to different value. and to make windows transparent if there not in focus you still have to use transset you just don't have to run xcompmgr to use it because xfwm4 has a composite manager built in.

---

### Post by Iandefor on 2006-01-08
[quote=codejunkie]i don't know exactly anymore commands to add to the themerc file for different effects, but i've played with a bunch xfwm4 themes that i found on xfce-look.org and other places and they do different things. when you minimize, maximize, and resize windows etc windows opacity change to different value. and to make windows transparent if there not in focus you still have to use transset you just don't have to run xcompmgr to use it because xfwm4 has a composite manager built in.[/quote] Hrm... after getting it set up, I found that it automatically set the opacities for the windows out of focus. Weird. Well, can you point me to a few themes that take advantage of compositing so I can look at them? I don't particularly feel like sifting through xfce-look.org just to find one, if you've already found one.

---

### Post by codejunkie on 2006-01-08
[QUOTE=Iandefor]Hrm... after getting it set up, I found that it automatically set the opacities for the windows out of focus. Weird. Well, can you point me to a few themes that take advantage of compositing so I can look at them? I don't particularly feel like sifting through xfce-look.org just to find one, if you've already found one.[/QUOTE]
i know the VistaBut theme has it when i find some more i'll post them.
[http://xfce-look.org/content/show.php?content=32227](http://xfce-look.org/content/show.php?content=32227)

---

### Post by poofyhairguy on 2006-01-08
[QUOTE=Stelmate]Okay, 
Well this is working for the most part on my dual-monitor setup (default nvidia driver with breezy and a Geforce 6600GT) now this is weird and I'm hoping someone can help me with this. When ubuntu first starts in the middle of my two screens is a wierd unrendered blob, when I move the cursor over it and highlight the section, it disappears and stays good for the rest of my login session.  Also xfwm4 seems to be messing with my gnome-panel upon login!  It moves it around or it taken a good while to start up?  Other than those minor details it works great.

-Stelmate[/QUOTE]

I will say that I have the exact same set-up (6600 GT and dual head) and I use Metacity (despite its boringness) just for the better Xinerama support (than all but Kwin and Enlightenment).

---

### Post by Iandefor on 2006-01-08
[quote=codejunkie]i know the VistaBut theme has it when i find some more i'll post them.
[http://xfce-look.org/content/show.php?content=32227]("http://xfce-look.org/content/show.php?content=32227")[/quote] Excellent. Thank you!

---

### Post by Norm 2782 on 2006-01-09
Hi and thanks for the guide. Unfortunately I just can't get the transparency to work. I've got the latest nVidia drivers on a -686 kernel for my mobile GeForce 4 MX. Down below my xorg.conf and themerc.

I already tried to re-enable DRI and GLCore, but that doesn't solve the problem.

Does anyone have an idea what I might have done wrong?

Thanks

xorg.conf
```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
#	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
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
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 420 Mac 32M/GeForce 440 Go 64M]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"		"1"
	Option 		"RenderAccel" 	"true" 
	Option 		"AllowGLXWithComposite" 	"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 420 Mac 32M/GeForce 440 Go 64M]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
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
	InputDevice	"Synaptics Touchpad"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

Section "Extensions"
        Option  "Composite" "Enable"
EndSection

```

themerc (Smoothwall)
```

button_offset=1
button_spacing=1
full_width_title=true
title_horizontal_offset=2
title_vertical_offset_active=3
title_vertical_offset_inactive=3
title_shadow_active=false
title_shadow_inactive=false
resize_opacity=100
move_opacity=60
popup_opacity=90
show_frame_shadow=true
show_popup_shadow=true

```

---

### Post by codejunkie on 2006-01-10
[QUOTE=Norm 2782]Hi and thanks for the guide. Unfortunately I just can't get the transparency to work. I've got the latest nVidia drivers on a -686 kernel for my mobile GeForce 4 MX. Down below my xorg.conf and themerc.

I already tried to re-enable DRI and GLCore, but that doesn't solve the problem.

Does anyone have an idea what I might have done wrong?

Thanks

xorg.conf
```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
#	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
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
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 420 Mac 32M/GeForce 440 Go 64M]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"		"1"
	Option 		"RenderAccel" 	"true" 
	Option 		"AllowGLXWithComposite" 	"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 420 Mac 32M/GeForce 440 Go 64M]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
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
	InputDevice	"Synaptics Touchpad"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

Section "Extensions"
        Option  "Composite" "Enable"
EndSection

```

themerc (Smoothwall)
```

button_offset=1
button_spacing=1
full_width_title=true
title_horizontal_offset=2
title_vertical_offset_active=3
title_vertical_offset_inactive=3
title_shadow_active=false
title_shadow_inactive=false
resize_opacity=100
move_opacity=60
popup_opacity=90
show_frame_shadow=true
show_popup_shadow=true

```[/QUOTE]

both your xorg.conf and themerc file seem to be ok, but as i mentioned in a earlier post, those theme settings dosen't change the window opacity, until you click and hold a window and move it. so if you can see window drop shadows then the composite manager is working correctly and to make a window 
stay transparent all of the time you have to use transset.

---

### Post by Norm 2782 on 2006-01-10
[QUOTE=codejunkie]both your xorg.conf and themerc file seem to be ok, but as i mentioned in a earlier post, those theme settings dosen't change the window opacity, until you click and hold a window and move it. so if you can see window drop shadows then the composite manager is working correctly and to make a window 
stay transparent all of the time you have to use transset.[/QUOTE]

Thanks for your reply, but I get no shadows, nor does the window become transparent when I click and drag it. :(

---

### Post by codejunkie on 2006-01-10
[QUOTE=Norm 2782]Thanks for your reply, but I get no shadows, nor does the window become transparent when I click and drag it. :([/QUOTE]
can you get shadows and transparency effects using metacity and xcompmgr?

---

### Post by Norm 2782 on 2006-01-10
[QUOTE=codejunkie]can you get shadows and transparency effects using metacity and xcompmgr?[/QUOTE]
Yup... that works like a charm. Transset works as well.

---

### Post by codejunkie on 2006-01-11
[QUOTE=Norm 2782]Yup... that works like a charm. Transset works as well.[/QUOTE]
im kinda lost on this one, if xcompmgr works than this should also, i don't know it might be your theme have you tried using the one i posted?

---

### Post by Norm 2782 on 2006-01-11
[QUOTE=codejunkie]im kinda lost on this one, if xcompmgr works than this should also, i don't know it might be your theme have you tried using the one i posted?[/QUOTE]

Using the one you posted right now. Nice theme btw. ;)
Restarted x.... no effect... restarted laptop... no effect.
Guess I'll have to do without composite effects :(

---

### Post by codejunkie on 2006-01-11
[QUOTE=Norm 2782]Using the one you posted right now. Nice theme btw. ;)
Restarted x.... no effect... restarted laptop... no effect.
Guess I'll have to do without composite effects :([/QUOTE]
sorry i dont know what's going on there you could always use xcompmgr for composite effects it works  well with metacity.

---

### Post by Stelmate on 2006-01-12
[QUOTE=Norm 2782]Hi and thanks for the guide. Unfortunately I just can't get the transparency to work. I've got the latest nVidia drivers on a -686 kernel for my mobile GeForce 4 MX. Down below my xorg.conf and themerc.

I already tried to re-enable DRI and GLCore, but that doesn't solve the problem.

Does anyone have an idea what I might have done wrong?

Thanks

xorg.conf
```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
#	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
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
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 420 Mac 32M/GeForce 440 Go 64M]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"		"1"
	Option 		"RenderAccel" 	"true" 
	Option 		"AllowGLXWithComposite" 	"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 420 Mac 32M/GeForce 440 Go 64M]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
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
	InputDevice	"Synaptics Touchpad"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

Section "Extensions"
        Option  "Composite" "Enable"
EndSection

```

themerc (Smoothwall)
```

button_offset=1
button_spacing=1
full_width_title=true
title_horizontal_offset=2
title_vertical_offset_active=3
title_vertical_offset_inactive=3
title_shadow_active=false
title_shadow_inactive=false
resize_opacity=100
move_opacity=60
popup_opacity=90
show_frame_shadow=true
show_popup_shadow=true

```[/QUOTE]

The only part I see that I have different on my box is I let the modules GLcore and dri load, 

Also under your "Extensions" section you have "Composite" listed as "Enable", I used "true".  Prob. does the same thing but I'm not 100% sure.

Also I let the Section "DRI" load as well.

---

### Post by Cybolic on 2006-01-13
I just found something cool at [http://gentoo-wiki.com]("http://gentoo-wiki.com/TIP_Xorg_X11_and_Tranparency#xcompmgr_and_transset") to add to this guide.

It makes it possible to change to transparency of the active window by scrolling your mousewheel.


Adapted for Ubuntu, the guide looks like this:

[LIST=1]
[*]Install the required X development packages (don't worry, they are not big): ```
sudo apt-get install libxcomposite-dev libxdamage-dev
```
[*]Get the patched transset, called transset-df, and unpack it to your homedir:```
wget http://forchheimer.se/transset-df/transset-df-5.tar.gz -P ~/ && tar -xzf transset-df-5.tar.gz -C ~/
```
[*]Install transset-df:```
cd ~/transset-df-5 && make && sudo make install
```
[*]Install xbindkeys:```
sudo apt-get install xbindkeys
```
[*]Setup xbindkeys to run transset-df when the mousewheel is used:```
gedit ~/.xbindkeysrc
```type in the following```
#Control+ScrollDown
"transset-df --min 0.1 -p --dec 0.2"
   mod4 + b:5

#Control+ScrollUp
"transset-df -p --inc 0.1"
   mod4 + b:4
``` and save the file
[*]Run xbindkeys by pressing Alt+F2 and type [FONT="Courier New"]**xbindkeys**[/FONT]
[*]This final step is optional, but you probably want to do it - adding xbindkeys to your gnome session so that it's started every time you log in.
Open the session-preferences from the System->Settings menu and add [FONT="Courier New"]**xbindkeys**[/FONT].

You're done!
Now hold down the Super-key (or Win-key if you want to call it that) and scroll!
[/LIST]

---

### Post by RoByLy on 2006-01-24
OMG! Thank you for helping me rediscover Gnome! It's so fast now and no more black drawings on the screen...Love it!

---

### Post by juantxorena on 2006-01-24
I tried this trick, and the WM was quite good, faster than Metacity, and everything. But I had problems with using some programs, like Eagle (an essential program to any electronic-linux geek). So I had to uninstall it.

Now I'm using Openbox as a sustitute to Metacity, very fast (faster than xfwm, I think), composite-compatible, and highly and easily customizable (less than fluxbox, icewm and others, but for me is enough). It has some problems with maximizing windows when starting some programs, but nothing that devil's pie can't fix.

If someone has problems with this xfwm, I sugest trying Openbox.

P.D. Sorry for the possible offtopic

---

### Post by zachtib on 2006-01-24
Can someone help me get this working (better) with an ATI Radeon 9000 card?

I followed the steps provided, and I can get it working using the Radeon driver, but it I use the fglrx driver, xfwm freaks out.

I'd like to be able to use the fglrx driver, as the radeon driver doesn't offer me any acceleration

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
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

        # paths to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/CID"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load  "GLcore"
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
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "Emulate3Buttons" "true"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Mobility 9000 M9 (R250 Lf)"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Radeon 9000"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Option      "RenderAccel" "true"
	Option	    "AllowGLXWithComposite" "true"
EndSection

Section "Device"
	Identifier "Radeon"
	Driver "radeon"
	Option "AccelMethod" "EXA"
	Option "AGPMode" "4"
	Option "EnablePageFlip" "true"
	Option "DDCMode"
	Option "RenderAccel" "true"
	Option "SubPixelOrder" "NONE"
	Option "ColorTiling" "false"
	Option "AllowGLXWithComposite" "true"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Mobility 9000 M9 (R250 Lf)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 0"
	Device     "Radeon"
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

Section "Extensions"
        Option  "Composite" "Enabled"
EndSection

```

at the moment, i have disabled the "show window contents when moving" option, as it really slows my computer down.

If anyone can help, I'd greatly appreciate it

Either way, XFWM is MUCH nicer than metacity

---

### Post by codejunkie on 2006-01-24
[QUOTE=zachtib]Can someone help me get this working (better) with an ATI Radeon 9000 card?

I followed the steps provided, and I can get it working using the Radeon driver, but it I use the fglrx driver, xfwm freaks out.

I'd like to be able to use the fglrx driver, as the radeon driver doesn't offer me any acceleration

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
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

        # paths to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/CID"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load  "GLcore"
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
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "Emulate3Buttons" "true"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Mobility 9000 M9 (R250 Lf)"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Radeon 9000"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Option      "RenderAccel" "true"
	Option	    "AllowGLXWithComposite" "true"
EndSection

Section "Device"
	Identifier "Radeon"
	Driver "radeon"
	Option "AccelMethod" "EXA"
	Option "AGPMode" "4"
	Option "EnablePageFlip" "true"
	Option "DDCMode"
	Option "RenderAccel" "true"
	Option "SubPixelOrder" "NONE"
	Option "ColorTiling" "false"
	Option "AllowGLXWithComposite" "true"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Mobility 9000 M9 (R250 Lf)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 0"
	Device     "Radeon"
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

Section "Extensions"
        Option  "Composite" "Enabled"
EndSection

```

at the moment, i have disabled the "show window contents when moving" option, as it really slows my computer down.

If anyone can help, I'd greatly appreciate it

Either way, XFWM is MUCH nicer than metacity[/QUOTE]
you have three device sections in your xorg.conf file there should be only one if your using one video card and this is an nvidia card only options and shouldn't be there unless your using an nvidia card
```

Option	    "AllowGLXWithComposite" "true"

```
you should have just added these options to your original device section
```

Option "AccelMethod" "EXA"
Option "AGPMode" "4"
Option "EnablePageFlip" "true"
Option "DDCMode"
Option "RenderAccel" "true"
Option "SubPixelOrder" "NONE"
Option "ColorTiling" "false"

```
try removing the unneeded device sections and add the above options to your device section.

---

### Post by zachtib on 2006-01-24
yeah, my xorg.conf file was a mess, most of that information wasn't ever used, i was just too lazy to clean it up.  I'll go do so now.

---

### Post by zachtib on 2006-01-24
How's this?
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
	Screen      0  "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

        # paths to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/CID"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load  "GLcore"
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
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "Emulate3Buttons" "true"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "Monitor"
	Identifier   "Default Monitor"
EndSection

Section "Device"
	Identifier "Radeon"
	Driver "radeon"
	Option "AccelMethod" "EXA"
	Option "AGPMode" "4"
	Option "EnablePageFlip" "true"
	Option "DDCMode"
	Option "RenderAccel" "true"
	Option "SubPixelOrder" "NONE"
	Option "ColorTiling" "false"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Radeon"
	Monitor    "Default Monitor"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
        Option  "Composite" "Enabled"
EndSection
```

That improved the performance a little bit, but I still don't have 3d acceleration.  I'mgoing to try out the fglrx drivers and report back

---

### Post by zachtib on 2006-01-24
OK, the fglrx driver loaded, and is working properly with the composite manager, but my glxgears frames dropped from ~1200 to ~200

---

### Post by codejunkie on 2006-01-24
[QUOTE=zachtib]OK, the fglrx driver loaded, and is working properly with the composite manager, but my glxgears frames dropped from ~1200 to ~200[/QUOTE]
im not real familiar with ati cards it's been a while since i've used anything since nvidia but if remember correctly you when using the fglrx driver gkxgears doesn't work you have to use something like fglrxgears.

---

### Post by zachtib on 2006-01-24
[QUOTE=codejunkie]im not real familiar with ati cards it's been a while since i've used anything since nvidia but if remember correctly you when using the fglrx driver gkxgears doesn't work you have to use something like fglrxgears.[/QUOTE]
glxgears has always worked fine for me.


not sure what I did, but I broke the fglrx drivers again, back to the radeon drivers.

---

### Post by zachtib on 2006-01-25
just noticed, since switching to xfwm, some apps, like vlc cannot go to fullscreen

---

### Post by detyabozhye on 2006-01-29
Works great. Thanks. ^_^

EDIT: Only one problem: I can't watch DVDs anymore. Help?
EDIT: I disabled the composite manager, and DVDs are back. I guess the only way to have both would be to install a newer version of the nVidia drivers, but I'm too lazy. XD

---

### Post by akiss on 2006-01-30
[QUOTE=codejunkie]
and finaly the lastthing were going to make some changes to our default xfwm4 WM theme by going into the /usr/share/themes dir
find the current theme were using and add these lines to the bottom of the "themerc" file.
```

resize_opacity=100
move_opacity=60
popup_opacity=90
show_frame_shadow=true
show_popup_shadow=true

``` 
[/QUOTE]

You can also enable the setting for all available themes by adding those lines to ~/.config/xfce4/xfwm4/xfwm4rc file. I think this is a cleaner way.

Nice HOWTO!

---

### Post by fortytwo on 2006-01-31
Great guide, the transparent effects are great.  I've got a couple questions:

Any way to just plain set the transparency for a window?  Instead of just when you're dragging it?  Do I need transset to do this?

After installing all the, xmms has stopped working, I get the following error:
```

Message: device: default
Gdk-ERROR **: BadDrawable (invalid Pixmap or Window parameter)
serial 1594 error_code 9 request_code 53 minor_code 0

```
Anyone have any idea on how to fix that?

---

### Post by codejunkie on 2006-01-31
[QUOTE=fortytwo]Great guide, the transparent effects are great.  I've got a couple questions:

Any way to just plain set the transparency for a window?  Instead of just when you're dragging it?  Do I need transset to do this?

After installing all the, xmms has stopped working, I get the following error:
```

Message: device: default
Gdk-ERROR **: BadDrawable (invalid Pixmap or Window parameter)
serial 1594 error_code 9 request_code 53 minor_code 0

```
Anyone have any idea on how to fix that?[/QUOTE]
as of right now it seems like all composite managers seem to affect certian things like some video/media players in funny ways and sometimes the composite managers just crash. myself when i watch certian types of video or im am working on something i can't take a chance on anything locking up i use a different user account that doesn't have composite effects enabled, for me that seems to be the easiest work around.

---

### Post by DigitalDuality on 2006-01-31
OK i've royally screwed up somehow...

I made a backup of xorg.conf before making changes  unfortunately i named the file xorg (copy).conf and couldn't do shit with it in the command line.

X simply wouldn't start.  I forgot the error message.  There seemed to be a dated xorg file in the directory too and no idea how it got there but i tried using that and voila ... Xwin came right up.

I've uninstalled  xfwm4, and gotten rid of it's shortcut.  I've also rebuilt my xorg.conf from scatch.

But i'm still having two problems.

#1... My logout button won't work even though xfwm4 has been removed

#2..when i start up now i no longer have a login screen to log into.  and when i start X, instead of their being the Ubuntu default splash screen showing Nautilus and other apps starting up.. i get a ..what looks like a low-res screen of white and green pixels and an X for a cursor.  Then it boots up as normal and ..from what i can tell..everything seems to be behaving.

I attempt to open up System --> Administration --> Login Screen and it simply doesn't come up.

Any ideas? 

All i want is whatever i did to be un-done.  I've spent a good amount of time configuring everything just the way i like.. i'd hate to start from scratch again.  I'm not really sure where i went wrong.  But i'm more concerned on fixing this system back to the way i had it before than anything else at this point.

I might try this again when i'm a bit more advanced.

---

### Post by codejunkie on 2006-01-31
[QUOTE=DigitalDuality]OK i've royally screwed up somehow...

I made a backup of xorg.conf before making changes  unfortunately i named the file xorg (copy).conf and couldn't do shit with it in the command line.

X simply wouldn't start.  I forgot the error message.  There seemed to be a dated xorg file in the directory too and no idea how it got there but i tried using that and voila ... Xwin came right up.

I've uninstalled  xfwm4, and gotten rid of it's shortcut.  I've also rebuilt my xorg.conf from scatch.

But i'm still having two problems.

#1... My logout button won't work even though xfwm4 has been removed

#2..when i start up now i no longer have a login screen to log into.  and when i start X, instead of their being the Ubuntu default splash screen showing Nautilus and other apps starting up.. i get a ..what looks like a low-res screen of white and green pixels and an X for a cursor.  Then it boots up as normal and ..from what i can tell..everything seems to be behaving.

I attempt to open up System --> Administration --> Login Screen and it simply doesn't come up.

Any ideas? 

All i want is whatever i did to be un-done.  I've spent a good amount of time configuring everything just the way i like.. i'd hate to start from scratch again.  I'm not really sure where i went wrong.  But i'm more concerned on fixing this system back to the way i had it before than anything else at this point.

I might try this again when i'm a bit more advanced.[/QUOTE]
i don't know exactly what changes your trying to undo because you didn't say what you changed in you xorg.conf file. but if your just wanting to reset the xorg.conf file to the default config run
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
NOTE: if you do this you will have to redo any changes you made to the xorg.conf file such as changing the resolution changing the driver etc. 
as for the menu the only change my howto made to the menu you can undo by opening Applications/SystemsTools/Configuration editor  
navigate to apps/gnome-session/options and recheck the logout_prompt box. hope this helps you get it sorted out.

---

### Post by DigitalDuality on 2006-02-01
the xorg.conf file is back to normal.  But the changes i made were exactly the changes this Howto advised me to do up until the instructions to restart X for the first time.

Curious..what's the difference between dkpg-reconfigure with and without the -phigh?

What i'm looking to set back..to at least the default is what i numbered.

#1-- logout button freezes.  I do not want to bypass the prompt screen.  I want the prompt screen and for the logout button to work again

#2.  I have no idea how to get my Login screen back.  

and well.. #3.. the Ubuntu default splash screen would be nice to have back too..

from there i can configure back to the way i had it i guess.  My monitor/card settings are fine and back to normal. And.. i think all traces of xfwm4 have been removed...

---

### Post by codejunkie on 2006-02-01
[QUOTE=DigitalDuality]the xorg.conf file is back to normal.  But the changes i made were exactly the changes this Howto advised me to do up until the instructions to restart X for the first time.

Curious..what's the difference between dkpg-reconfigure with and without the -phigh?

What i'm looking to set back..to at least the default is what i numbered.

#1-- logout button freezes.  I do not want to bypass the prompt screen.  I want the prompt screen and for the logout button to work again

#2.  I have no idea how to get my Login screen back.  

and well.. #3.. the Ubuntu default splash screen would be nice to have back too..

from there i can configure back to the way i had it i guess.  My monitor/card settings are fine and back to normal. And.. i think all traces of xfwm4 have been removed...[/QUOTE]
sudo dpkg-reconfigure xserver-xorg let's you configure the xserver manually with this option you need to know a little more info about your card monitor fequencies etc 
using it with the -phigh option
sudo dpkg-reconfigure -phigh xserver-xorg automaticly sets up the xorg.conf file just like the ubuntu installer does.
to get your logout prompt back follow the steps i provided in my earlier post about the gnome configuration editor also i forgot to mention earlier you also need to remove the .gnomerc file in your home dir to undo all the changes made by this howto you can do that by copying and pasting this into a terminal
```
rm ~/.gnomerc
```or open nautilus click view and then show hidden files and delete the .gnomerc file logout and then log back in to relod teh default settings hope this helps.

---

### Post by frodon on 2006-02-01
Does transset-df works with xfce WM ?

---

### Post by DigitalDuality on 2006-02-01
thanks a million codej  :)  

I'll give this another try in a month or so. I definately love the screenshots.

---

### Post by endersshadow on 2006-02-01
Well, I have xfwm4 and compositing enabled, and it's been amazing thus far.  Except for one little problem.  In Firefox, when I scroll down or up on web pages it puts my CPU 100% and lags...I've tried disabling and smooth scrolling and auto scrolling, but to no avail.  This also happens in Epiphany and any other browser that uses the Gecko engine.  Opera doesn't do this, though.  Personally, I absolutely hate Opera and would like to keep my beloved Firefox (hooray extensions).  Any ideas?

---

### Post by codejunkie on 2006-02-01
[QUOTE=frodon]Does transset-df works with xfce WM ?[/QUOTE]
transet seems to work fine with xfce never tried transset-df though so i can't say for sure.

---

### Post by LordBug on 2006-02-01
I just installed XFWM via the original instructions, minus the transparency theme changes.  I then installed transset-df and the xbindkeys script from Cybolic.  So far, in my 5 minutes of testing, everything is working ok.  Firefox is good, XMMS is good, no lag or slowdowns (nVidia 7667 drivers).

---

### Post by detyabozhye on 2006-02-01
Do you know how to make xcompmgr not fraw shadows on my gDesklets and kxdocker?

---

### Post by DigitalDuality on 2006-02-01
[QUOTE=codejunkie]
as for the menu the only change my howto made to the menu you can undo by opening Applications/SystemsTools/Configuration editor  
navigate to apps/gnome-session/options and recheck the logout_prompt box. hope this helps you get it sorted out.[/QUOTE]

:neutral: still not working...  and still can't get the login screen back

---

### Post by jacrider on 2006-02-02
Thanks for this HOW-TO.

I have installed everything and it seems to be working very well.  My only question in after logging in, the Ubuntu "box" in the middle of the screen is there for several minutes, and my Gdesklets don't appear until it goes away.  I assume some process is going on, but is there a way I can speed that up?

Thanks.

---

### Post by codejunkie on 2006-02-02
[QUOTE=jacrider]Thanks for this HOW-TO.

I have installed everything and it seems to be working very well.  My only question in after logging in, the Ubuntu "box" in the middle of the screen is there for several minutes, and my Gdesklets don't appear until it goes away.  I assume some process is going on, but is there a way I can speed that up?

Thanks.[/QUOTE]
i've noticed this when using gdesklets and the only thing i've found that seems to fix it is not to have gdesklets startup when loging in just launch them after the desktop is up on my computer they hang for a minute if i run them on startup.

---

### Post by codejunkie on 2006-02-02
[QUOTE=DigitalDuality]:neutral: still not working...  and still can't get the login screen back[/QUOTE]
if your talking about the login screen where you enter in your username & password try ```
sudo apt-get install --reinstall gdm
```you must have removed it when you uninstalled some packages.

---

### Post by codejunkie on 2006-02-02
[QUOTE=detyabozhye]Do you know how to make xcompmgr not draw shadows on my gDesklets and kxdocker?[/QUOTE]
nope i've been fighting with this one myself if i do find the answer i'll be sure and let you know how i fixed it though.

---

