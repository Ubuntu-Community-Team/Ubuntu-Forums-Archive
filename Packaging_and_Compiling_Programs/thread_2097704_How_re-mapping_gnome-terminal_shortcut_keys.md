---
title: "How re-mapping gnome-terminal shortcut keys"
date: 2012-12-24
forum: Packaging and Compiling Programs
---

### Post by woainvzu on 2012-12-24
According to the [Gnome-Termianl Usage]("http://library.gnome.org/users/gnome-terminal/stable/gnome-terminal-usage.html.en#gnome-terminal-contents"), I found that **ctrl**+**shift**+**up**/**down **can **scroll up/down** a line in the terminal.
  Now, I want to re-maping the shortcut key, just like: **alt**+**j**/**k** to **scroll up/down** a line, that's the old habit of vimer. :) I tried searching the settings in **Edit** -> **Keyboard Shortcuts** of Terminal, but found nothing.
  And, the **keybindings **still cannot be found at **~/.gconf/apps/gnome-terminal/** also.
  

I've tried to find the information about **readline** ($ bind -p),  only terminal character shortcuts and command were found (like: C-d:  delete a char, C-a: at the beginning of command , etc...), the scroll  command still cannot be found.
  

Can anyone help me? Thanks in advance.

---------------------
The information of my computer is :
  > $ cat /etc/issue Ubuntu 12.10 \n \l   By the way, I'v used **AutoHotKey** to re-map the shortcuts in Windwos OS.

---

### Post by woainvzu on 2013-01-07
Hi,

No one knows how to do it?

---

### Post by butt head on 2013-01-18
When you have the Keyboard Shortcuts pop-up open and you see the current shortcuts, simply click on the shortcut key for the action you want to change, then enter the new shortcut, ie if you want to change the Close Window action to CTRL E, just click on the current shortcut and push those two keys and the shortcut will be set to that combination.

Hope that helps.

BH

---

### Post by woainvzu on 2013-02-10
> **butt head said:**
> When you have the Keyboard Shortcuts pop-up open and you see the current shortcuts, simply click on the shortcut key for the action you want to change, then enter the new shortcut, ie if you want to change the Close Window action to CTRL E, just click on the current shortcut and push those two keys and the shortcut will be set to that combination.

Hope that helps.

BH

Thanks BH, I know how to change the 'regular' shortcuts. But there no way to change the shortcut for scoll up/down.

---

