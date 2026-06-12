---
title: "Add Destination To Move To List Ubuntu 12.04"
date: 2013-05-13
forum: New to Ubuntu
---

### Post by Landngroove on 2013-05-13
When I right click on a file there is a "move to" option. Is there a way to add to this move to list, such as "pictures" for example?  Thanks in advance.

---

### Post by schragge on 2013-05-14
I don't know an obvious way to *add* a folder to this list, but you can define your own context menu actions with [nautilus-actions-config-tool]("http://manpages.ubuntu.com/manpages/precise/en/man1/nautilus-actions-config-tool.1.html") from package *nautilus-actions*, or just put a simple script under *~/.gnome2/nautilus-scripts/* (yes, it's *.gnome2* even with Nautilus 3.*)

E.g. the following script will move selected files to location of your choice:
```

#!/bin/sh
[ 0 -eq $# ] && exit
dst=$(zenity --title='Where to move' --file-selection --directory) || exit
/bin/mv -- "$@" "$dst"

```
Put it into *~/.gnome2/nautilus-scripts/MoveTo*, and make it executable
```
chmod +x ~/.gnome2/nautilus-scripts/MoveTo
```
Now, when selecting one or more files in Nautilus you'll have a new context menu item **Scripts**>**MoveTo**.

Just copying files (as opposite to moving them) can be done with Nautilus D-Bus interface:
```

#!/bin/bash
mapfile -t src <<<"${NAUTILUS_SCRIPT_SELECTED_URIS%$'\n'}"
test -z "${src
[*]}" && exit
dst=$(zenity --title='Where to copy' --file-selection --directory) || exit
IFS=,
dbus-send --type=method_call --dest=org.gnome.Nautilus /org/gnome/Nautilus \
        org.gnome.Nautilus.FileOperations.CopyURIs \
                array:string:"${src
[*]//,/%2C}" string:"file://$dst"

```
Embedded newlines are URL-encoded in $NAUTILUS_SCRIPT_SELECTED_URIS as %0A, so the CopyTo script is newline-safe.

---

