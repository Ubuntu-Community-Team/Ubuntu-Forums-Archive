---
title: "bash, search directories by mtime osrt and play files"
date: 2009-11-09
forum: Programming Talk
---

### Post by lhoffmeyer on 2009-11-09
Hey all,

I have an external HD with music.  I wish to find all directories that
have been modified in the last 30 days.  I then want to play the files
in each of the directories, sorted by file name and not date modified
using mplayer.

So, to get the list of directories I use this command.  Where would
I go from here to sort the files by name and play in mplayer?

I only want to play *.flac or *.mp3 files.

$find .  -type d  -mtime -30   -exec ls -d {} \;

TIA,

Lance

---

### Post by DaithiF on 2009-11-10
this isn't pretty, but it seems to work ok:
```
find . -type d -exec find {} -name '*.mp3'  \; | sed 's/^\(.*\/\)\([^/]*\)$/\2\t\1\2/' | sort  | cut -f2 | sed 's/^/"/;s/$/"/' | xargs mplayer

```

some notes:
* i use another find command as the exec rather than ls, as otherwise you lose the full path to the directory
* the first sed command extracts the filename from path and prepends it to the line so that we can sort by just the filename and not the path
* the filename that we prepend to the line is just needed for sorting, once we've sorted we can drop it -- thats the cut command
* the 2nd sed command wraps quotes around the result so that mplayer will handle paths with spaces

---

### Post by DaithiF on 2009-11-10
edit: I left out your mtime 30 clause, wasn't using it for testing, but you'll need to add it back in.

---

