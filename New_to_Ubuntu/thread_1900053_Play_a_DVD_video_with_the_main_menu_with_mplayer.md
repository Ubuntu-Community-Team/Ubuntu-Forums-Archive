---
title: "Play a DVD video with the main menu with mplayer?"
date: 2011-12-25
forum: New to Ubuntu
---

### Post by honeybear on 2011-12-25
Hello,

I would like to play a DVD video with the main menu with mplayer.

this command launch it directly and play it wihtout men u :( 
>  mplayer -cdrom-device /dev/scd0  dvd://1 -fs



thx

---

### Post by BC59 on 2011-12-25
Did you follow the instructions from here?
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by honeybear on 2011-12-25
> **BC59 said:**
> Did you follow the instructions from here?
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

the region is okay but dvd not playing the menu

---

### Post by honeybear on 2011-12-25
SOLVED: 

```
mplayer -cdrom-device /dev/scd0  dvdnav:// -fs
```

---

