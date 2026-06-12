---
title: "Sed Log"
date: 2010-10-04
forum: Programming Talk
---

### Post by huangyingw on 2010-10-04
Hello,
    I am using Sed and Awk. I use them to find and replace in bundle.
    The most concern I had is that I could not see any log about what ever they have done.
    Does they support log function or, could they start a dry-run before formal run, just like the same things done by rsync?

---

### Post by ghostdog74 on 2010-10-04
sed and awk by default doesn't do anything to files you process. so you can see the changes just by stdout. 
awk/gawk has a few options you can use to show whats being done. check the gawk man page for --dump-variables. (and others)
lastly, awk can do what sed do and much more, so there is no need to use sed and gawk together.

---

### Post by huangyingw on 2010-10-04
> **ghostdog74 said:**
> sed and awk by default doesn't do anything to files you process. so you can see the changes just by stdout. 
awk/gawk has a few options you can use to show whats being done. check the gawk man page for --dump-variables. (and others)
lastly, awk can do what sed do and much more, so there is no need to use sed and gawk together.
Hey, I have wrote such script:```
#! /bin/sh
#find "$1" \( -name \.svn -o -name \.git -o -name \.hg \) -prune -o \( -name \*\.c -o -name \*\.cc -o -name \*\.h -o -name \*\.sh -o -name YBUILD -o -name [m,M]akefile \) -exec sed -e 's/chart/bbs/;s/pro/grup/' {} \;
find $1 \( -name \.svn -o -name \.git -o -name \.hg \) -prune -o \( -name \*\.c -o -name \*\.cc -o -name \*\.h -o -name \*\.sh -o -name YBUILD -o -name [m,M]akefile \) -exec sed -ie "s/$2/$3/gi" {} >>log \;

```
After running this script, I checked that indeed, some files were changed, but, there is nothing in the log file...:(.
According to the pdf manual, it should redirect output to my "log" file, but, here , it did not..

---

### Post by ghostdog74 on 2010-10-04
that's due to sed making the edits in place (-i switch.) and it does not spew out to stdout. What are you expecting to capture in the log?  File names?

---

### Post by huangyingw on 2010-10-05
> **ghostdog74 said:**
> that's due to sed making the edits in place (-i switch.) and it does not spew out to stdout. What are you expecting to capture in the log?  File names?
Could I get both, I mean, both in-place replacement, and stdout:)
I expect to capture the action detail sed has done. For example, to which files it affect, and what's more, at which line of a file, what replacement it has done.
So, I could use "vim log" or "| vim -" to check whatever sed has done

---

### Post by lloyd_b on 2010-10-05
> **huangyingw said:**
> Could I get both, I mean, both in-place replacement, and stdout:)
I expect to capture the action detail sed has done. For example, to which files it affect, and what's more, at which line of a file, what replacement it has done.
So, I could use "vim log" or "| vim -" to check whatever sed has done

Using either 'sed' or 'awk', you can get a good "what was changed" report by using a temp file and the 'diff' command.  For example:```
#!/bin/bash

cp livefile.txt tempfile.txt
sed -i "s/somevalue/othervalue/g" livefile.txt
diff -u tempfile.txt livefile.txt >> logfile.txt
rm tempfile.txt
```This will save the existing file to a temp file, make the edits, and then run a diff against the two files, showing you exactly what was changed by the sed command.

Lloyd B.

---

### Post by ghostdog74 on 2010-10-05
```

find $1 ..... | whiler read -r file
do
  sed -n "s/$2/$3/gi;p" $file  >> log.txt
  sed -ie "s/$2/$3/gi" $file
done

```

---

### Post by huangyingw on 2010-10-05
> **lloyd_b said:**
> Using either 'sed' or 'awk', you can get a good "what was changed" report by using a temp file and the 'diff' command.  For example:```
#!/bin/bash

cp livefile.txt tempfile.txt
sed -i "s/somevalue/othervalue/g" livefile.txt
diff -u tempfile.txt livefile.txt >> logfile.txt
rm tempfile.txt
```This will save the existing file to a temp file, make the edits, and then run a diff against the two files, showing you exactly what was changed by the sed command.

Lloyd B.
Yes, a good idea. Your solution remind me of a better solution: For all the files I wanted to replace were under GIT control, so, a simple command "git diff" could do everything..

---

### Post by huangyingw on 2010-10-05
> **ghostdog74 said:**
> ```

find $1 ..... | whiler read -r file
do
  sed -n "s/$2/$3/gi;p" $file  >> log.txt
  sed -ie "s/$2/$3/gi" $file
done

```
Great thanks for your solution. I have tried this. Seems that, the log.txt file would contain all the matching files' content. Could it only contain the matching line, instead of all files?

---

