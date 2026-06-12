---
title: "C++ pipe"
date: 2008-08-17
forum: Programming Talk
---

### Post by Ristar on 2008-08-17
```
...
char line[100];
fp=popen("ls -l", "r");
while(fgets(line, sizeof line, fp))
...
```



so, the above reads every line of entry from "ls -l"...

how do i pipe, and write to a file?

does any of u know where's a site for good C++ examples?

ie. examples that does not have thousands of lines of codes about every other thing, except the topic at hand.

---

### Post by mike_g on 2008-08-17
Well since youre writing C style code I'll give you a C style answer:
```
char line[100];
in=popen("ls -l", "r");
FILE * out = fopen("filename", "w");
while(fgets(line, sizeof line, in))
    fprintf(out, "%s" line);
fclose(out);
```
The above should right the content out to a file. As for piping the output I'm not completely sure hw you do that in C yet, but generally I'd think bash would be more suitable for that kind of stuff.

Oh and I find this site quite good for looking stuff up: [http://www.cplusplus.com/reference/](http://www.cplusplus.com/reference/)

---

### Post by dribeas on 2008-08-19
> **Ristar said:**
> 
how do i pipe, and write to a file?


If you want to pipe to a file, you have to do as suggested by mike_g. 

If you want to pipe data out of one command and into another then you can create a pipe, fork and use dup2 to map standard input/output (file descriptors 0,1) to the pipes before exec-ing the commands. Do not forget to close unused ends of the pipe in each of the forked processes and the main process.

I don't have an example at hand, but it's not really complex.

   David

---

