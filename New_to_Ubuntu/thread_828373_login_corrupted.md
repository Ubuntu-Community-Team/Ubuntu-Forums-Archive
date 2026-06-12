---
title: "login corrupted"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by msidhard on 2008-06-13
few days back i had a crash . my system hanged before login screen. then i entered in console mode and then i started dbus and started x then mounted all my drives manully. but the main problem is i cannot login using my previous id . now i enter as only root . how can i recover it . advance thanks

---

### Post by gr4nf on 2008-06-13
You could just create your old user with useradd. Would you post the output of:
```

ls /etc/rc3.d

```
please?

---

### Post by msidhard on 2008-06-13
i've tried useradd but it says user already exists then i also changed the rc3 instead of rc2 in /etc/inittab but it too not worked for me . the hanging problem presists . if i login in console mode it says root@lawyer instead of user@lawyer. if i logged in after booting to x then it says user@lawyer. but if i close the terminal then it comes back to root@lawyer.

---

### Post by msidhard on 2008-06-13
and now i am using my mobile to browse. so i cant say what was the output u need.

---

### Post by Happy_Man on 2008-06-13
What errors does it give if you boot normally (eg, not the recovery kernel)?

---

### Post by msidhard on 2008-06-14
The System Hangs Before Login Screen Loads.

---

### Post by Happy_Man on 2008-06-14
Interesting... try that again, only press ctrl-alt-f1 as it's booting and watch the text that flies by for any error messages. 

Also, the reason that you can't log in as yourself in the recovery kernel is because you are starting X from the root account (which is what the recovery kernel logs itself in as). I believe that if you press ctrl-alt-f3 and log in to that text prompt as yourself, you will be able to start X from there so that it lets you log in normally.

---

