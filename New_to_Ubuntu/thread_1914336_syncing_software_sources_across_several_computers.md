---
title: "syncing software sources across several computers"
date: 2012-01-24
forum: New to Ubuntu
---

### Post by farrinux on 2012-01-24
I have several computers setup with 11.10 on them and would like to have the same software sources on all.  I have one main computer setup with the sources I like.  Is there an easy way of getting the same sources on the other boxes without manually doing everyone. Is there a file I can copy from my main comp and move it to the others?

Thanks in advance.

---

### Post by Paqman on 2012-01-24
The file you want is /etc/apt/sources.list

---

### Post by farrinux on 2012-01-24
> **Paqman said:**
> The file you want is /etc/apt/sources.list

Paqman:
Just so I know the process, I would copy that file and then on the other comps open terminal and sudo to root and replace the file on each computer and then do an apt-get update.  Would this be correct?

---

### Post by Paqman on 2012-01-24
Spot on.

---

### Post by Cheesemill on 2012-01-24
If there are any files in the /etc/apt/sources.list.d/ directory you need to copy these as well.

---

### Post by philinux on 2012-01-24
> **farrinux said:**
> I have several computers setup with 11.10 on them and would like to have the same software sources on all.  I have one main computer setup with the sources I like.  Is there an easy way of getting the same sources on the other boxes without manually doing everyone. Is there a file I can copy from my main comp and move it to the others?

Thanks in advance.

You also might be interested in apt cacher.

[https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server)

[http://linuxexpresso.wordpress.com/2011/02/13/howto-apt-cacher-ng-on-ubuntu/](http://linuxexpresso.wordpress.com/2011/02/13/howto-apt-cacher-ng-on-ubuntu/)

---

### Post by mosaic2s on 2012-03-03
i will try this.

since every 14 days, I end up updating systems 8 times over and downloading some 100mb 8 times over. With 12.04 coming in, I am excited at using 64bit OS that will make use of 4gb RAM in the comp.

---

