---
title: "CVS script for recursive check-in of dirs and files"
date: 2007-10-10
forum: Programming Talk
---

### Post by dwhitney67 on 2007-10-10
If you have ever used CVS (or perhaps some other version system), things can get messy if a screw-up occurs when checking-in many files and directories using a script.

Thus I was wondering if anyone with CVS and shell-script experience could critique the following script:

```
#!/bin/sh

# $1 = path in which to start looking for files

if [ $# -ne 1 ]; then echo "Usage: $0 [dir]"; exit 1; fi

FILES=`find $1`
COMMENT="initial check-in"

for file in $FILES
do
        echo Checking in $file...

        cvs add $file

        if [ -f $file ]
        then
                cvs commit -m "$COMMENT" $file
        fi
done
```

My main concerns are:
1) Does one need to commit a directory that is being added to CVS?
2) When performing an add/commit on a regular file, should the full-path as reported by "find" be used, or does CVS prefer that the add/commit occur _within_ the directory where the file exists?

Here's an example of what "find" would report for a subdirectory containing a few files:

somedir
somedir/File1
somedir/File2
somedir/FileN

---

### Post by alauro on 2008-04-25
so - your script has the basic concepts but there are 2 things to know:
1. directories must be added to the module
2. cvs doesn't handle binary files particularly well, so you need to find them and deal with them correctly.

I have attached a script that shows how to do both things. It's safe to run ./cvs-add-commit.sh <dir> and it will just print out on the screen all the files and directories that would be added. if you run it as ./cvs-add-commit.sh <dir> true, it will then do the cvs add and commit actions

---

