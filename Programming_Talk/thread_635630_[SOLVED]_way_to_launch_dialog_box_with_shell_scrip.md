---
title: "[SOLVED] way to launch dialog box with shell script"
date: 2007-12-08
forum: Programming Talk
---

### Post by mridkash on 2007-12-08
Hi,
I'm making a simple file backup shell script.

I was wondering if its possible to launch a yes no message box through script and get a return value from it (yes no).
Also, it would be great if a script running in background interacts using notification popups.

is there any program which I can call through script and it shows the GUI element like,

```
showDialog --type yesno --message 'Do you want to apply'
```

---

### Post by geirha on 2007-12-09
Zenity has something close
```
if zenity --question --text="Do you want to apply?"; then
  echo "Ok, you want to apply, so I guess I'll be doing applying stuff"
else
  echo "Ok. Had to ask"
fi
```

It can put itself in the notification area too. with the --notification argument. Read the man-page and/or "zenity --help"

---

### Post by mridkash on 2007-12-10
Thanks, thats good.

---

