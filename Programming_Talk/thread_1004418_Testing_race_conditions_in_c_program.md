---
title: "Testing race conditions in c program"
date: 2008-12-07
forum: Programming Talk
---

### Post by myquidproquo on 2008-12-07
Hi everyone.

I've written a server-client program with threads and processes and I would like to test it for race conditions...

Anyone know how can I make a script or any other way to test it?

I've tried writing some commands to a text file and initialize the program like this "./program < file.txt". It didn't work.

I'm still learning unix :)

Thank you.

---

### Post by Delever on 2008-12-07
I used to avoid race conditions, not to test them :D

Seriously, you need to have good understanding of threads when you are writing code in which threads are involved. Usually race conditions are the hell to find and remove, and often requires basically reading source code to find them.

That said, you can modify your client to send some random data to test, then run lots of clients. If you can, test using real network, not loopback interface (127.0.0.1).

---

### Post by myquidproquo on 2008-12-07
Ok, thank you :)

Another thing that I can't find the answer...
I'm using a fork execl(). 
How can I make it work if the program is compiled in another computer with different folder names? Is there a path variable I can use?

Even if I make the execl() path argument as "./program" it will look "program" in the current working directory, not the directory where the first program is installed...

---

### Post by odyniec on 2008-12-07
> **myquidproquo said:**
> How can I make it work if the program is compiled in another computer with different folder names? Is there a path variable I can use?

Even if I make the execl() path argument as "./program" it will look "program" in the current working directory, not the directory where the first program is installed...

If you declare your main() function like this:
```
int main(int argc, char *argv[])
```

then argv[0] will be the actual path used to execute your program, either absolute or relative. You can then use the dirname() function to extract the directory part. Here's a simple example:
```
#include <stdio.h>
#include <libgen.h>

int main(int argc, char *argv[]) {
	printf("My directory is %s\n", dirname(argv[0]));
	return 0;
}
```

---

### Post by myquidproquo on 2008-12-08
Thank you. That helped me a lot.

I love this forum :)

---

