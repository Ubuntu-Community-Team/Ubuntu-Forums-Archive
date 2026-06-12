---
title: "Deletion of Large Files (possible bug?)"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by klemperal on 2008-10-20
When I delete large files, like several DVD .ISOs for example, the file operation gets stuck in "preparing."  No matter how long I wait it never completes and I end up having to restart my computer to get the window off my screen.  Is this just a bug that has yet to be dealt with or does Linux in general struggle with these sort of operations?

---

### Post by brallan on 2008-10-20
are you using nautilus or the command line (or something else) to delete?

---

### Post by klemperal on 2008-10-20
Nautilus.  Just right clicking the trash and selecting "empty trash."

---

### Post by WRDN on 2008-10-20
Try deleting the files one at a time, or rather than using nautilus, use the Terminal:

```
rm [filename]
```

Or to remove an entire directory of files:

```
rm -r [directory]
```

If you need to empty the trash, enter:

```
rm -r ~/.local/share/Trash
```

---

### Post by klemperal on 2008-10-20
Thanks, I'll keep this in mind in the future.  To your knowledge is this a problem with Nautilus, Ubuntu, or Linux in general?  Seems like something that shouldn't be an issue.

---

### Post by mkvnmtr on 2008-10-20
I have never had that problem in Ubuntu. I have downloaded all of the Ubuntu isos then copied the to another disk. When I put the originals in the trash I had no problem deleting several at once so I don't think it is a general problem.

---

