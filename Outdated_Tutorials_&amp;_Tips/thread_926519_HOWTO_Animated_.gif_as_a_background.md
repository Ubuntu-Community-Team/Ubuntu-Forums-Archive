---
title: "HOWTO: Animated .gif as a background"
date: 2008-09-22
forum: Outdated Tutorials &amp; Tips
---

### Post by memorygap on 2008-09-22
So you went to put that funny animated gif as your desktop background but only the first frame appeared, static and alone? Cheer up, we can make it move.
This is a guide to getting an animated gif centered on your desktop background. I've only tested it in gnome on Hardy Heron. It works with or without compiz. The only caveat is that if you happen to have icons on your desktop the gif may cover these up if it's big enough. 

Alright let's open a terminal window and get down to business.
We're going to grab Shantz modified (i.e. fixed) version of [xwinwrap]("https://launchpad.net/xwinwrap"). 
Ok we need the source from launchpad, but first we need to install bazaar to get the code, gcc to compile it, and gifsicle to actually display the gifs:
```
sudo apt-get install bzr build-essential gifsicle
```
Now let's grab the code:
```
bzr branch lp:xwinwrap
```
Let's change into that newly created directory and compile it and then install it.
```
cd xwinwrap
make
sudo make install
```

I've created a little script to make centering a gif easy for myself so open up your favorite text editor and copy and paste the following:
```
#!/bin/sh
# Uses xwinwrap to display given animated .gif in the center of the screen

if [ $# -ne 1 ]; then
    echo 1>&2 Usage: $0 image.gif
    exit 1
fi

#get screen resolution
SCRH=`xrandr | awk '/current/ { print $8 }'`
SCRW=`xrandr | awk '/current/ { print $10 }'`
SCRW=${SCRW%\,}

#get gif resolution
IMGHW=`gifsicle --info $1 | awk '/logical/ { print $3 }'`
IMGH=${IMGHW%x*}
IMGW=${IMGHW#*x}

#calculate position
POSH=$((($SCRH/2)-($IMGH/2)))
POSW=$((($SCRW/2)-($IMGW/2)))

xwinwrap -g ${IMGHW}+${POSH}+${POSW} -ov -ni -s -nf -- gifview -w WID $1 -a

exit 0
```

Save this file as gifbg.sh and let's not forget to make it executable:
```
chmod +x gifbg.sh
```
Now when we can make our background move:
```
./gifbg.sh /path/to/animated.gif
```

You'll probably want to start this script when you login so hit the gnome menu -> system -> preferences -> sessions hit Add and make up a name and copy the command into the appropriate box. Notes: You have to put the complete path to the script in here because gnome doesn't respect the $PATH variable. Also, for some reason the image will appear always on top when it's loaded from boot, one solution is to add a "sleep 5" on top of the script to make sure it loads after the rest of your desktop.

There you go, an animated background using a few megs of ram and an imperceptible amount of cpu time.

To stop the magic happening either Ctrl-C the command if you ran it from the terminal or hit Alt-F2 and type:
```
killall xwinwrap
```
To uninstall:
```
sudo rm /usr/bin/xwinwrap
```

---

### Post by thestig_992 on 2008-09-25
Does anyone have any good gifs to share? preferable some that would work as a background?

---

### Post by binbash on 2008-09-25
awesome guide, it will be cool if someone can share good gifs .

---

