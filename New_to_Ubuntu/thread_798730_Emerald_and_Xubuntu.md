---
title: "Emerald and Xubuntu"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by saintiria on 2008-05-18
I have Xubuntu Gutsy and I installed emerald and everything required for it to run. My question now is now that I have downloaded some themes how do I enable them? I now that the command is emerald --replace but for some reason every time I  do that nothing happens either in the terminal or with alt+f2. Instead now I have no window border at all around any of my windows and no idea on what to do with emerald. Can anyone help me?

---

### Post by AstralliS on 2008-05-18
You can start Emerald through System >> Preferences >> Emerald. And there you have Import button.

---

### Post by saintiria on 2008-05-18
already did that

---

### Post by AstralliS on 2008-05-18
And nothing changed?

---

### Post by saintiria on 2008-05-18
That was the first that I did of course otherwise if i didn't import the theme how else would I expect it to work? and no nothing changed

---

### Post by AstralliS on 2008-05-18
I have similar problem, can't see my window borders, as title bars on the windows, and when I import some .emerald theme it doesn't change in completeness.

---

### Post by saintiria on 2008-05-18
Does anybody know how to just restore the default xubuntu window manager?

---

### Post by shifty_powers on 2008-05-18
```
sudo apt-get install fusion-icon
```

in a terminal.

then, applications?system tolls>compiz fusion icon

you'll see icon in sys tray in top right, right click it.

select window decorator>emerald

now you will be able to go into your emerald settings and actually apply your themes, or disable it and go back to gtk/compiz combo ;)

---

### Post by AstralliS on 2008-05-18
I've installed that fusion icon, and after installation only I saw was blank screen...

---

### Post by Seamyst on 2008-08-31
> **shifty_powers said:**
> ```
sudo apt-get install fusion-icon
```

in a terminal.

then, applications?system tolls>compiz fusion icon

you'll see icon in sys tray in top right, right click it.

select window decorator>emerald

now you will be able to go into your emerald settings and actually apply your themes, or disable it and go back to gtk/compiz combo ;)

I did that and restarted X, but there's no difference.  Do I need to put Icon or Emerald in Autostarted Apps?  If so, what would the command be?

---

### Post by multisystem on 2010-06-01
Same issue here :(

I'm using Xubuntu 8.10
I have read all threads talking about emerald and tried all solutions, but I can't yet apply any theme in emerald.

I have all compiz dependencies installed, changed "Window Decorator" to Emerald, tried "emerald --replace".

Any help is appreciated. Thanks in advance :)

---

### Post by 4Orbs on 2010-06-01
You might try enabling compositing so the transparency will work. Open the xfce settings mgr and go to the "Window Manager Tweaks" and one of the tabs opens the compositing settings. Don't know it that will fix it or not, I never used compiz on xubuntu. You might go over to the Linux Mint forum and ask, since the Mint xfce version has compiz included and, I presume, working.

---

### Post by multisystem on 2010-06-01
Unfortunately it doesn't work too :(

I'll try Linux Mint forum. Thank you very much :)

---

### Post by multisystem on 2010-06-01
Sorry, I have forgotten to mention that when I write "emerald --replace" in terminal, I get these warnings.

```

(emerald:6853): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",

(emerald:6853): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8

```

---

### Post by 4Orbs on 2010-06-01
Since you are using version 8.10 of Xubuntu, that could be the problem. The theme you're trying to activate depends on the "Ubuntulooks" theme engine for gtk which may not be usable with such an old Xubuntu. You might check in Synaptic pkg mgr and see if  gtk2-engines-ubuntulooks is available for you to install. I don't know what could happen if you do install it. It might be an older engine for gtk rather than gtk2. Wish I could have a better answer for you.

EDIT: The theme you're trying to use... was it downloaded from gnome-look.org or was it already included in emerald? If you got it from gnome-look.org, usually the theme author includes a list of dependencies needed on the theme's home page. You also might want to check xfce-look.org for emerald themes as they may be customized specifically for xfce desktops.

---

### Post by t0p on 2010-06-01
> **4Orbs said:**
> Since you are using version 8.10 of Xubuntu, that could be the problem. The theme you're trying to activate depends on the "Ubuntulooks" theme engine for gtk2 which may not be usable with such an old Xubuntu. You might check in Synaptic pkg mgr and see if  gtk2-engine-ubuntulooks is available for you to install. I don't know what could happen if you do install it. Wish I could have a better answer for you.

I'm almost 100% with 4Orbs.  But the OP stated he's using *Gutst*, which is version 7.10, which is 2 and a half years old.

My recommendation to the OP is see how a more recent version works.  2 and a half years is, like, 21 in dog years.  I don't know how Gibbon time relates to our own, but I suspect Gusty might be old enough to get a driving license now.

---

### Post by Legendary_Bibo on 2010-06-01
try this, it worked for me on xubuntu (karmic)

Hit Alt+F2 then copy and paste this
```
emerald --replace
```

sometimes you have to switch to metacity then replace it with emerald
```
metacity --replace
```

---

### Post by multisystem on 2010-06-02
Really great point 4Orbs. :)

But unfortunately, it doesn't work too :(

gtk2-engines-ubuntulooks wasn't installed. I installed it but it never changes too.

The theme I was trying to apply was from gnome-look, but I tried many themes from xfce-look with the same result, many of them dates back to 2007, which is old enough for Xubutnu 8.10.

I can't upgrade to a newer version of Ubuntu as my old computer performance becomes unsatisfactory.

tried "metacity --replace" before "emerald --replace". It switched successfully to metacity, but doesn't switch to emerald after that.

I don't know what I should do :(

---

### Post by 4Orbs on 2010-06-02
Since you are able to switch to Metacity, I'd guess there is the possibility that you also have a minimal Gnome desktop session available. You might try a Gnome session instead of xfce and see if the theme works with Gnome. You can find the option to change sessions on the login screen.

EDIT: One of the earlier posts mentions the Autostart applications. Maybe if you add compiz or the fusion-icon to autostarted apps, or maybe Metacity. Don't know if any of that would help... it could leave you with a borked desktop or no panels. But it might work if you are bold enough to try.

EDIT2: Now, if this were my computer... and I had /home on a separate partition... or I had all my important files on a separate storage partition... or I had all my important stuff saved somewhere as a backup... I would simply download an old version of Mint xfce CE (maybe Mint 7 ??) and install that instead of Xubuntu. But only if Emerald themes were really, really important to me. Or, just to be cautious, I would install Mint inside a Virtual Box and take a look to see how they got compiz, fusion-icon and emerald to work.

---

### Post by 4Orbs on 2010-06-02
About the disappearing window borders. The same thing happened to me back when I was using Ubuntu 8.10 and the reason they had disappeared was because, before I activated my graphics driver and desktop effects, I had changed to a different screen resolution than the native resolution that was detected by Ubuntu when first installed.

The fix was this: switch back to the native resolution and if that restores the window frames... manually edit the xorg.conf file and remove all resolution options from the file EXCEPT the one resolution I wanted to keep.

---

### Post by multisystem on 2010-06-02
since I don't have Gnome session installed, I'll give Ubuntu 8.10 a try. If that doesn't help, I'll install Mint 7 inside a VirtualBox.

Thank you very much 4Orbs :) , really you're a great helper. Thanks a lot for your help and patience.

---

