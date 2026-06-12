---
title: "[SOLVED] google earth login error"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by DNK on 2008-08-13
I've uninstalled and reinstalled google earth from synaptic. It still appears to not be able to login to its servers. I have my firewall set to permissive. Thank you!

---

### Post by vikramaditya on 2008-08-13
I installed it from terminal last night using...
```
sudo apt-get install googleearth
```
At first, a bunch of stuff came up saying it couldn't connect to the IP address, ending with the suggestion to try "update".  So, I typed...
```
sudo apt-get update
```
...and Voilà, Google Earth is now hungrily consuming my resources!  I guess the repository has moved and the update command sorted things out?

**Edit:**  BTW, it's logging into the server just fine.

---

### Post by cariboo on 2008-08-13
Delete the .googleearth directory in your home folder. It is a hidden file so to see it in Nautilus, open Places-->Home Folder and hit Ctrl-h. The folder will be recreated when you start googleearth.

Jim

---

### Post by DNK on 2008-08-14
Still can't login. Checked for updates. Only stars visible. Not in sky mode. Thank you.

---

### Post by DNK on 2008-08-14
Google Earth works fine with sudo. If that helps.

---

### Post by DNK on 2008-08-18
Please help!

---

### Post by DNK on 2008-08-21
Fixed  courtesy of overdrank
 
overdrank's Avatar

-AR
HI and you can right click on the applications and choose edit menus. Then locate the google earth right click and right click select properties and add gksu at the command line. It may be just a patch but it works for me.

---

