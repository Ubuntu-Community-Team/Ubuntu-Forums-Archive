---
title: "Auto-login and start slideshow"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by 0m3ns on 2012-08-21
I have an Acer Revo driving an LCD TV. It displays a presentation in libre3 which cycles indefinitely. 

We sometimes have powercuts. The machine boots up after power is restored but then stops at the login screen. I need it to boot and load/start the presentation automatically. 

I think I can get the autologin to work fine (think it's just a tickbox opion) but how can I get the presentation to automatically load and play?

---

### Post by ajgreeny on 2012-08-21
Simply add it to the startup applications list.  I don't know where that is in unity, but use dash, and type **startup** and it should appear.

In the command box for the app use```
 libreoffice --impress /path/to/file
```

---

### Post by newb85 on 2012-08-21
I don't think that command will make the presentation start playing automatically.  Try this instead.
```
libreoffice --show /path/to/file
```

---

