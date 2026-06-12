---
title: "[SOLVED] Eve online and conky"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by shodan on 2008-08-28
I downloaded conky 1.6.1 but i can't get function
eve api_userid api_key character_id to work
I compiled it with "--enable-eve" option.

Configure:
```
 ./configure --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --datadir=/usr/share --sysconfdir=/etc --localstatedir=/var/lib --enable-xft --enable-double-buffer --enable-own-window --enable-x11 --enable-eve

```

Summary i got:

```
 * General:
  math:             yes
  hddtemp:          yes
  portmon:          yes
  RSS:              no
  wireless:         no
  SMAPI:            no
  nvidia:           no
  eve-online:       yes

```

-------------

Should be:
```
 ./configure --enable-xft --enable-double-buffer --enable-own-window --enable-x11 --enable-eve

```

---

