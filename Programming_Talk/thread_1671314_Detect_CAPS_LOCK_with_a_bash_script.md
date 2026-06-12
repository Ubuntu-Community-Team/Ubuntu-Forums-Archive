---
title: "Detect CAPS LOCK with a bash script?"
date: 2011-01-19
forum: Programming Talk
---

### Post by Dara Javaherian on 2011-01-19
Hello all, 

I have a laptop with no LED's to indicate whether or not the caps lock key is active. I was thinking of writing a bash script to do this but I can't seem to be able to detect it via the terminal. Is there any way that I can do this?

Thanks,
Dara

---

### Post by ghostdog74 on 2011-01-20
is your caps lock ALWAYS going to be ON? type a character on your terminal, if its CAPs, then turn it off. Why do you need a script for that?

---

### Post by Arndt on 2011-01-20
> **Dara Javaherian said:**
> Hello all, 

I have a laptop with no LED's to indicate whether or not the caps lock key is active. I was thinking of writing a bash script to do this but I can't seem to be able to detect it via the terminal. Is there any way that I can do this?

Thanks,
Dara

If you have an X server running, you can use "xset -q".

---

### Post by Dara Javaherian on 2011-01-20
> **Arndt said:**
> If you have an X server running, you can use "xset -q".

Thank you! This works! I use 

```
xset -q | grep Caps
```

---

