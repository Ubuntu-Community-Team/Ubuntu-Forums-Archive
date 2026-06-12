---
title: "HOWTO: Separate Xgl/Compiz Session"
date: 2006-05-11
forum: Outdated Tutorials &amp; Tips
---

### Post by bluevoodoo1 on 2006-05-11
Separate Xgl/Compiz Session: Xgl/Compiz/GNOME/KDE and your lightweight WM.

The Xgl/Compiz craze with Dapper is great, but if you install and configure it most ways found around here you will magically turn GNOME/KDE or your light-weight WM into a cpu hungry behemoth. Plus using Xgl instead of Xorg will make it difficult to play games, watch videos, etc. etc. If you would like Xgl/Compiz with GNOME/KDE then I STRONGLY suggest this link.... [https://wiki.ubuntu.com/xglati](https://wiki.ubuntu.com/xglati) It will help create a separate Xgl/Compiz session rather than having the Xgl-server completely taking over the X-server. (which will take over GNOME/KDE/your light-WM). 

**I'm using a [COLOR="DarkGreen"]Nvidia[/COLOR] card. I'm not sure what that means for [COLOR="Red"]ATI [/COLOR]users, so I will go on with [COLOR="DarkGreen"]NVIDIA[/COLOR] users in mind.** 

Again, the source is taken from [https://wiki.ubuntu.com/xglati](https://wiki.ubuntu.com/xglati), but I will be making a few alterations. My main reason for doing this is to spread the word on this wiki page! All the work goes to that author! It is great work!

I have both GNOME and KDE on my system, and the following works for me. I am not sure if this will work if you are only using Kubuntu!

=================================

**[COLOR="Red"]BEFORE YOU BEGIN[/COLOR]**
You might find this guide to be easier!
[http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29](http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29)

=================================

1. Add new repos to your /etc/apt/sources.list.

```
sudo gedit /etc/apt/sources.list
```


add these lines...
```
deb http://xgl.compiz.info/ dapper main 
deb http://www.beerorkid.com/compiz/ dapper main
```

...save

Add this key...
```
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
```

```
sudo apt-get update
```

2. Install

```
sudo apt-get install libglitz1 libglitz-glx1 xserver-xgl libgl1-mesa libsvg libsvg-cairo compiz compiz-gnome gset-compiz cgwd
```

3. Create a separate Xgl session (GNOME-based). 

First the script.

```
sudo gedit /usr/bin/xgl-gnome.sh
```
Paste this in.
```

#!/bin/bash  

Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:fbo & sleep 2 && DISPLAY=:1 gnome-session
```

Make it executable...
```
sudo chmod 755 /usr/bin/xgl-gnome.sh
```

Now create the session...
```
sudo gedit /usr/share/xsessions/xgl-gnome.desktop
```

paste this in...
```

[Desktop Entry]  
Encoding=UTF-8 
Name=XGL-GNOME
Exec=/usr/bin/xgl-gnome.sh 
Icon= 
Type=Application
```

Make it executable...
```
sudo chmod 755 /usr/share/xsessions/xgl-gnome.desktop
```


4. Starting it up.

Upon starting your xgl-gnome session (you might see black and + mouse symbol--mine shows it, eventually it goes)

**You will have to run**
```
cgwd
```
AND
```
compiz --replace gconf
```


There are some options for this:
You can add those two statements to your session startup, use "thefuture" script seen on most Xgl/Compiz threads and add it to your panel, use some sort of "toggle" script (seen around here), or make a panel icon (of any of those things). For any problems, type "metacity --replace" to get your window titles back.

4a. Here's a toggle script from the forums. (you can put it anywhere, I put it in my home/bin folder)

```
sudo gedit bin/toggle
```
```
#!/bin/bash
if ps -A | grep -e " compiz.real$" > /dev/null; then
	killall cgwd
	metacity --replace &
else
	cgwd &
	compiz --replace gconf &
fi

```

```
sudo chmod 755 bin/toggle
```

Now you have a script to use for a launcher!

5. For KDE...

same steps... except the following:

use xgl-kde.sh instead of xgl-gnome.sh (to name your session)
Change Name=XGL-GNOME to Name=XGL-KDE (or something similar)
use startkde instead of gnome-session (in your xgl-kde script)
use kwin instead of metacity (to get original window manager back)

6. Additional info.

Frodon's guide. Very similar to this with fewer steps. 
[http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29](http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29)

---

### Post by jon_z on 2006-05-18
Definatly works, I followed all other guides and was ready to gouge my eyes out.. After you showed me this i was in heaven.... This is the best guide i feel around because if you dont want XGL to load all of the time, you can choose your session.

---

### Post by joshrobinson on 2006-05-18
well, with having 0 luck with Xgl on my laptop, im gona give this a go.. will post my results

---

### Post by joshrobinson on 2006-05-18
well it booted xgl, so thats farther then ive mad it so far, but i have no window effects, wobbly fade cube anything.. oh well ill fiddle with it more later

---

### Post by bluevoodoo1 on 2006-05-18
[QUOTE=joshrobinson]well it booted xgl, so thats farther then ive mad it so far, but i have no window effects, wobbly fade cube anything.. oh well ill fiddle with it more later[/QUOTE]


Hmmm. Did you run "gnome-window-decorator" and "compiz --replace gconf" ? What video card are you using?

---

### Post by joshrobinson on 2006-05-18
[QUOTE=bluevoodoo1]Hmmm. Did you run "gnome-window-decorator" and "compiz --replace gconf" ? What video card are you using?[/QUOTE]

an ati mobility, got open gl and all running.. with the compiz --replace gconf, does that do all the settings for all the effects? or should i do

compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher  ?

---

### Post by Bazon on 2006-05-18
about the repos:
[QUOTE=bluevoodoo1]
1. Add new repos to your /etc/apt/sources.list.

```
sudo gedit /etc/apt/sources.list
```


add these lines...
```
deb http://xgl.compiz.info/ dapper main 
deb http://www.beerorkid.com/compiz/ dapper main
```

...save

```
sudo apt-get update
```
[/QUOTE]
maybe you should add you [need a key](http://compiz.net/viewtopic.php?id=2):
[quote="[QuinnStorm](http://compiz.net/viewtopic.php?id=2)"]Anyhow, here's a repost of my packages' info.

My repo's gpg key can be found at
[http://metascape.afraid.org:13666/quinn.key.asc.gz](http://metascape.afraid.org:13666/quinn.key.asc.gz)
to import it, use
```
zcat quinn.key.asc.gz | sudo apt-key add -
```
**PLEASE use this mirror instead of the old repo. (it redirects you here now anyway)**
```
deb http://www.beerorkid.com/compiz/ dapper main
```[/quote] 
[color=#FF0000]EDIT:[/color]
which is actually not working anymore, pleas read next two posts....

---

### Post by sanone on 2006-05-18
If you paste a link make sure it's working.. I found the key on this (official) site:
[http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/)

---

### Post by Bazon on 2006-05-18
[QUOTE=sanone]If you paste a link make sure it's working.. I found the key on this (official) site:
[http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/)[/QUOTE]
Sorry! :oops:

Although this is a bit Quinns fault, I quoted him from a [_sticky_ thread in the compiz forum](http://compiz.net/viewforum.php?id=4).... :wink:

I'll notice him there...

So ```
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
``` should work to get the key.

---

### Post by frodon on 2006-05-18
bluevoodoo1, i wrote something quite similar in the UDSF,if you see interesting things that you want to add to your guide feel free to do it :
[http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29](http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29)

The script include the start of compiz and the xmodmap workaround.

---

### Post by bluevoodoo1 on 2006-05-18
[QUOTE=joshrobinson]an ati mobility, got open gl and all running.. with the compiz --replace gconf, does that do all the settings for all the effects? [/QUOTE]

That should do it. That is what I use and all the effects work. Again I wrote this with nvidia card users in mind... not very sure about ATI. I know they sometimes have trouble with xgl.

---

### Post by bluevoodoo1 on 2006-05-18
Thank you sanone, Bazone, and frodon. 

Bazone, sanone: I added information for the key.

Frodon: Thank you for showing me your guide. I will play around with it... it's nice having the gnome-window-decorator and compiz inside the xgl script, it's much tidier than my method. In the mean time I will link it up!

---

### Post by nalthien on 2006-05-18
ATI users will need to use ```
xv:pbuffer
``` instead of ```
xv:fbo
``` in their XGL line--the updated Wiki page has information:

[http://wiki.ubuntu.com/xglati](http://wiki.ubuntu.com/xglati)

---

### Post by frodon on 2006-05-18
bluevoodoo1, any objections if i set your thread as the reference thread in the UDSF guide ?

BTW, you're free to edit my guide if you see errors, i think it might be good to merge the 2 guides.

---

### Post by bluevoodoo1 on 2006-05-18
[QUOTE=frodon]bluevoodoo1, any objections if i set your thread as the reference thread in the UDSF guide ?

BTW, you're free to edit my guide if you see errors, i think it might be good to merge the 2 guides.[/QUOTE]

Sure, I got this from [https://wiki.ubuntu.com/xglati](https://wiki.ubuntu.com/xglati) so quote that too.

I tried you guide and your script works, but only like this...

```

xmodmap /usr/share/xmodmap/xmodmap.us 
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1
gnome-window-decorator & 
compiz --replace gconf & 
exec gnome-session

```

the 'killall gnome-window-decorator' and 'wait' don't seem to work here... Taking them out works for me. But, the splash dialog doesn't want to go away (unless I click it) and I can't logout... hmmm... But I like the idea of having the compiz related startup here rather than in an external command/applet/panel/launcher.

---

### Post by frodon on 2006-05-18
Hum i wonder why the 'killall gnome-window-decorator' and 'wait' don't works, i translated that from the ubuntu fr wiki.
I will make some more tests next week.

Thanks for your guide, i'm sure that many users will love it ;)

---

### Post by Bazon on 2006-05-18
[QUOTE=bluevoodoo1]the 'killall gnome-window-decorator' and 'wait' don't seem to work here... [/QUOTE]Same for me!
With the [Script from frodon](http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29), my session don't even start.... (...all I got was a mouse-crosshair and black-white-pointed ground, although commenting in and out all options)
But I agree, starting compiz with the session would be really nice... :wink:

Anyway, thanks for that How-To, I didn't use XGL for severall weeks as it bothered me too much (espacially on fullscreen video playback...), but having the Option to start is as a session is really cool, thanks! :D

---

### Post by bluevoodoo1 on 2006-05-18
[QUOTE=Bazon]Same for me!
With the [Script from frodon](http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29), my session don't even start.... (...all I got was a mouse-crosshair and black-white-pointed ground)[/QUOTE]

Yup, that's what happened here.

---

### Post by frodon on 2006-05-18
I commented the 'killall gnome-window-decorator' and 'wait' lines for the moment, i have to wait my new computer (next week) to solve the issue but it doesn't seem to be a big deal and the 'killall gnome-window-decorator' and 'wait' lines are not mandatory.

A big thank you for your feedback guys ;)

---

### Post by escape on 2006-05-18
^^^Try hitting Ctrl+Alt+F1 or F2, and starting gnome-session.

Is there any way to start gnome-session so you're not logged in as root?

---

### Post by Bazon on 2006-05-18
For me, [that script](http://www.cywhale.de/index.php?page/news/id/4&viridiskeks=ba7a7fb181f0d5183862679018f49474) *(comments translated poorly by me...)* started compiz with the session:
```

#!/bin/bash
# change keyboard-layout, here to german
xmodmap /usr/share/xmodmap/xmodmap.de
# start XGL:
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1
# probably not neccesarry: change environment variable
LIBMESA=/opt/mesa/lib
# start compiz
LD_LIBRARY_PATH=/opt/mesa/lib compiz --replace decoration wobbly fade minimize cube rotate zoom scale move resize place switcher opaquefocus opacity &
# start Window-Decorator:
gnome-window-decorator &
# keyboar-Layout - neccesarry?
xmodmap /usr/share/xmodmap/xmodmap.de
# start Gnome
exec gnome-session
```
But another problem occured with that:
My plugins setting made in gset-compiz don't apply anymore!
I think that's because of that:
[QUOTE=escape]Is there any way to start gnome-session so you're not logged in as root?[/QUOTE]

---

### Post by bluevoodoo1 on 2006-05-18
[QUOTE=Bazon]For me, [that script](http://www.cywhale.de/index.php?page/news/id/4&viridiskeks=ba7a7fb181f0d5183862679018f49474) *(comments translated poorly by me...)* started compiz with the session:
```

#!/bin/bash
# change keyboard-layout, here to german
xmodmap /usr/share/xmodmap/xmodmap.de
# start XGL:
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1
# probably not neccesarry: change environment variable
LIBMESA=/opt/mesa/lib
# start compiz
LD_LIBRARY_PATH=/opt/mesa/lib compiz --replace decoration wobbly fade minimize cube rotate zoom scale move resize place switcher opaquefocus opacity &
# start Window-Decorator:
gnome-window-decorator &
# keyboar-Layout - neccesarry?
xmodmap /usr/share/xmodmap/xmodmap.de
# start Gnome
exec gnome-session
```
But another problem occured with that:
My plugins setting made in gset-compiz don't apply anymore!
I think that's because of that:[/QUOTE]

Why not add it? (you also have 2 instances of your keyboard setting, I took one out) How about this...

```

#!/bin/bash
# change keyboard-layout, here to german
xmodmap /usr/share/xmodmap/xmodmap.de
# start XGL:
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1
# probably not neccesarry: change environment variable
LIBMESA=/opt/mesa/lib
# start compiz
LD_LIBRARY_PATH=/opt/mesa/lib compiz --replace **gconf** decoration wobbly fade minimize cube rotate zoom scale move resize place switcher opaquefocus opacity &
# start Window-Decorator:
gnome-window-decorator &
# start Gnome
exec gnome-session
```

---

### Post by Bazon on 2006-05-18
[QUOTE=bluevoodoo1]Why not add it? (you also have 2 instances of your keyboard setting, I took one out) How about this...[/QUOTE]

I tried for myself and ended up with something very similar.
Actually, you can forget every additional option after **gconf**

So that's what I got now (without comments to keep it shorter...)
```
#!/bin/bash
xmodmap /usr/share/xmodmap/xmodmap.de
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1
LIBMESA=/opt/mesa/lib
LD_LIBRARY_PATH=/opt/mesa/lib compiz --replace gconf
gnome-window-decorator &
exec gnome-session
```
which also works very fine... :)

---

### Post by bluevoodoo1 on 2006-05-18
[QUOTE=Bazon]I tried for myself and ended up with something very similar.
Actually, you can forget every additional option after **gconf**[/QUOTE]

Yup.

---

### Post by Bazon on 2006-05-18
Hm. Just one thing I noticed here:

I don't havve a shutdown button in the shutdown dialog!

Only Hilbernate, log off, change user and log session!

Does anyone have the same problem here?
How can this be avoided?

I'd really like to be able to shut down directly....

---

### Post by bluevoodoo1 on 2006-05-18
[QUOTE=Bazon]Hm. Just one thing I noticed here:

I don't havve a shutdown button in the shutdown dialog!

Only Hilbernate, log off, change user and log session!

Does anyone have the same problem here?
How can this be avoided?

I'd really like to be able to shut down directly....[/QUOTE]


Yes, that happens here too. I should probably mention that in the guide... I don't have any ideas on finding a work around for that.

---

### Post by Bazon on 2006-05-19
About the shutdown issue:

Thread in Compiz Forum: [shutdown/restart/hibernate ?](http://compiz.net/viewtopic.php?id=429&p=1)
Bug in launchpad: [Incomplete logout options with XGL](https://launchpad.net/distros/ubuntu/+source/gnome-panel/+bug/36321/)

No solution yet, but one may keep an eye on it... :wink:

About the bug:
It is not confirmed yet.
Should it be confirmed?
I mean, I'm not sure whether that really is a failure of xserver-xgl....

---

### Post by archis on 2006-05-20
I think you're hitting the nail on the head: How to switch between Xservers -- Xgl & Xorg -- instead of window managers? As far as I know, Xgl is not a replacement for Xorg but merely a vehicle for compiz. Therefore, it would be neat to be able to switch, point-and-click-style, between Xservers, not between compiz and metacity on Xgl.

As far as I can tell, this isn't bringing us closer, though: the xsession file allows you to log into a dedicated xgl+compiz session from gdm but [as this poster explains]("http://compiz.net/viewtopic.php?pid=3661#p3661"), it's really an Xgl server on top of Xorg -- by the time you are seeing the gdm login screen, the regular Xorg server is already running.

Your script - and [frodon's]("http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29") - starts the Xgl server & compiz on a different display (#1), while gdm is running Xorg on display #0. It's a [nested Xgl session]("https://wiki.ubuntu.com/NestedXglHowto"). That means that gdm isn't actually managing the Xgl session, causing several issues -- for example, no direct shutdown or restart from within the Xgl-compiz session. You'll need to log out first, then reboot or shutdown from gdm's login screen. Not too bad, but not really convenient either. <[More on this archlinux wiki page]("http://wiki.archlinux.org/index.php/Xgl#Method_2_-_New_GDM_entry_starts_XGL")>.

I know of two ways to switch Xservers, and both involve (temporarily or permanently) replacing Xorg with Xgl:

a) change gdm.conf-custom to read something like this

```
[servers]
# Override Xserver config for display 0 to use Xgl instead of Xorg.
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -br -accel xv:fbo -accel glx:pbuffer
flexible=true
```

or b) replacing the /etc/X11/X symlink to /usr/bin/X11R6/bin/Xorg with a symlink to /usr/bin/Xgl

```
sudo ln -sf /usr/bin/Xgl /etc/X11/X
```

Again, no black magic. To change between Xservers, point the symlink back to /usr/bin/X11R6/bin/Xorg. 

```
sudo ln -sf /usr/bin/X11R6/bin/Xorg /etc/X11/X
```

Not exactly super convenient either. And both methods require a reboot.

Btw, the official (now deprecated) compiz from ubuntu universe had a [/usr/bin/startxgl script]("http://svn.xgl-coffee.org/xgl-coffee/trunk/startxgl") which [you can see here]("http://svn.xgl-coffee.org/xgl-coffee/trunk/startxgl"). (I don't know whether it is also in compiz-quinnstorm and compiz-vanilla.) It basically does the same thing your script does: it starts xgl , and eventually compiz etc, on a different display, with the attendant problems described above. Interestingly, it calls gnome-settings-daemon but no gnome-session:

```

if [ "$2" = "gnome" ]; then
	DISPLAY=:$1 gnome-window-decorator &
	DISPLAY=:$1 /usr/libexec/gnome-settings-daemon &
	DISPLAY=:$1 nautilus -n --sync &
	DISPLAY=:$1 gnome-panel
```

The Nested Xgl wiki page also has

```
unset SESSION_MANAGER
```

perhaps making the nested Xgl-compiz-gnome session somewhat smoother... 

Using the startxgl script, your xgl.desktop file for gdm could look look something like this (as descibed [at the archlinux wiki]("http://wiki.archlinux.org/index.php/Xgl#Method_2_-_New_GDM_entry_starts_XGL")):

```
[Desktop Entry]
Encoding=UTF-8
Type=XSession
Exec=startxgl 1 gnome nvidia
TryExec=startxgl
Name=Xgl-Compiz

```

In other words, we'd be calling on the startxgl script to start a Xgl-gnome session using nvidia card settings on display 1, but again, that's a nested Xgl session, with Xorg still running on display #0.

---

### Post by Bazon on 2006-05-20
[QUOTE=archis]Your script - and [frodon's]("http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29") - starts the Xgl server & compiz on a different display (#1), while gdm is running Xorg on display #0. It's a [nested Xgl session]("https://wiki.ubuntu.com/NestedXglHowto"). [/QUOTE]
I see.
But is it really necessarry to run it on another display?
(Before I mess around I ask...:__) Why not run it on Display 0?

And: How do I switch Displays?
I tried a bit naiv and found another thing:

[QUOTE=archis]That means that gdm isn't actually managing the Xgl session, causing several issues -- for example, no direct shutdown or restart from within the Xgl-compiz session. [/QUOTE]in fact, there is at least one further issue:
CTRL+ALT+F1 to switch to tty1 doesn't work with this kind of XGL session.

But anyway, for me that's an smaller issue than not being able to have direct rendering at all (mostly for full screen videos for me...), if everything wents wrong, ther is still CTRL+ALT+BACKSPACE...


But there is also another possibility for seperate Xorg / XGL sessions:
Start a Xorg session on tty7 and a XGL session on tty9.
That worked for me the last time I tried XGL, but when somehow it broke and I kicked off XGL completly for some time....
...maybe time to try it again.... :wink:

---

### Post by Bazon on 2006-05-20
[QUOTE=Bazon]But there is also another possibility for seperate Xorg / XGL sessions:
Start a Xorg session on tty7 and a XGL session on tty8.[/QUOTE]
OK, tried that, here is the How-to + issues with this method:

--------------------
[color=#CC9933][edit]shortened according to [this tipp](http://www.ubuntuforums.org/showpost.php?p=1036175&postcount=41)[/edit][/color]
short HOW-TO:
**_Seperate XGL-session on tty7 and Xorg session on tty8_**

*(you'll probably need only from step 3 or from step 5 on when you used compiz before...)*

1.
Install Compiz and XGL as described in the first post here or somewhere else...

2. 
If you used the method described in this thread before:
Make sure your default Session is Gnome and not XGL.

3. **That's the important step!**
Edit your /etc/gdm/gdm.conf-custom to contain this:
```
[servers]
# use Xgl on display 0 and Xorg on display 1
0=Xgl
1=Standard

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -br -accel xv:fbo -accel glx:pbuffer
flexible=true
```

4.[color=#FF0000][edit][/color]: To start compiz with session, use a simple thefuture script:

sudo gedit /usr/local/bin/thefuture
```
#!/bin/bash
gnome-window-decorator &
compiz --replace gconf
exit
```
Don't use xmodmap! That will cause problems in the Xorg session!

make it executeable:

sudo chmod 755 /usr/local/bin/thefuture

and put it in the session start:

System > Preferences > Sessions > Startup Programs > Add > thefuture

this will start compiz in XGL and cause no problesm in Xorg. :)
[color=#FF0000][/edit][/color]
reboot

5.
After the restart, two Sessions will start:
The XGL-Session on tty7 and the Xorg-Session on tty8.
As the Xorg Session starts after the XGL Session *(at least if you left the VT's as described above...)*, you will see the GDM screen of the Xorg session.
To switch to the XGL-Session directly, hit CTRL + ALT + F7.
To switch back to Xorg, hit CTRL + ALT + F8.


-------------------

_Advantages_
[list][*]In contrast to all other methods, you can use direct rendering (for fullscreen videos or games...) without logging out.
[*]Full logout options.
[*]As it seems now: Full working key-shortcuts.[/list]

_Disadvantages / Issues_[list]
[*]Auto-login works only on tty7, not on tty8. Started [another thread](http://www.ubuntuforums.org/showthread.php?p=1035387#post1035387) to search for solutions.
[*]Firefox will only run in one session, at least if you don't use [*export MOZ_NO_REMOTE=1*](http://www.firefox-browser.de/wiki/MOZ_NO_REMOTE#Vorgehen_unter_Linux) to start another Firefox profile (ask me if you need it...)[/list]


---------------------------

---

### Post by archis on 2006-05-20
I think that's the $64,000 question: is it possible to set up two different X servers -- Xgl and Xorg --  that both point at the same video card in xorg.conf (same pci/agp address) or not? If the graphics card can handle that (two Xservers 'side by side', not nested), one could then start two non-nested sessions and switch between them [Ctl-Alt-F7, Ctl-Alt-F8]. Thoughts?

> 6.
After the restart, two Sessions will start:
The XGL-Session on tty7 and the Xorg-Session on tty8.
As the Xorg Session starts after the XGL Session (at least if you left the VT's as described above...), you will see the GDM screen of the Xorg session.
To switch to the XGL-Session directly, hit CTRL + ALT + F7.
To switch back to Xorg, hit CTRL + ALT + F8.

I think you've just flipped the nested X server here: instead of nesting Xgl inside Xorg, we are now nesting Xorg inside Xgl.. that would mean that the Xorg session has the same issues the (nested) Xgl session had previously (autologin doesn't work, restart/shutdown isn't possible from within the session, keyboard layout issues, can't drop into vts from within the nested session..).

I guess one could switch between the nested and the parent servers with Ctl-Alt-F7/F8 in either case.

---

### Post by Bazon on 2006-05-20
[QUOTE=archis]I think that's the $64,000 question: is it possible to set up two different X servers -- Xgl and Xorg --  that both point at the same video card in xorg.conf (same pci/agp address) or not? If the graphics card can handle that (two Xservers 'side by side', not nested), one could then start two non-nested sessions and switch between them [Ctl-Alt-F7, Ctl-Alt-F8]. Thoughts?[/QUOTE]

Ehm, YES! It is possible!

I described it in [my post directly before your post](http://www.ubuntuforums.org/showpost.php?p=1035288&postcount=30).

Where can I collect my $64.000? :wink:

But it has some new disadvantages *(also see post before....)*: 
Only one auto-login works, compiz has to be started from hand again and only one Firefox Profile could be run by session.

The last is easily solveable, but if you could help me to solve the other ones, that would be great... :)

---

### Post by archis on 2006-05-20
I suppose there are a number of workarounds for the various funny bits that happen in nested Xserver sessions, but no real fixes. One reason for that could be that changing a symlink or editing a gdm.conf-custom file suddenly looks a lot more attractive than coming up with a whole bunch of workarounds.. 

think low-hanging fruit.. :roll:

---

### Post by Bazon on 2006-05-20
OK, starting compiz with the session is really simple, I edited [the post](http://www.ubuntuforums.org/showpost.php?p=1035288&postcount=30) with the two-xserver HOW-To.
And it won't hurt the Xorg Session. :)

---

### Post by bluevoodoo1 on 2006-05-20
[QUOTE=archis]I know of two ways to switch Xservers, and both involve (temporarily or permanently) replacing Xorg with Xgl:.[/QUOTE]

This is why I'm in favor of this "nested" mehthod. I agree it is nested, but since they run on different displays I can rationalize calling them separate, perhaps concurrent is a better word choice? I have a bunch of dekstop environments/window managers... Blackbox, IceWm, e16, xfce, jwm.. etc. etc. Using Xgl on the same display as xorg makes these light-weight WMs *incredibly* slow. Hence... having separate display for xorg/xgl makes sense, to me at least. The no shutdown/restart isn't a big problem for me, I don't even call it an inconvience. Anyway, Xgl/compiz is just eye candy to play around with, I don't want it to take over.

edit: typo

edit 2: archis: I will play around with the last thing you mentioned from [http://wiki.archlinux.org/index.php/Xgl#Method_2_-_New_GDM_entry_starts_XGL](http://wiki.archlinux.org/index.php/Xgl#Method_2_-_New_GDM_entry_starts_XGL) about getting nvidia card/gnome settings working with it.

---

### Post by Bazon on 2006-05-20
[QUOTE=bluevoodoo1][quote=archis]I know of two ways to switch Xservers, and both involve (temporarily or permanently) replacing Xorg with Xgl:.[/quote]This is why I'm in favor of this "nested" mehthod. I agree it is nested, but since they run on different displays I can rationalize calling them separate,[/QUOTE]Could you explain what's the problem with the method I introduced [there](http://www.ubuntuforums.org/showpost.php?p=1035288&postcount=30)?

There are two **seperate**  X-Servers running together at the same time, 
one is XGL running on tty7,
one is (native!) **Xorg** running on tty8.

Both are **not nested** and available al the time without loging out.

[b]What's the problem?
[/b]I'm really curious....:)

---

### Post by bluevoodoo1 on 2006-05-20
[QUOTE=Bazon]Could you explain what's the problem with the method I introduced [there](http://www.ubuntuforums.org/showpost.php?p=1035288&postcount=30)?

There are two **seperate**  X-Servers running together at the same time, 
one is XGL running on tty7,
one is (native!) **Xorg** running on tty8.

Both are **not nested** and available al the time without loging out.

[b]What's the problem?
[/b]I'm really curious....:)[/QUOTE]

I'll test it. If it works for you and others then that is a very good thing. Options are good.

Here's my question/concern. If there are two separate x-servers running at the same time, won't that just be the same problem I mentioned in my last post? (with xgl taking up lots of CPU). In tty7 and tty8 does the command "top" say you're running xorg and xgl, or just xorg in tty7 and xgl in tty8?

---

### Post by Bazon on 2006-05-20
[QUOTE=bluevoodoo1]Here's my question/concern. If there are two separate x-servers running at the same time, won't that just be the same problem I mentioned in my last post? (with xgl taking up lots of CPU). In tty7 and tty8 does the command "top" say you're running xorg and xgl, or just xorg in tty7 and xgl in tty8?[/QUOTE]top shows running both Xgl and Xorg, on tty7 and on tty8.
*(I run both sessions as the same user)*
For me, using a 1.4GHz AMD Geode 1750 Nx with 512MB RAM and A Nvidia Geforce 5200, Xgl needs less than 1.5% CPU, most of the time less than 1.0%CPU on tty8 where I run Xorg.

That is not nothing, but very little.

At least there is no problem with Fullscreen Video playback and 3-D Games on tty8 with Xorg:

A little test:
I watched an avi Movie with gmplayer in Fullscreen, top was running in a terminal. With ALT+TAB you can switch to that terminal without leaving Fullscreen.

Result:

tty7 with Xgl:
aprox. 72%CPU for Xgl
aprox. 13%CPU for gmplayer
movie not really running smooth

tty8 with Xorg:
aprox. 7%CPU for gmplayer
aprox 3%CPU for Xorg
movie absolutly smooth.

That's at least what I want :)

---

### Post by bluevoodoo1 on 2006-05-20
[QUOTE=Bazon]top shows running both Xgl and Xorg, on tty7 and on tty8.
*(I run both sessions as the same user)*
For me, using a 1.4GHz AMD Geode 1750 Nx with 512MB RAM and A Nvidia Geforce 5200, Xgl needs less than 1.5% CPU, most of the time less than 1.0%CPU on tty8 where I run Xorg.

That is not nothing, but very little.

At least there is no problem with Fullscreen Video playback and 3-D Games on tty8 with Xorg:

A little test:
I watched an avi Movie with gmplayer in Fullscreen, top was running in a terminal. With ALT+TAB you can switch to that terminal without leaving Fullscreen.

Result:

tty7 with Xgl:
aprox. 72%CPU for Xgl
aprox. 13%CPU for gmplayer
movie not really running smooth

tty8 with Xorg:
aprox. 7%CPU for gmplayer
aprox 3%CPU for Xorg
movie absolutly smooth.

That's at least what I want :)[/QUOTE]

That is very interesting! 

Hmm.... Do you use any other WMs? i'm curious to see what happens with those, since the main purpose of this guide--for me--is to preserve the "lightness" of a light window manager. My main concern is Xgl running when I only want xorg-- that defeats the purpose of "lightweight window managers."

When I first installed Xgl/compiz it completely killed Blackbox's performance (which is what I use for gaming, movies, etc. ), as well as many of its settings had been messed up. The typical startup of Blackbox went from <5 seconds to closer to 30, which is closer to a gnome session--- plus videos/games suffered.

But your guide is great... getting direct rendering, keyboard shortcuts and full logout possibilities is great, definitely a step beyond mine!!!

---

### Post by Bazon on 2006-05-20
No, sorry, I don't use any other WMs, only Metacity and Compiz.

---

### Post by archis on 2006-05-20
Sounds good! 8) So I presume gdm is now managing both sessions for you?

> 5. That's the important step!
Go to System > Administration > Login Window > Security > Configure X-Server. There hit the Add/modify button, select "1" for VT and "Standard" for Server and hit OK.


You're changing the display for the 'Standard' (Xorg) server from #0 to #1 while setting the newly defined Xgl server's display to #0. It seems you could just keep Xorg at #0 and define the Xgl server in gdm.conf-custom as using #1 instead, obviating the need for step 5. Why bother if you end up switching between sessions anyway?

Also: why not use a single startup script for xgl, compiz, decorator etc. and put it in the xgl.desktop file?

```
[servers] 
# Override Xserver config for display 0 to use Xgl instead of Xorg. 
0=Standard
1=Xgl 

[server-Xgl] 
name=Xgl server 
command=startxgl 1 gnome nvidia
flexible=true

```

---

### Post by Bazon on 2006-05-20
@archis:
First of all: Yes, you're right, GDM handles both sessions and starts two times.

Also:
You're absolutly right, this really could be optimized! :)
I didn't exactly know what I did there either, I also only read it somewhere...

In fact, my gdm.conf-custom looks after the steps I described that way:
```
[servers]
# Override Xserver config for display 0 to use Xgl instead of Xorg.
0=Xgl
1=Standard

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -br -accel xv:fbo -accel glx:pbuffer
flexible=true
```
So the [i]System > Administration > Login Window > Security > Configure X-Server
There hit the Add/modify button, select "1" for VT and "Standard" for Server and hit OK[/i] procedure is not necesarry when just the line* 1=Standard* is included in the gdm.conf-custom?
Seems so...
[quote="archis"]Also: why not use a single startup script for xgl, compiz, decorator etc. and put it in the xgl.desktop file?[/quote]
However, I haven't found a startup script which could be included in the gdm.conf-custom, but I didn't bother much about that as it works for me with the script started in the regular Gnome Session. :)

---

### Post by archis on 2006-05-20
```
[edit]No, seems not to work! Started with this 
command=scriptname in gdm.conf-custom and it ended up 
in x not working. Don't use that! (Unless you want to try 
yourself and improve it....) [/edit]
```

You mean the startxgl script? Perhaps it's not even there, right in the middle of the path, because it's not included in the more recent  compiz packages #-o 

How about something like this.. with either DISPLAY=:0 or :1 depending on your setup:

```
#!/bin/bash
/usr/bin/Xgl :1 -fullscreen -ac -br -accel xv:fbo -accel glx:pbuffer
# checking whether Xgl is running
if [ `ps -A | grep Xgl | wc -l` == "1" ]; then
          DISPLAY=:1 compiz --replace gconf &
          DISPLAY=:1 gnome-window-decorator &
          DISPLAY=:1 /usr/libexec/gnome-settings-daemon &
          DISPLAY=:1 nautilus -n --sync &
          DISPLAY=:1 exec gnome-session
fi

```


Save that to, say, ~/bin/compiz-gnome.sh, then do a 

```
chmod +x ~/bin/compiz-gnome.sh

```

and call it as 

```
command=/home/<usr>/bin/compiz-gnome.sh
```

---

### Post by ramiro on 2006-05-21
what I did was the following:

```
sudo gedit /usr/bin/compiz-start
```

```
#!/bin/bash
if ps -A | grep -e "Xgl" > /dev/null; then
        gnome-window-decorator &
        compiz --replace gconf &
fi

```

```
sudo chmod 755 /usr/bin/compiz-start
```

I then opened System->preferences->sessions and added compiz-start to my starting programs

now whenever Xgl is running, it will open up compiz, otherwise it will stick to metacity

another thing I did was add

```
export __GL_FSAA_MODE=1
export __GL_LOG_MAX_ANISO=1
export __GL_SYNC_TO_VBLANK=1

```

to my /usr/bin/xgl-gnome.sh (from the first post) to get antialiasing, vertical sync and anisotropic filtering

one problem I am having though, from my Xgl session, I cannot shut down or restart, the only option available is hibernate.

---

### Post by frodon on 2006-05-21
Good shot ramiro !, it seems to be the perfect way to do it, i will update my guide that way.

Thanks for sharing.

---

### Post by bluevoodoo1 on 2006-05-21
[QUOTE=ramiro]one problem I am having though, from my Xgl session, I cannot shut down or restart, the only option available is hibernate.[/QUOTE]

What about logging out??

---

### Post by Bazon on 2006-05-21
[QUOTE=ramiro]one problem I am having though, from my Xgl session, I cannot shut down or restart, the only option available is hibernate.[/QUOTE]
It's been discussed here before. [Archis explained](http://ubuntuforums.org/showpost.php?p=1035161&postcount=28) it is caused by the nested method and [I found](http://ubuntuforums.org/showpost.php?p=1031990&postcount=27) a bugreport in launchpad describing that and in therad in compiz forum about that.
Also, the logout-options problem is avoided if Xgl and Xorg are running parallel non-nested, which is described [there](http://ubuntuforums.org/showpost.php?p=1035288&postcount=30).

All on [page 3](http://ubuntuforums.org/showthread.php?t=174233&page=3) of this thread.

---

### Post by gruvsyco on 2006-05-23
I'm using the method from the first post and it works great especially when the XGL/Compiz stuff gets broken on update like today.  I have Xgl-Gnome and Xgl-KDE sessions... I had to add the Autostart script for KDE and it worked OK except I have no control over the plugins/effects via Gset-Compiz or gconf.

Thanks for the great how-to!  This was the easiest setup I have experienced outside of Kororaa (I've installed several flavors of Linux over the last week).

---

### Post by LordMau on 2006-08-04
I think all references to 
**gnome-window-decorator**
should be updated to point to
**cgwd**

---

### Post by bluevoodoo1 on 2006-08-04
> **LordMau said:**
> I think all references to 
**gnome-window-decorator**
should be updated to point to
**cgwd**

Yes good point

---

### Post by Hitchhiker427 on 2006-08-04
First off, great tutorial!

When I first followed the instructions, everything worked fine.  I originally tried to add the commands "cgwd" and "compiz --replace gconf" to my Session > Startup programs.  When I did this, Xgl started up with my "XGL-GNOME" session just fine, but when I tried to load up my "GNOME" session it also tried to load Xgl.  Except all I got was a garbled screen and it sent me back to the logon screen.  I tried ramiro's method and it worked great!  I could switch between Gnome and Xgl-Gnome no problem.  

However, I have a new problem.  I also use Xfce on this machine, and whenever I try to log into Xfce, it gives me the garbled screen, and kicks me back to the logon screen.  I'm assuming that Xfce is trying to load Xgl at startup.  Is there any way to fix this?  Thanks.

---

### Post by hype on 2006-08-05
Are there known issues with ATI card, who handle quite badly multiple X sessions?

---

### Post by jobby on 2006-08-06
Hi, thanks for the tutorial. Bazon, your method on page 3 worked really well - fullscreen games (mmm, [Orbiter]("http://orbit.medphys.ucl.ac.uk/orbit.html")) with cedega working in the Xorg session and everything! One odd thing - my xorg is on tty9, and the Xgl session is on tty7 - I mention this in case anyone tries it and is confused :-)

---

### Post by Tiftof on 2006-08-07
jobby, thx for mentioning that! At first my xorg session was at tty8 and since yesterday it dissappeared and didn't know how to fix it but it just changed to tty9.

thx for pointing that out!

---

### Post by cius on 2006-08-12
Hitchhiker427, I'm having the same problem.  XGL-Gnome works fine, but I can't get back into just Gnome.  Same garbled screen and xorg reset sending me to GDM.  I've now found a fix for this though.  Well, it will get you back into Gnome anyhow.  When you log out of xgl-gnome and get into GDM, simply do a Ctrl+Alt+Backspace to reset X.  This seems to work for me.  Not sure what the problem is exactly, maybe XGL is still running even after you log out?

I'm also having a problem where all windows open at the top left of the screen when I'm using xgl-gnome, but their titlebars are under my gnome-panel.  This means I can't reach the close button, etc.  I have to use the move shortcut key in order to get them to pop down below the panel where I can reach the titlebar.  Anyone else had this problem?

Also, I was messing around with CGWD Themer and changed the Frame Engine from blank (what it was the first time I ran it) to one of the choices in the drop down list (Zootreeves) and all of a sudden my window decorations disappeared with only the icon in the top left corner showing up.  Again, highly annoying, any way to fix it?  I downloaded a cgwd theme from gnome-look.org, imported it and switched to it, then ran xgl-toggle in order to get my frames back.  But of course, the frames I got were of the new theme I'd just downloaded and switched to.  Changing things in cgwd seems to do nothing for me.

---

### Post by Dinerty on 2006-08-17
Please help I keep getting this error when I use cgwd

```
dinerty@dinerty-wireless:~$ cgwd
Couldn't load settings.  Reverting to defaults.
Couldn't load theme.  Reverting to defaults.

```

---

### Post by Jaka83 on 2006-10-17
I'm having some problems on Ubuntu Daper. The last time I installed XGL and Compiz it worked without a problem, but since my last clean install of the sistem I can't get Compiz to install at all. I edited the repositories as described in the guide, I did all the steps but when it comes to installing the packages this pops up...

```
jaka@jaka-desktop:~$ sudo apt-get install libglitz1 libglitz-glx1 xserver-xgl libgl1-mesa libsvg libsvg-cairo compiz compiz-gnome cgwd
Reading package lists... Done
Building dependency tree... Done
libgl1-mesa is already the newest version.
Note, selecting emerald instead of cgwd
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-plugins (>= 0.2) but it is not going to be installed
E: Broken packages

```

Can someone please help me.

---

