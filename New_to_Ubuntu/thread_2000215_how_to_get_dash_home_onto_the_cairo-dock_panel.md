---
title: "how to get dash home onto the cairo-dock panel?"
date: 2012-06-09
forum: New to Ubuntu
---

### Post by vallvi on 2012-06-09
Well. That's my question. I like Cairo Dock and its panel much more than the Unity launcher, so I installed it. All fine. The one thing that I like of Unity is the 'dash home', where you can just type in a word and see where that leads you.

So I would be very happy if I could get the dash-home onto my cairo panel. Is that possible? How?

Thnx!

NB: I've got Ubuntu 12.04 and cairo-dock 3.0 installed.

---

### Post by krustenBrot on 2012-06-09
As far as i know that is not possible. The dash is an essential part of unity.

However, i do understand you. I played with docky for a while and i loved the snappier, faster experience. Maybe with a little patience they will port some "dash" to docky/cairo. ;)

---

### Post by vallvi on 2012-06-09
I think they should have used the cairo-dock as the starting point to create a launch panel, in steade of creating unity from scratch. 

Anyway, if anyone has other ideas on how to go about using dash-home on cairo, welcome. If not, I'll have to do as suggested: be patient and hope some one will develop this idea further.

---

### Post by blackbird34 on 2012-06-09
I suppose you'd have to find out which Bash/Terminal command activates the dash, and try associating it with a new launcher (.desktop file) which you could then put on Cairo Dock / Docky / etc. (just an idea, may not work :D )

---

### Post by vallvi on 2012-06-09
thanks! will try that one later today.
any other, more straightforward, ideas and options?

---

### Post by Vaphell on 2012-06-09
can't you use WIN key to invoke dash with unity bar hidden by default? if you want to type and see where it leads you need to have hands on the keyboard either way.

Or switch to another DE altoghether and install something like gnome-do or synapse (my setup on 10.04 = awn dock+synapse)? same idea - shortcut to invoke smart launcher thingie that looks for stuff according to typed text

---

### Post by Ubun2to on 2012-06-09
Well, I have a workaround.
I sometimes use Cairo-Dock (dockys are nice), and so I have a folder with all my most commonly used programs. The folder with all applications is at:
```
/usr/share/applications
```
From there, collect the apps you always want to be able to quickly access and throw them in the folder.
I just launch Cairo-Dock whenever I load Unity (for some reason it's buggy with Gnome Classic for me), so I have the best of both worlds.
I'm trying to get Gnome Classic to work with Cairo-Dock, so I don't have to have ANY desktop icons, but so far, it seems like trying to make 2 opposing forces meet (like trying to put the North ends or South ends of 2 magnets together).
Edit-after playing around a little longer, I finally got the Applications Menu icon I remembered about from 11.10 working. Now, I can clean up my desktop and ditch Unity entirely.

---

### Post by wilee-nilee on 2012-06-09
Not a cairo-dock resoulion, but I always install synapse a search option using a key set prompt for locating stuff, it is similar to gnome-do, but a bit nicer looking in my opinion.

---

### Post by deadflowr on 2012-06-09
You can always launch cairo from with unity.Then hide the launcher.
A simple solution would be, in systems setting, appearance, behavior, switch launcher to always hide(at some point you might want to increase the pressure sensitivity so that poking the edge doesn't invoke it But, afaik, that requires other resources like ccsm to set that)
Second, open up start-up applications, and add cairo-dock(the command is cairo-dock). This way, cairo-dock will always launch when you log in.
This will give you the cairo-dock running on top of unity, with a hidden unity launcher. Everything else will still work, such as the dash. Unfortunately, you'll have to deal with unity's other stuff, like global menus.

---

### Post by mc4man on 2012-06-09
Don't have cairo but maybe something along these lines

```
sudo apt-get install xdotool
```

Then create a .desktop either in this location or as appropriate to cairo

```
gedit ~/.local/share/applications/dash.desktop
```

Use whatever you wish for Name= &  Icon=, sometimes just the icon name is ok, otherwise full path, the icon below isn't really suitable though may be ok

```
[Desktop Entry]
Version=1.0
Type=Application
Name=Dash
Icon=/usr/share/unity/5/launcher_bfb.png
Exec=xdotool key super
```

Then add dash.desktop to your cairo dock, if need be make dash.desktop executable - 
chmod u+x ~/.local/share/applications/dash.desktop
or right click on > properties > permissions

---

### Post by Cpierce on 2012-10-11
Thank You Mc4man. It worked perfectly. You are the master of the launchers !

---

### Post by xrockonx on 2013-01-12
Er.. This is a bit late, but with my Cairo-Dock I made a new launcher and I have it execute <Alt> .. because I set it so the Alt key brings up the dash.. I then hid the launcher :|

---

### Post by sacp on 2013-01-31
> **mc4man said:**
> Don't have cairo but maybe something along these lines

```
sudo apt-get install xdotool
```Then create a .desktop either in this location or as appropriate to cairo

```
gedit ~/.local/share/applications/dash.desktop
```Use whatever you wish for Name= &  Icon=, sometimes just the icon name is ok, otherwise full path, the icon below isn't really suitable though may be ok

```
[Desktop Entry]
Version=1.0
Type=Application
Name=Dash
Icon=/usr/share/unity/5/launcher_bfb.png
Exec=xdotool key super
```Then add dash.desktop to your cairo dock, if need be make dash.desktop executable - 
chmod u+x ~/.local/share/applications/dash.desktop
or right click on > properties > permissions

Hi. 
For me didn't work :confused:

followed those steps, but no avail.

---

### Post by fabounet on 2013-03-05
Actually to add a launcher that triggers a shortkey in Cairo-Dock, you can just create a custom launcher, and set the command to the shortkey directly :-)
In this case: <Super> (with the <>)

Also, see this page for more information on using Cairo-Dock within Unity: [http://glx-dock.org/ww_page.php?p=Cairo-Dock%20and%20Unity&lang=en](http://glx-dock.org/ww_page.php?p=Cairo-Dock%20and%20Unity&lang=en)

---

### Post by tjohn81 on 2013-04-13
your solution works very well thanks

---

