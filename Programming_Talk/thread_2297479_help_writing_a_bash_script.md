---
title: "help writing a bash script"
date: 2015-10-04
forum: Programming Talk
---

### Post by daniel294 on 2015-10-04
I need help in writing a BASH script that is called from another BASH script to delete certain files according to a pattern in a text file.
I have a text file containing names or numbers.  And I have a directory (with sub directories) that contains many files.
I need to go over all files in my directory (and its sub directories) and delete these files that have any of the strings in my text file in their names.
 
For example:
 
Text file:
 
John
Dan
Ella
34567433
98844566
Test
 
And I have these files:
 
C_John_5453454.mp4
C_Dan_lastv_45435455.mp4
C_98844566_rrr.mp4
C_hello.mp4
C_hello_45354.mp4
 
In this case the first 3 files will be deleted.

---

### Post by Lars Noodén on 2015-10-04
Is this homework in any way?

[http://mywiki.wooledge.org/BashGuide/TestsAndConditionals](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals)

---

### Post by daniel294 on 2015-10-04
no, i record all my phone call automatically. once in a while (during backup) i want to remove recording of my friends and family.

---

### Post by Lars Noodén on 2015-10-04
Cool.  There are others better at scripting, but the way I would approach it would be something like this:

```

#/bin/bash
while read name; 
do find /some/path/ -type f -name "*$name*" -exec mv -t ~/.local/share/Trash "{}" \; 
done < somefile

```

[find](http://manpages.ubuntu.com/manpages/trusty/en/man1/find.1.html) also has a -delete option that you can use directly if moving them is not what you want.

---

### Post by daniel294 on 2015-10-04
Thank A LOT!!
it is so much simpler then the AWK i used..
(don't know why, i was always afraid using exec with find...)

anyway, if anybody else needs it:


#/bin/bash


echo "cleaning directory " "$1"


while read name;

do echo -e "\n"$name"\n------------\n";  find  "$1" -type f -name "*$name*" -printf "%f\n" -exec  mv -t ~/.local/share/Trash "{}" \;

done < list_file

---

