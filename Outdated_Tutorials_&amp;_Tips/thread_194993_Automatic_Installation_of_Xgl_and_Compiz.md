---
title: "Automatic Installation of Xgl and Compiz"
date: 2006-06-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Ra211 on 2006-06-12
I thought that by now there would be a ton of threads like this one around already, but as requested by [mstlyevil]("http://ubuntuforums.org/member.php?u=35815") [here]("http://www.compiz.net/viewtopic.php?id=1037") and several others like [sha_man]("http://ubuntuforums.org/member.php?u=83683") [here]("http://ubuntuforums.org/showthread.php?t=147049"), I decided to post my own version of a script to automize the installation of Xgl and Compiz on Ubuntu.

Attached to this post therefore is an improved version of what I sent to mstlyevil for Automatix, which I believe will work on both ATI and NVIDIA graphics cards using Ubuntu 6.06.

Please do understand that I do not have an NVIDIA graphics card, and therefore had to somewhat "guess" what the standard situation (of /etc/X11/xorg.conf) looks like and what it should look like after installation. It should work perfectly on ATI graphics cards and I think it'll work on NVIDIA graphics cards as well, but I couldn't find someone to quickly test it.

In short, this script installs the flgrx driver for your ATI graphics card or the nvidia driver for your NVIDIA graphics card, then installs Xgl and Compiz in a seperate X session, installs Gset-Compiz and then changes some bad default settings.
Therefore, to run Xgl and Compiz  you must select the "Xgl"-X session in the GNOME Display Manager (the loginscreen).
Packages installed are those from QuinnStorm; Gset-Compiz gives the user a nice interface to change many Compiz settings.

Run this script by entering the following in a terminal after downloading it:
```
cd Desktop
tar -xf Ra211.tar.bz2
sudo sh Ra211.sh
```

Again, I have not thoroughly tested this yet, and so far there has been no NVIDIA graphics card user willing to sacrifice enough time to confirm whether this script works.
Should this script work fine and enough people are interested, a future version might add compatibility for Kubuntu and Intel graphics cards.

To see whether you graphics card from ATI or NVIDIA will work, see [this]("http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL") page. Again, my script installs the fglrx driver (noted there as "ati-drivers-8.25.18") for ATI graphics cards, no support for other (open source) drivers yet.

Please be so kind to report your results.

---

### Post by Bhai on 2006-06-12
Checking Linux distribution and version. Expecting to see Ubuntu Linux 6.06 (LTS).

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06 LTS"


Error:
_______________________________________________

It stops after this one

