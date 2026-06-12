---
title: "A command to list installed hand-rolled programs."
date: 2012-05-18
forum: Programming Talk
---

### Post by ron999 on 2012-05-18
This is my attempt.:cool:


Patches are welcome.
:lolflag:

```
echo "Package                               Version" > packages.txt && \
echo "-------                               -------" >> packages.txt && \
dpkg -l | grep -i 'Package created with checkinstall' | cut -c 5- | sed 's/-1//' \
| sed 's/Package created with checkinstall 1.6.*//' >> packages.txt
```

---

### Post by rai4shu2 on 2012-05-18
Wow. VLC from source must have been fun.

That script doesn't work on my system since I like to use the proper descriptions. I just go into Synaptic and select "Origin" and then "Local" if I want to see a list of stuff I've installed locally.

---

### Post by ron999 on 2012-05-18
> **rai4shu2 said:**
> That script doesn't work on my system since I like to use the proper descriptions.
Ha, fortunately Checkinstall leaves it's message when the description field is left blank.;)

I started off trying to make dpkg list programs from Status > Installed Local.
And your suggestion Origin > Local is a similar idea.
But it defeated me.:(

Are you working on it now?:smile:

---

### Post by rai4shu2 on 2012-05-18
I'm not working at all right now. But if I were to do something like what you're trying to do, I'd look into maybe using xapian-tools or something like that.

---

### Post by ron999 on 2012-05-19
Hi

It seems the data is in file **var/lib/dpkg/status**
And also in file var/lib/dpkg/available

Is it possible to access the data to list package name and version
something like this....
cat /var/lib/dpkg/status | ......


The hand-rolled programs show "Section: checkinstall"
Like this:-



> Package: vlc
Status: install ok installed
Priority: extra
Section: checkinstall
Installed-Size: 59732
Maintainer: root@ubuntu
Architecture: i386
Version: 2.1.0+git20120406-1
Provides: vlc
Description: Package created with checkinstall 1.6.1

---

### Post by Bachstelze on 2012-05-19
Checkinstall is for _wimps_.

---

