---
title: "Unable to location libmysqlclient Ubuntu 12.10"
date: 2013-04-08
forum: Repositories &amp; Backports
---

### Post by GMScribe on 2013-04-08
Hi guys,

I'm attempting to compile the latest version of Wt (witty) and require the mysqlclient library. I've apt-get installed mysql-client and libmysqlclient-dev however, am unable to locate any related libmysql library files that I'm expecting to find within /usr/lib/.

Would someone be able to confirm what libraries I should expect to be seeing and if there's any reason why they're not showing up?

Many thanks

---

### Post by schragge on 2013-04-09
Try
```

dpkg -L mysql-client libmysqlclient-dev|grep '[COLOR=blue]file_you_are_looking_for[/COLOR]'

```
Most probably, the libraries are under ```
/usr/lib/`dpkg-architecture -qDEB_BUILD_GNU_TYPE`
```

---

