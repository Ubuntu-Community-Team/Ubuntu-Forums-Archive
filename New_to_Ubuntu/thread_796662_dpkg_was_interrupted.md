---
title: "dpkg was interrupted"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by DhzeyR on 2008-05-16
Hi Peeps!

I need help! I keep on getting the error:

E: dpkg was interrupted, you must manually run dpkg --configure -a to correct the problem when I try to install plugins and when I open the Synaptics Package Manager.

after running the command, I get the result that says:

   Setting up Flashplugin-nonfree (9.0.124.0ubuntu2) ...
   Downloading...
   ---04:00:19-- [http://.](http://.)..
   ...
   ...
   ok

the Update Manager window will then appear saying that the system is up-to-date.

I still get the same message when I try to either install the plugins or open the Package Manager Window. 

Another version of the error is:

E: dpkg was interrupted. you must run 'dpkg --configure -2' to 
   correct the problem.
E: _cache->open() failed, please report.

---

### Post by macaholic on 2008-05-16
What happens when you try to install it from terminal with```
sudo apt-get install flashplugin-nonfree
```

---

### Post by bodhi.zazen on 2008-05-16
update manager locked up on me yesterday like this (after updating). My system required a re-boot (kernel update) -> problem solved after re-booting.

HTH

---

