---
title: "flashable USB not visible after restart."
date: 2015-05-20
forum: New to Ubuntu
---

### Post by Ahmed_Faiz on 2015-05-20
Hello,

Yesterday I decided to install Ubuntu on my white macbook mid 2010 13inch. I downloaded and converted the iso file to IMG and made a flashable USB with terminal as instruction in the site. All went well .but after I restart and press option I can't see the flashable Ubuntu USB! 

Need help I am running the latest osx Yosemite

---

### Post by newb85 on 2015-05-20
I'm afraid I can't be any help, but I suspect this question will be answered more quickly if you make the title reflect your hardware situation.  I know apple hardware presents unique issues.  It is probably better suited for the Apple Hardware Users forum, but it's best to let a moderator move this thread, rather than double-posting.

---

### Post by cariboo on 2015-05-22
I recycled all my  Macs last year when I moved, so I can;t check, but if there isn't a gui program to create a bootable usb device from an iso image, then you can always open a terminal and use dd:

```
sudo dd if=vivid-desktop-amd64.iso  of=/dev/sdc bs=1M
```

where if= the name of your iso file and of= the name of your usb device

---

