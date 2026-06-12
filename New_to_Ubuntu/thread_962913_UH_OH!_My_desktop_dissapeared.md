---
title: "UH OH! My desktop dissapeared"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by psam3 on 2008-10-29
I installed startup manager and a new Usplash screen, but when I restarted to see it, it came back on without a desktop. The background image is gone and so are all of the icons, it's just a black screen. So I changed it back to the old one but that didn't make a difference. Anyone have any idea what happened? 

Thanks

---

### Post by Daveth on 2008-10-29
my guess is that you need to re-load it. Get to a terminal (control Alt F2) is you have no other way, then type

```
sudo /etc/init.d/gdm restart
```

assuming you are running a gnome desktop. You, of course, will have to put your password to that sudo command. Fairly innocuous if I have got completely the wrong end of the stick!

---

