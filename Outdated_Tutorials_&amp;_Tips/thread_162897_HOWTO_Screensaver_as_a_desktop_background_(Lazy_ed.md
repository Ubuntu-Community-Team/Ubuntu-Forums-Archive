---
title: "HOWTO: Screensaver as a desktop background (Lazy edition)"
date: 2006-04-19
forum: Outdated Tutorials &amp; Tips
---

### Post by Nequeo on 2006-04-19
This is a neat, though rather useless, piece of Eyecandy that is mostly useful as a way of showing up your Windows friends. 

You may or may not be aware that, in Prehistoric times, cute little programs that drew things like mountains, fractals, cockroaches or even ants all over your ['root window']("http://en.wikipedia.org/wiki/Root_window") were quite common. Now - funny thing. Xscreensaver works by creating a 'virtual' root window over the top of everything else, and then drawing cool stuff on it. As you might imagine, it's rather simple to tell Linux screensavers to draw themselves onto the *real* root window, rather than creating a virtual one. 

Many minimal window managers, like Fluxbox, leave the root window exposed, so this trick works nicely. Gnome, however, draws your desktop all over the top of it, so nothing you do to the root window is visible. 

You could install Fluxbox - but what if you're more comfortable Gnome? You can run a Gnome session and Gnome panels on top of Fluxbox... But if all you want is a quick demonstration to impress friends, there is a much quicker and easier way. 

First thing we need to do is stop Gnome, or rather Nautilus, from drawing over the top of your root window. 

1. Open a terminal window, or hit Alt-F2, and type in 'gconf-editor'. You'll end up with something that looks spookily similar to the registry editor in Windows.

2. Browse to 'apps/nautilus/preferences/' and set the 'show_desktop' key to 'false'. NOTE: Your desktop icons will vanish. 

3. From a terminal window, type '/usr/lib/xscreensaver/glmatrix -root'

4. Enjoy!

5. To stop the screensaver, hit ctrl+C, or close the terminal window. To get your Gnome background and icons back repeat steps 1 and 2, but change 'show_desktop' to true. 

Any of the programs in /usr/lib/xscreensaver will work with this trick, though some are rather more distracting than others. The 'fuzzy snowflakes' screensaver (I forget what the executable is called) that comes with Dapper also works particularly well. 

Things to try:

* Add an & after the screen saver command (i.e. /usr/lib/xscreensaver -root &) to background the process. This will let you continue working in the same terminal. But you'll need to understand how to [manage processes]("http://www.comptechdoc.org/os/linux/commands/linux_crprocman.html") in order to stop it. 

* Transparent terminals won't look as cool with a screensaver background - because they are not really transparent. I haven't tried this (yet), but with the latest Xgl and Compiz you could probably create neat translucent terminals that actually do show the screensaver running underneath.

---

### Post by n8bounds on 2006-05-04
Pretty neat, the GLMatrix looks nice

---

### Post by Monk22 on 2006-05-05
is there anyway to get electricsheep to work with this hack?  i tried replacing the glmatrix with electric sheep but it just said "bad option -root"

---

### Post by parktownprawn on 2006-05-05
rather than open the (irritating) gconf tool you can just cut and paste:

```

gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false

```

to recover your desktop type
```

gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop true

```

(you may need to restart nautilus)

for instant gratifiction you could make a script containing:

```

gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false
/usr/lib/xscreensaver/glmatrix -root

```

---

### Post by terminalspin on 2006-07-01
[QUOTE=Monk22]is there anyway to get electricsheep to work with this hack?  i tried replacing the glmatrix with electric sheep but it just said "bad option -root"[/QUOTE]

As long as you have the electricsheep package installed, you should be able to start it with :-

[FONT="Courier New"]electricsheep --zoom 1 --root 1[/FONT]

...without the /usr/lib/xscreensaver / bit.

---

### Post by NeoGreen on 2006-07-02
Coooool:p

---

### Post by NESFreak on 2006-07-04
pwnage! dude

---

### Post by eldaria on 2006-07-05
Any Idea of how to do this on Kubuntu?

---

### Post by cosimo on 2008-03-05
Hey guys,
I didnt bother to see how old this post is however, haveing a screensaver as a desktop background is easy and does not require disabling nautilus from writing the desktop!
All you need is xwinwrap written by Dave Raveman creator of compiz and coolbg  created by cyberorg one of the compiz fusion developers.
thats it!!
NO disabling nautilus at all!
coz

---

### Post by hollerith on 2008-05-17
I tried this with 8.04 and the desktop background still obscures the root window even with show_desktop false or by using xwinwrap either.  

xmatrix appears on the background as does mplayer but not glmatrix or xscreensaver-getimage which appears behind.

---

### Post by martinw89 on 2008-07-03
Just a quick note, seems Compiz doesn't expect this so you may get surprising results if you do this with Compiz effects enabled.

---

