---
title: "Copy files from a list"
date: 2007-12-16
forum: Programming Talk
---

### Post by pmorton on 2007-12-16
I'm having trouble with this. Using locate and egrep I've created a text file listing path/fileneme of multiple files located in various directories. I now want to copy them to a single directory without their original tree structure.  I've tried rsync and cpio, but I can't arrive at a satisfactory way of doing it. I'd be grateful for any suggestions.

---

### Post by ghostdog74 on 2007-12-16
unless  i misinterpreted your requirement, you can loop through the lines and just copy the files to the destination
```

while read line
do
cp " line" destination
done < myfile.txt

```

---

### Post by pmorton on 2007-12-16
> **ghostdog74 said:**
> unless  i misinterpreted your requirement, you can loop through the lines and just copy the files to the destination
```

while read line
do
cp " line" destination
done < myfile.txt

```

Thanks for the quick reply. Forgive me, but I'm entirely new to scripting. My script is:

```

#!/bin/sh -vx
while read line
do
cp " line" home/mydir/output_directory
done < /home/mydir/input_file_listing.txt

```


But that gives the error:

+ read line
+ cp  line home/mydir/output_directory
cp: cannot stat ` line': No such file or directory

Input_file_listing.txt contain a single line reading:
/home/mydir/testfile
and testfile exists in mydir.
Have I misunderstood the code you supplied?

---

### Post by ghostdog74 on 2007-12-16
> **pmorton said:**
> Thanks for the quick reply. Forgive me, but I'm entirely new to scripting. My script is:

```

#!/bin/sh -vx
while read line
do
cp " line" home/mydir/output_directory
done < /home/mydir/input_file_listing.txt

```


But that gives the error:

+ read line
+ cp  line home/mydir/output_directory
cp: cannot stat ` line': No such file or directory

Input_file_listing.txt contain a single line reading:
/home/mydir/testfile
and testfile exists in mydir.
Have I misunderstood the code you supplied?
```

while read line
do
cp "$line" home/mydir/output_directory
done < /home/mydir/input_file_listing.txt

```

---

### Post by pmorton on 2007-12-17
Thanks a million. I think you've just kick-started my scripting!
Regards
P Morton

---

### Post by miha on 2013-02-01
Hi,

You can also copy files like this:

# find / -name "*something*" -type f | awk '{print "cp " $1 " /path/to/directory/."}' | bash

Br,
-miha

---

