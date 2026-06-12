---
title: "Stream Music to PC"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by mbt12 on 2008-05-07
Hi, I was just wondering if there is a simple way that I can stream music from my ubuntu laptop (which I do not use) to my PC.  I want to be able to free up the hard drive space my music uses.  Is there a step by step guide on how to do this?

---

### Post by quelx on 2008-05-07
Try mt-daapd.  It is in the universe repository.

from the terminal
```
sudo apt-get install mt-daapd
```

edit the config file

```
sudo nano -w /etc/mt-daapd.conf
```

change **admin_pw** and **mp3_dir** to suit your needs

add it to startup

```
sudo update-rc.d avahi-daemon defaults
```

start it without rebooting

```
sudo /etc/init.d/mt-daapd start
```

It will take a bit yo scan your music you can see it's progress and make playlists and such from **[http://localhost:3689](http://localhost:3689)** (change localhost to your laptops ip if using another computer.

---

