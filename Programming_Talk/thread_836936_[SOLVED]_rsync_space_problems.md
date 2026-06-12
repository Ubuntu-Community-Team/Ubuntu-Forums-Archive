---
title: "[SOLVED] rsync space problems"
date: 2008-06-22
forum: Programming Talk
---

### Post by joesmoe10 on 2008-06-22
Hey all,
I'm starting to learn bash scripting but I'm stuck. I'm trying to write a simple function to sync music between two directories.  Unfortunately, I can't figure why rsync keeps choking on spaces in the directory paths.

```
function syncMusic {
        local winMusic='"/media/DATA/My Documents/My Music/Amazon MP3"'
        local linuxMusic='"/home/joe/Music/Amazon MP3"'

        rsync --whole-file --times --size-only --dry-run --exclude='.*' --ignore-existing --progress --perms --recursive $winMusic $linuxMusic 

        rsync --whole-file --times --size-only --dry-run --exclude='.*' --ignore-existing --progress --perms --recursive $linuxMusic $winMusic 
}
```


Here's what I get when I run this:

```
building file list ... 
rsync: link_stat "/home/joe/"/media/DATA/My" failed: No such file or directory (2)
rsync: link_stat "/home/joe/Documents/My" failed: No such file or directory (2)
rsync: link_stat "/home/joe/Music/Amazon" failed: No such file or directory (2)
rsync: link_stat "/home/joe/MP3"" failed: No such file or directory (2)
rsync: link_stat "/home/joe/"/home/joe/Music/Amazon" failed: No such file or directory (2)
0 files to consider

```

---

### Post by ghostdog74 on 2008-06-22
use double quotes for your variables.

---

### Post by jpkotta on 2008-06-22
Your quotes are not in the contents of the variable.  Since variable doesn't include the quotes from the definition, you'd either have to explicitly put them in the definition (by quoting them with a backslash) or by quoting each usage of the variable.

```

quoted="\"this has quotes in the value\""
unquoted="you need to quote this one every time"

some_command $quoted
some_command "$unquoted"

```

I think one of the trickiest things of shell scripting is the quoting.

---

### Post by joesmoe10 on 2008-06-22
Awesome, thanks for the help.

quoting the variables did the trick.

---

