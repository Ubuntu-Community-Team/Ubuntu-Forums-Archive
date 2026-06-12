---
title: "How can I take a screenshot like this?"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by vasa1 on 2011-10-21
I can take a screenshot of the entire desktop or of a window but how can I take a screenshot of dropdown menus like the one shown here:
[http://cloud.addictivetips.com/wp-content/uploads/2011/09/Power-Menu.png](http://cloud.addictivetips.com/wp-content/uploads/2011/09/Power-Menu.png) ???

If I click on a dropdown menu of any item at the top of the screen and then press Prnt Scrn, nothing happens. (Normally, I get a pop-up that allows me to save the screenshot.)

---

### Post by tors on 2011-10-21
Try to run this in a terminal:

gnome-screenshot --interactive



Edit post...

And use the delay function :)

---

### Post by M!K3_$ on 2011-10-21
KSnapshot will do it.

[http://www.kde.org/applications/graphics/ksnapshot]("http://www.kde.org/applications/graphics/ksnapshot")

---

### Post by tors on 2011-10-21
Another cool thing you could do is to install "recordmydesktop" or a similar program, which lets you record everything you see.

---

### Post by vasa1 on 2011-10-21
Thanks, guys!

I think I'll try gnome-screenshot since it's already installed. I'm reluctant to install any KDE stuff because I don't have any other KDE programs and fear having to pull in a whole bunch of dependencies just to get one thing going.

---

### Post by smarter phone on 2011-10-21
"recordmydesktop"? How is it?

---

### Post by tors on 2011-10-21
> **smarter phone said:**
> "recordmydesktop"? How is it?

I haven't tried any other recording tools so I don't know how it compares, it works for me :)

A snippet from the man page:

```
NAME
       recordMyDesktop - record desktop sessions to an Ogg-Theora-Vorbis file.

SYNOPSIS
       recordmydesktop [ Options ]^ filename

DESCRIPTION
               recordMyDesktop produces a file(default out.ogv) that contains a video and audio recording
       of a linux desktop session. The default behavior of recording is to mark areas that have changed(through libxdamage)
       and update the frame. This behavior can be changed (option --full-shots ) to produce a more accurate result
       or capture windows that do not generate events on change(windows with accelerated 3d context)
       but this will notably increase the workload.
       recordMyDesktop doesn't have a commandline interface.
       After startup, it can be controled only through the following signals:
       SIGUSR1 causes the program to pause if it's currently recording, and vice-versa.
       SIGTERM causes normal termination of the recording.
       SIGINT also causes normal termination.
       SIGABRT terminates the program and removes the specified output file.
       This signals can also be delivered on the application, with the use of shortcuts.
       See --pause-shortcut and --stop-shortcut , on the Misc.  section of Options bellow.

       A typical scenario of recording can be a command as simple as:
       ~$ recordmydesktop
       which will produce a fullscreen recording named out.ogv
       while a command like:
       ~$ recordmydesktop foo.ogv
       will write output to foo.ogv
       Since version 0.3, encoding will happen right after the recording finishes.
       While this behavior saves a lot of CPU, you can revert to the old one by entering the --on-the-fly-encoding switch.
       To specify a region for recording you can type this:
       ~$ recordmydesktop -x X_pos -y Y_pos --width WIDTH --height HEIGHT -o foo.ogv
       where X_pos and Y_pos specify the offset in pixels from the upper left
       corner of your screen and WIDTH and HEIGHT the size of the window to be recorded(again in pixels).
       If the area extends beyond your current resolution, you will be notified appropriately and nothing will happen.
       Notice also, that if any option is entered you have to specify the output file with the -o switch.
       If you try to save under a filename that already exists, the name will be post-fixed with a number (incremented if that name exists already)
       To normally end a recording you can press ctl-c.
       (which will send a SIGINT to the program).
       For further manipulation of the end result look at the OPTIONS and NOTES sections.

       ...

```

---

### Post by M!K3_$ on 2011-10-21
I have used it before to make a little youtube video. Worked well enough for me, and was  fairly easy.

---

### Post by vasa1 on 2011-10-21
I'm marking this "solved".

Though I got this:
```
** (gnome-screenshot:2971): DEBUG: The GetProfileForWindow request failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.ColorManager was not provided by any .service files
```
the operation was successful.

---

