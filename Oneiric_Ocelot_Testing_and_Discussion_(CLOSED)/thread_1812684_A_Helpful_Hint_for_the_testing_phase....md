---
title: "A Helpful Hint for the testing phase..."
date: 2011-07-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sgage on 2011-07-26
If you install nautilus-open-terminal, you will be able to right-click on the desktop and launch a terminal. This will usually work even when the launcher has "gone away" (I keep a terminal in my launcher) and the dash won't come up and Alt-F2 isn't working. Extremely handy...

It has saved my a** several times, so I just thought I'd mention it to all of you out there in Testing Land :KS

---

### Post by lucazade on 2011-07-26
agree with you, really handy tool and one of the first thing I install. (Ctrl+Alt+T is as well a shortcut to open terminal)
OT.. nautilus-gksu instead is still broken.. i miss it :)

---

### Post by sgage on 2011-07-26
> **lucazade said:**
> agree with you, really handy tool and one of the first thing I install. (Ctrl+Alt+T is as well a shortcut to open terminal)
OT.. nautilus-gksu instead is still broken.. i miss it :)

Me too... :(

---

### Post by mc4man on 2011-07-28
> **lucazade said:**
> 
OT.. nautilus-gksu instead is still broken.. i miss it :)
That's been fixed, (at least here

---

### Post by lucazade on 2011-07-28
> **mc4man said:**
> That's been fixed, (at least here

still don't see it in contextual menu, who knows!

---

### Post by mc4man on 2011-07-28
> **lucazade said:**
> still don't see it in contextual menu, who knows!
The extension will not work unless redone.
At least here (& on numerous bug reports), running gksu(do) nautilus in any of the various ways would fail.
That works fine now, I use either Alt+F2 or preferred, - a nautilus-action
(not sure if the current N-A in O works, previously didn't, I've a package i built from git that works fine.

---

### Post by mc4man on 2011-07-28
> **mc4man said:**
> The extension will not work unless redone.


Now that the root browser works you could try this in the meantime though myself will probably just use N-A

Assuming nautilus-gksu is installed - 
```
sudo cp /usr/lib/nautilus/extensions-2.0/libnautilus-gksu.so /usr/lib/nautilus/extensions-3.0/

```
log out/in

Edit: - went ahead and modified the gksu source and rebuilt, installed the nautilus-gksu package on another O machine and works fine, so it appears there should be no reason not to see a new gksu package at some point, time will tell

---

### Post by lucazade on 2011-07-28
smart solution, now it is present in context menu but unfortunately I still don't have luck, it dies after gksu dialog in a waiting mouse cursor.

well, it seems here also launching nautilus as root from terminal doesn't work :)

```
$ sudo nautilus
Initializing nautilus-open-terminal extension
** (nautilus:1605): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
Initializing nautilus-gdu extension

(nautilus:1605): GLib-GObject-CRITICAL **: g_object_set_data: assertion `G_IS_OBJECT (object)' failed

(nautilus:1605): GLib-GIO-CRITICAL **: g_file_has_prefix: assertion `G_IS_FILE (file)' failed

(nautilus:1605): GLib-GIO-CRITICAL **: g_file_has_prefix: assertion `G_IS_FILE (file)' failed


$ gksu nautilus
Initializing nautilus-open-terminal extension
** (nautilus:1651): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
Initializing nautilus-gdu extension
```

---

### Post by mc4man on 2011-07-28
do you have the current nautilus - 3.1.4-0ubuntu1?

I've 2 installs - one 07/27 iso, the other not entirely trustworthy (fresh natty install > upgraded and then immediately upgraded to O about  2 weeks ago 

Both started allowing a root browser the other day and now
 - on both,  this from terminal,  opens fine, clean in terminal
(though the bug on this error is still open

> doug@doug-XPS-M1330:~$ gksudo nautilus
Initializing nautilus-open-terminal extension
Initializing nautilus-gdu extension

As far as the ext. - after the cp on old install and using a rebuilt package on the new one it also works fine
(went ahead and filed a bug on gksu for consideration of a rebuild, we'll see

I guess there seems to be no discounting differences between people's install at times - for instance I still don't have window decoration on some modal windows, I gather most do  
curious - do you see this
[http://ubuntuforums.org/showthread.php?p=11090197#post11090197](http://ubuntuforums.org/showthread.php?p=11090197#post11090197)

---

### Post by lucazade on 2011-07-28
@mc4man

yes, nautilus is version 3.1.4-0ubuntu1
in previous installations I was able to open nautilus as root, now I can't but I don't know when it really broke.

Agree, sometimes differences between people's install are not little, something I noticed during these years and that make it difficult to track issues.
Probably during alpha phases some bug-fixes apply only on clean installation and are not always so incremental.

Haven't noticed that bug about modal windows (probably because I use mostly unity-2d in virtualized oneiric, and these should be different from compiz one) and also about the automounting issue I haven't seen yet it here (when I install guest additions media is auto mounted and I'm asked to choose to launch installation automatically, so I believe it works properly).

---

### Post by mc4man on 2011-07-28
Some of the small graphical glitches i'm just ignoring for the moment - they may just be on certain hardware, maybe in beta+ it'll be worth pursuing
I have another one - just in unity, where trying to place the cursor in text it's always off a few pixels (gedit, this forum actually, -  in firefox
In other words, if I want to place the cursor between the t and w when writing or editing this post
 
between 

I have to place/click on the w, not between the t & w, if i do that the cursor goes between the e and t.  Weird

---

### Post by lucazade on 2011-07-28
> **mc4man said:**
> Some of the small graphical glitches i'm just ignoring for the moment - they may just be on certain hardware, maybe in beta+ it'll be worth pursuing
I have another one - just in unity, where trying to place the cursor in text it's always off a few pixels (gedit, this forum actually, -  in firefox
In other words, if I want to place the cursor between the t and w when writing or editing this post
 
between 

I have to place/click on the w, not between the t & w, if i do that the cursor goes between the e and t.  Weird

Really weird.
Never happend here, anyway something similar I've seen in gedit (both 2.x and 3.x) is when you try to highlight the last word of a row, the last character cannot be selected with mouse but only using shift+arrows.

---

### Post by mc4man on 2011-07-31
> **lucazade said:**
> smart solution, now it is present in context menu but unfortunately I still don't have luck, it dies after gksu dialog in a waiting mouse cursor.

well, it seems here also launching nautilus as root from terminal doesn't work :)

(nautilus:1605): GLib-GIO-CRITICAL **: g_file_has_prefix: assertion `G_IS_FILE (file)' failed


I'm going to dump my current install where it ( & open as administrator) works fine and see what the current iso brings



I have been trying over the last several days to run a root browser in the live session w/ each days current iso
On the live session get the same error and no root browser possible -
Though just did discover that if deja-dup is removed gksudo-nautilus ect. will work fine on the live session

So considering I've deja-dep installed here on this install some hope this is fixed on a real install (though the various bugs remain open

Edit: fresh install, no root nautilus, remove deja-dup it works fine from terminal, run, and nautilus-gksu if adjusted

---

### Post by VinDSL on 2011-07-31
> **mc4man said:**
> [R]emove deja-dup it works fine from terminal, run, and nautilus-gksu [...]
Nice one!

Removed "deja-dup" and "$ gksu nautilus" works fine for me, too.

LoL!  How in the world did you figure that out?!?!?  :D

Anyway, thanks for that!  ;)

