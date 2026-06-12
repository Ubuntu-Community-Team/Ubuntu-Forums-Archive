---
title: "Error compiling C program with GCC in Cygwin"
date: 2010-08-07
forum: Programming Talk
---

### Post by redfox1160 on 2010-08-07
I have a basic C program:
```
/*H2E2.c: First handwritten program*/
#include <stdio.h>

main()
{
	printf ("It's fun to write my own program in C.\n");
	return 0;
}
```
when I run the GCC C compiler in Cygwin, I get the following output:
```
Eric@Gross-PC ~
$ gcc -o H2E2.exe H2E2.c
H3E2.c:8:2: warning: no newline at end of file

```
I don't know what this means. Could someone help? (I know there is a newline at the end of the printf statement, but do I need one somewhere else?)

Thanks!

---

### Post by nvteighen on 2010-08-07
Ugh... first, let's write that in modern standard C.

```

/*H2E2.c: First handwritten program*/
#include <stdio.h>

int main(void) /* Not "main()"!!!*/
{
	printf ("It's fun to write my own program in C.\n");
	return 0;
}

```

Now onto gcc. Notice that it isn't an error, but a warning. The executable was surely created and should work... The "no newline" thing means that your file should end with a blank line... I don't remember the reason, but for sure it's some legacy thing of none importance.

---

### Post by redfox1160 on 2010-08-07
> **nvteighen said:**
> Ugh... first, let's write that in modern standard C.

```

/*H2E2.c: First handwritten program*/
#include <stdio.h>

int main(void) /* Not "main()"!!!*/
{
	printf ("It's fun to write my own program in C.\n");
	return 0;
}

```

Now onto gcc. Notice that it isn't an error, but a warning. The executable was surely created and should work... The "no newline" thing means that your file should end with a blank line... I don't remember the reason, but for sure it's some legacy thing of none importance.

Thanks. I was using [this]("http://aelinik.free.fr/c/") website (I found it on these forums) to learn C. Do you know of a better, more modern website? Thanks again.

---

### Post by nvteighen on 2010-08-08
> **redfox1160 said:**
> Thanks. I was using [this]("http://aelinik.free.fr/c/") website (I found it on these forums) to learn C. Do you know of a better, more modern website? Thanks again.

This one is possibly the best: [http://www.crasseux.com/books/ctutorial/](http://www.crasseux.com/books/ctutorial/)

(It starts using the pre-ANSI C style at the beginning for explaining some stuff, but it soon starts using the standard constructs to teach you everything...)

---

