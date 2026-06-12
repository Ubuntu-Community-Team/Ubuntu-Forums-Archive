---
title: "Read line before last in a file"
date: 2008-11-19
forum: Programming Talk
---

### Post by 420shaggy on 2008-11-19
So I have a program that creates a log of commands entered line by line to a file.

Eg->

ls
ps
exit

  What I am trying to do is go to the end of the file (it could be hundreds of lines long) and read the line before the last one.  In this case it would be "ps."

  Is there an easy way to go about doing this?

**Forgot to mention that was in C**

---

### Post by Idefix82 on 2008-11-19
```
tail --lines=2 filename | sed '2d' $1
```

The tail command strips off all but the last two lines, then passes the output on to the sed command, which removes the 2nd line and prints out the result on to the screen.
The original file is left intact.

Edit: I didn't see your edit, this is in the terminal, not C.

---

### Post by 420shaggy on 2008-11-19
Thanks for the quick reply.  I forgot to mention originally that I was writing this in C.  So I was looking for a method of doing this using stdio.

---

### Post by Tony Flury on 2008-11-19
I would look at writing a C program that used the tail command get the last two lines redirected into a temp file - and then your C program just has to read the first line of the temp file.

If you want to do it without using tail i.e. a pure C solution - you could also look into how tail is implemented - and adapt that. I assume it effectively reads the file backwards.

---

### Post by 420shaggy on 2008-11-19
Using this command definitely makes things easier:

```
tail --lines=2 magma/relstex.tex | sed '2d' $1
```

But is there a way I that I can pipe the output to a variable in C?  I don't really need to see what the second to last line in the file is, I just need to execute it.

Eg->

```

	char *str = (char *)malloc(sizeof(char) * 100);		
	system("tail --lines=2 .hist | sed '2d' $1 | export(str)");

```

  When I tried this however I got the output:

> sh: Syntax error: word unexpected (expecting ")")

---

### Post by en0f on 2008-11-19
Replace - system("tail --lines=2 .hist | sed '2d' $1 | export(str)"); with 
system("tail --lines=2 .hist | sed \'2d\' $1 | export(str)");

---

### Post by 420shaggy on 2008-11-19
I still get the same error.

I think I found the solution... apparently it seems that this either cannot be done or it is awkward to try to do.  So what I decided to do was to pipe the output to a file then read the input ouside of the system call.  It seems excessive to me, but hey it gets the job done.

---

### Post by en0f on 2008-11-19
afaik its a really really cruel way of doing things.. you should really take some more time to solve this problem properly.. 

for e.g - you could glob the whole file in one go to a char[] (malloc) then you can use fseek() to get you to the exact position you want (second line last is actually one line ["\n"] before the last ;)
This will be more robust and withstand the wrath of time on several platform and is also a good programming practise.

---

### Post by Idefix82 on 2008-11-19
It's probably the best solution. This problem would have been very easy to solve with C++ using iterators but C is rather clumsy at this sort of thing. It can still be done using fgets() but I think that the combined shell/C approach is quicker to implement.

---

### Post by tomchuk on 2008-11-19
[php]
#include <stdio.h>
#include <string.h>
#include <linux/limits.h>

int main(){
  const char *file = "in";
  FILE *in = fopen(file, "r");
  if (in != NULL){
    char last[ARG_MAX];
    char prev[ARG_MAX];
    char temp[ARG_MAX];
    while(fgets(temp, sizeof temp, in) != NULL){
      strcpy(prev, last);
      strcpy(last, temp);
    }
    fputs(prev, stdout);
    fclose(in);
  }
  return 0;
}
[/php]

---

### Post by gpsmikey on 2008-11-19
I was thinking about that problem the other day for a different issue, but still looking for the last line or two of a file.  The problem with the "read the file to the end then we have the last lines" approach is that if it is a large file, the scan can take quite a bit of time and resources.  I think the better approach is to seek to the end of the file then seek back say 300 characters and look for the last lines in there.  That way is is always a short scan.

mikey

---

### Post by tomchuk on 2008-11-19
It's 0.1s for a 16MB file of 1.8M lines. But yeah, could be quicker:
[php]
#include <stdio.h>
#include <string.h>
#include <linux/limits.h>

int main(){
  const char *file = "in";
  FILE *in = fopen(file, "r");
  if (in != NULL){
    int bytes = 0;
    int nl = 0;
    while(fseek(in, --bytes, SEEK_END) == 0){
      if (fgetc(in) == '\n' && ++nl > 2){
        break;
      }
    }
    char line[ARG_MAX];
    fgets(line, sizeof line, in);
    fputs(line, stdout);
    fclose(in);
  }
  return 0;
}
[/php]


```

thomas@desktop$ ls -lh in
-rw-r--r-- 1 thomas thomas 256M 2008-11-19 16:47 in
~
thomas@desktop$ wc -l in
28387616 in
~
thomas@desktop$ tail -n2 in | head -n1
zygote
~
thomas@desktop$ time ./test2
zygote

real	0m0.001s
user	0m0.000s
sys	0m0.000s

```

---

