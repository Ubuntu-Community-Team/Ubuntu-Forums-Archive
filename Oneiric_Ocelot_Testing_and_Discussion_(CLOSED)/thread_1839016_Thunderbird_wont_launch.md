---
title: "Thunderbird wont launch"
date: 2011-09-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Kate the Enthusiast on 2011-09-04
Dear all, 

subj basically. I have installed-reinstalled it several times, rebooted. What am I to do?? 

Thunderbird has never launched after upgrade from 11.04 to 11.10 yesterday. PLeaSe, help. I am about to re-install the whole system and it is very sad as I need to make the drivers right all over again.

So if I type 
> thunderbird

I get the following:
 

(thunderbird-bin:3542): GLib-GObject-WARNING **: cannot register existing type `DbusmenuMenuitem'

(thunderbird-bin:3542): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(thunderbird-bin:3542): GLib-GObject-CRITICAL **: g_param_spec_object: assertion `g_type_is_a (object_type, G_TYPE_OBJECT)' failed

(thunderbird-bin:3542): GLib-GObject-CRITICAL **: g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed

---

### Post by miguelpires on 2011-09-05
Hello,
I upgrade yesterday from 11.04 to 11.10 in one of my computers. After some problems anda bugs i reported, i can't use Thunderbird 7.
I re-install the program and he don't lunch, but in the "system monitor" i see that 2 process are start. Have someone the same problem and a fix?
Best Regard's
Miguel Pires

---

### Post by jenigmat429 on 2011-09-05
I'm getting the same error as you are. I've tried deleting and recreating the profiles, using thunderbird -P, but no luck.

---

### Post by chrisccoulson on 2011-09-05
Uninstalling libunity4 will fix that, although I've just uploaded a proper fix for it

---

### Post by mc4man on 2011-09-05
> **chrisccoulson said:**
> Uninstalling libunity4 will fix that, although I've just uploaded a proper fix for it

Think the builds need a little help..

---

### Post by Harry33 on 2011-09-06
See here:

[http://ubuntuforums.org/showthread.php?t=1839016](http://ubuntuforums.org/showthread.php?t=1839016)

---

### Post by cariboo on 2011-09-06
Merged two threads on the same subject. Please do a search before creating new threads.

---

