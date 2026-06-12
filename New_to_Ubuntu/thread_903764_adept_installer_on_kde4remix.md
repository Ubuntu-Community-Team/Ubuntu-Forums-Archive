---
title: "adept installer on kde4remix?"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-08-28
it appears to be a bug with the installer but i cannot install anything every time it crashes. anyone knows anything by chance????

---

### Post by OffAxis on 2008-08-28
can you install programs from the command line with

```
sudo aptitude install <program name>
```

or

```
sudo apt-get install <program name>
```

you should get some better feedback if there's an error.

---

### Post by PatrickMoore on 2008-08-28
> **OffAxis said:**
> can you install programs from the command line with

```
sudo aptitude install <program name>
```

or

```
sudo apt-get install <program name>
```

you should get some better feedback if there's an error.

its hardware though. i was trying to install the broadcom drivers from the live disk

---

### Post by OffAxis on 2008-08-28
if you're running off your hard drive, and just have the liveCD referenced in adept (more precisely, in the **/etc/apt/sources.list** file) then it should look to your cd as the first place to install from.
If this is just a package with the driver, you can use dpkg to install

```
cd /folder/with/the/package
sudo dpkg -i packagename.deb
```

---

### Post by PatrickMoore on 2008-08-28
> **OffAxis said:**
> if you're running off your hard drive, and just have the liveCD referenced in adept (more precisely, in the **/etc/apt/sources.list** file) then it should look to your cd as the first place to install from.
If this is just a package with the driver, you can use dpkg to install

```
cd /folder/with/the/package
sudo dpkg -i packagename.deb
```

should i do that with m fwcutter package first?

---

### Post by OffAxis on 2008-08-28
Yes, that sounds right-I've never used or installed the fwcutter tool before, but it sounds good :)

---

