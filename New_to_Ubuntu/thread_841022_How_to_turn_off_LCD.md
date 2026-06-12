---
title: "How to turn off LCD?"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by ToTheMax on 2008-06-26
I want to turn off my computer's LCD and keep my ubuntu working,is there any way to do it?like applications,scripts or something else.

THX

---

### Post by wolfen69 on 2008-06-26
go to system>preferences>power management and you can set the monitor to shut off after a few minutes.

---

### Post by ToTheMax on 2008-06-26
But I want to close LCD manully,how to?

---

### Post by Colin82 on 2008-06-26
If this is a laptop you should be able to configure the LCD to shut off when you shut the lid via power management.  You can set it to do a specific action when you close the lid, ie: turn of monitor, blank screen,..

---

### Post by ToTheMax on 2008-06-26
If I don't want to shut the lid,how should I do?

---

### Post by kpkeerthi on 2008-06-26
To turn off LCD (including backlight), run this command in a terminal
```

xset dpms force off

```

* This works for me (using nvidia). Not sure about other, but worth a try.

---

### Post by ToTheMax on 2008-06-26
THX,it works for me!

---

### Post by kpkeerthi on 2008-06-26
Great. You may want to bind that command to a keyboard shortcut so you can turn the LCD off with easy key presses.

---

