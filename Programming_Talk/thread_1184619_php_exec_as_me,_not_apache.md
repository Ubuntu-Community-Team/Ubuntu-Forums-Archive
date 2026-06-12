---
title: "php exec as me, not apache"
date: 2009-06-11
forum: Programming Talk
---

### Post by MadnessRed on 2009-06-11
Hi, is it possible to execute scripts in php as myself, rather than apache, for example I would like to be able to control my media from php, as in,
exec("banshee --next"); the only probel is that banshee is running under anthony and php is runni gunder apache, any help would be great.

---

### Post by odyniec on 2009-06-11
Create a wrapper script for banshee, e.g.:
```
#!/bin/sh
/usr/bin/banshee $@
```
Then, add a /etc/sudoers line to allow the Apache user to execute the wrapper script as yourself:
```
sudo visudo
```
```
www-data    ALL=(yourusername) NOPASSWD: /some/path/banshee-wrapper.sh
```
In your PHP script, execute the wrapper with sudo:
```
exec('sudo -u yourusername /some/path/banshee-wrapper.sh --next')
```

---

### Post by MadnessRed on 2009-06-11
> **odyniec said:**
> Create a wrapper script for banshee, e.g.:
```
#!/bin/sh
/usr/bin/banshee $@
```
Then, add a /etc/sudoers line to allow the Apache user to execute the wrapper script as yourself:
```
sudo visudo
```
```
www-data    ALL=(yourusername) NOPASSWD: /some/path/banshee-wrapper.sh
```
In your PHP script, execute the wrapper with sudo:
```
exec('sudo -u yourusername /some/path/banshee-wrapper.sh --next')
```

hm, I seem to have done domethign wrong, when I made the changes nothing happenes, I went to check they sudoers file and...

```
anthony@Anthony-PC:~$ sudo visudo
>>> sudoers file: syntax error, line 26 <<<
sudo: parse error in /etc/sudoers near line 26

anthony@Anthony-PC:~$ sudo gedit /etc/sudoers
>>> sudoers file: syntax error, line 26 <<<
sudo: parse error in /etc/sudoers near line 26

anthony@Anthony-PC:~$ sudo
>>> sudoers file: syntax error, line 26 <<<
sudo: parse error in /etc/sudoers near line 26

anthony@Anthony-PC:~$ visudo
visudo: /etc/sudoers: Permission denied
```

whoops, I think I have just broken sudo. Hopefulyl I have root login enabled

---

### Post by MadnessRed on 2009-06-11
nope, I dont have root access, though i think I have fixed it, I booted into live cd, sudo gedit the file and, its read only, even to root, I though ill chmod it to readable for mod, then though actually chmod it 777, for now and edit it normally. So i commented out the line, and saved, then chmoded it back to 400.

now I will restart and hopefully it will work.

---

### Post by randallecook on 2009-06-11
Apache is configurable to run as different users, but you might not want to do that for security reasons. Speaking of security, what you are doing is tricky because you are essentially giving your web handling code higher privileges. I had to do this at work for various reasons, and had to jump through some hoops to get past all the security restrictions. The sysadmin and I ended up setting the 'setuid' bit on the CGI script to that our CGI would run as the proper user and not Apache. Good luck.

---

### Post by MadnessRed on 2009-06-12
> **randallecook said:**
> Apache is configurable to run as different users, but you might not want to do that for security reasons. Speaking of security, what you are doing is tricky because you are essentially giving your web handling code higher privileges. I had to do this at work for various reasons, and had to jump through some hoops to get past all the security restrictions. The sysadmin and I ended up setting the 'setuid' bit on the CGI script to that our CGI would run as the proper user and not Apache. Good luck.

lol all I wated to do was have a little app on my homepage that would show currently playing track and have, next previous, pause and play. Don't think its worth messing up computer completely.

---

