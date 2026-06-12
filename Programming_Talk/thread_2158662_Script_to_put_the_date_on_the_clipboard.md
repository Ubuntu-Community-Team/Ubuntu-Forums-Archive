---
title: "Script to put the date on the clipboard"
date: 2013-06-30
forum: Programming Talk
---

### Post by GrouchyGaijin on 2013-06-30
Hi Guys,

I've started using Scribes quite a bit.  I really like it, but can't seem to find an option to insert the current date into a document.
(OK I could just type the date, but where is the fun in that?)

Anyway, I've come up with a _*very ugly*_ work around.

```


#!/bin/bash
now=$(date +"%d-%b-%Y")
echo $now > ~/scripts/xclip-scripts/current_date
xclip -in -selection c ~/scripts/xclip-scripts/current_date
xdotool key ctrl+v


```
I have the script mapped to ctrl+alt+D

This works, but I'm sure there are many better ways to do this.
Could someone clue me in to a more succinct way of doing this?

---

### Post by Vaphell on 2013-06-30
your very ugly workaround can be reduced to a less ugly workaround, without temporary files ;-)
```
date +"%d-%b-%Y" | xsel -bi
xdotool key ctrl+v
```

---

### Post by sudodus on 2013-06-30
Great tool to get date into strings! Please, could it be made available as marked to be pasted as middle-click too?

---

### Post by GrouchyGaijin on 2013-06-30
Thanks man!
I've picked up a bunch of tips from you!

---

### Post by ofnuts on 2013-06-30
In KDE, the clock in the taskbar can copy the date/time to the clipboard in various formats. Check if your clock couldn't do the same by any chance (right-click menu).

---

### Post by GrouchyGaijin on 2013-06-30
> **ofnuts said:**
> In KDE, the clock in the taskbar can copy the date/time to the clipboard in various formats. Check if your clock couldn't do the same by any chance (right-click menu).

Bummer - the Unity clock doesn't seem to be able to do that.

---

### Post by Vaphell on 2013-06-30
> **sudodus said:**
> Great tool to get date into strings! Please, could it be made available as marked to be pasted as middle-click too?

xsel -**p**i will do that. there are 3 buffers, primary (middleclick) -p, secondary (?) -s and clipboard (ctrl+v) -b

if the ending \n is not needed then wrapping the command and passing its output with printf should work
```
printf "$( date )" | xsel -pi
```
or **tr -d '\n'**
```
date | tr -d '\n' | xsel -pi
```

---

### Post by sudodus on 2013-06-30
Thank you :-)

---

