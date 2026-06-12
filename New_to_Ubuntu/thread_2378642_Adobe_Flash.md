---
title: "Adobe Flash"
date: 2017-11-25
forum: New to Ubuntu
---

### Post by lobsters152 on 2017-11-25
I am hoping to return to Ubuntu after getting fed up with Windows 10. I am presently experimenting with the latest Ubuntu 18 live from a usb stick which has 1Gb of persistence. It boots quickly and I am enjoying it however I need Adobe Flash. What do I do to get Adobe Flash?

---

### Post by vasa1 on 2017-11-25
What about installing Google Chrome? It has Flash built-in.

---

### Post by again? on 2017-11-25
Don't use alpha releases or firefox but unless something has changed,
you just need to enable the [partner repo]("https://help.ubuntu.com/stable/ubuntu-help/addremove-sources.html#canonical-partner"), and
```
sudo apt update
sudo apt install adobe-flashplugin
```
Why would you run an alpha release on a persistent usb???
Seems like a quick way to kill the usb.

---

### Post by Jack Waugh on 2017-12-17
[deleted]

---

### Post by faraco2 on 2017-12-19
If you use Firefox, then you can also install Adobe Flash (might be not the latest) from Ubuntu repository without taking any other extra steps.

Here is the package you'll need.

```
sudo apt install flashplugin-installer
```

After the installation is done, launch your Firefox browser and try to see if executing a flash based web application is working.

---

