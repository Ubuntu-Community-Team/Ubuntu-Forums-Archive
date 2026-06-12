---
title: "Strange system time problems"
date: 2014-05-07
forum: New to Ubuntu
---

### Post by LastDino on 2014-05-07
My system clock seems to slow itself over period of time. I've tried both manual and online synchro setting. It is not really a big deal as I simply go and correct it in settings if I notice the difference in my wall clock and clock on xubu. Oddly enough, it also managed to fasten itself for 5 min. yesterday. 

Like I said, it is not really a big deal as I tend to notice it rather quickly and change it to correct time in settings. But I would like to know if it is some bug or something? And if there is fix.

---

### Post by sandyd on 2014-05-07
Does the problem occur while the computer is shut off?
It may be that the CMOS battery needs a change.

---

### Post by sammiev on 2014-05-07
> **sandyd said:**
> Does the problem occur while the computer is shut off?
It may be that the CMOS battery needs a change.

+1 but if you have it set to update from the Internet it should update within seconds on been on-line.

---

### Post by tgalati4 on 2014-05-08
Add a driftfile and you can get to microseconds.

```
man ntp.conf
```

[http://ubuntuforums.org/showthread.php?t=2117108&highlight=ntp+microseconds](http://ubuntuforums.org/showthread.php?t=2117108&highlight=ntp+microseconds)

---

### Post by LastDino on 2014-05-08
> **sandyd said:**
> Does the problem occur while the computer is shut off?
It may be that the CMOS battery needs a change.

> **sammiev said:**
> +1 but if you have it set to update from the Internet it should update within seconds on been on-line.

This is likely, after all I haven't changed BIOS battery in last 2 years. Though, it's synched with internet, like I mentioned in OP. I'll let you know if problem persists after I change batteries, I'll mark thread as solved for time being.

> **tgalati4 said:**
> Add a driftfile and you can get to microseconds.

```
man ntp.conf
```

[http://ubuntuforums.org/showthread.php?t=2117108&highlight=ntp+microseconds](http://ubuntuforums.org/showthread.php?t=2117108&highlight=ntp+microseconds)

Thanks for nice read ^^

---

