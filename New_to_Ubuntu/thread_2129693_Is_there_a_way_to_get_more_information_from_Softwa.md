---
title: "Is there a way to get more information from Software Updater?"
date: 2013-03-27
forum: New to Ubuntu
---

### Post by Ziski on 2013-03-27
I clicked "details" but it doesn't show me much. I want to be shown the download speed, download remaining, total downloaded, etc... I've just installed Ubuntu and am downloading the updates through Software Updater. I haven't used Linux since Ubuntu switched from Gnome 2 and I was never very knowledgeable in the first place, but I remember Software Updater used to show a lot of these details. Is there any way to enable them?

Thanks,

Ziski

---

### Post by LuisGMarine on 2013-03-27
I'm not entirely positive that you can squeeze any more information other than the options that it gives on the window.  

Have you tried updating the system from a terminal?  I feel like that has a lot more information presented, as oppose to clicking 'details' in the software updater.  

In case you don't recall, you can update your system with the following two commands:

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Ziski on 2013-03-27
That's right! Thank you! I knew it was apt-something... Cheers.

---

### Post by deadflowr on 2013-03-27
The details just gives the package size and any information available on what the update package does.
Running through the terminal gives a better idea of what speeds are going on at what time.

---

### Post by mike555 on 2013-03-27
If you install and use Synaptic Package Manager when you check things to install , it shows everything it will install ... good way to avoid KDE stuff if you want to.......

---

