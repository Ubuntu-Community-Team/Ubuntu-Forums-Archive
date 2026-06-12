---
title: "addling word to a file."
date: 2009-10-23
forum: Programming Talk
---

### Post by aliahsan81 on 2009-10-23
Hi All

I am making a script in which.I have a problem i try to discribe.

```

File1 content need to be append in file 2 but such as if content already exist then dont add.

File1 IS Like this

myname
yourname
hername
hisname

File2 

%AddNameHere  myname yourname hername hisname






```

---

### Post by Arndt on 2009-10-23
> **aliahsan81 said:**
> Hi All

I am making a script in which.I have a problem i try to discribe.

```

File1 content need to be append in file 2 but such as if content already exist then dont add.

File1 IS Like this

myname
yourname
hername
hisname

File2 

%AddNameHere  myname yourname hername hisname






```

A bash script? My suggestion: read in the first file, and put it as one line in a variable. Look for the content in file2 (using 'grep'), and using if-then-else, add it if appropriate.

---

### Post by aliahsan81 on 2009-10-23
Yes that correct i manage to make a loop to pick file1 content one by one.But i am not able to get in my head how to put that content at end of the line.I will post my script part in a while 

This is already define in file2

%AddNameher name...............

---

### Post by diesch on 2009-10-23
Something like this:

```
#!/bin/sh

while read name; do
 if ! egrep "$name" File2; then
   sed -i -es"/\(^%AddNameHere.*\)/\1 $name/" File2
 fi
done < File1

```

---

