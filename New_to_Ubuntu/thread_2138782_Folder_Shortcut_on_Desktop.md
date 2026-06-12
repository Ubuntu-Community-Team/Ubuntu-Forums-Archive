---
title: "Folder Shortcut on Desktop"
date: 2013-04-25
forum: New to Ubuntu
---

### Post by Hishighness on 2013-04-25
Hey all, I've been trying to figure out how to do this but have been unable so far. When I right click on folders there's no shortcut button and the Make Link button is greyed out. I'd just like to be able to make shortcuts to different folders on my desktop if possible.

I'm running 12.10 with Unity.

Thanks for your time,
H2

---

### Post by howefield on 2013-04-25
Try opening a terminal and typing

```
cd Desktop/
```

then

```
ln -s path_to_folder
```

substituting path_to_folder with the path to your folder.

---

### Post by Hishighness on 2013-04-25
Ah, there we go. Thank you very kindly. :D

---

