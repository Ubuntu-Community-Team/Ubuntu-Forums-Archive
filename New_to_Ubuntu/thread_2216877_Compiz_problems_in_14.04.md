---
title: "Compiz problems in 14.04"
date: 2014-04-14
forum: New to Ubuntu
---

### Post by fattyz on 2014-04-14
Hi I am running 14.04 in flashback mode with Compiz.  It works mostly but there are a few problems. The cube will rotate using the arrow keys but not using the mouse.  When I try to use mouse to rotate cube the original deskop deforms but then when I try to rotate the cube is not there, just the caps and the original desktop.  When I adjust the number of desktops in ccsm under general, the settings will not save.  The number of desktops goes back to the default setting.  Wobbly windows and water effect work fine.  Also, the compiz fusion icon will not appear in the panel.  If I try to start it nothing happens then I get a message that the cube had to close would I like to close it or try to restart it.  

I have worked my way through this before but don't remember how I did it.  I do not think it is the video driver because compiz worked fine in 10.04 on this setup.  It may or may not be relevant that the new appearence tab does not allow you to adjust desktop effects like the old one did in 10.04.

I know I mention more than one issue but I DO think they are related.  I was having this exact issue in 13.04 as well.

Thanks

---

### Post by fattyz on 2014-04-14
I got emerald working in this 14.04 install.  I stumbled on this thread by accident.  I had given up on having compiz and emerald in this newest revision.  Things are pretty unstable at this point and i'm hardly out of the woods but i've been working on this over a week now and I have to keep going.  This thread helped me install it.  

