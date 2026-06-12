---
title: "apt-cacher woes"
date: 2006-06-01
forum: Repositories &amp; Backports
---

### Post by psyke83 on 2006-06-01
Hi,

I've been a user of Dapper since flight 1, and I have always used apt-cacher to keep a local repository for updating multiple computers. Today I did a fresh reinstall of Dapper, and installed apt-cacher, configured the daemon to start, and modified my sources.list as per usual (192.168.1.2:3142). When I try apt-get update, I get output like this:

```
conn@dimension:~$ sudo apt-get update
Ign [http://192.168.1.2](http://192.168.1.2) dapper Release.gpg
Ign [http://192.168.1.2](http://192.168.1.2) dapper-updates Release.gpg
Ign [http://192.168.1.2](http://192.168.1.2) dapper-backports Release.gpg
Ign [http://192.168.1.2](http://192.168.1.2) dapper-security Release.gpg
...
Err [http://192.168.1.2](http://192.168.1.2) dapper/main Packages
  500 (Internal Server Error) Can't connect to http::80 (Bad hostname 'http:')
Err [http://192.168.1.2](http://192.168.1.2) dapper/restricted Packages
  500 (Internal Server Error) Can't connect to http::80 (Bad hostname 'http:')
Err [http://192.168.1.2](http://192.168.1.2) dapper/main Sources
  500 (Internal Server Error) Can't connect to http::80 (Bad hostname 'http:')
Err [http://192.168.1.2](http://192.168.1.2) dapper/restricted Sources
  500 (Internal Server Error) Can't connect to http::80 (Bad hostname 'http:')
Err [http://192.168.1.2](http://192.168.1.2) dapper/universe Packages
...
```What's wrong? When I visit 192.168.1.2:3142 in firefox, I'm greeted with the apt-cacher page, so the daemon is running. Here's the contents of /var/log/apt-cacher/error.log:
```

Thu Jun  1 20:07:16 2006|127.0.1.1|--- /usr/sbin/apt-cacher: Usage error
Thu Jun  1 20:07:17 2006|127.0.1.1|--- /usr/sbin/apt-cacher: Usage error
Thu Jun  1 20:45:52 2006|127.0.0.1|--- /usr/sbin/apt-cacher: Usage error
Thu Jun  1 20:45:53 2006|127.0.0.1|--- /usr/sbin/apt-cacher: Usage error
Thu Jun  1 20:47:53 2006|127.0.0.1|--- /usr/sbin/apt-cacher: Usage error
Thu Jun  1 21:01:06 2006|192.168.1.2|--- /usr/sbin/apt-cacher: Usage error
Thu Jun  1 21:01:07 2006|192.168.1.2|--- /usr/sbin/apt-cacher: Usage error
```
(The previous entries are from when I tried "localhost:3142" with no improvement).

Sources.list sample:```
deb http://192.168.1.2:3142/ie.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://192.168.1.2:3142/ie.archive.ubuntu.com/ubuntu/ dapper main restricted
```
Any ideas?

---

### Post by hysterio on 2006-06-02
try removing the following line from /etc/apt/apt.conf

```
Acquire::http::Proxy "false"
```

---

### Post by psyke83 on 2006-06-02
That did the trick, thanks hysterio!

---

