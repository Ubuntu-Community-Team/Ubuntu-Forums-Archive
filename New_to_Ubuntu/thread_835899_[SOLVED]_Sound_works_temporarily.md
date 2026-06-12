---
title: "[SOLVED] Sound works temporarily"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by Nazty_Nayt on 2008-06-20
Ok, I just installed Ubuntu yesterday, and I think my sound is messed up.  When I first boot up, it gives me the welcome sound, I can listen to an MP3, but when I pull up firefox, and go to sites like youtube the videos only play for the first 2 seconds then freeze, then after that sound does not work at all.  If I close the browser, and go to listen to an mp3 again, it plays, but no sound!?  :confused:  I'm at a loss on this one.

---

### Post by iaculallad on 2008-06-20
Install the libflashsupport file, that would probably solve your youtube sound problems:

```
sudo apt-get install libflashsupport
```

---

### Post by Nazty_Nayt on 2008-06-20
> **iaculallad said:**
> Install the libflashsupport file, that would probably solve your youtube sound problems:

```
sudo apt-get install libflashsupport
```

Ok, that seemed to take care of the issue with the sound, and the videos are playing now at least.  I'm still having certain issues with some sites that are heavy on flash.  But I'll look around for some options/solutions.  Thanks for the help

:guitar:

---

### Post by iaculallad on 2008-06-20
For the Flash video issue, try installing the GNU Flash player [GNASH]("http://www.gnu.org/software/gnash/") instead of using the proprietary Adobe Flash.

---

### Post by Nazty_Nayt on 2008-06-20
I added GNASH, but it's the same thing, alot of flash sites just don't display.

---

