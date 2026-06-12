---
title: "Sony erricsson W980"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by Technomouse on 2008-11-09
OK i am confused i have spent some time trying to get the above model of phone working.

Two posts here i have followed which included PSYDYM and that didnt work can anyone here help please

I plug the phone in and i can see the photo's but not the music?

HELP PLEASE

---

### Post by zachalekos on 2008-12-01
You may visit the 3rd page for his post. The post says

1- Download these two files

[http://www.esnips.com/doc/2ca0b833-c...rage.rules.tar](http://www.esnips.com/doc/2ca0b833-c...rage.rules.tar)

[http://www.esnips.com/doc/79f10bc4-b...ions.rules.tar](http://www.esnips.com/doc/79f10bc4-b...ions.rules.tar)

2- Backup 60-persistent-storage.rules and 40-permissions.rules of /etc/udev/rules.d/


3- rename 65-persistent-storage.rules to 60-persistent-storage.rules

4- copy 60-persistent-storage.rules and
40-permissions.rules in /etc/udev/rules.d/


Thanks jmaxx. It worked for me in 8.10. Hope it works for all.

[http://ubuntuforums.org/showthread.php?t=975622&page=3](http://ubuntuforums.org/showthread.php?t=975622&page=3)

This worked for me. If it works for you, please mark thread as closed.

---

