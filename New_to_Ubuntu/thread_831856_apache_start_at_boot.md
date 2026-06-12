---
title: "apache start at boot"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by bryctucker on 2008-06-17
hi guys, i got apache, mysql and php5 all working together and was just wondering what i had to do to get apache and the MySQL daemons to start at boot

keep on rockin' :guitar:

---

### Post by hyper_ch on 2008-06-17
it should automatically start at boot - or you did not install it from the repos.

---

### Post by brian_p on 2008-06-17
> **bryctucker said:**
> hi guys, i got apache, mysql and php5 all working together and was just wondering what i had to do to get apache and the MySQL daemons to start at boot

If they are working they must have been started. To reassure yourself check for the obvious scripts in /etc/init.d.

---

### Post by billygriffiths on 2008-06-17
I installed mine using the "sudo aptitude install" command, and all starts up automatically.

---

### Post by bryctucker on 2008-06-17
yes i installed them via sudo apt-get install

the only thing i didn't install via repos is webmin

and it asked me if i wanted to start that at boot.

---

### Post by hyper_ch on 2008-06-17
well, if you installed apache etc. through the repos then they are installed as daemons and run at boot.

---

### Post by bryctucker on 2008-06-17
alright, thanks i just wanted to make sure incase the power joes out here

---

