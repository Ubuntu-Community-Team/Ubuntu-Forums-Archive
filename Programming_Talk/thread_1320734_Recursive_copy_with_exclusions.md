---
title: "Recursive copy with exclusions"
date: 2009-11-09
forum: Programming Talk
---

### Post by silentrebel on 2009-11-09
I require a solution for this problem:

Let there be a directory *original/* with the following structure:
> original/
++-dir1/
++++-file1
++++-file2
++++-file3
++-dir2/
++++-pic1
++++-pic2
Let there also be a file named *directives* with the following content:
> dir1/
dir2/pic1
How would I recursively copy the contents of *original/* to *new/* and exclude the files and directories listed in *directives*.  The original directory tree must be reproduced in *new/*.
I've tried a few things with find and xargs to little avail (they would copy all the files to new (except those in the excluded directories), but the directory tree would not be preserved).  
I'm starting to think about writing my own recursive copy function, but there must surely be an easier way...
Thanks,
silentrebel

---

### Post by stylishpants on 2009-11-09
Use rsync.  It's not just for remote directory copies.

You can use some combination of the following options (from the man page) to include/exclude whatever files you want.

```

-f, --filter=RULE           add a file-filtering RULE
-F                          same as --filter=’dir-merge /.rsync-filter’
                            repeated: --filter=’- .rsync-filter’
    --exclude=PATTERN       exclude files matching PATTERN
    --exclude-from=FILE     read exclude patterns from FILE
    --include=PATTERN       don’t exclude files matching PATTERN
    --include-from=FILE     read include patterns from FILE
    --files-from=FILE       read list of source-file names from FILE

```

---

### Post by silentrebel on 2009-11-10
This looks like it might be exactly what I mean...  I guess I've always underestimated the usefulness of rsync...  Let me fiddle around with it and I'll let you know...
Thanks,
silentrebel

---

