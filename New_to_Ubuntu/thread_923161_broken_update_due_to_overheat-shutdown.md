---
title: "broken update due to overheat-shutdown"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by tcoffeep on 2008-09-18
Hello all.
It's been quite awhile since I last had a computer, and finally, I got my hands on one. However, it's a Dell Inspiron 5150, used, and it seems to enjoy overheating. :(
I just finished downloading the ~200 updates and was about 3/4 into installing them when suddenly, it began to freeze up, and then blinked out.
I let it cool down for a few minutes, and restarted. Now, it won't allow me to get back into the Ubuntu GUI. It loops in between the login screen and the desktop, but won't show the desktop.

I assume this is related to the overheating + update, but I might be wrong. Does anyone know how I might be able to find out?

---

### Post by iaculallad on 2008-09-18
Try to boot using recovery mode and input the following commands:
```

sudo apt-get install -f
sudo dpkg --configure -a
sudo xfix
```

and try rebooting:

```
sudo shutdown -r now
```

---

### Post by tcoffeep on 2008-09-20
> **iaculallad said:**
> Try to boot using recovery mode and input the following commands:
```

sudo apt-get install -f
sudo dpkg --configure -a
sudo xfix
```

and try rebooting:

```
sudo shutdown -r now
```

Thanks, that worked. Well, it *mostly* worked, as typing sudo xfix did nothing at all, but tell me there's no such thing as xfix. :confused:

---

