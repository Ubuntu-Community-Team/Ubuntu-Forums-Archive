---
title: "Changes to Compiz and Load time - debugging"
date: 2011-09-16
forum: New to Ubuntu
---

### Post by psylencer on 2011-09-16
Ok here's the story,

I've created an image using clozilla - restore the image - everything loads fine in around 45 seconds.

I edit the /home/myuser/config/compiz-1/compizconfig/default.ini
to reflect changes which I have backed up from a previous install.  Load time almost doubles.  My immediate thoughts are OK - something in this file is causing the slow load time - so for giggles, I restore the file to its original settings (from a backup made before making changes).  Problem is, load time remains doubled, even though the only file I have edited is the aforementioned file and it is now back to its original state.

Could anyone please explain what's happening or perhaps define a process so I can debug this annoying issue.


Many thanks in advance.

---

### Post by Lisiano on 2011-09-16
Could you post the the Before and After files? I assume you already did some tweaking in Gconf?

---

### Post by psylencer on 2011-09-16
Sure here you go : 

**Before :**
[core]
s0_number_of_desktops = 2
s0_active_plugins = core;bailer;detection;composite;opengl;decor;mousepoll;resize;compiztoolbox;move;regex;grid;place;gnomecompat;wall;animation;imgpng;vpswitch;snap;fade;scale;workarounds;expo;ezoom;session;switcher;

[composite]
s0_refresh_rate = 120

**After :**
[core]
s0_number_of_desktops = 2
s0_active_plugins = core;bailer;detection;composite;opengl;decor;mousepoll;resize;compiztoolbox;move;regex;grid;place;gnomecompat;wall;imgpng;vpswitch;staticswitcher;snap;session;

[composite]
s0_refresh_rate = 200
s0_detect_refresh_rate = false
s0_unredirect_fullscreen_windows = true
s0_force_independent_output_painting = true

[opengl]
s0_texture_filter = 0


Again, after reverting to the original file, load time remains doubled. It should also be noted that that is the ONLY file I have knowingly modified.  Ie start up system, change file, save it then reboot. 

The real question is why, after reverting to the original does the system take as long to boot? Incidentally, I tried an experiment by only changing the composite section and leaving the plugins as is.  That was enough to cause the longer irreversible boot time.  


thanks for your help.

---

### Post by Lisiano on 2011-09-16
Ah. I think I get it now. Press Alt+F2 and open gconf-editor and navigate to /desktop/gnome/session/required_components then change the windowmanager string to say metacity instead of wm-manage or something. Now I assume you have fusion-icon installed? If not install it. Add fusion-icon to your autorun in System -> Preference -> Autostart applications (Bear with me, going by memory) and add a new entry with any name and description you will understand and command "fusion-icon" (No quotes) . Next time you boot, metacity will launch instead of compiz (Ubuntu default) but fusion-icon will load and replace it with compiz.

EDIT: You also need to actually tell fusion-icon (Looks like a blue box with a mouse arrow) to start compiz. Just Right-click -> Select Windows Manager -> Compiz

---

