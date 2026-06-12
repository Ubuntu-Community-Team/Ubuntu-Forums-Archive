---
title: "HowTo: Reconfigure X with “dpkg-reconfigure xserver-xorg”"
date: 2008-02-07
forum: Outdated Tutorials &amp; Tips
---

### Post by Rocket2DMn on 2008-02-07
This HowTo Guide is primarily for users who cannot get into the GUI after a fresh install, a dist-upgrade, a new video card install, or a video driver upgrade, and for users who cannot set their screen resolutions correctly from within the GUI.  It is designed to be easy to use without being overly simplistic.

[SIZE="3"][COLOR="red"]UPDATE:[/COLOR][/SIZE]  This method **does not** work with *Hardy Heron* and probably all versions to follow (including Intrepid Ibex).  This method seems to ONLY work with *Gutsy Gibbon* and older.
I think this is because the newer versions of xserver-xorg rely more on auto-detecting the configuration during runtime rather than looking at xorg.conf.
[SIZE="3"][COLOR="red"]/UPDATE[/COLOR][/SIZE]

[SIZE="3"] **Step 1: Get to the terminal**[/SIZE]

1a) [COLOR="Green"]If you are already in the GUI.[/COLOR]
For Gnome and Xfce: Applications->Accessories->Terminal
For KDE: KMenu->System->Konsole

1b) [COLOR="Red"]If you are NOT in the GUI (maybe you have a blank screen after boot-up)[/COLOR]
Do CTRL+ALT+F1 to get to a tty, and login with your username and password.  Then depending on your desktop environment, run
For Gnome (Ubuntu):
```
sudo /etc/init.d/gdm stop
```
For KDE (Kubuntu):
```
sudo /etc/init.d/kdm stop
```
For Xfce (Xubuntu):
```
sudo /etc/init.d/xdm stop
```

[SIZE="3"] **Step 2: Run the reconfiguration**[/SIZE]

First start by making a manual backup (even though one will be auto-generated in the form *xorg.conf.YearMonthDayTime*):
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
Now run the configuration:
```
sudo dpkg-reconfigure xserver-xorg
```
***Details:***
--You will be asked a bunch of questions about your hardware, do your best to answer.  If you don&#8217;t know the answer, take an educated guess or use the default selection.
--When asked about video drivers, select &#8220;ati&#8221; if you have an ATI card, &#8220;nv&#8221; if you have an Nvidia card, or &#8220;intel&#8221; if you have an onboard Intel graphics card.  Otherwise select &#8220;vesa&#8221; &#8211; this is more of a fallback driver if the other options don&#8217;t work, it is useful to select this to get into the GUI initially, then install the propriety drivers if needed (step 4).
--When asked about screen resolutions, use TAB to move and SPACEBAR to select your monitor&#8217;s max resolution and everything less.

Once the questions are finished, you may proceed.

[SIZE="3"] **Step 3: Restart the GUI**[/SIZE]

3a) [COLOR="Green"]You are currently in the GUI, so restart X with CTRL+ALT+BACKSPACE[/COLOR]

3b) [COLOR="Red"]You are in a tty, so run[/COLOR]
For Gnome (Ubuntu):
```
sudo /etc/init.d/gdm start
```
For KDE (Kubuntu):
```
sudo /etc/init.d/kdm start
```
For Xfce (Xubuntu):
```
sudo /etc/init.d/xdm start
```

[SIZE="3"] **Step 4: [COLOR="Blue"](OPTIONAL) Setup Proprietary Drivers**[/COLOR][/SIZE]
This is for users whose cards do not have full support with the open source drivers.  Nvidia users tend to use this more, but newer ATI cards also need them.
See links for details on card compatibility.

[Installing Nvidia propriety drivers]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")
[Installing ATI propriety drivers]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

[Details on ati/radeon open source drivers]("https://help.ubuntu.com/community/RadeonDriver")

If something doesn&#8217;t work out correctly and you want to recover your previous configuration for X, then restore your backup:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
Then restart X.

