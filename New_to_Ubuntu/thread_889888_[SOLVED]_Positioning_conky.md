---
title: "[SOLVED] Positioning conky?"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-08-14
IS there a way to Position Conky in a specific place on the desktop? I know you can edit the ".conkyrc" file but I can only see options for "top" or bottom_left" I want to be able to position it exactly over a part of my wallpaper:)

Thanks in advance!:KS

***edit***

never mind i fpund a way by adding
```

gap_x 400
gap_y 35
```

to my conky settings file

---

### Post by blazercist on 2008-08-14
you can do that with gap_x and gap_y in pixels.  so set position say top_left and the gap_x is how far to the right in pixels conky will move from the edge of the screen and gap_y is how far it will move from the top of the screen.

---

### Post by opcahrles on 2013-04-16
Oh i did mine and it works fine for me
go to your home directory and unhide all files by pressing Ctrl + H, scroll and look for .conkyrc
open this file and edit where you find the alignment 

[I]alignment tl
gab_x -10     [SIZE=1] (replace 0 with what you think is better form -5 to 150 may be)[/SIZE]
gab_y 35    [/I][SIZE=1]*(replace 35 with what you think is better form -5 to 150 may be)*[/SIZE]

use tl for left alignment, tr for right alignment.

save the file and start conky.
you can be adjusting the figures until you are happy wit it.

This picture is of my screen and with the above configurations.

---

### Post by overdrank on 2013-04-16
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

