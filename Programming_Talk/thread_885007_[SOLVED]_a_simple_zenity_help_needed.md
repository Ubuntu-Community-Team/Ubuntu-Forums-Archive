---
title: "[SOLVED] a simple zenity help needed"
date: 2008-08-09
forum: Programming Talk
---

### Post by dexter.deepak on 2008-08-09
when i use the --file-selection option, it returns the pathname of the file, which is relative to the script's location.
what do i need to do, if i want the absolute pathname of the file ?

---

### Post by ConMan318 on 2008-08-09
When I use the --file-selection option I get the absolute path to the file returned...  For example
```

/stor/music$ zenity --file-selection
/stor/music/Gryphon/Red Queen to Gryphon Three/01. Opening Move.mp3

```

which would have returned
```

./Gryphon/Red Queen to Gryphon Three/01. Opening Move.mp3

```
if I were returned a relative path.  Are you sure all of your other options are correct?

---

### Post by dexter.deepak on 2008-08-09
oops!! i just got confused with my code...thanks, the problem was somewhere else.

---

