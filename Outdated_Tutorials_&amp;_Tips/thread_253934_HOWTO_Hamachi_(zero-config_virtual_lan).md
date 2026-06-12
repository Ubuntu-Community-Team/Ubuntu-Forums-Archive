---
title: "HOWTO: Hamachi (zero-config virtual lan)"
date: 2006-09-09
forum: Outdated Tutorials &amp; Tips
---

### Post by greeklegend on 2006-09-09
Hamachi=program that makes a virtual LAN on Windows, MacOS and Linux
Ghamachi=graphical frontend to hamachi
This .deb=install with ```
dpkg -i (path to hamachi-0.9.deb)/hamachi-0.9.deb
``` where(path to hamachi-0.9.deb is the path you downloaded hamachi-0.9.deb into. Just double click and hit install, and start the program by running the command ```
ghamachi
```
Easy.

---

### Post by Blairboy on 2006-09-09
It would be easy if you provided the link to the debs.

---

### Post by HAARP on 2006-09-09
When you reboot and hamachi suddenly stops working:
```
sudo tuncfg
```

When tuncfg complains about a missing TUN/TAP device:
```
sudo mknod /dev/net/tun c 10 200
```

---

### Post by Izuil on 2006-09-10
Ok, so i've installed hamachi but it gives me: hamachi could not be started when i try to start ghamachi.

```
sudo hamachi start
```
says that hamachi starts logs in and works :S
what's the problem?

---

### Post by Richieeeeeee on 2006-10-16
Where I can find this .deb file?

Thanks!

Richie

---

### Post by NevidS on 2006-10-17
I know how to save the world
> dpkg -i save_the_world.deb
 but I forgot where download the package :mrgreen: 

Okokok, sorry, BUT: where we can download the .deb file???]:confused:

---

### Post by HAARP on 2006-10-17
Since noone seems to be able to upload a package, here's mine.

---

### Post by jpkotta on 2006-11-14
I haven't tried this yet but it looks pretty good.

[http://forums.hamachi.cc/viewtopic.php?t=5974&sid=c60cc0a04c1fea97fe7c4a21c865312a](http://forums.hamachi.cc/viewtopic.php?t=5974&sid=c60cc0a04c1fea97fe7c4a21c865312a)

---

### Post by mrashley on 2006-12-08
Just so no one else has to google too much.

I'm using Edgy Eft (with nothing too funky installed)

I downloaded [Hamachi Version 9.9.9-20]("http://files.hamachi.cc/linux/hamachi-0.9.9.9-20-lnx.tar.gz") from the hamachi site.

I unzipped it onto my desktop then opened a terminal.

```

cd Desktop/hamachi-0.9.9.9-20-lnx
sudo make install

```
This puts all the hamachi bits into the right places.
I tried to run gHamachi at this point, but it didn't like my lack of any login information.

I couldn't remember my old network password so I made a new network.
```

hamachi start
hamachi set-nick {username}
hamachi login
hamachi create {networkname} {password}

```

Then, after having extracted the [GTK2 version from the gHamachi site,]("http://www.penguinbyte.com/software/ghamachi/download/2/?filename=gHamachi_gtk2.tar.gz") I ran gHamachi and it worked.... kinda

It's not got all it's pretty colours on the site screenshots and is giving me these errors:

```
(ghamachi:12134): Gdk-WARNING **: The gdk_draw_*_image require the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(ghamachi:12134): Gtk-CRITICAL **: gtk_pixmap_set: assertion `gdk_colormap_get_visual (gtk_widget_get_colormap (GTK_WIDGET (pixmap)))->depth == gdk_drawable_get_depth (GDK_DRAWABLE (val))' failed

(ghamachi:12134): Gdk-CRITICAL **: gdk_draw_drawable: assertion `src != NULL' failed

```

There were lines and lines of them. I've no time to figure out what they mean at the moment..

I hope this helps someone! :-D

Hamachi is at [http://hamachi.cc/](http://hamachi.cc/)
gHamachi is at [http://www.penguinbyte.com/software/ghamachi/](http://www.penguinbyte.com/software/ghamachi/)

Thanks to the authors of these programs. :-) They're very helpful.

Oh quick last minute addition - I did this on a 6.06 machine and gHamachi worked beautifully without all the pre-configuring nonsense. I guess it's a problem with Edgy and gHamachi not liking eachother much. Any suggestion for a fix would be great!!

---

### Post by abacate on 2007-02-18
I tried looking into this on the hamachi for linux forums but those aren't really much help..

Just installed my hamachi and gHamachi and they seem to be running ok, but I'm still having trouble with multiplayer games. I can see everyone online on the network and I hear I'm showing green for them as well. Still for some reason I can't even see the games I should be joining. The other people on the network, including the owner, are using WinXP.

The game I was trying out was Warcraft 3 - The Frozen Throne. Is there some known trouble with hamachi and TransGaming Cedega or is there just something I'm not noticing?

---

### Post by Dabrorius on 2007-11-12
I have installed Hamachi and everything seemed to be ok but when I type in

hamachi start

or just

hamachi

i get no response (no errors, nothing happens)

what could be the problem?

i tried installing from both .deb and standard install

---

### Post by nutter78 on 2007-11-13
> **Dabrorius said:**
> I have installed Hamachi and everything seemed to be ok but when I type in

hamachi start

or just

hamachi

i get no response (no errors, nothing happens)

what could be the problem?

i tried installing from both .deb and standard install

- Having same problem here - will post if i find solution 
- also for people having problems with gHamachi - try the  beta one - check there site - it's currently ver: 0.8.1

---

### Post by paulg on 2007-11-16
Let me guess, Gutsy? If you're using Gutsy, this should fix the problem for you.

sudo aptitude install upx-ucl
upx -d /usr/bin/hamachi

See this thread [here]("http://ubuntuforums.org/showthread.php?t=553774&highlight=gutsy+hamachi") for more information.

---

### Post by misse- on 2008-03-14
> **abacate said:**
> I tried looking into this on the hamachi for linux forums but those aren't really much help..

Just installed my hamachi and gHamachi and they seem to be running ok, but I'm still having trouble with multiplayer games. I can see everyone online on the network and I hear I'm showing green for them as well. Still for some reason I can't even see the games I should be joining. The other people on the network, including the owner, are using WinXP.

The game I was trying out was Warcraft 3 - The Frozen Throne. Is there some known trouble with hamachi and TransGaming Cedega or is there just something I'm not noticing?

I have exactly the same problem. Does anyone know a solution?

---

