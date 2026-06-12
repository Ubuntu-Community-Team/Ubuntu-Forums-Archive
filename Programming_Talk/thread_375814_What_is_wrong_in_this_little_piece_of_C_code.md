---
title: "What is wrong in this little piece of C code?"
date: 2007-03-04
forum: Programming Talk
---

### Post by jincast90 on 2007-03-04
Hello. I have written this following piece of code:

#include <stdio.h>

int main()
{
	char key;

	puts("Type your favorite keyboard character");
	scanf("%c",&key);
	printf("Your favorite character is %c!\n",key);
	return(0);
}

After trying to compile using this command: "gcc favkey1.c  -o favkey1"  I get the following error:

favkey1.c:1:19: error: stdio.h: No such file or directory
favkey1.c: In function ‘main’:
favkey1.c:8: warning: incompatible implicit declaration of built-in function ‘scanf’
favkey1.c:9: warning: incompatible implicit declaration of built-in function ‘printf’


Can anyone tell me what is wrong in my source code?

---

### Post by jincast90 on 2007-03-04
I was thinking maybe something is set up wrong with the compiler or such, because I remember a couple a weeks ago my laptop would not compile some source code, but my Desktop would compile it just fine.

---

### Post by tribaal on 2007-03-04
Compiles flawlessly on my machine...

Hope you'll figure it out?

- trib'

---

### Post by ghostdog74 on 2007-03-04
can you do a find on your machine
```

find / -type f -name "stdio.h" -print

```
see if there are results. If nothing at all, you have installed gcc incorrectly i guess. pls reinstall. If there are stdio.h, you can look at where its stored, the include the path in your environment

---

### Post by tribaal on 2007-03-04
Make sure you installed "build-essentials", not only the "gcc" package.
Build-essentials installs the standard C library and lots of other things, while the GCC package only installs gcc itself...

Hope this is the problem :)

- trib'

---

### Post by jincast90 on 2007-03-04
> **tribaal said:**
> Make sure you installed "build-essentials", not only the "gcc" package.
Build-essentials installs the standard C library and lots of other things, while the GCC package only installs gcc itself...

Hope this is the problem :)

- trib'

I tried doing a "aptitude search build-essentials" but nothing came up. So where should I get it?

And to ghostdog74, I didn't install gcc, it was installed with Ubuntu. (From the live cd).

---

### Post by Ramses de Norre on 2007-03-04
It's build-essential, you can find it in main.

---

### Post by jincast90 on 2007-03-04
Alright! I installed build-essential and now it compiled. Thanks for your help.

---

