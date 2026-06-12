---
title: "How to &quot;paste-over&quot; a line with Vi(m)?"
date: 2008-02-28
forum: Programming Talk
---

### Post by kinghajj on 2008-02-28
I want to change the copyright line of the source files of a project to have a copyright of "2007-2008" instead of just "2007". I know that I can yank one changed line  ("yy") and paste it ("p"), but I'm wondering if there's a way to delete a line without yanking it (which is what "dd" does automatically) so I can quickly replace the old lines with the new one.

---

### Post by dwhitney67 on 2008-02-28
I presume you have many files.  Here's a simple script that can change a collection of files:

```
#!/bin/sh

for file in `ls file*`         # modify this line to meet your needs (e.g. ls *.cpp)
do
        sed -i -e "s/2007/2007-2008/" $file
done
```

---

### Post by farruinn on 2008-02-28
You want to do a search and replace. In Vim:

```
:s/2007/2007-2008
```

Although the script posted will be much faster if  you want to do it for multiple files.

---

### Post by ghostdog74 on 2008-02-28
> **dwhitney67 said:**
> I presume you have many files.  Here's a simple script that can change a collection of files:

```
#!/bin/sh

for file in `ls file*`         # modify this line to meet your needs (e.g. ls *.cpp)
do
        sed -i -e "s/2007/2007-2008/" $file
done
```
even simpler..no need to use ls with the for loop. Shell expansion * will do
also, there is no need even for  the loop. sed takes in file names
```

 sed -i -e "s/2007/2007-2008/" file*

```

---

### Post by stylishpants on 2008-02-29
To answer your original question:
To delete a line in vim without yanking it, you can use this comand:

"_dd

This supplies the _ register (a null register, the vim registers equivalent of /dev/null) as the yank destination for the following dd command.


If you're comfortable using a substitution operator as suggested by the previous posters, you could accomplish this within vim as follows:

# 1. Open vim, supply on the cmd line all the files you want modified
vim file1 file2 file3 file4

# 2. Use the 'bufdo' command to apply the s/// command to all buffers at once.
:bufdo! %s/2007/2007-2008/

---

