---
title: "running a program"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by harry rao on 2008-04-28
can i run transmission at a particular time through the terminal?
i.e. i would like to run transmission at 12 pm since that's when my off peak limit starts.
is there a command i can use?

-harry.

---

### Post by TerpInHotLanta on 2008-04-28
Have you tried using cron for this? It's the tried-and-true method of running scheduled commands.

-Charlie

---

### Post by pedro_orange on 2008-04-28
A good scheduler (For scheduled tasks that is) is Cron.

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

To invoke Transmission from the Command-line you just type in:

```
transmission
```

Therefore to run transmission everyday at 12 (noon I presume) using Cron I would try using something along the lines of (NOT tested):

```
00 12 * * * transmission
```

---

### Post by Hospadar on 2008-04-28
cron will definately work, but can be a little arcane.  You may want to look into something more graphical.  I've used kalarm (I think) to do this sort of thing in the past.

---

