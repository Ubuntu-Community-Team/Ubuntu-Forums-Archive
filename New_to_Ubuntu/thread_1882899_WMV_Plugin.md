---
title: "WMV Plugin"
date: 2011-11-18
forum: New to Ubuntu
---

### Post by Cubanicous on 2011-11-18
The WMV plugin is not working in Chrome or Firefox in Ubuntu 10.11. It is says it is missing the plugin, but the plugin is downloaded when I look at the list of all the plugins in Chrome

---

### Post by ajgreeny on 2011-11-18
Have you installed all the codecs you need for wmv files and all the other restricted formats?
```
sudo apt-get install ubuntu-restricted-extras
``` should do it for you.

---

### Post by Cubanicous on 2011-11-18
Entered the command in the terminal and restarted the computer and the wmv plugin is still not working

---

### Post by SeijiSensei on 2011-11-18
Try removing the WMV plugin then installing the gecko-mediaplayer package instead ("sudo apt-get install gecko-mediaplayer").

---

