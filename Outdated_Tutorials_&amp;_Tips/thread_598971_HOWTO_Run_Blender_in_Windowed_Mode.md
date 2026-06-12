---
title: "HOWTO: Run Blender in Windowed Mode"
date: 2007-10-31
forum: Outdated Tutorials &amp; Tips
---

### Post by jelly on 2007-10-31
When you install Blender it creates two menu items: one for fullscreen mode and one for windowed mode.  For some reason, windowed mode has never worked for me - even with the latest version in Gutsy - it always opens in full screen.

You can solve this by explicitly specifying the position and dimensions of the window using the command-line option -p.  From the blender help (blender --help):

```

-p <sx> <sy> <w> <h>  Open with lower left corner at <sx>, <sy> 
                      and width and height <w>, <h>

```

For example, I have a 1280x1024 desktop.  I want Blender to open as a 1024x768 window in the top left corner of the desktop - with a little padding.  I found that the following options did what I needed:

```

blender -p 5 225 1024 768

```

What these options are saying:
[LIST]
[*]I want the left edge of the blender window to be 5 pixels from the left edge of the screen.
[*]I want the *bottom* edge of the blender window to be 225 pixels from the *bottom* edge of the screen.
[*]The blender window will be 1024 pixels wide.
[*]The blender window will be 768 pixels high.
[/LIST]

You might need to play with these settings to get them right for your tastes, which you can do from the terminal.  Anyway, when it's open in windowed mode - you can then simply move / resize the window as normal - and even open multiple instances.  Neat!

If you want to change your Gnome Applications menu entry for blender to use these settings by default, simply:

[LIST=1]
[*]Go to System / Preferences / Main Menu *(in Gnome, not blender)*
[*]Navigate to Applications / Graphics
[*]Right-click on 'Blender 3D modeller (windowed)' and select properties, which opens up a window for you to edit that menu item. *(It sometimes appears out of focus below my other windows for some reason, but you can select it from the task bar).*
[*]Change command to be the blender command with your size / position options.
[*]Press Close and you're done.
[/LIST]

- Jelly.

---

### Post by Sabaki on 2007-11-08
Thanks! Just what I needed. This worked perfectly in Gutsy 64.

Chuck

---

### Post by jharris on 2008-01-01
Top tip! This was bugging me for a short while until I searched here for a solution. Works great on my Gutsy 64 too! Thanks so much.

---

### Post by melopsittacus on 2008-01-02
Well no wonder the two launchers were both opening the full screen mode: their commands were identical: ```
blender -W
```:) Thanks for the tip!

---

### Post by thedaemon on 2008-01-21
Thanks. This should be fixed. Any idea how we can get it fixed? This is a major problem imho.

---

### Post by ewanchic on 2008-02-12
Thanks Jelly. This is exactly what I need!

---

### Post by Anduu on 2008-02-13
That deserves a star

:KS

---

### Post by thedaemon on 2008-02-14
The SVN version on graphicall.org doesn't have this problem. Strange. I wish I could update the repository version at least to 2.45!

---

### Post by loop444 on 2008-05-06
This problem is still existent, and sucks, to this day, just got Blender from the ubuntu menu (gutsy).

---

### Post by nsingapu on 2008-06-26
there is a bug with compiz fusion effects enabled that prevents windowed mode
for me following the instructions at 
[https://bugs.launchpad.net/ubuntu/+source/blender/+bug/221651](https://bugs.launchpad.net/ubuntu/+source/blender/+bug/221651) fixed it.

---

### Post by Sean-Michael on 2008-08-27
Thanks a billion!  This was bugging me for a while now!

---

### Post by plus on 2008-12-01
thank you very much!it solved the same problem for blender in 8.10

---

### Post by bahram3d on 2009-03-13
thanks for the tip:popcorn:

---

### Post by harakiri1976 on 2009-03-14
Thanks a lot! :)

---

### Post by SwedishWings on 2009-06-10
I have similar problems with Compiz...

Starting blender with
```
blender -p 5 225 1024 768
```
creates a window _without decorations_. However, if i disable Compiz (via Compiz fusion icon) start blender, then enable Compiz again, all works.

I use Ubuntu 9.04 and ATI (X600).

Any suggestions on how to fix this?

Thanks,
Mike

---

