---
title: "samba unknown job"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by david0075 on 2008-06-13
i tried to start samba with 'sudo start /ect/init.d/samba' as suggested by another forum post, but it replies with 'start: unknown job: /ect/init.d/samba'. 
it didnt ask me for my password. i checked for /ect/init.d/samba file using nautilus and found it. i have had it working before and have transfered files. not sure what i should be doing.
oh, im using hardy heron 8.04 and the latest samba (3 weeks old)

---

### Post by hyper_ch on 2008-06-13
On debian-based system its:
```

sudo /etc/init.d/samba start|restart|stop

```
start|restart|stop are the usual way to handle the services... and for other services just replace "samba" accordingly.

---

### Post by david0075 on 2008-06-13
thanks for the help, i see what i was doing wrong.
now i tried 'sudo /ect/init.d/samba start' and also for restart, and both returned 'sudo: /ect/init.d/samba: command not found'

---

### Post by hyper_ch on 2008-06-13
have a look at what you write...

---

