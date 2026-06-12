---
title: "Ubuntu-Server (PHP5) Problem"
date: 2007-07-30
forum: Programming Talk
---

### Post by md5hash on 2007-07-30
i have a working LAMP server, but when i type 

```
php -v
```

it say php is not yet installed.

what is wrong?

---

### Post by heimo on 2007-07-30
Maybe you don't have PHP command line interpreter installed? If you're running php5, that package would be php5-cli and command to run php files would be php5

EDIT: I'm assuming here that your problem is that you can't run php on command line. If you just want to know version of your php, create a script with [phpinfo]("http://php.net/phpinfo") and check its output.

---

### Post by md5hash on 2007-07-30
i tried to install php5-cli but there are unresolved dependecies leading to php is not installed.
do i still have to still install php even if i have a completely working server ?

---

### Post by deuce868 on 2007-07-30
The cli and the apache are really two different packages. The one that is working will server pages through apache, but if you want to do some php shell scripts or cron files then you'll need the cli version working.

---

### Post by md5hash on 2007-07-30
i see, default installation of ubuntu-server(LAMP) doesnt include cli, right?

---

