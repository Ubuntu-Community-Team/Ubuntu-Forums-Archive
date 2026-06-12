---
title: "[SOLVED] GIMP error"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-10-20
I just finished a download this weekend of updated Ubuntu files. When I finished and went to edit a photo in Gimp, I received this gimp error message.

[COLOR="Blue"]Libgimp version mismatch!

The GIMP binary cannot run with a libgimp version
other than its own. This is GIMP 2.4.2, but the
libgimp version is 2.4.6.

Maybe you have GIMP versions in both /usr and /usr/local ?[/COLOR]

How & where do I correct it ???

---

### Post by lesergi on 2008-10-20
Hi!

I think libgimp and gimp-data packages does not have the same version.

Try this:

```
sudo apt-get update && sudo apt-get remove libgimp2.0 gimp-data && sudo apt-get install gimp ubuntu-desktop
```

---

### Post by CoCoKnots on 2008-10-20
Your English in fine. Your terminal line worked great. Thank you. When I rebooted my system, it generated 18 updates including gimp files. Everything works fine now. Thanks Again, Cal

---

