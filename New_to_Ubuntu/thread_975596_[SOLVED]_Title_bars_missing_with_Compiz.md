---
title: "[SOLVED] Title bars missing with Compiz"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by AncientPC on 2008-11-08
Compiz worked fine in 8.04, but after upgrading to 8.10 my titlebars started missing from all my applications.  Anybody know what may be causing this?

---

### Post by alienexplorers on 2008-11-08
add this line to your screen section of xorg.conf:
> Option "AddARGBGLXVisuals"  "true"

---

### Post by Bloch on 2008-11-08
This used to happen to me too.
I changed themes and it was fine. 

I'm not sure why, but some themes make unusual demands on your graphics card.

---

### Post by NIT006.5 on 2008-11-08
Yep it could be something to do with the theme... I remember having huge issues at one point and eventually finding out that it was something to do with the Crux theme.

What window decorator were you using though? The default metacity? Or had you installed something like Emerald? In order to troubleshoot, you could try to start your window decorator from terminal, and that way you would see any errors etc. and might be able to figure out why it's failing.

If you're using the default and haven't installed a different one, then you would use:

metacity --replace

If you installed a different one, then substitute the command accordingly. for instance:

emerald --replace

If you get any specific errors, you could then do a search on the exact error text and see if that gives any further clues.

Hmm... an after-thought: if you do metacity --replace I think it might turn compiz off entirely. But it wouldn't for something like emerald. However, if you don't find any solutions for metacity, you could always try emerald. Generally that's all I use.

---

### Post by AncientPC on 2008-11-08
> **alienexplorers said:**
> add this line to your screen section of xorg.conf:

Added this line to xorg.conf and rebooted but still missing title bars.

I switched themes back to Human from Dark Room, but still am missing title bars.

Running `metacity --replace` worked but only because it disabled Compiz . . .

I'd also like to add that this same error occurs on another laptop when I upgraded to 8.10.  This hasn't happened to anyone else?

---

### Post by asgard_command on 2008-11-08
I know this is a bit obvious but you haven't got the window decoration option unchecked in compiz have you.

---

### Post by AncientPC on 2008-11-12
Window decoration is enabled within Compiz.

Any other suggestions?

---

### Post by pastalavista on 2008-11-12
> **AncientPC said:**
> Window decoration is enabled within Compiz.

Any other suggestions?

I was going to suggest disabling window decorations in compiz. It was the only way I could keep my title bars. It conflicted with Metacity, I think.

---

### Post by sharkster2007 on 2008-11-12
I too have the titlebar problem

I heard elsewhere that it was down to Nvidia's Drivers (From Version 97 & above) as they are "closed source" we unfortunately have to wait for Nvidia to make new drivers :-(

PS: The "Open Source" ones only support 2D but not 3D as yet

*Sorry I thought you meant the blank titlebar problem, just re-read it seems yours are missing altogether, I haven't experienced this problem*

---

### Post by AncientPC on 2008-11-12
Tried disabling window decoration but it doesn't work.  In either case, the [screen tearing]("http://http://ubuntuforums.org/showthread.php?p=6164795") is really bad whenever I'm running Compiz.  It's slightly better when I'm running Metacity.  I'm running an Intel 4500 MHD on a Dell E6500 laptop.

On the other hand, I have another Dell Inspiron 6000 laptop with a Radeon 7000 that's been running Compiz fine since 7.10.  However 8.10 has broken Compiz with the missing title bars as well.

---

### Post by blazoner on 2008-11-13
Try checking to see if compiz-fusion and its various parts are still installed. That's what I just got finished doing, and, voila! title bars have returned.

---

### Post by starcannon on 2008-11-13
Be sure to grab a handy little desktop utility called fusion-icon, it runs in the system tray and makes reloading window decorators and desktop managers a breeze.
```
sudo apt-get install fusion-icon
```
You will find this new program in:
Applications>System Tools>Fusion Icon

R-clicking the icon in the system tray located in the upper right corner of your monitor on a default Ubuntu(gnome) install, it looks like a little blue box, will bring up a menu, each submenu will offer you some options to play with, including but not limited to restarting your window decorator, as well as your desktop manager.

GL and have fun.

---

### Post by AncientPC on 2008-11-13
I re-installed compiz but that didn't help.  After installing fusion-icon and switching to Metacity and back to Compiz gave me title bars!  I can't understand why installing the icon would help, but either way now I have title bars, yay!

Thanks for the help everyone!

---

### Post by AncientPC on 2008-11-14
I just wanted to add that I fixed the title bar issue on another laptop simply by installing fusion-icon . . .

---

