---
title: "Volume notification on screen"
date: 2018-04-13
forum: New to Ubuntu
---

### Post by everknight on 2018-04-13
Hello, I recently moved to lubuntu in an old laptop.

I  am having issues with the on screen widget notification that should pop up whenever I change the volume using the keyboard, sometimes it does work, sometimes it stops working out of the blue.
I have installed xfce4-notifyd, xcfe4-volumed.   The xfce volume daemon option is set ON on notifyd. When I change the volume with the terminal code, namely

```
notify-send -i audio-volume-medium -h int:value:100 text
```

the volume notification does pop up

Any idea what is doing the notification not to pop up sometimes?

---

