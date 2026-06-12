---
title: "C/C++, reading from STDIN using fread...."
date: 2010-08-28
forum: Programming Talk
---

### Post by arkashkin on 2010-08-28
Hi,
I'm writing some client/server application for my class assignment.
The client should read the input from STDIN and send it to the socket.
My program stack on those lines:

char buffer [STD_BUFF_SIZE];
printf("Before fread.\n");
int len = fread(&buffer,sizeof(buffer),1,stdin);
printf("After fread.\n");

(I'm passing some text to it's STDIN from some text file...)

1. The line "Before fread." isn't printed until I press 'enter' key, why is that?
2. The line "After fread." isn't printed at all, that mean that the fread function never returns, why? how to solve this?

Thanks in advance.

---

### Post by MadCow108 on 2010-08-28
1. printing to stdout is buffered and may print later then indicated in the code. To get it to print out at a certain time use fflush.

2. because fread reads until the buffer is full, an error uccors or end of file is indicated (ctrl +d in most terminals)
if you want to read line delimited input use fgets or getline

---

### Post by arkashkin on 2010-08-28
> **MadCow108 said:**
> 1. printing to stdout is buffered and may print later then indicated in the code. To get it to print out at a certain time use fflush.

2. because fread reads until the buffer is full, an error uccors or end of file is indicated (ctrl +d in most terminals)
if you want to read line delimited input use fgets or getline

**I am building a remote shell service.**

The client should get the commands that need to be executed on the other side from ARGV and the standard input from it's STDIN.
I can't use get line because my lecturer told me that the input may be binary. He told me that fread should be good for this purpose. The input from stdin may come in different sizes. How to properly get it into a buffer, so I can send it to the server?

---

### Post by MadCow108 on 2010-08-28
you have an error in the fread call, drop the & in front of buffer, buffer converts to a pointer to the memory automatically
And you should swap the sizes to read arbitrary binary data:
fread(buffer,1,sizeof(buffer),stdin);
Otherwise it just returns 1 when the buffer was completely filled and zero in all other cases, which may not be what you want

concerning sending to server, read this:
[http://www.gnu.org/software/libc/manual/html_node/Sockets.html#Sockets](http://www.gnu.org/software/libc/manual/html_node/Sockets.html#Sockets)

---

