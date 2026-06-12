---
title: "installing VLC"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by yuva3d on 2008-05-18
can any one tell me how to install VLC player on Ubuntu - i am new to Linux.... any how i install Ubuntu in my pc. now i cant able to watch clips and listing audio  

solution are great appreciated.

---

### Post by vishzilla on 2008-05-18
in the terminal enter ```
sudo apt-get install vlc
```

---

### Post by Xiong Chiamiov on 2008-05-18
In the teach-a-man-to-fish vein, [here's a guide on how to install things in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by zvacet on 2008-05-18
If you still runing Ubuntu from live CD then folow [this]("http://psychocats.s465.sureserver.com/ubuntu/installing") guide to install it.Once you install Ubuntu go to the system>admin>software sources<check all under Ubuntu software and updates tab.Reload.After that applications<accessories>terminal and type

```
sudo apt-get install ubuntu-restricted-extras
```

Now go to the link **Xiong Chiamiov** posted to you.

---

### Post by yuva3d on 2008-05-18
Great thanks to you all:guitar:

---

### Post by ubunu on 2008-05-18
Please post here if you manage to find a simple way of making it the default player for music & DVD!

---

### Post by MrWES on 2008-05-18
Goto: System | Preferences | Removable Drives and Media

Enter the following for Audio CD:

```
/usr/bin/vlc
```

And the following for DVD:

```
/usr/bin/vlc dvd://
```

Bill

---

### Post by Bradtek on 2008-05-18
"Goto: System | Preferences | Removable Drives and Media"

I dont see Audio CD or DVD there (Ubuntu 8.04)
Only
Cameras |PDAs |Printers & Scanners |Input Devices (Mice/Keyboards/Tablets)

---

### Post by ubunu on 2008-05-18
If only it were that simple

[http://ubuntuforums.org/showthread.php?t=791436](http://ubuntuforums.org/showthread.php?t=791436)

[http://ubuntuforums.org/showthread.php?t=713724](http://ubuntuforums.org/showthread.php?t=713724)

---

### Post by mc4man on 2008-05-18
> simple way of making it the default player for music & DVD!
By far the easiest way for _dvd_ is from terminal
```
gksudo gedit /etc/gnome/defaults.list
``` near bottom change this line _x-content/video-dvd=totem.desktop_ to _x-content/video-dvd=vlc.desktop_, save.(ie. just replace totem with vlc )

Now right click on Applications -> edit menus -> highlight sound & video and on the r. side box right click on vlc -> properties. Change the command to this

```
vlc %f
```

 
This assumes you haven't edited other files like mimeapps.list

To switch default choices enable file management in preferences (edit menus)
If you install totem-xine to make that default over totem-gstreamer
```
sudo update-alternatives --config totem
``` and choose 2

or to keep *totem-gstreamer as default totem player* but add totem-xine as a choice for dvd play back see edit in thread linked below

edit : one word of warning about defaults.list
Any one line can be edited safely once per app and only with <app>.desktop, don't ever use commands in there or try switching apps back and forth on one particular line. Multiple editing of the same line, repeating an app a couple of times can produce unexpected results. 

For other players (non kde apps) see here under replace .desktop (replace mplayer with other name if desired

[http://ubuntuforums.org/showthread.php?p=5633803#post5633803](http://ubuntuforums.org/showthread.php?p=5633803#post5633803)

---

### Post by Sirchristopher on 2008-06-01
I have deleted VLC and re installed it but I can't find it to add it back to my menu.

---

### Post by Sirchristopher on 2008-06-02
I fixed it.

---

### Post by kaligus on 2008-06-22
I just finished following the instructions in this thread on a friends XP box with ubuntu 8.04 running under virtualbox (a slow convert who wants to try it b4 he doesn't buy it).

Prior to following the instructions to make VLC the default for DVD playback all is good, Totem plays DVDs just fine, no amount of coaxing and cajoling can get VLC to even pretend to play anything at all.

Anyone have an idea what I missed and where?

(VLC with these instructions works fine on my dual boot box so I assume either a typo or something I dont grok with virtualbox etc.)

FWIW I also tried using the gconfig-editor to change it on the vbox machine *prior* to trying the defaults.list gedit with no luck. (reverted before trying gedit, powered down and restarted the vbox between everything because I know vbox has issues with his USB DVD drive)

---

### Post by mnkpx7 on 2008-07-08
I just upgraded my system to 8.04 and couldn't get vlc to work.  A friend had me run sudo apt-get uninstall vlc, apt-get purge vlc, and apt-get install vlc.

After doing this, I get "E: Package vlc has no installation candidate"

What can i do?

---

### Post by oldos2er on 2008-07-09
> **mnkpx7 said:**
> I just upgraded my system to 8.04 and couldn't get vlc to work.  A friend had me run sudo apt-get uninstall vlc, apt-get purge vlc, and apt-get install vlc.

After doing this, I get "E: Package vlc has no installation candidate"

What can i do?

 Check your Software Sources (System, Administration) to make sure all repositories are enabled.

---

### Post by outerspacerace on 2008-08-28
Sorry for the lack of detail, though I'm at work now... 

I edited my lists file to make VLC the default player for DVD/VCD and was told I didn't have permission to do so. From memory there was one or two other things I couldn't do for that reason also.

I am just using the user name I set up upon install - do I need to add it to an admin group or something similar to enable such rights?

I've tried making myself a root and admin user without much luck.

---

### Post by Elephantman5 on 2008-09-03
I'm just wondering why you changed the launcher command to vlc %m.

---

### Post by tweston on 2009-02-07
odd, but in Hardy I *did* have to edit ~/.local/share/applications/mimeapps.list (making the same change that you said for /etc/gnome/defaults.list)

anyway, thanks much, you were very helpful

> **mc4man said:**
> By far the easiest way for _dvd_ is from terminal
```
gksudo gedit /etc/gnome/defaults.list
``` near bottom change this line _x-content/video-dvd=totem.desktop_ to _x-content/video-dvd=vlc.desktop_, save.(ie. just replace totem with vlc )

 Then go to edit menus (right click on applications or go system -> preferences -> main menu), expand sound and video, and on right side right click on vlc -> properties. Change the launcher command to ```
vlc %m
``` 
Or
```
vlc %f
```
That will do it.
This assumes you haven't edited other files like mimeapps.list

To switch default choices enable file management in preferences (edit menus)
If you install totem-xine to make that default over totem-gstreamer
```
sudo update-alternatives --config totem
``` and choose 2

or to keep *totem-gstreamer as default totem player* but add totem-xine as a choice for dvd play back see edit in thread linked below

edit : one word of warning about defaults.list
Any one line can be edited safely once per app and only with <app>.desktop, don't ever use commands in there or try switching apps back and forth on one particular line. Multiple editing of the same line, repeating an app a couple of times can produce unexpected results. 

For other players (non kde apps) see here under replace .desktop (replace mplayer with other name if desired

[http://ubuntuforums.org/showthread.php?p=5633803#post5633803](http://ubuntuforums.org/showthread.php?p=5633803#post5633803)

---

### Post by mc4man on 2009-02-07
> I'm just wondering why you changed the launcher command to vlc %m (or %f

Back in the spring, summer vlc installed with the default of %U which was wrong, complained to no avail in launchpad, that hasn't  changed. %m was what I used in gutsy, it works well as does %f which technically is more proper. %U can cause navigation issues with some disc's

> odd, but in Hardy I *did* have to edit ~/.local/share/applications/mimeapps.list (making the same change that you said for /etc/gnome/defaults.list)

The whole defaults.list thing was just an easy way to do, especially for people who may not want to get involved with .local/share/applications and mimeapps.list.

Did just try on a tester on hardy, still works fine, not sure why not for you unless you edited there before, anyway ....

In the end though you can do and set pretty much anything you wish there  (..../applications and mimeapps.list ) in regards to auto play, auto launch, file associations, defaults, userapps, ect. ect.
Handy place to be comfortable in.

---

### Post by insanity54 on 2009-03-12
Hmm... your guide didn't seem to work for me. DVDs autoplay in totem still. Even after resetting, VLC doesn't autoplay!

---

