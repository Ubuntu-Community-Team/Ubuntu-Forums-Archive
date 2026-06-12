---
title: "You don't have permission to access ......."
date: 2012-03-25
forum: New to Ubuntu
---

### Post by vivekpandey1991 on 2012-03-25
i installed moodle using 
```

sudo apt-get install moodle

```
bt when i try to access it from the browser using [http://localhost/moodle](http://localhost/moodle)
i get this error 
;code]
You don't have permission to access /moodle/home on this server.
[/code]
does anyone know where am i going wrong ? please help... thanx in advace

---

### Post by Ms. Daisy on 2012-03-27
If you don't find anyone on this forum that uses moodle, you could check the [moodle website]("http://moodle.org/support/").  They have some extensive documentation, and it looks like they have a forum as well.

---

### Post by shubham1 on 2012-03-27
> **vivekpandey1991 said:**
> i installed moodle using 
```

sudo apt-get install moodle

```bt when i try to access it from the browser using [http://localhost/moodle](http://localhost/moodle)
i get this error 
;code]
You don't have permission to access /moodle/home on this server.
[/code]
does anyone know where am i going wrong ? please help... thanx in advace
try these:
open a terminal and type:
```
sudo chown username /moodle/home
```
if it still dont work or it restricts permision in some other area then:
```
sudo chmod -R 777 /moodle/home
```
or 
```
sudo chmod -R 644 /moodle/home
```
depending on your needs choose any or depending on which will work usually the second is considered safe and is recommened
does not works os something do this:
```
sudo chown username /var/www/moodle
```
and if still not works or any other problem:
```
sudo chmod -R 777 /var/www/moodle
```
or
```
sudo chmod -R 644 /var/www/moodle
```
depending on your needs choose any or depending on which will work usually the second is considered safe and is recommened

---

