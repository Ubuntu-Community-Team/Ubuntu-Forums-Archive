---
title: "Firefox crashing"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-05-29
OK Firefox has started randomly crashing for no reason, but generally when it's loading a page. it will just close completely! no going Grey or any warning at all:confused:

---

### Post by P3ngu1n0 on 2008-05-29
sudo apt-get install firefox and see if it reinstalls over it

hope this helps

---

### Post by kamitsukai on 2008-05-29
> **P3ngu1n0 said:**
> sudo apt-get install firefox and see if it reinstalls over it

hope this helps

that wouldn't work as it's already installed

but thanks anyway:KS

---

### Post by wolfen69 on 2008-05-29
i heard that removing libflashsupport can help. cant hurt to try.

---

### Post by spiderbatdad on 2008-05-29
Firefox bug filing:[http://forums.mozillazine.org/viewforum.php?f=9](http://forums.mozillazine.org/viewforum.php?f=9)

---

### Post by shifty_powers on 2008-05-29
is this after the update?

just had a big *** 49meg update, including ff3rc1 ;)

---

### Post by peakshysteria on 2008-05-29
Seems more like an addon problem. Try to temporary disable the addons which is known to be problematic.

It might also be useful to see which version of FF you are using as well as what plugins and addons you have installed. (the fantastic flashblock among others are for example be known to be problematic). And are you running 32-bit or 64-bit? Feisty? Gutsy? Hardy? etc.....

________

Running smooth as hell after i checked Hardy-proposed in software sources. Got 128 updates all in all. Now running:

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9) Gecko/2008052909 Firefox/3.0

Greasemonkey disabled (not compatible)
Last.Fm code disabled (not compatible)

Seems faster. Uses less memory.

---

### Post by KaliVoid on 2008-05-29
*if you are using firefox 3 beta 5*

try upgrade to firefox 3 RC1 
or downgrade to firefox-2 

im using firefox 3 RC1 and didnt have any crashes (so far..., i installed it one week ago)

---

### Post by Crafty Kisses on 2008-05-29
> **kamitsukai said:**
> OK Firefox has started randomly crashing for no reason, but generally when it's loading a page. it will just close completely! no going Grey or any warning at all:confused:

Post the following output:
```
top
```

---

### Post by kamitsukai on 2008-05-29
[SIZE="4"][FONT="Comic Sans MS"]OK there's lots of people offering help here so i will try and list what Add-ons i have and what Firefox I'm using and such...

Firefox 3 Beta 5 (no reason updates)

_Add-ons:_
Adblock plus
Beta of delicious bookmarks (installed after problems started occurring)
DownloadHelper
DownThemAll
NoScript
Persona's for Firefox
User Agent Switcher

Couldn't cop and paste the out put for "top" as it was dynamic and kept changing so here's a screenshot below:KS[/FONT][/SIZE]

---

### Post by ice60 on 2008-05-29
you can try running firefox from the terminal, that way when it crashes it might tell you why it crashed.

also, if you want to try running firefox without your themes and extensions you can run it like this -
```
firefox -safe-mode
```

you can save the results of top to your desktop like this -
```
cd Desktop && top n 1 > top.txt
```

**[color=red]EDIT[/color]**
that last command doesn't look very good in a text reader, i looked up a better option and you can run one of these instead -

```
cd Desktop && top -cSb n 1 > top.txt
```
```
cd Desktop && top -b n 1 > top.txt
```

**[color=red]EDIT 2 lol[/color]**
there's also Swiftfox, lots of people say it's great :) 

there's opera too, i love opera, although i'm unsure if flash works with the released version atm, i'm using one of the betas and updating it every week or so as it's released. you can get it here if you want?
[http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)

---

### Post by marcelo danico on 2008-05-29
I've upgraded to RC1 and downgraded to FF2.0 but the crashing problem persists. And I'm not using any add-ons.  I saw on mozilla that out of 3million? downloaders, about 10,000 have this sudden crash problem.

---

### Post by kamitsukai on 2008-05-29
> **marcelo danico said:**
> I've upgraded to RC1 and downgraded to FF2.0 but the crashing problem persists. And I'm not using any add-ons.  I saw on mozilla that out of 3million? downloaders, about 10,000 have this sudden crash problem.

[FONT="Comic Sans MS"][SIZE="3"]WOW nice to know I'm special i seem to have this "special" thing going on with XP as well i had a corruption in the registry which caused (according to Microsoft) a very rare problem lol check out the video...[http://youtube.com/watch?v=0x5K96cg87A](http://youtube.com/watch?v=0x5K96cg87A) (and yes the screen is scrolling:mad:)

