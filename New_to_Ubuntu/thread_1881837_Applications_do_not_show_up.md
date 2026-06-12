---
title: "Applications do not show up"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by jrr_wired on 2011-11-16
I ran a system upgrade, and now my applications do not show up in unity.  Before posting, I ran
sudo apt-get update
sudo apt-get dist-upgrade

and still, no applications in my menu.  Any suggestions?

---

### Post by Mark Phelps on 2011-11-16
What version of Ubuntu are you running now?

What version were you running before the upgrade?

What menu are you talking about -- 11.10 really doesn't have menus.

---

### Post by jrr_wired on 2011-11-17
I am running 11.10, and where I say "menu" I'm meaning when I click off on the Ubuntu symbol on Dash Home, and the program/shortcuts listing comes up - there used to be four symbols.  A home symbol, a programs symbol, a documents symbol and a music symbol below the four default programs/shortcuts icons.  The documents symbol and programs symbol are now gone, and when I click on the More Apps icon at the top, nothing happens.  

However, when I run programs in the command terminal, the programs are still there - It's like Unity's program index files were corrupted somewhere along the way. I'd rather learn how to fix the problem than go with the usual fresh reinstall.

---

### Post by raja.genupula on 2011-11-17
try from your terminal
```
unity --reset
unity --reset-icon
```

---

### Post by Frogs Hair on 2011-11-17
If you upgraded from 11.04 to 11.10 you may have lost some applications due to Gnome 3 compatibility . The program and Files lenses are now part of dash , but there should be a home folder icon .

---

### Post by Kellemora on 2011-11-17
I'm running version 10.04.? just keeping up with the normal updates that come in every few days.

TODAYS UPDATE has caused the system programs Applications, Places, System, etc. to no longer appear in the upper panel.

This was not a kernel update so the grub file wasn't changed.

I've rebooted a few times because sometimes that fixes it.

Whatever was all included in this mornings update, it messed things up!

TTUL
Gary

---

### Post by corncob on 2011-11-17
> **Kellemora said:**
> I'm running version 10.04.? just keeping up with the normal updates that come in every few days.

TODAYS UPDATE has caused the system programs Applications, Places, System, etc. to no longer appear in the upper panel.

This was not a kernel update so the grub file wasn't changed.

I've rebooted a few times because sometimes that fixes it.

Whatever was all included in this mornings update, it messed things up!

TTUL
Gary

Just to give you some input, I did the upgrades on my 10.04 today with no problem.  It could be an application you're running.

---

### Post by Kellemora on 2011-11-17
I have not installed or used any applications that I don't use every single day of the week.  I rebooted yesterday to help clear some of the cache memory that seems to build up slowly over time and it was working just fine last night and this morning.

Then when the Update Manager appeared, like always I gave it permission to do its thing.

I rebooted afterwards, not that it was necessary, I'm just in the habit of doing that after a larger update.

I also updated my 8.04 machines later with no problems.

What I've done for now is loaded to the panel the Main Menu so at least I can get to the things I need to get to that way.

Maybe by the next update it will come back again?

I'm seriously trying very hard to get used to this lousy version 10.04 and now us it daily, but it don't hold a candle to how WONDERFUL and PERFECT version 8.04 was and still remains to be.  Many of the Standard FEATURES I LOVED about 8.04 are not present at all in 10.04 and 10.04 will only run on two of our 8 machines anyhow.
Maybe by 14.04 they will wise up and go back to 8.04 and simply enhance it?  Why the need to totally change things every 3 years makes no sense to me.  When you have something that works, you expound on it, not dump it and start over again!

TTUL
Gary

---

### Post by corncob on 2011-11-18
> **Kellemora said:**
> I have not installed or used any applications that I don't use every single day of the week.  I rebooted yesterday to help clear some of the cache memory that seems to build up slowly over time and it was working just fine last night and this morning.

Then when the Update Manager appeared, like always I gave it permission to do its thing.

I rebooted afterwards, not that it was necessary, I'm just in the habit of doing that after a larger update.

