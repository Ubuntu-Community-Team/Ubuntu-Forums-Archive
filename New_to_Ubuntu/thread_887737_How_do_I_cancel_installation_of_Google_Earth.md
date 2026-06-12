---
title: "How do I cancel installation of Google Earth?"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by vikramaditya on 2008-08-12
I'm grabbing Google Earth **_thru terminal_** & it's downloading very sloooow!  I don't have the 2hrs 22min it says is remaining, so I'd like to halt the process safely.  "plz help". :)

---

### Post by Ryadt on 2008-08-12
Does closing the terminal not cancel it?

---

### Post by neurostu on 2008-08-12
Generally to cancel a command that is running in a terminal all you have to do is press:
```

Ctrl+C

```
That should cancel almost anything...

---

### Post by vikramaditya on 2008-08-12
> **neurostu said:**
> Generally to cancel a command that is running in a terminal all you have to do is press:
```

Ctrl+C

```
That should cancel almost anything...
Thanks, that got it all killed up good!  Now, where do I find the "orphaned" junk that *did* get downloaded?

---

### Post by neurostu on 2008-08-12
how did you download it?

---

### Post by vikramaditya on 2008-08-14
> **neurostu said:**
> how did you download it?
```
sudo apt-get install googleearth
```
I'm just wondering if the partially d/l'ed stuff was cached somewhere in the system.

---

### Post by Martje_001 on 2008-08-14
/tmp

But that's empty everytime you startup. And do this:
```
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get autoclean
```

---