### Post by bcde617 on 2008-09-25
Cool topic, come on to update it. will keep an eye on it. Coolingame was established in December 25, 2004. Our head office located in Malaysia beachPenang. We focus on provide the professional power leveling services. Different to other sites we do powerleveling ONLY, no any virtual goods trade. We have our own [wow powerleveling](http://www.coolingame.com) team and this make sure that your order will be done in time with high quality. A hands-on shopping with us will immediately tell the difference. We wrecked our brains to better cater to the needs of our dear customers and constantly meliorated our services to better entertain our clients. With flying delivery, around-the-clock customer service, sophisticated order processing system and guaranteed powerleveling security, coolingame has won the trust from thousands of customers. Perhaps around your friends as well as our customers. i like [wow power leveling](http://www.coolingame.com) service.[WoW Powerleveling](http://www.levelmyth.com) & World of Warcraft power leveling service.Do you feel bored while level rate increasing process? Don't worry about that. Let LevelMyth do it for you. Trust our professional level service. We will do our best in all of our orders. We have done a great number of orders for: [WOW power leveling](http://www.levelmyth.com) US, World of Warcraft power leveling EUand other games.

---

### Post by memorygap on 2008-09-25
the gif that made me figure this out is on this page [http://squareamerica.com/gif4.htm](http://squareamerica.com/gif4.htm)

---

### Post by toucher5 on 2008-09-26
This is a little different than the animated gif but I think it is interesting.

[http://gnome-look.org/content/show.php/All+Day+Long+(Animated+Wallpaper)?content=83443](http://gnome-look.org/content/show.php/All+Day+Long+(Animated+Wallpaper)?content=83443)

Basically you make an xml file as the background that refers to the pictures of choice. It changes over time. The artist set it up to look like the sun moving in the sky.

I have one in the works and will upload it to gnome-look when its done. So keep a look out.

---

### Post by whitethorn on 2008-11-04
I wasn't able to get this to work in Ibex.  Just getting the branch downloaded from launchpad was pretty complicated (had to create a gpg and ssh key). After downloading the folder I wasn't able to make it.

> :xwinwrap|$make
gcc -Wall -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wredundant-decls -lX11 -lXext -lXrender xwinwrap.c -o xwinwrap
mkdir x86_64
mv ./xwinwrap ./x86_64
gcc -m32 -Wall -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wredundant-decls -lX11 -lXext -lXrender xwinwrap.c -o xwinwrap
mkdir i386
mv ./xwinwrap ./i386
:xwinwrap|$sudo make install
make: *** No rule to make target `install'.  Stop.


It's really too bad, I was about to use the hypnotoad gif.

[http://www.stumbleupon.com/toolbar/#topic=Humor&url=http%253A%252F%252Fgallery2.jpmullan.com%252Fv%252Fscans%252Fblog%252Fhypnotoad.gif.html%253Fg2_imageViewsIndex%253D1](http://www.stumbleupon.com/toolbar/#topic=Humor&url=http%253A%252F%252Fgallery2.jpmullan.com%252Fv%252Fscans%252Fblog%252Fhypnotoad.gif.html%253Fg2_imageViewsIndex%253D1)

---

### Post by kranny on 2009-02-04
This is what i get when i try to compile

```

gcc -Wall -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wredundant-decls -lX11 -lXext -lXrender xwinwrap.c -o xwinwrap
xwinwrap.c:39:22: error: X11/Xlib.h: No such file or directory
xwinwrap.c:40:23: error: X11/Xutil.h: No such file or directory
xwinwrap.c:41:23: error: X11/Xatom.h: No such file or directory
xwinwrap.c:42:24: error: X11/Xproto.h: No such file or directory
xwinwrap.c:44:34: error: X11/extensions/shape.h: No such file or directory
xwinwrap.c:45:36: error: X11/extensions/Xrender.h: No such file or directory
xwinwrap.c:97: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
xwinwrap.c:110: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
xwinwrap.c:177: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;find_desktop_window&#8217;
xwinwrap.c: In function &#8216;main&#8217;:
xwinwrap.c:219: error: &#8216;Display&#8217; undeclared (first use in this function)
xwinwrap.c:219: error: (Each undeclared identifier is reported only once
xwinwrap.c:219: error: for each function it appears in.)
xwinwrap.c:219: error: &#8216;dpy&#8217; undeclared (first use in this function)
xwinwrap.c:220: error: &#8216;Window&#8217; undeclared (first use in this function)
xwinwrap.c:220: error: expected &#8216;;&#8217; before &#8216;win&#8217;
xwinwrap.c:221: error: expected &#8216;;&#8217; before &#8216;root&#8217;
xwinwrap.c:222: error: expected &#8216;;&#8217; before &#8216;p_desktop&#8217;
xwinwrap.c:224: error: &#8216;XSizeHints&#8217; undeclared (first use in this function)
xwinwrap.c:224: error: expected &#8216;;&#8217; before &#8216;xsh&#8217;
xwinwrap.c:225: error: &#8216;XWMHints&#8217; undeclared (first use in this function)
xwinwrap.c:225: error: expected &#8216;;&#8217; before &#8216;xwmh&#8217;
xwinwrap.c:240: error: &#8216;Atom&#8217; undeclared (first use in this function)
xwinwrap.c:240: error: expected &#8216;;&#8217; before &#8216;state&#8217;
xwinwrap.c:244: error: &#8216;Pixmap&#8217; undeclared (first use in this function)
xwinwrap.c:244: error: expected &#8216;;&#8217; before &#8216;mask&#8217;
xwinwrap.c:245: error: &#8216;GC&#8217; undeclared (first use in this function)
xwinwrap.c:245: error: expected &#8216;;&#8217; before &#8216;mask_gc&#8217;
xwinwrap.c:246: error: &#8216;XGCValues&#8217; undeclared (first use in this function)
xwinwrap.c:246: error: expected &#8216;;&#8217; before &#8216;xgcv&#8217;
xwinwrap.c:248: warning: implicit declaration of function &#8216;XOpenDisplay&#8217;
xwinwrap.c:255: warning: implicit declaration of function &#8216;DefaultScreen&#8217;
xwinwrap.c:256: error: &#8216;root&#8217; undeclared (first use in this function)
xwinwrap.c:256: warning: implicit declaration of function &#8216;RootWindow&#8217;
xwinwrap.c:263: warning: implicit declaration of function &#8216;XParseGeometry&#8217;
xwinwrap.c:275: error: &#8216;state&#8217; undeclared (first use in this function)
xwinwrap.c:275: warning: implicit declaration of function &#8216;XInternAtom&#8217;
xwinwrap.c:357: error: &#8216;xsh&#8217; undeclared (first use in this function)
xwinwrap.c:357: error: &#8216;PSize&#8217; undeclared (first use in this function)
xwinwrap.c:357: error: &#8216;PPosition&#8217; undeclared (first use in this function)
xwinwrap.c:358: warning: implicit declaration of function &#8216;DisplayWidth&#8217;
xwinwrap.c:359: warning: implicit declaration of function &#8216;DisplayHeight&#8217;
xwinwrap.c:368: error: &#8216;xwmh&#8217; undeclared (first use in this function)
xwinwrap.c:368: error: &#8216;InputHint&#8217; undeclared (first use in this function)
xwinwrap.c:373: error: &#8216;XSetWindowAttributes&#8217; undeclared (first use in this function)
xwinwrap.c:373: error: expected &#8216;;&#8217; before &#8216;attr&#8217;
xwinwrap.c:374: error: &#8216;Visual&#8217; undeclared (first use in this function)
xwinwrap.c:374: error: &#8216;visual&#8217; undeclared (first use in this function)
xwinwrap.c:376: warning: implicit declaration of function &#8216;findArgbVisual&#8217;
xwinwrap.c:383: error: &#8216;attr&#8217; undeclared (first use in this function)
xwinwrap.c:385: warning: implicit declaration of function &#8216;XCreateColormap&#8217;
xwinwrap.c:385: error: &#8216;AllocNone&#8217; undeclared (first use in this function)
xwinwrap.c:387: error: &#8216;win&#8217; undeclared (first use in this function)
xwinwrap.c:387: warning: implicit declaration of function &#8216;XCreateWindow&#8217;
xwinwrap.c:388: error: &#8216;InputOutput&#8217; undeclared (first use in this function)
xwinwrap.c:389: error: &#8216;CWBackPixel&#8217; undeclared (first use in this function)
xwinwrap.c:389: error: &#8216;CWBorderPixel&#8217; undeclared (first use in this function)
xwinwrap.c:389: error: &#8216;CWColormap&#8217; undeclared (first use in this function)
xwinwrap.c:393: error: expected &#8216;;&#8217; before &#8216;attr&#8217;
xwinwrap.c:396: warning: implicit declaration of function &#8216;find_desktop_window&#8217;
xwinwrap.c:396: error: &#8216;p_desktop&#8217; undeclared (first use in this function)
xwinwrap.c:399: error: &#8216;CopyFromParent&#8217; undeclared (first use in this function)
xwinwrap.c:400: error: &#8216;CWOverrideRedirect&#8217; undeclared (first use in this function)
xwinwrap.c:410: warning: implicit declaration of function &#8216;XSetWMProperties&#8217;
xwinwrap.c:413: warning: implicit declaration of function &#8216;setWindowOpacity&#8217;
xwinwrap.c:417: error: &#8216;Region&#8217; undeclared (first use in this function)
xwinwrap.c:417: error: expected &#8216;;&#8217; before &#8216;region&#8217;
xwinwrap.c:419: error: &#8216;region&#8217; undeclared (first use in this function)
xwinwrap.c:419: warning: implicit declaration of function &#8216;XCreateRegion&#8217;
xwinwrap.c:422: warning: implicit declaration of function &#8216;XShapeCombineRegion&#8217;
xwinwrap.c:422: error: &#8216;ShapeInput&#8217; undeclared (first use in this function)
xwinwrap.c:422: error: &#8216;ShapeSet&#8217; undeclared (first use in this function)
xwinwrap.c:423: warning: implicit declaration of function &#8216;XDestroyRegion&#8217;
xwinwrap.c:428: warning: implicit declaration of function &#8216;XChangeProperty&#8217;
xwinwrap.c:429: error: &#8216;XA_ATOM&#8217; undeclared (first use in this function)
xwinwrap.c:429: error: &#8216;PropModeReplace&#8217; undeclared (first use in this function)
xwinwrap.c:434: error: &#8216;mask&#8217; undeclared (first use in this function)
xwinwrap.c:434: warning: implicit declaration of function &#8216;XCreatePixmap&#8217;
xwinwrap.c:435: error: &#8216;mask_gc&#8217; undeclared (first use in this function)
xwinwrap.c:435: warning: implicit declaration of function &#8216;XCreateGC&#8217;
xwinwrap.c:435: error: &#8216;xgcv&#8217; undeclared (first use in this function)
xwinwrap.c:442: warning: implicit declaration of function &#8216;XSetForeground&#8217;
xwinwrap.c:443: warning: implicit declaration of function &#8216;XFillRectangle&#8217;
xwinwrap.c:446: warning: implicit declaration of function &#8216;XFillArc&#8217;
xwinwrap.c:451: error: &#8216;XPoint&#8217; undeclared (first use in this function)
xwinwrap.c:451: error: expected &#8216;;&#8217; before &#8216;points&#8217;
xwinwrap.c:459: warning: implicit declaration of function &#8216;XFillPolygon&#8217;
xwinwrap.c:459: error: &#8216;points&#8217; undeclared (first use in this function)
xwinwrap.c:459: error: &#8216;Complex&#8217; undeclared (first use in this function)
xwinwrap.c:459: error: &#8216;CoordModeOrigin&#8217; undeclared (first use in this function)
xwinwrap.c:469: warning: implicit declaration of function &#8216;XShapeCombineMask&#8217;
xwinwrap.c:469: error: &#8216;ShapeBounding&#8217; undeclared (first use in this function)
xwinwrap.c:472: warning: implicit declaration of function &#8216;XMapWindow&#8217;
xwinwrap.c:476: warning: implicit declaration of function &#8216;XLowerWindow&#8217;
xwinwrap.c:479: warning: implicit declaration of function &#8216;XSync&#8217;
xwinwrap.c:513: warning: implicit declaration of function &#8216;XDestroyWindow&#8217;
xwinwrap.c:514: warning: implicit declaration of function &#8216;XCloseDisplay&#8217;
make: *** [all64] Error 1

```

---

### Post by Bachstelze on 2009-03-23
@kranny

```
sudo apt-get install xorg-dev
```

---

### Post by [.root/fail] on 2009-04-03
This is after getting the stuff from the post before me and running the rest of the first post I could:



fail@dotroot:~/xwinwrap$ cd xwinwrap
bash: cd: xwinwrap: No such file or directory
fail@dotroot:~/xwinwrap$ make
gcc -Wall -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wredundant-decls -lX11 -lXext -lXrender xwinwrap.c -o xwinwrap
mkdir x86_64
mv ./xwinwrap ./x86_64
gcc -m32 -Wall -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wredundant-decls -lX11 -lXext -lXrender xwinwrap.c -o xwinwrap
In file included from /usr/include/features.h:354,
                 from /usr/include/sys/types.h:27,
                 from /usr/include/X11/Xlib.h:52,
                 from xwinwrap.c:45:
/usr/include/gnu/stubs.h:7:27: error: gnu/stubs-32.h: No such file or directory
make: *** [all32] Error 1
fail@dotroot:~/xwinwrap$ sudo make install
[sudo] password for kyo: 
make: *** No rule to make target `install'.  Stop.
fail@dotroot:~/xwinwrap$

---

### Post by Earl_Maroon on 2009-05-05
> **whitethorn said:**
> I wasn't able to get this to work in Ibex.  Just getting the branch downloaded from launchpad was pretty complicated (had to create a gpg and ssh key). After downloading the folder I wasn't able to make it.



It's really too bad, I was about to use the hypnotoad gif.

[http://www.stumbleupon.com/toolbar/#topic=Humor&url=http%253A%252F%252Fgallery2.jpmullan.com%252Fv%252Fscans%252Fblog%252Fhypnotoad.gif.html%253Fg2_imageViewsIndex%253D1](http://www.stumbleupon.com/toolbar/#topic=Humor&url=http%253A%252F%252Fgallery2.jpmullan.com%252Fv%252Fscans%252Fblog%252Fhypnotoad.gif.html%253Fg2_imageViewsIndex%253D1)
@ Whitethorn:

This happened to me too. All that has happened is that the winwrap ececutable file hasn't been moved to /usr/bin, which isn't too much of a problem. You could move it or alter the script to direct to the file. Depending on your architecture the file to direct to is in i386 or x86_64 in the winwrap directory.

---

### Post by asm_Coty on 2009-05-05
Fascinating tutorial, I will be sure to pass this one on :D

---

### Post by angels21usa on 2010-01-12
Hey,

I just want to say thank you for the HOWTO. I got the xwinwrapper working with my gif images. When I start it the gifs initially show up in the background, but when I click on the image it covers up all of my other programs including the panels. I was wondering if anyone might know a way to keep the gif image on the desktop even when it is clicked.

Thanks for any help in advance

---

### Post by Chiapo on 2010-01-17
Awesome! 

I especially like post #5) [http://ubuntuforums.org/showpost.php?p=5858279&postcount=5](http://ubuntuforums.org/showpost.php?p=5858279&postcount=5)

What a wonderful concept using xml to change the image!

For myself, I prefer to create my own animations using gimp, or a free online service like [http://imator.com/](http://imator.com/)

Thanks for sharing!

---

### Post by d3v1150m471c on 2010-03-15
```

mplayer -gif89a yourvideo.avi

```
You can use mplayer like so to create gif animations from video.

---

### Post by TheProphetJonah on 2011-06-04
I couldn't get the .c file to "make" so make install just gave me the old familiar "no rule to make install -stop" message.
So I left out of that and went looking for a .deb file and found it on mediafire xwinwrap_1386.deb dl'ed it and dpkg'ed it.
I'm assuming it's going to work.

From my limited reading on the possible uses, it seems that I can use the gif as a background in any xwindow, yes/no?

Hopefully. But I've got this really cool word-by-word or chunk-by-chunk text reader called "dictator", got Orca and this really simple hipno-spiral that will stretch  across the desktop or any window.

Bam, instant hypnosis session where I can insert any text I want.

Hopefully it will work, one other thing though, no worries or hurries, but does either the gif tool or xwinwrap make it a transparent layer?
Da Gimp has a tool that supposedly works for that but I've not advanced that far.

---

### Post by el_itur on 2011-10-26
This gif would make a great wallpaper 

[[IMG]http://i.imgur.com/l3LL3.gif[/IMG]]("http://i.imgur.com/l3LL3.gif")

I would love to see some native solution :D

---

### Post by Angelus-Michael on 2011-10-26
Awesome. Respect man

---

### Post by DrDunkMcNally on 2012-05-17
> **'[.root/fail] said:**
> This is after getting the stuff from the post before me and running the rest of the first post I could:



fail@dotroot:~/xwinwrap$ cd xwinwrap
bash: cd: xwinwrap: No such file or directory
fail@dotroot:~/xwinwrap$ make
gcc -Wall -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wredundant-decls -lX11 -lXext -lXrender xwinwrap.c -o xwinwrap
mkdir x86_64
mv ./xwinwrap ./x86_64
gcc -m32 -Wall -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wredundant-decls -lX11 -lXext -lXrender xwinwrap.c -o xwinwrap
In file included from /usr/include/features.h:354,
                 from /usr/include/sys/types.h:27,
                 from /usr/include/X11/Xlib.h:52,
                 from xwinwrap.c:45:
/usr/include/gnu/stubs.h:7:27: error: gnu/stubs-32.h: No such file or directory
make: *** [all32] Error 1
fail@dotroot:~/xwinwrap$ sudo make install
[sudo] password for kyo: 
make: *** No rule to make target `install'.  Stop.
fail@dotroot:~/xwinwrap$

It seems like this is because you must choose which install you are going to run with from the "Makefile" if you wrote "sudo make install32" it would work for you, 64-bit would use "sudo make install64"

I followed all of the op's instructions but i'm facing an issue of my own, I got my exploding heads gif on my background (had to add sleep 5 to the script) but as soon as there are no windows open, xwinwrap jumps to the front again and I've got exploding zombie heads right in the middle of everything. any ideas how to prevent this?

here's the gif (it's small, but it's still great!)

*edit:* So upon further investigation, the gif will stay in the background unless I happen to click on it at which point it sits in the middle of the screen on top of everything. i haven't changed the gifbg.sh options.

---

### Post by hanusjoe03 on 2013-06-21
[SIZE=4]This does not work for me. I have ubuntu 12.4 and when i entered the code: 
[/SIZE]

```
bzr branch lp:xwinwrap
```

i get this error:

[SIZE=4][B][COLOR=#ff0000]You have not informed bzr of your Launchpad ID, and you must do this to
write to Launchpad or access private data.  See "bzr help launchpad-login".
bzr: ERROR: Already a branch: "xwinwrap".[/COLOR][/B][/SIZE]

How do i fix this and continue with the install so i can enjoy my Ubnutu with animated .gif?

Also Would this be something Ubuntu will add native with a new version of Ubuntu?

It would be nice to be able to use .gif as wallpaper as easy as it is to 
change the wallpaper (.jpg) from a fresh install of Ubuntu.

---

### Post by zach832 on 2013-07-05
Im really interested in this howto but im getting some strange errors that I dont know how to fix. This is right after running brz branch lp:xwinwrap. Im guessing im missing a package somewhere?

```
~/xwinwrap$ make
gcc -Wall -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wredundant-decls -lX11 -lXext -lXrender xwinwrap.c -o xwinwrap
/tmp/ccG67lai.o: In function `setWindowOpacity':
xwinwrap.c:(.text+0xdf): undefined reference to `XInternAtom'
xwinwrap.c:(.text+0x113): undefined reference to `XChangeProperty'
/tmp/ccG67lai.o: In function `findArgbVisual':
xwinwrap.c:(.text+0x151): undefined reference to `XGetVisualInfo'
xwinwrap.c:(.text+0x19c): undefined reference to `XRenderFindVisualFormat'
xwinwrap.c:(.text+0x1ed): undefined reference to `XFree'
/tmp/ccG67lai.o: In function `find_desktop_window':
xwinwrap.c:(.text+0x337): undefined reference to `XQueryTree'
xwinwrap.c:(.text+0x379): undefined reference to `XFetchName'
xwinwrap.c:(.text+0x3b2): undefined reference to `XGetWindowAttributes'
xwinwrap.c:(.text+0x444): undefined reference to `XFree'
xwinwrap.c:(.text+0x453): undefined reference to `XFree'
xwinwrap.c:(.text+0x488): undefined reference to `XFree'
/tmp/ccG67lai.o: In function `main':
xwinwrap.c:(.text+0x5a7): undefined reference to `XOpenDisplay'
xwinwrap.c:(.text+0x6cc): undefined reference to `XParseGeometry'
xwinwrap.c:(.text+0x7f6): undefined reference to `XInternAtom'
xwinwrap.c:(.text+0x864): undefined reference to `XInternAtom'
xwinwrap.c:(.text+0x8c8): undefined reference to `XInternAtom'
xwinwrap.c:(.text+0x92c): undefined reference to `XInternAtom'
xwinwrap.c:(.text+0x990): undefined reference to `XInternAtom'
/tmp/ccG67lai.o:xwinwrap.c:(.text+0x9f4): more undefined references to `XInternAtom' follow
/tmp/ccG67lai.o: In function `main':
xwinwrap.c:(.text+0xe84): undefined reference to `XCreateColormap'
xwinwrap.c:(.text+0xef9): undefined reference to `XCreateWindow'
xwinwrap.c:(.text+0xfaf): undefined reference to `XCreateWindow'
xwinwrap.c:(.text+0x1021): undefined reference to `XCreateWindow'
xwinwrap.c:(.text+0x107b): undefined reference to `XSetWMProperties'
xwinwrap.c:(.text+0x10b1): undefined reference to `XCreateRegion'
xwinwrap.c:(.text+0x10f9): undefined reference to `XShapeCombineRegion'
xwinwrap.c:(.text+0x1108): undefined reference to `XDestroyRegion'
xwinwrap.c:(.text+0x112a): undefined reference to `XInternAtom'
xwinwrap.c:(.text+0x1169): undefined reference to `XChangeProperty'
xwinwrap.c:(.text+0x119e): undefined reference to `XCreatePixmap'
xwinwrap.c:(.text+0x11ca): undefined reference to `XCreateGC'
xwinwrap.c:(.text+0x1208): undefined reference to `XSetForeground'
xwinwrap.c:(.text+0x1242): undefined reference to `XFillRectangle'
xwinwrap.c:(.text+0x1260): undefined reference to `XSetForeground'
xwinwrap.c:(.text+0x12aa): undefined reference to `XFillArc'
xwinwrap.c:(.text+0x1315): undefined reference to `XSetForeground'
xwinwrap.c:(.text+0x134f): undefined reference to `XFillRectangle'
xwinwrap.c:(.text+0x136d): undefined reference to `XSetForeground'
xwinwrap.c:(.text+0x13a4): undefined reference to `XFillPolygon'
xwinwrap.c:(.text+0x13de): undefined reference to `XShapeCombineMask'
xwinwrap.c:(.text+0x13f7): undefined reference to `XMapWindow'
xwinwrap.c:(.text+0x141c): undefined reference to `XLowerWindow'
xwinwrap.c:(.text+0x1436): undefined reference to `XSync'
xwinwrap.c:(.text+0x1575): undefined reference to `XDestroyWindow'
xwinwrap.c:(.text+0x1584): undefined reference to `XCloseDisplay'
collect2: error: ld returned 1 exit status
make: *** [all64] Error 1
```

---

### Post by blackhouse2 on 2014-02-27
Hey, guys!

I managed to get the GIF working, but it showes up only as the session is loading. Then, as the desktop shows, is just disappears and leaves me with a blank black background... Any ideas? Thanks in advance!

---

### Post by umithaz on 2014-02-28
It's a new info for me. I'll try it soon. Thanks, this is awesome how to tutorial. :rolleyes:

---

### Post by andrew103 on 2014-03-17
with Ibex didn`t worked for me also, any other solution?

---

### Post by firas2 on 2014-08-01
Hi I am on step 3  and i get this error   any help  thank u 


ubuntu@ubuntu:~/xwinwrap$ cd xwinwrap
bash: cd: xwinwrap: No such file or directory
ubuntu@ubuntu:~/xwinwrap$ cd xwinwrap
bash: cd: xwinwrap: No such file or directory
ubuntu@ubuntu:~/xwinwrap$ make
gcc -Wall -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wredundant-decls -lX11 -lXext -lXrender xwinwrap.c -o xwinwrap
xwinwrap.c:45:22: fatal error: X11/Xlib.h: No such file or directory
 #include <X11/Xlib.h>
                      ^
compilation terminated.
make: *** [all64] Error 1
ubuntu@ubuntu:~/xwinwrap$ sudo make install
make: *** No rule to make target `install'.  Stop.
ubuntu@ubuntu:~/xwinwrap$

---

