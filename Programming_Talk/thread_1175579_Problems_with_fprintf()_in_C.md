---
title: "Problems with fprintf() in C"
date: 2009-06-01
forum: Programming Talk
---

### Post by whoelse on 2009-06-01
Hi, I am having some trouble with a C-program of mine. I want to write some chars to a file. On some PCs it is working, on others I have a lot of strange symbols in the file instead (boxes, boxes with points in it, ... - I cannot describe it any better, but the file is much bigger than it should be).

Here is the code responsible for it:
[PHP]
FILE *file_pointer;
char data[DATA_SIZE];
file_pointer=fopen(file_name,"wb");
fprintf(file_pointer, "%s", data);[/PHP]
BTW, the control output in the terminal works fine.

If anybody has an idea, any help would be appreciated.

---

### Post by Thesuperchang on 2009-06-01
If your data is a null terminated string.
[PHP]FILE *file_pointer;
char data[DATA_SIZE];
file_pointer=fopen(file_name,"w");
if(file_pointer == NULL) return -1; // Error state
fprintf(file_pointer, "%s", data);[/PHP]

Else
[PHP]FILE *file_pointer;
int errCheck;
char data[DATA_SIZE];
file_pointer=fopen(file_name,"wb");
if(file_pointer == NULL) return -1; // Error state
errCheck = fwrite(data, sizeof(char), DATA_SIZE, file_pointer);
if(errCheck != sizeof(char) * DATA_SIZE) return -1; // Error state[/PHP]

---

### Post by whoelse on 2009-06-01
Seems that I have to use fwrite() instead of fprintf(), thanks for the help.

---

### Post by nvteighen on 2009-06-01
The binary mode in UNIX and Unix-like systems is redundant, being the usage of fread()/fwrite() over fscanf()/fprintf() which defines what kind of data (ASCII or binary) you're reading/writing.

Binary mode means to dump/get a certain memory location to/from disk. You take a variable and copy it exactly into/from the file... that's why you need to take the data's sizeof() in fwrite()/fread(). 

(Yay, this text is written conforming to both I/O :D)

---

### Post by Can+~ on 2009-06-01
> **nvteighen said:**
> The binary mode in UNIX and Unix-like systems is redundant, being the usage of fread()/fwrite() over fscanf()/fprintf() which defines what kind of data (ASCII or binary) you're reading/writing.

Binary mode means to dump/get a certain memory location to/from disk. You take a variable and copy it exactly into/from the file... that's why you need to take the data's sizeof() in fwrite()/fread(). 

(Yay, this text is written conforming to both I/O :D)

Achievement Unlocked.

---