---

### Post by mc4man on 2011-07-31
It was bugging me that while it, (gksudo nautilus), worked fine here it wasn't on recent livecd sessions nor for some others.
So just booted to live session, purged nautilus and libnautilus*, re-installed naut and minimum to log out/in to   gnome session.
Saw it worked then  so just a process of elimination...
To confirm I did a fresh real install

Had an orig. bug against this, filed new one, duped the old
[https://bugs.launchpad.net/ubuntu/+source/deja-dup/+bug/819109](https://bugs.launchpad.net/ubuntu/+source/deja-dup/+bug/819109)

If desired nautilus-gksu can be usable with workaround mentioned earlier in a post until gksu is rebuilt and whatever this deja-dup/nautilus mess is is fixed

---

### Post by lucazade on 2011-08-01
> **mc4man said:**
> I'm going to dump my current install where it ( & open as administrator) works fine and see what the current iso brings



I have been trying over the last several days to run a root browser in the live session w/ each days current iso
On the live session get the same error and no root browser possible -
Though just did discover that if deja-dup is removed gksudo-nautilus ect. will work fine on the live session

So considering I've deja-dep installed here on this install some hope this is fixed on a real install (though the various bugs remain open

Edit: fresh install, no root nautilus, remove deja-dup it works fine from terminal, run, and nautilus-gksu if adjusted

Bingo!

Dejadup removed, gksu nautilus working as expected.
Subscribed to bug report and added me-too.

thumbs up!

---

### Post by sgage on 2011-08-01
> **lucazade said:**
> Bingo!

Dejadup removed, gksu nautilus working as expected.
Subscribed to bug report and added me-too.

thumbs up!

Ditto!

---

### Post by mc4man on 2011-08-01
Fairly good day for the issue's I've seen, some mentioned in this thread
alacarte - fixed
deja-dup - root naut - will be fixed in next deja-dup upgrade
Missing window dec on some modal windows - fixed w/ compiz upgrade today (for the moment
No automount of removable media - will be fixed with next gnome-settings-daemon upgrade 
Banshee cd info retrieval - in next banshee upgrade
Fixed defaults.list to remove nautilus-folder-handler - new desktop-file-utils
No man for gsettings  - at least confirmed (easily user replaced

While more a convenience than 'useful' I find removing the need for password on sudo something I wish on dev  (actually always
can be revisited if desired

---

