---
title: "Different desktops when switching from Unity to GNOME"
date: 2017-10-29
forum: New to Ubuntu
---

### Post by yliu1 on 2017-10-29
Hi,

I am new to using Linux and just started using the GNOME desktop environment. However, I've noticed that files that I have on the desktop in Unity does not appear in GNOME...

Can someone explain why this occurs? Would you just suggest to save all my files to the home folder or is there a way to have both Unity and GNOME desktops 'synced'?

Thanks!

---

### Post by Buntu Bunny on 2017-11-02
Hi yliu1, welcome to the forums! Do you have them on the same partition?

---

### Post by again? on 2017-11-03
If you mean the same install when you log into different sessions,
the Gnome session doesn't show desktop icons by default.
To show desktop icons in gnome-shell, run this terminal command.
```
dconf write /org/gnome/desktop/background/show-desktop-icons true
```

---

