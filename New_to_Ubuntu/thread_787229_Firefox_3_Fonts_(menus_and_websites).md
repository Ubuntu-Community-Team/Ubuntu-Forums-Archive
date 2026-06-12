---
title: "Firefox 3 Fonts (menus and websites)"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by shanepardue on 2008-05-08
I've noticed with beta builds of Firefox where the menus and toolbars don't take on the subpixel rendering they usually do. Anytime I download a build straight from Mozilla as opposed to through the repos, the problem occurs.

Thanks for any help!

---

### Post by shanepardue on 2008-05-13
Anyone running Firefox trunk would know what I'm talking about. It's a common issue, surprised I can't find anything on it.

---

### Post by shanepardue on 2008-06-16
This problem has come to haunt me again when I tried to run the Flock beta browser. 
It has to do with Firefox builds missing a particular attribute that renders fonts 
smoother.

Any ideas?

---

### Post by st33med on 2008-06-16
Um... Not sure what you are talking about, but, whatever it is, it belongs more to the Firefox forums.

[http://support.mozilla.com/en-US/kb/Support+Website+Forums]("http://support.mozilla.com/en-US/kb/Support+Website+Forums")

Not that we don't want to help, its just that that problem is more specific for those forums.

PS: My guess is that you need the Ubuntu plugin for Firefox to render correctly, but, I am not sure...

---

### Post by jordanmthomas on 2008-06-16
I know what you're talking about and that's why I build it myself.
This line in mozconfig makes fonts much better for me:
```
ac_add_options --enable-system-cairo
```

---

### Post by shanepardue on 2008-06-21
> **jordanmthomas said:**
> I know what you're talking about and that's why I build it myself.
This line in mozconfig makes fonts much better for me:
```
ac_add_options --enable-system-cairo
```
So Cairo must be the issue. I wonder why they don't build it with Cairo by default!

---

