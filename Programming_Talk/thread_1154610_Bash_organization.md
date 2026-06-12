---
title: "Bash organization"
date: 2009-05-09
forum: Programming Talk
---

### Post by Squigy Dunkens on 2009-05-09
My moms computer is extremely unorganized. She has well over a thousand ms word doc files, and they're spread out everywhere. So i installed cygwin on her computer, and i want to make a script that takes every file that has .doc in the name from the directory i am in and all the sub directories within it, and then move them all to one directory called Docs.

so far i have this
```
find . -name '*.doc*' > docs.txt
```

that listed all her .doc and .docx files in docs.txt, but i'm not even sure if thats a start to what i want to do.

---

### Post by 73ckn797 on 2009-05-09
Is it Ubuntu or Windows? I assume Windows. You could use the search, if Windows, and command it to find all "*.doc" files. You could then use that listing and copy/paste or cut/paste to the new directory.

In Ubuntu "Places/Search for Files" should also accomplish the task or, at least, know where they all are.

---

### Post by kaibob on 2009-05-10
I am not familiar with cygwin, but the following will do what you want within a Linux environment:

```
#!/bin/bash
find /source/directory -name '*.doc' -type f | while read FILE ; do
cp "$FILE" /target/directory
done
```

You have to change the source and target directories. Also, if two or more files have identical names, some provision would have to be made for this.

---

### Post by geirha on 2009-05-10
I'd try with something like this:
```
find . -iname "*.doc" -type f -print0 | xargs -0 -- cp -v -t /target/directory --backup=numbered --
```

The --backup=numbered argument to cp will make sure that it doesn't overwrite any files.

EDIT: Oh wait, you wanted to move them, well it's almost the same line. Just replace cp with mv.
```
find . -iname "*.doc" -type f -print0 | xargs -0 -- mv -v -t /target/directory --backup=numbered --
```

---

