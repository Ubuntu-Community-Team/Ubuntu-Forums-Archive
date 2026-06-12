---
title: "Beginner's MySQL question (Hardy)"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by jbirky on 2008-06-23
Hey there

I'm still pretty new to Linux in general, so I'm sorry if this is pretty basic.  I've installed Apache2/PHP5/MySQL on my Hardy (8.04) machine in an attempt to learn a little about web servers.  For the most part, it's been working ok.  However, for some reason my MySQL server is not starting on boot like it's supposed to.  (It tries to load it during the boot sequence, but it ends up with a [FAIL].  When I start it manually from the terminal after Ubuntu has loaded, however, it works fine.

I've looked on several other forums for solutions.  They say that the reason for this is because MySQL is trying to load before some other essential network service or something along those lines.  (They mention something about RC scripts and SXX numbering)  I'm just wondering how I would go about fixing a problem like this.  Or, if anyone has another solution, I would be open to that as well.

---

### Post by comandrei on 2008-06-23
Try:
```

   sudo update-rc.d mysql defaults

```
If it dosen't work, please give us the ouput of 
```

ls -l /etc/rc2.d/ | grep mysql

```
It should look like this:
```

lrwxrwxrwx 1 root root  23 2008-06-21 08:36 S17mysql-ndb-mgm -> ../init.d/mysql-ndb-mgm
lrwxrwxrwx 1 root root  19 2008-06-21 08:36 S18mysql-ndb -> ../init.d/mysql-ndb
lrwxrwxrwx 1 root root  15 2008-06-21 08:36 S19mysql -> ../init.d/mysql

```

---

### Post by jbirky on 2008-06-23
Upon entering the update command, it tells me 'System startup links for /etc/init.d/mysql already exist.'

Here is the output for the grep:

```
lrwxrwxrwx 1 root root  23 2008-06-18 00:13 S17mysql-ndb-mgm -> ../init.d/mysql-ndb-mgm
lrwxrwxrwx 1 root root  19 2008-06-18 00:13 S18mysql-ndb -> ../init.d/mysql-ndb
lrwxrwxrwx 1 root root  15 2008-06-18 00:13 S19mysql -> ../init.d/mysql
```

---

### Post by jbirky on 2008-06-23
I think I might have just figured out what's wrong.  I don't have a static IP configured, so there's a good chance that my machine's not getting one until after Ubuntu loads.  Is this correct?

---