I also updated my 8.04 machines later with no problems.

What I've done for now is loaded to the panel the Main Menu so at least I can get to the things I need to get to that way.

Maybe by the next update it will come back again?

I'm seriously trying very hard to get used to this lousy version 10.04 and now us it daily, but it don't hold a candle to how WONDERFUL and PERFECT version 8.04 was and still remains to be.  Many of the Standard FEATURES I LOVED about 8.04 are not present at all in 10.04 and 10.04 will only run on two of our 8 machines anyhow.
Maybe by 14.04 they will wise up and go back to 8.04 and simply enhance it?  Why the need to totally change things every 3 years makes no sense to me.  When you have something that works, you expound on it, not dump it and start over again!

TTUL
Gary

I meant to say that maybe an upgrade to one of your applications did it.  Anyway, to add it back right click on the panel, select 'Add to Panel' from the dropdown menu, select 'Menu Bar' and add.
I agree with your last sentence.  Its the way the world's going though.

---

### Post by jrr_wired on 2011-11-18
I tried your suggestion, and it seemed to work at first - but the process kept getting hung up on something.  Sorry for the beefy cut and paste, but this is the content I got from running **sudo unity --reset**

WARNING: no current gconf profile set, assuming unity
WARNING: Unity currently default profile, so switching to metacity while resetting the values
Window manager warning: from event callback
Window manager warning: from event callback
Window manager warning: from event callback
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing resize options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing scale options...done
Initializing session options...done
WARN  2011-11-18 05:22:50 glib.glib-gobject <unknown>:0 invalid (NULL) pointer instance

Screen geometry changed:
   0x0x1280x720

