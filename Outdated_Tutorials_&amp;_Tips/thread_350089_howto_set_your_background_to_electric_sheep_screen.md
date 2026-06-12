---
title: "howto set your background to electric sheep screensaver"
date: 2007-01-31
forum: Outdated Tutorials &amp; Tips
---

### Post by Triorph on 2007-01-31
Xwinwrap is a great tool, designed for use with the beryl window management system for making movies run in mplayer or screensavers from xscreensaver run as your background.

electricsheep is a screensaver which creates and shares different patterns via bittorrent, some of these patterns look very nice and some people want to be able to use them with xwinwrap's screensaver setting.

I am basing my work off of this thread: [(xgl desktop screensaver script)]("http://ubuntuforums.org/showthread.php?t=198968")

Currently this has been tested on my i386 ubuntu edgy eft system, using an nvidia graphics card, aiglx and beryl. I don't see any reason why this shouldn't work on any other of the architectures though. I will not handle support for getting your beryl working, I will assume you have already got it working on your own. This method will work by changing electricsheep so it uses the mplayer engine to play its files.

I'd suggest you take a look at the above link first, however it is not necessary.
First you will need to add the multiverse ubuntu repository to install mplayer.

```
 sudo gedit /etc/apt/sources.list 
```

and then add the lines

```
 deb http://au.archive.ubuntu.com/ubuntu/ edgy multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy multiverse 
```

 


Second you will need to install xwinwrap, mplayer and electricsheep, so

```
sudo apt-get install  electricsheep mplayer 
wget http://3v1n0.tuxfamily.org/pool/edgy/beryl-svn/xwinwrap_0.1+cvs20060209_i386.deb
sudo dpkg -i xwinwrap_0.1+cvs20060209_i386.deb 
```

after doing so you should be able to run electricsheep in a window, using the mplayer engine

Just a note, the electricsheep program requires mpg files to play, so you will have to let it download some via bittorrent or download some manually to your cache directory (~/.sheep/), a tutorial to do this manually can be found [here]("http://electricsheep.wikispaces.com/Downloading+Manually")

```
 electricsheep --mplayer 1 
```

once you have electricsheep working, and if xwinwrap works as from the tutorial above, you should just be able to run 


```
 xwinwrap -ni -o 0.3 -fs -s -st -sp -b -nf -- /usr/bin/electricsheep --mplayer 1 -window-id WID & 
```

and to close 

```
 killall electricsheep 
```

The following script is based on the script in the link at the top of this tutorial.

I'm going to call the script xwinsheep, so we will first

```
 sudo gedit /usr/bin/xwinsheep 
```

then fill this into the file and save

```
 #!/bin/bash

# 
# This script runs the electric sheep screensaver on your desktop,
# and drops the name of the screensaver in a marker file.
# When run a second time, it will kill the screensaver.
# Requires xwinwrap to be installed.
# Usage: xwinsheep <OPACITY> <NICENESS> 
# e.g "xwinsheep 0.3 10" will run it at 0.3 opacity
# with a niceness value of 10. Just running "xwinsheep" will
# run it at 1.0 opacity and 19 niceness.


# dir to write marker file to
DIR=~/

#Niceness to run screen saver at. The lower this value, the higher
#priority the screensaver will be. The higher the value, the jerkier
#the screensaver will be, and the less it will intefere with your
#work
NICENESS=$2
if [ -z "$2" ]
then
  NICENESS=19
fi

 

OPACITY=$1
if [ -z $1 ]
then
  OPACITY=1.0
fi

  

if [ -e $DIR.flipflopmarker2 ]
then
	#shows that electric sheep is running via this script
	#kill it, remove the marker file
	killall electricsheep 
	rm $DIR.flipflopmarker2
	exit
fi
	#start the screensaver, write the name of it to a file
	nice -n $NICENESS xwinwrap -ni  -o $OPACITY -fs -s -st -sp -b -nf -- /usr/bin/electricsheep --mplayer 1  -window-id WID &
	touch $DIR.flipflopmarker2

exit

```

then just make the script executable

```
 chmod 755 /usr/bin/xwinsheep 
```

I hope this helps.

---

### Post by pay on 2007-01-31
A screenshot would be nice:)

---

### Post by Triorph on 2007-01-31
> **pay said:**
> A screenshot would be nice:)

here goes

---

### Post by pay on 2007-01-31
That looks pretty cool. I'll try this tomorrow morning:)

---

### Post by stalefries on 2007-01-31
Have you guys found a way to run electricsheep with gnome-screensaver? It doesn't seem to work for me. :(

