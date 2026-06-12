---
title: "HOWTO: MythTV with Dual-Head and LIRC"
date: 2007-10-07
forum: Outdated Tutorials &amp; Tips
---

### Post by Toxicity999 on 2007-10-07
Well it's really not that difficult!

[SIZE=3]Contents:
Part 0.5: What do I need?
Part 1: Make use of that TV!
Part 2: LIRC is your friend![/SIZE]
[SIZE=3]Part 3: Fun Stuff
Part 3.1: Using your Power button for something
Part 3.2: Make Logging in less boring!
Part [/SIZE][SIZE=3]3.3: Starting MythFrontend on your TV at login[/SIZE]
[SIZE=4]
Part 0.5: What do I need?[/SIZE]
Required:
-A functional MythTV install
-A Graphics Card with some form of TV Out Capability
-A Good Remote which works with LIRC (I recommend a Microsoft MCE Remote, they work well)
-GDM, most likely for the last portion you can drop in replace GDM with KDM, XDM, what have you, but who knows

[SIZE=4]Part 1: Make use of that TV!

[/SIZE]Firstly, we have to get TV out working for you! What we're going to do is a method called Dual X, or Dual head... Essentially you have two X sessions, within one X server, the cursor/key presses can pass from one to another, you just cannot drag between the two.



WARNING: The following can reeeeeally screw up your X system if you mess up, nothing is irreversible however, it's just a configuration file! For the sake of your sanity and my own in answering any questions, BACK UP YOUR xorg.conf to a SAFE LOCATION.



What we have to do is define two monitors, and two graphics processors in /etc/X11/xorg.conf this will most likely be the trickiest portion to the whole thing as it can vary from setup to setup... what you'll want to do is  just copy and paste your video card portion of Xorg.conf below it, then you have tow identical entries, change the name of the second one, for instance add a 1 to the end, along with each pointing to their respective screens, where screen 0 is your monitor and screen 1 is your TV as seen here:

```
Section "Device"
    Identifier    "videocard0"
    Driver        "nvidia"
    Screen 0
    BusID        "PCI:5:0:0"
EndSection

Section "Device"
    Identifier    "videocard1"
    Driver        "nvidia"
    Screen 1
    BusID        "PCI:5:0:0"
EndSection
```Make sure the BusID is in tact! all your previous options will be thrown under the original video card entry, as this points to the monitor.

Now go down to the Monitor portion of Xorg.conf, you will see something similar to:

```
Section "Monitor"
    Identifier    "DELL 1504FP"
    Option        "DPMS"
    HorizSync    30-60
    VertRefresh    56-75
EndSection
```Add this below it:
```
Section "Monitor"
        Identifier "Television"
        HorizSync 30-50
        VertRefresh 60
EndSection
```Of course exchanging my sync and refresh rates with your own (Experiment later).

Now we pull it all together! Do down to the screen section, you will see something similar to:

```
Section "Screen"
    Identifier    "Screen0"
    Device        "videocard0"
    Monitor        "DELL 1504FP"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```Add this below it:
```
Section "Screen"
        Identifier      "Screen1"
        Device          "videocard1"
        Monitor         "Television"
        DefaultDepth    24
        Option  "TVOutFormat" "SVIDEO"
        Option  "TVStandard" "NTSC-M"
        Option  "ConnectedMonitor" "TV"
        SubSection "Display"
                Depth 24
                Modes "640x480"
        EndSubSection
EndSection
```Again substituting your own values for my own.

Now we simply tell X how to display this in the server layout section:
```
Section "ServerLayout"
    Identifier    "Default Layout"
        Screen 0        "Screen0"
        Screen 1        "Screen1" rightof "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection
```I know this is all fairly confusing... theres no real way to make it simple, I will however provide my xorg.conf for reference. all I can say is make *sure* that the identifiers match up, for example if you name something Videocard1, make sure the screen is asking for Videocard1 and not supercard3000 or something. Yes, I know, odd example, but you get the point I would hope.

See attached Xorg.conf

When you restart X you should have a default looking gnome setup on your TV after you login... don't worry about how the Tv is fairly blank looking during GDM... we'll fix that later with some spicing up!


[SIZE=4]Part 2: LIRC is your friend!

[/SIZE]The next thing we're going to do is get your remote working. I'm not here to teach you about configuring LIRC... this should already be done. By that I mean LIRC should have names to all of your button presses in lirc.conf. I'm basically going to throw up my .lircrc which you just need to put in to ~/ (your home directory) and restart LIRC with:

```
sudo /etc/init.d/lirc restart
``` See attached .lircrc
[SIZE=4]
Part 3: Fun stuff[/SIZE]
Here we get the fun stuff going, like a power toggle button, throwing something on the TV screen during GDM, random things I've got going on my build.

[SIZE=4]Part 3.1: Using your Power button for something[/SIZE]
I'll need you to issue a 
```
gksu /usr/bin/mythrun
```Here we create a script to toggle mythfrontend on the TV, we assign this to the power button on your remote. If it's off, it'll run, if it's on, it'll close it, fun right? so put this in it:
```
#!/bin/bash
PROG=mythfrontend
STATUS=`ps -e | grep $PROG | grep -v grep | wc -l | awk '{print $1}'`

if [ `echo $DISPLAY | grep -c ":0"` -ge 1 ]
then
    if [ $STATUS -eq 0 ]
    then
        ( DISPLAY=:0.1 $PROG & )
    else
        killall $PROG
    fi
fi
exit 0
```Now issue the command to make it executable:
```
sudo chmod +x /usr/bin/mythrun
```And there you have it. Now you need to get irexec going! This is a program which will run to translate button presses of the remote in to scripts... so add irexec to your session startup, or run it yourself manually. Make sure to only have one instance of it going at a time or else the script will be run twice. which is rather fun... but not very efficient.

