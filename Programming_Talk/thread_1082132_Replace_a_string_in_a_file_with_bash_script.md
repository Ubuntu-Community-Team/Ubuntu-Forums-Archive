---
title: "Replace a string in a file with bash script"
date: 2009-02-27
forum: Programming Talk
---

### Post by scifo_dk on 2009-02-27
Hi there.

I need at bash script to open a file and replace a single line of code, with one i provide.
To be more exact, i want it to:
gksu gedit /etc/init.d/rc

and replace CONCURRENCY=none with CONCURRENCY=shell and save.

Can anyone tell me how to do that?

Kind regard
Scifo

---

### Post by geirha on 2009-02-27
sed is your friend.
```
sudo sed -i 's/CONCURRENCY=none/CONCURRENCY=shell/' /etc/init.d/rc
```

[http://manpages.ubuntu.com/manpages/intrepid/en/man1/sed.1.html](http://manpages.ubuntu.com/manpages/intrepid/en/man1/sed.1.html)

---

### Post by monkeyking on 2009-02-27
just take care that none, only appears once in the file.

---

### Post by leewebb on 2009-02-28
> **geirha said:**
> sed is your friend.
```
sudo sed -i 's/CONCURRENCY=none/CONCURRENCY=shell/' /etc/init.d/rc
```

[http://manpages.ubuntu.com/manpages/intrepid/en/man1/sed.1.html](http://manpages.ubuntu.com/manpages/intrepid/en/man1/sed.1.html)

This is a good example of how to do it, but I would personally enhance it further by specifying that only lines **beginning** with [FONT="Courier New"]CONCURRENCY[/FONT] are replaced. This ensures that only config item is changed (as opposed to comments etc, unless you want them done as well), but also to avoid other tests that may hardwire [FONT="Courier New"]CONCURRENCY=none[/FONT] (which /etc/init.d/rc does)

So this gives:

[FONT="Courier New"]sudo sed -i 's/^CONCURRENCY=none/CONCURRENCY=shell/' /etc/init.d/rc[/FONT]

---

### Post by scifo_dk on 2009-03-04
Great work guys!

Exactly what I needed.

Thank you for your help, I might need more like this in the near future. :D

// Scifo

---

