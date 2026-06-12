---
title: "file issues"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by djrunslinux on 2008-07-11
I own and operate a online radio station and a record label.I do spend time dealing with various mp3 files, but one serious issues that I have is after moving about 15-20 files around on ubuntu, the files start giving me errors and the icon become what looks like a blank page and the only way I can resume working with the files again is by logging out and back in again.When it does this it wont let me move the files or eve view properties..how can i resolve this?

---

### Post by quantumstitch on 2008-07-11
you could try moving files around in the terminal using the mv or cp command. mv is moves files and cp copies them leaving the original intact. implementation:
```

mv file.mp3 /new/path/for/file.mp3

```
or 
```

cp file.mp3 /new/path/for/file.mp3

```

---

### Post by finer recliner on 2008-07-11
if you're moving a lot of files around often, your computer may be too slow to catch up with the changes (depending on your computer specs). next time it happens, try just waiting a few minutes and then refresh that directory to see if the files are useable again. 

next time it happens also check your memory usage by opening a terminal and typing the command 'free' (without quotes). make sure you're not using any swap, since this will thrash your harddrive and make it very slow to use.

just some ideas.

---