Thanks for the help so far i will post back with the out-put of me running Firefox from the terminal[/SIZE][/FONT]

---

### Post by peakshysteria on 2008-05-29
> **kamitsukai said:**
> [SIZE="4"][FONT="Comic Sans MS"]OK there's lots of people offering help here so i will try and list what Add-ons i have and what Firefox I'm using and such...

Firefox 3 Beta 5 (no reason updates)

_Add-ons:_
Adblock plus
Beta of delicious bookmarks (installed after problems started occurring)
DownloadHelper
DownThemAll
NoScript
Persona's for Firefox
User Agent Switcher
]

Running it in safe mode is a good advice. Anyway you don't have a lot of addons. So first try to disable all addons (tools --> addons --> extensions and disable all one by one). Then try to run Firefox and see if it crashes. If not it's one of the addons which is the perpetrator. Then try to enable them one by one again.

Adblock have a history of being somewhat unstable as far as I remember. But I haven't used for a very long time. It looks good now.

My best guess are one of these or a combination of these:

DownloadHelper
DownThemAll
NoScript

Persona's for Firefox i don't know. Do you have a link for it so i can check it out?

If it still crashes when all addons are disabled it's something else. It's doubtful that it's a plugin.

And what is Persona's for Firefox?? Do you have a link for it so i can check it out?

Have you tried to check hardy-proposed in software sources? That's how I got 3.0. I checked it and ran the update manager. It told me I had to choose a partial update. Choosing this didn't work. Tried one more time. When prompted with partial update I hit close. Then hitting install in the update manager. All updates (128 in my case) installed smooth and nicely. Est voila I had Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9) Gecko/2008052909 Firefox/3.0 which is running very smooth and flawlessly.

Also mentioned here:

