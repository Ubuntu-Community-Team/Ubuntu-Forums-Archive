---
title: "Writing A Script To Make Then Execute A File?"
date: 2009-09-16
forum: Packaging and Compiling Programs
---

### Post by jsmidt on 2009-09-16
I have a program with source called compute.c and a makefile.  compute.c contains a line of code containing ```
fort_10.dat
```
I need to write script that:

1. Compiles by executing "make".
2. Run the executable "./compute"
3. Change "fort_10.dat" to "fort_11.dat"
4. Compile again with "make".
5. Run the executable "./compute"
6. Change "fort_11.dat" to "fort_12.dat"
7. etc...
8. Finish when run after "fort_99.dat" is compiled and run.

Anyways, I understand people will say just write a for loop inside the program itself, but this program is complicated enough that it would be best if I could find a script that does this.

If it could either be a bash shell script or python that would be preferable.  Thanks in advance.

---

### Post by lloyd_b on 2009-09-16
> **jsmidt said:**
> I have a program with source called compute.c and a makefile.  compute.c contains a line of code containing ```
fort_10.dat
```
I need to write script that:

1. Compiles by executing "make".
2. Run the executable "./compute"
3. Change "fort_10.dat" to "fort_11.dat"
4. Compile again with "make".
5. Run the executable "./compute"
6. Change "fort_11.dat" to "fort_12.dat"
7. etc...
8. Finish when run after "fort_99.dat" is compiled and run.

Anyways, I understand people will say just write a for loop inside the program itself, but this program is complicated enough that it would be best if I could find a script that does this.

If it could either be a bash shell script or python that would be preferable.  Thanks in advance.

Well, this *does* sound a bit silly (I'd have the program set so that the filename was passed as a command-line parameter, which eliminates the recompile on each pass).  However:```
#!/bin/bash

PREV=10

for CURRENT in {10..99}; do
    if [ $CURRENT -gt 10 ]
        # Need to do the string replace
        OLD="fort_$PREV.dat"
        NEW="fort_$CURRENT.dat"
        sed -i "s/$OLD/$NEW/" compute.c
        PREV=$CURRENT
    fi

    # recompile the code.
    make

    # run the program
    ./compute

done
```Note: This has *not* been tested - make sure you have backups of everything before trying it.

Lloyd B.

---

