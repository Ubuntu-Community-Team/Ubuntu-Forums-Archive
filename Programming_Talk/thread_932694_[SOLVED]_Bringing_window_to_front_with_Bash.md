---
title: "[SOLVED] Bringing window to front with Bash"
date: 2008-09-28
forum: Programming Talk
---

### Post by lavinog on 2008-09-28
I am playing around with automating a web application.
If the site is already loaded I want to use the already loaded site, but i need a way to make it the active window.

How can I make a window active through bash?

---

### Post by tomchuk on 2008-09-28
Install wmctrl
```

sudo apt-get install wmctrl

```
Activate and raise a window (match against its window title)
```

wmctrl -a 'Firefox'

```
or since firefox sets the window title to the page title:
```

wmctrl -a 'Bringing window to front with Bash'

```

---

### Post by lavinog on 2008-09-28
Exactly what I was looking for. Thank You.

---

