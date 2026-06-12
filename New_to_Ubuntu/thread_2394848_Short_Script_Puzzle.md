---
title: "Short Script Puzzle"
date: 2018-06-22
forum: New to Ubuntu
---

### Post by electrosteam on 2018-06-22
Trying to write a short script to capture a screen window using scrot launched via a [DeskTop Entry] icon on the desktop.

The following works fine from the command line in terminal:
```

   scrot -s /home/john/Pictures/desktop.jpg

```

]The following does not work in a script:
```

   #!/bin/bash
   scrot -s /home/john/Pictures/desktop.jpg

```

Tried all sorts of variations and did some searching, but it puzzles me.
As far as I know, PATH and Permissions are correct.
The command line version waits for at least a minute for the cursor to define the required window.
The script takes several seconds to terminate, then nothing.
Very similar scripts to map keyboard keys work fine.

What am I doing wrong ?
John.

---

### Post by &amp;KyT$0P# on 2018-06-22
[This]("https://bbs.archlinux.org/viewtopic.php?pid=1113911#p1113911") fixes the problem for me -
```
[Desktop Entry]
Type=Application
Name=screen shot
Comment=Capture a screen window
Exec=sh -c 'sleep 0.1;scrot -s /home/john/Pictures/desktop.jpg'
Icon=camera-photo
Terminal=false
StartupNotify=false
```

---

### Post by electrosteam on 2018-06-22
halogen2,
Thanks for the code, it works a treat.
Now I have to understand how it works, including following up the reference to an Arch forum - thanks.
John

---

### Post by rickdiaz on 2018-07-10
> **electrosteam said:**
> halogen2,
Thanks for the code, it works a treat.
Now I have to understand how it works, including following up the reference to an Arch forum - thanks.
John
Great!!

---

### Post by Crafty Kisses on 2018-07-10
Heh, brings back memories for me trying to find it one week like 5 years ago. Thanks for this, was looking for something similar last week!

---

