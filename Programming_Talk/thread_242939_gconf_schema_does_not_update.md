---
title: "gconf schema does not update"
date: 2006-08-24
forum: Programming Talk
---

### Post by G|N| on 2006-08-24
i installed a gconf schema like this:
```

GCONF_CONFIG_SOURCE=`gconftool-2 --get-default-source`
sudo gconftool-2 --makefile-install-rule 'specto.schemas'

```
this is the output:
```
Resolved address "xml:merged:/etc/gconf/gconf.xml.defaults" to a writable configuration source at position 0
Attached schema `/schemas/apps/specto/preferences/debug_mode' to key `/apps/specto/preferences/debug_mode'
Installed schema `/schemas/apps/specto/preferences/debug_mode' for locale `C'

```
so gconf installs the schema, but when i make a change in the schema-file and i install the schema again, the values are not updated.

when i print $GCONF_CONFIG_SOURCE, i get this error:
```

Warning: unknown mime-type for "xml:merged:/etc/gconf/gconf.xml.defaults" -- using "application/*"
Error: no such file "xml:merged:/etc/gconf/gconf.xml.defaults"

```
so could this be the problem and how do i solve it?

---

