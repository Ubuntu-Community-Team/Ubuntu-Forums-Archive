---
title: "Java Scanner HasNextInt()"
date: 2013-12-05
forum: Programming Talk
---

### Post by magikarp2 on 2013-12-05
Hello. I'm attempting to load int values that are stored in a file that will later be used in fields of an object. I load the file with a *FileReader* and pass that to a S*canner*. But it doesn't seem to see any int's at all.

The file I'm reading from is like this.```
StringHere 400 200 100 100 1
```
And the code
```
while( scan.hasNextInt() )
    {
    System.out.println(scan.nextInt());
    }
```
Which returns nothing.

---

### Post by aytuggurbuz on 2013-12-05
You have to first scan the string I think, unless you already have done so.

---

### Post by r-senior on 2013-12-05
When the scanner sees the string "StringHere", hasNextInt() returns false so you never enter the loop.

---

