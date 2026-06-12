---
title: "patch - seems to do nothing"
date: 2012-05-11
forum: New to Ubuntu
---

### Post by wlraider70 on 2012-05-11
I am trying to use a patch however when I ...

```


server@hyrule:/etc/pptp-eap/ppp-2.4.5$ sudo patch -p1 /etc/pptp-eap/ppp-2.4.5/ppp-2.4.5-eaptls-mppe-0.993.patch

```

it just sits and show no output at all.

verbose give me this and back to start

```

server@hyrule:/etc/pptp-eap/ppp-2.4.5$ sudo patch -p1 -vvv /etc/pptp-eap/ppp-2.4.5/ppp-2.4.5-eaptls-mppe-0.993.patch
patch 2.6
Copyright (C) 1988 Larry Wall
Copyright (C) 2003 Free Software Foundation, Inc.

This program comes with NO WARRANTY, to the extent permitted by law.
You may redistribute copies of this program
under the terms of the GNU General Public License.
For more information about these matters, see the file named COPYING.

written by Larry Wall and Paul Eggert
server@hyrule:/etc/pptp-eap/ppp-2.4.5$ 


```

---

### Post by andrew.46 on 2012-05-11
You have omitted the **[COLOR="Red"]<[/COLOR]** sign:

```

patch -pnum **[COLOR="Red"]<[/COLOR]**patchfile

```

---

### Post by wlraider70 on 2012-05-11
Thanks

---

