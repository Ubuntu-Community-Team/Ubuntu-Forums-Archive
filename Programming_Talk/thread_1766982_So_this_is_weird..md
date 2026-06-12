---
title: "So this is weird."
date: 2011-05-25
forum: Programming Talk
---

### Post by btolman on 2011-05-25
I have 3 machines - a windows xp box that I use dreamweaver on; a windows 7 notebook that I use when I travel to client sites.  And I have a ubuntu 10LTS that I use to make sure that it will all run on a linux box.

With me so far?

I have a web app (php/mysql) that I sell that, when I sell it, I create a directory like "clientname-widget" and put them in the same directory.

I got a new client.  I did the usual copy.  It runs on the two windows boxes just fine.  It runs on the clients' hosted website.  It doesn't run on my ubuntu box.

Permissions are set identical.  Files are the same.  Only the name of the database and the directory's names are changed.  It runs from the master, and from other copies. It doesn't run from the new one.

Help?

---

### Post by Petrolea on 2011-05-25
Can you make your question a bit easier? There is so much info that I get confused while reading it. What exactly goes wrong?

---

### Post by jespdj on 2011-05-25
What does "it doesn't run" mean? Do you get an error message? If so, then what is the error message?

---

### Post by btolman on 2011-05-25
There is no error message.  Just a blank screen.

Not kidding.  This one has me banging my head on the keyboard.

---

### Post by DangerOnTheRanger on 2011-05-25
There *is* an error message, PHP's just hiding it from you. Enable debugging.
Although, I don't know how to do that myself...

---

### Post by Reiger on 2011-05-25
Licks index finger and points it at the sky... 
... this is what server logs are for:
```

cat /var/log/apache2/error.log

```

---

### Post by btolman on 2011-05-28
> **Reiger said:**
> Licks index finger and points it at the sky... 
... this is what server logs are for:
```

cat /var/log/apache2/error.log

```

That gave me the clue.

I misspelled the mysql username.

d'oh.

Thanks guys.

---

