---
title: "small nautilus script"
date: 2009-04-17
forum: Programming Talk
---

### Post by Stefanie on 2009-04-17
I wanted to write a small nautilus script to remove the first page of a selected pdf file. My programming knowledge is very limited, but in the end I tried this code and it worked:

```

#!/bin/bash
#
# Nautilus script -> delete first page pdf
#
filesall=""
while [ $# -gt 0 ]
do
files=`echo "$1" | sed 's/ /\?/g'`
filesall="$files $filesall"
shift
done
pdftk $filesall cat 2-end output xxx.pdf
mv xxx.pdf $filesall

``` 

I copied the first bit of code from another script, but I don't know exactly how it works. What does the variable $# stand for, and what about $1?

---

### Post by odyniec on 2009-04-17
> **Stefanie said:**
> I copied the first bit of code from another script, but I don't know exactly how it works. What does the variable $# stand for, and what about $1?

$# is the number of command-line arguments passed to the script, and $1 is the first argument ($2 is the second, and so on).

Each time your script does a "shift", the first argument is discarded and the second one takes its place -- what was $2 becomes $1, $3 becomes $2, etc. Since one argument is eliminated, $# is decreased by one. So the while loop in your script iterates over all the arguments, keeping the currently processed argument in $1.

This is all explained in the bash man page.

---

### Post by Stefanie on 2009-04-17
ok thanks. i had a look at the man page for bash, but my programming knowledge is very limited so I found it hard to find what i was looking for.

---

### Post by kaibob on 2009-04-17
> **Stefanie said:**
> I wanted to write a small nautilus script to remove the first page of a selected pdf file. My programming knowledge is very limited, but in the end I tried this code and it worked... I copied the first bit of code from another script, but I don't know exactly how it works. What does the variable $# stand for, and what about $1?

If you want to eliminate the first page of one or more selected PDF files, the Nautilus script shown below will do what you want. Were you intending to do something more with the script--as written it appears to rename and merge when multiple files are selected? 

```
#!/bin/bash

cd $(dirname "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS")

for FILE in "$@" ; do
pdftk "$FILE" cat 2-end output xxx.pdf
mv -f xxx.pdf "$FILE"
done
```

If you only want to work with one selected file, you wouldn't even need the for loop included in the above. 

BTW, this script overwrites the existing PDF files, so be sure to have backups.

---

### Post by Stefanie on 2009-04-18
Thanks a lot. I didn't want to do anything special apart from removing the first page, but I just couldn't find out how to point bash to a selected file so I copied the first lines from another script. 

Where can I find an overview with the names of the different bash variables? (like $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ?

---

### Post by kaibob on 2009-04-18
The Nautilus variables are discussed here:

[http://g-scripts.sourceforge.net/faq.php](http://g-scripts.sourceforge.net/faq.php)

You can also view them as follows:

1) Open Nautilus and right-click on any file.

2) Scroll down to the the "Scripts" menu item and then select "Open Scripts Folder."

3) Click on "Show more details."

---

