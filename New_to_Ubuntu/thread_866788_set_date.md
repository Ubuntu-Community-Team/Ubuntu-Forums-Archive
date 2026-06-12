---
title: "set date??"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by ra2008 on 2008-07-22
Hi my date format when i type,
```
$ date
``` is :
Thu Jan  1 02:52:56 CET 1970

i am trying to change it by:

$ date -s "Tue Jul  22 12:20:0 CET 2008"

i get :

date: invalid date ` Tue Jul  22 12:20:00 CET 2008'

help?
thanx

---

### Post by abn91c on 2008-07-22
try updating the tzdata package, or just adjust time from the desktop

---

### Post by brian_p on 2008-07-22
> **ra2008 said:**
> 

$ date -s "Tue Jul  22 12:20:0 CET 2008"

i get :

date: invalid date ` Tue Jul  22 12:20:00 CET 2008'


Leaving out 'CET' may get you on your way. Google with 'set date linux' or 'change date linux' will also point you in the direction you want to go.

---

### Post by Joeb454 on 2008-07-22
Try ```
man date
``` and read through that, it should help :)

---

### Post by Bachstelze on 2008-07-22
Why is the clock still in 1970 anyway? You might want to check your CMOS battery. Also, instead of setting the date manually, use ntp:

```
sudo ntpdate pool.ntp.org
```

---

### Post by ra2008 on 2008-07-22
> **HymnToLife said:**
> Why is the clock still in 1970 anyway? You might want to check your CMOS battery. Also, instead of setting the date manually, use ntp:

```
sudo ntpdate pool.ntp.org
```

well how can i change the value of hardware rtc. ???
the date is old coz it is an embedded board.
thanks

---

### Post by RuleMaker on 2008-07-22
Just click on the clock on your panel, expand "Locations", click "Edit"-->"Time Settings"-->"Unlock" and set the date and time as you want.

---

### Post by paul101 on 2008-07-22
change the date and time in the bios?

---

### Post by ra2008 on 2008-07-22
> **RuleMaker said:**
> Just click on the clock on your panel, expand "Locations", click "Edit"-->"Time Settings"-->"Unlock" and set the date and time as you want.

i told u its an embedded board. no windows and mouse..

---

### Post by brian_p on 2008-07-22
> **ra2008 said:**
> i told u its an embedded board. no windows and mouse..

So did any suggestion given work for you? It should be possible to set the system time even in this case.

---

