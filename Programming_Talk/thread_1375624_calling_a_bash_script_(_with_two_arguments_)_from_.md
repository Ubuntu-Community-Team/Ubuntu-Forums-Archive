---
title: "calling a bash script ( with two arguments ) from a bash script"
date: 2010-01-08
forum: Programming Talk
---

### Post by lemonsf on 2010-01-08
Greetings,

I have a slight problem, and I am unable to find a solution to it, so any help here would be greatly appreciated...

I have written a compiling script which simply takes two parameters ( sourcefile name, and outputfile name ), this works fine. 

On top of this I have written another small script which compiles some files and then links them with the required parameters, the problem arises when I call my original 'compiling' script.

```
sh /home/dev/scripts/comp "sourceFile.c outputFile.o"
```

This runs the script, but passes the whole string ( "sourceFile.c outputFile.o" ) as one parameter, but I want to pass this as two arguments. I've tried putting them into vars and seperating the vars but to no avail. Is this possible?

To elaborate: The compile script takes the two arguments 'sourceFile.c' and 'outputFile.o' and runs 
```
gcc -c /home/dev/source/sourceFile.c -o /home/dev/o/outputFile.o
```
So essentially its just filling in the paths for me.

Thanks in advance

---

### Post by DaithiF on 2010-01-08
```
sh /home/dev/scripts/comp sourceFile.c outputFile.o
```

or if either of your files had spaces in their names then enclose each in quotes:
```
sh /home/dev/scripts/comp "sourceFile.c" "outputFile.o"
```

---

### Post by lemonsf on 2010-01-08
#-o. Thoguht I tried that. God I'm such a lemon.

Thanks DaithiF

---

