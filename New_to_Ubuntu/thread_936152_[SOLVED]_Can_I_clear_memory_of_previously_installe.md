---
title: "[SOLVED] Can I clear memory of previously installed printers?"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by kansasnoob on 2008-10-02
I quite often use my desktop for testing. I've purchased many printers for other folks and I always try them on my machine before taking them and installing them on the users machine .......... so under both Pref > Default Printer & Admin > Printing I have a couple dozen entries!!!!!!!!!! It's a cluttered mess!

Is there some way I can clear all the old printer/driver info?

---

### Post by whizbaby on 2008-10-02
The things you can do are:
-remove the old stuff in the CUPS webinterface (if you can find it there). Open your favourite browser and put
```
localhost:631
```
into the address bar and hit return.
-remove the 'stuff' directly. The ppd files generated are in the directory
```
/etc/cups/ppd/
```
(delete unused files)
and the printer entries in the file
```
/etc/cups/printers.conf
```
(remove unused sections).
finally do a
```
sudo /etc/init.d/cupsys restart
```

If old stuff still is showing up it must be the fault of your window managers print service, which wm are you using?

---

### Post by kansasnoob on 2008-10-02
Thanks a million friend! That got it!

---