[SIZE=4]Part 3.2: Make Logging in less boring!
[SIZE=2]The first thing you need to do is decide what you want to show... I opted for a screensaver, specifically Helios. So if you choose something else, like a video just replace that reference in my run through with whatever you want.[/SIZE]

[SIZE=2]What we're going to do is a bit of gdm config hacking. If you cd into /etc/gdm/ and issue an ls, you'll see a basic tree of what we're working with. the first thing we want to edit is /etc/gdm/Init/Default so issue a:
```
gksu gedit 
```[/SIZE][/SIZE]```
[SIZE=4][SIZE=2]/etc/gdm/Init/Default[/SIZE][/SIZE]
```[SIZE=4][SIZE=2]

Right under the comments add:
```
/usr/bin/tvgdm < /dev/null
```This calls the script which we use to display what we want there. Save that and close it, then open up [/SIZE][/SIZE][SIZE=4][SIZE=2]/usr/bin/tvgdm as we just went over here throw in:
```
#/bin/bash
DISPLAY=:0.1 /usr/lib/xscreensaver/helios -r &
```Where "[/SIZE][/SIZE][SIZE=4][SIZE=2]/usr/lib/xscreensaver/helios -r" is your own command, be it mplayer, another screensaver, whatever. Save that and make it executable with:
```
sudo chmod +x /usr/bin/tvgdm
```Now we have it starting... but that does us little good as it will simply stay going as root until we kill it manually in the user session! That's just crazy! so what we do is modify the GDM PostLogin script so that right after we login, the screensaver is killed, cool, huh?
```
sudo cp /etc/gdm/PostLogin/Default.sample /etc/gdm/PostLogin/Default
```Then
```
gksu gedit 
```[/SIZE][/SIZE]```
[SIZE=4][SIZE=2]/etc/gdm/PostLogin/Default[/SIZE][/SIZE]
```[SIZE=4][SIZE=2]

Make it look like:
```
#!/bin/sh
#
# Note: this is a sample and will not be run as is.  Change the name of this
# file to <gdmconfdir>/PostLogin/Default for this script to be run.  This
# script will be run before any setup is run on behalf of the user and is
# useful if you for example need to do some setup to create a home directory
# for the user or something like that.  $HOME, $LOGNAME and such will all be
# set appropriately and this script is run as root.
/usr/bin/killhelios &
```Now we have just the one more script to make... then this section is done!

gksu gedit /usr/bin/killhelios

What we're going to do here is make it wait 3 seconds after login to kill the screensaver, this gives the Desktop time to load, so you never see anything else, this also transitions nicely if you start Mythfrontend automatically on the TV. So enter:
```
#/bin/bash
sleep 3
killall helios >/dev/null
```Save it then again:
```
sudo chmod +x /usr/bin/killhelios
```Save it, and DONE. Now you should have the screensaver on your TV with GDM login present on your monitor, it will kill about 3 seconds after your gnome-session begins.

[SIZE=4]Part 3.3: Starting MythFrontend on your TV at login[/SIZE]
First see Section 3.1 about creating the mythrun script.

This ones easy, just one script and a minor edit to a GUI dialog!

```
gksu gedit /usr/bin/gnomestartmyth
```Put this in to it:
```
#/bin/bash
sleep 5
/usr/bin/mythrun
```The timer is to make it delay enough so that the mythtv backend is started before it starts... if you have a large sessions startup list or a slow computer, increase this number as you see fit.

Make it executable with
```
sudo chmod +x /usr/bin/gnomestartmyth
```and there you have it.

Now just add it to System >> Preferences >> Sessions as
Name: Mythfrontend TV startup
Description: Start MythTV on TV Out channel
Command: gnomestartmyth

And there you have it!

That's all for now... Sorry if it seems rather confusing. Feel free to ask questions.
[/SIZE][/SIZE]

---

### Post by Ubeast on 2008-04-27
Cool toggle script, I would never have been able to write that from scratch so thanks so much for that!

I had to modify it a little to get it to work with Hardy 8.04 and MythTV 0.21. It wouldn't kill the frontend with just *killall mythfrontend* as your script calls, so I made it thus:

```
#!/bin/bash
PROG=mythfrontend
STATUS=`ps -e | grep $PROG | grep -v grep | wc -l | awk '{print $1}'`

if [ `echo $DISPLAY | grep -c ":0"` -ge 1 ]
then
    if [ $STATUS -eq 0 ]
    then
        ( DISPLAY=:0.1 $PROG & )
    else
        killall mythfrontend.real
    fi
fi
exit 0
```

I realise it's not as neat but it works :).

Also, I have two screens, so by making two scripts and setting one to use:

```
        ( DISPLAY=:0.0 $PROG & )
```

and the other to use

```
        ( DISPLAY=:0.1 $PROG & )
```

I can now easily launch Myth on the right screen. Legend! Even more brilliant as one of my screens is a projector so if it's off but I have left MythTV running on it, this script will tidy up before I launch MythTV on my LCD TV.

Now I just have to figure out how to use irexec call from my mythtv lirc config.

---

### Post by Toxicity999 on 2008-04-27
Cool. I've recently switched to using a dedicated box for my TV output, so I'm out of practice with this stuff. I'm glad you got some use out of it.

All of the ubuntu packages, by convention, only use mythfrontend and mythbackend as launcher scripts, with *.real being the actual binary.

---

