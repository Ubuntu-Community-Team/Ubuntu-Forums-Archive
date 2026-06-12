---
title: "How do I change from Ambiance to Radiance?"
date: 2011-07-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by iClouseau88 on 2011-07-09
Hi,

I am using Ubuntu 11.10 i386 the latest kernel 3.0-3-generic. I also installed "light-themes" version 0.1.8.18.

I would like to be able to change Adwaita gtk-theme from the default Ambiance (dark theme) to Radiance (lighter theme), so that bookmarks and everything else will be easier to find and see!

I did try running "dconf-editor":

org >gnome >desktop >interface >gtk-theme

Changed Adwaita to Radiance

Set to Default

However, nothing got changed!

Any suggestions?  Thanks a lot for your help!

:confused:

---

### Post by dino99 on 2011-07-09
try with gnome-tweak-tool

---

### Post by Harry33 on 2011-07-09
> **iClouseau88 said:**
> Hi,
...
I would like to be able to change Adwaita gtk-theme from the default Ambiance (dark theme) to Radiance (lighter theme), so that bookmarks and everything else will be easier to find and see!
...
Any suggestions?  Thanks a lot for your help!
:confused:

Adwaita is the default theme of Gnome.
Ambiance and Radiance are Ubuntu-specific themes.
So, if you have Ambiance, then you are not using Adwaita.

---

### Post by MacUntu on 2011-07-09
Also keep in mind that unity-window-decorator uses the theme set for Metacity, so you need to change that using gconf-editor.

---

### Post by iClouseau88 on 2011-07-09
Hello Harry33,

On my login screen, Gnome is one of the 3 choices but when I select it I saw a file error message called "failed to load session Gnome".  As a result, I always choose Ubuntu2D and not Ubuntu.

The gtk-theme interface screen shows [COLOR="blue"]Adwaita[/COLOR] as default:

gtk-theme: Adwaita
icon-theme: ubuntu-mono-dark

---

### Post by JRV on 2011-07-09
> **MacUntu said:**
> Also keep in mind that unity-window-decorator uses the theme set for Metacity, so you need to change that using gconf-editor.

That worked for me, thank you.

---

### Post by iClouseau88 on 2011-07-09
Hello MacUntu and JRV,

I installed gconf-editor then opened the terminal:

```

gconf-editor

```

[LIST=1]
[*]apps > metacity > general > theme

[*]Right click > edit key

[*]Change from "ambiance" (default key value) to "radiance"

[*]Reboot
[/LIST]

Still same very dark black/brown navigation bar after reboot!

:confused:

---

### Post by iClouseau88 on 2011-07-09
Hello dino99,

gnome-tweak-tool is not yet installed. It depends on gnome-shell which in turn depends on libgnome-desktop-3-2, which depends on gnome-desktop3-data but this last package would have to be downgraded to version 3.0.2-2.

Too much hassle already!

For now, Kubuntu 11.10 has been much smoother to use than its Ubuntu counterpart.  Come October if Ubuntu 11.10 doesn't have Gnome 3 ready to use out of the box I may permanently use Kubuntu 11.10 instead.

---

### Post by MacUntu on 2011-07-09
What navigation bar are you talking about? Can you add a screenshot?

---

### Post by iClouseau88 on 2011-07-09
Hello MacUntu,

I meant the one on the top to the right of the grey Ubuntu icon.  It has NM, sound, time, instant messaging or chat, and on/off icons.

---

### Post by MacUntu on 2011-07-09
Yeah, that should be changed when doing 

```
gsettings set org.gnome.desktop.interface gtk-theme 'Radiance'
```

(or using dconf-editor). Do you have a 'gtk-3.0' folder in '/usr/share/themes/Radiance'? Do you have 'gtk3-engines-unico' installed?

---

### Post by iClouseau88 on 2011-07-09
> **MacUntu said:**
> Yeah, that should be changed when doing 

```
gsettings set org.gnome.desktop.interface gtk-theme 'Radiance'
```

(or using dconf-editor). Do you have a 'gtk-3.0' folder in '/usr/share/themes/Radiance'? Do you have 'gtk3-engines-unico' installed?

Hi MacUntu,

1. Yes, I do have the gtk-3.0 folder in /usr/share/themes/Radiance

2.  Yes, I do have gtk3-engines-unico installed, and its version is the latest, i.e. 0.1.0+r740ubuntu

---

### Post by iClouseau88 on 2011-07-10
Hi everyone,

I seem to have accidentally achieved my goal of having a lighter theme in an indirect way: 

I was also working on getting Google Chrome/Chromium icon show up on the desktop.  Found that these browsers load via the terminal, but the dash (vertical band on the left side of the desktop) shows the browser icons but when right-clicked the icons has no "keep in launcher" option.  Further googling shows Bug#657771 in Unity.  This has 2 work-around options:

1. Install libunity-dev then restart

2.  sudo dpkg-reconfigure libunity, then logout and login

Tried Option 1 first, didn't work so removed it.  Installed unitycore-4.0-dev but Synaptic removes all the indicator icons except those representing NM (RedX but still shows network info) and userid. As I installed indicator-session-gtk2 in order to get the power icon back, Synaptic removes unity2D.

I then tried the 2nd option above and reboot.  After reboot, I cannot boot into ubuntu (unity) 2D obviously, but had no other choice but to boot into ubuntu.  The gnome session boot shows "failed to load session "gnome".

After booting into ubuntu (classic?), I noticed that the bar on top is very light gray in color and shows faint icons of NM, sound, envelope (chat & broadcast), power and darker icons of time/date and userid.  All these icons work, by the way.

In short, I believe the change to Radiance theme along with the removal of unity2D has lead to a lighter horizontal bar on top, for ubuntu (classic?).

I would appreciate your comments and suggestions.

:D

---

