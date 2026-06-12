---
title: "upgrading from 11.10 to 12.04"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by pfwalter on 2012-04-26
Hello,

   Another functioning beginner, with a question !
   Ubuntu 11.10 is currently installed on my desktop.  It was accomplished with the usage of WUBI in a Windows Vista environment and of course dual boot is process to WIN/UBUNTU.  When 12.04 LTS becomes available(actually, today), what should the upgrade process be?  I assume WUBI would not be the way to proceed with an installation process?
  
   Should I uninstall WUBI first ? and Create a 12.04 ISO disc

   Install 12.04 via UPDATE MANAGER ? 
              or 
   Create an 12.04 ISO disc?  
    
   Keeping in mind A) a backup is done B) third party drivers are uninstalled C) etc.

Thank You for your patience,
Philip Walter

---

### Post by M!K3_$ on 2012-04-26
This will do it for you when the time comes. This shouldn't bork your dual boot setup - maybe somebody can verify that for me...


```
sudo do-release-upgrade
```

---

### Post by pfwalter on 2012-04-26
Thank You Sir,

Philip Walter

---

### Post by bcbc on 2012-04-26
I wrote up something on this: [http://ubuntu-with-wubi.blogspot.ca/2012/04/how-to-upgrade-wubi-install.html](http://ubuntu-with-wubi.blogspot.ca/2012/04/how-to-upgrade-wubi-install.html)

---

### Post by M!K3_$ on 2012-04-26
I believe the graphical package manager also notifies you of a new release.

And I am fairly certain that your dual boot setup will be fine (again, you should do some 'googling' to verify).

---

### Post by M!K3_$ on 2012-04-26
> **bcbc said:**
> I wrote up something on this: [http://ubuntu-with-wubi.blogspot.ca/2012/04/how-to-upgrade-wubi-install.html](http://ubuntu-with-wubi.blogspot.ca/2012/04/how-to-upgrade-wubi-install.html)

Perfect!

---

