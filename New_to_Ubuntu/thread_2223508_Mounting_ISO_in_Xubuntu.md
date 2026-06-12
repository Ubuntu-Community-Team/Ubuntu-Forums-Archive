---
title: "Mounting ISO in Xubuntu"
date: 2014-05-11
forum: New to Ubuntu
---

### Post by jmeeter on 2014-05-11
I know in Ubuntu there is Startup Disk Creator which will easily allow you to create a bootable USB drive (Say for instance I wanted to test drive another Linux distro)... I am wondering if SDC can be installed in Xubuntu through the software center? Also if someone could link me to a beginner's tutorial for using the command line (mounting an ISO to USB) I wouldn't mind getting my hands dirty...

---

### Post by Vladlenin5000 on 2014-05-11
Unebootin or even a more complex solution like multisystem should do it if you can't use the default software. 
Obs.: Startup Disk Creator was included in Xubuntu at least until 13.10.

---

### Post by matt_symes on 2014-05-11
Hi

> **jmeeter said:**
> I know in Ubuntu there is Startup Disk Creator which will easily allow you to create a bootable USB drive (Say for instance I wanted to test drive another Linux distro)... I am wondering if SDC can be installed in Xubuntu through the software center? 

Look for usb-creator-gtk in the software center or install from the terminal using

```
sudo apt-get install usb-creator-gtk
```

> Also if someone could link me to a beginner's tutorial for using the command line (mounting an ISO to USB) I wouldn't mind getting my hands dirty...

Not 100% sure what you mean here. You can mount an ISO or a USB pen drive but you don't mount an ISO to USB.

If you're asking about how to create a bootable USB pen drive with an ISO copied onto it, you're better off using a GUI application like usb-creator-gtk.

It can be done with programs like dd but there is at least one poster on the forums today who has managed to write the ISO to their hard drive and not their USB by mistake. Ths has made their hard drive currently unbootable.

Kind regards

---

### Post by LastDino on 2014-05-11
Once you're used to GUI tool try using DD sometime in future. It is the best even though it's command. :p 

[http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

---

### Post by jmeeter on 2014-05-11
> **Vladlenin5000 said:**
> Unebootin or even a more complex solution like multisystem should do it if you can't use the default software. 
Obs.: Startup Disk Creator was included in Xubuntu at least until 13.10.



Thank you!

@matt_symes - I'll heed your advice. :)

---

