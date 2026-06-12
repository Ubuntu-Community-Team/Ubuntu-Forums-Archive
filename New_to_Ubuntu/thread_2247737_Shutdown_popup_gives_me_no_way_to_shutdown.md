---
title: "Shutdown popup gives me no way to shutdown"
date: 2014-10-09
forum: New to Ubuntu
---

### Post by dogfiresmith on 2014-10-09
Unbuntu 14.04  I select shutdown, and a popup window appears and says something like "Shut down, are you sure you would like to shut down?".  Nothing else.  No buttons, no drop-downs, no way to execute the shut down request.  I end up having to force shut down, by holding down the power key.  This is a problem because on reboot, when I want to go back to using Windows, it tells me the shut down was (bad), and suggests I start up in safe mode.

---

### Post by frncz on 2014-10-10
I had this problem too, but it solved itself after a few days and updating the system.

---

### Post by Doug S on 2014-10-10
I do not know what the problem with the GUI pop up thing is, but you can do a clean shutdown via the command line:```
sudo shutdown -h now
```or a restart:```
sudo shutdown -r now
```

---

### Post by Vladlenin5000 on 2014-10-10
An additional comment:

In a dual-boot scenario, Windows may complain about an incorrect Ubuntu shutdown if - and only if - it somehow messed with the Windows system partition, ie, if you had it mounted in Ubuntu and was reading/writing to it. Otherwise no, it can't happen.

---

