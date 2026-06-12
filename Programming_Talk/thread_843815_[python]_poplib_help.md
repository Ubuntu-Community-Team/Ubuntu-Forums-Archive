---
title: "[python] poplib help"
date: 2008-06-28
forum: Programming Talk
---

### Post by days_of_ruin on 2008-06-28
I can never get this to work!
```
import poplib
a = poplib.POP3("pop.gmail.com")
```
It never loads.:(

---

### Post by ghostdog74 on 2008-06-28
> **days_of_ruin said:**
> I can never get this to work!
```
import poplib
a = poplib.POP3("pop.gmail.com")
```
It never loads.:(

just these 2 statements will not get it to work. how about user name and password. also next time, post what doesn't work and error messages if any.

---

### Post by days_of_ruin on 2008-06-28
> **ghostdog74 said:**
> just these 2 statements will not get it to work. how about user name and password. also next time, post what doesn't work and error messages if any.
No you have to connect to the pop server first then you do stuff with
a username and password.The point is it never loads.No error it just
stops there.

---

### Post by ghostdog74 on 2008-06-28
make sure you enable POP in gmail. check Google Help  >  Gmail Help  >  POP  > Configuring other mail clients for more info.
then make sure you connect using SSL and at port 995. 
```

server = poplib.POP3_SSL("pop.gmail.com", 995)

```
 Also POP is obsolete. Use IMAP and imaplib module if possible.

---

### Post by days_of_ruin on 2008-06-29
> **ghostdog74 said:**
> make sure you enable POP in gmail. check Google Help  >  Gmail Help  >  POP  > Configuring other mail clients for more info.
then make sure you connect using SSL and at port 995. 
```

server = poplib.POP3_SSL("pop.gmail.com", 995)

```
 Also POP is obsolete. Use IMAP and imaplib module if possible.

Thanks bro!How is POP obsolete?Do any mainstream email servers use it?

EDIT:To anyone who reads this: don't try this in the interactive prompt (">>>") as it will not work.

---

### Post by ghostdog74 on 2008-06-29
> **days_of_ruin said:**
> Thanks bro!How is POP obsolete?Do any mainstream email servers use it?

See [here]("http://www.imap.org/papers/imap.vs.pop.brief.html") and also [here]("http://www.python.org/doc/lib/module-poplib.html")

---

