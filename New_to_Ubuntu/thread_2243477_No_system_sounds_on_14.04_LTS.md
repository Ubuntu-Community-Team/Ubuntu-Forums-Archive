---
title: "No system sounds on 14.04 LTS?"
date: 2014-09-09
forum: New to Ubuntu
---

### Post by rgotolei on 2014-09-09
Didn't want to necro, but I suppose it's better than making yet another thread about this.

I can't seem to get it working here. I've enabled event and inputfeedback sounds in both dconf and xfconf, installed gnome-session-canberra and its dependencies, created [the two files]("http://ubuntuforums.org/showthread.php?t=1869787&p=12079098#post12079098")..
Only thing I've done differently is set the sound theme to freedesktop.

```
raster@meridian:~$ xfconf-query -c xsettings -p /Net/SoundThemeName
freedesktop
raster@meridian:~$ env | grep GTK_MODULE
raster@meridian:~$ ls /usr/share/sounds/$(xfconf-query -c xsettings -p /Net/SoundThemeName)/stereo
alarm-clock-elapsed.oga        camera-shutter.oga              phone-incoming-call.oga
audio-channel-front-center.oga    complete.oga                  phone-outgoing-busy.oga
audio-channel-front-left.oga    device-added.oga              phone-outgoing-calling.oga
audio-channel-front-right.oga    device-removed.oga              power-plug.oga
audio-channel-rear-center.oga    dialog-error.oga              power-unplug.oga
audio-channel-rear-left.oga    dialog-information.oga              screen-capture.oga
audio-channel-rear-right.oga    dialog-warning.oga              service-login.oga
audio-channel-side-left.oga    message-new-instant.oga              service-logout.oga
audio-channel-side-right.oga    message.oga                  suspend-error.oga
audio-test-signal.oga        network-connectivity-established.oga  trash-empty.oga
audio-volume-change.oga        network-connectivity-lost.oga          window-attention.oga
bell.oga            onboard-key-feedback.oga          window-question.oga
raster@meridian:~$ which canberra-gtk-play
/usr/bin/canberra-gtk-play
raster@meridian:~$ xfconf-query -c xsettings -p /Net/EnableEventSounds
true
raster@meridian:~$ xfconf-query -c xsettings -p /Net/EnableInputFeedbackSounds
true
```

All I can see that might be out of place is 'env | grep GTK_MODULE' returned nothing.
But wasn't creating the two files in /etc/X11/Xsession.d supposed to fix that? Is there some sort of cache that needs to be rebuilt, or perms set?

I've restarted, and 'system sounds' is not muted (and is set ~70%) in pavucontrol.

Xubuntu 14.04, just like the original post.. What am I missing?

---

### Post by coffeecat on 2014-09-09
> **rgotolei said:**
> Didn't want to necro, but I suppose it's better than making yet another thread about this.

Did you not see the [SOLVED] prefix on the old thread? The chances of you getting help on an old thread marked solved is remote. I've moved your post to its own thread and added the xubuntu prefix to the thread title.

---

### Post by Toz on 2014-09-09
> **rgotolei said:**
> All I can see that might be out of place is 'env | grep GTK_MODULE' returned nothing.
This is the problem. Can we see the content of the files that you created?
```
cat /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules
cat /etc/X11/Xsession.d/52libcanberra-gtk3-module_add-to-gtk-modules
```

System sounds do work in 14.04 with those directions.

---

