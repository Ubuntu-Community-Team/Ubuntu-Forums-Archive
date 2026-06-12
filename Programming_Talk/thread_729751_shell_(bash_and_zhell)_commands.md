---
title: "shell (bash and zhell) commands"
date: 2008-03-20
forum: Programming Talk
---

### Post by webdreamer on 2008-03-20
We are doing a work for a compilers course, and the first step it's to change the name of the compiler files. It used to be "compact" and now will be "nx6" (we have some files for a more simple compiler, and the work consists of modifying it so it compiles a new language).
That's an awfully boring job, and as so we would like to change all the occurrences of "compact" to "nx6" in all files recursively using shell commands, namely the grep and the for.
Our professor gave us an extra class, and performed the little stunt in a matter of seconds, but we, as shell newbies aren't getting the same luck. What he wrote in zhell looked something like this:

for i in `grep Compact ./**/* |awk -f '{print $1}' |sort |uniq `
>do
>echo "###$i###"
>sed -e 's/Compact/Nx6/g'
>\mv $i .tmp $i
>done

We do not manage to fully understand the command, and the transcript has probably some errors, and that's why we can't make it through. (At this point all files containing Compact in it's name are already renamed to Nx6).

What we needed was help both understanding the command and correcting it. Any help you're able to provide will be welcomed.

---

### Post by ghostdog74 on 2008-03-20
if your purpose is to change all files with names that contain "Compact" to "Nx6"
```

find /fullpath -name "*Compact*" | awk 'BEGIN{ q="\047"}
 {
  oldfile=$0
  gsub("Compact","nx6")
  cmd = "mv "q oldfile q " "q $0 q
  print cmd
  #system(cmd)   #uncomment to rename file.
}'


```

---

### Post by WW on 2008-03-20
I believe he is changing all occurrences of "Compact" in the *contents* of the files (not the file names) to "Nx6".

Perhaps something like this, which changes occurrences of "three" to "THREE":

**changenames.sh**
```

for i in `grep three file* | awk -F : '{print $1}' | sort | uniq`
    do
    echo "### $i ###"
    sed -e 's/three/THREE/g' -i '~' $i
    done

```
Example
> 
$ ls
changenames.sh  filea           fileb           filec
$ cat filea
one
two three four
five four three
$ cat fileb
four three two one
one two three four
three
$ cat filec
eight nine
$ # The next several commands show what is going in inside the back-ticks 
$ # in the for-loop in changenames.sh
$ # grep finds all occurrences of the string "three" in all the files whose filename begins with "file"
$ grep three file* 
filea:two three four
filea:five four three
fileb:four three two one
fileb:one two three four
fileb:three
$ # Use awk to keep just the filenames.
$ grep three file* | awk -F : '{print $1}' 
filea
filea
fileb
fileb
fileb
$ # Sort the filenames (although in this case, they are already sorted)
$ grep three file* | awk -F : '{print $1}' | sort 
filea
filea
fileb
fileb
fileb
$ # Use uniq to keep only the unique filenames
$ grep three file* | awk -F : '{print $1}' | sort | uniq
filea
fileb
$ # So the for-loop in changenames.sh will loop twice, with $i=filea then $i=fileb
$ sh changenames.sh 
### filea ###
### fileb ###
$ cat filea
one
two THREE four
five four THREE
$ cat fileb
four THREE two one
one two THREE four
THREE
$ cat filec
eight nine
$ # The original versions of the files that have been changed have been backed up, using the ~ extension.
$ ls
changenames.sh  filea           filea~          fileb           fileb~          filec
$ cat filea~
one
two three four
five four three
$


---

### Post by WW on 2008-03-20
In hindsight, I wonder why your instructor wanted to use a for-loop, when a single sed command could do the same thing. E.g.
```

sed -e 's/three/THREE/g' -i '~' file*

```
Maybe it has something to do with the second argument of the grep command that you showed: **./**/***, which I couldn't make much sense of.


EDIT: The loop avoids running sed on files that don't contain the string to be changed, so perhaps it is more efficient.

---

### Post by webdreamer on 2008-03-20
Thank you WW, your first command was right. The grep is related to the fact you can do /**/* in zhell and get the files recursively from both the current folders and all the subfolders. That command is not possible in the shell.

---

