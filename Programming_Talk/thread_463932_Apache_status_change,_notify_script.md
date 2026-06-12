---
title: "Apache status change, notify script?"
date: 2007-06-04
forum: Programming Talk
---

### Post by ahlt on 2007-06-04
Hi

I'm trying to learn some Python, and are therefor I'm writing a small script to toggle Apache on/off. It will supply an icon in systray indicating if Apache is running or not.

I'm checking if apache is running using this command:
```

a = os.popen('pidof apache2')
b = a.read()

```

But I don't know how my script can be notified if the status of the server is changed.
For instant, if someone was to stop the server by the init.d script. How can my script be notified? I just can't run a loop of the pidof command forever:p

---