[http://ubuntuforums.org/showthread.php?t=811670](http://ubuntuforums.org/showthread.php?t=811670)

Just close every running program and give it a go. No problems at all in my end. Give it some thought and tell us how it goes...

---

### Post by kamitsukai on 2008-05-29
Yer here is a link for persona's it's great little skinning add-on [http://labs.mozilla.com/2007/12/personas-for-firefox/](http://labs.mozilla.com/2007/12/personas-for-firefox/)

---

### Post by kamitsukai on 2008-05-29
Ok it crashed while i was running it from the terminal and this is the output (with add-ons running)

```
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

(firefox:6372): Gdk-CRITICAL **: gdk_colormap_query_color: assertion `GDK_IS_COLORMAP (colormap)' failed

(firefox:6372): Gtk-CRITICAL **: _gtk_container_queue_resize: assertion `GTK_IS_CONTAINER (container)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_colormap_query_color: assertion `GDK_IS_COLORMAP (colormap)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_colormap_query_color: assertion `GDK_IS_COLORMAP (colormap)' failed

(firefox:6372): Gtk-CRITICAL **: _gtk_container_queue_resize: assertion `GTK_IS_CONTAINER (container)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_colormap_query_color: assertion `GDK_IS_COLORMAP (colormap)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_colormap_query_color: assertion `GDK_IS_COLORMAP (colormap)' failed

(firefox:6372): Gtk-CRITICAL **: _gtk_container_queue_resize: assertion `GTK_IS_CONTAINER (container)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed

(firefox:6372): Gdk-CRITICAL **: gdk_colormap_query_color: assertion `GDK_IS_COLORMAP (colormap)' failed

(firefox:6372): GLib-GObject-CRITICAL **: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed
Segmentation fault

```

---

### Post by kamitsukai on 2008-05-29
Doesent look good does it :D

---

### Post by kamitsukai on 2008-05-29
And i have just started Firefox in safe mode and the output from the terminal is starting to go the same way as above. so far it doesn't look like the add-ons are the problem but Firefox itself (think i might start using opera more :( )

***Edit***
ignore above looks like it's working fine without add-ons :P

---

### Post by peakshysteria on 2008-05-29
Then try to enable them one by one and see if you can find the one wanting you to change to Opera.

And try to update to 3.0 when you have solved it. Smooth it is man....smooth I tell you :)

Hmm, Personas is running fine on my 3.0. Didn't like it though it's got potential :)

It might be DownloadHelper and/or DownThemAll which is conflicting with the built in download manager.

Are you running 32-bit or 64-bit 8.04 Hardy?

My Firefox Information:

Last updated: Thu, 29 May 2008 22:14:35 GMT
User Agent: Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9) Gecko/2008052909 Firefox/3.0

**Extensions** (enabled: 10, disabled: 3; total: 13)
[list]
[*][Flashblock](http://flashblock.mozdev.org/) 1.5.6 [disabled]
[*][Forecastfox](http://forecastfox.mozdev.org/) 0.9.6 
[*][Greasemonkey](http://www.greasespot.net/) 0.7.20080121.0 [disabled]
[*][InfoLister](http://mozilla.doslash.org/infolister) 0.10 
[*][last.fmCode](http://mll02.free.fr/?p=42) 0.7 [disabled]
[*][Linkification](http://yellow5.us/firefox/linkification/) 1.3.3 
[*][Norsk Bokmål ordliste]() 2.0.10.0 
[*][Norsk Nynorsk ordliste]() 2.0.10.0 
[*][Tab Mix Plus](http://tmp.garyr.net) 0.3.6.1.080416 
[*][Text Link](http://piro.sakura.ne.jp/xul/_textlink.html.en) 2.0.2008052801 
[*][Ubuntu Firefox Modifications]() 0.5 
[*][Update Channel Selector](http://www.oxymoronical.com/web/firefox/updatechannel) 1.0.3 
[*][User Agent Switcher](http://chrispederick.com/work/user-agent-switcher/) 0.6.11 
[/list]

**Themes** (1)
[list]
[*]Default [selected]
[/list]

**Plugins**
[list]
[*]Default Plugin
[*]Demo Print Plugin for unix/linux
[*]DivX® Web Player
[*]GCJ Web Browser Plugin (using IcedTea) 1.0
[*]Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)
[*]iTunes Application Detector
[*]QuickTime Plug-in 7.2.0
[*]Shockwave Flash
[*]Totem Web Browser Plugin 2.22.1
[*]VLC Multimedia Plugin (compatible Totem 2.22.1)
[*]Windows Media Player Plug-in 10 (compatible; Totem)
[/list]

---

### Post by kamitsukai on 2008-05-29
Im running 32bit, also although safe mode never actually crashed im still getting the same errors in the terminal output...

```
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

(firefox:11097): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:11097): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:11097): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:11097): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:11097): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:11097): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:11097): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:11097): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:11097): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:11097): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:11097): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:11097): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:11097): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:11097): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:11097): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:11097): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:11097): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:11097): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:11097): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:11097): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:11097): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:11097): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```

---

### Post by kamitsukai on 2008-05-29
when did DivX® Web Player get ported to linux?

---

### Post by peakshysteria on 2008-05-29
Close down every instance of Firefox and go for the above mentioned update:
> 
Have you tried to check hardy-proposed in software sources? That's how I got 3.0. I checked it and ran the update manager. It told me I had to choose a partial update. Choosing this didn't work. Tried one more time. When prompted with partial update I hit close. Then hitting install in the update manager. All updates (128 in my case) installed smooth and nicely. Est voila I had Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9) Gecko/2008052909 Firefox/3.0 which is running very smooth and flawlessly.

Also mentioned here:

[http://ubuntuforums.org/showthread.php?t=811670](http://ubuntuforums.org/showthread.php?t=811670)

Just close every running program and give it a go. No problems at all in my end. Give it some thought and tell us how it goes...


Ofcourse if the problem is at all related to one or more (a combination/missmatch) of your addons the problem will follow. You said it was running fine when disabling all addons. What about enabling them one by one pinpointing the one ruining the evening? Nogo?

---

### Post by kamitsukai on 2008-05-29
well it worked but there were still errors in the terminal i just wondered what they were?

---

### Post by peakshysteria on 2008-05-29
Google the last lines of the error output. All seems good your end then. Not sure which one of your addons made trouble yet though.

Going to sleep now......must...sle ep..now zZzZZzzz zz

---

### Post by kamitsukai on 2008-05-29
I've installed the updates and so far so good firefox RC1 is doing pretty well :)

---

### Post by marcelo danico on 2008-05-29
I fixed my crash issue thanks to defcon (ubuntu-unleashed), maybe this will help you too ---> [http://www.ubuntu-unleashed.com/2008/05/howto-fix-firefox-and-epiphany-web.html](http://www.ubuntu-unleashed.com/2008/05/howto-fix-firefox-and-epiphany-web.html)
:)

---

