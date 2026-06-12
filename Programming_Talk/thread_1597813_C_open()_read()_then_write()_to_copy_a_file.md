---
title: "C open() read() then write() to copy a file"
date: 2010-10-15
forum: Programming Talk
---

### Post by Xender1 on 2010-10-15
I know its possible as my friend has been able to copy a file using C but using the open() read() and write() C commands. I have attempted in doing the same thing to merely copy a file but it is not working. Here is what I got: 
```

//i have a variable size which is an int and is the byte size of the file
//i got the byte size of file from stat
int fileread = open("original.txt",'r');
void *buffer;
buffer = malloc(sizeof(void) * size);

int nread = read(fileread,buffer,size);

int filewrite = open("original.txt.backup",'w');

write(filewrite,buffer,size);

close(filewrite);
close(fileread);

```

This is creating the file original.txt.backup with some strange permissions which I can address later but its not a copy of original.txt it is just a empty file. Most of the info I have from read write and open is from [http://rabbit.eng.miami.edu/info/functions/unixio.html](http://rabbit.eng.miami.edu/info/functions/unixio.html)

Thanks!

---

### Post by annoyingrob on 2010-10-15
I don't have any of my code ni front of me, but I do remember having to fflush() before closing to commit any changes currently cached to disk.

---

### Post by worksofcraft on 2010-10-15
> **Xender1 said:**
> 
```

int fileread = open("original.txt",'r');

```



ah you confuse two different ways of doing it.
the open, read and write functions use a file handle and you need to open it with an integer access code like so:
```

int fileread = open("original.txt", O_RDONLY);

```
otoh there are functions fopen, fread and fwrite that are perhaps slightly higher level and they use struct FILE and you open them with a string like "r" or "w" which is not a single character code but a null terminated string. :shock:

---

### Post by Some Penguin on 2010-10-15
In addition to the O_FLAG problems, read() and write() are permitted to read and write fewer bytes than you ask them to.

---

### Post by psusi on 2010-10-15
In addition to using the wrong argument with the wrong function, you are multiplying your size by sizeof( void ) which I think would be zero, since void means NOTHING.

---

### Post by worksofcraft on 2010-10-15
> **psusi said:**
> In addition to using the wrong argument with the wrong function, you are multiplying your size by sizeof( void ) which I think would be zero, since void means NOTHING.

lol - that is true, however the new ANSI standard doesn't guarantee size of char to be one anymore so people need to use sizeof(void) to get smallest addressable unit :shock:

If you use the C++ compiler it will tell you:
```

void.c:4: warning: invalid application of ‘sizeof’ to a void type

```

but if you use the C compiler it is quite happy and says:
```

$> gcc -Wall void.c
$> ./a.out
sizeof(void)=1

```

---

### Post by Xender1 on 2010-10-16
Ah thank you all very much for your help. Following your advice I was able to fix it perfectly! Here is what I have now: 
```

//i have a variable size which is an int and is the byte size of the file
//i got the byte size of file from stat
int fileread = open("original.txt", O_RDONLY);
void *buffer;
buffer = malloc(sizeof(void) * size);

int nread = read(fileread,buffer,size);

int filewrite = open("original.txt.backup",O_CREAT | O_RDWR, 0644);

write(filewrite,buffer,size);

close(filewrite);
close(fileread);

```

0644 for rw-r--r--

Thanks!

---

### Post by psusi on 2010-10-16
> **worksofcraft said:**
> lol - that is true, however the new ANSI standard doesn't guarantee size of char to be one anymore so people need to use sizeof(void) to get smallest addressable unit :shock:


Ok, but why bother multiplying by one?

---

### Post by spjackson on 2010-10-16
> **worksofcraft said:**
> lol - that is true, however the new ANSI standard doesn't guarantee size of char to be one anymore so people need to use sizeof(void) to get smallest addressable unit :shock:

Which issue of which standard are you referring to here?

---

