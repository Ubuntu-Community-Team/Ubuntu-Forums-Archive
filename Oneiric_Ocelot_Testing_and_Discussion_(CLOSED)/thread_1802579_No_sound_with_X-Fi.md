---
title: "No sound with X-Fi"
date: 2011-07-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rv65 on 2011-07-12
I updated my Ubuntu 11.10 installation to the latest update, and all of a sudden my sound went away. I have an X-fi card, and it was working before the update. There must be some issue with Pulseaudio or something like that. Any response would be great.

---

### Post by jfernyhough on 2011-07-12
Run alsamixer and check your levels. I have to increase the levels of my internal speakers every boot (which has been a common theme with early dev versions for me for several releases).

I could probably find a way to fix it but every time I'm reminded about the problem is when I want to watch or listen to something; once it's finished I've forgotten about it. :)

---

### Post by cariboo on 2011-07-12
@jfernyhough, doesn't running:

```
sudo alsactl store
```

save alsamixer settings after you exit?

---

### Post by jfernyhough on 2011-07-12
That may well be the command I half-remembered but never got around to finding again - thanks!

---

### Post by P-I H on 2011-07-12
My sound also disappeared after yesterday's updates. Alsamixer did not start. It was related to the udev problem, so sudo mv /run/udev /run/udev.old fixed the problem.

---

### Post by terabit8 on 2011-09-30
I have sound with my x-fi fatal1ty card on a fresh install of 11.10 beta 2 with the exception of the center and subwoofer.

Center/L is maxed out in alsamixer.

@X-fi owners here: Have u done the upgrade or a fresh install of beta 2 already and what are the results?
Thank you.

---

### Post by flipper T on 2011-09-30
i use the xfi-go usb sound card.

works fine

---

