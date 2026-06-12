---
title: "What wrong with my cron?"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by Jason Weiss on 2008-06-10
Hi People my crontab does not work

>  55 23 * * *     transmission

0 12 * * *      killall transmission

10 12 * * *     killall transmission


is it saved in the correct location?

> /tmp/crontab.WZg7Lw/crontab    

---

### Post by Oldsoldier2003 on 2008-06-10
> **Jason Weiss said:**
> Hi People my crontab does not work



is it saved in the correct location?
 
transmission is a gui application use this format for gui applications.
```
18 10 * * * DISPLAY=:0 /full/path/to/application
```

---

### Post by Jason Weiss on 2008-06-10
So I wonder how do find the path?

---

### Post by hyper_ch on 2008-06-10
```

find

```

```

locate

```

---

### Post by Jason Weiss on 2008-06-10
man i love ubuntu 

thankyou all

---

