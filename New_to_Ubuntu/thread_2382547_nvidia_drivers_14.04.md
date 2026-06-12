---
title: "nvidia drivers 14.04"
date: 2018-01-14
forum: New to Ubuntu
---

### Post by fattyz on 2018-01-14
Hi, I installed the Nvidia driver in software updater and now i can't log into ubuntu and change it back.  I can log into a guest session.  If I try to type a password the screen goes blank and reloads.  Is there a way to do this without re installation.  I also tried logging into failsafe graphics mode from grub advanced options but no luck, system won't load.

Dell inspiron 7567 Nvidia geforce gtx 1050 ti  Windows 10 ubuntu 14.04

Thanks

---

### Post by Bashing-om on 2018-01-14
fattyz; Hello -

Could be any number of things.
What results at the login screen with key combo ctl+alt+F1 -> TTY1 ?
Can you log into the system here ?

If so, execute terminal command:
```

sudo lshw -C display

```
and tell us what is the configuration line in that output. 

[INDENT][INDENT]Just a good place to start
[/INDENT][/INDENT]

---

### Post by fattyz on 2018-01-14
Can't get anything with that the screen just goes black and rolls back to the login.  I'll just reinstall, and not try that Nvidia driver tomorrow, I think I've gotten that far a few other times.  I erased everything last big crash anyway so it's just a matter of a little reinstall time.   I'll mark the thread closed thanks.

---

### Post by Bashing-om on 2018-01-14
fattyz; Ho Kay :)

That nuclear solution always works .

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

### Post by monkeybrain20122 on 2018-01-14
I think it is the HEW kernel, I think 14.04 get upgraded to the same bad kernel as 16.04 if HEW is enabled.
[https://ubuntuforums.org/showthread.php?t=2382206](https://ubuntuforums.org/showthread.php?t=2382206)
There are a few threads like this.

You don't need the nuclear option, all you have to do is to log into the old kernel and delete the new one and reboot.

---

