---
title: "very low apt-get speed even for update descriptor"
date: 2013-10-31
forum: New to Ubuntu
---

### Post by ignatov-msu on 2013-10-31
Hello! I have a problem in Ubuntu 13.10 wih apt-get - even updating information about packages can't be done in hours. Common speed is between 0,5kb/sec - 10kb/sec (so I download 500kb in 4-5 hours).  I can easily download files from web with good speed (in system monitor much more speed when i using browser). I already checked best destination for downloading packages and i don`t know what to do. It persist even if I chose usb-wifi adaptor instead of notebook wifi module. I can write more useful information if you tell me how to do it. Hoping for your help!

---

### Post by wildmanne39 on 2013-10-31
Hi, please run: 
```
gksu software-properties-gtk
```
then enter user password in the window that opens change the server until you get a better speed.
Thanks

---

### Post by ignatov-msu on 2013-10-31
Thanks for replying!
I did it before post here - i start script that found best server for me. And it didn't help me.

---

### Post by ignatov-msu on 2013-10-31
Also my noutbook is much warmer than when i use win7. Could it be that my slow apt-get speed is connected with wrong working cpu or smth else?

---

### Post by ikt on 2013-10-31
Have you tried different mirrors that are within your country?

---

### Post by DuckHook on 2013-10-31
Really need more info or clearer info before we can help. Are you downloading through WIFI or wired? If WIFI, how are typical downloads of other large files? Have you tested connection speeds downloading such a file through HTTP? FTP? You can also measure your connection speed from [here]("http://www.speedtest.net/").> **ignatov-msu said:**
> ...i start script that found best server for me.Please specify what script this is. Are you referring to the "Find fastest server" button in software properties, or are you referring to the:```
deb mirror://mirrors.ubuntu.com/mirrors.txt...
```method that you append to sources.list? Or is it another script altogether?

Please deal with the heat issue by starting a separate thread.

---

### Post by merlyn2748 on 2013-10-31
Apt-fast might help as well.  It allows for multiple concurrent connections when using apt.  You can check it out at:  [https://code.launchpad.net/~apt-fast/+archive/stable](https://code.launchpad.net/~apt-fast/+archive/stable)

---

