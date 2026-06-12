---
title: "firefox 8 crashes immediately on ubuntu 11.10"
date: 2011-11-23
forum: New to Ubuntu
---

### Post by pythonscript on 2011-11-23
I'm running ubuntu 11.10 x86, and I just installed firefox 8 through the standard update channel (no PPAs) and it crashes immediately upon start. I removed the global menu addon and tried to run it in safe mode, but the same thing still occurs. I'd rather not just wait for a new update to come down; I know it's still new, but is there any way to fix this?

Thank you!

---

### Post by alphacrucis2 on 2011-11-23
What happens when you start it from the command line?

---

### Post by pythonscript on 2011-11-23
I get this set of errors:

```

(firefox:18706): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(firefox:18706): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(firefox:18706): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(firefox:18706): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(crashreporter:18720): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(crashreporter:18720): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(crashreporter:18720): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(crashreporter:18720): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

```

However, I get these same warnings every time I start any app from the terminal, and I've gotten them for every version of Ubuntu I've ever used, so I don't think they constitute a problem.

---

### Post by lovinglinux on 2011-11-24
Try to launch the profile manager and create a new profile for testing:

```
firefox -P
```

If a new profile works, then you will need to find what is causing the problem in the old profile and remove it or copy some stuff from the old profile to the new one.

---

### Post by pythonscript on 2011-11-24
I created a new profile and re-installed the extensions I previously had, one by one, and everything is working now. This is strange to me because I had only installed three extensions (NoScript, AdBlockPlus, and HTTPS Everywhere) and had not changed anything else about the browser (home page, privacy, etc.). This was a fresh install of Ubuntu. Maybe the update corrupted the default profile somehow.

---

### Post by lovinglinux on 2011-11-24
> **pythonscript said:**
> I created a new profile and re-installed the extensions I previously had, one by one, and everything is working now. This is strange to me because I had only installed three extensions (NoScript, AdBlockPlus, and HTTPS Everywhere) and had not changed anything else about the browser (home page, privacy, etc.). This was a fresh install of Ubuntu. Maybe the update corrupted the default profile somehow.

Yes, most likely to be a corrupted file in your profile. Let me know if you need to recover something else, like passwords or settings.

---

### Post by fcarramate on 2011-11-25
hi,

found myself in trouble too.

check this link from mozilla
[http://support.mozilla.com/en-US/questions/894141]("http://support.mozilla.com/en-US/questions/894141")

---

### Post by lovinglinux on 2011-11-26
> **fcarramate said:**
> hi,

found myself in trouble too.

check this link from mozilla
[http://support.mozilla.com/en-US/questions/894141]("http://support.mozilla.com/en-US/questions/894141")

Are you still in trouble?

---

