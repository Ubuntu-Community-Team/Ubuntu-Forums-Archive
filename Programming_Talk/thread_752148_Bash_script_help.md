---
title: "Bash script help"
date: 2008-04-11
forum: Programming Talk
---

### Post by mark1969 on 2008-04-11
I am trying to write a script to delete any characters from file names that are not recognized by a FAT file system i.e.\ / : * ? " < > | so they can be copied to an external media player. I have written basic programs before using BBC basic but that was about 25 years ago and thought i would try again. I'm not sure how to approach this problem and would be grateful for any advise given. Thanks for taking the time to read this

---

### Post by ghostdog74 on 2008-04-11
assuming your current directory only contains files.
```

#!/bin/bash
ls | awk 'BEGIN{q="\047"}
/[\/:*?"<>|]/{ 
         oldfile=$0
         gsub(/[\/:*?"<>|]/,"")
         cmd="mv "q oldfile q" "q $0 q
         print cmd
         #system(cmd)         #uncomment to use
}' 

```

---

### Post by WW on 2008-04-11
How did you get file names with these characters in them?  Do you really have files that have a forward slash / in the file name?

The command ```
rename 's/[\/\\:*?"<>|]//g' list_of_files
``` can do this.  For example:
```

$ touch '<file>' '|ugly|name|.dat' '\\\V.dat' '?*"what:now'
$ ls
<file>  ?*"what:now  \\\V.dat  |ugly|name|.dat
$ rename 's/[\/\\:*?"<>|]//g' *
$ ls
V.dat  file  uglyname.dat  whatnow
$ 

```

---

### Post by mark1969 on 2008-04-12
thank you both. that's great to get me started

---

