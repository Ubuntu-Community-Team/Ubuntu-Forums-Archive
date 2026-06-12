---
title: "How to make Ubuntu faster?"
date: 2011-09-16
forum: New to Ubuntu
---

### Post by sakibmoon on 2011-09-16
When I used Windows, I tried things like defragment, cleaning registry, dumping history files. It cleared a lot of space and Pc worked better.

Ubuntu runs faster on my PC. I am glad about that as my Pc configuration is not very high, but I was wondering if there is anything that needs to be done to keep Ubuntu faster. Like clearing old history files or temporary files or anything. Anything that could be done.

---

### Post by wildmanne39 on 2011-09-16
Hi, ubuntu does not get fragmented like windows, so you do not need to defrag. 

You can install bleachbit from the software center and clean up unused files but be careful sometimes it wants to remove packages that are still being used.

I personally would never use computer janitor for that very reason.
Thank you

---

### Post by Elfy on 2011-09-16
In the 6 to 9 months I have between versions or OS's I don't find any slowdown at all. 

I don't bother doing anything like that - all personal preference I suspect :)

---

### Post by 3rdalbum on 2011-09-16
Meh, there's nothing you need to do. If you are low on disk space you might want to 'sudo rm /var/cache/apt/archives/*' every now and then - it removes all the cached package files that you have downloaded for new software or for updates. Once they've been installed you don't really need them for anything.

Other than that, just enjoy the fact that your computer is not making more work for you!

---

### Post by wildmanne39 on 2011-09-16
Hi forestpiskie, good to see you back as staff.

---

### Post by sakibmoon on 2011-09-16
Thanks guys. Good to know that I don't need to do anything.

---

### Post by Megaptera on 2011-09-16
> **wildmanne39 said:**
> hi forestpiskie, good to see you back as staff.

+ 1 !!

---

### Post by bookcrazy on 2011-09-17
You could always install ubuntu tweak to clean your cache and other things but, like everyone else said, it's up to you.

---

### Post by sakibmoon on 2011-09-17
How can I install ubuntu tweak?

---

### Post by Megaptera on 2011-09-17
One method [http://blog.ubuntu-tweak.com/downloads](http://blog.ubuntu-tweak.com/downloads)

---

### Post by Elfy on 2011-09-17
```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```

[http://www.ubuntugeek.com/ubuntu-tweak-0-5-10-released-with-autohide-option-for-unity-launcher.html](http://www.ubuntugeek.com/ubuntu-tweak-0-5-10-released-with-autohide-option-for-unity-launcher.html)

You'll find more or less most of the basic tasks well represented by most search engines :)

I use these 2 for ubuntu

[http://www.googlubuntu.com/](http://www.googlubuntu.com/)
[http://crunchbang.org/ubuntu-search-engine/](http://crunchbang.org/ubuntu-search-engine/)

---

