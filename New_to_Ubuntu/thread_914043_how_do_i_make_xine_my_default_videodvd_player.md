---
title: "how do i make xine my default video/dvd player?"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by nutpants on 2008-09-08
im sure this has been asked before.
i just cant find the answer 

nuts

---

### Post by Perfect Storm on 2008-09-08
[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

---

### Post by jamesrl on 2008-09-08
In Gnome/ubuntu go to System->Preferred Applications->Multimedia Player

---

### Post by mc4man on 2008-09-08
The defaults.list method may or may not be a good method with xine. The determining factor is whether the default launch command of xine is suitable for autoplay.
If not, then by using that method your forced to change the command for xine itself which may not be suitable for other uses of xine.

That's why I use that method for vlc - it benefits from having a new default command (%m

You may want to use the copy .desktop method (**if not 100% clear** ask for specific instr.

Or the quick method is very safe and easily reverted

see here
[http://ubuntuforums.org/showthread.php?p=5633803#post5633803](http://ubuntuforums.org/showthread.php?p=5633803#post5633803)

I'm going to ck. xine out for suitable launch command (if default isn't right


Edit: it just struck me - if you mean gxine (vs. xine-ui) then it should be available as a choice. (places -> home folder -> edit -> preferences -> media or hold down shift while inserting a dvd and see if it's in the pop up list, if so set there

---

### Post by philinux on 2008-09-08
> **jamesrl said:**
> In Gnome/ubuntu go to System->Preferred Applications->Multimedia Player

I'm afraid this changed in **Hardy** it's in Edit> Prefs from within Nautilus now. And you cant select the player of your choice. I hope this changes with Intrepid.

---

### Post by mc4man on 2008-09-08
Xine-ui will need a different launch command then the default so the defaults.list isn't best choice

Note: xine-ui like a lot of apps works off of a specific device that is set in the app's preferences
Unfortunately atm there doesn't appear to be a way to dynamically reset that to the device that calls xine, so you can only get autoplay from 1 dvd drive (the one set in xine - there are workarounds for 2 dvd drives

Using the copy .desktop method (copy and paste carefully

first browse to home dir. -> .local -> share and see if there is a folder named applications and if so, is there a file - mimeapps.list inside. If so good, **if not** you can create the **folder** if needed

```
mkdir ~/.local/share/applications
```

then run
```
cp /usr/share/xine/desktop/xine.desktop ~/.local/share/applications/xine-dvd.desktop
```

Then run
```
gedit ~/.local/share/applications/mimeapps.list
```

If it's **empty** then paste this in 
```
[Added Associations]
   x-content/video-dvd=xine-dvd.desktop;totem.desktop;

```
If **it's not** then paste just this line in
```
x-content/video-dvd=xine-dvd.desktop;totem.desktop;
```

if the **line exists** then just add at the end of the line
```
xine-dvd.desktop;
```

Be careful to keep formatting - _no space between entries and end with a ;_

then run
```

gedit ~/.local/share/applications/xine-dvd.desktop
```

find the line - Exec=xine 
change to - ```
Exec=xine dvd:// 
```

On the line **name=xine**   add a 1 (if you don't alter the name then in your applications menu you'll see 2 xine's, better to just add 1 to tell default from autoplay ver.

Tested and works fine (use copy and paste carefully - no spaces in mimeapps

Quick safe method
Install gxine
go to places -> home folder -> edit -> preferences -> media and see if gxine is now a choice for dvd, if so set it, if not reboot, if still not there post for instr.

right click on applications -> edit menus, highlight sound & video and find gxine. Right click -> properties and change the launch command to 
```
xine dvd://
```

After your done xine1 should be default dvd player see screen (using hold shift on dvd insert

---

### Post by nutpants on 2008-09-20
dvd are really my least important concern..
avis and mpegs etc are the big one for me
i can "open with" then xine

but i would really like to double click it and have xine go from there.

thanks for the information 

nutz

---

### Post by Perfect Storm on 2008-09-20
> **nutpants said:**
> dvd are really my least important concern..
avis and mpegs etc are the big one for me
i can "open with" then xine

but i would really like to double click it and have xine go from there.

thanks for the information 

nutz


Right click one of your mpegs file, and pick "properties".
In the "Open with" tab you choose "xine",

Now all your mpeg files when you double-click them open/play with xine.

---

### Post by nutpants on 2008-09-20
> **Artificial Intelligence said:**
> Right click one of your mpegs file, and pick "properties".
In the "Open with" tab you choose "xine",

Now all your mpeg files when you double-click them open/play with xine.

i wish, i have been doing that for weeks and i have to do it each time.
it always defauts to one of the other players.

nutz

---

### Post by Perfect Storm on 2008-09-20
It should work...you might encountered an unique bug if it doesn't work regarding xine. 
Try set it to open with another media application and see if it set that application as default.

---

### Post by mc4man on 2008-09-20
@ nutpants
run this and post results, use a maximized terminal for readability (replace red with your username

```
cat /home/[COLOR="Red"]doug[/COLOR]/.local/share/applications/mimeapps.list
```

all set file associations will create or add to a line in there. In the case of multiple apps having *been set*, the first listed on a line is the *current* default (in other words it is a *dynamic* list and that's one reason it doesn't 'respond' well to mis formatting, among other things


Edit : this is the line for **.avi**, notice xine is listed first and will be d. left click default till another app precedes it.

> video/x-msvideo=xine.desktop;totem.desktop;

---

