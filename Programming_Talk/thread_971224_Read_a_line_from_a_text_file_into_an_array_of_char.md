---
title: "Read a line from a text file into an array of characters"
date: 2008-11-04
forum: Programming Talk
---

### Post by J05HYYY on 2008-11-04
Hello, I have the following text file:

A/112412512.wav
B/1231243124.wav
C/23516524362.wav
D/24562.wav
E/42142.wav
FA/23344.wav
G12/344/ssf.wav

and I want to get the nth line 

... Is there a way of doing this in C?

Any help much appreciated, Josh

---

### Post by lisati on 2008-11-04
I'm a bit rusty with "C", but here goes with an idea

Have a loop that uses fscanf() or fread() to get one line from the file at a time into a buffer in your program, then use strcpy() or strncpy() to put it in the proper element of the array.

---

### Post by grepgav on 2008-11-04
does it have to be in c?

that would be easier to do in awk.

---

### Post by slavik on 2008-11-04
grepgav, if this has to be done in C, there is most likely a specific reason (I hope) ... in any case.

J05HYYY, you can fopen() the file, then use fgets() into a buffer. I am also assuming you know at least some C.

---

### Post by J05HYYY on 2008-11-05
I'll get back to this ... you'd be wrong to assume.

> 
#include <stdio.h>

main()
{
int dirsize = 80;
char array[9][dirsize];
int linenum = 0;
FILE *filepointer;
filepointer = fopen("projectfile.txt","r");
while (feof(filepointer) == 0)
{
linenum++;
fgets(array[linenum], dirsize, filepointer);
}
fclose(filepointer);
}


takes the file, and line by line, puts the contents into an array

---

### Post by J05HYYY on 2008-11-05
arrr, this is annoying ... fgets stores the new line (\n) symbol into the array; which is no good for file handling.
Is there a way to stop this happening?:(

---

### Post by LaRoza on 2008-11-05
> **J05HYYY said:**
> arrr, this is annoying ... fgets stores the new line (\n) symbol into the array; which is no good for file handling.
Is there a way to stop this happening?:(

Remove the newlines. Yes, it takes more work, but this is C ;)

---

