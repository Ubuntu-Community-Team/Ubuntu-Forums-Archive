---
title: "Removing Wine"
date: 2014-04-16
forum: New to Ubuntu
---

### Post by bukhari2 on 2014-04-16
I removed wine but it is still showing in applications. How to remove completely?

---

### Post by jmbell on 2014-04-16
First, I recommend logging out and then logging back in again. If doing so fails to remove wine from your application list, try to reboot your system. If this fails too, try running ```
sudo apt-get remove wine
``` in a terminal. Maybe one of these will do the trick?

---

### Post by bukhari2 on 2014-04-16
well I did all these

---

### Post by jmbell on 2014-04-17
Sure, just covering all the basics first. Please post the output to this line if you haven't tried it already: ```
 dpkg --get-selections | grep -v deinstall | grep wine 
```
This will list all packages containing the string 'wine'. If any remain on your computer, delete them as well.

---

### Post by monkeybrain20122 on 2014-04-17
After removing wine some of the icons are in your home so they needed to be removed manually. Open the file browser, press ctrl+h or choose 'show hidden files' in the menu, then go to .local/share/applications and remove the wine folder and all .desktop files for wine applications. You may need to logout for this to take effect.

Also you may want to remove the folder .wine in your home since you don't need it anymore and in case you want to reinstallwine in the future you would want a clean slate.

**Edited:** I looked at the command you ran, It is possible that your package is not called 'wine'. Depending on how it was installed, it may be wine-1.7, wine-1.4 etc and it also installed other packages which sudo apt-get remove may not remove all of them (should have used apt-get autoremove). It is easy to do that with a gui, install synaptic and just search for all wine packages and remove them. Problem with the command line is you may get the name of the package wrong.
```
sudo apt-get install synaptic
```

---

### Post by bukhari2 on 2014-04-22
thank you jmbell  its done

---

