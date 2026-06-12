---
title: "Shutdown command"
date: 2012-02-06
forum: New to Ubuntu
---

### Post by astrobob.tk on 2012-02-06
Hey there,

I recently started using the shutdown command in the form:

```
sudo shutdown -P hh:mm
```

It has been working great for the past couple of days except for this morning. I left the laptop downloading some stuff & issued the command:

```
sudo shutdown -P 0640
```

so that it shutdowns at 0640 in the morning.

I didn't check it until 1400 when I noticed that it shutdown at 1025:

```
$ last -x | grep shutdown
shutdown system down  2.6.32-38-generi Mon Feb  6 10:25 - 14:39  (04:14) 
```

I am not sure what happened. Do you have any idea why it shutdown @ 1025 instead of 0640?

---

### Post by Sigma1 on 2012-02-06
My guess is you got it to shutdown 640 mins later, cf. man shutdown. The format for clock times would be 06:40.

> TIME  may  have  different  formats, the most common is simply the word 'now' which will bring the system down immediately.  Other  valid  formats  are  +m,where m is the number of minutes to wait until shutting down and hh:mm which specifies the time on the 24hr clock.

;)

---

### Post by astrobob.tk on 2012-02-06
> **Sigma1 said:**
> My guess is you got it to shutdown 640 mins later, cf. man shutdown. The format for clock times would be 06:40.
;)


LOL. thanks :D

Indeed, it wrote 0640 instead of 06:40. I'm accustomed to use use 0640 hrs.

Thanks :D

---