[http://ubuntuforums.org/showthread.php?t=2192044](http://ubuntuforums.org/showthread.php?t=2192044)

I found it would run by typing emerald --replace in terminal but then you have to leave the terminal open.  You can use the run dialoge which used to start with alt + F2, you have to install that as well.  I found out how to do it here.  

[http://askubuntu.com/questions/8925/command-to-launch-the-altf2-window](http://askubuntu.com/questions/8925/command-to-launch-the-altf2-window)

The fun never stops!

---

### Post by fattyz on 2014-04-15
This is a very good summation of what I have been doing.  Brings all the issues to the the table but sadly, no solution.  I know I'm getting close!  :  )

EDIT I thought I posted a link here I will look for it.

---

### Post by grahammechanical on 2014-04-15
This is just a thought. Do you have Workspaces enabled in Unity? System Settings>Appearance>Behaviour tab>Enable Workspaces.

The Appearance Utility now does some things that we needed Compiz Configuration Settings Manager to do in the past. One can override the other. By setting the Workspaces to 1 in CCSM, the Enable Workspaces option in Appearance gets overridden, in my experience. May be, not having Enable workspaces ticked in Appearance prevents those settings in CCSM from working. Just a thought.

Regards.

---

### Post by fattyz on 2014-04-15
Yes, thank you for your reply.  The same setting is available in flashback which I am running.  I think I found my answer here, [http://ubuntuforums.org/showthread.php?t=2087344](http://ubuntuforums.org/showthread.php?t=2087344).  It seem you can not have 3d windows enabled.  I know I never ran into this before when setting up compiz so I was surprised! 

I will search some more but for now this is working along with all the other effects in compiz AND emerald.  :  )  All things considered I am pretty happy.  I don't think I'll mark this solved quite yet as I want to do some more searching.  (otherwise I'll have to get back to real life) 

If I don't find anything else by this weekend I'll close the thread thanks again!

Yours

---

### Post by grumblebum2 on 2014-04-15
Hi fattyz,
I couldn't find emerald in the default repositories.
Installed using [**_[COLOR="#B22222"]this guide from noobslab[/COLOR]_**]("http://www.noobslab.com/2014/02/emerald-decorator-and-themes-available.html"). 

The guide was probably written early in the 14.04 beta.
You can no longer run emerald in the ubuntu/unity session because decorations are now handled by the unity compiz plugin 
and can't be replaced by emerald without disabling the unity plugin. The guide works for the compiz/flashback session though.

In the compiz flashback session enabling emerald works as before as the compiz unity plugin is not enabled in this session
and the decorations plugin can be used.

See [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2216168&p=12983739#post12983739") for setting workspaces in the compiz/flashback session.

---

### Post by fattyz on 2014-04-17
Yes I have it all working thanks.  The link I posted gives the code to install it.  There are some changes to Compiz like no additonal animations and I still can't get the Compiz fusion icon to appear in the gnome panel but, overall it's excellent. The issue with the workspaces resolved itself when I stopped trying to select 3D Windows. I still can't save the settings for number of desktops, but it is not having any effect on the cube.  I suppose I should try different settings but for now as long as it's working ...  Emerald is also working fine which is a real bonus.

Thanks for your reply.

Yours

---

### Post by Chanath on 2014-04-24
Cannot get desktop cube started in Flashback session. Doesn't react to any keybindings. Cannot save amount of desktops (4) in CCSM. 3D windows plugin is not ticked. How did you get the cube appear and rotate, fattyz?

---

### Post by Navneet_Kumar on 2014-04-24
I am having the same problem from the day i installed 14.04.....can anyone please help.......????

---

### Post by SkOrPn on 2014-06-22
I normally hate to revive a thread that becomes over two to three months old, but since it is only two months old and I am using all updated software I feel compelled to warn others about my experience last night with Ubuntu 14.04 LTS and Compiz. Oh and yes I know this thread seems focused about Flashback, Compiz and 14.04 but a Google search will bring you here if your looking for info about Compiz and 14.04 none the less. So it's relevant that I comment... 

In the "Effects" tab of Compiz, DO NOT even think about clicking on the "Windows Decoration" icon. At first it appears that it may be working, but there may be some things that makes you believe you need to uncheck it and recheck it and that event alone caused me 2 or 3 hours of my life last night. Everything on the desktop disapeared and none of the shortcuts were working, not even Ctrl-alt-del or ctrl-alt-t". I still had the Wallpaper and a cursor, and the cursor was functional, but that was about it. I could right click, yay. It took me a while to realize that the keyboard short to Virtual Terminal was still functional, and that let me fire up Firefox so I could research on how to use the Virtual terminal to fix the main terminal and that finally led to me figuring out how to set the compiz defaults back to active. Unfortunately, and although I been jabbing at Linux here and there for 15 years, I just do not have enough knowledge about terminal commands or keyboard commands as I would like, so hours passed, as I tried and tried to get it fixed without a re-install. I won eventually.

I have a fresh Ubuntu 14.04 LTS with all updates, and the latest Compiz installed. However, I am not touching it again, lol... Wobbly Windows works and Water affect did not seem to change a thing, or at least I do not see anything different... I am not willing to try any other features of it.

To say the least, Compiz on Trusty, is NOT very Trusty... lol

EDIT: Quick question, is the Emerald manager a plugin for Compiz? and if so is that why my machine fell apart when I clicked on the Windows Decoration icon? If so, maybe I should try installing Emerald before complaining about Compiz breaking my computer, lol... I guess I didn't realize some of those icons required plugins to be installed beforehand.

---

### Post by grumblebum2 on 2014-06-22
Had you updated after installing?
I have encountered your problem in the past but as of now ccsm will
give me warnings about conflict and a disable option for the unity or window decorations plugin.

Also if you switch to a tty to fix a messed up unity you can run...
```
DISPLAY=":0" dconf reset -f /org/compiz/ && setsid unity
```

Sometimes I find the **setsid unity** command fails to reload compiz properly
and may be simpler from tty1 to just reset compiz and then reboot...
```
DISPLAY=":0" dconf reset -f /org/compiz/
sudo reboot
```

---

### Post by SkOrPn on 2014-06-22
> **grumblebum2 said:**
> Had you updated after installing?
I have encountered your problem in the past but as of now ccsm will
give me warnings about conflict and a disable option for the unity or window decorations plugin.

Also if you switch to a tty to fix a messed up unity you can run...
```
DISPLAY=":0" dconf reset -f /org/compiz/ && setsid unity
```

This might have come in handy about 5 hours ago lol, but I tried installing Emerald and when I clicked on the Windows Decorations it hosed my Ubuntu installation completely this time. I couldn't even get back into my Windows installation. Ubuntu Live USB could not fix it and all the standard terminal options for repairing or defaulting compiz failed in tty.

I'm back in Windows for now and will give Ubuntu another go when I have a drive to install it on. All I have right now to install it on are two old 30gb SSD's and those are two small, unless of course I give Ubuntu software RAID a try and I'm not sure I am ready for that level of sudo'ing just yet, lol...

---

### Post by grumblebum2 on 2014-06-22
None of my installs are using more than 15GB.
Most are less than 10GB.

Could also install Home on one SSD and "/" on the other?

---

### Post by cwmoser on 2014-06-23
I installed Emerald and the associated themes on my 14.04 Ubuntu installation and it worked fine.
I did the install choosing Metacity located on the log on screen, did the installation, logged off
and then back in choosing Compiz.  I don't use Unity - instead I use Gnome flashback.

Carl

---

### Post by SkOrPn on 2014-06-24
> **cwmoser said:**
> I installed Emerald and the associated themes on my 14.04 Ubuntu installation and it worked fine.
I did the install choosing Metacity located on the log on screen, did the installation, logged off
and then back in choosing Compiz.  I don't use Unity - instead I use Gnome flashback.

Carl
Can you explain what the advantages are with Gnome Flashback over Unity or Gnome 3?

I think what I want for a daily OS, is Emerald, Wobbly windows, snapping windows, Conky, and possibly Cairo all working together, but like I said I can never make it to the end of my customizing without my system breaking on me. I wonder if I could get all this to work on Ubuntu Gnome Flashback 14.04? However, I think I read Flashback does not work on Gnome 3.10?

Is Unity and Gnome3 just incompatible with all these mods on 14.04? Is that why both keep breaking on me every time I try to use them as a base to my custom distro setup? Is Flashback necessary to run all these mods?

Can it be my hardware? lol

---

### Post by grumblebum2 on 2014-06-24
If you have installed cairo-dock you should have a cairo-dock session using compiz as the window manager.
You should not see unity in this session.
If you do, use ccsm to disable unity and enable window decorations.
If you want to use emerald as the decorator add the following as shown in pic...
```
emerald --replace &
```

Unity, gnome-shell, gnome-flashback lxde and xfce are all desktop environments that run on top of Gnome3.

Basicaslly they differ in what applications are installed as default.
Panel, text editor, web browser, file browser, screensaver , window manager, music applications etc etc.
Conky should run fine in any session.

eg
Logging into the **ubuntu** session, disabling the unity plugin, enabling window decorations
and running cairo-dock would be much the same as logging in to the **cairo-dock** session.

---

### Post by fattyz on 2014-08-07
Guys I am so sorry I have not looked back here in all this time.  The truth is I don't remember how I did it.  This always happens when I run Ubuntu, I get it all up and going and when I crash it finally I forget how I did all that and then I start searching and it comes back to me.  I had the same problems with not saving the number of desktops and I couldn't get the cube to work.  I am so sorry because I know it is as frustrating as hell!!  If you want specific settings or anything like that just post here or email me and I'll give you whatever I have.  I have it working except skydome won't display properly. I am looking back through my old posts if I find anything I'll link it.  I hope you have it working by now!

Yours

---

### Post by fattyz on 2014-08-12
I shut off tweak tool and everything is working ok.  I posted this in another thread that was particular to skydome.  Here are a couple pics.  I hope all is well with everyone.  I am still not sure I am getting all the 3D rendering I should in these images but before I shut off tweak tool it was really 2D.  Almost like a drawing.  I don't know for sure how it works but it looks much better now.  

Yours

---

### Post by fenario on 2014-09-26
Hi compiz lovers
FattyZ it's a good idea to keep a change log diary. I can always find my tweaks again that way.
Fusion Icon never workded for me but I found this neat app:
[http://sourceforge.net/projects/displex/files/displex-0.7.2/](http://sourceforge.net/projects/displex/files/displex-0.7.2/)
this is "A unifying AppIndicator.
Integrates applications that configure display settings."
Copyright © 2011 Arick McNiel-Cho
my diary shows following entries:
------------------------------------------------
installing displex for compiz
Setting up python-central (0.6.17ubuntu2)
from precise repos
Setting up libappindicator1 (12.10.1+13.10.20130920-0ubuntu4) ...
Setting up python-appindicator (12.10.1+13.10.20130920-0ubuntu4)
Setting up indicator-displex (0.7.2)
Setting up indicator-applet-complete (12.10.2+14.04.20140403-0ubuntu1) ...
Setting up indicator-application-gtk2 (12.10.0.1-0ubuntu2)
Setting up disper (0.3.1-1)
didn't work
in /usr/share/indicator-displex/indicator-displex.py
disabled lines: 1071 - 1079 and 1091 - 1113
this works now
Setting up fusion-icon (0.1.0-2ubuntu1) from precise
still not working!
Removing fusion-icon (0.1.0-2ubuntu1)
Displex replaced it
---------------------------
created autostart for indicator-displex
------------------------------------------------------
Setting up libemeraldengine0 (0.9.5-0~webupd8~saucy2) ...
Setting up emerald (0.9.5-0~webupd8~saucy2)
-------------------------------------------
changed window decorator in compiz from:
/usr/bin/gtk-window-decorator to emerald --replace
------------------------------------------------------------------------
Trusty is a nightmare to tweak; a lot of options we had in precise are not possible any longer
so I'm still using Precise.
------------------------------------
But still, in Trusty I got my 4 C's working
Gnome Flashback (old Classic), Conky, Compiz and Cairo-Dock
I replaced nautilus with nemo which has better options and still has the:
" up to parent folder" option
plus some other tweaks made Trusty quite useful.

---

