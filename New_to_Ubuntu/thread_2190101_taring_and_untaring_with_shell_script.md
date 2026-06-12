---
title: "taring and untaring with shell script"
date: 2013-11-25
forum: New to Ubuntu
---

### Post by hookitup on 2013-11-25
Hello All,


I'm having a little bit of trouble with Tar.


I have a folder named foo i want to tar. i have a shell script in directory /home/username/scripts 
that is supposed to go to /home/username/test/bar/foo and tar it with gzip as well and save it in /home/username/foosaves with the current date and time in the name.
I know how to do this manually but in a shell script i think i may be doing it wrong because its taring the entire path and not just the one directory.
Heres what i have. 

```

#!/bin/bash

ARDIR=/home/username/foosaves
BUDIR=/home/username/test/bar/foo
DATE=`date +%m%d%y`

tar -czvf "ARDIR"/foobu-"DATE".tar.gz "$BUDIR"

```


it tars it fine but when i untar it i get the entire directory tree /home/username/test/bar/foo
i just want foo. can anybody help ?

---

### Post by VMC on 2013-11-25
Did you try adding "$" to both ARDIR and DATE?

---

### Post by hookitup on 2013-11-26
woops yes. i just typed it wrong on here. but yes in the script i call the variables correctly. i don't know why when i untar it i get the entire directory tree

home
username
test
bar
foo


i just want directory foo to be tared . 

any ideas ?

---

### Post by VMC on 2013-11-26
Try adding "cd /home/username/test/bar/foo" to your script and then just tar that folder.

---

### Post by newb85 on 2013-11-26
+1 to VMC's advise. Tar will include the relative path from where you are when you create the tar file.   If you're not in the same place when you un-tar it, the resulting files won't be, either.

---

### Post by steeldriver on 2013-11-26
Yes instead of specifying the full path to the target directory (foo) you can change to foo's parent directory and then just tar 'foo' from there. You can either do that explicitly using the 'cd' command in your script or (equivalently, as far as I can see) using the '-C' switch

```
tar czvf "$ArDir/foobu-$Date.tar.gz" -C "$FooDir" foo
```

where

```
FooDir="/home/username/test/bar"
```

The '-C' option is more elegant imho - but I'm not sure how portable. I also snuck in a suggestion not to use ALL CAPS for variable names (they are unofficially reserved for system variables).

There is also an option to create the tar with full paths and then srip the leading ones when you untar

```

     --strip-components=NUMBER
           strip NUMBER leading components from file names on extraction

```

---

### Post by hookitup on 2013-11-26
This is now working thanks to VWC.

i did not think it was that easy as to just drop the cd command in it. 



Thanks for the help folks.

---

