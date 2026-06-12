---
title: "monitor a folder &amp; exec command"
date: 2010-03-21
forum: Programming Talk
---

### Post by kerry_s on 2010-03-21
hey all,
i've got a headache & can't think straight, so i hope you don't mind if i milk you guys a little.

my friends asked me if i could do a little trash notification for him for lxde, i told him i'll see what i can do.

the part i'm locked up on is the monitoring of $Home/.local/share/Trash/files for new items.

question: **what is the best way to monitor this folder & execute the command when there are new items without impacting the low computer resources?**

i'v got the part i want to run, this is what i want it to run in the script:

```

clicked=`zenity --notification --window-icon="/usr/share/icons/gnome/scalable/status/user-trash-full.svg" --text=" `gvfs-ls trash:///` " ;echo "clicked"`
if [$clicked ]; then
 pcmanfm $HOME/.local/share/Trash/files
fi

```


thanks for the help, i'm going to take a nap. :lolflag:

---

### Post by falconindy on 2010-03-21
use inotifywait to monitor a directory for file changes. It's event based, so its low overhead.

---

### Post by kerry_s on 2010-03-21
> **falconindy said:**
> use inotifywait to monitor a directory for file changes. It's event based, so its low overhead.

thanks i'll take a look, would require inotify-tools to be installed, so i'll need to check for that in the script.

---

### Post by kerry_s on 2010-03-21
i'm almost there, but for some reason it's not working.
this is what i got:

```

#!/bin/bash
#
# created for Lubuntu 10.04 on 3/21/2010
# created to fill a need, do with it as you please
#
# make sure you have gvfs-bin if you wish to see the trash items in tool tip.
###

dir=$HOME/.local/share/Trash/files
test=`gvfs-info trash:/// | grep trash::item-count:`

if [ "$test" = "trash::item-count: 0" ]; then
 sleep 10 ;exec $HOME/bin/trash.sh
else
  zenity --notification --window-icon="/usr/share/icons/gnome/scalable/status/user-trash-full.svg" --text=" `gvfs-ls trash:///` " ;pcmanfm $dir ;sleep 10 ;exec $HOME/bin/trash.sh
fi

exit 0


```
(i'll adjust the sleep later)

for some reason the script is skipping the "sleep 10 ;exec $HOME/bin/trash.sh" part & running the zenity line, even though the "gvfs-info trash:/// | grep trash::item-count:" is returning "trash::item-count: 0". 
any ideas?

---

### Post by Hellkeepa on 2010-03-21
HELLo!

Now, I'm by no means a Bash expert, but isn't one supposed to use "-e" to check for equality between two strings? Try replacing that single equals sign with "-e", if that doesn't work, try with two equal signs. ;-)

Happy codin'!

---

### Post by kerry_s on 2010-03-21
> **Hellkeepa said:**
> HELLo!

Now, I'm by no means a Bash expert, but isn't one supposed to use "-e" to check for equality between two strings? Try replacing that single equals sign with "-e", if that doesn't work, try with two equal signs. ;-)

Happy codin'!

nope, that don't work gives "./trash.sh: line 14: [: -e: binary operator expected"

"=" & "==" is the same, ones just strict posix.

i cleaned up the script, so easier to modify:

```

#!/bin/bash
#
# created for Lubuntu 10.04 on 3/21/2010
# created to fill a need, do with it as you please
#
# make sure you have gvfs-bin if you wish to see the trash items in tool tip.
###

script=$HOME/bin/trash.sh
icon=/usr/share/icons/gnome/scalable/status/user-trash-full.svg
dir=$HOME/.local/share/Trash/files
test=`gvfs-info trash:/// | grep trash::item-count:`

if [ "$test" = "trash::item-count: 0" ]; then
 sleep 10 ;
 exec $script
else
  zenity --notification --window-icon="$icon" --text=" `gvfs-ls trash:///` " ;
  pcmanfm $dir ;
  sleep 10 ; 
  exec $script
fi

exit 0


```

---

### Post by falconindy on 2010-03-21
> **kerry_s said:**
> nope, that don't work gives "./trash.sh: line 14: [: -e: binary operator expected"

"=" & "==" is the same, ones just strict posix.

i cleaned up the script, so easier to modify:


You've already grepped once, there's no need to do it once and then check for equality (grep gives you that). Also, if you declare a Bash shebang, script like you mean it.

Did some cleanup for you. I can't test it however as I'm not using gvfs, or zenity, or gnome.

```

#!/bin/bash
#
# created for Lubuntu 10.04 on 3/21/2010
# created to fill a need, do with it as you please
#
# make sure you have gvfs-bin if you wish to see the trash items in tool tip.
###

icon=/usr/share/icons/gnome/scalable/status/user-trash-full.svg
dir=$HOME/.local/share/Trash/files

while true; do
  [[ $(gvfs-info trash:/// | grep 'trash::item-count: 0') ]] || {
    zenity --notification --window-icon="$icon" --text=" $(gvfs-ls trash:///) ";
    pcmanfm $dir;
  }
  sleep 10
done

```

---

### Post by kerry_s on 2010-03-21
> **falconindy said:**
> You've already grepped once, there's no need to do it once and then check for equality (grep gives you that). Also, if you declare a Bash shebang, script like you mean it.

Did some cleanup for you. I can't test it however as I'm not using gvfs, or zenity, or gnome.

```

#!/bin/bash
#
# created for Lubuntu 10.04 on 3/21/2010
# created to fill a need, do with it as you please
#
# make sure you have gvfs-bin if you wish to see the trash items in tool tip.
###

icon=/usr/share/icons/gnome/scalable/status/user-trash-full.svg
dir=$HOME/.local/share/Trash/files

while true; do
  [[ $(gvfs-info trash:/// | grep 'trash::item-count: 0') ]] || {
    zenity --notification --window-icon="$icon" --text=" $(gvfs-ls trash:///) ";
    pcmanfm $dir;
  }
  sleep 10
done

```

thank you!!!! that works perfectly!

do i have your permission to share this & post it here>
[http://ubuntuforums.org/showthread.php?p=9005574#post9005574](http://ubuntuforums.org/showthread.php?p=9005574#post9005574)

for other lxde users?

```

#!/bin/bash
#
# created for Lubuntu 10.04 on 3/21/2010
# by falconindy @ ubuntu forums
#
# make sure you have gvfs-bin installed.
###

icon=/usr/share/icons/gnome/scalable/status/user-trash-full.svg
dir=$HOME/.local/share/Trash/files

while true; do
  [[ $(gvfs-info trash:/// | grep 'trash::item-count: 0') ]] || {
    zenity --notification --window-icon="$icon" --text=" $(gvfs-ls trash:///) ";
    pcmanfm $dir;
  }
  sleep 10
done


```

---

### Post by falconindy on 2010-03-21
> **kerry_s said:**
> do i have your permission to share this & post it here>
[http://ubuntuforums.org/showthread.php?p=9005574#post9005574](http://ubuntuforums.org/showthread.php?p=9005574#post9005574)

for other lxde users?
Eh, go for it. You wrote it as far as I'm concerned.

---

### Post by kerry_s on 2010-03-21
> **falconindy said:**
> Eh, go for it. You wrote it as far as I'm concerned.

i'm going to leave your name on it.

---

