---
title: "halt / poweroff: symbolic links to reboot?"
date: 2012-12-07
forum: New to Ubuntu
---

### Post by ttmvtolinux on 2012-12-07
Hi, I'm learning about the halt and poweroff commands. What I found out just puzzles me. Here:
```

$ which halt
/sbin/halt
$ file /sbin/halt
/sbin/halt: symbolic link to `reboot'
$ which poweroff
/sbin/poweroff
$ file /sbin/poweroff
/sbin/poweroff: symbolic link to `reboot'

```Could anyone explain?
Thanks,

---

### Post by audiomick on 2012-12-07
What is it exactly that is puzzling you? Is it that those commands are coming up as being symbolic links? If so, I think your answer is that they are all the the same program. Looks like it to me, anyway.

Do you know about man pages? The manual pages you get with the command
```
man <command name>
```

I just looked, and saw that
```
man halt
```
```
man poweroff
```
```
man reboot
```

all pull up the same man page. Have a look at it yourself.

---

### Post by CharlesA on 2012-12-07
Basically running halt, poweroff, reboot just calls shutdown with certain flags set.

---

### Post by audiomick on 2012-12-07
> **CharlesA said:**
> Basically running halt, poweroff, reboot just calls shutdown with certain flags set.

Ah, I had wondered why there was more than just "shutdown". It does seem to do everything a person could need... ;)

I, when I need to turn the computer off from the terminal, use

```
shutdown -r now
```
to reboot, 
and
```
shutdown -P now
```
to turn off completely.

---

### Post by ttmvtolinux on 2012-12-07
Thanks, that really cleared it up for me.

---

