---
title: "Bash: Desktop path variable in Gutsy"
date: 2007-11-05
forum: Programming Talk
---

### Post by Yuzem on 2007-11-05
Someone told me that since Gutsy his Desktop folders is called Bureau. I think that Bureau is French for Desktop.
The problem is that my [script]("http://ubuntuforums.org/showthread.php?p=3713560") does not work correctly any more for him.

This is what I use to get the desktop folder:
```
$HOME/Desktop
```
...but it doesn't work for everybody on Gutsy.

Is there a variable for the Desktop?

---

### Post by duff on 2007-11-05
run ```
# xdg-user-dir DESKTOP
```

---

### Post by Yuzem on 2007-11-05
Thanks for the answer but it doesn't work:
```
azd@asd:~$ xdg-user-dir DESKTOP
bash: xdg-user-dir: command not found
```

---

### Post by alex_o on 2009-08-04
xdg-user-dir desktop
will tell you $HOME... wierd
try this...
#!/bin/bash
if [ -e $HOME/Desktop ]; then
DESKTOP=$HOME/Desktop
else
if [ -e $HOME/Bureau ]; then
DESKTOP=$HOME/Bureau
else
echo "i cant find your Desktop, please type it"
fi
fi
echo $DESKTOP
and then use $DESKTOP to locate the desktop :D

---

### Post by geirha on 2009-08-04
If you don't have the xdg-user-dir command, you can still find the right one.

```
#!/bin/sh

: ${XDG_CONFIG_HOME:=~/.config}
[ -f "${XDG_CONFIG_HOME}/user-dirs.dirs" ] && . "${XDG_CONFIG_HOME}/user-dirs.dirs"

desktop_dir="${XDG_DESKTOP_DIR:-~/Desktop}"
echo "$desktop_dir"

```

See [http://mywiki.wooledge.org/BashFAQ/073](http://mywiki.wooledge.org/BashFAQ/073) for information on the "${parameter:-...}" magic

Look inside ~/.config/user-dirs.dirs to see what other localized dirs there may be.

EDIT: Ehrm. This thread is from 2007

---

