---
title: "[SOLVED] Start gui program in seperate process from terminal"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by Doogle999 on 2008-07-30
Hi guys/gals,

If I wanna run a gui program from the terminal (gparted for example) I type:

```
sudo gparted
```

...but this makes the terminal wait until gparted has been closed before letting me type more commands. Is there a way to run gparted in a separate process so I can carry on using my terminal while it's running?

Thanks in advance,

Doogle.

---

### Post by freak42 on 2008-07-30
append a & to your command
like ```
sudo gparted &
```

---

### Post by freak42 on 2008-07-30
oh.. and something else:

if you forgot to append the & and you find your terminal locked/busy 
press ctrl-z and on the terminal you get: bg
this will free your terminal again without closing the app that was locking your terminal.

---

### Post by billgoldberg on 2008-07-30
> **freak42 said:**
> oh.. and something else:

if you forgot to append the & and you find your terminal locked/busy 
press ctrl-z and on the terminal you get: bg
this will free your terminal again without closing the app that was locking your terminal.

Or just open another terminal.

If you have your terminal sitting on f12, it's faster.

---

### Post by hyper_ch on 2008-07-30
besides, you should use gksudo

---

### Post by gvartser on 2008-07-30
> **hyper_ch said:**
> besides, you should use gksudo

Why?
/g

---

### Post by hyper_ch on 2008-07-30
> **gvartser said:**
> Why?
/g

Because I say so 8)

You could also have a read here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Doogle999 on 2008-07-30
Thanks guys, all useful tips!

---

### Post by gvartser on 2008-07-30
> **hyper_ch said:**
> Because I say so 8)

You could also have a read here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Thanx for a very usefully and enlightening answer.

---

