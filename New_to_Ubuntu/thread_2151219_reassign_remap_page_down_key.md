---
title: "reassign remap page down key"
date: 2013-06-03
forum: New to Ubuntu
---

### Post by Kevin McCready on 2013-06-03
I want reassign or remap my supersuser key to make it a "page down" key. My shoulder op is now booked and I have a few days to finish tweaking the computer for left-handed use. Thanks to all who've helped with other tweaks to get this done!

---

### Post by MidnightGrey on 2013-06-04
the following command should do it:
```
xmodmap -e "add Next = mod4"
```

edit: sorry the command should be $ xmodmap -e "add mod4 = Next"

---

### Post by Kevin McCready on 2013-06-04
Thanks. 

Unfortunately $ xmodmap -e "add mod4 = Next" wiped out my "Page Down" key but didn't alter the behaviour of my superuser key. By SuperUser key I mean the one on the bottom row, third from the left. It's the Windows Key if using windows. 

My system is a Compaq Presario-CQ57-Notebook-PC 3.2.0-45-generic-pae #70-Ubuntu SMP Wed May 29 20:31:05 UTC 2013 i686 i686 i386 GNU/Linux

---

### Post by MidnightGrey on 2013-06-04
Haha sorry, i misread your question.
The command 'xmodmap -e "add mod4 = Next"' actually sets Page Down to act as a Super Key in addition to the Windows key.
To undo this, use this command 'xmodmap -e "remove mod4 = Next"

To set the super key (Windows Key) to act as Page Down:
1. First you must de-assign it as the super key shortcut
$ xmodmap -e "remove mod4 = Super_L"
2. Assign the super key to act as a Page Down key:
$ xmodmap -e "keycode 133 = Next"

Hope that helps.

Edit: also forgot to mention this these change are for the active x session only and will be lost after reboot. When you want to save the changes permanently you have to run the following commands after the ones above:
 
xmodmap -pke >~/.Xmodmap   (it creates a files called .Xmodmap in your home directory ~   )

  Then you have to create a file called **.xinitrc** in your home directory.
Inside .xinitrc put this in "xmodmap .Xmodmap"

---

### Post by Kevin McCready on 2013-06-04
awesome
thanks so much

---

### Post by Kevin McCready on 2013-06-05
Oops
It's stopped working. First it required a double hit to make it work. Now it's dead. Even when I repeat the commands
xmodmap -e "remove mod4 = Super_L"
xmodmap -e "keycode 133 = Next"
It doesn't work.

---

### Post by Kevin McCready on 2013-06-06
I tried rebooting whole machine. It works for a while then the superuser key is completely dead, doing nothing.

---

