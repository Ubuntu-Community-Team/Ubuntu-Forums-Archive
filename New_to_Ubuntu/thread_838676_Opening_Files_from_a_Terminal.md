---
title: "Opening Files from a Terminal"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by Papenco on 2008-06-23
Ok, it's me again, How do I open a file let's say .mp3 or .c from the terminal?
THanks.

---

### Post by Rocket2DMn on 2008-06-23
For a .c file, you can use your favorite text editor, like
```
emacs filename.c
gedit filename.c
```
.mp3 files can be loaded similarly into your favorite media player (or you can just open the media player and access the file from there).

---

### Post by sdennie on 2008-06-23
I think you are looking for gnome-open:

```

gnome-open some_file

```

That will open the file with whatever it would open with if you had double clicked on it in nautilus.

---

### Post by RomeReactor on 2008-06-23
Hi. Just in case that by 'open files from the terminal' you mean 'use a command line application to open the files', you can open .c files with Emacs, Vim, or Nano:
```
nano /path/to/file.c
```

To play mp3 files, you can install MPD and MPC, MP3Blaster, or Cplay.

---

