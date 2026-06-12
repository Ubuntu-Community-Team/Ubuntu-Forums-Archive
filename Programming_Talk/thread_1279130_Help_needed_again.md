---
title: "Help needed again"
date: 2009-09-30
forum: Programming Talk
---

### Post by Dark-Byte on 2009-09-30
Hello I'm writing a program in C to read from a file and write to standard output but it is giving me something like this:
&#65533;&#65533;&#65533;p&#65533;
     &#65533;&#65533;&#65533;DB&#65533;&#959;8&#65533;
&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#959;&#65533;P&#65533;   &#65533;&#65533;&#65533;&#65533;p&#65533;&#65533;P&#65533;&#959;D&#65533;&#959;&#65533;&#65533;
          &#65533;
&#65533;&#65533;         &#65533;&#65533;&#65533;&#959;b&#65533;
  &#65533;&#65533;
    &#65533;
&#65533;(&#65533;&#65533;p&#65533;&#65533;&#65533;&#959;&#65533;&#65533;&#65533;&#65533;
p &#65533;&#65533;&#65533;p&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;P[&#65533;p[&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
       &#65533;&#65533;&#65533;&#65533;

Here is the code:

```

int main()
{
  char holding[1000];
  int x;
  x = open( "/home/user/Desktop/Labsheets/Labsheet4/input.dat", O_RDONLY, S_IRWXU  );
  int i;
  i = lseek( x, 0, SEEK_END );//get number of bytes in file
  read( x, holding, i );
  close( x );
  printf
  return 0;
}

```

Can someone help me please?

---

### Post by johnl on 2009-09-30
Is your file a plain text file? If not, it makes no sense to print the contents of the file.

Otherwise, I would check the return values of open() and read()  to make sure it is actually opening the file and actually reading some bytes.  Also make sure that you are null-terminating the buffer (I don't think read() does this for you).

---

### Post by MadCow108 on 2009-09-30
your setting the position in the file to the end with your lseek
so you need to reset it before reading:
lseek(x,0,SEEK_SET);

```
int main()
{
  char holding[1000];
  int x;
  x = open( "test.c", O_RDONLY);
  int i;
  i = lseek( x, 0, SEEK_END );
  lseek(x,0,SEEK_SET);            // seek to start
  int r = read( x, holding, i );
  holding[r] = '\0';              // null terminate
  close( x );
  printf("%s",holding);
  return 0;
}
```

this is of course not very effective.
it would be simpler to just read into your buffer until you encounter EOF (or end of buffer or error) with the fread/fget/... functions

---

### Post by Dark-Byte on 2009-09-30
> **MadCow108 said:**
> your setting the position in the file to the end with your lseek
so you need to reset it before reading:
lseek(x,0,SEEK_SET);

```
int main()
{
  char holding[1000];
  int x;
  x = open( "test.c", O_RDONLY);
  int i;
  i = lseek( x, 0, SEEK_END );
  lseek(x,0,SEEK_SET);            // seek to start
  int r = read( x, holding, i );
  holding[r] = '\0';              // null terminate
  close( x );
  printf("%s",holding);
  return 0;
}
```


Very true!!Thanks a lot to both of you.

---

### Post by Can+~ on 2009-09-30
Why are you using the unistd file functions instead of the C standard functions?

---

### Post by Dark-Byte on 2009-09-30
Beacuse I got tons of labsheet from my university which says to use only those functions(system calls ):
  	 	 	 	 	 	  
[LIST]
[*]open
[*]close
[*]read
[*]write
[*]lseek
[/LIST]
:(

---

