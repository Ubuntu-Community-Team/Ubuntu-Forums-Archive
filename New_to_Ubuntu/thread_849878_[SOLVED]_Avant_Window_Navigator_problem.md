---
title: "[SOLVED] Avant Window Navigator problem"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by deadlySniper on 2008-07-04
I used synaptic to download it, it appears in my applications but when I click on the AWN it blinks a white box at me and then disappears. Is there something I am missing or have to install with terminal?

---

### Post by ChameleonDave on 2008-07-05
> **deadlySniper said:**
> I used synaptic to download it, it appears in my applications but when I click on the AWN it blinks a white box at me and then disappears. Is there something I am missing or have to install with terminal?

Other people are reporting crashes with this software.  The latest version seems to be buggy.  It's not to be relied upon.

Update: it opens fine for me, but after a few seconds, it freezes with my icons in mid-bounce.

---

### Post by YaroMan86 on 2008-07-05
Open up a terminal and type the following:

```
avant-window-navigator
```

What is the output?

---

### Post by ChameleonDave on 2008-07-05
> **YaroMan86 said:**
> Open up a terminal and type the following:

```
avant-window-navigator
```

What is the output?

Well, I get this:

```

APPLET : /usr/lib/awn/applets/taskman.desktop
APPLET : /usr/lib/awn/applets/awnterm.desktop
APPLET : /usr/lib/awn/applets/cairo_main_menu.desktop

** (awn-applet-activation:8639): WARNING **: This desktop file does not exist /usr/lib/awn/applets/awnterm.desktop


** (awn-applet-activation:8641): WARNING **: This desktop file does not exist /usr/lib/awn/applets/cairo_main_menu.desktop


(avant-window-navigator:8637): GLib-GObject-WARNING **: cannot register existing type `AwnTitle'

(avant-window-navigator:8637): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

** (avant-window-navigator:8637): CRITICAL **: awn_title_show: assertion `AWN_IS_TITLE (title)' failed

```

---

### Post by YaroMan86 on 2008-07-05
> **ChameleonDave said:**
> Well, I get this:

```

APPLET : /usr/lib/awn/applets/taskman.desktop
APPLET : /usr/lib/awn/applets/awnterm.desktop
APPLET : /usr/lib/awn/applets/cairo_main_menu.desktop

** (awn-applet-activation:8639): WARNING **: This desktop file does not exist /usr/lib/awn/applets/awnterm.desktop


** (awn-applet-activation:8641): WARNING **: This desktop file does not exist /usr/lib/awn/applets/cairo_main_menu.desktop


(avant-window-navigator:8637): GLib-GObject-WARNING **: cannot register existing type `AwnTitle'

(avant-window-navigator:8637): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

** (avant-window-navigator:8637): CRITICAL **: awn_title_show: assertion `AWN_IS_TITLE (title)' failed

```

Looks to me like your configuration for AWN is bad. Try uninstalling it from Synaptic, including configuration files, and try again.

---

### Post by deadlySniper on 2008-07-05
> avant-window-navigator 

I get this
```
Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

```

---

### Post by YaroMan86 on 2008-07-05
That's a no-brainer. :) Make sure you have desktop efects turned on. Ubuntu, since 7.10 Gutsy, has Compiz Fusion installed by default. Just make sure you have a video card that supports it, go to **System -> Preferences -> Appearance** and click on the **Visual Effects** tab and select Minimal or Extra.

Note: If you're feeling lucky, you can try installing compizconfig-setting-manager and customizing your effects. But that's not needed for AWN.

If THAT doesn't wanna work, go into the terminal and type the following:

```
compiz --replace
```

---

### Post by DarkSaga70 on 2008-07-05
> **deadlySniper said:**
> I get this
```
Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

```
Do you have compiz installed?

---

### Post by deadlySniper on 2008-07-05
i do but the screen resolution is too small for me which causes the apps to look very big

---

### Post by DarkSaga70 on 2008-07-05
> **deadlySniper said:**
> i do but the screen resolution is too small for me which causes the apps to look very big

not to be stupid but have you tried to set your resolution?

---

### Post by deadlySniper on 2008-07-05
yes I just did now and I enabled compiz and now the title bars for all my windows are gone and avant is frozen

---

### Post by YaroMan86 on 2008-07-05
> **DarkSaga70 said:**
> not to be stupid but have you tried to set your resolution?

I recommend running displayconfig-gtk and specifying your monitor. That way you get all the resolutions your monitor supports. Autodetect, to put it simply... sucks.

