---
title: "crontab"
date: 2010-10-03
forum: Programming Talk
---

### Post by flyingsliverfin on 2010-10-03
how would i add an entry to crontab if i just want the script to be run once every day at any time (but only once a day!) would it be:

* * * * * /x/x/x/x

---

### Post by dwhitney67 on 2010-10-03
Your example runs the script every minute.

To run it once per day, at a designated hour, modify the second field (ie the second *) with a hour number ranging from 0 to 23.
```

* 14 * * * /path/to/my/script

```
Above, the script will be run at 14:00 (2pm) every day.

---

### Post by SeijiSensei on 2010-10-03
I'd put a zero  in the first column to get 14:00 like this:

0 14 * * * /path/to/my/script

I think that 

* 14 * * * /path/to/my/script

will run once every minute from 14:00 to 14:59.

---

### Post by flyingsliverfin on 2010-10-03
right but my desktop isnt always on and im not sure when i'll be on. It's different day to day. is there a way to get it to run the script once a day as soon as the computer turns on?

---

### Post by spjackson on 2010-10-04
> **flyingsliverfin said:**
> right but my desktop isnt always on and im not sure when i'll be on. It's different day to day. is there a way to get it to run the script once a day as soon as the computer turns on?
Well, you can get a command to run at reboot
```

@reboot /x/x/x/x

```(See "man 5 crontab".) However, that wouldn't quite do what you want because
a) It would run twice if you booted twice in one day.
b) If your computer stayed on for over 24 hours then it would not run on the 2nd day.

You could put something in your script to check whether it has already been run today to cater for a). You could also include an "@daily" entry to cater for b).

---

### Post by dwhitney67 on 2010-10-04
> **SeijiSensei said:**
> I'd put a zero  in the first column to get 14:00 like this:

0 14 * * * /path/to/my/script

I think that 

* 14 * * * /path/to/my/script

will run once every minute from 14:00 to 14:59.

Thanks for catching my mistake.

---

### Post by flyingsliverfin on 2010-10-04
i actually usually put my desktop to suspend not shutdown. is there a @___ for waking up?

---

### Post by spjackson on 2010-10-04
> **flyingsliverfin said:**
> i actually usually put my desktop to suspend not shutdown. is there a @___ for waking up?
Did you read the bit that said 'See "man 5 crontab"'? Let me see... no there isn't.

However, a quick Google tells me any jobs that were due to run while suspended will run on wakeup. So, just schedule it for any time you like. (Note that, jobs that were skipped while the system was down, rather than suspended, are *not* invoked at boot time.)

---

### Post by flyingsliverfin on 2010-10-04
so it makes up the things it missed. thta should be good enough for my purposes

---

### Post by jakupl on 2010-10-04
Have a look at anacron. Anacron is probably more suitable for you.

[http://en.wikipedia.org/wiki/Anacron](http://en.wikipedia.org/wiki/Anacron)

---

### Post by flyingsliverfin on 2010-10-04
so for anacron i edited the /etc/anacrontab and added
1   5   test   /x/x/x

that will execute it once a day at a 5 min after the computer turns on?

---

