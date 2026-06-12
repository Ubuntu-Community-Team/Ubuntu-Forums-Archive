---
title: "Mute on login"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by Rokurosv on 2008-11-16
When I login the volume control is on mute, and I have to unmute the master channel manually. It's not that much of an issue, I just wanted to know if there's a way to have like a default volume on startup?

Thanks for your time.

---

### Post by lovinglinux on 2008-11-16
Add the following code to System >>> Preferences >>> Sessions

```
amixer -q set "Master" 80% unmute
```

Replace the percentage with the value you want.

You can also do this for "Line In", "PCM" or other controls, replacing "Master" with the name of the control.

---

### Post by Rokurosv on 2008-11-16
Thanks I'll try it

---

### Post by supernova_hq on 2008-11-21
I know that you have a solution, but there is a proper way to do this.

Set all your volume settings to what you want, then run the following command:

```
sudo alsactl store
```

That will take the current settings and make them default at ever reboot.

Hope this helps.

---

