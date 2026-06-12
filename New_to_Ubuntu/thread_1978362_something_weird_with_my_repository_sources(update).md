---
title: "something weird with my repository sources(update)"
date: 2012-05-11
forum: New to Ubuntu
---

### Post by werty2010 on 2012-05-11
i ran "sudo apt-get update" today and i think i have duplicate repos(both i386 and  amd64) for example running the command will give me among others this:
```

...
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages   
...
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages 
...

```

im not sure if this is normal...?
if not is there a way to fix it?

---

### Post by cariboo on 2012-05-11
That's normal, if you have 'foreign-architecture i386' in /etc/dpkg/dpkg.cfg.d/multiarch, to get rid of the the i386 repositories, just comment out the line like this:

 ```
#foreign-architecture i386'
```

To edit the file just type:

```
gksu gedit /etc/dpkg/dpkg.cfg.d/multiarch
```

---

