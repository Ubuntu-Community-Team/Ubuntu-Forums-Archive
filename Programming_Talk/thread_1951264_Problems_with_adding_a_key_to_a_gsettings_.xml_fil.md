---
title: "Problems with adding a key to a gsettings .xml file"
date: 2012-04-02
forum: Programming Talk
---

### Post by sacridex on 2012-04-02
Hello,

im trying to add a key to a gsettings file. I have added the key to the specific .xml file in /usr/share/glib-2.0/schemas and i ran glib-compile-schemas on that folder.

When i open the dconf-editor, the key with the correct value is shown.
But when i want to list the keys with "gsettings list-keys name", the key is not shown at all. In addition i can (obviously) not gain access to this key via gsettings.

thx for help.

---

