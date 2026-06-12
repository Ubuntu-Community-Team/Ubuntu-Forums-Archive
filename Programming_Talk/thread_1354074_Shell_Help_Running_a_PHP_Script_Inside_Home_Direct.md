---
title: "Shell Help: Running a PHP Script Inside Home Directory"
date: 2009-12-13
forum: Programming Talk
---

### Post by Gias Kay on 2009-12-13
Hi all,

As far as I know, below is one of the ways to have a shell script executing a PHP file, providing that the PHP file can be reached through the internet:

```
#!/bin/sh
wget -t 1 -q -O - "http://localhost/scripts/example.php"
```

My question is, whether I can put the PHP file inside my home directory (keeping it away from the net for security reasons) but still being able to execute it? And if so, what is the correct Shell script to do the task? Thanks for your help!

---

### Post by Physical Hook on 2009-12-13
Install [COLOR=Green]php5-cli[/COLOR].

---

### Post by Gias Kay on 2009-12-13
Nice, I got it, thanks :D

---

### Post by Hellkeepa on 2009-12-13
HELLo!

Also, add the correct shebang line to the top of the PHP-script, add execute permissions to it, and you can use it just like any other shell script. ;-)

Happy codin'!

---

### Post by Barriehie on 2009-12-14
On a side note what I've ended up doing is creating a www folder in my home dir and then anything that I want net available gets a sym link in /var/www.  It's a spin off of my backup routine... :)

Barrie

---

