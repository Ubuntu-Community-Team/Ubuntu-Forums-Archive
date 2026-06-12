---
title: "Another shellscript/find(1) puzzle"
date: 2009-01-09
forum: Programming Talk
---

### Post by Cracauer on 2009-01-09
If you use find with -print0 (intended to go into xargs -0), how do you sort?

find traverses in order of the directory entries, it's not even alphabetically. Not happy.

Best I can do:
```

#! /bin/sh

find . -print \
        | sort \
        | while read foo ; do
                # can't use -e here because filename might have funky chars
                echo -n "$foo"
                # force an echo that understands -e
                # in Ubuntu /bin/sh it doesn't
                /bin/echo -en '\0'
        done

```

Of course that sorts by directory name first, where what I want is sorting inside a directory.

I really thing find should have an option to sort within a directory.

---

### Post by stroyan on 2009-01-09
Since sort defaults to sorting by each entire file path it will sort first by directory name and then by file name.  Files within the same directory will be sorted among other files in the same directory.

Exactly what do you want to be different from what you see?

Note that sort has a -z option, allowing you to use something like
find . -print0 | sort -z | xargs -0 -n 1 /bin/echo
to sort in combination with -print0.

If you want to sort on names within directories, mixing files from multiple directories, you could use the -t and -k options to specify a number of / characters to skip.  But that would always start the sort from the same depth rather than from the last, final file name.

find . -print0 | sort -z -t / -k 3 | xargs -0 echo

---

### Post by Cracauer on 2009-01-09
Ah.

The -z option to sort is the piece of the puzzle I was missing. I wonder how many more tools they hacked up to work with this. Is this in POSIX? FreeBSD has it, so it's not a GNU-only thing.

Thanks a lot. And you are right, sorting the whole line will bring the directories out in the same order anyway. The only disadvantage is runtime.

---

