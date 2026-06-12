---
title: "Automatically sorting Firefox downloads"
date: 2008-04-12
forum: Programming Talk
---

### Post by aboutblank on 2008-04-12
Let's hook into linux's inotify system to get event details about Firefox downloads to our default directory and have default actions for them!

For me....
*.torrent -> Directory watched by rtorrent so they are automatically started
*.iso -> A separate directory
*.mp3 -> Music folder
*.tar.gz or *.bz2 -> Decompressed
All others default to an "unsortable" directory

Anyone interested in helping with this project may. Code written by me may be reproduced, modified, or eaten at will. Credit would be kind though.

It's written in python. Both files below are needed. If you make some good modifications to it, send me an email. I'd love to see them.

**Big fat warning: This is so alpha it's not even funny. This program may overwrite files, delete files, or eat your mother. Don't blame me!**

Also, I did not write pyinotify but the version I used is below. You can find their website [here]("http://pyinotify.sourceforge.net/").

Questions? Comments? Feel free to email/PM me through the forum!

---

### Post by engla on 2008-04-13
Great application suggestion! I'll look at it

---

