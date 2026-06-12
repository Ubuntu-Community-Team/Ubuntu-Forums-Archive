---
title: "VNC and/or NX with Unity 2D?"
date: 2011-09-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by MadNachos on 2011-09-08
I have a headless system that I sometimes need a GUI on that has been running Oneiric for a few days. Its working well but I cant seem to get Unity 2D to function with either VNC or with NX. I set ~/.dmrc to "Session=ubuntu-2d" but I end up with just the top bar on the desktop and no window manager or sidebar/launcher. Any thoughts on this?

---

### Post by cariboo on 2011-09-09
Do you actually need a full desktop, or just a gui application, if you only need a gui app, use X forwarding with ssh:

```
ssh -X user@server
```

Then type the name of the application at the prompt.

---

### Post by MadNachos on 2011-09-09
Thanks but that method does not really fit my requirements, I need a desktop that can be resumed from a few different clients hence vnc or NX.

---

