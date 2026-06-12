---
title: "File size in C - need some help !"
date: 2009-06-11
forum: Programming Talk
---

### Post by ActiveFrost on 2009-06-11
```
int getfilesize(char* filepath) {
       FILE *file;
       int fileSize = 0;
       file = fopen(filepath, "r");
       if (file > 0) {
          fseek(file, 0, SEEK_END);
          fileSize = ftell(file);
          fseek(file, 0, SEEK_SET);
          fclose(file);
          return fileSize;        
       }
}
```

When I use this function in a loop ( file by file ), it always give me the same size/number : 2009291924. Why it is so ? Am I doing something in the wrong way ?

---

### Post by fr4nko on 2009-06-11
Hi,

to get the file size you should use the 'stat' function. It works like that

```
struct stat info[1];

stat (filename, info)
file_size = info->st_size;

```
You can type info libc to have more help on the stat function.

Otherwise, talking about your code, it looks correct in principle but I think you should check the return code of fseek because ***it can fails***. Also, but less important, you should check that the FILE * is not null with something like file != 0 or file != NULL but not file > 0.

I hope that helps.

Francesc

---

### Post by Eeqmcsq on 2009-06-11
```
int getfilesize(char* filepath) {
       FILE *file;
       int fileSize = 0;
       file = fopen(filepath, "r");
       if (file > 0) {
          fseek(file, 0, SEEK_END);
          fileSize = ftell(file);
          fseek(file, 0, SEEK_SET);
          fclose(file);
          return fileSize;        
       }
}
```

You're missing a return statement at the end of the function. It's possible that your code failed the "if (file > 0)" check and is returning a junk value. Try putting a "return 12345;" at the end to see if your code reaches that return statement.

---

### Post by cmay on 2009-06-11
i am just begin&#324;ing to lean working with files so i am far from being the one that should answer this question. but i playeed around whit the example and this works for all different filenames i supply it and 0 if it does not exist. 
```
#include <stdio.h>
#include <stdlib.h>
#include <dirent.h>

int getfilesize(char* filepath);
int main(int argc ,char *argv[])
{
    
      fprintf(stdout,"%d", getfilesize("filesizeprog.c"));

return 0;
}

int getfilesize(char* filepath) {
       FILE *file;
       int fileSize = 0;
       file = fopen(filepath, "r");
       if (file > 0)
      {
          fseek(file, 0, SEEK_END);
          fileSize = ftell(file);
          fseek(file, 0, SEEK_SET);
          fclose(file);
          return fileSize;        
       }
   return 0;
}
```any way thanks for posing this since i never seen a example of fseek so i found this very useful.

---

### Post by ActiveFrost on 2009-06-11
Problem solved ( didn't knew that I need to use _return 0_ if my function is meant to return another integer ).

---

### Post by dwhitney67 on 2009-06-11
> **cmay said:**
> ...
```

int getfilesize(const char* filepath)
{
   int fileSize = 0;
   FILE* file = fopen(filepath, "r");
   if (file != 0)
   {
       fseek(file, 0, SEEK_END);
       fileSize = ftell(file);
       fclose(file);       
   }
   return fileSize;
}
```


There's no need to have two return statements in the function; one will suffice (see above for the corrected code).

---

### Post by soltanis on 2009-06-11
dwhitney had this in his post but to point this out to you, there is no point in seeking back to the beginning of the file

```

fseek(file, 0, SEEK_SET);

```

If you are closing the file anyway.

---

### Post by ActiveFrost on 2009-06-12
> **dwhitney67 said:**
> There's no need to have two return statements in the function; one will suffice (see above for the corrected code).

No, if I do not add return 0, I get the following :
```
read_dir.c:28: warning: control reaches end of non-void function
```

---

### Post by dwhitney67 on 2009-06-12
> **ActiveFrost said:**
> No, if I do not add return 0, I get the following :
```
read_dir.c:28: warning: control reaches end of non-void function
```

Look carefully at the modified code I posted (which was originally posted by Cmay).

---

### Post by ActiveFrost on 2009-06-12
> **dwhitney67 said:**
> Look carefully at the modified code I posted (which was originally posted by Cmay).

Yeah, sorry .. It works without the second return statement, but - why should I remove it ? I mean, it works in both cases now ..

---

