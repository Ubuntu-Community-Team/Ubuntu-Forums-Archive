---
title: "Botched gitweb install, not recreating config file"
date: 2012-02-08
forum: Programming Talk
---

### Post by mrtc on 2012-02-08
I'm trying to reinstall gitweb to no avail. I assumed an apt-get remove and install would recreate the /etc/gitweb.conf file but that doesn't appear to be the case. Is there a way I can affirmatively perform a clean install of gitweb, or will I have to create gitweb.conf myself?

Thanks!

---

### Post by SevenMachines on 2012-02-09
If the deb package is still in the cache then to restore missing conf files
```
$ dpkg -i --force-confmiss  /var/cache/apt/archives/gitweb_*.deb
```

I think purging and reinstalling would probably do it too
```
$ apt-get purge gitweb
$ apt-get install gitweb
```

---

### Post by mrtc on 2012-02-09
Excellent, that seems to have created the conf files. However it doesn't look like gitweb's working yet. I see references in the gitweb file in /etc/apache2/conf.d to the directory /usr/share/gitweb. I took a look and there's no gitweb directory there. Any suggestions?

---

