---
title: "totem/vlc"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by rbee on 2008-10-24
how do i get vlc to play instead of totem?

---

### Post by cairnzi on 2008-10-24
right click file you want to play or watch and set vlc as default, or right click and open with....... vlc.

---

### Post by WRDN on 2008-10-24
To open a file(s) with VLC, right click on the file, place the cursor over "Open With" and choose VLC media player" if it is listed. Otherwise, select "Open with other application" and select VLC from the list.
To make this change permanent, right click on the file, select Properties then click the Open With tab, and find and select VLC.
Once you have done this, VLC will be used for all files of the same format.

I use VLC for all my media, but I run a script when opening the file.
This is because VLC opens multiple instances of the program playing various files, and this can be annoying.

I use the following .sh script:

```
#!/bin/bash

kill -TERM $(pidof vlc)

vlc "$1"
```

Save this in a file called "vlc.sh" (or any name you wish), right click on the file, select Properties then the Permissions tab, and check the "Allow executing file as program" check box. Now, instead of selecting VLC from the Open With list, click "Add", "Use Custom Command" and select Browse. Find the file you saved, and open VLC with it instead.

---