---

### Post by groggyboy on 2007-01-31
does the xwinrap plugin require the SVN beryl, or will beryl from the regular repo work?

---

### Post by Triorph on 2007-01-31
I haven't found anyway to get electric sheep to work with gnome-screensaver, it does however have support with xscreensaver. 

I was using the beryl-svn repos originally but there were some stability issues so i downgraded to the normal repos and xwinwrap still runs fine on normal beryl (0.2.0 i believe)

---

### Post by EReckase on 2007-02-07
I've submitted a howto on how to get Electric Sheep running under gnome-screensaver, but it's waiting to be approved.  If you're interested, I'll be happy to forward a copy of the text to private messages - just let me know.

:mrgreen:

---

### Post by cprophecy on 2007-02-18
Triorph:

THANKYOUSIR!
awesome writeup man. i cant thank you enough. made it so easy

edit:
hmm it seems i found an issue. when i click the 'show desktop' icon in the bottom right it turns off the electricsheep background. is there a way to fix this?

---

### Post by Triorph on 2007-02-20
I checked and the show desktop button does the same to me aswell, i don't really know enough on the topic on how to fix that, but beryl has options for its own show desktop that doesn't get rid of the screensaver background, try removing the showdesktop button from the bottom right corner, then in beryl-settings-manager edit the bottom right corner to do either "show desktop" or "fade to desktop" (depending on which you prefer)

---

### Post by cprophecy on 2007-03-30
yea thats what i ended up doing. thanks buddy

---

### Post by Yendor on 2007-04-16
Wonderful how-to, thank you Triorph.

I've noticed though that the animations flash at regular intervals, and that my gDesklets will alternate "above" and "below" with each flash.  Any chance someone knows a fix for this?  I don't mind dumping gDesklets, but the flashing is just too annoying.

---

### Post by Opeth115 on 2007-05-30
my windows on the desktop seem to go below the animation instead of staying on top any ideas about this?

---

### Post by Triorph on 2007-05-31
Yeah I seem to get this problem as well, it seems to be something to do with xwinwrap, you can select the windows however and they will go above the background. There also seems to be the problem that if you have blur enabled it will blur out all your icons (and windows underneath the transparent background)

---

### Post by awesomo3999 on 2007-07-12
Thanks a lot:):) this was easy and im a noob at linux:)::)

---

### Post by glymph on 2007-12-22
Although xwinwrap doesn't appear to be available in the repositories, I found a way of running the glmatrix screensaver on the background using devilspie, I put a screenshot here: [http://rowla.dyndns.org/gallery/v/screenshots/glmatrix_desktop.png.html]("http://rowla.dyndns.org/gallery/v/screenshots/glmatrix_desktop.png.html")

I couldn't find a way to display the icons on top, nor allow the right-click menu to still appear, but it's rather nice in combination with compiz' transparent windows. :D

Dom

---

### Post by Flynn555 on 2008-09-22
sorry

---

### Post by Flynn555 on 2008-09-22
sorry

---

### Post by Flynn555 on 2008-09-22
i had an issue...whenever i added the lines --mplayer -1 i recieved the output 

:/usr/bin$ electricsheep --mplayer -1
Terminated

so i removed --mplayer -1 and just ran electricsheep.
it pulled electric sheep up in a window.  whever the window is maximized electric sheep only shows up in the top left corner

