---
title: "Speed up performance with 'preload'"
date: 2008-03-28
forum: Outdated Tutorials &amp; Tips
---

### Post by cisforcojo on 2008-03-28
I just ran across this program and thought I'd share it with everyone. 
It's absolutely fantastic. [http://www.techthrob.com/tech/preload.php](http://www.techthrob.com/tech/preload.php)

> Preload is an "adaptive readahead daemon" that runs in the background of your system, and observes what programs you use most often, caching them in order to speed up application load time. By using Preload, you can put unused RAM to good work, and improve the overall performance of your desktop system. 

```
sudo apt-get install preload
```

Enjoy!

---

### Post by 3rdalbum on 2008-03-29
I tried it on Dapper. It did slightly speed up the launching of applications, but the startup time of the whole operating systems increased a fair bit; not sure if Preload was causing / affected-by disk fragmentation, or if it was preloading things while the rest of the system was loading.

I was scared that if I uninstalled it, that my system would become unbootable, so I lived with it. I might give it another go now as I've got about 1.5 gigabytes of RAM that's never had data stored in it, apart from Memtest86 :-)

---

### Post by wPwLUi3N on 2008-03-29
I will give it a try too.

---

### Post by luckylin on 2008-03-29
Thanks, I'll give it a try

---

### Post by ellalan on 2008-03-30
Thank you cisforcojo, it made a difference.

---

### Post by cisforcojo on 2008-03-30
Glad to help!

---

