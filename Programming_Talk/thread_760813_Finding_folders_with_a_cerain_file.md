---
title: "Finding folders with a cerain file"
date: 2008-04-20
forum: Programming Talk
---

### Post by dr.koljan on 2008-04-20
Here's the situation:

There is a directory with lots of folders. In some of these folders, there is a certain file (say ABC). I want to make a shell script that would find folders with the ABC file and make a symbolic link to it in the same folder. Is that possible?

Thanks in advance :D

---

### Post by vanadium on 2008-04-20
I guess so. You probably will need the "find" command to find the file then use the output of it to create a link to that file. The benefit of making a symbolic link in the same folder where the file resides escapes me, though.

---

### Post by WW on 2008-04-20
> **dr.koljan said:**
> Here's the situation:

There is a directory with lots of folders. In some of these folders, there is a certain file (say ABC). I want to make a shell script that would find folders with the ABC file and make a symbolic link to it in the same folder. Is that possible?

Thanks in advance :D
By "in the same folder", do you mean in the top directory, the one that contains all the folders?  What you said sounds like you want the symbolic link to ABC in the folder that already has ABC, which is not possible.

---

### Post by dr.koljan on 2008-04-20
> **vanadium said:**
> I guess so. You probably will need the "find" command to find the file then use the output of it to create a link to that file. The benefit of making a symbolic link in the same folder where the file resides escapes me, though.

I have tried using [Ifind ]*/<filename>[/I], but it gives me the filename together with the directory, but I only need the directory, is that possible?

I want to create a script that would automatically create icon symlinks in those folders where the target image exists, to avoid creating broken symlinks. (I'm working on a package that involves creating icons)

> **WW said:**
> By "in the same folder", do you mean in the top directory, the one that contains all the folders?  What you said sounds like you want the symbolic link to ABC in the folder that already has ABC, which is not possible.

In the folder which contains ABC, of course, otherwise it would be too easy :) 

I know it is impossible when the filename is the same, but I want the filename of the symlink to be different.

---

### Post by ghostdog74 on 2008-04-20
```

find /path -name "ABC" | awk 'BEGIN{
 q="\047"
}
{
 cmd = "ln -s "q $0 q" "q $0"_"c++ q" "
 print cmd
 #system(cmd) #uncomment to use
}'

```

---

### Post by stylishpants on 2008-04-20
```

find . -name ABC | while read f; do ln -s "$f" "$f.symlink"; done
```

---

### Post by vanadium on 2008-04-21
Why not just with the find command:

```

find . -name "*" -exec ln -s "{}" "{}.symlink" \;

```

---

### Post by dr.koljan on 2008-04-21
Thanks a lot for all your advices, I guess I'll stick with vanadium's code as it looks cleaner and easier :P

---

### Post by WW on 2008-04-21
Test it first.  I just tried this:
```

find . -name "ABC" -exec ln -s "{}" "{}.symlink" \;

```
and while it created links with the name "ABC.symlink", the links were bad.  The problem is using "." as the first argument.  This worked:
```

find `pwd` -name "ABC" -exec ln -s "{}" "{}.symlink" \;

```

---

