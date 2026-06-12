---
title: "nautilus starting errors"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by taith on 2008-08-15
hey everyone :-)

got some nautilus errors when starting nautilus from terminal(sudo nautilus)... anyone know what may be going on here? and/or how to fix? nothing new(program wise) has been installed lately...

seahorse nautilus module initialized
Initializing nautilus-share extension
Segmentation fault

---

### Post by drs305 on 2008-08-15
> **taith said:**
> hey everyone :-)

got some nautilus errors when starting nautilus from terminal(sudo nautilus)... anyone know what may be going on here? 

Run graphical apps with "gksudo":
```
gksudo nautilus
```

Reserve sudo for command line only operations. It may or may not eliminate your problems, but it is a good practice regardless. Here's why:
[URL="http://www.psychocats.net/ubuntu/graphicalsudo"]
[/URL][http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

