---
title: "desktop shortcuts to folders"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by ayu on 2008-06-06
Hi,
I have shortcuts to Computer and Home on my desktop (I think I enabled them from nautilus options somewhere), and a couple more ".desktop" files linking to other folders on my computer (launcher with command: nautilus /target/folder). In Feisty and Gutsy Nautilus was happy with the names " " (1 space), "  " (2 spaces), 3 spaces, etc, so I only have the icons visible for those shortcuts. However, after I upgraded to Hardy, it insists on having the words computer and home displayed, and calls the other shortcuts "alacarte-made.desktop", "alacarte-made (copy).desktop" etc. Any ways to get my textless shortcuts back? 
Thanks!

edit: ok, it finally seems that my renames are kept after restarting. But I still can't get a blank character as the file name. Are there any unicode characters that I can input instead?

---

### Post by nhandler on 2008-06-14
I just tested this on my Intrepid machine, and I was able to successfully rename a shortcut to " " (space). Have you tried renaming the shortcut from the terminal? You can use the 'mv' command to rename a file.
```
mv "/path/to/old/file" "/path/to/new/file"
```

The "s are needed because you are going to have a space in the filename.

---