unity-panel-service: no process found
Initializing unityshell options...done
DEBUG 2011-11-18 05:22:50 glib <unknown>:0 Setting to primary screen rect: x=0 y=0 w=1280 h=720
Initializing addhelper options...done
Initializing animationaddon options...done
Initializing annotate options...done
Initializing bench options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...done
Initializing commands options...done
Initializing crashhandler options...done
Initializing cube options...done
Initializing cubeaddon options...done
Initializing debugspew options...done
Initializing extrawm options...done
Initializing fadedesktop options...done
Initializing firepaint options...done
Initializing group options...done
Initializing imgjpeg options...done
Initializing kdecompat options...done
Initializing loginout options...done
Initializing mag options...done
Initializing maximumize options...done
Initializing mblur options...done
Initializing neg options...done
Initializing notification options...done
Initializing obs options...done
Initializing opacify options...done
Initializing put options...done
Initializing reflex options...done
Initializing resizeinfo options...done
Initializing ring options...done
Initializing rotate options...done
Initializing scaleaddon options...done
Initializing scalefilter options...done
Initializing screenshot options...done
Initializing shelf options...done
Initializing shift options...done
Initializing showdesktop options...done
Initializing showmouse options...done
Initializing splash options...done
Initializing staticswitcher options...done
Initializing switcher options...done
Initializing td options...done
Initializing thumbnail options...done
Initializing trailfocus options...done
Initializing wallpaper options...done
Initializing water options...done
Initializing widget options...done
Initializing winrules options...done
Initializing wobbly options...done
Initializing zoom options...done
WARN  2011-11-18 05:22:53 unity.favorites FavoriteStoreGSettings.cpp:138 Unable to load GDesktopAppInfo for 'ubiquity-gtkui.desktop'
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
Setting Update "autoraise"
Setting Update "autoraise_delay"
Setting Update "maximize_window_key"
Setting Update "minimize_window_key"
Setting Update "show_desktop_key"
Setting Update "toggle_window_maximized_key"
Setting Update "toggle_window_shaded_key"
Setting Update "fullscreen_visual_bell"
Setting Update "main_menu_key"
Setting Update "run_command_terminal_key"
Setting Update "run_key"
WARN  2011-11-18 05:23:51 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/music does not exist
WARN  2011-11-18 05:23:51 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/music does not exist
WARN  2011-11-18 05:40:09 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-11-18 05:40:09 glib.glib-gobject <unknown>:0 instance with invalid (NULL) class pointer
WARN  2011-11-18 05:46:21 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-11-18 05:46:21 glib.glib-gobject <unknown>:0 instance of invalid non-instantiatable type `(null)'
WARN  2011-11-18 05:46:22 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


Initializing nautilus-gdu extension
Initializing nautilus-dropbox 0.6.8
** (nautilus:3177): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
compiz (core) - Warn: unhandled ConfigureNotify on 0x1200278!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> l2070
--> inode/directory
--> root

(nautilus:3177): Eel-WARNING **: "unique eel_ref_str" hash table still has 3 elements at quit time (keys above)

--- Hash table keys for warning below:
--> file:///

(nautilus:3177): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time (keys above)
Shutting down nautilus-gdu extension
WARN  2011-11-18 05:48:21 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-11-18 05:55:13 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-11-18 05:55:13 glib.glib-gobject <unknown>:0 instance of invalid non-instantiatable type `(null)'
WARN  2011-11-18 05:55:24 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-11-18 05:55:24 glib.glib-gobject <unknown>:0 instance of invalid non-instantiatable type `(null)'

(gnome-control-center:3705): info-cc-panel-WARNING **: Failed to get fallback mode: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
WARN  2011-11-18 05:55:53 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-11-18 05:55:53 glib.glib-gobject <unknown>:0 instance of invalid non-instantiatable type `(null)'
WARN  2011-11-18 05:59:16 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-11-18 05:59:16 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-11-18 05:59:16 glib.glib-gobject <unknown>:0 instance of invalid non-instantiatable type `(null)'
WARN  2011-11-18 05:59:16 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-11-18 05:59:27 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-11-18 05:59:28 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


^Cjrr@i7:~$ g_dbus_connection_real_closed: Remote peer vanished with error: Error receiving message: Connection reset by peer (g-io-error-quark, 0). Exiting.
WARN  2011-11-18 06:02:01 glib.glib-gio <unknown>:0 Error releasing name com.canonical.Unity.Lens.music.T1321619031.Filters: Timeout was reached
*** glibc detected *** compiz: corrupted double-linked list: 0x00000000028b47a0 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x78a96)[0x7f02defc7a96]
/lib/x86_64-linux-gnu/libc.so.6(+0x798b3)[0x7f02defc88b3]
/lib/x86_64-linux-gnu/libc.so.6(cfree+0x6c)[0x7f02defcbd7c]
/usr/lib/dri/fglrx_dri.so(+0x18b31d9)[0x7f02d65211d9]
/usr/lib/dri/fglrx_dri.so(+0x19414bc)[0x7f02d65af4bc]
/usr/lib/dri/fglrx_dri.so(+0xfe68af)[0x7f02d5c548af]
/usr/lib/dri/fglrx_dri.so(+0xf6b72d)[0x7f02d5bd972d]
/usr/lib/dri/fglrx_dri.so(+0xf73a26)[0x7f02d5be1a26]
/usr/lib/dri/fglrx_dri.so(+0xddc2eb)[0x7f02d5a4a2eb]
/usr/lib/dri/fglrx_dri.so(+0x2ffa92)[0x7f02d4f6da92]
/usr/lib/dri/fglrx_dri.so(+0x36a234)[0x7f02d4fd8234]
/usr/lib/dri/fglrx_dri.so(+0xdf3317)[0x7f02d5a61317]
/usr/lib/dri/fglrx_dri.so(+0x18e9998)[0x7f02d6557998]
/usr/lib/dri/fglrx_dri.so(+0x18e30e5)[0x7f02d65510e5]
/usr/lib/fglrx/libGL.so.1(+0x3819e)[0x7f02d6cc319e]
/usr/lib/fglrx/libGL.so.1(glXDestroyContext+0x8b)[0x7f02d6cc348b]
/usr/lib/compiz/libopengl.so(_ZN8GLScreenD1Ev+0x61)[0x7f02d6ebab81]
/usr/lib/compiz/libopengl.so(_ZN8GLScreenD0Ev+0x9)[0x7f02d6ebacc9]
compiz(_ZN11CompManager10finiPluginEP10CompPlugin+0x2a)[0x459dba]
compiz(_ZN10CompPlugin3popEv+0x5f)[0x45b69f]
compiz(_ZN10CompScreenD1Ev+0x5d)[0x42a20d]
compiz(_ZN10CompScreenD0Ev+0x9)[0x42a469]
compiz(_ZN11CompManager4finiEv+0x20)[0x4256e0]
compiz(main+0x102)[0x422222]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed)[0x7f02def7030d]
compiz[0x422871]
======= Memory map: ========
00400000-0047b000 r-xp 00000000 08:16 2492917                            /usr/bin/compiz
0067b000-0067c000 r--p 0007b000 08:16 2492917                            /usr/bin/compiz
0067c000-0067d000 rw-p 0007c000 08:16 2492917                            /usr/bin/compiz
0067d000-0067e000 rw-p 00000000 00:00 0 
0163a000-043ff000 rw-p 00000000 00:00 0                                  [heap]
7f02b6ee7000-7f02b6f3e000 r--p 00000000 08:16 3408810                    /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf
7f02b773f000-7f02b7740000 ---p 00000000 00:00 0 
7f02b7740000-7f02b7f40000 rw-p 00000000 00:00 0 
7f02bc69f000-7f02c0000000 r--p 00000000 08:16 3147348                    /usr/share/icons/gnome/icon-theme.cache
7f02c0000000-7f02c0628000 rw-p 00000000 00:00 0 
7f02c0628000-7f02c4000000 ---p 00000000 00:00 0 
7f02c4168000-7f02c416b000 r-xp 00000000 08:16 2755817                    /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-tga.so
7f02c416b000-7f02c436a000 ---p 00003000 08:16 2755817                    /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-tga.so
7f02c436a000-7f02c436b000 r--p 00002000 08:16 2755817                    /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-tga.so
7f02c436b000-7f02c436c000 rw-p 00003000 08:16 2755817                    /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-tga.so
7f02c436c000-7f02c436d000 ---p 00000000 00:00 0 
7f02c436d000-7f02c4b6d000 rw-p 00000000 00:00 0 
7f02c4b6d000-7f02c4b6e000 ---p 00000000 00:00 0 
7f02c4b6e000-7f02c536e000 rw-p 00000000 00:00 0 
7f02c536e000-7f02c538f000 r--p 00000000 08:16 3414133                    /usr/share/fonts/truetype/ttf-liberation/LiberationSansNarrow-Italic.ttf
7f02c538f000-7f02c543f000 r--p 00000000 08:16 3409218                    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
7f02c5528000-7f02c5628000 rw-s 00970000 00:05 13504                      /dev/ati/card0
7f02c5628000-7f02c565e000 r-xp 00000000 08:16 2494134                    /usr/lib/libcroco-0.6.so.3.0.1
7f02c565e000-7f02c585d000 ---p 00036000 08:16 2494134                    /usr/lib/libcroco-0.6.so.3.0.1
7f02c585d000-7f02c585e000 r--p 00035000 08:16 2494134                    /usr/lib/libcroco-0.6.so.3.0.1
7f02c585e000-7f02c5861000 rw-p 00036000 08:16 2494134                    /usr/lib/libcroco-0.6.so.3.0.1
7f02c5861000-7f02c5895000 r-xp 00000000 08:16 2502012                    /usr/lib/x86_64-linux-gnu/librsvg-2.so.2.34.1
7f02c5895000-7f02c5a95000 ---p 00034000 08:16 2502012                    /usr/lib/x86_64-linux-gnu/librsvg-2.so.2.34.1
7f02c5a95000-7f02c5a96000 r--p 00034000 08:16 2502012                    /usr/lib/x86_64-linux-gnu/librsvg-2.so.2.34.1
7f02c5a96000-7f02c5a97000 rw-p 00035000 08:16 2502012                    /usr/lib/x86_64-linux-gnu/librsvg-2.so.2.34.1
7f02c5a97000-7f02c5a99000 r-xp 00000000 08:16 2752552                    /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
7f02c5a99000-7f02c5c98000 ---p 00002000 08:16 2752552                    /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
7f02c5c98000-7f02c5c99000 r--p 00001000 08:16 2752552                    /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
7f02c5c99000-7f02c5c9a000 rw-p 00002000 08:16 2752552                    /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
7f02c5c9a000-7f02c6a98000 r--p 00000000 08:16 3148659                    /usr/share/icons/hicolor/icon-theme.cache
7f02c6a98000-7f02c6b81000 r--p 00000000 08:16 3151553                    /usr/share/icons/Humanity/icon-theme.cache
7f02c6b81000-7f02c6bd3000 r--p 00000000 08:16 3408809                    /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-B.ttf
7f02c6bd3000-7f02c6be9000 r-xp 00000000 08:16 2496868                    /usr/lib/gvfs/libgvfscommon.so
7f02c6be9000-7f02c6de8000 ---p 00016000 08:16 2496868                    /usr/lib/gvfs/libgvfscommon.so
7f02c6de8000-7f02c6de9000 r--p 00015000 08:16 2496868                    /usr/lib/gvfs/libgvfscommon.so
7f02c6de9000-7f02c6dea000 rw-p 00016000 08:16 2496868                    /usr/lib/gvfs/libgvfscommon.so
7f02c6dea000-7f02c6dfd000 r-xp 00000000 08:16 2496869                    /usr/lib/gio/modules/libgioremote-volume-monitor.so
7f02c6dfd000-7f02c6ffc000 ---p 00013000 08:16 2496869                    /usr/lib/gio/modules/libgioremote-volume-monitor.so
7f02c6ffc000-7f02c6ffd000 r--p 00012000 08:16 2496869                    /usr/lib/gio/modules/libgioremote-volume-monitor.so
7f02c6ffd000-7f02c6ffe000 rw-p 00013000 08:16 2496869                    /usr/lib/gio/modules/libgioremote-volume-monitor.so
7f02c6ffe000-7f02c6fff000 ---p 00000000 00:00 0 
7f02c6fff000-7f02c77ff000 rw-p 00000000 00:00 0

---

### Post by jrr_wired on 2011-11-18
So I read this as some error with compiz, and I uninstalled it.  Then from a command line recovery console, I reinstalled compiz
sudo apt-get install compiz
When I tried running unity from the command line, it told me I didn't have unity installed, so I reinstalled that from the command line as well
sudo apt-get install unity

Now, my programs are back in the programs lens, and everything is running.  I'm still bothered that when I tried running a reset the terminal kept getting hung up for twenty to thirty minutes on a line that followed the "Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist" line.

What does that reference?  I removed the extra repositories I had installed from my software sources, and was only going with Canonical, the third parties software sources at the time I tried running this.

---

### Post by Kellemora on 2011-11-18
Many Thanks CORNCOB

THATS JUST WHAT I NEEDED!

I saw it in the list, but didn't know what "Menu Bar" was so used just "Menu"!

Bar usually means something adds an entirely new BLOCK under the existing, as in adding a toolbar in a web browser does.  Which is why I didn't try that option.

My Hats off to ya!
Thanks!

TTUL
Gary

---

### Post by corncob on 2011-11-18
> **Kellemora said:**
> Many Thanks CORNCOB

THATS JUST WHAT I NEEDED!

I saw it in the list, but didn't know what "Menu Bar" was so used just "Menu"!

Bar usually means something adds an entirely new BLOCK under the existing, as in adding a toolbar in a web browser does.  Which is why I didn't try that option.

My Hats off to ya!
Thanks!

TTUL
Gary
Glad to have been able to help.  I did have one more suggestion if that didn't work thinking you might have inadvertently pressed F11-- it toggles the panels on and off.  You might still be able to use that info when you want more screen space.  I'd suggest you mark the thread as 'solved' but I think we hijacked it lol.

---

