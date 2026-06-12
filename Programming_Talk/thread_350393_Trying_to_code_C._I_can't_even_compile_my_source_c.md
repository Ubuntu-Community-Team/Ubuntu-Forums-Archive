---
title: "Trying to code C. I can't even compile my source code."
date: 2007-01-31
forum: Programming Talk
---

### Post by jincast90 on 2007-01-31
Hello. I am trying to learn some C. But I just can't get my source code compiled. I will explain what I am doing:

This is my source code:

#include <stdio.h>

int mail()
{
	printf("Hello everybody!\n");
	return(0);
}

I save it as:

"HELLO.C." (without the "") on my Desktop

Then I go into my terminal, and type cd Desktop

Then I write: gcc HELLO.C -o hello 
I have also tried: gcc HELLO.C. -o hello, gcc hello.c -o hello and gcc hello.c. -o hello but none of these helps. They all give me an error:
 
gcc: hello.c (Or HELLO.C or whatever I typed in the particular case) : No such file or directory
gcc: no input files

So what am I doing wrong? I have not installed any programs for coding, if that helps in any way. This is probably a typical newbie question, but I hope you can help me.

Thank you.

---

### Post by lnostdal on 2007-01-31
..you really are typing it wrong or the file is not there .. type ls and check .. then try again

edit:
note that you can use tab-completion .. if you type "gcc hel" then press tab it will complete it to "gcc hello.c"

also note that you should compile like this:
```
gcc -g -Wall hello.c -o hello
```

-g adds debug info and -Wall gives you extra info about stuff .. both are things you want

---

### Post by Wybiral on 2007-01-31
Try "main" not "mail"

---

### Post by jblebrun on 2007-01-31
First, make sure the file is saved as "hello.c"... if it's "HELLO.C", the capital C will make the compiler think it's a C++ file.

Next, after you save it to the desktop, type
```

ls ~/Desktop

```
To ensure that it's really there.

---

### Post by jincast90 on 2007-02-02
I just changed the name of the file from HELLO.C. to hello.c and it then it compiled fine. Thank you very much for your help!

---

