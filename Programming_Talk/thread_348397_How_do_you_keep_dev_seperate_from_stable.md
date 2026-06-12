---
title: "How do you keep dev seperate from stable?"
date: 2007-01-28
forum: Programming Talk
---

### Post by montgoss on 2007-01-28
So, I have one version of MythTV that works.  How do I install/work with a version out of subversion without messing up or overwriting the stable version on the machine?

I'm guessing there's some configure or make options that would allow this, right?  Anyone know them?

---

### Post by po0f on 2007-01-29
montgoss,

```
[FONT="Courier New"]$ cd /mythtv/source/dir
$ ./configure --prefix=/usr/local
$ make
$ sudo make install[/FONT]
```

/usr/local should be the default PREFIX, you may want to specify it just to be sure.

You may want to use [checkinstall](http://packages.ubuntu.com/edgy/admin/checkinstall) instead of `sudo make install` as well.  This will create a deb that you can uninstall (just in case there is no "uninstall" rule in MythTV's Makefile).

---

### Post by jblebrun on 2007-01-29
> **po0f said:**
> montgoss,

```
[FONT="Courier New"]$ cd /mythtv/source/dir
$ ./configure --prefix=/usr/local
$ make
$ sudo make install[/FONT]
```

/usr/local should be the default PREFIX, you may want to specify it just to be sure.

You may want to use [checkinstall](http://packages.ubuntu.com/edgy/admin/checkinstall) instead of `sudo make install` as well.  This will create a deb that you can uninstall (just in case there is no "uninstall" rule in MythTV's Makefile).

When using this method, make sure you also create a new database and config file location, so you don't overwrite your current setup files with potentially incompatible information.

---

### Post by montgoss on 2007-01-29
> **po0f said:**
> montgoss,

```
[FONT="Courier New"]$ cd /mythtv/source/dir
$ ./configure --prefix=/usr/local
$ make
$ sudo make install[/FONT]
```

/usr/local should be the default PREFIX, you may want to specify it just to be sure.If /usr/local is the default, don't I want to specify something else in order to prevent it from overwriting the existing install?  Note: The stable MythTV was installed from source also.

---

### Post by po0f on 2007-01-29
montgoss,

Ah, I thought that you had previously installed MythTV through the repos.  How messy is the install?  Does it install just a single binary, or a bunch of files that go in PREFIX/{lib,man,share} as well?

---

### Post by jblebrun on 2007-01-30
> **montgoss said:**
> If /usr/local is the default, don't I want to specify something else in order to prevent it from overwriting the existing install?  Note: The stable MythTV was installed from source also.

If you installed it from source using an unmodified ./configure && make && make install, then most likely, it's in /usr/local/*

You can verify this using the "which"command:

```

jason@localhost$ which mythtv-backend
/usr/bin/mythtv-backend
jason@localhsot$  

```

Assuming the package is made properly, using autotools, you can specify any prefix you'd like! I often install things into a local directory in my homepath:

```

./configure --prefix=/home/jblebrun/local

```

---

### Post by montgoss on 2007-01-30
> **jblebrun said:**
> If you installed it from source using an unmodified ./configure && make && make install, then most likely, it's in /usr/local/*

You can verify this using the "which"command:

```

jason@localhost$ which mythtv-backend
/usr/bin/mythtv-backend
jason@localhsot$  

``````
montgoss@montgoss-desktop:~$ which mythfrontend 
/usr/local/bin/mythfrontend
```
I'll try your suggestion later tonight.

---

