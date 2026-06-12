---
title: "Awk confusion with regular expressions"
date: 2013-09-25
forum: Programming Talk
---

### Post by vasa1 on 2013-09-25
```
**[09:38 PM] ~ $ awk '/bin/sh/ { print }' /etc/passwd**
awk: cmd. line:1: /bin/sh/ { print }
awk: cmd. line:1:          ^ syntax error
**[09:39 PM] ~ $ awk '/bin\/sh/ { print }' /etc/passwd**
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
**[09:39 PM] ~ $ awk '/\/bin\/sh\// { print }' /etc/passwd**
[09:40 PM] ~ $ 

```
I tried three awk commands (in **bold**) using /etc/passwd as the input file. Only the second command worked. Why did the third command not work? Instead, I just got back the prompt implying that there was nothing for awk to print.

---

### Post by Vaphell on 2013-09-25
because there is no /bin/sh[COLOR="#0000FF"]/[/COLOR]

---

### Post by vasa1 on 2013-09-25
> **Vaphell said:**
> because there is no /bin/sh[COLOR="#0000FF"]/[/COLOR]
Kicks self ... hard :(

---

### Post by tgalati4 on 2013-09-25
You could make one.

---