[http://i34.tinypic.com/2lc1w7.png](http://i34.tinypic.com/2lc1w7.png)

the same thing happens when i run the xwinwrap command...

ive tried all kinds of arguments with the mplayer command and none of them seem to solve my problem:(


*edit: omg triple post im so sorry

---

### Post by EReckase on 2008-09-23
I'd uninstall that version and install the new one :D

[http://ubuntuforums.org/showthread.php?t=826554]("http://ubuntuforums.org/showthread.php?t=826554")

Uninstall the old one first, as there may be conflicts otherwise.

---

### Post by Flynn555 on 2008-09-23
ok thank you...i will try this as soon as i get home

---

### Post by Flynn555 on 2008-09-23
hmmm i uninstalled the previous version..
i added the following lines to my sources list

deb [http://ppa.launchpad.net/flam3/ubuntu](http://ppa.launchpad.net/flam3/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/flam3/ubuntu](http://ppa.launchpad.net/flam3/ubuntu) hardy main

then i ran

apt-get update
apt-get install electricsheep

i still get the following output:

~$ electricsheep
Terminated

i also tried the script that compiled electric sheep from source and i get
the same output..

sorry noob here.


*edit:

ok i i added X11 as the video driver in electricsheep-preferences.
now when i run electric sheep it brings up electric sheep in a window.  when maximized electric sheep is in the same dimensions as before but in the middle of the screen...

[http://i36.tinypic.com/2nsbzmr.png]("http://i36.tinypic.com/2nsbzmr.png")

---

### Post by RavUn on 2008-09-24
It's working but covers my icons.  Yours doesn't seem to cover icons and is in the background.  Also, would it work with conky running?  The only thing I did differently was exclude --mplayer 1 in the command, but it would say "bad option: --mplayer".

Also, it looks like your wallpaper is still showing.  Mine just shows the sheep.

EDIT: Sorry, I hadn't noticed the opacity/niceness deal.  However, it only seems to show in the black places of my wallpaper.  I need to make the opacity around 0.9 to be able to see much so it makes my background pretty dark (see attachment... the wallpaper is white).

hmm... it doesn't show in the screenshot... but that black space in the middle is the spot where it shows and in my conky on the bottom right.


If I change the video driver to x11 it seems to work well but it's not full screen, any way to change that?  The xwinwrap takes up the entire screen but the animation is only a portion of the screen in the middle.

---

### Post by Flynn555 on 2008-09-24
that screenshot is what i get when i exclude the xwinwrap command.
i only entered electricsheep in terminal.  

i also get bad option: --mplayer when entering electricsheep --mplayer 1, i dont think you are suposed to use that arguement with the newer version.

what are you using as your video driver when its not X11 ??  blank?? i tried all of the ones listed on the project page (x11, gl, xv) they all give me 
electricsheep
Terminated
the only one that actually opens electricsheep is X11

i might try some more mplayer -vo arguments when i get home.

---

### Post by Flynn555 on 2008-09-24
hmm yeah nothing is working for me...i still cant get it to work.  :(

---

### Post by Triorph on 2008-09-26
OK, its been a long time since I wrote this post, so I can't remember exactly everything that was going on perfectly, however I'll try to help as I can for now.

You guys seemed to have a few problems with opacity/niceness etc, are you running the script I supplied to handle the turning on/off of the desktop, or are you just trying to run the xwinwrap command it self?

Also RavUn that screenshot doesn't look like it has any sheep playing at all, have you left it on sufficiently long enough to download a sheep, or downloaded some manually and added them to your .sheep folder? You shouldn't need to have opacity that high to see the sheep at all (My screenshot was at 0.3)

---

### Post by Triorph on 2008-09-26
ok, well looking into it deeper it seems there is a new version of electricsheep that behaves completely differently to before, so thats why this current method to get the background doesn't work. The new version uses mplayer by default, so it still works with xwinwrap. 

For some reason it doesn't look like it provides the -fs option to mplayer on its own though, which is weird, since you can't even provide an option for it to do this, the only way to get it to display in full screen is by changing the configuration file for mplayer, in ~/.mplayer/config

e.g.
```
gedit ~/.mplayer/config
```

you will then want to add the following lines to the end of this file
```

vo=x11
fs=yes

```

These will set it to be in full screen mode, and use x11 as the rendering (gl should probably work fine here too). This also means you do not have to add the option to electric sheep each time.

I modified the xwinsheep script to work with the new electric sheep as well

```

sudo gedit /usr/bin/xwinsheep

```

then overwrite its contents with the following:

```

#!/bin/bash

# 
# This script runs the electric sheep screensaver on your desktop,
# and drops the name of the screensaver in a marker file.
# When run a second time, it will kill the screensaver.
# Requires xwinwrap to be installed.
# Usage: xwinsheep <OPACITY> <NICENESS> 
# e.g "xwinsheep 0.3 10" will run it at 0.3 opacity
# with a niceness value of 10. Just running "xwinsheep" will
# run it at 1.0 opacity and 19 niceness.


# dir to write marker file to
DIR=~/

#Niceness to run screen saver at. The lower this value, the higher
#priority the screensaver will be. The higher the value, the jerkier
#the screensaver will be, and the less it will intefere with your
#work
NICENESS=$2
if [ -z "$2" ]
then
  NICENESS=19
fi

 

OPACITY=$1
if [ -z $1 ]
then
  OPACITY=1.0
fi

  

if [ -e $DIR.flipflopmarker2 ]
then
	#shows that electric sheep is running via this script
	#kill it, remove the marker file
	killall electricsheep 
	rm $DIR.flipflopmarker2
	exit
fi
	#start the screensaver, write the name of it to a file
	nice -n $NICENESS xwinwrap -ni  -o $OPACITY -fs -s -st -sp -b -nf -- nice -n $NICENESS /usr/bin/electricsheep -window-id WID &
	touch $DIR.flipflopmarker2

exit

```

and if you need to, don't forget to add executable permissions

```

sudo chmod a+x /usr/bin/xwinsheep

```

major changes to the above script are removing the --mplayer=1 option, since mplayer is provided by default, and adding the nice command to the electricsheep part as well. For some reason I was noticing that electric sheep was grinding my computer to a halt before it had any seeds (haven't got any seeds yet, so don't know if this behaviour has improved), but by setting its nice value to be 19 (the default this script uses), other applications gets CPU preference over it.

so finally to show the sheep as the background, just type:
```

xwinsheep 0.3

```

i've added attachment of a screenshot here, no sheeps are playing because it hasn't downloaded any yet (and will probably take days to with New Zealand internet speeds), but the concept is working.

Hopefully this fixes your problems.

---

### Post by Triorph on 2008-09-26
ok it seems new zealand internet is too slow to upload screenshots at the moment as well, I'll upload it later, but hopefully you can just take my word that it works.

---

### Post by RavUn on 2008-09-26
I'm still having the same issue.  I added the fs=yes and changed load_fullscreen to yes in ~/.mplayer/gui.conf but it's still not loading the video fullscreen.

---

### Post by Triorph on 2008-09-26
strange, this probably won't help but could you try putting the fs=yes in the /etc/mplayer/mplayer.conf?

---

### Post by Triorph on 2008-09-26
ok, adding the zoom = yes option to your ~/.mplayer/config file should fix this, however now that i have sheep on this I'm noticing that a mix of software zoom and software mplayer rendering is really lagging my computer, use at your own discretion.

---

### Post by Flynn555 on 2008-09-27
thx for the help triorph.

im going to give this a shot as soon as i get off work.

---

### Post by Flynn555 on 2008-09-28
thx triorph...just letting you know everything works.

i did have to take out /usr/bin/electricsheep out of the script and replace it with just electricsheep

also i wasntable to run the script using xwinsheep 0.3 so i just added the opacity in the script  so i just run xwinsheep.

but other than that everything is working.  it is a little laggy but not much.
thx again for your help!

---

### Post by Shotime on 2008-10-06
Thanks so much for this tutorial, following it almost exactly and with a little of my own tweaking I got electricsheep to work on my Heron Ubuntu with just a little bit of trouble.
It's so flashy man.

---

### Post by BattleStarJesus on 2009-01-21
> **glymph said:**
> Although xwinwrap doesn't appear to be available in the repositories, I found a way of running the glmatrix screensaver on the background using devilspie, I put a screenshot here: [http://rowla.dyndns.org/gallery/v/screenshots/glmatrix_desktop.png.html]("http://rowla.dyndns.org/gallery/v/screenshots/glmatrix_desktop.png.html")

I couldn't find a way to display the icons on top, nor allow the right-click menu to still appear, but it's rather nice in combination with compiz' transparent windows. :D

Dom

How did you achieve this?  I got the electric sheep working, but it only shows short clips of sheep and it is real choppy like.  I am wondering how to adjust the settings?  Also what is the best app to use for managing screen saver, I am using Xubuntu 8.10.  The screen saver manager does not permit me to adjust any of the screen saver settings. 

I would like to configure my background to periodically fade between the electric sheep and the matrix or a mix of the two, how can this be accomplished?

---

### Post by Triorph on 2009-01-22
I don't know about this other devilspie application, but the original post I based this script off [here]("http://ubuntuforums.org/showthread.php?t=198968") has a script that allows you to set most of the generic screensavers to your background, including GLmatrix. Combine this with another script that works out the timing you should be able to cycle between the two. I haven't looked into it deeply though. One likely problem about this method is that the "fade-in" between the two screensavers is likely to be jerky, but electric sheep is generally like that anyway so you should probably be used to it.

---

### Post by Triorph on 2009-01-28
Also just like to point out you can have both electricsheep and glmatrix going at the same time. See the attached screenshot

---

### Post by Bobbake4 on 2009-10-29
I know this thread is old but I didn't know where else to ask this.  First off I have electricsheep running as my background but it will only run on my main monitor no in dual monitors.  The other one is just left blank.  If you know how to fix this that would be very helpful.  Also the only way I could make it work is to change my ~/.mplayer/config file to add some options including root window.  Now I am unable to lock the screen because it is set as root window but I would still like electricsheep to be my screensaver.  Any ideas on either of these problems would be helpful.

Thanks

Bobbake

---

