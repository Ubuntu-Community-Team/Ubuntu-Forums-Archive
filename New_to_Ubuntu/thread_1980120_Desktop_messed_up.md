---
title: "Desktop messed up"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by s1baker on 2012-05-14
I just tried to change some "Users and Groups" settings and after I logged out, then back in to see if they would work, I notice now my Desktop environment is messed up. For example:
( I am using xfce )

  I only have one workspace showing in my panel, although the panel preferences show 6, as it was originally set.

   When I try to open a window such as Firefox or gedit, there are no little icons that will let me shrink the window down, nor are there any grips on the windows to allow the window to be resized, or even moved for that matter. 
Anybody know what might have happened.

---

### Post by QIII on 2012-05-14
Are you using Compiz?

If so, the number of desktops will have to be set in CCSM.

If not, (I'm not at my Xubuntu machine, so bear with my old memory)  you'll have to go to settings, window settings and change the number of  desktops there.

I've never managed to get this to work right just using the panel icon.

As for the buttons, that may be due (if you are using Compiz) to not having Window Decorations checked in CCSM.

You may also have to experiment with gtk-window-manager, but before you do that wait for more detail.  I don't want to get into that from memory.

---

### Post by s1baker on 2012-05-14
I'm not using Compiz.
Also, if it matters, I am using the xfce desktop.
When I try to select Applications Menu/Settings/Windows Manager, or Windows Manager Tweeks, nothing happens, as if it is not there.
I know it was before.

There are no windowing frames around any of the programs that I can run.

---

### Post by QIII on 2012-05-14
Could you create a new user account, log in and see what it looks like?  It might be a user profile issue, but let's not mess with your current one for the time being.

---

### Post by s1baker on 2012-05-14
I found out what the problem was.
I needed to run xfwm4 in a terminal to get the settings back.
( This is for the xfce desktop )

---

