---
title: "blubuntu"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by Dark006 on 2008-06-10
Hey everyone, I was just wondering if anyone can tell me how to stop seeing this error in my terminal. For example, every time I open ~/.bashrc from my terminal (sudo gedit ~/.bashrc) it gives me this error, "/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored." Is there any way to get rid of this error?


Also, what are some good programs to use to copy/burn DVD's?

---

### Post by gr4nf on 2008-06-10
The error is rather foreign to me, but you could try a different text editor:
```
sudo nano ~/.bashrc
```

---

### Post by renfrew on 2008-06-10
You might try the following:

sudo cp /usr/share/themes/Blubuntu/gtk-2.0/gtkrc /usr/share/themes/Blubuntu/gtk-2.0/gtkrc.backup

sudo gedit usr/share/themes/Blubuntu/gtk-2.0/gtkrc
-goto/comment out line 169

if you are using gnome, try gnome-baker or brasero for DVD copying/burning.. 

nb. brasero doesn't work with dual-layer media, yet

---

### Post by ajgreeny on 2008-06-10
The best CD burning software is k3b.  Yes, I know it's a kde app, but it is sooo good that I can overlook the strange look of it on my gnome desktop.

---

### Post by Duck2006 on 2008-06-10
> **ajgreeny said:**
> The best CD burning software is k3b.  Yes, I know it's a kde app, but it is sooo good that I can overlook the strange look of it on my gnome desktop.

+1 on that one.

---

