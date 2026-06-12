---
title: "Hard Disk Suspicion"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by adewale on 2008-08-24
Hi,
This morning i booted up ubuntu and got the usual message that hard disk has been mounted over 27 times need to check. It does this normally without issues. But today there was a problem. After it finished i noticed a strange noise coming from the hard disk and its really making me feel uncomfortable. Also i noticed hard disk tuning started as the last service before gdm. I also restarted but that sound doesn't stop. This is the second disk am buying. 
Thanks

---

### Post by tamoneya on 2008-08-24
install a smart tools monitor:
```
sudo apt-get install smart-notifier
```

---

### Post by adewale on 2008-08-24
i just installed smart-notifier and so far i haven't been able to get it running. I tried it from the command line and after i cancel it (cause its not showing anything), it gives this error.
~$ smart-notifier --help
Traceback (most recent call last):
  File "/usr/bin/smart-notifier", line 17, in <module>
    smart_notifier.gui.service()
  File "/usr/share/smart-notifier/smart_notifier/gui.py", line 52, in service
    gtk.main()
KeyboardInterrupt
 PS I use KDE

Thanks

---

### Post by tamoneya on 2008-08-24
I think you need a restart first.

---

