---
title: "How to change look to the new one?"
date: 2012-02-19
forum: New to Ubuntu
---

### Post by Agusia on 2012-02-19
Hi All. :)
I've got a problem. I've been changing something and now my Ubuntu looks so old. How to fix this??

---

### Post by MG&amp;TL on 2012-02-19
> **Agusia said:**
> Hi All. :)
I've got a problem. I've been changing something and now my Ubuntu looks so old. How to fix this??

Which release are you running? Somehow the gtk theme has reset itself to defaults, that's all. :) Easily fixed.

---

### Post by Agusia on 2012-02-19
I've got Ubuntu 11.10.

---

### Post by Baldrick_NZ on 2012-02-19
Right click on the desktop, click "Change Desktop Background", and under 'Theme' choose either 'Radience' or 'Ambience'.

This should fix the prob.

Welcome aboard the Ubuntu bandwagon! :-)

---

### Post by MG&amp;TL on 2012-02-19
Okay, run the following command in the terminal to install gnome-tweak tool. (There is no doubt a way to do it without this, but I can't find anything.

```
sudo apt-get install gnome-tweak-tool
```Then launch 'advanced settings' from the dash. click the theme button, then set "Gtk+ theme" to your choice (Ambiance is the default Ubuntu one). You might have to log out and in again, but there again, maybe not.

EDIT: ^^ that works too. :D

---

### Post by Agusia on 2012-02-19
> **Baldrick_NZ said:**
> Right click on the desktop, click "Change Desktop Background", and under 'Theme' choose either 'Radience' or 'Ambience'.

This should fix the prob.

Welcome aboard the Ubuntu bandwagon! :-)
It doesn't fix it. :(
Does that "!" shows that something is wrong??

---

### Post by MG&amp;TL on 2012-02-19
> **Agusia said:**
> It doesn't fix it. :(
Does that "!" shows that something is wrong??

No, that's on mine too. Have you tried logging out and in again?

---

### Post by Agusia on 2012-02-19
I've turned my computer again and it didn't help. :/

---

### Post by mcduck on 2012-02-19
> **Agusia said:**
> It doesn't fix it. :(
Does that "!" shows that something is wrong??

That warning is next to *Shell theme* which is related to Gnome Shell, not Unity desktop. So you see the warning sign simply because you aren't running Gnome-Shell at the moment and thus that setting doesn't apply to you.

Anyway, open and try running "gnome-settings-daemon". Does it fix the problem? Do you get any error messages?

---

### Post by Agusia on 2012-02-19
agusia@Acer:~$ gnome-settings-daemon
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"

** (gnome-settings-daemon:2151): WARNING **: You can only run one xsettings manager at a time; exiting

** (gnome-settings-daemon:2151): WARNING **: Unable to start xsettings manager: Could not initialize xsettings manager.
[1329647379,000,xklavier.c:xkl_engine_start_listen/] 	The backend does not require manual layout management - but it is provided by the application

(gnome-settings-daemon:2151): media-keys-plugin-WARNING **: Grab failed for some keys, another application may already have access the them.

(gnome-settings-daemon:2151): clipboard-plugin-WARNING **: Clipboard manager is already running.

** (gnome-settings-daemon:2151): WARNING **: Name taken or bus went away - shutting down

---

### Post by Agusia on 2012-03-01
I still haven't repaired it. :(
Can somebody help me?? :(

---

### Post by Agusia on 2012-03-02
Please. :(

---

### Post by Krytarik on 2012-03-02
Please try this workaround; although it's quite strange if that's still needed in some occasions, even with LightDM as the display manager, but that's confirmed in at least one other case:

[http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html](http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html)

Hope that works.

---

### Post by Agusia on 2012-03-03
No, it still doesn't work. :( But thanks for help. :)
I've also have a problem with my desktop, it doesn't work, I can't click on it and when i try the right-click, the menu doesn't show. Maybe this has something to do with this too.

---

### Post by Krytarik on 2012-03-03
> **Agusia said:**
> No, it still doesn't work. :( But thanks for help. :)
Sorry that that workaround doesn't work for you - actually good, since that fosters the theory that without both the login screen *and* the desktop session using "gnome-settings-daemon", you don't need that workaround anymore. :P

> **Agusia said:**
> I've also have a problem with my desktop, it doesn't work, I can't click on it and when i try the right-click, the menu doesn't show.
Make sure that "Have file manager handle the desktop" is enabled under "Advanced Settings -> Desktop".

---

### Post by Agusia on 2012-03-03
Yes, I've got this enabled. Additionally I can't even open any folder on my computer. Is there any easy way to re-install the whole system?? I think that would be the best way to repair it. Or maybe I should install any other Linux system??

---

### Post by Krytarik on 2012-03-03
> **Agusia said:**
> Additionally I can't even open any folder on my computer.
Do you mean via the "Places" menu, or the Unity Dash? If yes to any of these, try this:
```
sed -i '/inode\/directory/d' ~/.local/share/applications/mimeapps.list
```> **Agusia said:**
> Is there any easy way to re-install the whole system?? I think that would be the best way to repair it.
Nope, only the 'back up all your personal stuff and start over' method. :P But before you resort to something like that, please create a new user and check if those or any other issues you may not have mentioned yet are present in that new user account, too.

> **Agusia said:**
> Or maybe I should install any other Linux system??
Well, that depends on how much you like the Ubuntu 'system', obviously - whether or not you like Unity, but that definitely helps. :P If you decide to stick with Ubuntu, I'd recommend heading straight to its next version, Precise 12.04 LTS (!), which is now available as Beta, and should already work pretty stable:

[https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta1](https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta1)

---

### Post by Agusia on 2012-03-03
I've managed to fix all the problems. ;)
PS
I'm writing to you from Ubuntu 12.04. :)

---

### Post by Krytarik on 2012-03-03
> **Agusia said:**
> I've managed to fix all the problems. ;)
PS
I'm writing to you from Ubuntu 12.04. :)
:popcorn: LOL :D

---

