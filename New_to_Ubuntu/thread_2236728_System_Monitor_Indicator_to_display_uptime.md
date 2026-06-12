---
title: "System Monitor Indicator to display uptime"
date: 2014-07-28
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2014-07-28
Hi Guys,

I am trying to use webupd8.org's System Monitor Indicator to display the uptime of the machine in the panel at the top of Ubuntu 14.04.
I can get it to work but am getting too much information.
I am getting:
```

13:46:24 up 22:51,  2 users,  load average: 0.24, 0.35, 0.55

```

Is there a way I can use sed or grep to just display 
```
22:51
```
as the output?

---

### Post by tgalati4 on 2014-07-28
Not pretty:

> tgalati4@Mint14-Extensa ~ $ uptime
 14:25:07 up 6 days, 18:51,  2 users,  load average: 0.06, 0.14, 0.25
tgalati4@Mint14-Extensa ~ $ uptime | gawk '{print $5}'
18:51,

tgalati4@Mint14-Extensa /proc $ uptime | gawk -F , '{print $1}'
 14:30:41 up 6 days
tgalati4@Mint14-Extensa /proc $ uptime | gawk -F , '{print $2}'
 18:56



Or elegant.

You might have better luck with working on /proc/uptime directly.

Uptime displays differently with days versus just hours so your display script needs to take that into account.

Uptime is too long.
Gawk works but its not pretty.
You want elegant.

---

### Post by ajgreeny on 2014-07-28
You should be able to do it with **uptime | cut -c 14-18**

---

### Post by GrouchyGaijin on 2014-07-28
thank you AJ

---

