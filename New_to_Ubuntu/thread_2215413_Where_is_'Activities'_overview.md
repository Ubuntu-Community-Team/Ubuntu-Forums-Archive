---
title: "Where is 'Activities' overview"
date: 2014-04-06
forum: New to Ubuntu
---

### Post by tarzanofnazareth on 2014-04-06
Hello all 

Naturallyi ma new to this Linux environment etc - pushed here by Windows XP's imminent expiry. Not overly tech minded, but not completely dumb neither. I have taken the plunge, however, I am not hearing any sound - which is particularly annoying as i am a musician and need my computer for that. I reckon it is one of a couple if reasons - either my soundcard is incompatible or it hasn't been detected properly. I hope the second!

I am trying to use the help files but they are not very clear - it says   [COLOR=#2E3436][FONT=sans-serif]Go to the [/FONT][/COLOR][COLOR=#515C5F][FONT=sans-serif]Activities[/FONT][/COLOR][COLOR=#2E3436][FONT=sans-serif] overview and open a Terminal.  [/FONT][/COLOR] [SIZE=2] But where is said mysterious Activities overview - I have looked now for 2 hours and nothing... i'm sure somebody can help me with at least finding that. For the record, the SOundcard is an E-MU

Thanks in advance[/SIZE]
[COLOR=#2E3436][FONT=sans-serif]
[/FONT][/COLOR]

---

### Post by buzzingrobot on 2014-04-06
You probably just need to use the Sound configuation tool.  You didn't mention which version of Ubuntu you are using, but "Activities" is a feature of the Gnome desktop environment used in the Ubuntu Gnome version. (On Gnome, you will see the word "Activities" on the left side of the top panel.) There, click the small triangle on the far right of the top panel to display a drop down menu. Three icons will be displayed along the bottom. Click the icon on the left to open Systems Settings.  You will see an icon for the sound tool.

If you are using Ubuntu Unity, System Setting is also available with a click at the right end of the top panel.

it would be helpful to know which version and release of Ubuntu you are using.

---

### Post by grahammechanical on 2014-04-06
Well, Ubuntu is definitely a Linux distribution and stuff like help documentation comes under the heading of "Community" and is sometimes out of date because there are not enough people willing to write help documentation. But there is something that you can do to help us help you. Please tell us the version of Ubuntu that you are using? Or, which version of which flavour if you are using a Ubuntu flavour. Or, which user interface that is installed.

The latest versions of Ubuntu, 12.04, 13.10 and 14.04 (to be released at the end of April) come with the Unity user interface. The flavours of Ubuntu have other user interfaces and it all makes a difference in giving directions.

For example, Ubuntu+Unity does not have the structured menu system that you are familiar with from Windows XP and therefore it does not have an Activities menu. I am looking at the Ubuntu help documentation now and I find it up to date.

No sound?

>  [COLOR=#3C3C3C][FONT=sans-serif]Click the [/FONT][/COLOR][COLOR=#6C6C6C][FONT=sans-serif]sound menu[/FONT][/COLOR][COLOR=#3C3C3C][FONT=sans-serif] on the menu bar (it looks like a speaker) and make sure that the sound is not muted or turned down.[/FONT][/COLOR][COLOR=#3C3C3C][FONT=sans-serif]Some laptops have mute switches or keys on their keyboards—try pressing that key to see if it unmutes the sound.[/FONT][/COLOR]
[COLOR=#3C3C3C][FONT=sans-serif]
You should also check that you have not muted the application that you are using to play sound (e.g. your music player or video player). The application may have a mute or volume button in its main window, so check that. Also, click the sound menu on the menu bar and choose [COLOR=#6C6C6C]Sound Settings[/COLOR]. When the [COLOR=#6C6C6C]Sound[/COLOR] window appears, go to the [COLOR=#6C6C6C]Applications[/COLOR] tab and check that your application is not muted.[/FONT][/COLOR]


Check that the sound card was detected properly

> [COLOR=#3C3C3C][FONT=sans-serif]Your sound card may not have been detected properly. If this has happened, your computer will think that it isn't able to play sound. A possible reason for the card not being detected properly is that the drivers for the card are not installed.[/FONT][/COLOR]
[COLOR=#3C3C3C][FONT=sans-serif]
[LIST]
[*]Go to the [Dash]("xref:unity-dash-intro") and open the Terminal.
[*]Type [FONT=monospace]aplay -l[/FONT] and press Enter.
[*]A list of devices will be shown. If there are no [COLOR=#6C6C6C]playback hardware devices[/COLOR], your sound card has not been detected.
[/LIST]
[/FONT][/COLOR]

> [COLOR=#3C3C3C][FONT=sans-serif]If your sound card is not detected, you may need to manually install the drivers for it. How you do this will depend on the card you have.[/FONT][/COLOR]
[COLOR=#3C3C3C][FONT=sans-serif]You can see what sound card you have by using the [FONT=monospace]lspci[/FONT] command in the*Terminal*. You can get more complete results if you run [FONT=monospace]lspci[/FONT] as [superuser]("xref:user-admin-explain"); enter [FONT=monospace]sudo lspci[/FONT] and type your password. See if an *audio controller* or *audio device* is listed—it should have the sound card's make and model number.[FONT=monospace]sudo lspci -v[/FONT] will show a list with more detailed information.[/FONT][/COLOR]
[COLOR=#3C3C3C][FONT=sans-serif]You may be able to find and install drivers for your card by searching the Internet. Otherwise, you can [file a bug]("xref:report-ubuntu-bug").[/FONT][/COLOR]
[COLOR=#3C3C3C][FONT=sans-serif]If you can't get drivers for your sound card, you might prefer to buy a new sound card. You can get sound cards that can be installed inside the computer and external USB sound cards.[/FONT][/COLOR]


I think that is clear, even if it is unfamiliar to you and it is up to date for Ubuntu+Unity.

By the way in Ubuntu+Unity we open the Dash by click on the Ubuntu icon at the top of the Launcger (panel on the left side of the screen) or by pressing the Super key (the key with the flying windows logo).

This is what I see when i enter aplay -l in a terminal

> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD1988B Analog [AD1988B Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD1988B Digital [AD1988B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: AD1988B Alt Analog [AD1988B Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Regards.

---

### Post by tarzanofnazareth on 2014-04-06
Thanks for your replies.

I am (i think) using Ubuntu One. At least when i go to the System settings there is a ubunto one icon in the personal settings area. I havent actually registered for this yet - maybe that is a hinderance? As regards gnomes or other names, i don't know.

I initially got the thread saying go to the dash (equally as mystifying and un-locatable). Now when i go to the help, i get the go to the activities suggestion.

I know it is clear, if you know where these things are, its just - i really dont. 

thanks

---

### Post by buzzingrobot on 2014-04-06
Ubuntu One is not a version of Ubuntu.  It is a cloud storage facility similar to Dropbox. Whether you have registered with it, or use it, or not, makes no difference here.

Go to Systems Settings and click the "Details" icon.  It will display the Ubuntu version and release you are using.

---

### Post by sotiris2 on 2014-04-06
[this](http://en.wikipedia.org/wiki/File:Ubuntu_13.04_Desktop.png) is Unity. [This](http://en.wikipedia.org/wiki/File:GNOME-Shell-3.10.png) is gnome shell. 

 If you are using Unity, dash is the search panel/window/pane/whatever that pops up if you click on top icon in the left bar or if you press your **win** key. There search for terminal and a new window will open up (black and white probably). There you can type (or better copy and paste via clicking the mouse wheel) the *aplay-l* command. 

If you are using gnome shell try pressing *Alt+Ctrl+T* and you will probably get a terminal as well where you can type that command.

---

### Post by tarzanofnazareth on 2014-04-06
crikey - this is a confusing experience - the forum wouldn't let me post then - it had logged me out for some reason...

anyway it is Ubuntu 12.04 LTS

as regards those images of Gnome and Unity, it looks nothing like either tbh 

the win key does nothing

i have tried the alt/ctrl+t and tried typing in that command - nothing happening - says doesnt recognise that command

---

### Post by tarzanofnazareth on 2014-04-06
grahammechanical:

i have managed to make the command work - this is what i get when i enter  the aplay -l command:

live@live:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
live@live:~$

---

### Post by buzzingrobot on 2014-04-06
> **tarzanofnazareth said:**
> 

as regards those images of Gnome and Unity, it looks nothing like either tbh 

You won't see "Activities" unless it is Gnome.

If it is Unity, you should see a vertical column of icons at the left of the screen, extending from the top to the bottom of the screen.  That is the "Launcher".

If you see neither, then either you are not running either Gnome or Unity, or the one you are using is installed incorrectly.

> the win key does nothing

*Tapping* the Win key in both Gnome and Unity should display a search bar.  Holding the Windows key down for a few seconds displays a popup in Unity.

> i have tried the alt/ctrl+t and tried typing in that command - nothing happening - says doesnt recognise that command

aplay is a standard Ubuntu utility program. If "aplay -l" returns a message that the command is not recognized ( more likely it was, "...not found") that's another indication of a possible broken installation of Ubuntu.

What happened when you clicked the "Sound" icon in Systems Settings?  Were you able to successfully configure the sound settings?

---

### Post by tarzanofnazareth on 2014-04-06
buzzingrobot: managed to get aplay -l to work  (l not 1)... see above post  - not sure what it means

also, maybe i should say it is zorin 6 not 8


just one more thing which may be something to with it - i just decided to 'change the look' and when i tried it said you need to do a full installation of Zorin... which i thought i had - 

anyway - i have been sat in fornt of this computer for 12 hours now and am too tired to do anymore right now

:(

---

### Post by buzzingrobot on 2014-04-06
> **tarzanofnazareth said:**
> buzzingrobot: managed to get aplay -l to work  (l not 1)... see above post  - not sure what it means

It is showing that it detected the audio component on your system's motherboard (the ALC883 Analog) and it also detected the HDMI component of the Nvidia video card you apparently have installed.

This verifies that the sound chips on your system have been recognized.

You *need* to use "System Settings -> Sound" to configure sound.  Also, make sure sound is simply not muted by clicking on the volume control icon.

> ...also, maybe i should say it is zorin 6 not 8

This is the first intance you have said it is any version of Zorin.  Previously, you identified it as Ubuntu 12.04.  Zorin is based on Ubuntu, but it is a different Linux distribution.

Still, if you have not properly configured your sound settings, you can't know if sound is working correctly. (I am not familiar with Zorin, but I assume it has a sound configuration tool.)

---

### Post by buzzingrobot on 2014-04-06
From looking at the Zorin site, it seems to produce a free version and a "Premium" version that requires a "donation" to acquire.

A forum is available there, as well.  It's likely a more productive place for questions specific to Zorin.

---

### Post by tarzanofnazareth on 2014-04-07
So my tribulations continue - and it isnt fun.

I have just spent the best part of 2 hours not being able to start up my computer - initially it was saying it couldnt read any devices or graphics card on start up, then it was just loading and not going anywhere. However i am persistent and eventually it loaded like yesterday, as though nothing has happened, except that yet still my sound card doesn't work. 

 Perhaps, I may have Gnome as when i went into the look changer thing it offered me Windows 7, XP and Gnome??!!

Please help me to like Linux / Zorin / Ubuntu and make it work

---

### Post by tarzanofnazareth on 2014-04-07
thanks - i will check the zorin site

---

