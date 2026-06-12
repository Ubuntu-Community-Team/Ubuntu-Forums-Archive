---
title: "Problems with Update Manager and Mozilla"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by xrough on 2008-05-06
I have just upgraded to 8.04 Ubuntu. There seems to be a problem with the Update Manager. After clicking on Install Updates it freezes.

I also have problems with Mozilla firefox - Beta.

Wonder if any one has figured the solution.

---

### Post by Oldsoldier2003 on 2008-05-06
> **xrough said:**
> I have just upgraded to 8.04 Ubuntu. There seems to be a problem with the Update Manager. After clicking on Install Updates it freezes.

I also have problems with Mozilla firefox - Beta.

Wonder if any one has figured the solution.

post any error messages you get from:

```
sudo apt-get update
sudo apt-get upgrade
```

As for the Firefox issues? what are they... 

Usually you get better results if you separate your issues into different threads, don't take that as a criticism just a helpful suggestion to get you your needed help as fast as possible.

---

### Post by Thingymebob on 2008-05-06
Loads of known problems with FF - It is after all Beta. If its causing you real headaches revert to FF2

Update manager
open a terminal and type ```
sudo ls
```
if you get a message along the lines of
```
unable to resolve host *YourComputerName*
```

then you will need to edit your /etc/hosts
```
sudo gedit /etc/hosts
```
change the first two lines to read
```
127.0.0.1 localhost
127.0.1.1 *YourComputerName*

# The following lines are desirable for IPv6 capable hosts
....
```

This is a known bug and will cause gksudo to fail to start, hence update manager freezes.

you can read more about it here
[http://ubuntuforums.org/showthread.php?t=723361]("http://ubuntuforums.org/showthread.php?t=723361")
and here
[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906]("https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906")

---

### Post by xrough on 2008-05-09
Thanks the Update Manager works now.

---

