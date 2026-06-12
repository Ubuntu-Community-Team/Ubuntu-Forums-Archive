---
title: "trying to install apache"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by witash on 2008-05-05
I am trying to install apache, and i think i screwed it up. apache was installed a few months ago but i removed it. Now, when i try to install it again (using sudo apt-get install apache2) it tells me this-


Setting up apache2-mpm-worker (2.2.4-3ubuntu0.1) ...
grep: /etc/apache2/mods-enabled/*.load: No such file or directory
Module cgi does not exist!
This module does not exist!
It looks like you've deleted /etc/apache2/mods-available/cgid.load, so mod_cgid cannot be enabled.  To fix this, please purge and reinstall apache2.2-common.
 * Starting web server apache2                                                  apache2: Could not open configuration file /etc/apache2/apache2.conf: No such file or directory
                                                                         [fail]
invoke-rc.d: initscript apache2, action "start" failed.

Help?

---

### Post by Monicker on 2008-05-05
Did you remove it using Synaptic/apt-get, or by manually removing the apache directories?

---

### Post by lesergi on 2008-05-05
Hi!

Like the error message says to you, you must purge and reinstall apache2.

```
sudo apt-get remove --purge apache2 && sudo apt-get install apache2
```

Salut!

---