As for titlebars missing... you might wanna make sure Metacity or Emerald are running.

---

### Post by DarkSaga70 on 2008-07-05
ill tell you exactly what i did and you can try it but i had a similar problem. Un install it completley... then follow the help here : [http://www.ubuntugeek.com/howto-install-avant-window-navigator-awn-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/howto-install-avant-window-navigator-awn-in-ubuntu-710-gutsy-gibbon.html)

Then i went into the repos and reinstalled it and it fixed it. Good luck

---

### Post by deadlySniper on 2008-07-05
well I turned off compiz so I can do these things. What it that I might have to do with emerald and avant to get every thing workin

---

### Post by deadlySniper on 2008-07-05
well the only thing that is not workin right now is AWN and I just have to adjust the title bar color

---

### Post by ChameleonDave on 2008-07-05
> **YaroMan86 said:**
> Looks to me like your configuration for AWN is bad. Try uninstalling it from Synaptic, including configuration files, and try again.
No, that's not it.

---

### Post by buntunub on 2008-07-05
AWN requires Compiz to be enabled and properly working. Xubuntu does not have Compiz setup by default. You must follow the guides to setup Compiz properly first, then follow the guides to properly setup AWN and you will be good to go. AWN is stable as hell for me. In fact, AWN has been more stable for me than most other things in Hardy.

---

### Post by tjwoosta on 2008-07-05
> yes I just did now and I enabled compiz and now the title bars for all my windows are gone and avant is frozen
the reason that your compiz --replace command made your window boarders disapear and made awn freeze is because you ran the command from a terminal rather than the run dialouge

press alt-f2
then run the compiz --replace command here

i know this because i had the same issues awile back when doing the emerald --replace command for emerald

---

### Post by pound_forthesound on 2008-07-05
> **ChameleonDave said:**
> No, that's not it.

I appear to have the same problem as you, but only since this morning - everything worked fine yesterday...

Have you managed to find a fix?

---

### Post by ChameleonDave on 2008-07-05
> **pound_forthesound said:**
> I appear to have the same problem as you, but only since this morning - everything worked fine yesterday...

Have you managed to find a fix?

Yeah, I've stopped using it.  ;-)

OK, no, no fix.  I even tried purging and downgrading to the previous version, which worked before.

AWN must now be conflicting with some other updated software.

---

### Post by sharks on 2008-07-05
i think that the XFCE doesnt support AWN that well as GNOME does.

---

### Post by moonbeam on 2008-07-05
Please see:

[http://ubuntuforums.org/showthread.php?t=849005&highlight=avant+window+navigator](http://ubuntuforums.org/showthread.php?t=849005&highlight=avant+window+navigator)

and

[https://bugs.launchpad.net/awn/+bug/245448](https://bugs.launchpad.net/awn/+bug/245448)

The awn package in -proposed is broken.

---

### Post by deadlySniper on 2008-07-05
I forced downgrade and the AWN has the icons move from the bottom left of the screen to the center and freeze. 

P.S. I did downgrade everything with AWN.

---

### Post by ChameleonDave on 2008-07-05
> **moonbeam said:**
> Please see:

[http://ubuntuforums.org/showthread.php?t=849005&highlight=avant+window+navigator](http://ubuntuforums.org/showthread.php?t=849005&highlight=avant+window+navigator)

and

[https://bugs.launchpad.net/awn/+bug/245448](https://bugs.launchpad.net/awn/+bug/245448)

The awn package in -proposed is broken.

That fixed it for me.

I had previously tried to fix it by downgrading, but I forgot to also downgrade libawn0 and libawn-dev.

---

### Post by deadlySniper on 2008-07-05
oops, forgot libawn-dev.

---

### Post by deadlySniper on 2008-07-05
New problem, synaptic says that I hold broken packages

---

### Post by ChameleonDave on 2008-07-05
> **deadlySniper said:**
> New problem, synaptic says that I hold broken packages

Yeah, I got that.

I just removed all of them, and then installed each of them, forcing the version each time.

Strangely, a whole load of other packages magically ended up marked for installation after I installed the AWN packages.  I just ignored that and shut down Synaptic.

---

### Post by pound_forthesound on 2008-07-08
> **ChameleonDave said:**
> Yeah, I've stopped using it.  ;-)

OK, no, no fix.  I even tried purging and downgrading to the previous version, which worked before.

AWN must now be conflicting with some other updated software.

Haha, I've stopped using it for now, too.  Guess I'll wait for a new version or something

Edit: oops, didn't read up on the thread before posting... If the package is broken when will it be fixed?

---

