---
title: "help plz, messed up desktop"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by deaddudehangin on 2008-06-13
Well, I was trying to get my wireless card up and running, then my cpu froze and the top and bottom bar things (the ones that have an appication, places, and modzilla bottens) disapeared! 
I tried rebooting but that didn't solve anything.
I'm really stumped on this.

Help is appreciated, btw I'm running xubutu 8.4.

---

### Post by wootah on 2008-06-13
Press: ALT-F2 then

```

gnome-panel
```

---

### Post by deaddudehangin on 2008-06-13
thanx for the quick respose, but when I do that i recieve an error saying 

failed to execute child process "gnome-panel"(no such file or directory?

---

### Post by Mentem on 2008-06-13
How new is your install, and how experienced user are you?

I just transferred to linux about a month or 2 ago, and since then, I've reinstalled ubuntu about 5 times due to similar troubles you are having. So if you are still a new user with only a few packages installed, may I just suggest a reinstall?

---

### Post by bumanie on 2008-06-13
> sudo dpkg --reconfigure xubuntu-desktop I think should work.

---

### Post by OffAxis on 2008-06-13
xubuntu uses **xfce4-panel** (ubuntu proper uses gnome-panel).

---

### Post by deaddudehangin on 2008-06-13
> **OffAxis said:**
> xubuntu uses **xfce4-panel** (ubuntu proper uses gnome-panel).

Thank You!
it worked I'm relieved that I don't have to reinstall it again :)

---

### Post by OffAxis on 2008-06-13
@ bumanie
I think you've got a typo there...
should be
```
sudo dpkg-reconfigure xubuntu-desktop
```

---

### Post by wootah on 2008-06-13
> **OffAxis said:**
> xubuntu uses **xfce4-panel** (ubuntu proper uses gnome-panel).

Dangit, just realized my mistake :)

OffAxis is correct, you want ALT-F2 then xfce4-panel

---

### Post by OffAxis on 2008-06-13
> it worked I'm relieved that I don't have to reinstall it again 
I'm glad it worked for you.

At most you probably would have just had to uninstall and reinstall the desktop (not the whole Operating System). So it would've been 

```
sudo apt-get remove xubuntu-desktop
sudo apt-get install xubuntu-desktop
```

but even having to do that is unlikely.

---

