---
title: "moving from dialog to zenity"
date: 2009-11-08
forum: Programming Talk
---

### Post by kainalu on 2009-11-08
Hey guys,

having trouble moving from dialog to zenity for my scripts. Specifically (for now) the bug Im having is that I am used to doing dialog like this:


```
fgfs --show-aircraft >~/Desktop/dialog.ans

dialog --no-shadow \
   --backtitle "Flightgear setup script" \
   --title "Available aircraft" \
   --textbox ~/Desktop/dialog.ans 25 99
rm -f ~/Desktop/dialog.ans # don't litter !
```


but Zenity seems to be a lot more picky about taking text files as input. Im trying this:


```
fgfs --show-aircraft >~/Desktop/dialog.ans

zenity --title "Available aircraft" \
   --height 400 --width 500 \
   --info ~/Desktop/dialog.ans

rm -f ~/Desktop/dialog.ans # don't litter !
```

This gives me a weird error message along the lines of "all updates are complete" instead of properly drawing the box with the text. This is part of a large script that wraps FlightGear that Im writing, as I have given up on trying to get FGRun to compile for Ubuntu. If needed, Ill post the whole dialog script up here, but its not quite done yet and is kinda "ugly".

---

### Post by dwhitney67 on 2009-11-08
Try something like:
```

zenity --title "Available aircraft" \
   --height 400 --width 500 \
   --info **--text** **"`cat ~/Desktop/dialog.ans`"**

```

---

### Post by kainalu on 2009-11-09
Thanks, That fixed the zenity error I was having!



{Moved somewhat unrelated second question to new thread}

---

