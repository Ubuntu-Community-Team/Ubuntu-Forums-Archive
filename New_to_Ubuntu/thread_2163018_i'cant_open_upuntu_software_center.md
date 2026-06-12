---
title: "i'cant open upuntu software center"
date: 2013-07-16
forum: New to Ubuntu
---

### Post by mastercode on 2013-07-16
i'cant open "Ubuntu software centre" and I cant take shot screen from desk top  

and I&#8217;ve that Error in right top of desktop 

```
    An error occurred pleas run package Manager from the right click menu or apt_get in terminal to see what is wrong the error message was :'Error :Opening the cache (E:Type '>!DOCKTYPE is not known on line 1 in source list of sources .list.d/playonlinux.list E:The list of sources could not be read E:The package lists or stutus file could not be parsed or opened.
    this usually means that your installed packages have unmet dependencies   
```

   

now I&#8217;m trying to UN install play on Linux and that UN install take for ever o.O

---

### Post by dannyboy79 on 2013-07-16
try step 9 on this page: [https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)

---

### Post by mastercode on 2013-07-16
> **dannyboy79 said:**
> try step 9 on this page: [https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)

dosen't work for me  how i can re install upuntu ?? i have upuntu 13.04 dvd

---

### Post by oldos2er on 2013-07-17
Why reinstall? Open a terminal (Ctrl-Alt-t) and run ```
sudo rm /etc/apt/sources.list.d/playonlinux.list

sudo apt-get update
``` The error should be gone.

---