cat /etc/*release* above
egrep -qi "$rel" returns nothing

proberly thats why it gives an error?

---

### Post by Mellon on 2006-06-12
same here, trying in ubuntu dapper with a Ati card.

---

### Post by Ra211 on 2006-06-12
I'm sorry, will have a look at that later.
Removed that part for now.

---

### Post by larsemil on 2006-06-12
Your graphics card is currently not supported.

Ati x800xt.... arggh!

---

### Post by larsemil on 2006-06-12
Your graphics card is currently not supported.

Ati x800xt.... arggh!

---

### Post by stefannasello on 2006-06-12
I get the same thing...

Your system is now up-to-date.

~/Desktop
Your graphics card is currently not supporte

X800 pro.

---

### Post by SuperMightyMo on 2006-06-12
Hey

Same problem, 

I tested it on a NVDIA card 6800,

---

### Post by Ra211 on 2006-06-12
Yes, I already found the problem.
Will be fixed in a minute or so; this post will then be edited.

Edit: Found and fixed.

---

### Post by RJMacReady on 2006-06-12
Your graphics card is not currently supported.

Its an ATI Radeon 9700pro.

---

### Post by Slicedbread on 2006-06-12
[QUOTE=Ra211]Yes, I already found the problem.
Will be fixed in a minute or so; this post will then be edited.

Edit: Found and fixed.[/QUOTE]

```
Your graphics card is currently not supported.
```

ATI xpress 200m (integrated), I just removed my xgl/compiz installation to try this so I am pretty sure it works on this chipset too. Yes I tried the newest one that was updated like 4 minutes ago..

---

### Post by Trespasser on 2006-06-12
Probably will not work with mine, but getting the same message. I have a ATI Radeon 7000 VE PCI card.

---

### Post by Torstein_V on 2006-06-12
Very good initiative, Ra211, but there seems to be some issues with your script concerning supported graphic cards. 

I'm using Dapper 6.06 with Ati Radeon 9600 256mb ram, and even I get the "Not supported graphic card" error. And that's odd!

---

### Post by Ra211 on 2006-06-12
Yes, I'm sorry, I messed up while updating my startpost. Should work now.

Some cards, like Trespassers Radeon 7000 will definitely not work. You will have to check that out for yourself [here]("http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL") until my script does that.

---

### Post by Slicedbread on 2006-06-12
It works now, make sure you restart though -gave me a little scare when nothing loaded. I like the seperate Xsession to.

---

### Post by Torstein_V on 2006-06-12
Hmm, something's wrong with the XGL-session. Attempting to load into it, makes the screen turn brown for ten seconds, before I'm thrown back into the login screen. 

Logging into the normal Gnome-session works like a charm, but not the XGL.

I didn't get any errors installing the script, and I remembered to reboot after its successful installation.

Any gueses on what might has caused this?

Using ATI Radeon 9600 as graphic card.

EDIT: At least I think it was successful. I didn't get any errors, anyway.

---

### Post by Torstein_V on 2006-06-12
Ok, this is what I got at the very end of the script:

> This scrip may have modified and backed up the following files: /etc/apt/sources.list and /etc/X11/xorg.conf.
Ra211.sh: line 159: syntax error near unexpected token `('
Ra211.sh: line 159: `echo "You can start Xgl and Compiz by selecting the Xgl X session in the GNOME Display Manager (the loginscreen).'


---

### Post by cohill on 2006-06-12
ATI Radeon 9100u (I think)

Seemed to work fine, but when I go to the xgl session after restart i just get a screen that is like looking into a Kaleidoscope.

Also when the script is finished there is a syntax error...
"Ra211.sh: Line 159: syntax near unexpected token ')'"

---

### Post by Slicedbread on 2006-06-12
Edit: I did get the error, but its just a text prompt, nothing to do with the installation putting ' ' around the paranthesis fixes it.


As for the brown checkerboard screen, that shows that compiz is installed.

Try
```
 sudo gedit /etc/gdm/gdm.conf
```

and change "GdmXserverTimeout=10" to like "GdmXserverTimeout=50"

---

### Post by Torstein_V on 2006-06-12
Slicebread:

I changed it from 10 to 50, rebooted, but am getting the same brown screen for 10 - 14 seconds, before I'm back at the login screen.

I even tried to run the script twice with a reboot whitout any luck. Help? :-(

---

### Post by cohill on 2006-06-12
I am getting the same thing.  Except the login screen is now a checkerboard.  I can log in, but everthing is still a checkerboard until I restart and go into gnome.

---

### Post by KaridaSerious on 2006-06-12
I tested it and it worked for me

My graphics adapter isNvidia 6600

Thou some problems occured but it still worked. Thanks alot for your help i've been battling with this for some time now :). but keep up the good work and fix those minor problems that occured. The script didn't install xserver-xgl and compiz for me so I had to install them my self.

- KDS

---

### Post by Bhai on 2006-06-12
The file is corrupted?

I cant extract it :-(

Its telling me its not a bzip2 file and extis
----------------------
nvm i downloaded it with my laptop and copied it over network

---

### Post by Torstein_V on 2006-06-12
Bhai, try isntalling .rar-support.
_____________


Okay, installing xserver-xgl and compiz:

```
sudo apt-get install xserver-xgl compiz
```

has somewhat solved my problem with the brown screen. I am now able to log into XGL-session, but when I do, I encounter a two problems, one of them strange :)

1. No XGL-effects 

2. No window borders (Yep, that's correct, the minimize, maximize and close buttons are all gone, along with the border.)

So, I figure the problems lies in the lack of packages.

So far I've installed xserver-xgl and compiz. Are there any other packages that should be installed?

---

### Post by Ra211 on 2006-06-12
Try the script again.
I just changed something related to installing the packages (and fixed the syntax errors reported earlier).

---

### Post by Torstein_V on 2006-06-12
Hmm, new error it seems. This is what I get with your new changes, Ra211:

> torstein@torstein-desktop:~/Desktop$ sudo sh Ra211.sh
Password:
Checking Linux distribution and version. Expecting to see Ubuntu Linux 6.06 (LTS).

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06 LTS"


Error:
torstein@torstein-desktop:~/Desktop$


Hmmm ;)

---

### Post by RavenOfOdin on 2006-06-12
[QUOTE=Torstein_V]
2. No window borders (Yep, that's correct, the minimize, maximize and close buttons are all gone, along with the border.)
[/QUOTE]

To get them back just bring up a terminal window and execute metacity.

---

### Post by Torstein_V on 2006-06-12
Okay, I opened up the script, and had a look at it, and I'm impressed! It's a very good and thouroughly done work ,and even though I have no experience in scripting, I understood quite much of it ;)

Anyway, that's how I found the packages that I missed to get XGL up and working. Here's the recipe:

Download the script. Untar and run it. After it's done, write this into SHELL/Terminal:

```
sudo apt-get install libgl1-mesa libglitz1 libglitz-glx1 xserver-xgl compiz compiz-gnome gset-compiz
```

If you get the message:

[B]E: Couldn't find package gset-compiz
[/B]
 Just skip that package, much likely you won't need it, like I don't.

Reboot, and voila, XGL up and working! Major thanks to Ra211 for making the script! :)


Anyway, I have adressed a few bugs, and it is related to the XGL performance: Swapping desktops, playing with the "cube" etc works perfectly, but if I try making the windows wobble they some how "freezes" in a position for a couple of seconds, before they wobble a bit more, freezes in a new position that would be natural to the wobbling movement, wobbles again, freezes and stops to wobble, when the wobble action has comed to an end.

Anybody know if this is caused by the **gset-compiz** package I couldn't install, and how I might retrieve it? 

:)

---

### Post by edgarf28 on 2006-06-12
i get this error on a new fresh dapper installation:

> "Checking Linux distribution and version. Expecting to see Ubuntu Linux 6.06 (LTS).

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06 LTS"


Error:"

I have an ATI X800XT-PE AGP

---

### Post by Slicedbread on 2006-06-12
Torstein, the freezing is most likely do to incorrect settings in x, run fglrxinfo and see if it says ati, if it does it means you have rendering. It could also be a configuration error due to a bad install. I have an ati integrated chipset and I dont get lag or slow downs besides scrolling in firefox. The gset-compiz is a graphical configuration package that is not required for correct operation. 

If you would like to try and install it for your self (its pretty easy) try [here ]("http://www.compiz.net/viewtopic.php?id=389")

---

### Post by Torstein_V on 2006-06-12
Slicebread, here follows what I got out of fgrlxinfo:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5814 (8.25.18 )

So, should I change it to fglrx, or just let it be? 

After reading through the Howto you linked to, I've decided to follow that one, and more precisely "the second howto" :) But before I proceed with that, it is noticed that I must make sure to remove all previous XGL-installations, but I'm not quite sure how to reverse this thread's script (No offense Ra211, it just didn't work for me, great initiative and effort though! ;) ).

Any ideas, Slicedbread?

---

### Post by veelivar on 2006-06-12
I'm also getting the  following error with the latest script.

I have a compleatly fresh install of Dapper (from cd, just updated) and an nvidia 6800GS graphics card.

Any help/suggestions that you could give to gett he script workign would be appreciated.  This looks a much easier way of getting xgl working (I've tried manually following a number of different posts but not been successful) and I like the idea of being able to choose a xgl/compiz session or not at start up.

Thanks in advance,
Dan


> Checking Linux distribution and version. Expecting to see Ubuntu Linux 6.06 (LTS).

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06 LTS"


Error:


---

### Post by RavenOfOdin on 2006-06-12
*notices the " major pain in the *** " button on Compiz is lit*

I'm running an ATI Radeon 9200 SE and I can't seem to get this working, after these steps:

1. Timeout in gdm.conf modified to 50 and Servers section modified from 0=Standard to 1=Standard
2. gdm-conf.custom modified as follows:
```

 [servers] 
1=Xgl 
 [server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true

```

(Notice I put in server-Xgl instead of server=Xgl because the standard server didn't require an '=' either.)

3. Desktop script as per Method B of Compiz installation on Ubuntu Wiki to load up gnome-window-decorator and compiz itself, as well as xmodmap to get around the alt-meta keys error.

4. Shell script named startxgl.sh in my [color=red]/etc/X11[/color](now in /usr/bin, and executable)directory with the following:

```

#!/bin/sh
#Start up XGL, Compiz and GNOME
#Run XGL server on :1, on top of normal X
Xgl -fullscreen -ac -accel xv -accel glx:pbuffer & sleep = 2 && DISPLAY=:1
exec gnome-session

```

5. "diversions" directory created in /usr/share/fglrx and populated with the following:

```

sudo ln -s /usr/lib/fglrx/libGL.so.1.xlibmesa libGL.so.1

```


I'm using GDM, GNOME and 6.06 with an ATI Radeon 9200 SE graphics card.  Each time I've tried bringing up compiz, it gives me the error:

> 
compiz.real: Support for non power of two textures missing.


I'm also using the fglrx drivers (8.25.48) with a custom kernel and the 8.14.13 libGL.so workaround.

Compiz doesn't show up in gconf-editor and after trying this:

```

sudo gconftool --set --type list --list-type string /apps/compiz/general/allscreens/options/active_plugins '[gconf, miniwin, decoration, browser, fade, minimize, cube, rotate, zoom, scale, move, resize, place, switcher, trailfocus, water]' 

```

which should get entries for Compiz to be placed there, nothing happens and no change is noticed in the config editor, even after a few restarts.

I've tried preloading the diversion with compiz --replace gconf in a second xterm, but that isn't working either. I either get a notice which says "LD_PRELOAD: Cannot preload object of this type for <object here>" or the error "Support for non power of two textures missing" again.

glxinfo -display :1 doesn't list that extension, and nor does it list my ATI drivers under OpenGL. The ATI Control application gives a notice which says "Driver does not provide FireGL X11 extensions! Panel components will operate only partially." I've tried aticonfig to resolve this but have had no luck.

When I try to run the startup script from way up above in the console, I get errors which are saved to Xorg.93.log, followed by a few breakdowns in fonts and RGB problems.

Some of this, like the sessions panel, is probably to excess what with the startup script mods, so I might take them out. 

Is there anyone who knows what the problem might be? I'd really appreciate the help.

(Oh BTW, upon getting into GNOME, Metacity is killed before loading window borders. I can't get into the "Windows" section of Preferences either.)

(LD_LIBRARY_PATH variable is set to /usr/lib)

---

### Post by aktiwers on 2006-06-12
I cant download the file.

It says 

> Invalid Attachment specified. If you followed a valid link, please notify the [administrator]("http://www.ubuntuforums.org/sendmessage.php")

---

### Post by RavenOfOdin on 2006-06-13
OK. . .been at this a while longer and not even the Compiz installation methods on the Ubuntu Wiki are working. Tried to get fglrx OpenGL running with both the 8.14.13 libGL.so and the correct one for current version.  Hacking my xorg.conf file to redirect fglrx to a different display doesn't work, either.

If no one has any ideas, I might just download the .deb files QuinnStorm put up on compiz.net, and barring that somehow removing the "non power of two" error I'll just say "f*** it."

(EDIT: gnome-session seems to run fine under root access with Xgl, although I haven't checked the capability of my ATI card to process images there, nor have I checked Compiz. )

---

### Post by RavenOfOdin on 2006-06-13
(little unrelated sidebar: Mods: PLEASE, PLEASE make it so users can delete their own posts.
I hate it when this happens.
;) )

---

### Post by protonmule on 2006-06-13
Ran the script and rebooted. When logging in using the XGL session, X loads as if no window manager is running (black+white checkerboardbackground, default x cursor, no windows).

ATI Radeon 9600 mobility.

fglrxinfo:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600 Generic
OpenGL version string: 2.0.5814 (8.25.18)
```

---

### Post by paul.maddox on 2006-06-13
Wehey! Worked great for me on my laptop (ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9])

You rock!

---

### Post by Nuld on 2006-06-13
Well it's working for me... sometimes ;). I just started the Xgl session 3 times and the following happend:

1st try: it froze immediately after I logged in until I pressed the power off button, then it did a clean shutdown
2nd try: gnome loaded, but all window borders were missing
3rd try: it seems to be working ok, window borders are present and several xgl effects are working

It remains to be tested if it'll work more reliable in the future or if I'll always have to start the session several times.

Transparency and water effects are not working, but this may be do to the fact that I installed the packages from the universe repository instead of running your script (I performed several steps of your script manually). Maybe those packages are older? Any other ideas?

One more thing that I don't like is that the shutdown dialog of this session doesn't have the options to reboot or shutdown the computer, but only to log out, hibernate, etc. Any ideas what's the reason for this and how I can get the same dialog that I have when I start the default session?

Thanks.

---

### Post by Nuld on 2006-06-13
Oh and another question: The files in ~/.config/autostart/* are being executed from every session. Wouldn't it be better if the xgl specific commands were only executed when the xgl session is begin started? Is it possible to specify this somehow?

---

### Post by boakes on 2006-06-13
I managed to get it installed but, everything looks like the refresh rate is off.  I can't read the browser unless I minimize it first.

---

### Post by Slicedbread on 2006-06-13
Go to gset-compiz (applications>accessories) and select the appropriate refresh rate.

---

### Post by freemanen on 2006-06-13
I have a  Nvidia GeForce Go 6200 TurboCache. Then i login in xgl mode i just get a brown screen and after some seconds it logs out. It worked for me with koorana live cd. But I would love to have it in ubuntu. Any ide what could be wrong and why script doesn't work for me? thanks for the god ide with the script.

---

### Post by Seadap on 2006-06-13
[QUOTE=freemanen]I have a  Nvidia GeForce Go 6200 TurboCache. Then i login in xgl mode i just get a brown screen and after some seconds it logs out. It worked for me with koorana live cd. But I would love to have it in ubuntu. Any ide what could be wrong and why script doesn't work for me? thanks for the god ide with the script.[/QUOTE]

I tried this just now and had this problem.  Then the update manager notified me that there were updates - so naturally I ran them.  Afterwords, the same 10 sec timeout happened, this time it showed me the error message log.  It complains of a bad option referencing xv:fd0 and dropped me back to the login screen.

I'm using an AMD64 with dual SLi Nvidia Geforce 6600 GT's.

Still looking...


Edit:
After running the command :

sudo gconftool --set --type list --list-type string /apps/compiz/general/allscreens/options/active_plugins '[gconf, miniwin, decoration, browser, fade, minimize, cube, rotate, zoom, scale, move, resize, place, switcher, trailfocus, water]' 

I now get the entry in gconf-editor

Getting closer methinks....

---

### Post by WetWilly on 2006-06-13
no show....9800 pro.

I tell you how I installed it.

downloaded, untarred to desktop, ran as sudo. Immidietly 3 errors printed in terminal but script continued:

Ra211.sh: line 151: GNOME: command not found
Ra211.sh: line 153: UbuntuDapper: command not found
cp: target " " is not a folder: File or folder does not exist

I guess in your editing you removed the GNOME() and UBUNTUDAPPER() subs. so until you readd them you should at least comment them or delete them entirely.

Then at the end it printed

Ra211.sh: line 121: /home/basti/.config/autostart/compiz.desktop: File or folder does not exist
Ra211.sh: line 122: /home/basti/.config/autostart/gnome-window-decorator.desktop: File or folder does not exist
Ra211.sh: line 123: /home/basti/.config/autostart/gnome-panel.desktop: File or folder does not exist
Ra211.sh: line 124: /home/basti/.config/autostart/xmodmap.desktop: File or folder does not exist

then once the script finished Update Manager manager told me there was an update; libcairo2. I installed it!

Anyway, after logging out, restarting x(u say reboot, is that really needed?), and selecting XGL at loginpanel I logged in and had massive hacks... like if you have really low fps in a computergame... and no special effects... I ran fglrxinfo and it printed out some lame driver version.. not fglrx like I had before.. 

so I thought f*ck it I restore my old xorg.conf (xorg.conf.save) and guess what? The backup of xorg.conf was wrong.... very wrong!! For example it had the driver part totally deleted... wtf?

This need alot more work :(

---

### Post by Valshar on 2006-06-13
I'm sorry, but is there anyway to undo what that package just did?

---

### Post by WetWilly on 2006-06-13
Valshar. if you are lucky the script backed up your xorg.conf properly.

Then you can do:

```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_bad

sudo mv /etc/X11/xorg.conf.save /etc/X11/xorg.conf

```

If it did not... then you have to edit xorg.conf manually and readd whatever was changed/deleted..

anyway, people should not use this script...

the second guide here is alot better. and safer.

[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)

---

### Post by KLineD on 2006-06-13
I have tried everything to get XGL working with my system. I have an ATI Radeon 9250 with fglrx drivers.

3D acceleration is working. When I ran the script I algo got the same errors WetWilly mentioned. I restarted the computer, then logged in with Xgl session but nothing changed. I had no Xgl effects, nothing fancy. 3D acceleration is still working and everything works out normal but I'm left exactly as I was.

---

### Post by WetWilly on 2006-06-13
KLineD

I used this [guide]("http://www.compiz.net/viewtopic.php?id=389") instead of the script, use the second guide, and got it to work now, but the script destroyed my 3d accelaration. I will fix that later, too tired now :P

Also if u have run the script, u will have 2 xgl sessions in gnome login manager. Use the bottom one (number .4 for me)

I dont recommend anyone to use this script at it's current state.

---

### Post by KLineD on 2006-06-13
Thanks for the advice WetWilly. I'll just remove the other Xgl session located in /usr/share/xsessions/Xgl.desktop so there's no confussion.

I'll post the results later (when I get home, I'm @ work right now where Windows reigns and Linux is a taboo topic)

---

### Post by TechnoMage on 2006-06-13
Tried on a new Dell XPS M1210 laptop.  Script installed fine but when I try to log in with a XGL session it hangs for about 30 seconds and then takes me back to the main login screen.

FYI: Graphics in this is a 256MB NVIDIA GeForce Go 7400 TurboCache

---

### Post by Ra211 on 2006-06-13
For those who can successfully launch their Xgl-X session but don't see the fancy effects, I found and fixed the problem, pretty sure that's it.
Run this to correct it:
```
echo -e "[Desktop Entry]\nName=No name\nEncoding=UTF-8\nVersion=1.0\nExec=compiz --replace gconf\nX-GNOME-Autostart-enabled=true" > $HOME/.config/autostart/compiz.desktop
echo -e "[Desktop Entry]\nName=No name\nEncoding=UTF-8\nVersion=1.0\nExec=gnome-window-decorator\nX-GNOME-Autostart-enabled=true" > $HOME/.config/autostart/gnome-window-decorator.desktop
echo -e "[Desktop Entry]\nName=No name\nEncoding=UTF-8\nVersion=1.0\nExec=killall gnome-panel\nX-GNOME-Autostart-enabled=true" > $HOME/.config/autostart/gnome-panel.desktop
```

Could NVIDIA-users who have recently tried the script and whose Xgl-X session refuses to load please try what I posted above and the following and report their results?
```
sudo apt-get -y install --reinstall libgl1-mesa libglitz1 libglitz-glx1 xserver-xgl compiz compiz-gnome
sudo echo -e "Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1\nexec gnome-session" > /usr/local/bin/Xgl.sh
```

To go back to your old xorg.conf, use the following:
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

Lastly, my apologies for all of you who are having problems.
I'm very busy at the moment, but I'm convinced that with your help we can fix all problems.

---

### Post by yavez on 2006-06-13
Didn't work for me either :(

I think i've tried everything now.  Same thing happens, I'm met with a black screen before I even reach GDM (this happens even if it's only the Nvidia driver I'm trying to load)  I have to go in through recovery mode and copy over the xorg backup every time.

Anybody know why this is?  I'm running an Nvidia 6200.

---

### Post by nephesh on 2006-06-13
Just tried the script and it didn't work for me.

I'm running on k7 kernel with a Radeon 9800 Pro.

---

### Post by axiomata on 2006-06-13
[QUOTE=Ra211]For those who can successfully launch their Xgl-X session but don't see the fancy effects, I found and fixed the problem, pretty sure that's it.
Run this to correct it:
```
echo -e "[Desktop Entry]\nName=No name\nEncoding=UTF-8\nVersion=1.0\nExec=compiz --replace gconf\nX-GNOME-Autostart-enabled=true" > $HOME/.config/autostart/compiz.desktop
echo -e "[Desktop Entry]\nName=No name\nEncoding=UTF-8\nVersion=1.0\nExec=gnome-window-decorator\nX-GNOME-Autostart-enabled=true" > $HOME/.config/autostart/gnome-window-decorator.desktop
echo -e "[Desktop Entry]\nName=No name\nEncoding=UTF-8\nVersion=1.0\nExec=killall gnome-panel\nX-GNOME-Autostart-enabled=true" > $HOME/.config/autostart/gnome-panel.desktop
```

It appeared to install correctly, no errors and all, but I don't see fancy effects when I run the Xgl session (I do get the lag though).  If I try to run what you recommended I get:

```
bash: /home/brett/.config/autostart/gnome-panel.desktop: No such file or directory
```

Browsing my home folder I don't even have the hidden .config folder.

---

### Post by KLineD on 2006-06-14
[QUOTE=Ra211]For those who can successfully launch their Xgl-X session but don't see the fancy effects, I found and fixed the problem, pretty sure that's it.
Run this to correct it:
```
echo -e "[Desktop Entry]\nName=No name\nEncoding=UTF-8\nVersion=1.0\nExec=compiz --replace gconf\nX-GNOME-Autostart-enabled=true" > $HOME/.config/autostart/compiz.desktop
echo -e "[Desktop Entry]\nName=No name\nEncoding=UTF-8\nVersion=1.0\nExec=gnome-window-decorator\nX-GNOME-Autostart-enabled=true" > $HOME/.config/autostart/gnome-window-decorator.desktop
echo -e "[Desktop Entry]\nName=No name\nEncoding=UTF-8\nVersion=1.0\nExec=killall gnome-panel\nX-GNOME-Autostart-enabled=true" > $HOME/.config/autostart/gnome-panel.desktop
```

Could NVIDIA-users who have recently tried the script and whose Xgl-X session refuses to load please try what I posted above and the following and report their results?
```
sudo apt-get -y install --reinstall libgl1-mesa libglitz1 libglitz-glx1 xserver-xgl compiz compiz-gnome
sudo echo -e "Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1\nexec gnome-session" > /usr/local/bin/Xgl.sh
```

To go back to your old xorg.conf, use the following:
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

Lastly, my apologies for all of you who are having problems.
I'm very busy at the moment, but I'm convinced that with your help we can fix all problems.[/QUOTE]

Nope... I still don't get the fancy effects. However my keyboard layout seems broken. I read somewhere how to fix it but I don't remember where.

Ok, I investigated a bit and it seems that even when I select Xgl session from gdm, Xgl server is not started and when I try to manually run compiz, it complains about no composite extensions.

Then I try to manually run Xgl, by means of the following script
```

Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1
exec gnome-session

```

Xgl server runs, but I'm left with just a background and the spinning cursor. Then I go to tty2 (ctrl+alt+F2) and try to run Compiz, with the following script:
```

killall gnome-window-decorator
wait
gnome-window-decorator & DISPLAY=:1
compiz --replace gconf
#fixes the shift-backspace bug
xmodmap /usr/share/xmodmap/xmodmap.mx

```

Compiz complains about D-BUS and says it'll deactivate it. Then it complains about not being able to open the display and sits there idle. So I'm left with Xgl server with no compiz and no desktop at all.

Can anyone help me nail this one? I would surely appreciate it.

---

### Post by KLineD on 2006-06-14
Does anyone know how else can I check if /usr/bin/startxgl.sh is executing when I select Xgl session? I think the reason I get no composite extensions when trying to run compiz.

---

### Post by b0rsten on 2006-06-14
how do i remove everythink that was installed by this script?

i can't switch to other useraccounts anymore, i have to logout with account A and then login with account B...  [-X :confused:


and everytime i press <ALT> it opens the "take a screenshot" - dialog...

---

### Post by KLineD on 2006-06-14
I finally made it!!!

What I finally did was edit /etc/gdm/gdm.conf-custom and added the following info:
```

[servers]
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX).
1=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer

```

My problem was that the command above didn't recognized the && Display part as an option, so I just removed that to see what happened and to my surprise it started gdm (it took a while, with checkered background and spinning cursor).

After Xgl was initialized I just manually ran compizstart and it did it. Of course my keyboard layout is broken (tab completion in the console just makes the window sort of vibrate, but no autocompletion)

---

### Post by Laurier on 2006-06-14
Works fine on first try here. I Thought I'd post even my uninteresting results seeing as the script asked so nicely. I've got a Radeon X300 and Dapper.

---

### Post by neoflight on 2006-06-14
i havent used tihs script yet.... 
was using the other how to (step by step ) the other day and had several problems...

anyone observed a slow firefox open (i mean in stages) after installing xgl-compiz? after using this script?

i had that problem and was pretty annoying...so had to revert to the default one... 

i dont want to screw the system again....btw. what range of FPS are you guys getting?
is this ok ???

from 
$ glxgears -printfps

[PHP]10747 frames in 5.0 seconds = 2149.315 FPS
10796 frames in 5.0 seconds = 2159.025 FPS
10796 frames in 5.0 seconds = 2159.150 FPS
10796 frames in 5.0 seconds = 2159.088 FPS
[/PHP]

and the driver is 
[PHP]$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600 Generic
OpenGL version string: 2.0.5814 (8.25.18)
[/PHP]

thanks

---

### Post by WetWilly on 2006-06-14
I installed Xgl+Compiz using this step by step guide [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389) and it's working fine, except the fact that I can't run fgl_glxgears. Is that normal behaviour? If I run fglrxinfo while logged in a normal Gnome session I get

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.5814 (8.25.18)
```

while if I run it when logged in xgl I get

```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.5814 (8.25.18)
```


Could someone with working xgl and an ATI card run this command and post their result, here is mine.

glxinfo |grep direct

```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No
```

I fear it's that Xlib part that is the cause of my errors.

---

### Post by KLineD on 2006-06-14
Even thou I got Xgl to work, there are too many small problems with it that make it just a really great show off but not really usable (IMHO).

Several apps make the Xgl server crash and for me, the plugins where unstable (sometimes they load, sometimes they dont) and my keyboard shortcuts refuse to work.

Anyway, great to see this stuff progressing nice.

---

### Post by RavenOfOdin on 2006-06-14
[QUOTE=KLineD]
Several apps make the Xgl server crash[/QUOTE]

. . . the XGL server is crashing for me on the drop of a hat. All I have to do is go into the terminal and type in a few letters.

---

### Post by Poison0985 on 2006-06-14
I installed the script and ran it, but now it doesn't enter in any session except for terminal. It asks me for my login info and then it tries to load but returns to the main screen. What can I do? Please someone help me out. I have nVidia 6600 and Dapper

---

### Post by clov on 2006-06-14
Hi!
I used the script and it worked fine.
The only problem I had was ~/.config/autostart directory was missing, I created and solved the problem. 
Now I can't use ALT+GR key it doeen't work! can anyone solve this problem?

thkx

---

### Post by Koybe on 2006-06-15
What if i already have my graphics driver installed?

---

### Post by KLineD on 2006-06-15
[QUOTE=clov]Hi!
I used the script and it worked fine.
The only problem I had was ~/.config/autostart directory was missing, I created and solved the problem. 
Now I can't use ALT+GR key it doeen't work! can anyone solve this problem?

thkx[/QUOTE]
Try this
```

xmodmap /usr/share/xmodmap/xmodmap.us

```

Substitute 'us' ending with your country code. Have a look at the content of /usr/share/xmodmap first (for example I'm in Mexico so my country code is 'mx' but it doesn't exists, so I choose 'es' for Spanish or Spain I guess)

---

### Post by KLineD on 2006-06-15
[QUOTE=Koybe]What if i already have my graphics driver installed?[/QUOTE]
apt will report that you already have the newest drivers. At least it did with me, I was in the same situation as you are.

---

### Post by clov on 2006-06-15
[QUOTE=KLineD]Try this
```

xmodmap /usr/share/xmodmap/xmodmap.us

```

Substitute 'us' ending with your country code. Have a look at the content of /usr/share/xmodmap first (for example I'm in Mexico so my country code is 'mx' but it doesn't exists, so I choose 'es' for Spanish or Spain I guess)[/QUOTE]

Thkx! I added xmodmap do /usr/local/bin/Xgl.sh

---

### Post by leftware on 2006-06-15
I just ran the script on my fresh installation of 6.06 and it ran without error, or at least no error that I saw.  I rebooted and went into the Xgl session and I get absolutely crap performance, i.e. terrible redraw times and any keyboard entry takes about 2 seconds to show up on screen.  

This is on an ATI 9800Pro.

Ideas?

---

### Post by RavenOfOdin on 2006-06-15
[QUOTE=leftware]I just ran the script on my fresh installation of 6.06 and it ran without error, or at least no error that I saw.  I rebooted and went into the Xgl session and I get absolutely crap performance, i.e. terrible redraw times and any keyboard entry takes about 2 seconds to show up on screen.  

This is on an ATI 9800Pro.

Ideas?[/QUOTE]

I don't know if these entries in xorg.conf would help but try:

Option "AccelMethod" "EXA"
Option "EnablePageFlip" "true"
Option "RenderAccel" "true"
Option "backingstore" "true"

in your ATI card section.

---

### Post by KLineD on 2006-06-16
I got this after an update today, maybe that's it? Too bad I didn't saw what packages got updated but after that, Xgl performance is sluggish to say the least. [-X

---

### Post by leftware on 2006-06-16
[QUOTE=RavenOfOdin]I don't know if these entries in xorg.conf would help but try:

Option "AccelMethod" "EXA"
Option "EnablePageFlip" "true"
Option "RenderAccel" "true"
Option "backingstore" "true"

in your ATI card section.[/QUOTE]

Tried it, didn't seem to do anything.  Still seeing 0 effects, typing delays, etc.  I *will* have this working if I have to try every guide there is!  :P

---

### Post by WetWilly on 2006-06-16
please someone with an ATI card and xgl+compiz running paste your

```
fglrxinfo
```

---

### Post by Alpha_Cluster on 2006-06-16
Ive been trying everything under the sun to get the fancy effects to work... But every time i think im close or use one of the fixes i just lose borders to all my windows and still can move is there a way to solve this?

---

### Post by KLineD on 2006-06-16
[QUOTE=leftware]I just ran the script on my fresh installation of 6.06 and it ran without error, or at least no error that I saw.  I rebooted and went into the Xgl session and I get absolutely crap performance, i.e. terrible redraw times and any keyboard entry takes about 2 seconds to show up on screen.  

This is on an ATI 9800Pro.

Ideas?[/QUOTE]

Try running glxgears from a console, if it crashes, then you need to replace your libGL.so.1.2 file with an older one. The same thing happened to me because there was an updated fglrx package and I installed it.

---

### Post by KLineD on 2006-06-16
[QUOTE=WetWilly]please someone with an ATI card and xgl+compiz running paste your

```
fglrxinfo
```[/QUOTE]

I'll do when I get home... somewhere around 7pm GMT-7

---

### Post by leftware on 2006-06-16
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
10199 frames in 5.1 seconds = 2005.069 FPS

I get the above error, but the program runs fine.  I get the same error in fglrxinfo.  On the GNOME session (which I had to switch to so I could type this), I don't get the error.

---

### Post by leftware on 2006-06-16
Well, I basically just followed this guide to fix a couple things, and everything works perfectly.

[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)

Craziness.  Pure craziness.

---

### Post by lime4x4 on 2006-06-16
well i ran the script everything installed with no errors..I can login with xgl but when i do i havfe no shutdown or restart buttons. Second when i log out and start gnome session and run the following command i get this

john@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.

i still have fglrx listed as the driver but it's not loading it anymore..

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AS [Radeon 9600]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"

And this is what i get under xgl session
 
john@ubuntu:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

Also when in xgl session when scrolling it moves 1 line at a time very very very annoying...How would i go about uninstalling this and getting back my proper video driver's?

---

### Post by FryerFox on 2006-06-16
I just tried the script and couldn't get back into GNOME or XGL. I get a black screen, and then knocked back out again. I had fortunately backed up my /etc/ and /home/a/.gnome* directories and restored them from a terminal.

I was then able to restart gdm and get back in.

I give you an A for effort, though :)

EDIT: I'm using an nVidia card

---

### Post by f3x on 2006-06-16
Hi & tanks for your usefull script
Grabbing your script is the defenitive argument for registering at this forum and thus you deserve the privilege of having my first post ;)


Well my experience is a bit special concerning your script...
The first thing i did was to try to install evething manually
I used the "Compiz Thread that rule them all" and installed lasted of everything
Also fixed a few thing and configured Xgl to start automaticly on my gnome.

I got a not really functioning gnome with hard to move window etc...

Then i used you script and reboot.

Bad new first: Xgl session really does not work. Stuck a brown screen and logoff.

Good news: your script somehow fixed what was not working on the normal gnome session. this really rocks ;)

Remark: Compiz / State plugin is absolutely awfull... it makes the window so transparent i cant use them.... disabling it makes everything better ;)

<Keyboard>
Well it's a know pain when dealing with compiz that it reset some keyboard setting. One useful thing i have discovered is that you can backup your config  with xmodmap -pke wich is less confusing that choseing the language letters.

-----------------

Now do you know how to remove that Xgl from session as it does not work anyway? I also have some problem at login screen concerning keyboard and num keypad. Otherwise it work great

---

### Post by KLineD on 2006-06-16
[QUOTE=f3x]Now do you know how to remove that Xgl from session as it does not work anyway? I also have some problem at login screen concerning keyboard and num keypad. Otherwise it work great[/QUOTE]

Remove the corresponding file from /usr/share/xsessions

---

### Post by Mikeynewbie on 2006-06-17
Hello there I tried this, I have an Nvidia Geforce graphics card everything seems to go where it needs to I even get an xgl session choice at login, however when I try to go into this session i get a black screen and then it reverts to the login screen again.  Just as a note I have both k and g desktops on my computer, I wonder if this may present a problem.

---

### Post by lowrizzle on 2006-06-17
I ran the script and saw no errors, but when I logged back in with an Xgl session I got terrible TERRIBLE performance on a 9600 with 256mb of ram.  And it broke my wifi.  Totally broke it, and I can't figure out how.  It worked just fine before now, I'm using an Airlink+ 802.11g PCI card with the 111 chipset.  I had to delete the default config that came with dapper and installed the windows drivers using ndiswrapper and it worked just fine.  Now, when I go to System->Administration->Networking it always defaults to eth0 instead of wlan0, and if I set it for wlan0, I quit and return to the Networking util and it goes back to eth0.  If I disable eth0, I return and the field is blank.  I've tried uninstalling the driver using ndiswrapper, reinstalled it, made sure it was running which is is, I've tried a great many things, and it won't work.  I've got a cat5 draped across my living room, and it's inconvenient.  Can anyone help point out something I'm not seeing.  I'm half tempted to reinstall dapper, but I'd hate to have to.

---

### Post by leftware on 2006-06-20
The only issue I'm having at the moment is all windows that are created are created in the upper left corner far too high up, obscuring the title bar.  I have to use alt+click to drag a window back into view or right click it in the titlebar.  

Anyone know a fix for this?

---

### Post by oocce on 2006-06-21
I have installed Xgl/Compiz like this: [http://ubuntuguide.org/wiki/Dapper#H...z_.28Nvidia.29](http://ubuntuguide.org/wiki/Dapper#H...z_.28Nvidia.29) , but I cant get transparency working... I have read that alt+mouse wheel should do it to focused window :roll:

---

### Post by NETabuse on 2006-06-21
i'm running this now since the week of Dapper 6.06 release.. it's damn cool.. still struggling with the xmodmap issue.. if i set to .uk it give me no euro sign with alt-gr + 4 .. so still have the shift backspace issue. maybe i just need to locate a .ie version of xmodmap (there isn't one in that directory)

anyway.. my other issue is with starup,, when gdm loads the login dialog.. i get what i believe is known as artifacts.. but they obscure everything... blank patches of colour over whatever you click on.. menu's popup.. but no text,,, you type in your username.. but no text actually visibly goes into input area... i have to blind type to login... then start compiz with a script(i could add this to my session startup scripts sure) but how could i get rid of the issues at gdm login screen.

hardware:
compaq (3y/o) N610c, pentium 4m(the bad mobile chip) 1.6 Ghz, 768MB ram, ati radeon mobility 7500. 

I run on the "ati" driver, not gflrx. 
xorg.conf 
```

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

I'm not sure if the DRI section is neccessary,, and as to why the Identifier lists the card as Radeon Mobility M7 LW[9000] i really don't know.. specially as lspci shows up "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]" 
strange. anyway. One issue i had while starting my Xgl 2 weeks ago was at boot up, Xgl had a fatal error seemingly due to the bcm43xx driver, and wacom input devices. i cleared the wacom devices, and odly the bcm43xx which is still loading ceased to throw errors.. The bcm43xx is due to my Buffalo G54S pcmcia wireless card which is broadcom 4306 based chipset.

Hope all this info is of use to someone.

forgot to mention.. also had major issues with the plugins.. but everything is reasonably stable now i just turn off water, (which throws a missing GL_ARB  type file..) turn off trailfocus(cause it's ugly) turn off gconf-dump and dock which is just seriously buggy.. and finally,, whatever you do, DO NOT USE miniwin.... does not work at all.

I see someone has issues with wifi, the problem is usually with wpasupplicant, the fix to get things easily working with network-admin and nm-applet(even simultaniously) for me was just create /etc/default/wpasupplicat and have just the line "ENABLED=0" in there.

---

### Post by TheEclypse on 2006-06-21
I ran the script, restarted, and have the problem where you get the brown screen then thrown back to the login screen.

I tried modifying xgl.sh to:

```
Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:0
exec gnome-session
```

which enables me to login, but I dont think Xgl is actually running.  I have all the usual metacity look and feel of things, except there is edge resistance on the windows (i suppose that is gnome-window-decorators work?).  Checking the running processes with ps -A shows that the gnome-window-decorator is running, but compiz and Xgl arent listed.

Any ideas?

I have an ATI X1800XL and am using Dapper.

Edit: trying to start compiz with "compiz --replace gconf &" tells me that there is "No composite extension"

---

### Post by Johnnyboyct on 2006-06-21
Ran the script on a geforce 5200 go, and it wouldent restart,just gave me black login. Then i edited the .conf file and and took out the extra few entries. 

I get the same thing with the brown screen and it drops me back down to the normal login, anyone fixed this yet?

---

### Post by ballgofar on 2006-06-21
THANKS!! This script got me further than I have been on this XGL/COMPIZ quest but everytime I move a window X crashes and kicks me back out to the login screen.

Anyone seen something similar?

---

### Post by SlimDady on 2006-06-22
Works well.

ati 9800xt

I had the same issue someone else had.. no option for restart or shutdown from withing the desktop.. I have to logout then use the login screen, or shutdown from a terminal window.

Not too sure why it removed those options from the shutdown/logout screen..

---

### Post by Hexenjagd on 2006-06-22
When running this script, I get these errors:

Ra211.sh: line 122: /home/dsfargeg/.config/autostart/compiz.desktop: No such file or directory
Ra211.sh: line 123: /home/dsfargeg/.config/autostart/gnome-window-decorator.desktop: No such file or directory
Ra211.sh: line 124: /home/dsfargeg/.config/autostart/gnome-panel.desktop: No such file or directory
Ra211.sh: line 125: /home/dsfargeg/.config/autostart/xmodmap.desktop: No such file or directory
chown: cannot access `/home/dsfargeg/.config/autostart/': No such file or directory

Any idea what I'm doing wrong? (I'm really new to linux so it could be something incredibly obvious.)

---

### Post by JackandJohn on 2006-06-23
I just did a manual install based on the stuff in the script: 
add beerorkid repository
update and install packages
(I already had the fglrx driver working)
Echo the text to the files
-reboot
XGL worked, but everything was messed up: oops, forgot something
run the gconf stuff
log out
log in



Living the sweet life :)


9800pro AGP, A64 on i386 kernel w/powernowd killed dead

---

### Post by ChemPete on 2006-06-24
My computer:

Dell Inspiron 9400 laptop (Core Duo, 1gb DDR, Ati x1400 and Ubuntu 6.06 clean installation).
Script gives me no errors.

My problems:

[IMG]http://img66.imageshack.us/img66/3659/1a9hu.jpg[/IMG]
Logged with the Xgl session.

[IMG]http://img121.imageshack.us/img121/5921/2a8sv.jpg[/IMG]
Ubuntu splash screen with a extrange patterned black and white background (not my default background), after this background goes normal.

[IMG]http://img407.imageshack.us/img407/1503/3a6en.jpg[/IMG]
I ran on a terminal a script and try to run Xgl/Compiz.
```
gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher water &
```

[IMG]http://img224.imageshack.us/img224/5115/4a5gj.jpg[/IMG]
Ok, Xgl/Compiz get up, i get the funzy effects, the rotating cube, everything smooth and nice with my Ati x1400.

[IMG]http://img394.imageshack.us/img394/9611/5a8nm.jpg[/IMG]
But when i try to make an alt+tab switch betwen windows Xgl/Compiz goes down.

[IMG]http://img369.imageshack.us/img369/8625/6a1rd.jpg[/IMG]
And removes me the topbar, so i`m not able to move windows or rotate the cube any more.

I asume this bug is caused because of my "non traditional" way to run Xgl/Compiz. Any help will be welcome :).

[COLOR="Red"]EDIT: PROBLEM SOLVED, MINIWIN AND DOCK PRODUCES BUGS ON SOME SYSTEMS.[/COLOR]

---

### Post by Brando569 on 2006-06-24
just some thing you might wanna correct in the first post so n00bs dont get confused:

1. change "cd desktop" to "cd <where you downloaded the file>" :D

---

### Post by shoyer on 2006-06-24
I'm getting errors like Torstein_V did -- I select login with Xgl and I get a brown screen for 15 seconds and then get returned to the login screen. I tried your suggestions and his suggestions but neither have changed it.

I have an ATI Mobility Radeon 9000 card running on a Dell Latitude D600.

Thanks for your help.

---

### Post by anakin_sk4jvoker on 2006-06-25
thanks , works just fine :)

---

### Post by mstlyevil on 2006-06-25
I am going to have Jdong look this script over for modification and inclusion in Automatix. We may leave it to the user to make certain they have the latest drivers installed since we are taking a sessions approach to Compiz. This way all people who have cards supported by compiz will be able to install compiz through Automatix and if it does not work all they have to do is reboot and change sessions back to a non XGL session to restore their system.

This approach is much safer and we feel more comfortable with it. Also if you are a gamer or use 3D applications you can just choose the session you need for the particular task.

We are discussing adding ATI for only chipsets that are known to play well with the drivers to Automatix. All other ATI chipsets are a support nightmare and that is why we have not included ATI.

I will talk to Jdong and formulate a plan to get this going soon. We have had a setback due to arnieboy having to leave the team as a dev due to work. This has made us short handed. If any of you are experienced at bash (not a novice) and want to help get this in Automatix, get in touch with me.

Thanks 
mstlyevil

---

### Post by Dubbayoo on 2006-06-25
This did not work with my Radeon 8500. The script seemed to run w/o error. After rebooting and selecting XGL login I get a blank screen w/cursor, the cursor changes to the waiting cursor then i'm sent back to the login screen. I can log in with Gnome normally.
Where do I look to troubleshoot the error? xorg log?

---

### Post by Ra211 on 2006-06-25
Put a new version online.

Only contains a few small tweaks:
Fixed the "No such file or directory"-error.
Possibly fixed keyboardproblems.
Possibly fixed problems nVidia-users are having (I really need someone with knowledge over settings for the nVidia-driver in xorg.conf here).


Due to various personal problems, I've barely been online over the past few weeks and may not be able to do so the next few weeks, my apologies for that. I'll really try to be online more in the future to help everyone out, but can't promise anything.
It'd be really nice if someone with enough knowledge could help me track down problems or simply take over this project.

---

### Post by leftware on 2006-07-10
So.. nobody's having the same problem I am with windows being created in the far upper left corner?  I'd like to find out it's just a config file issue and I can just modify it to create new windows in center or something.

---

### Post by qrm on 2006-07-10
i have an nvidia fx5200, I ran this script and when i try to log in with session Xgl it doesnt start. But when i try to log in with default gnome i get all the fancy effects :confused:

---

### Post by slowz3r on 2006-07-11
i cant get it to log in to this at all

---

### Post by nir78 on 2006-07-11
I executed the script and everything went fine (I think...).
Now I logged in to the XGL session and everything looks the same like the gnome one...
Anything I should execute\ use ?

Nir

---

### Post by jonah1980 on 2006-07-11
i get the 10-15 secs of brown screen then a flash of black and back to login

---

### Post by bageloid on 2006-07-11
I love you

after 5 trys and two complete ubuntu reinstallations(linux newbie and forgot to back up files...ugh), this worked, just have to fix the resolution, i cant get 1280*1024 anymore, but thats not a big deal.

Running a dell xps gen 5 with geforce 6800 [nv41.1]

did i mention i love you?

\\:D/


heh, now my xorg.conf says im running a radeon, whatever, it works.

---

### Post by INMCM on 2006-07-11
Works great on my X800XL. So far this script has been the only way I can install the ATI drivers and not have my moniter go out of range (Vert/Horiz Refresh Rate Probs). One Thing though: A couple of values in the Wobble plugin are set to absurd defaults. The menus and when I maximize windows wobble like crazy for a long period of time making them hard to use.

---

### Post by bageloid on 2006-07-11
Wobble was cool and all, but after trying to go through the menus to test it out, i started to feel sea sick, so i decided to turn it off, besides it caused too much tearing of the windows.


Edit:
Because of xgl, my whole family now wants me install linux for them on their computers. I guess people like shiny.

---

### Post by ericesque on 2006-07-12
@RA211

"I thought that by now there would be a ton of threads like this one around already, but as requested by mstlyevil here and several others like sha_man here, I decided to post my own version of a script to automize the installation of Xgl and Compiz on Ubuntu."

I'm assuming by now you realize why the task of developing an automated approach had not been undertaken. ;)

---

### Post by matoxxx on 2006-07-12
Nice one, woked like a charm for me :) finnaly

Ati x1600xt
athlon 64

only thing i needed to install the fglrx drivers manualy , cause the sript seems to not execute the --initial command
thanks a lot

---

### Post by jonah1980 on 2006-07-12
anyone know how to get past the 15 second brown screen of death?

---

### Post by bocmaxima on 2006-07-12
> **bageloid said:**
> Wobble was cool and all, but after trying to go through the menus to test it out, i started to feel sea sick, so i decided to turn it off, besides it caused too much tearing of the windows.



Install gset-compiz and you can change the amounts of everything. So you can add details to your desktop but not get motion sickness.

---

### Post by hit0442 on 2006-07-12
Well, I`m on a live CD `cause I don`t know what to do. I ran the script and when I try to log in GNOME, some of the panels appears but suddenly, appears a black screen and back to GDM. I`ve already tried to back up the xorg.conf but it still doesn`t work.

---

### Post by ZarathustraDK on 2006-07-12
WOOT! It works! ThankyouthankyouThankyouthankyouThankyouthankyouThankyouthankyouThankyouthankyouThankyouthankyou

I tried using Poofyhairguys guide (doing it manually), but I must have screwed up somewhere.

So, thumbs up for my part, my keyboard settings are screwed up though (layout switched to US instead of danish). I got the 15 sec brown screen of poop, then it changed to a white cube that I could manipulate, then I was kicked back to login, logged in, and xgl-compix-love is mine.

My system uses an Inno3d geforce 7800 GT.

---

### Post by Sethro on 2006-07-15
I really hope XGL works.. iam downloading ubuntu just for XGL.
I HOPE IT WORKS!!! LOL


Thanks so much man for putting this script togethere
YOu are the man
you are the king
you are god
you are the almighty
you are a kick *** programmer


LOL

Okay wish me luck

---

### Post by rs3 on 2006-07-15
> **hit0442 said:**
> Well, I`m on a live CD `cause I don`t know what to do. I ran the script and when I try to log in GNOME, some of the panels appears but suddenly, appears a black screen and back to GDM. I`ve already tried to back up the xorg.conf but it still doesn`t work.

My experience with this automatic installation is quite similar.  Attempting to run the Xgl session (as specified in the instructions at the end of the script) resulted in about a 15-second pause on the brown pre-splash screen, then a gdm restart.  Attempts to boot the standard (not failsafe) GNOME session would get as far as panel loads then another gdm restart.

I was able to comment out the last three lines of the new xorg.conf to get back to a working GNOME session...I just returned to my backup xorg.conf, though, just for general principles.

(Also, upon my arrival, I was given update notification and found five packages (cairo, cairo2, glitz, etc; all pertinent to this effort) to install.  I tried it, hoping that might remedy the 15-second pause and all that, but to no avail)

I'm using two nVidia GeForce 7600 cards with SLI set to "on."

(edit: contrary to my signature, I'm trying this out on Dapper for x86, not amd64)

---

### Post by FRiEd on 2006-07-15
Hi,
Thank you very much to the author of this script, it appears it works for most people which is great.

While the script was running it appears it ran fine, started with xgl option, I get a message saying that the session was run for less than 10seconds, and to check the logs.

I am quite new to xubuntu, although I have run xfce on Arch Linux before, never attempted xgl though.

Can anybody make heads or tales of this log, maybe give me some idea why its not working.

I am running the 64bit version of Xubuntu with an ATi Radeon Mobility 9700 pro.

---

### Post by AirRaven on 2006-07-15
...This is agony.

I spend three hours extricating myself from endless crashes and glitches to get Compiz working manually, break it completely by using a bad script, and then I notice **THIS**?

You're an absolute genius. Here's hoping it works.

---

### Post by Sethro on 2006-07-15
OH MY GOD!!!


WOW Thanks so much to the author of this script you have done a wounderfull job on this, thanks so much!!!


XGL works perfectly


God Bless

---

### Post by Epperly on 2006-07-16
Can somebody help me please? I don't really know what I have to do in response to this, because I know I have an ATI graphics card.

"sammy@SAMMY:~$ cd Desktop
sammy@SAMMY:~/Desktop$ tar -xf Ra211.tar.bz2
sammy@SAMMY:~/Desktop$ sudo sh Ra211.sh

**To use this script, you must either have a graphic card from ATI or NVIDIA.**

sammy@SAMMY:~/Desktop$"

Thanks in advance!

---

### Post by odyssey41 on 2006-07-16
Followed instructions and rebooted. Only thing I notice is new, higher screen resolution (ATI 9600) and the GSET-COMPIZ program under "accessories." Never got any XGL Login screen or anything like it. Am I missing something??? (Sorry, I'm newbie).Do I have to re-install?

---

### Post by odyssey41 on 2006-07-16
Never mind!!!! I got it. It's working PERFECTLY!!! Thank you!!! Now I have to make some adjustments to the "wobbliness," otherwise, it will make me have disorientation/sickness...  :-D

---

### Post by AirRaven on 2006-07-16
*whistles*
The wobble settings are a little high, no? :-k 

Still. Awesome! Worked perfectly first time. Kudos!

---

### Post by shane_on_u on 2006-07-16
Worked for me!

ATI x850xt

Thanks!

---

### Post by blanc11 on 2006-07-16
I installed it and now every time I log into Xgl and my Gnome sessions it stands still for 10 seconds then it returns to loging, how do I fix this problem?Thanks.

---

### Post by jonah1980 on 2006-07-16
is it the brown screen of death like i get also? i hope a new version of the script will fix this?

---

### Post by blanc11 on 2006-07-16
> **jonah1980 said:**
> is it the brown screen of death like i get also? i hope a new version of the script will fix this?

I don't have an error message, but I think it is. I am reinstalling Ubuntu and prbably won't try again, because this is the 5th time I reinstalled.

---

### Post by GuitarHero on 2006-07-16
Can you still use 3d acceleration with XGL/Compiz?  Like can I play wolfenstein?

---

### Post by AirRaven on 2006-07-16
Is there any way of getting a "Shut Down" and "Restart" button in the "Quit" dialog? They're missing at the moment.

It's kind of inconvenient to have to do [FONT="Courier New"]sudo shutdown -r now[/FONT] everytime I want to restart the computer.
> **GuitarHero said:**
> Can you still use 3d acceleration with XGL/Compiz?  Like can I play wolfenstein?
Looks like the answer's no as far as I can see. At least that's what Cedega's test results say. You'll have to boot into the standard GNOME session.

---

### Post by GuitarHero on 2006-07-17
Well the script seemed to work, I rebooted and selected xgl as the session.  It boots into ubuntu but im not seeing the xgl effects.  The system is noticibly sluggish as if it was running it but i dont see the fancy eye candy.  Also my machine shouldnt be bogged down this much i wouldnt think.  2gig ram, 512mb radeon x1900xt vid, 2ghz AMD dual core.... hmmm.  I looked in apps>accessories>gsetcompiz but it seems like everything is enabled.

---

### Post by Sak on 2006-07-17
I thought I'd post the results of my experience here.  So far everything is great in terms of graphics.  Prior to running this script I was using the default Radeon driver that installs from 6.06.  It showed that DRI was enabled but I kept getting freezes on various 3D applications.  i.e. simply creating a UVsphere in Blender would cause X to hang.  Several GL based screensavers would do the same.  

So everything seems to be working great now.  I only get about half the frame rate on glxgears if I'm running under the Xgl session as opposed to the default Gnome session however - approx 3200-3400 fps compared to about 6400 fps.  

Unfortunately, somewhere during the process I got a new kernel, among other  changes to the system, and so I've lost my wireless connection to my network.  I've rebuilt and reinstalled the driver for the wireless dongle, and it seems to be working fine, except that it won't let me access my secure network.  Instead it keeps defaulting to my neighbor's convieniently unsecured access point.  

I've also posted here...
[http://www.ubuntuforums.org/showthread.php?t=217724](http://www.ubuntuforums.org/showthread.php?t=217724)
... in regards to this issue, so I hope this isn't considered cross posting.  Just trying to get the info out to anyone else who's using a similar setup as I have.

Athlon XP 2400
1g RAM
Radeon 9800 Pro
ZyDas zd1211 usb net dongle

---

### Post by GuitarHero on 2006-07-17
Did you use DCHP or direct ip

---

### Post by Sak on 2006-07-18
> **GuitarHero said:**
> Did you use DCHP or direct ip

My wireless access point is using DHCP for all hosts.  I'm not really sure that I can define static IP addresses in it.  At least I haven't found a way yet.  Linksys WRT54G

I don't think DHCP is the problem though.  It seems to work fine as long as I have open the access point without any security.  I'd rather not do that though.  I use WEP because some older wireless cards here can't do WPA.

---

### Post by odyssey41 on 2006-07-18
I was able to manage the wobbliness properly. What I have been unable to change is the transparency of the drop-down menus... way too transparent. Any suggestions on how to modify this???:confused:

---

### Post by PaulEdwards on 2006-07-18
Works great (after toning down the menu wobble), except for one thing.....
I now have no sound in X...

There is sound in GDM, but after logging in, no more sound.
The sound card appears to have disappeared. :confused:

---

### Post by jkwarras on 2006-07-19
This is really nice and easy, thanks!

I just have two problems like othe people here:

- No windows decorations, and no way to get them back no matter if I restart xgl or change settings under compiz.

- No shutdown/restart buttons.

If someone knows how to fix it, I'll appretiate it.

---

### Post by jonah1980 on 2006-07-20
anyone know what's causing this 15second brown screen yet and how to fix it? i'm still on the brown screen of death...

---

### Post by AirRaven on 2006-07-20
The sluggishness happened to me as well when I tried to set up Compiz manually. I fixed it by reformatting and reinstalling Ubuntu- hardly an ideal solution. 

The missing reboot and shutdown buttons are apparently a long-standing problem with seperate XGl sessions. Check out the official Compiz forums- they don't know what's causing it.

---

### Post by richbarna on 2006-07-21
I already had compiz on another pc, so I tried this script on a nVidia FX 5200.
The install went fine, booted chose the session, logged in and the login manager keeps crashing.
Here are the xsession logs:-
> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "richs"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/dapper:/tmp/.ICE-unix/4705
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(gnome-panel:4774): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(gnome-panel:4812): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed
compiz.real: No composite extension

(gnome-panel:4812): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -9 and height 24


I know xgl/compiz works on this machine because I had it before. This is a fresh partition with Dapper + all updates and latest nVidia drivers.

---

### Post by alb_gra on 2006-07-21
Ra211, your are the new god :)

I've installed the script on a Acer 4002WLMI Laptop (Radeon Mobility 9700 64MB) and everything was OK, low CPU use, high speed, MARVELLOUS!!

Thank you very very much!!

---

### Post by LCC on 2006-07-21
The script was run sucessfully, but for some reason I got none of the eye candy of XGL, in fact it looks just like before. After the reeboot I chosen XGL it flashes a grey screen for about two secs, then it turns brown gain, and ubuntu starts just like before,I cannot switch between the workspace areas and when I minimize a program it just vanishes,how do I fix it or go back to what it was before?.I am running ubuntu x_64 with ATI X800 XL
Any idea???

---

### Post by tuxbunta on 2006-07-21
[COLOR="Black"]Hi there,

I ran your script, but sadly after loggin in after 10 seconds it failed I tried to copy the error text, but once I got in to n operable session it havd not copied to allow me to paste.

This was the closest to using XGL I have gotten, but sadly no luck I currently use an ATI X1600 on an amd64 not sure if this is too new?

Any help would be apprecaited.

Thanks,

Tuxbunta.[/COLOR]:confused:

---

### Post by AirRaven on 2006-07-22
The Compiz team appear to have deprecated gnome-window-decorator and replaced it with "cgwd". 

Any way you could reflect this in your script? All that it takes is replacing all mentions of gnome-window-decorator with "cgwd".

---

### Post by ericcmi on 2006-07-22
> Get:37 [http://en.archive.ubuntu.com](http://en.archive.ubuntu.com) dapper-backports/multiverse Sources [14B]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (146.137.96.15), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (146.137.96.7), connection timed out
Fetched 4495kB in 11m34s (6475B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (146.137.96.15), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (146.137.96.7), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.



I keep getting this. The connections to en.archive.ubuntu.com just fine. I searched around in the sh and didnt find a reference to that domain.

How can I find which libraries or what ever are not being installed? I will just do it manually so they just get skipped over. I accidentally stopped the script and restarted it and it says "Hit" instead of "Get", which i am assuming means they are already installed.

thanks

---

### Post by Luk8 on 2006-07-23
I just followed this script and after it's finished I restarted X , selected the XGL session and after 2-3 seconds I get a black screen and the X server restarts itself. I am using Kubuntu Dapper and I have a supported card: NV Geforce4 MX440 . I've seen others with the black screen + x restart problem , but no solution so far.Any tips ?

---

### Post by duartemolha on 2006-07-24
Hi after following the instructions I was able to set up xgk just fine but for some reason in some programs the keyboard is not configured properly.

It is correct when i write in programs such as gedit but in some other my keys for ~ ^* etc... do not seem to work

could this be a result of the xmodmap configuration?

I have a portuguese keyboard so I used xmodmap.pt

do you think it is something else?

Best regards

Duarte Molha

---

### Post by cptjaben on 2006-07-24
I seem to be having the same problem as LCC, in which there is no eye candy, i can't switch between workspaces, and all my windows don't have borders around them. I have a radeon 9700pro, anyone have suggestion?

Thanks,
cptjaben

---

### Post by rwabel on 2006-07-30
is there an easy way to undo the whole thing? xorg.conf and source.list is no problem, but there are the part Xgl() and Preferences()

---

### Post by jkwarras on 2006-07-31
> **rwabel said:**
> is there an easy way to undo the whole thing? xorg.conf and source.list is no problem, but there are the part Xgl() and Preferences()
I just did it a couple of days ago. Open the installation script file in text mode, and you'll see what's been installed and what files has beeen created. So, you know what to remove/delete.

---

### Post by nathandh on 2006-07-31
Thanks alot for this script, worked like a charm for Gnome. I'm a KDE user tho so if you could find the time it would be awesome to have a Kubuntu version aswell cause I don't manage to put it up manually =(

---

### Post by aum11 on 2006-08-01
Tried this last night on dell 9300 with ati x300.

Have lost GUI and am left with command line.

Advice please.

have backed out successfully using:

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

---

### Post by philipgm on 2006-08-24
For Nvidia users.

This script adds 

Section "Extensions"
Option "Composite" "Enable"
EndSection

to the xorg.conf file. This will break things and needs to be removed.


It has just taken me quite a bit of time to back this out and recover my original configuration. The script assumes that it needs to install nvidia-glx. In fact my card is supported by the nvidia-glx-legacy driver so I ended up back at the command line. Fortunately its the school holidays so I have a little time to spare.

---

### Post by srusso on 2006-08-24
I have a ATi 9700Pro and install was great but I try loggin in with XGL and it starts to load and srops back into the login screen... ???

---

### Post by Alexander_Corvinus on 2006-08-25
Your script runned succesfully but when I try to run the Xgl session it takes me back to the login screen after 5-6 seconds.
I have an Ati 9550.
Any ideas?

---

### Post by alexandermimix on 2006-08-25
why when I run this script is the first thing it talks about is VMware player? Like I installed VMware earlier on today however I have rebooted since then so I dont see the link between the two...


Anyway I installed it all anyways and have the same problem as reported above, just drops back to login screen after 10 seconds or so.

---

### Post by lordsavant on 2006-08-25
This script working beautifully on a MSI MS-1029 (ATI MRx700), and I had been trying to get XGL to work manually for awhile.  Thanks for the script!

---

### Post by Rainz3 on 2006-08-25
Well I installed the script and it worked pretty much perfectly. Only problems I had was the whole going brown after login the kicking me back to the login screen. To those who are having that problem. Do the script again. I reran the script and noticed it did some diffrent stuff the second time around and now it works great.

The only problem I am having now is I don't know how to change the settings and I dont have the windows border so I cant downsize or close the windows. Any thoughts? Also, I am trying to download compiz themes but I have no clue how to use them. Thanks for the great script(it also corrected my screen resolution problem :) :)) 

btw I am on acer travelmate 4400 with a mobile x700 and does this work on a geforce 4 ti 4600?

---

### Post by redhotone1 on 2006-08-28
I have an ATI 9600 and reran the script, however the screen still goes brown for 6 or 6 seconds then kicks me back to login screen. Any help would be greatly appreciated.

---

### Post by Frank Golden on 2006-08-29
> **redhotone1 said:**
> I have an ATI 9600 and reran the script, however the screen still goes brown for 6 or 6 seconds then kicks me back to login screen. Any help would be greatly appreciated.
Script don't work for me same problem as above poster. ATi card x1400.
Have a partimage backup of my original install so I can recover to before easily. Nice idea too bad it won't work for me.
I have been able to get xgl/compiz to work fairly well using a manual tutorial and have made a 
partimage copy of that install also so I can play with it and try to work out the bugs. The big problem with that one is an error
message at startup about display 1: that I can get around by typing ctrl+alt+F7. Would like to not have to type the key combo. I have my machine set to
autologon if that makes a difference. I am beginning to think that the "eye candy" just ain't worth the aggravation. My regular install works great.
Anybody seen this particular issue.

---

### Post by Sethro on 2006-08-29
Yeah I install it and I get a couple of errors like 

"cant find gset-compiz"

and "cant install ATI drivers- Access Denied"


Any help?

---

### Post by redhotone1 on 2006-08-30
I got most of XGL working, however, I dont have the close/maximise/minimise buttons and no screen wobble, no shutdown button either. 

Getting there slowly though.

---

### Post by muchtomydelight on 2006-08-30
i ran the script but i too get the 5-7 second brown screen and then back to gdm.  I am working on it.  rm ~/.config/autostart/compiz.desktop will get you started.  after doing that you should be able to log in.  when i run compiz --replace i see XGL for a frame or two and then back to gdm.  i also replaced gnome-window-decorator with cgwd.  probably a good idea. if i get it working i might try to fix the script.

---

### Post by rabid9797 on 2006-08-30
i get the 5-7 brown screen and then get kicked back to session login too.

im basically a newbie to xgl and such(only been using ubuntu for 2 months)

can someone explain to me what to do in laymen's terms?

thx

---

### Post by rabid9797 on 2006-08-30
also, i just started with a fresh copy of ubuntu, no driver installation besides the default ones that come for ATI. should i install the latest updates and 3d support for my drivers for this to work?

---

### Post by Frank Golden on 2006-08-30
Life is too short to play around with this
stuff. Xorg works fine without xgl-compiz 
I give up.

---

### Post by rabid9797 on 2006-08-30
weakling :rolleyes:

---

### Post by rabid9797 on 2006-08-30
i installed 3d support for my card fine, and ran the script again but got these errors:



xorg-driver-fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
fglrx
cp: target `' is not a directory: No such file or directory
Leaving `diversion of /usr/share/man/man1/Xserver.1x.gz to /usr/share/man/man1/Xserver.1x.gz.xgl by xserver-xorg-core'
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gset-compiz
mkdir: cannot create directory `/home/rabid9797/.config': File exists
mkdir: cannot create directory `/home/rabid9797/.config/autostart': File exists



so whats going on?

---

### Post by Frank Golden on 2006-08-30
> **rabid9797 said:**
> weakling :rolleyes:
Thank You! You must be a better man than I.:rolleyes:

---

### Post by rabid9797 on 2006-08-30
i still need a reply:(

---

### Post by rabid9797 on 2006-08-31
bump

---

### Post by Sethro on 2006-09-01
Okay Iam getting this error, when I try to log into XGL i got thrown back into the login screen.

cp: target `' is not a directory: No such file or directory
Leaving `diversion of /usr/share/man/man1/Xserver.1x.gz to /usr/share/man/man1/Xserver.1x.gz.xgl by xserver-xorg-core'
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gset-compiz

---

### Post by hvc123 on 2006-09-01
Hi All,

i have followed this and got it working perfectly with the script.
my machine is a dell precision 350 and ati x700.

the only problem i have is that DRI does not work if i do glxinfo i get this 

BrainStrain:~$ glxinfo | grep render
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: RADEON X700 Generic

i also cannot run fgl_glxgears because of this. other than that XGL runs Sweet. i patically like the wobbly windows and virtual desktop switch.

help please

---

### Post by mjpatey on 2006-09-04
I just ran the script.  I have an ATI Radeon 9200, and have tried installing XGL / Compiz before.

When attempting to log into an XGL session after running the script, I get about 10 seconds of very promising, brown "thinking" screen... followed by a return to the login dialog.  :-(

Has anybody been here and know what I should do?

Here's the rundown from the Terminal window during the running of the script.  There are a few errors... to save you the reading, here they are, from late in the script:

-------------

E: Couldn't find package gset-compiz
mkdir: cannot create directory `/home/mjpatey/.config': File exists
mkdir: cannot create directory `/home/mjpatey/.config/autostart': File exists

----------------

Here's the entire text of the script running:

[http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:3 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release [5405B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:5 [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Get:6 [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release [5405B]
Get:7 [http://en.archive.ubuntu.com](http://en.archive.ubuntu.com) dapper Release.gpg [189B]
Get:8 [http://en.archive.ubuntu.com](http://en.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Get:9 [http://en.archive.ubuntu.com](http://en.archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://en.archive.ubuntu.com](http://en.archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages
Hit [http://en.archive.ubuntu.com](http://en.archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://en.archive.ubuntu.com](http://en.archive.ubuntu.com) dapper-backports Release
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Get:10 [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages [ 12.7kB]
Get:11 [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages [12.7kB]
Hit [http://en.archive.ubuntu.com](http://en.archive.ubuntu.com) dapper/main Sources
Get:12 [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Sources [6880B]
Hit [http://en.archive.ubuntu.com](http://en.archive.ubuntu.com) dapper/restricted Sources
Hit [http://en.archive.ubuntu.com](http://en.archive.ubuntu.com) dapper/universe Sources
Hit [http://en.archive.ubuntu.com](http://en.archive.ubuntu.com) dapper-updates/main Packages
Get:13 [http://en.archive.ubuntu.com](http://en.archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Hit [http://en.archive.ubuntu.com](http://en.archive.ubuntu.com) dapper-updates/main Sources
Get:14 [http://en.archive.ubuntu.com](http://en.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Hit [http://en.archive.ubuntu.com](http://en.archive.ubuntu.com) dapper-backports/main Packages
Get:15 [http://en.archive.ubuntu.com](http://en.archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Hit [http://en.archive.ubuntu.com](http://en.archive.ubuntu.com) dapper-backports/universe Packages
Get:16 [http://en.archive.ubuntu.com](http://en.archive.ubuntu.com) dapper-backports/multiverse Packages [14B]
Hit [http://en.archive.ubuntu.com](http://en.archive.ubuntu.com) dapper-backports/main Sources
Get:17 [http://en.archive.ubuntu.com](http://en.archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Hit [http://en.archive.ubuntu.com](http://en.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://en.archive.ubuntu.com](http://en.archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 43.6kB in 1s (24.9kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Your system is now up-to-date.

~/Desktop/Downloadages
An installation for graphics cards from ATI will now follow.

Installing the fglrx driver from ATI.

Reading package lists... Done
Building dependency tree... Done
xorg-driver-fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
fglrx
cp: target `' is not a directory: No such file or directory
Leaving `diversion of /usr/share/man/man1/Xserver.1x.gz to /usr/share/man/man1/Xserver.1x.gz.xgl by xserver-xorg-core'
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gset-compiz
mkdir: cannot create directory `/home/mjpatey/.config': File exists
mkdir: cannot create directory `/home/mjpatey/.config/autostart': File exists



This scrip may have modified and backed up the following files: /etc/apt/sources.list and /etc/X11/xorg.conf.
Installation of Xgl, Compiz, several tweaks and possibly new drivers is now completed.
You can start Xgl and Compiz by selecting the Xgl X session in the GNOME Display Manager (the loginscreen).
Please reboot your computer and report your results.

---

### Post by lordsavant on 2006-09-04
@hvc123:

That message is normal because XGL uses the GL extensions.

---

### Post by pau on 2006-09-07
Hi,

i do have a radeon and your script just screwed my X... going back to the backup copy of xorg.conf doesn't help at all: After a few minutes X reboots and I get back to the login screen!

What can I do to "undo" the things your script modified?

I don't want to start from a scratch ubuntu installation :evil:

---

### Post by Sethro on 2006-09-09
could  somebody PLEASE upgrade the script!!!

Thanks](*,)

---

### Post by Sethro on 2006-09-10
I think the gset-compiz thing needs upgrading...

---

### Post by spacepimp on 2006-09-10
this automation did not work with nvidia geforce 6800 gs. it fails to start the session (no error message havent checked the log yet) but the session does appear on the list.

---

### Post by lordsavant on 2006-09-10
If you have recently run this script, compiz went thru some major changes and no longer uses gset-compiz.  It now uses csm.

You can get compiz to work after running this script, just do:

sudo apt-get install csm

sudo rm /usr/xsessions/Xgl.desktop

Then follow this guide:
[http://www.compiz.net/topic-389-1.html](http://www.compiz.net/topic-389-1.html)

from where it says "Make a startup script for xgl:" in the "second howto"

Good luck.

---

### Post by herot on 2006-09-10
> **lordsavant said:**
> If you have recently run this script, compiz went thru some major changes and no longer uses gset-compiz.  It now uses csm.

You can get compiz to work after running this script, just do:

sudo apt-get install csm

sudo rm /usr/xsessions/Xgl.desktop

Then follow this guide:
[http://www.compiz.net/topic-389-1.html](http://www.compiz.net/topic-389-1.html)

from where it says "Make a startup script for xgl:" in the "second howto"

Good luck.

i got this:

```

root@Armagh:/home/herot# sudo apt-get install csm
Reading package lists... Done
Building dependency tree... Done
Package csm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package csm has no installation candidate

```

---

### Post by Psycs on 2006-09-10
I was following the guide lordsavent linked to, and got the following trying to install the necesary packages:

> Fetched 3554kB in 1m7s (53.0kB/s)
Selecting previously deselected package compiz-core.
(Reading database ... 90175 files and directories currently installed.)
Unpacking compiz-core (from .../compiz-core_0.0.13.48-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-core_0.0.13.48-0ubuntu1_i3 86.deb (--unpack):
 trying to overwrite `/usr/bin/compiz', which is also in package compiz
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package csm.
Unpacking csm (from .../csm_0.10-0ubuntu1_i386.deb) ...
Selecting previously deselected package compiz-plugins.
Unpacking compiz-plugins (from .../compiz-plugins_0.22-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-plugins_0.22-0ubuntu1_i386 .deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libresize.so', which is also in package co mpiz
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package cgwd.
Unpacking cgwd (from .../cgwd_0.68-0ubuntu1_i386.deb) ...
Preparing to replace compiz-gnome 0.0.2-4ubuntu2 (using .../compiz-gnome_0.0.13. 48-0ubuntu1_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_0.0.13.48-0ubuntu1_i 386.deb (--unpack):
 trying to overwrite `/usr/share/gnome/wm-properties/compiz.desktop', which is a lso in package compiz
Preparing to replace compiz 0.0.2-4ubuntu2 (using .../compiz_0.0.13.48-0ubuntu1_ i386.deb) ...
Unpacking replacement compiz ...
Preparing to replace libglitz-glx1 0.5.3-0ubuntu2 (using .../libglitz-glx1_0.5.6 -0ubuntu1_i386.deb) ...
Unpacking replacement libglitz-glx1 ...
Preparing to replace xserver-xgl 7.0.0-0ubuntu4 (using .../xserver-xgl_7.0.0+cvs 20060625_i386.deb) ...
Unpacking replacement xserver-xgl ...
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-core_0.0.13.48-0ubuntu1_i386.deb
 /var/cache/apt/archives/compiz-plugins_0.22-0ubuntu1_i386.deb
 /var/cache/apt/archives/compiz-gnome_0.0.13.48-0ubuntu1_i386.deb
Running prelink, please wait...
E: Sub-process /usr/bin/dpkg returned an error code (1)


What happened? :-k

---

### Post by Psycs on 2006-09-11
Overall didn't have good results.  My specs are as follows: 

Dell 9400 laptop 
Core Duo T2300 @ 1.66Ghz
512 MB Ram
60 GB Hard Drive
17-inch WXGA+ (1440 x 900)
Nvidia GeForce 7800 Go - 256 MB

Twice I have managed to (apparently) install everything properly with the Script. But several seconds after I log into the XGL session, a black screen briefly appears and I am sent back to the login screen.

---

### Post by UbuntuniX on 2006-09-11
how helpful,
I just finished installing it manually :angry:

---

### Post by Sethro on 2006-09-11
Hi 


Could you possible update the script so that IDOITS like me can have a fool proof method of getting XGL running.. u know something that install drivers too 



Thanks

---

### Post by Psycs on 2006-09-11
Sethro, I am currently having better luck with the guide at wiki.ubuntu.com.  Just search for "xgl".

I am still having trouble with window borders, though.

Possible solutions discussed here:

[http://ubuntuforums.org/showthread.php?p=982459&highlight=window+border#post982459](http://ubuntuforums.org/showthread.php?p=982459&highlight=window+border#post982459)

I am thinking of installing compiz-vanilla and compiz-gnome-vanilla to see if it helps. 

Wish me luck!

---

### Post by Trip272 on 2006-09-12
I am having the same problem as the guy on page 11. Everything seemed to work great (I even got the nvidia splash screen now), however; when I start xgl by selecting it at the login I just get a black screen with a cursor.. after about 10 seconds it goes right back to login screen.

Any ideas? I'd love to get this up and working.

---

### Post by Sethro on 2006-09-12
I tried so many options but no luck. I have used this script before and everything was perfect! 



PLEASE PLEASE PLEASE!!!

Upgrade the script so that it works with the newer versions of XGL.


Thanks

---

### Post by Sethro on 2006-09-14
Guys come on !!! LOL

Could somebody update the script pretty please!

---

### Post by Groovie on 2006-09-16
So does anyone who has the Ati Radeon x700 MOBILE card running on fglrx drivers got this thing running? This is my seccond try to get it working but noooo..
The first time i followed a tutorial and got the same problem.

Problem:
As soon as i trie to load XGL the creen flickers and hang, then it goes back to the welcome screen. This happends every time i try.. ](*,)  :confused: 

Are there someone that can help me out there? 
I am fairly new to ubuntu (been running for 3weeks) so all help would be appriciated! :biggrin:

---

### Post by Sethro on 2006-09-16
We need a new script....


PLEASE!!!!

---

### Post by pantless on 2006-09-17
I don't know if anyone has had a result like mine with this script, or if its something with the packages...  when i ran the script it set everything up for xgl to work... but it didnt...:frown: 

so i set the GDMXsession timeout to 50 for xgl, no big deal...
i soon realize that compiz, cgwd, and xgl-session arent isntalled... i figured it was probably because of package versions changing...](*,) 

point is, i ran the script... then did a 
```
sudo apt-get install compiz compiz-gnome cgwd cgwd-themes xserver-xgl
```

now everything runs fine.  i still have to put
```
compiz
```
followed by a
```
cgwd --replace
```

:biggrin:  hope this helps someone that may have been in the same situation i was

---

### Post by 3rdalbum on 2006-09-17
There's a reason why there are no other scripts for getting Xgl and Compiz going on Ubuntu: Compiz changes so often, if your script gets out-of-date it can fail or mess up someone's install.

---

### Post by jman2807 on 2006-09-17
I installed using this script on an ati 9600xt and nothing seemed to work. However if I open a terminal and type compiz I get 

XGL Present

** (process:5054): WARNING **: bailing, couln't find a val for put_viewport_up in
[put]->a_put_viewport_up or
[put]->d_a_put_viewport_up

** (process:5054): WARNING **: bailing, couln't find a val for put_viewport_down in
[put]->a_put_viewport_down or
[put]->d_a_put_viewport_down


However compiz still loads. Then when i type cgwd --replace everything loads and works fine. I have to do this everytime i start xgl. Any ideas on how to fix this? Its kind of annoying having to keep the terminal open the entire time. Thanks in advance.

---

### Post by rretch on 2006-09-17
> **pantless said:**
> I don't know if anyone has had a result like mine with this script, or if its something with the packages...  when i ran the script it set everything up for xgl to work... but it didnt...:frown: 

so i set the GDMXsession timeout to 50 for xgl, no big deal...
i soon realize that compiz, cgwd, and xgl-session arent isntalled... i figured it was probably because of package versions changing...](*,) 

point is, i ran the script... then did a 
```
sudo apt-get install compiz compiz-gnome cgwd cgwd-themes xserver-xgl
```

now everything runs fine.  i still have to put
```
compiz
```
followed by a
```
cgwd --replace
```

:biggrin:  hope this helps someone that may have been in the same situation i was



say Pantless...the code you put up worked. Thanks a lot man!

for the curious:
My ATI 9600 card is working great w/XGL. I used the code posted -on first message of thread- followed by the posted code from Pantless. Didn't see the 9600 as 'supported', but it is in fact working.

rretch

---

### Post by pantless on 2006-09-18
im glad my script helped someone, but as soon as i did that.. and i mean 15 minutes after i wrote the reply to this thread compiz and all of that good stuff wanted an update.  reluctantly i did so hoping it wouldnt break it... it didnt break compiz, but it did break the water effects. does anyone know how to fix this?  when i try to do the rain effect the xserver just crashes and i have to do a ctrl+alt+backspace.

---

### Post by IDeus on 2006-09-18
I was hoping to get this running on my ASUS laptop (W3J). It has an ATI Mobility Radeon X1600. Will this handle this?

---

### Post by lordsavant on 2006-09-18
Groovie:

I have a MR x700 and XGL/Compiz works fine.  Just use the installation instructions at: [http://www.compiz.net/topic-389-1.html](http://www.compiz.net/topic-389-1.html)

Good luck.

---

### Post by smylie on 2006-09-23
> **herot said:**
> i got this:

```

root@Armagh:/home/herot# sudo apt-get install csm
Reading package lists... Done
Building dependency tree... Done
Package csm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package csm has no installation candidate

```

all the packages currently missing from the repositories can be found here:

[http://www.compiz.net/topic-4690-2.html](http://www.compiz.net/topic-4690-2.html)

cheers
Dave Smylie

---

### Post by Sethro on 2006-10-14
Does anyone here have a script that will automatically install the ATI FGLX drivers, I have been trying to do it manually but Iam just not having any luck at all...

Any recommendations


Many thanks

---

### Post by PaulEdwards on 2006-10-15
> **Sethro said:**
> Does anyone here have a script that will automatically install the ATI FGLX drivers, I have been trying to do it manually but Iam just not having any luck at all...

Any recommendations

Many thanks
There is one on the forum, but I don't recommend it.

I tried it yesterday on a friend's box and it didn't install properly and I had to spend an hour fixing it.
](*,)

---

### Post by Sethro on 2006-10-21
Could you give me the link?

IAM DIEING TO GET XGL working again !!!

---

### Post by joplass on 2006-10-25
Can someone help me with this output?  I have tried a few things here without success every time I lost my xserver.
Thanks,

An installation for graphics cards from ATI will now follow.

Installing the fglrx driver from ATI.

Reading package lists... Done
Building dependency tree... Done
xorg-driver-fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
fglrx
cp: target `' is not a directory: No such file or directory
Leaving `diversion of /usr/share/man/man1/Xserver.1x.gz to /usr/share/man/man1/Xserver.1x.gz.xgl by xserver-xorg-core'
Reading package lists... Done
Building dependency tree... Done
**E: Couldn't find package gset-compiz**
mkdir: cannot create directory `/home/job/.config': File exists
mkdir: cannot create directory `/home/job/.config/autostart': File exists



This scrip may have modified and backed up the following files: /etc/apt/sources.list and /etc/X11/xorg.conf.
Installation of Xgl, Compiz, several tweaks and possibly new drivers is now completed.
You can start Xgl and Compiz by selecting the Xgl X session in the GNOME Display Manager (the loginscreen).
Please reboot your computer and report your results.



job@job-ubuntu:~/Desktop$ sudo apt-get install gset-compiz
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gset-compiz
job@job-ubuntu:~/Desktop$

---

### Post by Sethro on 2006-10-26
I get the same output

---

### Post by YaseenKriel on 2006-12-19
how do i get my xserv back? the script totally ruined everything? this is what u get when u wanna do things the easy way.reminds me of the days when ppl downloaded virus from usenet, quite harmless until u execute the file and kiss your pc good bye.](*,)

---

### Post by FreakTech on 2006-12-31
I am having problems loading compiz  I am getting this error

```
cody@cody-laptop:~$ sudo apt-get install compiz compiz-gnome
Reading package lists... Done
Building dependency tree... Done
compiz-gnome is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-plugins (>= 0.2) but it is not going to be installed
E: Broken packages
cody@cody-laptop:~$

```

Anyone have any ideas.

---

### Post by pissedoffdude on 2006-12-31
> **FreakTech said:**
> I am having problems loading compiz  I am getting this error

```
cody@cody-laptop:~$ sudo apt-get install compiz compiz-gnome
Reading package lists... Done
Building dependency tree... Done
compiz-gnome is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-plugins (>= 0.2) but it is not going to be installed
E: Broken packages
cody@cody-laptop:~$

```

Anyone have any ideas.

are you using edgy? I think this howto is for dapper.  Take a look at this guide instead [http://ubuntuforums.org/showthread.php?t=263851]("http://ubuntuforums.org/showthread.php?t=263851").

---

### Post by mindstate on 2007-02-19
this script sucks ROYALLY..totally messed up my GDM Configuration and screwed up Gnome

pointless

---

