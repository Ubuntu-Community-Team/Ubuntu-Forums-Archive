---
title: "Map a file directly into memory using C"
date: 2014-03-04
forum: Programming Talk
---

### Post by dan60 on 2014-03-04
Hello guys,
I'm trying to study more about PE headers, so i wanted to load a file diretly into memory and then print his PE headers.
To do this i first use fopen() and fread()
```

FILE* fd = fopen("test.exe","r");
fread(buffer, sizeof(short),1,fd);
printf("The magic is: %s",buffer);

```
And then o got the "MZ".
Now i'm trying to simulate a file structure:
```

STRUCT dos_header{
  char e_magic[1];
...
}

```
But here is here i got stuck. In order for me to "point" this structure on the exe, i have to be able to load this exe directly onto memory (without using a file descriptor i think). Do you guys know a way to do this?
Just to better explain what im thinking, i wanted to do the following:

```

//Magicaly load the exe onto memory and a pointer named "p_EXE" points to the first byte, so:
dos_header* dheader = p_EXE;
printf("The magic is %s", dheader->e_magic);

```

Can you guys help me!? 
Thanks all!

---

### Post by lisati on 2014-03-04
You might want to look into opening the file with "rb" (binary) mode, where what would ordinairily be new line sequences can have a different meaning than in "r" (text) mode.

---

### Post by Bachstelze on 2014-03-04
If you are running your program on Windows, then you probably need rb indeed. In Linux (or other POSIX-compliant systems), it has no effet (r and rb are equivalent).

---

### Post by dan60 on 2014-03-04
yep. I think i need to, somehow, load the entire file on the memory and the access it without using a FILE structure...am i right?

---

### Post by ofnuts on 2014-03-05
You can use mmap() and derivatives to map a range of addresses to the file (never tried that though).

Otherwise you can use your FILE to read the whole file in memory and if you have a pointer to the first byte, and a struct describing the header, you can cast the pointer to a pointer to that struct and read the header elements.

---

### Post by dan60 on 2014-03-05
Thank you!
Could you please show me some code, because i still don't know how to implement that :(

---

