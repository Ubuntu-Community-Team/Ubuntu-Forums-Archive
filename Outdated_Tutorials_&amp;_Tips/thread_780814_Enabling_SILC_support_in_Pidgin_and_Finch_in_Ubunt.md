---
title: "Enabling SILC support in Pidgin and Finch in Ubuntu 8.04"
date: 2008-05-03
forum: Outdated Tutorials &amp; Tips
---

### Post by agent8131 on 2008-05-03
Although SILC support is advertised as part of Pidgin and Finch that support is not actually available.  SILC is a highly secure instant messaging platform that is popular with groups and businesses concerned with privacy and security.  Unfortunately that last several releases of Ubuntu have not included a graphical SILC client and Hardy Heron is no exception.  So here are the steps to enable SILC support in Pidgin, and Finch as well.

1. Check your sources list to make sure the universe repository is enabled and that source packages are available.

   2. Change directories to where you’d like to work.

   3. ```
sudo aptitude update
```

   4. ```
sudo aptitude install build-essential devscripts fakeroot
```

   5. ```
sudo aptitude install libsilc-1.1-2 libsilc-1.1-2-dev
```

   6. ```
sudo apt-get build-dep pidgin
```

   7. ```
apt-get source pidgin
```

   8. ```
cd pidgin-2.4.1/
```

   9. ```
dch -n
```

  10. ```
dpkg-buildpackage -rfakeroot
```

  11. ```
cd ..
```

  12. ```
sudo dpkg -i libpurple0_2.4.1-1ubuntu2.1_*.deb
```

To revert:

```
sudo apt-get install libpurple0=1:2.4.1-1ubuntu2
```

Copied from:
[Enabling SILC support in Pidgin under Ubuntu 8.04 (Hardy Heron)]("http://hightechsorcery.com/2008/04/enabling-silc-support-pidgin-under-ubuntu-804-hardy-heron")

---

