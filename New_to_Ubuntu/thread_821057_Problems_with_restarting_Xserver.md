---
title: "Problems with restarting Xserver"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by whitethorn on 2008-06-06
Hi,

When I try to restart my xserver using ctrl alt backspace, sometimes it'll work (usually right after a new boot).  If I leave my laptop on for a couple hours and try to restart my X, it'll go kill all the processes and then it stays stuck at some grey screen.  No matter what I try afterwards get's it to do anything.  I have to hard shut down and then boot up normally.  Is there some way to get this fixed?

---

### Post by spiderbatdad on 2008-06-06
This is potentially a bad thing to do...depending on your motherboard, I believe, you may be doing the same as ctrl-alt-del...which kills all the session processes without confirmation.

I would ask why are you always doing this?

---

### Post by whitethorn on 2008-06-06
I was restarting my Xserver, because I changed some settings in Pulse and I have to restart Pulseaudio to get them loaded (now that I think about it, there's probably another way of getting pulse started but I wouldn't know how)

---

### Post by spiderbatdad on 2008-06-06
I think this will work:```
sudo /etc/init.d/pulseaudio restart
```

---

### Post by whitethorn on 2008-06-07
I tried that and it didn't work.  The reason I restart pulseaudio is because I want it to use a different soundcard. So far the only way to get it to work is by restarting X.  I just found out that my computer also freezes in the same place if I try to log out. Seems like the only thing that works is when I tell it to restart (reboot).

---

### Post by T2manner on 2008-06-07
i have to restart my X Server when everything freezes and i can't restart the normal way.
there just is nothing else i know to do, and i don't want to hard boot.

---

