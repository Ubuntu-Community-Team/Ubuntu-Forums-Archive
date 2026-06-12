---
title: "Weird compiz upgrade??"
date: 2011-08-23
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by xebian on 2011-08-23
apt-get wants to install compiz-kde + bunch of kde stuff in a pure gnome box?  Never had this before till now.:confused:

---

### Post by mc4man on 2011-08-23
You need to wait for a newer libcompizconfig0 or exclude that from your updates (should be available shortly (0.9.5.92-0ubuntu2

---

### Post by xebian on 2011-08-23
> **mc4man said:**
> You need to wait for a newer libcompizconfig0 or exclude that from your updates (should be available shortly (0.9.5.92-0ubuntu2

Still don't understand why it wants to install when compiz depends on compiz-gnome OR compiz-kde.  compiz-gnome is installed so I can't understand the need for compiz-kde when there is no kde stuff.

---

### Post by mc4man on 2011-08-23
There was a small problem with the build and it would want to remove  -  compizconfig-backend-gconf
It's been fixed so just wait till it shows

Here's the current fixed build page
[https://launchpad.net/ubuntu/+source/libcompizconfig/0.9.5.92-0ubuntu2](https://launchpad.net/ubuntu/+source/libcompizconfig/0.9.5.92-0ubuntu2)

If you want to know why  - the changelog
>  * debian/control:
    - compizconfig-backend-gconf doesn't have an epoch, use correct version
 -- Sebastien Bacher <seb128@ubuntu.com>   Tue, 23 Aug 2011 23:19:12 +0200
And the diff which makes it a bit clearer, - I added red for emphasis
> diff -Nru libcompizconfig-0.9.5.92/debian/control libcompizconfig-0.9.5.92/debian/control
--- libcompizconfig-0.9.5.92/debian/control	2011-08-23 17:41:31.000000000 +0000
+++ libcompizconfig-0.9.5.92/debian/control	2011-08-23 21:19:35.000000000 +0000
@@ -23,7 +23,7 @@
 Depends: ${shlibs:Depends}, ${misc:Depends}, 
  compiz-core, compiz-core-abiversion-${coreabiversion}
 Breaks: compiz-core (<< 1:0.9.2.1+glibmainloop3),
-        compizconfig-backend-gconf (<< [COLOR="Red"]1[/COLOR]:0.9.5.92)
+        compizconfig-backend-gconf (<< 0.9.5.92)

---

### Post by xebian on 2011-08-23
fixed already. thanks.

---

