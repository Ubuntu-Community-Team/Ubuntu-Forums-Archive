---
title: "[SOLVED] Xsession problem"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by Ddub on 2008-07-17
I tried to install FVWM-Crytsal and in the process modified my /etc/X11/Xsession file. Now I can only log in to console. I know what needs to be changed back but I can't use gedit to edit Xsession because it "can't open display". Does anyone know how to edit it from the console?

---

### Post by iaculallad on 2008-07-17
> **Ddub said:**
> I tried to install FVWM-Crytsal and in the process modified my /etc/X11/Xsession file. Now I can only log in to console. I know what needs to be changed back but I can't use gedit to edit Xsession because it "can't open display". Does anyone know how to edit it from the console?

Had you tried:

```
sudo vi /etc/X11/Xsession
```

or 

```
sudo nano /etc/X11/Xsession
```

---

### Post by seagullplayer77 on 2008-07-17
If you can't manage to get X back by editing the files from a terminal, I believe there's a feature on the alternate install disk that's called "X-Fix" or something along those lines. It'll reset X to the original settings, so if you've got a highly customized display, you'd probably want to do the X-Fix thing only as a last resort. I've done it a few times, and while it usually works, re-customizing my display is a pain.

---

### Post by Ddub on 2008-07-17
nano /etc/X11/Xsession worked. thanks.

---

### Post by Inxsible on 2008-07-17
> **Ddub said:**
> nano /etc/X11/Xsession worked. thanks.
Cool. Could you please mark the thread solved by going to Thread tools.

---

