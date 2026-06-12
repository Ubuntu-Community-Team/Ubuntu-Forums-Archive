---
title: "gnome-shell-mousewheel-zoom not downloading from internet"
date: 2012-05-28
forum: New to Ubuntu
---

### Post by bubazoo on 2012-05-28
in the following article:
[http://www.upubuntu.com/2012/05/tool-to-magnify-screen-resolution-under.html](http://www.upubuntu.com/2012/05/tool-to-magnify-screen-resolution-under.html)

```

sudo add-apt-repository ppa:tobias-quinn/gsmz
sudo apt-get update
sudo apt-get install gnome-shell-mousewheel-zoom

```

trying to issue to add repository

```

add-apt-repository ppa:tobias-quinn/gsmz

```

I keep getting an error attempting to goto a website, so the repository doesn't get added, so issuing gnome-shell-mousewheel-zoom  keeps saying file not found.

Is anyone else getting this same problem?  and how can I fix this?  I have tried several times, on different days, and it still keeps saying it can't find an internet website in that repository. anyone else getting this too? or is it just me?

why would they post that if the repository server is down?

otherwise how do I install this gnome-shell-mousewheel-zoom manually since obviously the sever this repository is on is down or something. is it available somewhere else?   please help

---

### Post by Senior_Buckethead on 2012-05-28
ok when you run 
```

sudo apt-get update

```
You dont get a 404 (not found) error for the repository you have just added?

---

