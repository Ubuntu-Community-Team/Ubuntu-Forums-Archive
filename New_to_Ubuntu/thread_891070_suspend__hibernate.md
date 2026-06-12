---
title: "suspend / hibernate"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by loyaleagle on 2008-08-15
Can you disable suspend and hibernate. (Also take their icons away on the dialog exit box. They do not work on my system and lock it up.

Thank,

Benoit

---

### Post by sdennie on 2008-08-15
You can.  Hit Alt-F2, type gconf-editor and then navigate to /apps/gnome-power-manager/general and unselect can_suspend and can_hibernate.

---

### Post by loyaleagle on 2008-08-15
Worked great... Thanks!!!

---

### Post by kwc01 on 2008-08-24
I've tried this and can't seem to change the setting.  The key is marked as unwritable.  I tried to "unset" the key and change it but haven't had any success, even when running gconf-editor as root.  The error says, "Can't overwrite existing read-only value: Value for '/apps/gnome-power-manager/general/can_suspend' set in a read-only source at the front of your configuration path."

Anyone know how I can change this key?

Thank you,
kwc

---

### Post by dranger92 on 2009-05-01
> **kwc01 said:**
> I've tried this and can't seem to change the setting.  The key is marked as unwritable.  I tried to "unset" the key and change it but haven't had any success, even when running gconf-editor as root.  The error says, "Can't overwrite existing read-only value: Value for '/apps/gnome-power-manager/general/can_suspend' set in a read-only source at the front of your configuration path."

Anyone know how I can change this key?

Thank you,
kwc

I too got the same problem even after using sudo gconf-editor.

---

### Post by Spiritous on 2009-05-01
And me >: /

---

### Post by TiredBird on 2009-05-09
> **sdennie said:**
> You can.  Hit Alt-F2, type gconf-editor and then navigate to /apps/gnome-power-manager/general and unselect can_suspend and can_hibernate.
They were already set that way. My problem is that the GUI doesn't seem to recognize those settings. Its not giving me the option to suspend or hibernate. (They both work fine from the CLI however.)

---

### Post by TiredBird on 2009-05-10
My problems related to suspend and hibernate have been solved thanks to the posts in these threads: [http://ubuntuforums.org/showthread.php?t=1144999]("http://ubuntuforums.org/showthread.php?t=1144999.") and [http://ubuntuforums.org/showthread.php?t=814939]("http://ubuntuforums.org/showthread.php?t=814939").

---

