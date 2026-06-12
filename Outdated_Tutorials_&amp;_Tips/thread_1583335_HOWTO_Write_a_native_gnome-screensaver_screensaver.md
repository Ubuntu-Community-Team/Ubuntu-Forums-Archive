---
title: "HOWTO: Write a native gnome-screensaver screensaver"
date: 2010-09-27
forum: Outdated Tutorials &amp; Tips
---

### Post by ankillito on 2010-09-27
I hope this can serve as a quick start guide on how to create a native gnome screensaver.  That is to say, this is a tutorial on how to write a program that will be recognized as an option in Ubuntu's screensaver preference dialogue.  This tutorial assumes competency with C, and familiarity with OpenGL.

[IMG]http://i1209.photobucket.com/albums/cc385/scotlandguy/sample_screensaver.png?t=1285621858[/IMG]


In the attached tar file, you should find 8 files.
```

tar -xvf screensaver_demo.tar
cd screensaver_demo; ls
```For the screensaver itself:

[LIST]
[*]first.h
[*]first.c
[*]makefile
[/LIST]
For the window to render the screensaver in:

[LIST]
[*]config.h
[*]gs-theme-window.h
[*]gs-theme-window.c
[/LIST]
And for administrative stuff:

[LIST]
[*]install.sh
[*]your_screensaver.desktop
[/LIST]
To use this code, you will need OpenGL, glu, gtk, and gtkglext.  I'm not sure what is pre-installed, nor what apt-gets to use for these, but in your package manager, look for libgtkglext1-dev and libgtk2.0-dev.

Try the install script (it will exit after `make` if it doesn't compile).
```
./install.sh
```Assuming it compiles, it will copy the program into the folder that gnome-screensaver would like the executables to be in.  Next, it will edit the .desktop file to use this location, and then place the .desktop file where gnome-screensaver would like it to be.  Finally, it will copy the .desktop file to one more place because that is the only way I know to get gnome-screensaver to instantly show the new screensaver.

Ok, that's the general outline, and may be enough for some to get up and running, but here's more detail:

[B]1) Compiling the program:
*first.c first.h gs_theme_window.c gs_theme_window.h config.h makefile*
[/B]This program must use a window that gnome-screensaver can control.  Therefore, we must use GTK+, and we must use a gs_theme_window.  That is why you need the libgtk2.0 library, and that is why you need gs_theme_window.(h|c) and config.h.  Config.h is a file that you can put #defines in to change the way gs_theme_window compiles.  I didn't have a need for that, so I left it blank.

If you look first.(c|h), I think I commented fairly clearly.  You should be able to easily modify it and add to it.

To simply compile your program, use make.
```

make
./base
#or for fullscreen: ./base -root 
```To make your own awesome screensaver, you'll be wanting to add some OpenGL code in the exposeCb function.
[B]
2) Placement of the executable
*install.sh*
[/B]Ok, the executable could actually go anywhere.  However, using pkg-config, you can find out where gnome-screensaver would like it to go.  Why not play nice?

[B]3) .desktop file
*install.sh your_screensaver.desktop*
[/B]This file contains the name of the program as you would like it to appear in the screensaver preferences box, and the path to the program itself.  The install script attempts to take care of this all for you. The file is really self-explanatory, except for the difference between Exec and TryExec.  Exec is how to run the screensaver, and should include the command line option for fullscreen, hence the "-root".

The odd part is that simply putting it where pkg-config says gnome-screensaver wants it is not enough to make it show up.  For me, I had to also put it in ~/.local/share/applications/screensavers/  Please let me know if that doesn't work for you, or if you know how I should be handling that.

**4) Other resources:**
This thread is for using existing programs to make a screensaver.  If you don't want to code, start here:[ http://ubuntuforums.org/showthread.php?t=1534840]("http://ubuntuforums.org/showthread.php?t=1534840")

Ok, I think that's it.  Please let me know if this does or does not work for you, and I hope you all have fun making awesome screensavers!

--Ankillito

PS - if this was not n00b friendly enough, ask a question!

---

### Post by shinyblue on 2011-02-08
Great, thanks!

I didn't want to write a screensaver, but what I did want was to configure glslideshow so that it would zoom-and-pan ("Ken Burns effect") and fade between one photo and the next from my collection.

The default settings are annoying: black letterbox lines and three-ish separate pan-and-zooms per image is just disconcerting. One is nice.

Now xscreensaver has a nice(ish) GUI for configuring all the xscreensaver-gl screensavers, so you could set these options up. Not so gnome-screensaver, in fact gnome-screensaver seems to do everything in its power to stop you configuring it.

Your post helped me: I got it working by 

```
$ sudo mv usr/share/applications/screensavers/glslideshow.desktop \
          ~/local/share/applications/screensavers/glslideshow.desktop 

```
and editing the Exec line, adding in my options:

```
Exec=/usr/lib/xscreensaver/glslideshow -root -no-letterbox -fade 3 -duration 8 -pan 8
```

Thanks!

---

### Post by ankillito on 2011-02-08
woot!

---

### Post by bgmort on 2011-02-19
Thank you so much!  Today I felt like making myself a screensaver, and thanks to your post, it was relatively easy.  And now I feel like sharing the love.  Have you seen ThinkGeek's [Jumbo Binary Clock]("http://www.thinkgeek.com/homeoffice/lights/9df7/")?  Here's the gnome screensaver version.

---

### Post by ankillito on 2011-02-19
I know this was my fault, but if you cast the gs-theme-window to a gtk widget, you can remove the compiler warning. It's line 39 in your code, change to:
```
	window = GTK_WIDGET(gs_theme_window_new());
```

I also wanted to briefly mention the Ubuntu Unity decision. I had heard that Ubuntu was moving away from gnome, so I figured I wouldn't bother finishing my gnome-specific screensavers. Turns out I was misunderstanding. Unity is a shell for gnome, and the gnome programs will still be used even when Ubuntu switches to Unity with 11.04. So back to coding for me!
[http://www.jonobacon.org/2010/10/25/ubuntu-11-04-to-ship-unity/](http://www.jonobacon.org/2010/10/25/ubuntu-11-04-to-ship-unity/)

---

### Post by bgmort on 2011-02-21
Thanks, I'll throw that into my code.

After creating this screensaver, I was so pleased with how it turned out, I wanted to get it my android, so I spent the next couple hours turning it into an Android live wallpaper.  It turned out great, so I threw it on the Android market.  If anybody is interested, it's here: [Binary Clock Live Wallpaper]("https://market.android.com/details?id=com.piumosso.binaryclocklive").  And it's completely free.  There are over six hundred downloads already and mostly five star reviews. So if you'd like a simple, geeky live wallpaper, give it a try.  I'll add some features later on.

---

### Post by cragwolf on 2011-05-03
Thank you so much for your effort. Now I finally have a new project to work on, after I had run out of ideas. Coder's block is not fun.

---

### Post by ankillito on 2011-05-03
so basically because I'm an idiot, I accidentally double posted, and there are two of these threads running. ..k1.. thinks the other thread I started is easier to understand, it can be found here:

[http://ubuntuforums.org/showthread.php?p=10751738#post10751738]("http://ubuntuforums.org/showthread.php?p=10751738#post10751738")

...sorry for being a n00b...

---

