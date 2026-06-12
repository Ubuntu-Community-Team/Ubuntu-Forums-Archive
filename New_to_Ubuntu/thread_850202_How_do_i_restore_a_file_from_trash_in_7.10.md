---
title: "How do i restore a file from trash in 7.10 ?"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by sharks on 2008-07-05
How do i restore a file from trash in 7.10 ? i know i cant. can i import this feature from 8.04 to use in 7.10?

---

### Post by scragar on 2008-07-05
trash is just a folder within your home folder, so just open your home folder, navigate to .trash and move the file out to anywhere you want.

---

### Post by Victormd on 2008-07-05
When a file is sent to the trash, it's stored in a hidden folder in your home directory
> cd ~/.Trash
If you haven't emptied your trash can, then the files should be there. If you deleted a file from an external drive or extra partition, then the .Trash directory will be in the root of that device.

---

### Post by sayakb on 2008-07-05
> **Victormd said:**
> When a file is sent to the trash, it's stored in a hidden folder in your home directory

If you haven't emptied your trash can, then the files should be there. If you deleted a file from an external drive or extra partition, then the .Trash directory will be in the root of that device.

The trash folder is no longer ~/.Trash but [B]~/.local/share/Trash/files
[/B]
@OP
As scragar said, just **Cut** the file from the trash and **Paste** it anywhere.

---

### Post by Elfy on 2008-07-05
> The trash folder is no longer ~/.Trash but ~/.local/share/Trash/filesIn Hardy - the op is running Gutsy 7.10 :)

---

### Post by sayakb on 2008-07-05
Ouch.. point taken. Missed the **topic**? .. duh

---

### Post by Elfy on 2008-07-05
Yea - :) - I do it all the time, got it from my mum - she can read a 2 page letter and make it mean what she want's and then moan about the content, another 20 years and I too will be an oap 

As an aside - while the prefix thing has saved a lot of heartache - why open a xubuntu question if you have no idea - but I do wish it could refer to versions instead.

---

### Post by nowshining on 2008-07-05
in kde - u just press ctrl+z on the desktop to restore it. :) or go into the trash can and right-click and click restore.

---

