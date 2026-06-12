---
title: "HOWTO : Run OpenGL apps better and faster if you are using Xgl"
date: 2006-03-25
forum: Outdated Tutorials &amp; Tips
---

### Post by phoboulinos on 2006-03-25
I don't know if has been posted before but I am gonna post it since it may help may ubuntu users.

When I installed Xgl and compiz I realized that opengl games werent perfoming as they used to, so I thought "why dont I run the game one a second Xserver without Xgl and make the Xserver close after the game has exited so it would be seemless, just like I would have run it on my first Xserver?".
The only drawback in this process is that you must provide your password to gksudo to start the Xserver as root since there is no other way to start it, BUT your OpenGL application would be run as a regular user so it will use your own settings.

Here what you have to do:

First make a new xorg.conf file to set a default resolution like I did to run everything in 1024x768, if you like offcourse since most recent OpenGL games change the Xserver resolution natively ignoring your default settings so you are safe to enter the highest possible resolution.

Here's what I did

```

...
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
...

```

My first Xserver's resolution is different than the one above, I do this because Quake III uses the resolution of your Xserver and does not change it the moment you request it. Name the new Xserver config as lets say /etc/X11/xorg.conf.games 

Next, we must make a new script to start everything. Here is what I use:
```

#!/bin/sh

X :1 -ac -br -config /etc/X11/xorg.conf.games &
export DISPLAY="localhost:1"
sleep 1
su <your_username_here> -c $1
sleep 1
kill `cat /tmp/.X1-lock`


```

I put this in /usr/local/bin/Xgames
Its usage is

```

# Xgames quake3

```

I launch it through a gnome shortcut like this

```

gksudo Xgames quake3

```


Please note that I am aware that the second Xserver is launched WITHOUT access restrictions since it was a quick hack for me, if someone i willing to post how to do this using xinit I would me more then glad edit my post.

Well thats all and have fun playing....

---

### Post by mucha on 2006-03-27
Thanks works good :)

The only thing i had to do was to change

```
X :1 -ac -br -config /etc/X11/xorg.conf.games &
```
to:
```
/usr/bin/X :1 -ac -br -config /etc/X11/xorg.conf.games &
```

Because i followed this guide: [https://wiki.ubuntu.com/XglHowto](https://wiki.ubuntu.com/XglHowto)

Edit: I tested it a little more and notice that there's no sound. But when I play normal with X I got sound. Is there a way to fix this? It was quake3 arena I played.

---

### Post by phoboulinos on 2006-03-27
Have you checked whether you are running an esd daemon already or anything else ?? Try lsof /dev/dsp*

---

### Post by mucha on 2006-03-27
It seems that i dont have anything like that running. Theres no output when i run lsof /dev/dsp*

---

### Post by phoboulinos on 2006-03-27
This is not an X related problem. It has nothing to do with I have done.

---

### Post by Jason_25 on 2006-03-27
So does sound work with this method or no?

---

### Post by phoboulinos on 2006-03-28
It has nothing to do with how the X server is run, the quake3 binary uses the sound devices directly and whether is run on a X server or from svgalib (not) its not affected by it. I think you should redirected the output quake3 is printing to inspect it, like this quake3 &> q3output

---

### Post by mucha on 2006-03-28
It was a Quake3 issue, funny I thought it worked in Xorg. Anyway fixed it with [http://icculus.org/quake3/](http://icculus.org/quake3/)

Sorry for bringin this up :)

---

### Post by asdf25 on 2006-04-14
Has anyone done this using an ATI card with FGLRX driver?

I haven't been able to get it to work... it seems to make X or Xgl crash. Anyone have it working and want to tell me how they did it?

---

### Post by Grimmy on 2006-04-19
I have succeeded in running both ET and RTCW when running xgl using the instructions in this howto:

[http://www.ubuntuforums.org/showthread.php?t=51486&highlight=x.et](http://www.ubuntuforums.org/showthread.php?t=51486&highlight=x.et)

---

### Post by harnir on 2006-04-22
I made a modified version which supports multiuser systems: [http://linux.net.pl/~harnir/2006-04-22/how-to-run-sdl-and-opengl-based-games-under-xgl/](http://linux.net.pl/~harnir/2006-04-22/how-to-run-sdl-and-opengl-based-games-under-xgl/)

---

### Post by Sipheren on 2006-05-02
ok so I have done everything in the "how to"...but when I run the file I get this....

[IMG]http://home.exetel.com.au/xcalibrestudios/Xgames.png[/IMG]

---

### Post by frodon on 2006-05-02
You should really concider to use Xgame, it's a perl script designed for this purpose : [http://xgame.tlhiv.org/](http://xgame.tlhiv.org/)
Here is a usefull post to get it working quickly : [http://ubuntuforums.org/showpost.php?p=781066&postcount=13](http://ubuntuforums.org/showpost.php?p=781066&postcount=13)

---

### Post by phoboulinos on 2006-05-02
Sipheren try this
```

chmod +x /usr/local/bin/Xgames

```

Maybe I didnt include that in the howto...

---

