---
title: "Cannot get into gnome/unity"
date: 2011-09-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by davepoth on 2011-09-02
Upgraded, and left it to upgrade overnight. When I rebooted it broke a bit. Lots of stuff didn't install properly, so a few visits to the recovery console got that sorted.

However when I try to boot up now, it gets as far as the mouse pointer being displayed and moveable for a second or so and then it drops back to a sort of non-gui startup, except there's no prompt, almost as if unity is running in the background. The only thing that does anything is ctrl-alt-delete which causes a shutdown. Any ideas?

---

### Post by davepoth on 2011-09-02
Odd one. I told it to use GDM rather than LightDM, and when I ran LightDM it got into Unity, in a stupid resolution, and everything appears to be broken. I can't even switch back into gnome because lightDM appears to be borked somehow.

---

### Post by cariboo on 2011-09-02
Can you boot into recovery mode, and after you have logged in type:

```
sudo service lightdm start
```

If that works, all may need to do is reconfigure lightdb:

```
sudo dpkg --configure lightdm
```

---

