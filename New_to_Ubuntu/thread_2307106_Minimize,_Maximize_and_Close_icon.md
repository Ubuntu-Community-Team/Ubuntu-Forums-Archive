---
title: "Minimize, Maximize and Close icon"
date: 2015-12-22
forum: New to Ubuntu
---

### Post by Jayanth_Krishnamoo on 2015-12-22
I've recently installed Ubuntu 14.04 in my desktop. The 'minimize, maximize and close' icons are appearing on the top left hand side on my desktop. I have two questions to request:-

1. How to move the icons from the top left to the top right?
2. How to interchange the icons? For example, I have 'Close, Minimize and Maximize'. I need to reorder them to 'Minimize, Maximize and Close'. How to go about doing the same?

Kindly help.

K.N.Jayanth Krishnamoorthy

---

### Post by claracc on 2015-12-22
Please, see: [http://ubuntuforums.org/showthread.php?t=2255495](http://ubuntuforums.org/showthread.php?t=2255495)

I hope it helps

---

### Post by Jayanth_Krishnamoo on 2015-12-22
The above link says it cannot be done. Isn't there any way to change the icons to the right, at all?

---

### Post by howefield on 2015-12-22
I do not believe that you can change the button order or placement any more, at least not without a supreme effort recoding the relevant bits.

Your best option might be to use a different desktop environment or go all the way back to Ubuntu 12.04 which is supported till April 2017.

---

### Post by buzzingrobot on 2015-12-22
> **Jayanth_Krishnamoo said:**
> 2. How to interchange the icons? For example, I have 'Close, Minimize and Maximize'. I need to reorder them to 'Minimize, Maximize and Close'. How to go about doing the same?


That might be configurable but I'm not sure.  Install dconf-editor and navigate to the org.gnome.desktop.wm section.  There may be a "preferences" setting there that allows rearranging the "button-layout". If it's there on Unity, you can click on the text string that's there as the default and edit it as you wish.

---

### Post by philinux on 2015-12-22
Install deconf-editor

```
sudo apt-get install dconf-editor
```

Run it from terminal or Dash. 

See screenshot.

---

### Post by Image on 2015-12-23
> **philinux said:**
> Install deconf-editor

```
sudo apt-get install dconf-editor
```

Run it from terminal or Dash. 

See screenshot.

I installed this but I dont see the options shown in your screen shot. 14.04

---

### Post by leunam12 on 2015-12-24
It cannot be done if you are running Unity Desktop. Switch to a different Desktop Environment. to move my buttons to the right I uninstalled Unity and now use Cairo-Dock Desktop.

---

### Post by monkeybrain20122 on 2015-12-24
It cannot be done normally. However, there is one way that I know but with a catch. Install emerald following instructions from link. See the screenshots.

[http://www.noobslab.com/2014/02/emerald-decorator-and-themes-available.html](http://www.noobslab.com/2014/02/emerald-decorator-and-themes-available.html)

The catch is if you go fullscreen the buttons will revert to the left.

---

### Post by monkeybrain20122 on 2015-12-24
> **philinux said:**
> Install deconf-editor

```
sudo apt-get install dconf-editor
```

Run it from terminal or Dash. 

See screenshot.

That never works with unity, used to work with gnome-shell to change button to the left (right is default), but not anymore since 3.18. If you do that the menus for gnome apps will go missing.

---

### Post by philinux on 2015-12-24
> **monkeybrain20122 said:**
> That never works with unity, used to work with gnome-shell to change button to the left (right is default), but not anymore since 3.18. If you do that the menus for gnome apps will go missing.

Ah well. I've got so used to the buttons on the left i get confused when I boot into Win 10 now. :p

---

### Post by monkeybrain20122 on 2015-12-27
> **philinux said:**
> Ah well. I've got so used to the buttons on the left i get confused when I boot into Win 10 now. :p

Yeah I am used to buttons on the left too, that's why I know the dconf editing trick, I used it to put the button on the left on Fedora. :)

---

### Post by thomassisson on 2016-08-25
This works in gnome-flashback, a.k.a. gnome-fallback, a.k.a. Gnome Classic.

gsettings [FONT=monospace][COLOR=#000000]set org.gnome.desktop.wm.preferences button-layout menu:minimize,maximize,close

This should work with dconf-tool or dconf-edit, as well.

Notice the menu to the left of the colon and the other buttons to the right of the colon. I saw part of this on an Ubuntu Forum review from the beginning of 2016. All I had was the close button. I kept guessing until the app icon and window title was added with the word menu.

I don't know about Unity, but I recall it basically just stole from Gnome including gsettings, gconf, dconf*, etc. It's pretty, but it looks like an OS for a phone or tablet. I found it quite annoying. I'm also a regular KDE user, but KDE is becoming bloatware.


[/COLOR]
[/FONT]

---

