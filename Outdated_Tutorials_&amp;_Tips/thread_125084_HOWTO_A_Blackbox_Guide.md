---
title: "HOWTO: A Blackbox Guide"
date: 2006-02-03
forum: Outdated Tutorials &amp; Tips
---

### Post by bluevoodoo1 on 2006-02-03
A Blackbox Guide.


After searching the internet, I found there was really no easy, all-in-one guide for the new Blackbox user. Although some of this information has been listed elsewhere, here's an attempt at putting together all the information I found most useful. This guide assumes you are using Gnome, and are familiar with the GDM. Much of this uses the terminal, but can also be done with Nautilus. I have included some of my configuration files and a screenshot. Blackbox isn't terribly hard to install and configure. It can be very fast, as long as you don't mind typing some commands. Here we go!


I.   INSTALLATION
II.  CONFIGURATION
III. OTHER USEFUL PROGRAMS
IV.  STARTUP
V.   EYE CANDY
VI.  FURTHER READING and SOURCES


I. INSTALLATION:

1. You will have to enable the Universe repositories... [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
```

sudo apt-get install blackbox blackbox-themes

```

Or use Synaptic and give it a search, they should be all there.


That's it!!! A few of the following will help with customizing.

======================================================

Now, the following will move some folders to your home folder to make editing easier.

2. See if there is a .blackbox folder in your home directory. "ls -a"  If yes, skip skep 3. If not...

3.
```

cd
mkdir .blackbox
```

4. 
We need a .blackboxrc file. 

```

gedit .blackboxrc

```

paste this in... replacing bluevoodoo1 with your username.
> 
session.styleFile:      /usr/share/blackbox/styles/Gray
session.menuFile:       /home/**bluevoodoo1**/.blackbox/menu
session.screen0.slit.placement: CenterRight
session.screen0.slit.direction: Vertical
session.screen0.slit.onTop:     False
session.screen0.slit.autoHide:  False
session.screen0.toolbar.onTop:  False
session.screen0.toolbar.autoHide:       False
session.screen0.toolbar.placement:      BottomCenter
session.screen0.toolbar.widthPercent:   66
session.screen0.enableToolbar:  True
session.screen0.workspaces:     4
session.screen0.workspaceNames: Workspace 1,Workspace 2,Workspace 3,Workspace 4
session.screen0.strftimeFormat: %I:%M %p
session.windowSnapThreshold:    0
session.autoRaiseDelay: 400
session.placementIgnoresShaded: True
session.focusLastWindow:        True
session.opaqueMove:     True
session.changeWorkspaceWithMouseWheel:  True
session.imageDither:    OrderedDither
session.windowPlacement:        RowSmartPlacement
session.shadeWindowWithMouseWheel:      True
session.opaqueResize:   True
session.toolbarActionsWithMouseWheel:   True
session.rowPlacementDirection:  LeftToRight
session.maximumColors:  0
session.disableBindingsWithScrollLock:  False
session.fullMaximization:       False
session.colPlacementDirection:  TopToBottom
session.doubleClickInterval:    250
session.edgeSnapThreshold:      0
session.focusNewWindows:        True
session.focusModel:     ClickToFocus


(of course the path can be to any location you prefer)

II. CONFIGURATION

-Menu/Styles: 

1.Menu:
Since we changed the path of the menu file, we have to add our own menu. **If you don't paste in some sort of menu then nothing will appear with a right click on the desktop**. 

```

gedit .blackbox/menu

```

Here is an example of my menu. [nop] () = a space

```

[begin] (b l a c k b o x )
	[exec] (Eterm) {Eterm -x -0 --trans --scrollbar=off --buttonbar 0 --geometry 79x35+13+495 --font-fx none -f lightgrey}
	[nop] ()
	[submenu] (terminals) {terminals}
		[exec] (aterm) {aterm -tr -bg black -fg lightgrey -fn 7x14 -fb 7x14 +vb +sb -geometry 79x32+13+495}
		[exec] (gterm) {gnome-terminal}
		[exec] (kterm) {konsole}
		[exec] (xterm) {xterm -ls}
	[end]
	[submenu] (gnome) {gnome}
		[exec] (nautilus) {nautilus --no-desktop}
		[exec] (gnome-theme-manager) {gnome-theme-manager}
		[exec] (gnome-settings-daemon) {gnome-settings-daemon}
		
	[end]
	[submenu] (audio) {}
		[exec] (xmms) {xmms}
		[exec] (gnome-volume) {gnome-volume-manager}
	[end]
	[submenu] (internet) {}
		[exec] (firefox) {firefox}
		[exec] (gaim) {gaim}
		[exec] (gftp) {gftp}
		[exec] (bluefish) {bluefish}
		[exec] (firestarter) {gksudo /usr/sbin/firestarter}
		[exec] (virus scanner) {aegis-virus-scanner}
	[end]
	[submenu] (graphics) {}
		[exec] (the gimp) {gimp}
	[end]
	[submenu] (office apps) {}
		[exec] (oo.o writer) {ooffice2}
	[end]
	[submenu] (video) {}
		[exec] (gmplayer) {gmplayer}
		[exec] (vlc) {vlc}
		[exec] (xine) {xine}
	[end]
	[submenu] (system monitor) {}
		[exec] (monitor start) {conky}
		[exec] (monitor stop) {killall conky}
	[end]
	[nop] ()
	[workspaces] (workspace list)
	[config] (configuration)
	[nop] ()
	[submenu] (startup) {}
		[exec] (gnome-settings-daemon ) {gnome-settings-daemon &}
		[exec] (conky) {conky &}
		[exec] (Esetroot) {Esetroot .blackbox/backgrounds/Complex_2.jpg}
		[exec] (wmbutton) {wmbutton &}
		[exec] (wmweather) {wmweather -w -s KROC &}
		[exec] (wmcpuload ) {wmcpuload &}
		[exec] (wmclock) {wmclock -12 -led white &}
	[end]
	[nop] ()
	[reconfig] (reconfigure)
	[restart] (restart) {}
	[exit] (exit)
[end]


```

2. Styles:
You can edit the styles by hand. Open your /usr/share/blackbox/styles/ files with your favorite text editor and edit away (colors/borders/fonts... etc.). To have a wallpaper install "eterm" to use its "esetroot" utility. Add/Replace this command to your current style file for a wallpaper/background

```

rootCommand: Esetroot /usr/share/blackbox/backgrounds/wallpaper.jpg

```

Log out. And it should be in the gdm! Some other neat styles can be found here. [http://snkmchnb.no-ip.com/bbstyles.php](http://snkmchnb.no-ip.com/bbstyles.php)



III. OTHER USEFUL PROGRAMS:

-conky: Used to monitor your system. Neat because it sits on the desktop as if it were part of it, displaying useful system information... CPU temps, RAM, swap, CPU+MEM usage, networking info...

1.
```

sudo apt-get install conky

```

or 

You can download the newest version from [http://conky.sourceforge.net/](http://conky.sourceforge.net/) and do the following: (you can add all or none of the following options during ./configure. I highly recommend --enable-double-buffer [more on that in a bit])

```

./configure --prefix=/usr --enable-xft --enable-mpd --enable-seti --enable-double-buffer --enable-own-window --enable-proc-uptime
make
sudo checkinstall

```

If you don't have checkinstall... I recommend getting it, especially for removing a package that is manually installed. 

2.
You can edit what appears by changing the .conkyrc file. (Make a backup first) 

```

cp .conkyrc ~/.conkyrc_backup
gedit .conkyrc

```

for conky variables... [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

-Potential problems with conky: Flickering.
To get rid of the flicker from conky you will to manually install it and make sure, make sure the following are true:

In .conkyrc

double_buffer yes

and in /etc/X11/xorg.conf (make a backup first!!)

```
sudo gedit /etc/X11/xorg.conf
```

add the following...

Section "Module" Load "dbe" 

Restart the computer, start conky, and it should not flicker! 

CONKY EXTRA: weather

From what I've read METAR support was stopped after version 1.3... but here's somewhat of a workaround (not the greatest, hopefully something better will work)

get python-pymetar...

```

sudo apt-get install python-pymetar
```

Then add the following line to your .conkyrc file (replacing KROC with your 4-digit code) (a HOW-TO for finding your code is listed under 'wmweather'). The number 60 refers to the time in seconds before updating. You can change it to anything you wish.

```
${texeci 60 pymetar KROC}
```

or

```
${execi 60 pymetar KROC}
```


The texeci works for me, others say that execi works for them, but I suggest you experiment and see which works for you.

(You might want to comment out some of the description or other features. Simply open the file (make a backup first if you would like) then type

```
sudo gedit /usr/bin/pymetar
```

and place a # on the line you don't want to display. I commented out the following because the output was too long...

```

#print "Weather report for %s (%s) as of %s" %\

#    (pr.getStationName(), station, pr.getISOTime())

#print "Values of \"None\" indicate that the value is missing from the report."

```

You can search for your METAR here...

[http://adds.aviationweather.noaa.gov/metars/stations.txt](http://adds.aviationweather.noaa.gov/metars/stations.txt)

Find your code then replace my 'KROC' with your four digit code, or you will simply get the weather for Rochester, NY USA.


IV. STARTUP

1. We make a startup script.
2. We change the path of exec blackbox in /usr/share/xsessions/blackbox.desktop

1. We create a script.
```
gedit ~/.bbstartup.sh
```
and paste this in
```

#!/bin/sh

gnome-settings-daemon &
conky &
exec /usr/local/bin/blackbox

```
then make it executable
```
chmod +x ~/.bbstartup.sh
```

2. We change the path of exec blackbox in /usr/share/xsessions/blackbox.desktop

first a backup.
```
sudo cp /usr/share/xsessions/blackbox.desktop /usr/share/xsessions/blackbox.desktop_backup
```
then
```
sudo gedit /usr/share/xsessions/blackbox.desktop
```

Before we change anything, It will look something like this...
```

[Desktop Entry]
Encoding=UTF-8
Name=BlackBox
Comment=Highly configurable and low resource X11 Window manager
Exec=/usr/local/bin/blackbox
Terminal=False
TryExec=/usr/local/bin/blackbox
Type=Application
```

then we change the Exec and TryExec to the path of the newly created script. Replacing bluevoodoo1 with your username.
```

[Desktop Entry]
Encoding=UTF-8
Name=BlackBox
Comment=Highly configurable and low resource X11 Window manager
Exec=/home/**bluevoodoo1**/.bbstartup.sh
Terminal=False
TryExec=/home/**bluevoodoo1**/.bbstartup.sh
Type=Application
```

Logout, and hopefully you'll be all set.

V. EYE CANDY: (more info on these topics can be found throughout the forums)

-Eterm: Terminal with many customizable features.

1.
```

sudo apt-get install eterm

```

2. Here's a sample. Please adjust geometry and -f color to your liking.
```
Eterm -x -0 --trans --scrollbar=off --buttonbar 0 --geometry 79x35+13+495 -f lightgrey
```

*yes it is "Eterm" not "eterm"

This is my command for Eterm. It will produce a transparent, borderless terminal with lightgray text in the exact position I want. Type "man Eterm" or "Eterm --help" to get a full listing of what each command does. For Eterm to be transparent and not simply shuffle a random background on startup, you must use Esetroot to set the wallpaper before launching Eterm... everytime you start Blackbox*. Use Esetroot and the path to the wallpaper you want, for example...

```

Esetroot /usr/share/blackbox/backgrounds/yourpicture.jpg

```

*Either use it as a code upon startup (listed above in IV. STARTUP), type that command into a terminal before the use of Eterm, make a custom application command and run it from the menu before Eterm, or add that line to your current style file. I use the last. 

VI. FURTHER READING and SOURCES

[http://blackboxwm.sourceforge.net/](http://blackboxwm.sourceforge.net/)

[http://ubuntuforums.org/showthread.php?t=18626&highlight=blackbox](http://ubuntuforums.org/showthread.php?t=18626&highlight=blackbox)
[http://snkmchnb.no-ip.com/bbstyles.php](http://snkmchnb.no-ip.com/bbstyles.php)
[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)
[http://www.dotfiles.com/software/wmmp3/](http://www.dotfiles.com/software/wmmp3/)
[http://home.nyc.rr.com/computertaijutsu/blackbox.html](http://home.nyc.rr.com/computertaijutsu/blackbox.html)
[http://www.dockapps.org/file.php/id/17](http://www.dockapps.org/file.php/id/17)
[http://www.linuxquestions.org/questions/showthread.php?t=218928](http://www.linuxquestions.org/questions/showthread.php?t=218928)
[http://adds.aviationweather.noaa.gov/metars/stations.txt](http://adds.aviationweather.noaa.gov/metars/stations.txt)

---

### Post by william_nbg on 2006-02-06
Nice how to! :D 

I've been getting blackbox set up on my computer for a week now, but there are a few useful things in your how to for me. Coming from bblean in my windows days I am used to bb conf - slowly getting better with Linux. 

I spent a week playing around with a way to run a start-up script, so far, your solution seems to be the only way without really screwing things up for Gnome.


[IMG]http://www.moonpad.net/images/bbscreenshot2.jpg[/IMG]

---

### Post by johannes on 2006-02-06
Yes, a very nice howto. Too bad you didn't post this a week earlier when I installed Blackbox. :)

One thing though, I think it is much easier to install the package "menu" which generates a program menu for practically all installed applications, and then delete the ones you don't want in it. "Menu" will also create a "Debian" entry in the Gnome menu, but if you don't want it you can easilly remove it with "Applications menu editor".

---

### Post by bluevoodoo1 on 2006-02-06
Thank you for the kind words. I will have a look at the menu package. That "Debian" menu somewhat annoys me, but you're right that it can be turned off. I'll have to give that a try.


EDITS: Added how to manually install conky, get rid of flickering in conky and how to add weather reading to conky.

---

### Post by george_apan on 2006-02-12
Very nice HOWTO, thank you! I just installed blackbox in my ubuntu on an old Cyrix 200MHz with 96MB that I use as a headless fileserver/bittorrent downloader and it flies! The same PC was struggling with XFCE.

One thing that gave me some trouble is that there was no ~/.blackbox/menu file and when I created one blackbox refused to read from it. What I had to do was create a .blackboxrc file in my home folder and then add the following line in it:
```
session.menuFile:       /home/george/.blackbox/menu
```
That was it... I had my menu after that.

---

### Post by bluevoodoo1 on 2006-02-12
[QUOTE=george_apan]One thing that gave me some trouble is that there was no ~/.blackbox/menu file and when I created one blackbox refused to read from it. What I had to do was create a .blackboxrc file in my home folder and then add the following line in it:
```
session.menuFile:       /home/george/.blackbox/menu
```
That was it... I had my menu after that.[/QUOTE]

Exactly! Hmm, I wonder why there wasn't a menu file? But your solution is perfect.

EDIT: george_apan, I added your suggestion.

---

### Post by skymt on 2006-02-12
One quick question: why Blackbox? Why not Fluxbox, or Openbox, or any of the other *boxen floating around? Is there anything special in BB that the others don't have yet?

---

### Post by bluevoodoo1 on 2006-02-12
[QUOTE=skymt]One quick question: why Blackbox? Why not Fluxbox, or Openbox, or any of the other *boxen floating around? Is there anything special in BB that the others don't have yet?[/QUOTE]

Both are based on older version of Blackbox code. Fluxbox is based on the Blackbox 0.61.1 code and Openbox is based on Blackbox 0.65.0 code. I'm currently running Blackbox 0.70.0. 

I've had the most success with Blackbox compared to Open* or Flux*. Why not experiment with them? I had some trouble having Black* and Flux* on my system at the same time, but perhaps experimenting one at a time is an idea? They all have features unique to them. Read up on them, there is some information around the forums and also in these links....

[http://blackboxwm.sourceforge.net/AboutBlackbox#WhatsDifferentAboutBlackbox](http://blackboxwm.sourceforge.net/AboutBlackbox#WhatsDifferentAboutBlackbox)
and
[http://fluxbox.sourceforge.net/](http://fluxbox.sourceforge.net/)
and
[http://icculus.org/openbox/about.php](http://icculus.org/openbox/about.php)

---

### Post by Maelgwyn on 2006-02-12
[QUOTE=bluevoodoo1]
```

sudo mv usr/share/blackbox/backgrounds ~/.blackbox/backgrounds
sudo mv usr/share/blackbox/styles ~/.blackbox/styles
sudo mv usr/share/blackbox/menu ~/.blackbox

```
[/QUOTE]


when I try to mv the /menu file, I get this:
```

mv: cannot stat `/usr/share/blackbox/menu': No such file or directory

```

:cry:

---

### Post by bluevoodoo1 on 2006-02-12
[QUOTE=Maelgwyn]when I try to mv the /menu file, I get this:
```

mv: cannot stat `/usr/share/blackbox/menu': No such file or directory

```

:cry:[/QUOTE]

Check to see if there actually is a menu file in the /usr/share/blackbox folder. Can't move something that doesn't exist! If it doesn't exist you can, with Nautilus (or Konqueror) create a new document in your  /home/your-user-name/.blackbox folder named "menu" Then make sure the .blackboxrc file points to that menu path. Then you can either use bbconf to add to your menu (to open it, sudo bbconf) or edit the menu file by hand. (I have an example listed). Hope that helps...

EDIT: I also noticed that I had a typo, it should be...

sudo mv /usr/share/blackbox/backgrounds ~/.blackbox/backgrounds
sudo mv /usr/share/blackbox/styles ~/.blackbox/styles
sudo mv /usr/share/blackbox/menu ~/.blackbox

and **NOT** be...

sudo mv usr/share/blackbox/backgrounds ~/.blackbox/backgrounds
sudo mv usr/share/blackbox/styles ~/.blackbox/styles
sudo mv usr/share/blackbox/menu ~/.blackbox

---

### Post by super on 2006-02-12
great blackbox guide!
you've done a really good job. :D 

just fyi:
you wrote in the guide.
> -Potential problems with menu/styles:
No text in the menu. Answer. Make sure the style file you're using states a font to be used. Many I've found will say "snap*" in place of a font.

'snap' actually is a part of the [artwiz font pack]("http://artwizaleczapka.sourceforge.net/"). a set of fonts made for fluxbox (or blackbox, i guess) it is not an error in the themes.

---

### Post by bluevoodoo1 on 2006-02-12
[QUOTE=super]great blackbox guide!
you've done a really good job. :D 

just fyi:
you wrote in the guide.


'snap' actually is a part of the [artwiz font pack]("http://artwizaleczapka.sourceforge.net/"). a set of fonts made for fluxbox (or blackbox, i guess) it is not an error in the themes.[/QUOTE]

OH wow thanks! I had no idea it was a font! Many style files I've seen have that listed as the font and I thought it was strange! Now it makes sense why the text wouldn't show up, since I don't have the snap font installed. I'll edit the guide and acknowledge your fix! Thanks!

---

### Post by bluevoodoo1 on 2006-02-13
Added how to install latest Blackbox 0.70.1 and how to add it to the gdm.

---

### Post by william_nbg on 2006-02-14
What about upgrading to the new version. I've got my .70 all up and running. Is it possible to upgrade somehow, or do I have to redo the whole thing?? OK, it might not be that big of a deal.

Is there a big difference. I was looking at the changelog and it said something about improved window placement - Have you seen a difference??

---

### Post by bluevoodoo1 on 2006-02-14
Well I've only been toying around with it for a few hours and I don't see too really anything new. The one that bugs me though is....

I don't use the blackbox panel, so I turned it off. But whenever I open the gnome-panel it sits above the normal place of the blackbox panel. It creates an open space on the bottom of the screen. So i have to manually move the gnome-panel down to the bottom of the window. Somewhat annoying, but just an observation.

---

### Post by m666 on 2006-02-26
Nice guide!
Finally I got rid of the flicking in conky! :D 
I can't figure out how to thread conky with xmms though. :-? 
Could you post a sample of your .conkyrc containing xmms section please?

---

### Post by bluevoodoo1 on 2006-02-26
[QUOTE=m666]Nice guide!
Finally I got rid of the flicking in conky! :D 
I can't figure out how to thread conky with xmms though. :-? 
Could you post a sample of your .conkyrc containing xmms section please?[/QUOTE]


I haven't figured that out yet, but that's probably because the version of conky I'm running 1.3.5 doesn't have xmms support... BUT on this [post ]("http://ubuntuforums.org/showpost.php?p=734531&postcount=138")of this [thread]("http://ubuntuforums.org/showthread.php?t=61297") it says that conky 1.4 is out AND it supports xmms (and some other things) you can get the .deb from the post or the source from [http://conky.sourceforge.net/](http://conky.sourceforge.net/). When I have some time I'll upgrade to 1.4 and test out the xmms support, if you beat me to it, tell me how it goes!

---

### Post by bluevoodoo1 on 2006-02-26
Well, rather than doing my work, I decided to compile conky 1.4 :mrgreen:. Be sure to read the README file to get all of the optional arguments for the ./configure... including --enable-xmms. I haven't gotten xmms up with conky yet... The README also includes all variables for 1.4. The links I posted above have some relevant information about xmms and getting it to work with conky (post 140 especially).

---

### Post by m666 on 2006-02-26
I got it working...
But XMMS is behaving very strange, skipping tracks, loosing custom skin...
I guess I have lot to do...
But not today. Maybe tomorrow. ;-)

---

### Post by nitefly on 2006-03-04
hi all, im quite new here. i thought id try ubuntu, i downloaded 5.10, installed it, but so far its only been a pain in the ***.
first boot, gdm shows up, but it wouldnt let me login. says xinitrc is missing. got around it by chown-ing my homefolder to myself. doh..
so im in. yaay!
so lets make it look better. blackbox is the solution! i tried apt-get, it didnt find the package. tried downloading the source, but couldnt compile it cause it was missing a bunch of stuff, like gcc, libiconv etc etc etc. opened up synaptic, got the packages it was crying for, one after another, until bb configured itself successfully. i ran a make and it returned lotsof errors.

so my question is:
how did you guys install blackbox onto your systems? following this great guide is a dead end for me, since im stuck at step 1.
how did you manage to compile it?

---

### Post by bluevoodoo1 on 2006-03-04
It's trickier if you compile it since you'll have to manually make an entry for it in the gdm. Do you have the 'build-essential' package? What exactly were the errors of make install? Can you post the terminal output of it? I suggest you get "checkinstall." Then use 'sudo checkinstall' instead of 'make install'. checkinstall will make a .deb file so later if you want to remove it you can use Synaptic to remove it or 'sudo dpkg -r BLAHBLAH'.

---

### Post by nitefly on 2006-03-07
found the build-essentials, installed it plus a bunch of other stuff, i managed to compile bb. yaay! now comes the big part, configuring it..
thanks for tip!

---

### Post by william_nbg on 2006-03-07
I had the same problem with 'no .rc' file. 

Found a good work around on the backbox home page, in their wiki

[http://blackboxwm.sourceforge.net/BlackboxDocumentation/BlackboxConfiguration#IDontHaveAConfigFileHowDoIGetOne](http://blackboxwm.sourceforge.net/BlackboxDocumentation/BlackboxConfiguration#IDontHaveAConfigFileHowDoIGetOne)

---

### Post by bluevoodoo1 on 2006-03-07
[QUOTE=nitefly]found the build-essentials, installed it plus a bunch of other stuff, i managed to compile bb. yaay! now comes the big part, configuring it..
thanks for tip![/QUOTE]


Great! Now the fun part!

[quote=william_nbg]I had the same problem with 'no .rc' file.

Found a good work around on the backbox home page, in their wiki

[http://blackboxwm.sourceforge.net/Bl...HowDoIGe](http://blackboxwm.sourceforge.net/Bl...HowDoIGe) tOne[/quote]

Thanks! I added that to the guide...

Also added... A link to the compilation requirements required for Blackbox (from their wiki)

---

### Post by uzi09 on 2006-03-07
wow, thats one hella nice desktop ^_^

thanks very much for the helpful article,
uzi

---

### Post by R3linquish3r on 2006-03-08
for some reason (i tried both downlaoding from repo's and compiling myself) it wont create a .blackbox folder and i have to make it myself and im not skilled enough to setup the menu file and such that i need. why isnt the folder being made on its own?

---

### Post by bluevoodoo1 on 2006-03-08
[QUOTE=R3linquish3r]for some reason (i tried both downlaoding from repo's and compiling myself) it wont create a .blackbox folder and i have to make it myself and im not skilled enough to setup the menu file and such that i need. why isnt the folder being made on its own?[/QUOTE]


Strange, I don't have an answer for that. Well make a .blackbox folder in your home folder. Inside that you might want to make a backgrounds and styles folder as well. In your .blackbox folder make a new file called menu. Grab my sample menu and paste it in if you like, you can change it to anything you like. Then look in your home folder for the .blackboxrc file and make sure...

session.menuFile:	/home/user-name-goes-here/.blackbox/menu

reads accordingly. If you do not have a .blackboxrc file either read this [link]("http://blackboxwm.sourceforge.net/Bl...HowDoIGe").

You might have to hit "restart" or "reconfigure" from the blackbox menu (it will restart/refresh blackbox). 

If you get the bbconf program it will graphically help you make a menu (you will have to know the commands of the programs you want to open). I hope that helps. Post again if things don't work.

---

### Post by uzi09 on 2006-04-02
[QUOTE=R3linquish3r]for some reason (i tried both downlaoding from repo's and compiling myself) it wont create a .blackbox folder and i have to make it myself and im not skilled enough to setup the menu file and such that i need. why isnt the folder being made on its own?[/QUOTE]

when i loaded up BB on my school computer, i ran into the same situtation - no .blackbox directory. i just did it all manually - not very hard AT ALL! basically, create the directory (duh! =D). the only thing i really had a problem with was the fact that they said (on all these websites) that to modify something, we just need to modify such and such file and "alakazam it works!", but because i didn't know what format the files should be in (much less what things i can use/modify in it) it was a bit of a problem (hopefully BB dev's will do this automatically in future versions).

i just did a quick google search for things like "keys sample file" as well as read up on BB's user documentation ([http://blackboxwm.sourceforge.net/BlackboxDocumentation)](http://blackboxwm.sourceforge.net/BlackboxDocumentation)). the documentation stated that the directory and files may not be there in which case we can just copy the sample files from where the source is located, but the problem with that was BB was preinstalled by school admin and i had no clue where it was ](*,) . luckily, you have voodoo's sample files to go off of, but if you really want, u can always google for sample files (coming from experience, they may require a bit of searching though =\)

(to summarize)
-you can either use voodoo's sample files
-get the sample files from the source
-google it
- (and if u really want, ur more then welcome to e-mail me and i'll e-mail em to u)

good luck,
uzi

---

### Post by louiscyphre on 2006-04-03
Great How To! I'm currently running your configuration!

You can make GDM (and KDM) able to run a script instead of an application just changing the "Type=Application" line in "Type=Xsession" in /usr/share/xsessions/blackbox.desktop.

An example of "blackbox.desktop":
```
[Desktop Entry]
Encoding=UTF-8
Name=Blackbox
Comment=Highly configurable and low resource X11 Window manager
Exec=/usr/bin/blackbox_startup
Terminal=False
TryExec=/usr/bin/blackbox_startup
Icon=blackbox.xpm
Type=Xsession
```

This will execute automatically "/usr/bin/blackbox_startup" when you log in.
Hope this help ;)

---

### Post by McAbre on 2006-04-28
Thanks for a great HOW To. Was a big help. =)

Got a few problems I've been fighting with for a lil while... 

1. when I run Nautilus, it starts gnome, and then I can't get to menus etc. (doesn't load the gnome toolbars and things... so I have to hit ctrl-alt-backspace to get out.)

2. I tried to add the Esetroot -line to my style file, but it did nothing. If I execute the line in terminal, then Eterm works fine, but... that's no fun. ;D

and 3. not really important cause I don't need conky, but when I run it, it resets the menus and I have to edit them back with bbconf. No idea why it does that. 

-M

---

### Post by bluevoodoo1 on 2006-04-28
[QUOTE=McAbre]Thanks for a great HOW To. Was a big help. =)

Got a few problems I've been fighting with for a lil while... 

1. when I run Nautilus, it starts gnome, and then I can't get to menus etc. (doesn't load the gnome toolbars and things... so I have to hit ctrl-alt-backspace to get out.)

2. I tried to add the Esetroot -line to my style file, but it did nothing. If I execute the line in terminal, then Eterm works fine, but... that's no fun. ;D

and 3. not really important cause I don't need conky, but when I run it, it resets the menus and I have to edit them back with bbconf. No idea why it does that. 

-M[/QUOTE]


1. nautilus --no-desktop

2. Are you running Dapper? I upgraded to Dapper and 80% of the time Esetroot would not work with setting my Eterm either, though it did change the background. Does it change the background (wallpaper) too or not?

3, Hmm...  Make sure that in .blackboxrc you have the line that reads...
session.menuFile:	/home/<username>/.blackbox/menu

And if you open /home/<username>/.blackbox/menu you can see your custom menu.

(if it reads /usr/share/blackbox/menu, then conky might be trying to fall back on the default location for the menu rather than the one you've done).

---

### Post by bluevoodoo1 on 2006-04-28
Fixed a few [more] typos.

---

### Post by william_nbg on 2006-04-28
[QUOTE=McAbre]Thanks for a great HOW To. Was a big help. =)

Got a few problems I've been fighting with for a lil while... 

1. when I run Nautilus, it starts gnome, and then I can't get to menus etc. (doesn't load the gnome toolbars and things... so I have to hit ctrl-alt-backspace to get out.)

2. I tried to add the Esetroot -line to my style file, but it did nothing. If I execute the line in terminal, then Eterm works fine, but... that's no fun. ;D

and 3. not really important cause I don't need conky, but when I run it, it resets the menus and I have to edit them back with bbconf. No idea why it does that. 

-M[/QUOTE]

Question 1. When you run Nautilus from your BB menu you have to run it - nautilus --no-desktop  - otherwise it will change to the Gnome desktop.

Question 2. that happens even after you restart? Where is your rc file?

Question 3. not sure, I've never messed with Conky.

---

### Post by McAbre on 2006-04-28
Thanks a lot to both. 

Got Nautilus and Conky running in no time with your help, and I didn't have "rootCommand:" in front of the Esetroot -line in my style file. So got that working too. =)

Things are looking mighty fine now. :mrgreen: 

-M

---

### Post by zedwards on 2006-06-08
Ok, this has been driving me crazy. I have always used blackbox. Since trying Ubuntu since 4.10 to 6.06 i have had trouble getting blackbox to be able to read the rc file. I have one in my home dir but it wont read it, it also wont display a menu. what gives? is it reading it from somewhere else that doesnt have permissions?

---

### Post by Maelgwyn on 2006-06-08
I just tried this out in Dapper, and it was fine up until I sudo ./configure'd. The error message was this:

```

checking for GNU libiconv... no, assuming POSIX compliance
checking for setlocale... yes
checking for nl_langinfo... yes
checking for t_open in -lnsl... no
checking for socket in -lsocket... no
checking for X... no
configure: error: Blackbox requires the X Window System libraries and headers.

```

so I'm going to continue and go through the install and update bb when I can :)

---

### Post by bluevoodoo1 on 2006-06-16
[QUOTE=zedwards]Ok, this has been driving me crazy. I have always used blackbox. Since trying Ubuntu since 4.10 to 6.06 i have had trouble getting blackbox to be able to read the rc file. I have one in my home dir but it wont read it, it also wont display a menu. what gives? is it reading it from somewhere else that doesnt have permissions?[/QUOTE]

Has it been named correctly? .blackboxrc ? Perhaps this might help...
[http://blackboxwm.sourceforge.net/BlackboxDocumentation/BlackboxConfiguration#IDontHaveAConfigFileHowDoIGetOne](http://blackboxwm.sourceforge.net/BlackboxDocumentation/BlackboxConfiguration#IDontHaveAConfigFileHowDoIGetOne)


[QUOTE=Maelgwyn]I just tried this out in Dapper, and it was fine up until I sudo ./configure'd. The error message was this:

```

checking for GNU libiconv... no, assuming POSIX compliance
checking for setlocale... yes
checking for nl_langinfo... yes
checking for t_open in -lnsl... no
checking for socket in -lsocket... no
checking for X... no
configure: error: Blackbox requires the X Window System libraries and headers.

```

so I'm going to continue and go through the install and update bb when I can :)[/QUOTE]

The xserver-xorg-core package might help you out, though I can't remember for sure if it has everything needed, but it's a start. Without x server, all you have is the console. (white text/black background)

---

### Post by yteh on 2006-06-16
bluevoodoo1...... just wanted to say THANKS!!! I'm now happily using Blackbox on my desktop and will probably get it set up on my laptop very soon. I love it.

---

### Post by frozenflame on 2006-06-18
Hey, awesome How-To, I likey. :razz: 
Anywho,  I got Mr. Blackbox running, the only problem I'm having is configuring the menu, I created a menu file with ur example since I had none, and modify it just to run the apps I know I have installed, and I went to the .blackboxrc file to change the path of the menu, but it is still pulling it from somewhere that I don't know. 
Right now the menu only shows xterm, restart, and exit.
I remember that when I opened the .blackboxrc file the menu path was /etc/X11/blackbox/blackbox-menu, I went to that path and I did a vi blackbox-menu and it told me that the file didn't exist:-( , did ls -a, and nothing showed up, very bizarre I must say.:confused: 

Also I tried compiling BB and it asked me for iconv(3), i went to gnu and installed iconv and it still asked for it when trying to complie BB, i couldn't find any other kind of iconv package, any ideas?

---

### Post by bluevoodoo1 on 2006-06-18
[QUOTE=frozenflame]Hey, awesome How-To, I likey. :razz: 
Anywho,  I got Mr. Blackbox running, the only problem I'm having is configuring the menu, I created a menu file with ur example since I had none, and modify it just to run the apps I know I have installed, and I went to the .blackboxrc file to change the path of the menu, but it is still pulling it from somewhere that I don't know. 
Right now the menu only shows xterm, restart, and exit.
I remember that when I opened the .blackboxrc file the menu path was /etc/X11/blackbox/blackbox-menu, I went to that path and I did a vi blackbox-menu and it told me that the file didn't exist:-( , did ls -a, and nothing showed up, very bizarre I must say.:confused: [/quote]

Try looking in... /usr/share/blackbox/menu that's where mine was initially installed, and where I moved mine from.

from the terminal try:

```
locate blackbox
``` that will pullup anything contatining blackbox. 


> Also I tried compiling BB and it asked me for iconv(3), i went to gnu and installed iconv and it still asked for it when trying to complie BB, i couldn't find any other kind of iconv package, any ideas?

Strange, the only package containing "iconv" that I have installed is "libtext-iconv-perl." Don't actually think it's related to anything Blackbox reltaed.

---

### Post by ~LoKe on 2006-06-18
After ./configure, I get the "blackbox version 0.70.1 configured successfully." notice, with no errors.  Them **make** and it goes through all fine.  sudo checkinstall goes through everything, asks me a few things.  Then it comes to the cd .blackbox ... ```
x04d@127:~/blackbox-0.70.1$ cd .blackbox
bash: cd: .blackbox: No such file or directory
```

Am I doing something wrong?

EDIT: I have XGL/Compiz if that changes anything.  If I need to remove it, just let me know and let me know how and I'll do it. =]

---

### Post by bluevoodoo1 on 2006-06-18
[QUOTE=~LoKe]After ./configure, I get the "blackbox version 0.70.1 configured successfully." notice, with no errors.  Them **make** and it goes through all fine.  sudo checkinstall goes through everything, asks me a few things.  Then it comes to the cd .blackbox ... ```
x04d@127:~/blackbox-0.70.1$ cd .blackbox
bash: cd: .blackbox: No such file or directory
```

Am I doing something wrong?

EDIT: I have XGL/Compiz if that changes anything.  If I need to remove it, just let me know and let me know how and I'll do it. =][/QUOTE]


```
cd
```

Try that, so you will be back at something like 
```
bluevoodoo1@ubuntu:~$ 
```
then do ```
cd .blackbox
```

Sorry, it wasn't that clear. I fixed it now. Thanks.

---

### Post by ~LoKe on 2006-06-18
Ah, forgive my noobness. =]

```
x04d@127:~/.blackbox$ ls
blackbox
x04d@127:~/.blackbox$
```

There's a blackbox directory within .blackbox.  Is that a problem?

---

### Post by bluevoodoo1 on 2006-06-18
[QUOTE=~LoKe]Ah, forgive my noobness. =]

```
x04d@127:~/.blackbox$ ls
blackbox
x04d@127:~/.blackbox$
```

There's a blackbox directory within .blackbox.  Is that a problem?[/QUOTE]

Hmm, don't know why it's there. Just ignore it.

---

### Post by ~LoKe on 2006-06-19
Yet another problem.  If I'm doing something obviously wrong, don't hesitate to tell me. =]

```
x04d@127:~$ sudo mv /usr/local/share/blackbox/menu ~/.blackbox/menu
x04d@127:~$ sudo mv /usr/local/share/blackbox/styles/ ~/.blackbox/styles/
mv: cannot overwrite directory `/home/x04d/.blackbox/styles/styles'
x04d@127:~$ cp .blackboxrc ~/.blackboxrc_backup
cp: cannot stat `.blackboxrc': No such file or directory
```

---

### Post by bluevoodoo1 on 2006-06-19
[QUOTE=~LoKe]Yet another problem.  If I'm doing something obviously wrong, don't hesitate to tell me. =]

```
x04d@127:~$ sudo mv /usr/local/share/blackbox/menu ~/.blackbox/menu
x04d@127:~$ sudo mv /usr/local/share/blackbox/styles/ ~/.blackbox/styles/
mv: cannot overwrite directory `/home/x04d/.blackbox/styles/styles'
```
[/quote]

That is ok. That step was only there to make sure you have a styles folder. 

> ```
x04d@127:~$ cp .blackboxrc ~/.blackboxrc_backup
cp: cannot stat `.blackboxrc': No such file or directory
```

For that... see this:
"No .rc file... william_nbg points out this link, if for some reason, you do not have a .blackboxrc file and need one![http://blackboxwm.sourceforge.net/BlackboxDocumentation/BlackboxConfiguration#IDontHaveAConfigFileHowDoIGetOne](http://blackboxwm.sourceforge.net/BlackboxDocumentation/BlackboxConfiguration#IDontHaveAConfigFileHowDoIGetOne) "

you'll want to copy the file to a text document and save it as .blackboxrc

---

### Post by ~LoKe on 2006-06-19
Nice, it works!

Thanks. =]

---

### Post by bluevoodoo1 on 2006-06-19
[QUOTE=~LoKe]Thanks. =]

Please excuse me again, but I'm an Ubuntu/Linux newb.  Where exactly is the .blackbox folder?  Heh.[/QUOTE]


no problemo. 

the .blackbox folder is a hidden folder in your home directory which contains several components to make blackbox work. In order to gain easy access to things like styles, the menu, and backgrounds we put them in the .blackbox folder.

---

### Post by bluevoodoo1 on 2006-06-19
[QUOTE=~LoKe]Nice, it works!

Thanks. =][/QUOTE]

:)

---

### Post by DewBoy3d on 2006-06-21
[QUOTE=bluevoodoo1]
1.
```

sudo apt-get install blackbox blackbox-themes bbconf

```

Or use Synaptic and give it a search, they should be all there.
[/QUOTE]

       *On a clean install of Ubuntu (Dapper), these packages are NOT available through apt. Which sources should I add to find them?*

EDIT: Found them. I needed to edit sources.list to uncomment universe and multiverse and then all is well..

---

### Post by bluevoodoo1 on 2006-06-21
[QUOTE=DewBoy3d]On a clean install of Ubuntu (Dapper), these packages are NOT available through apt. Which sources should I add to find them?[/QUOTE]

Ah yes, they're in the Universe repositories. See here for how to enable them...
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by DewBoy3d on 2006-06-21
[QUOTE=bluevoodoo1]Ah yes, they're in the Universe repositories. See here for how to enable them...
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)[/QUOTE]

Thanks. I got it figured out with some help from IRC and [this]("http://ubuntuforums.org/showthread.php?t=185758") post on the forums.

One other thing i ran into was with the bsetbg command. It was unable to change the background. it produced a list of things it tried such as esetroot. I simply installed eterm to fix that problem.

---

### Post by bluevoodoo1 on 2006-06-21
[QUOTE=DewBoy3d]One other thing i ran into was with the bsetbg command. It was unable to change the background. it produced a list of things it tried such as esetroot. I simply installed eterm to fix that problem.[/QUOTE]

Yes you are correct. I removed references to bsetroot (bsetbg) and changed it to use Esetroot by installing Eterm. 


Sidenote: Revamped guide and I tested it on a fresh Dapper install. It *should* work fine.

---

### Post by Poka64 on 2006-07-15
Is there a way to get a quit menu like the one in gnome/metacity (logoff/shutdown etc.) ?

---

### Post by bluevoodoo1 on 2006-07-15
> **Poka64 said:**
> Is there a way to get a quit menu like the one in gnome/metacity (logoff/shutdown etc.) ?

Hmm... not that I know of.... unless someone else knows?

---

### Post by Zodiac on 2006-08-02
Is there a way to do a clean Blackbox install?

---

### Post by bluevoodoo1 on 2006-08-02
> **Zodiac said:**
> Is there a way to do a clean Blackbox install?

What do you mean clean install? Do you have it already and want to remove it completely?

---

### Post by Zodiac on 2006-08-04
I was thinking more like, how there is Xubuntu and such... is there a way to install Blackbox right from the get go?

---

### Post by bluevoodoo1 on 2006-08-04
> **Zodiac said:**
> I was thinking more like, how there is Xubuntu and such... is there a way to install Blackbox right from the get go?

Just enable Universe and sudo apt-get install blackbox that's the shortest way of installing it I know. 

I was working on an interactive blackbox install script, something like automatix, that will help with the install, but above is pretty easy.

---

### Post by SirOracle on 2006-09-30
Great howto, works like a charm on my Ubuntu!
But do you install something to get keyboard-shortcuts, like ALT-TAB, ALT-F4 and so on? After some googling I found out that you need something called bbkeys to get that, and I can easly install it with "sudo apt-get install bbkeys", but when I try to start it, I get an error-message:
bbkeys: ScreenHandler: Found compatible window manager: [Blackbox] for screen: [0].
bbkeys: ScreenHandler: Supported atoms: [45].
*** glibc detected *** free(): invalid pointer: 0x0808b388 ***
Aborted

I use Ubuntu in VMware, and I have tried again on a fresh install, but the same error. Has anyone got bbkeys to work correctly on their Blackbox? Or do you do anything else to get keyboard-shortcuts?

---

### Post by hulet on 2006-10-02
> **SirOracle said:**
> Great howto, works like a charm on my Ubuntu!
But do you install something to get keyboard-shortcuts, like ALT-TAB, ALT-F4 and so on? After some googling I found out that you need something called bbkeys to get that, and I can easly install it with "sudo apt-get install bbkeys", but when I try to start it, I get an error-message:
bbkeys: ScreenHandler: Found compatible window manager: [Blackbox] for screen: [0].
bbkeys: ScreenHandler: Supported atoms: [45].
*** glibc detected *** free(): invalid pointer: 0x0808b388 ***
Aborted

I use Ubuntu in VMware, and I have tried again on a fresh install, but the same error. Has anyone got bbkeys to work correctly on their Blackbox? Or do you do anything else to get keyboard-shortcuts?

Or alternatively you can use the bbconf to set keyboard-shortcuts:
```
 sudo apt-get install bbconf
```
Then open bbconf and click on the "Key Bindings" on the left hand side frame.

---

### Post by SirOracle on 2006-10-03
Thanks for the tips, but it didnt help. Are you sure bbkeys is not needed if you use bbconf? I see bbconf write the keboard-maps to a file called .bbkeysrc, so to me it looks as it just configures bbkeys. But since I can't get bbkeys to work...

Do you have Ubuntu with Blackbox and keyboard-shortcuts? You didnt have to do anything special to make it work? I have tried this on three different computers now, same problem. Im using Dapper Drake.

---

### Post by hulet on 2006-10-03
> **SirOracle said:**
> Thanks for the tips, but it didnt help. Are you sure bbkeys is not needed if you use bbconf? I see bbconf write the keboard-maps to a file called .bbkeysrc, so to me it looks as it just configures bbkeys. But since I can't get bbkeys to work...

Do you have Ubuntu with Blackbox and keyboard-shortcuts? You didnt have to do anything special to make it work? I have tried this on three different computers now, same problem. Im using Dapper Drake.

Yes, you are correct SirOracle. bbkeys is needed for keyboard-shortcuts to work. Obviously, I had to install bbkeys from the source since the package from apt-get is somehow broken (I got the glibc error you were getting when you tried to run it. To install from the source here is what I have done 

1)I first uninstalled the old bbkeys:
```
sudo apt-get remove bbkeys
```
2)Then, I installed the chekinstall package necessary to install compiled packages:
```
 sudo apt-get install checkinstall
```
3)Next, I installed the libbt development library needed to compile bbkeys
```
 sudo apt-get install libbt-dev
```
4)Since I didn't have the g++ compiler on my system, I installed it using the build-essential package
```
sudo apt-get install build-essential
```
5)Then I downloaded and untarred the bbkey source package from sourceforge
```
wget http://jaist.dl.sourceforge.net/sourceforge/bbkeys/bbkeys-0.9.0.tar.gz &
tar xvzf ./bbkeys-0.9.0.tar.gz &
cd bbkeys-0.9.0/

```
6)Finally configure, make, checkinstall and run bbkey
```
./configure &
make &
sudo checkinstall

```

One thing I noticed is that the .bbkeysrc created by bbconf doesn't work so I have to create my own - which I basically copied from the example in the man page for bbkeysrc.

---

### Post by SirOracle on 2006-10-06
I did step 1 to 5, but at step 6 it stopped when I tried ./configure.
configure ended with the message:
checking for XMissingExtension in -lXext... no
configure: error: XMissingExtension not found in -lXext

And if I try to run make it says:
make: *** No targets specified and no makefile found.  Stop.

So I guess its not one of those error-messages you can ignore :(

Please have a solution, I feel so close now.

---

### Post by hulet on 2006-10-06
> **SirOracle said:**
> I did step 1 to 5, but at step 6 it stopped when I tried ./configure.
configure ended with the message:
checking for XMissingExtension in -lXext... no
configure: error: XMissingExtension not found in -lXext

And if I try to run make it says:
make: *** No targets specified and no makefile found.  Stop.

So I guess its not one of those error-messages you can ignore :(

Please have a solution, I feel so close now.

Ah, do you have the libxext6 package installed? Check by typing this:
```
 sudo apt-cache showpkg libxext6
```
If not, then that could be the problem, so install it and the libext-dev package (just to be safe) by executing:
```
sudo apt-get install libxext6 libxext-dev
```
Then run the ./configure and then make commands.

Hope that solves it. :)

---

### Post by hulet on 2006-10-06
Have anyone installed adesklets on blackbox? They are fantabulous. :)

---

### Post by SirOracle on 2006-10-07
Thank you hulet, you are genious!!
I already had libxext6, but it worked after I installed libxext-dev.

---

### Post by q335r49 on 2006-11-27
Anyone here get the pipe menus to work?  It seems almost trivial but i can't find any way to run it.  [include] |(~/somescript.sh)?  [include] (|~/somescript.sh)?

---

### Post by q335r49 on 2006-11-27
Ok ... ok... forgot to add the #!/bin/bash to the beginning of the script.

Second question:
Say I want to use the menu to display a clock.  So

echo "[nop] ($(date))"

will work.  But it won't update, unless the timestamp of the original file is updated.  So every time I open the menu, it's the same time, unless I do:

touch ~/.blackbox/myScript

Outside of blackbox.  The only solution is that I've added an "update" command which touches myScript.  And then I open the menu again and the clock is right.  But this is a hassle.

Is there any way to have blackbox update the menu on every evocation, perhaps to do something like

echo "[nop] ($(date))"
touch ~/.blackbox/myScript &

(which doesn't work.)?

---

### Post by q335r49 on 2006-11-28
Aaa, problem solved, via screen.  I don't know how obvious this is, but for those who are interested in having a genuine clock on their menu, try using this script:

menu2: (~/.blackbox/menu2)
#!/bin/bash

AV=$(acpi)
AV=${AV:16:13}
echo "[nop] ($(date))"
echo "[nop] ($AV)"

screen -d -m ~/.blackbox/menu3

menu3:
sleep 2s
STAMP=2007111111$(date +%S).11
touch -t $STAMP ~/.blackbox/menu2

and in the menu file:
[include] (|~/.blackbox/menu)


So the main thing I learned over the course of several hours is the ability to run an application in the background via "screen -d -m", which in this case calls menu3 to change to timestamp of menu2 so that the menu will update every time.

Why the hell wouldn't any menu with a piped menu update every time anyways, or at least include the option?  Is there something I missed?

I think this pretty much eliminates the need for conky, or in fact the vast majority of slit or tab applications, as its possible to put all the information you want in the main menu or a submenu.
8-)


Other things that can be done?
A volume display, as well as a volume adjuster in menu?
A wifi display?
A cpu load display?
A task switcher?
A display of the currently active workspace?

---

### Post by fj34r on 2007-05-17
Trying to install bbconf, but aptitude can never find it.  Has it been discontinued or do i need to enable another repository?

---

### Post by tomski on 2007-05-25
i have tried blackbox but i prefer fulxbox myself but i must say
 where did you get the wallpaper/background image that i do like

---

### Post by bensode on 2007-06-08
This thread is a little dated so I'm hoping it's still watched ;)  BB installed, menus customized and overall wholesome goodness!  Only problem I have is when exiting / logging out, I get a black screen with no mouse.  Hard resetting X (ctrl-alt-backspace) flickers the screen once, then goes to the black screen.  I can get to my alt console no problems but even restarting or killing GDM gives me the same blank screen.  If I reboot, GDM comes back fine and I can select BB session but I can't logout I always have to shutdown or reboot.  Any clues?  I copied / pasted everything from the howto and only changed my home directory for the path.

Bensode

Edit: This also happens with any X session manager I use ... Gnome and BB are both broken.

Edit: Removed GDM (which also removed ubuntu-desktop package??) to boot console without gui and can safely startx and logout back to the console so I am willing to bet something was broken in GDM.  Going to try and reinstall GDM and see if that corrects the problem that way although I don't mind manually starting the gui since it's not that often that I need to logout/login I usually just lock screen ...

Edit: Removing, purging and reinstalling brings it back so there is definately a problem with GDM under Fiesty ... I'll goof around with it a little more and probably start a new thread once I find the solutions or get completely frustrated with it.

---

### Post by wounded on 2007-09-05
Did a fresh install of Kubuntu then installed Blackbox and everything's going pretty good except I cannot get bbpager and bbdock to show up in the slit. bbpager has no config options (Except image links for the apps) and even though I set Withdraw to True in the bbdock config (Which says will put it inside the slit) both apps load up in somewhat random locations along the right side of the screen and not in the slit. Any idea how to fix that? bbpager isn't required but I would love to get bbdock working at least.

---

### Post by Meilin Mistress on 2007-09-14
Very nice How To! I know it's an older thread, but I found this one the most helpful by far! Just got blackbox working for my dubuntu and it works great! Now I'll just go configure it a bit more. Thanks again!
[http://ubuntuforums.org/images/smilies/icon_smile.gifhttp://ubuntuforuhttp://ubuntuforums.org/images/smilies/icon_smile.gifms.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gifhttp://ubuntuforuhttp://ubuntuforums.org/images/smilies/icon_smile.gifms.org/images/smilies/icon_smile.gif)

---

### Post by bluevoodoo1 on 2007-09-15
> **Meilin Mistress said:**
> Very nice How To! I know it's an older thread, but I found this one the most helpful by far! Just got blackbox working for my dubuntu and it works great! Now I'll just go configure it a bit more. Thanks again!
[http://ubuntuforums.org/images/smilies/icon_smile.gifhttp://ubuntuforuhttp://ubuntuforums.org/images/smilies/icon_smile.gifms.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gifhttp://ubuntuforuhttp://ubuntuforums.org/images/smilies/icon_smile.gifms.org/images/smilies/icon_smile.gif)

yeah... I haven't used BB in ages myself! :)

---

### Post by andrew.46 on 2007-09-20
Hi,

> **bluevoodoo1 said:**
> yeah... I haven't used BB in ages myself! :)

Which begs the question (I saw it asked previously) where did you get that amazing background image??

                     Andrew

---

### Post by AustinMarton on 2007-11-02
Hi, the last part with the terminal was just what I was looking for, but I can't get my Eterm to be transparent... it still always shows a random background, any ideas how to fix that?

---

### Post by bluevoodoo1 on 2007-11-03
> **andrew.46 said:**
> Hi,



Which begs the question (I saw it asked previously) where did you get that amazing background image??

                     Andrew

Hmm... I don't remember, could have been deviantart...

here it is...

---

### Post by DoXiD on 2008-04-27
What you should be aware of (couldn't find it here in the thread, if i missed it i'm sorry), is that the /usr/bin/local/blackbox path actually should be /usr/bin/blackbox in:

/home/username/.bbstartup.sh

Otherwise you will get a error message when trying to run the blackbox session saying that blackbox dosn't excist : )



*This might count as a bump but seeing that this was the tophit on google and it's outdated i thought it would actually be ok to update the thread instead of posting a new one. Great how-to btw, and it still works nicely*

---

### Post by oswaldkelso on 2008-11-16
## Someone was wanting to setup bbpager here is the file I use found it someware on the web but it has nice comments. This is **the** Blackbox setup thread. Thanks.
#######################start#########################
!**********************************************************************
!** bbpager.rc: bbpager configuration file                           **
!**                                                                  **
!** This is the global bbpager configuration file. To make           **
!** user-specific modifications, you should copy this file to your   **
!** home directory in $HOME/.bbtools/bbpager.rc and edit that file.  **
!**                                                                  **
!** All options have been commented out in this file. To change an   **
!** option from its default setting, uncomment it and modify the     **
!** setting.                                                         **
!**********************************************************************


!**********************************************************************
!** behavior section
!**********************************************************************

!** Indicate whether the bbpager window is withdrawn. If using with
!**   blackbox, "withdrawn" means it will be placed in the slit.
bbpager.withdrawn:     false

!** Set the position of the bbpager window.
!** Relevant only when bbpager.withdrawn is False.
bbpager.position:               +570-40

!** Set the width and height of bbpager's model of the desktop windows.
bbpager.desktop.width:          54
bbpager.desktop.height:         36

!** Set the desktop orientation.
!** Possible values: horizontal, vertical
!bbpager.desktop.orientation:	horizontal

!** Define the maximum number of columns. The number of rows will
!**   increase as necessary to accommodate additional desktops.
!** Relevant only when bbpager.desktop.orientation is horizontal.
!bbpager.desktop.columns:               1

!** Define the maximum number of rows. The number of columns will
!**   increase as necessary to accommodate additional desktops.
!** Relevant only when bbpager.desktop.orientation is vertical.
!bbpager.desktop.rows:                  1

!** Set the window focus style. This is the method to distinguish
!**   the focused window from unfocused windows. When set to none,
!**   a window will appear the same whether or not it is focused.
!**   When set to border, a window's border may change when it is
!**   focused, but its interior appearance will not. When set to
!**   texture, a window's border and interior appearance may
!**   change when it is focused.
!** Possible values: none, border, texture
bbpager.window.focusStyle:      texture

!** Set the desktop focus style. This is the method to distinguish
!**   the focused desktop from the other desktops. When set to none,
!**   a desktop will appear the same whether or not it is focused.
!**   When set to border, a desktop's border may change when it is
!**   focused, but its interior appearance will not. When set to
!**   texture, a desktop's border and interior appearance may
!**   change when it is focused.
!** Possible values: none, border, texture
bbpager.desktop.focusStyle:	 border

!** Set the mouse button used to perform various actions.
!** Typically, button 1 is the left mouse button, 2 middle, 3 right,
!**   etc., though this may be changed in the user's X configuration.
!** A value of 0 may be assigned to bbpager.windowFocusButton or
!**   bbpager.windowRaiseButton, meaning that no button will perform
!**   these actions.
!** Multiple functions may be assigned to a single mouse button. For
!**   example, raise and focus might be good candidates to assign to
!**   the same button.
bbpager.desktopChangeButton:	1
bbpager.windowMoveButton:      1
bbpager.windowFocusButton:	1
bbpager.windowRaiseButton:	1


!**********************************************************************
!** style section
!**
!** See the blackbox documentation for a description of the style
!** syntax.
!**********************************************************************

!** Set the margin between the edge of the tool and the desktops.
bbpager.margin:             1

!** Set the margin between the desktops.
bbpager.desktop.margin:	 1

!** Define the frame style.
!** bbpager will attempt to copy these options from the blackbox
!**   toolbar style.
bbpager.frame.appearance: Raised Gradient Vertical
bbpager.frame.color1:     white
bbpager.frame.color2:     white

!** Define the desktop window style. This style is used to draw
!**   all desktops when bbpager.desktop.focusStyle is none or border,
!**   and it is used to draw the unfocused desktops when
!**   bbpager.desktop.focusStyle is texture.
!** bbpager will attempt to copy these options from the blackbox
!**   toolbar.label style.
bbpager.desktop.appearance: Sunken Gradient Vertical
bbpager.desktop.color1:     lightblue
bbpager.desktop.color2:     darkblue

!** Define the focused desktop window style. This style is used
!**   to draw the focused desktop when bbpager.desktop.focusStyle
!**   is texture.
bbpager.desktop.focus.appearance: Sunken Gradient Vertical
bbpager.desktop.focus.color1:     yellow
bbpager.desktop.focus.color2:     yellow

!** Define the border for the focused desktop window.
!** Set borderWidth to 0 for no border.
!** Not relevant when bbpager.desktop.focusStyle is none.
bbpager.active.desktop.borderColor:	white
bbpager.active.desktop.borderWidth:	1

!** Define the border for unfocused desktop windows.
!** Set borderWidth to 0 for no border.
bbpager.inactive.desktop.borderColor:	black
bbpager.inactive.desktop.borderWidth:	1

!** Define the window style. This style is used to draw all
!**   windows when bbpager.window.focusStyle is none or border,
!**   and it is used to draw the unfocused windows when
!**   bbpager.window.focusStyle is texture.
!** bbpager will attempt to copy these options from the blackbox
!**   window.label.unfocus style.
bbpager.window.appearance: Raised Gradient Diagonal
bbpager.window.color1:     white
bbpager.window.color2:     white

!** Define the focused window style. This style is used to draw
!**   the focused window when bbpager.window.focusStyle is
!**   texture.
!** bbpager will attempt to copy these options from the blackbox
!**   window.label.focus style.
bbpager.window.focus.appearance: Raised Gradient Vertical
bbpager.window.focus.color1:     orange
bbpager.window.focus.color2:     yellow

!** Define the border for the focused window.
!** Set borderWidth to 0 for no border.
!** Not relevant when bbpager.window.focusStyle is none.
bbpager.active.window.borderColor:	black
bbpager.active.window.borderWidth:	1

!** Define the border for unfocused windows.
!** Set borderWidth to 0 for no border.
!bbpager.inactive.window.borderColor:	black
!bbpager.inactive.window.borderWidth:	1

######################end######################

A picture of it. [http://img352.imageshack.us/my.php?image=200811131730481024x600sjv7.png](http://img352.imageshack.us/my.php?image=200811131730481024x600sjv7.png)

---

### Post by Clade on 2009-06-20
Such an excellent guide, thank you for getting me on my feet with Blackbox; this is the only GUI for me!

One thing to note about 9.04 and the startup script:

Xwindows gave me some difficulty when attempting to run "exec /usr/local/bin/blackbox" in my ~/.bbstartup.sh script. However, when I edited the /usr/share/xsessions/blackbox.desktop file, the executable path simply listed "blackbox," and nothing else. I was unable to find a /usr/local/bin/blackbox directory in general upon further review.

I was able to alleviate this by simply telling my startup script to "exec blackbox."

I don't know if this is common knowledge at this rate or what, but hopefully this will help anyone with a simliar issue I had when attempting to use bluevoodoo1's amazing guide :-)

Cheers,
-Mike

---

### Post by bluevoodoo1 on 2010-11-01
Nearly four years after creating this tutorial, it still mostly works (just tried it successfully with 10.4)!

---

### Post by manzdagratiano on 2010-11-13
Thank you for a most excellent guide! I like Blackbox a lot, but I have tried setting the wallpaper through altering the rootCommand to no avail so far - running Maverick here. I changed the rootCommand in the style file - no effect; I then changed it in .blackboxrc, and still no effect. I do know that the .blackboxrc file is being read since I am able to set whatever menu options I want through there, but it just seems like the Esetroot command is not there at all! Eterm is certainly installed, and my rootCommand in .blackboxrc looks like:

rootCommand: Esetroot -scale /path/to/wallpaper

I would like to keep the rootCommand in the blackboxrc file as opposed to changing it in each style file - that seems like no fun. When I use the command manually from a terminal, the wallpaper is changed instantly, so it certainly works, just not during startup. Any ideas? This happens both in Ubuntu and Arch Linux - am I missing something? I have the usual Ubuntu Desktop Edition gnome as well and my login manager is gdm, but I think that should not be cause for trouble.

I must comment here that I want to keep using blackbox, for nostalgic reasons - I did install fluxbox once but it seemed no different except for a few additional features, so I chose to stick with the real thing. Aside from this I would only use ratpoison when not in gnome. Running a low memory footprint is not exactly my criterion, in this day and age of humongous RAMs and CPU power, but it is the elegance of these unique approaches that drives me.

---

### Post by manzdagratiano on 2010-11-18
I believe I lied a little - apparently the Esetroot Command in the the blackboxrc file does have some effect - the effect is just to keep the same background as the login screen in gdm. If I remove the rootCommand from the file, since I have set my default style to "Green", I just get a solid green background. So I guess I am bewildered as to what is happening.

---

### Post by manzdagratiano on 2010-12-01
Okay got it! The command was correct - I was using:
```

rootCommand: Esetroot -scale <path/to/image>

```in my .blackboxrc, and for some reason blackbox did not wish to locate the image file, which was in a directory named 'GNU\Linux' on another partition; as soon as I copied the image file over and put it in ~/.blackbox/backgrounds and changed the path in the Esetroot command, the wallpaper is thrown as desired! I believe even though the folder name 'GNU\Linux' is legal - it exists for one and it is allowed to be transferred over rsync and what not else, it is somehow treated as illegal - for instance, when I try a tab completion in the terminal, say, to copy a file from this folder, tab completion does not work for anything inside this folder, whereas `ls' shows the contents just fine. If I change the name of the folder to say 'GNU', everything is good and normal. Ratpoison can find the file just fine in that folder with the original name. Bewildering! If anybody would be able to throw some light on this, it would be much appreciated!

---

