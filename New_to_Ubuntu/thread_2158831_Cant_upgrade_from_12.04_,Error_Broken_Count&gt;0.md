---
title: "Cant upgrade from 12.04 ,Error Broken Count&gt;0"
date: 2013-06-30
forum: New to Ubuntu
---

### Post by ro12 on 2013-06-30
Hi I have a problem,I cant update or fix broken dependencies in Synamptic . How can I use the commands from apt-get? 

Thanks if you can help.

---

### Post by newb85 on 2013-06-30
Have you attempted
```
sudo apt-get -f install
```

---

### Post by ro12 on 2013-07-01
When I try ```
 [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get -f install[/FONT][/COLOR]   
```
I get this```
  dpkg: error: parsing file '/var/lib/dpkg/status' near line 27728 package 'rar': mixed non-coinstallable and coinstallable package instances present
E: Sub-process /usr/bin/dpkg returned an error code (2)        
```

---