Please do not post help questions on this thread, start a new thread on the [Absolute Beginner&#8217;s Forum]("http://ubuntuforums.org/forumdisplay.php?f=73") instead.  Suggestions, reviews, and critique are certainly welcome.

Keywords: can&#8217;t login, broken X, no login screen, blank screen, low or wrong resolution, new video card

---

### Post by jaya28inside on 2008-02-21
sorry

but i hope this could help me out.... 
sigh... i have an onboard card
and it's poor quality 
but then Ubuntu cant' detect it?? so it's appeared blank?

OMG.... help me...!!

---

### Post by jaya28inside on 2008-02-21
and the blank screen was appeared after i choose it
from the Boot Logon...

then BANG!
blank...no other loading or someting else

but after few days.. it happened working OK
suddenly a few hours i restart it again.. .same problems happened...
it's appeared BLANK again :( hiks

---

### Post by komputes on 2008-03-04
I have usually used the following to reconfigure xorg when the screen did not work properly (such as booting into a black screen).

Press ESC at Grub prompt and select RECOVERY MODE

```
dpkg-reconfigure -phigh xserver-xorg
```This would usually ask me a series of questions concerning my video card, resolution, driver etc. 

Removing "-phigh" from the command added a lot more questions concerning the keyboard.

Until recently when I ran that command on a new computer using hardy. -phigh did not work at all and taking it out allowed me to configure they keyboard but does not ask me to configure video (which is what I want to configure). I got the following error:

xserver-xorg postinst warning: overwritting possibly customized configuration   file: backup in /etc/X11/xorg.conf.20080203121105

Any Tips? Currently using Intel Mobile VGA GM965/GL960 (Rev3) on Ubuntu Hardy 8.04 alpha5, but I have also seen this when trying to reconfigure an ATI Radeon 9200.

---

### Post by Rocket2DMn on 2008-03-04
"xserver-xorg postinst warning: overwritting possibly customized configuration file: backup in /etc/X11/xorg.conf.20080203121105" - is not an error.  This is normal, it is making a backup of your old xorg.conf and putting the new one in its place.  Backups are made automatically in the format xorg.conf.YearMonthDayTime
If you need specific help with cards, please start a new thread and somebody will be glad to help you out there.  Remember that Hardy is still in alpha, and you will need "intel" driver for the onbard graphics and "ati" open source driver for the 9200.

---

### Post by komputes on 2008-03-04
I completely understand that this is not an error. I expected to be able to select my video driver with this command. What I experienced is that this command skipped right over the part where it asks questions about the video driver and monitor refresh rates etc. How do I get to that screen?

---

### Post by Rocket2DMn on 2008-03-04
That command without phigh should ask about video drivers and screen resolutions.  By default it should be asking low priority questions as well, but you can double check by using the "-plow" flag with the command.  Otherwise, I need to see your xorg.conf file:
```
cat /etc/X11/xorg.conf
lspci | grep VGA
```

---

### Post by komputes on 2008-03-04
I have tried this at all prority levels and none of them asked be video driver or monitor related questions. I ended up rewriting my xorg.conf file and it seems to work in low resolution now.

The good side: I got to familiarize myself with xorg.conf (once again) yaaay!

The bad side: There is no way for my grandmother to do this. Bring back the config! ;p

---

### Post by Rocket2DMn on 2008-03-04
OK, why don't you make a manual backup of the working xorg.conf file just in case:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

---

### Post by komputes on 2008-03-05
> **Rocket2DMn said:**
> OK, why don't you make a manual backup of the working xorg.conf file just in case:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```


Doesn't solve lack of auto-configuration or user-interactive configuration.

---

### Post by Rocket2DMn on 2008-03-05
> **komputes said:**
> Doesn't solve lack of auto-configuration or user-interactive configuration.

No, it doesn't, but there isn't anything we can do about that except wait for better interfaces (Gutsy was a major improvement, hopefully Hardy will be, too).

---

### Post by JohnMac on 2008-03-06
I have(had) UBUNTU running in a virtual drive with WindowsXP  as a host. I tried this procedure to get my UBUNTU screen size correct, although When I closed nothing seemed to have changed - all so I thought.

When next I started up windows, it would not boot, not even in safe mode.  I will use by rescue disk to save all my data, including my Ubuntu files, but it seems my little experiment to share Linux and Windows on one PC is over.

My new plan is to run XBUNTU on an old PC I have , That way I will keep my Wife and kids off my back.

---

### Post by Rocket2DMn on 2008-03-06
Reconfiguring X won't screw up your windows, that had to have been something else.
You can try setting up a dual boot rather than using a VM.

---

### Post by ynnhoj on 2008-03-26
> **komputes said:**
> What I experienced is that this command skipped right over the part where it asks questions about the video driver and monitor refresh rates etc. How do I get to that screen?
i've been having the exact same problem!  this is god awful -- i can't deal with 800x600.  and since *xorgconfig* isn't packaged into ubuntu, i can't fall back on that either.

---

### Post by Rocket2DMn on 2008-03-26
> **ynnhoj said:**
> i've been having the exact same problem!  this is god awful -- i can't deal with 800x600.  and since *xorgconfig* isn't packaged into ubuntu, i can't fall back on that either.

First check - you're NOT using Hardy Heron, right?  I found recently that this method does not work with Hardy, so I need to update my original post to note that (thanks for the reminder).  The version of X in Hardy relies on more auto-detection than xorg.conf, which can be convenient if it works, but annoying if you have problems.
Second, you're NOT using the -phigh flag, right?  Using that forces it to autodetect.
You should be starting a new thread to troubleshoot this, but since you're already here, what is your video card?  Also post your xorg.conf
```
lspci | grep VGA
cat /etc/X11/xorg.conf
```

---

### Post by ynnhoj on 2008-03-26
> **Rocket2DMn said:**
> First check - you're NOT using Hardy Heron, right?  I found recently that this method does not work with Hardy, so I need to update my original post to note that (thanks for the reminder).  The version of X in Hardy relies on more auto-detection than xorg.conf, which can be convenient if it works, but annoying if you have problems.
Second, you're NOT using the -phigh flag, right?  Using that forces it to autodetect.
You should be starting a new thread to troubleshoot this, but since you're already here, what is your video card?  Also post your xorg.conf
```
lspci | grep VGA
cat /etc/X11/xorg.conf
```
i have an onboard geforce2 card; in my experience, it doesn't play nice with the nvidia driver, so i normally use the more generic *nv* driver ('xf86-video-nv').

i didn't realize that hardy relied so heavily on auto-detection as to deny a user access to configuring things themselves (aside from writing yer own xorg.conf).  if my only option is to type up an xorg.conf file myself, i'll probably just install arch again.  i thought i'd see how ubuntu's come along since i last used it (edgy, i think) and this was a bit of an unpleasant surprise.  note: i've always had problems with ubuntu figuring out my screen resolution on this machine, but that was fine since up until now it's been easy to fix.

---

### Post by Rocket2DMn on 2008-03-26
Yeah, Hardy is still Testing for a few more weeks though, hopefully X will be a little better when they release Hardy as stable in April (I should hope so, it's an LTS release).  I found the manually editing xorg.conf didn't work very well in Hardy either. 
I will be sure to find out more details about working with X in Hardy since I help a lot of users troubleshoot X.

---

### Post by ynnhoj on 2008-03-26
i appreciate the help -- i just can't believe the doing a reconfig on xorg, which used to be so simple, has become so problematic!  ah well, hopefully this is just a bug which will be fixed in time for the release..?

---

### Post by Rocket2DMn on 2008-03-26
Doubtful, I think that is the direction they are trying to go with X, though I wish they would have an override option for those of us with cards that have less support :(
If I get around to writing a HowTo for doing this in Hardy, I will post a link from this thread, but until then, we're stuck.

---

### Post by komputes on 2008-03-27
ynnhoj, I would ask you to please voice your opinion on the bug which I have created concerning this issue. Your opinion is appreciated. I really hope we can make them change this before the final Hardy comes out 28 days from now.

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/207409](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/207409)

As well, since in your case you do get 800x600 access to GDM, please try running displayconfig-gtk as a user-interactive method for configuring xorg.conf

---

### Post by goohman on 2008-03-29
when i boot i hear the drums and do the ctrl+alt+f1 thing and login in but none of the commands can be found.

I typed in "sudo /ect/init.d/gdm stop"

"command /ect/init.d/gdm" cannot be found"

or something like that

---

### Post by Rocket2DMn on 2008-03-30
The path is "/etc/init.d/gdm stop" not "ect".  Also, gdm won't work if you're not using Gnome (standard Ubuntu install).  You use kdm if you have Kubuntu and xdm if you have Xubuntu.

---

### Post by goohman on 2008-03-30
> **Rocket2DMn said:**
> The path is "/etc/init.d/gdm stop" not "ect".  Also, gdm won't work if you're not using Gnome (standard Ubuntu install).  You use kdm if you have Kubuntu and xdm if you have Xubuntu.

Oops :oops:

I i got it to work, i didnt know alot of the questions especially the port one since it was connected to mobo. so i used escape.

but i downloaded the restricted driver that poped up onscreen and i now get full resolution ^_^ thanks!:lolflag:

---

### Post by ynnhoj on 2008-03-31
> **komputes said:**
> As well, since in your case you do get 800x600 access to GDM, please try running displayconfig-gtk as a user-interactive method for configuring xorg.conf
hey, that's a handy little tool that i didn't even know existed!  thanks for the tip -- i'm back to good ol' 1280x1024, and lovin' it!  it seems that my display wasn't detected properly (it's just a samsung syncmaster, but maybe it's a weird model...?).

---

### Post by Rocket2DMn on 2008-03-31
> **ynnhoj said:**
> hey, that's a handy little tool that i didn't even know existed!  thanks for the tip -- i'm back to good ol' 1280x1024, and lovin' it!  it seems that my display wasn't detected properly (it's just a samsung syncmaster, but maybe it's a weird model...?).

That is the same as going to System->Administration->Screens and Graphics

---

### Post by ynnhoj on 2008-04-01
heh, i figured that out a few hours after my last post :o

i haven't used ubuntu since edgy -- this must be a new tool?

---

### Post by Rocket2DMn on 2008-04-01
I think it is new with Gutsy, they use it in Hardy, too.

---

### Post by blindhog on 2008-09-01
If anyone is still having issues with this in Hardy Heron, try this command

```
gksu displayconfig-gtk
```

Then you can try to restart X with ctrl+alt+bksp , restart or powerfail completely. 

I power failed my machine and it came back with correct resolution. Rebooting or restarting X might work. I am so wiped right now, I am confused as to what fixed it. What a freaking mess...:mad:

---

### Post by WitchCraft on 2008-12-09
> **Rocket2DMn said:**
> "xserver-xorg postinst warning: overwritting possibly customized configuration file: backup in /etc/X11/xorg.conf.20080203121105" - is not an error.  This is normal, it is making a backup of your old xorg.conf and putting the new one in its place.  Backups are made automatically in the format xorg.conf.YearMonthDayTime
If you need specific help with cards, please start a new thread and somebody will be glad to help you out there.  Remember that Hardy is still in alpha, and you will need "intel" driver for the onbard graphics and "ati" open source driver for the 9200.

I had this when I couldn't set the screen resolution. It remaind at 600x800...

Neither dpkg-reconfigure nor -phigh worked.

To do it manually:

apt-get install xresprobe

xresprobe -n



make a backup of xorg.conf:
```

cp /etc/X11/xorg.conf /etc/X11/xorg.backup.conf

```

Then edit the xorg config file:
sudo gedit /etc/X11/xorg.conf

Look out for these sections:
```

Section "Monitor"
        Identifier      "Configured Monitor"
        DisplaySize     376 301
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
EndSection

```


And change them to this:
```

Section "Monitor"
        Identifier      "Configured Monitor"
        DisplaySize     328 248
        HorizSync       30-85
        VertRefresh     50-120
EndSection




Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768"
        EndSubSection
EndSection

```

Get the values for hsync and vsync via:
```

xresprobe -n

```
and get the available modes via
```

fbset -x

```



[http://wiki.ubuntuusers.de/XServer](http://wiki.ubuntuusers.de/XServer)

---

### Post by Rocket2DMn on 2008-12-09
This HowTo is outdated now, it doesn't really apply to Hardy, Intrepid, or Jaunty (testing) - the newer X servers rely more on autodetection than they used to.  These days, this method is mostly only useful to resetting a manually configured xorg.conf or one that was modified by restricted drivers, which can be useful after a kernel upgrade in which the restricted drivers were not recompiled after the update.

---

### Post by arjanhs on 2009-01-05
Is there already an updates version available, cause my 8.10 version with a Intel Corporation Mobile GM965/GL960 chipset isn't working with compiz.

Arjan

---

### Post by Rocket2DMn on 2009-01-05
Arjan, this guide is outdated and doesn't apply to Hardy or Intrepid (though in some cases, it may work).  The primary purpose of this guide was to get users into a graphical session, not enable compiz.  You should create a new thread in one of the primary support forums, like Absolute Beginner Talk, General Help, or Desktop Effects & Customization.  Good luck.

---

### Post by chepe263 on 2009-04-11
In the most easy way just type new values on xorg.conf

Make a backup copy first. Then run in terminal (konsole or gnome-terminal) sudo nautilus (or your prefered file browser) and go to /etc/X11/ make copy of xorg.conf find this part

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

and change 
		Virtual	640	480
		Modes		"640x480@60"

to

		Virtual	1024	768
		Modes		"1024x768@60"

save changes and resar X (ctrl+alt+shift+backspace) and your screen resolution change

This make the screen resolution from 640x480 to 1024x768, make sure you are writing real values and make a copy of the xorg.conf file again to have another backup

if it doesn't work copy backup to /etc/X11/ again (using windows with ext2 driver if it is possible)


chepe263

Spanish users, write me and i will explain you in spanish
(Usuarios que hablan español, escribanme y les explico en español)

[http://twitter.com/chepe263](http://twitter.com/chepe263)   ):P

by the way, i'm using ubuntu 8.04 with kde

---

### Post by Holmes245 on 2010-05-06
I hate to say it but this and a lot of other problems like this is the reason Linux will never be the more popular OS over Windows or Mac.

---

### Post by chepe263 on 2010-05-06
> **Holmes245 said:**
> I hate to say it but this and a lot of other problems like this is the reason Linux will never be the more popular OS over Windows or Mac.

Well, this is the reason why we (the ubuntu users and linux users in general) have more 'cojones' than MacOSX and Windows users. Plus, there's a reward. We are no longer afraid to windows viruses.

Who's with me?:guitar:

---

### Post by tamashumi on 2010-11-03
Well yea I guess so. But I prefer to use them other, more pleasure way ;)

---

