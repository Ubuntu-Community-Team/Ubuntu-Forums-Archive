---
title: "Not all available packages are shown in the Synaptic Package Manager?"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by Akhran on 2008-11-11
In Ubuntu 8.10, 'compizfusion-config-manager' is not found in the search results of the Synaptic Package Manager. However, in CLI it can be found with 'aptitude search compiz'. Is there some settings I need to tweak to display all available packages in Synaptic Package Manager?

Thanks!

---

### Post by Crafty Kisses on 2008-11-11
Paste this command in the terminal:
```
sudo apt-get update
```

---

### Post by Tatty on 2008-11-11
are you looking for: compizconfig-settings-manager  ?

---

### Post by m_l17 on 2008-11-12
This has happened to me in the past, if I would use quick search. The I would use the regular search it would come up, for whatever I was searching for.

Doing an update before doesn't hurt, click on reload or 

```
$ sudo apt-get update 
```

---

