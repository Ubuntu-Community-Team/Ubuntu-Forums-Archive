---
title: "How do you add Windows Wireless Drivers"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by jleach49 on 2008-11-12
Hi, how do you add windows wireless drivers option to the System-> Administration menu? Thanks :guitar::guitar:

---

### Post by jimmy the saint on 2008-11-12
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

This is the community guide to that very question!!

---

### Post by jleach49 on 2008-11-12
What I was asking is on my one Laptop when I click System-> Administrative menu at the bottom it has Windows Wireless Drivers. I click it to load a wireless driver. On this Laptop it doesn't have this option. Is there some way to enable it? It's easier for me to load the Linksys WUSB11v4 driver then going through the above process as you mention above. I never had luck running ndiswrapper. I am using Ubuntu 8.10. Thanks

---

### Post by jimmy the saint on 2008-11-12
As far I can tell, it seems that it is only loaded on machines that require a windows driver, similar to the restricted video card drivers.

---

### Post by jleach49 on 2008-11-12
Come to think of it I believe the other Laptop has a built-in wireless card. Boy that option sure works well for us newbies, especially loading tricky drivers. Maybe this option might become a standard. I rather learn the Linux way but sometimes it's a real pain just to get them to work. Thanks for your time and help.....Joe

---

### Post by coolbrook on 2008-11-12
```
sudo apt-get install ndisgtk
```

---

### Post by jleach49 on 2008-11-12
I'll ttry it thanks.

---

### Post by jleach49 on 2008-11-12
Hey that did the trick......THANKS

---

