---
title: "System time changes automatically."
date: 2011-10-06
forum: New to Ubuntu
---

### Post by pmohankumar on 2011-10-06
Hi friends,

Iam using ubuntu 9.10.
in my system, date & time changes automatically for a weak or two weaks later.

---

### Post by binary00mind on 2011-10-06
Do you have "ntp" package installed. and if yes did you set up automatic time/date update (by ntp pool sync) 

Never heard of scenario like you have on your hands.

---

### Post by qkall on 2011-10-06
try reconfiguring your location..

> sudo dpkg-reconfigure tzdata

---

### Post by maniat1k on 2011-10-06
If you have ntp installed n a terminal try this

```

sudo -i
ntpdate -u ntp.ubuntu.com

```
after that type
```

date 

```
and show us what you get

---

### Post by pmohankumar on 2011-10-07
Hi,

I didn't installed "NTP".
i just configured time & date in default OS settings.

---

