---
title: "Gconf script"
date: 2015-10-29
forum: New to Ubuntu
---

### Post by Michael_Honaker on 2015-10-29
I want to edit gconf with a script. Does anyone have any ideas on how to do this? any help would be appreciated

---

### Post by sandyd on 2015-10-29
You will want to use gconftool to do this.

See [http://manpages.ubuntu.com/manpages/trusty/man1/gconftool-2.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/gconftool-2.1.html)

You probably want to use gconf-editor to view the path, then use the --set/--get/--unset/etc flags to manage the value.

Example:
```

gconftool-2 --get /apps/xxx/xxx
``` where you replace the part after "--get" with the path to the value you are looking to get.

---

### Post by CantankRus on 2015-10-29
Here's a couple of old scripts I once used to toggle gconf settings.
 ```
#!/bin/bash

hide="gconftool-2 --set /apps/nautilus/desktop/volumes_visible --type bool FALSE"
show="gconftool-2 --set /apps/nautilus/desktop/volumes_visible --type bool TRUE"
test=$( gconftool-2 --get /apps/nautilus/desktop/volumes_visible )

if [ $test = "true" ]; then
	eval $hide
else
	eval $show
fi
```

```
#!/bin/bash

STATUS=$(gconftool-2 --get /apps/nautilus/preferences/desktop_font)

if [ "$STATUS" == "Ubuntu 11" ]; then
	gconftool-2 --set /apps/nautilus/preferences/desktop_font  --type string "Ubuntu 8"
        gconftool-2 --set /apps/metacity/general/titlebar_font  --type string "Ubuntu Bold 6"
        gconftool-2 --set /desktop/gnome/interface/document_font_name --type string "Sans 8"
        gconftool-2 --set /desktop/gnome/interface/font_name --type string "Ubuntu 8"
        gconftool-2 --set /desktop/gnome/interface/monospace_font_name --type string "Monospace 7"
else
	gconftool-2 --set /apps/nautilus/preferences/desktop_font  --type string "Ubuntu 11"
        gconftool-2 --set /apps/metacity/general/titlebar_font  --type string "Ubuntu Bold 9"
        gconftool-2 --set /desktop/gnome/interface/document_font_name --type string "Sans 11"
        gconftool-2 --set /desktop/gnome/interface/font_name --type string "Ubuntu 11"
        gconftool-2 --set /desktop/gnome/interface/monospace_font_name --type string "Monospace 10"
fi
```

If you mean **dconf** then you can use gsettings or dconf.
```
man gsettings
man dconf
```

---

