---
title: "FRUSTRATED AS HELL with Kalarm."
date: 2008-11-22
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-11-22
Hi, all:

I'm still having this problem resizing windows.  I've posted this a couple of times before, but no one seems to know what the problem is.  

When I start KAlarm and try to create a new alarm, the new alarm window is oversized, and jumps around when I try to click on it to change any of the settings.  Minimize, maximize, resize, move--nothing from the context window seems to work.  I'm getting frustrated, since there doesn't seem to be any other Linux cognate for a program I used to use in Windows called TimeLeft--it was one of the two or three programs I LOVED in Windows.  Don't get me wrong, I'm a total convert, but I'm getting pissy at having to use Ktimer and calculate the number of SECONDS to my next desired alarm event.  

I'm using a 32" plasma tv as my monitor.  I can't figure out how to configure the default size for KAlarm new alarm settings windows.  Does ANYBODY know how to fix this problem?

KDE 4.1.3, Intrepid.

Thanks!

---

### Post by whitethorn on 2008-11-22
If you are using using compiz, then you can use a plugin called Windows Rules, to set a rule for a specific size for whatever window you want (I haven't used it yet so can't help you further). You could also try using devilspie, doing a quick google search to see if it works on kubuntu brought up this thread which might help you.

[http://ubuntuforums.org/showthread.php?t=502271](http://ubuntuforums.org/showthread.php?t=502271)

---

### Post by tarahmarie on 2008-11-22
I've tried using Windows Rules before, but I'm not sure how to configure it properly.  I added class=KAlarm in the Size Rules tab, and set the default size to 1097x1097.  It didn't change anything.  I'll try devilspie, and see what happens.

---

### Post by tarahmarie on 2008-11-24
I tried devilspie, and the main KAlarm window sizes according to the rules I included.  The Add New Alarm - KAlarm window is STILL too big for the screen and still jumps around.  Here's the contents of my devilspie rule for KAlarm.

(if
(contains (window_name) "KAlarm")
(begin
(pin)
(geometry "600x600")
)
)

Why would this not work on the new alarm window?

---

### Post by whitethorn on 2008-11-25
run devilspie in konsole, and then start kalarm, and then click on the Add New Alarm. It can be that the window is called differently and you'll have to create a rule only for the New Alarm Window.  

By keeping Devilspie running in the konsole you can see the different programs which are opened by class, window name ... That way you can define it better. I have one set up for pidgin 

> (if (is (application_name) "Pidgin")  
        (begin
                (if (is (window_role) "buddy_list")
                        (begin
                                (undecorate)
                                (skip_tasklist)
                                (geometry "199x567+1165+0")
                        )
                )
                (if (is (window_role) "conversation")
                        (begin
                                (undecorate)
                                (geometry "522x400+0+800")
                        )
                )
        )
)


Hope this helps.

---

### Post by tarahmarie on 2008-11-28
I tried killing devilspie and restarting KAlarm.  Here's the output:

~/Documents/Software : Yes, Supreme Empress? $ pgrep devilspie
6037
~/Documents/Software : Yes, Supreme Empress? $ kill 6037
~/Documents/Software : Yes, Supreme Empress? $ devilspie
^C
~/Documents/Software : Yes, Supreme Empress? $ kalarm
<unknown program name>(30744)/ main: initialising
kalarm(30744) EventListModel::EventListModel: Event 0x833e228
kalarm(30744) EventListModel::EventListModel: Event 0x831be88
kalarm(30744) EventListModel::EventListModel: Event 0x82ee2e0
~/Documents/Software : Yes, Supreme Empress? $ 


I'm not exactly sure what it means or how to use it to fix devilspie.

---

### Post by whitethorn on 2008-11-29
What I meant is the following. To figure out how the program/class/window name is you have to let devilspie run in an active terminal/konsole.  So start konsole and type 

```
sudo killall devilspie
devilspie
```

I just let it run and it shows 

> Window Title: 'tilda'; Application Name: 'tilda'; Class: 'Tilda'; Geometry: 1428x472+126+572
Window Title: '[kubuntu] FRUSTRATED AS HELL with Kalarm. - Ubuntu Forums - Opera'; Application Name: '[kubuntu] FRUSTRATED AS HELL with Kalarm. - Ubuntu Forums - Opera'; Class: 'Opera'; Geometry: 888x1026+792+24
Window Title: 'x-nautilus-desktop'; Application Name: 'File Manager'; Class: 'Nautilus'; Geometry: 1680x1050+0+0
Window Title: 'Top Expanded Edge Panel'; Application Name: 'Top Expanded Edge Panel'; Class: 'Gnome-panel'; Geometry: 1680x24+0+0
Window Title: 'Bottom Expanded Edge Panel'; Application Name: 'Bottom Expanded Edge Panel'; Class: 'Gnome-panel'; Geometry: 1680x24+0+1044
Window Title: 'Untitled window'; Application Name: 'switcher-window'; Class: 'switcher-window'; Geometry: 668x264+506+413
Window Title: 'Videos - File Browser'; Application Name: 'File Manager'; Class: 'Nautilus'; Geometry: 793x581+604+332
Window Title: 'tilda'; Application Name: 'tilda'; Class: 'Tilda'; Geometry: 1428x472+126+572

It shows how the application is called/classified.  All you need now is to apply your rule to the specific New Alarm window (in other words the window role). Look at my last post to see.  The first specification

> (if (is (application_name) "Pidgin")

Just tells what to do with the main window (don't need to change that one)

Next specification 

> (if (is (window_role) "buddy_list")

Tells what to do with a specific window which is identified as windows role (each conversation window should be identifed and do the following -check my previous post for the whole command-.  

This is what you need to be able to set a specific rule to get devilspie to work for you New Alarm window.  You only have to run devilspie in a konsole to get the *specific* name (that being what the window_role application name, whichever specifies the program/window for being what it is.  In other words the identifying factor which seperates it from the original program.) for the code.

---

### Post by tarahmarie on 2008-11-29
I killalled devilspie, restarted it, and let it run.  Then, I started KAlarm and a new display alarm.  I got no output in the terminal like that which you got.  Is there some kind of verbose mode for devilspie that I don't have turned on?

---

