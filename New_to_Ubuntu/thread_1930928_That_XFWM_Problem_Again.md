---
title: "That XFWM Problem Again"
date: 2012-02-24
forum: New to Ubuntu
---

### Post by qazokm2 on 2012-02-24
> EDIT: I've been told I should specify that this problem is not with xubuntu really, but with xubuntu-desktop installed over a normal ubuntu install (oneiric).
Hi, first post. I am having the seemingly well known problem of xfwm not running at start-up, leaving my windows unable to be moved/focused. I have removed compiz, unity, nautilus. and ubuntudesktop, and even reinstalled ubuntu (which works fine for a spell), but the problem persists.

I noticed a precursor to the problem is that, one day, the desktop will suddenly change from the xfce wallpaper to the default ubuntu purple gnome wallpaper. There is then a  bar at the top (which is like an out of window menu bar for whichever window is highlighted, know what i mean?) that i think is used in unity. The desktop icons, except for program launchers, disappear, and the right click menu seems changed from xfce's.  However, the xfce application menu bar, which i put at the bottom, is also still around. So its kind of like both are running at the same time.

So anyway, I try to alleviate this by reloading xfdesktop, but it does nothing. Reloading xfwm4 flickers the old desktop into being for a few seconds, but then it goes right back to the original.

Finally, I restart. The desktop seems returned to normal...but the main problem now shows itself. As i have reproduced, the bars at the top of windows won't focus. Deleting the session folder in ./.cache did not work for me. So, as is detailed [here(url),]("http://ubuntuforums.org/showthread.php?t=1821623&highlight=xfwm4+display") i set it to replace. The response is(this is in ctrl+alt+F1 by the way):
```
xfwm4-CRITICAL **: Xfconf could not be initialised
xfwm4-WARNING **: Missing data from default files
```
And so this is how I proceed, and what i get:
```
$: xfwm4
   (xfwm4:2069) GTK Warning: cannot open display.
$: export DISPLAY=:0
$: xfwm4
   (xfwm4:3084): xfwm4-WARNING **: Failed to connect to session manager: Failed to connect to the session manager: SESSION_MANAGER environment variable not defined
```

And then everything works peachy. However, it does tie up my 'emergency console' as I call it, since i have to do all of it in ctrl+alt+F1, and as it's running there if I ctrl+C and end it, xfwm4 terminates too.

Here is my .xsession-error file right after I get it running: ```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/startxfce4: X server already running on display :0
ssh-agent is already running
xfdesktop[1556]: starting up
xfce4-settings-helper: Another instance is already running. Leaving...
** (process:1621): DEBUG: Telepathy Indicator started

(polkit-gnome-authentication-agent-1:1617): polkit-gnome-1-WARNING **: Failed to register client: The name org.gnome.SessionManager was not provided by any .service files
** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/blueman/plugins/BasePlugin.py", line 65, in _load
    self.on_load(parent)
  File "/usr/lib/python2.7/dist-packages/blueman/plugins/applet/PulseAudio.py", line 173, in on_load
    raise Exception("PulseAudio too old, required 0.9.15 or higher")
Exception: PulseAudio too old, required 0.9.15 or higher
xfce4-panel: No window manager registered on screen 0. To start the panel without this check, run with --disable-wm-check.
** Message: applet now embedded in the notification area

(Thunar:1548): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed
** (process:1591): DEBUG: desktop-launch-listener.vala:118: ran with uri: file:///home/qazokm/.xsession-errors
** (process:1591): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events 
```

My question is, what is causing the problem, if you can yet tell, and how do I get things to work on start-up? If possible I would like to treat the cause, not the symptom. Also, I'm extremely illiterate, if you haven't already been able to tell.

Sorry for the seemingly exhaustively long post, but I really wanted to be as thorough as possible. Thanks in advance!

EDIT: I'm considering removing metacity, as seems to be one of the general recommendations, but would like some thoughtful suggestions before proceeding any further.

I stated that deleting the session folder did not work for me. that was because I was still saving my session when restarting. For all of my noob kin, when you shudown using the log off button in the application menu, uncheck 'save session for future logins' at the bottom of the menu that pops up. This will solve the problem on restart.

---

### Post by Elfy on 2012-02-24
Closed as fixed and solved after IRC session.

---

