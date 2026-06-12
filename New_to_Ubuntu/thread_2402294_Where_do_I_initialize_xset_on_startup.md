---
title: "Where do I initialize xset on startup"
date: 2018-09-28
forum: New to Ubuntu
---

### Post by bedo2991 on 2018-09-28
Hi all, I am trying to build a PC that just turns on, opens a browser in fullscreen mode and then runs happily forever.

I've managed to do everything with Lubuntu, apart from disabling the screensaver.

If I manually give those commands:
```
xset -dpms
xset s off
xset s noblank
```

everything works fine.

I've tried to set a
```
sleep 10 && xset -dpms && xset s off && xset s noblank
```
inside this Lubuntu autostart tool "LXSession Configuration", but still no luck.

Where can I put those commands to make sure that the screensaver (and in particular the noblank option) is properly set?

---

### Post by Tadaen_Sylvermane on 2018-09-28
I think the Lubuntu autostart tool is getting confused by the && in your syntax. You can do that with a single command. ```
xset s off s noblank -dpms
```. No reason for the sleep part imo. Try that?

Another idea is to ignore the Lubuntu autostart tool. I think Lubuntu uses Openbox. Put it in /home/"$USER"/.config/openbox/autostart. Here is mine for my Kodi box in living room.

```
kodi &
xset s 0 s blank -dpms &
```

---

