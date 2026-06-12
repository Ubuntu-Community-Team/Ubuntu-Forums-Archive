---
title: "problem with sudo"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by lio_013 on 2008-08-24
i just install the Ubuntu and first time i use the terminal i get this 
:(:(:(:(:(:(:(:(

```

sudo: timestamp too far in the future: Aug 24 15:02:24 2008

```

---

### Post by fiddledd on 2008-08-24
Have you tried rebooting?

---

### Post by Too Late on 2008-08-24
I hate that problem, too. But here's the solution:
[http://my.opera.com/render/blog/show.dml/337121](http://my.opera.com/render/blog/show.dml/337121)
> 
1. Check the timestamp sudo reports (will look something like below).
sudo: timestamp too far in the future: Jun 17 08:17:55 2006

2. Use Adjust Date & Time to set the date/time to the sudo timestamp or later.

3. Execute the 'sudo -k' command. (Clears the timestamp).

4. Use Adjust Date & Time to set the date/time back to the correct values.


---

### Post by skymera on 2008-08-24
I had that last year on Gutsy.

It happened because i think my clock in my BIOS was set either too far back or too far forward.

---

