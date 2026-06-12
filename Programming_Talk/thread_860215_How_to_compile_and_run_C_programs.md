---
title: "How to compile and run C programs ?"
date: 2008-07-15
forum: Programming Talk
---

### Post by Gaurav_Shah on 2008-07-15
Hello Everyone,
I am new to Ubuntu I am having a little 'C' program with me 
//hello.c
#include <stdio.h>
void main()
{
	printf("Hello From Ubuntu");
	return ;
}

when I tried to compile it using "cc hello.c"
I get following errors :
hello.c:1:19: error: stdio.h: No such file or directory
hello.c: In function ‘main’:
hello.c:4: warning: incompatible implicit declaration of built-in function ‘printf’
hello.c:3: warning: return type of ‘main’ is not ‘int’

can you tell me how to fix it ?
moreover I will like to install anjuta when i tried to get it from add/remove pakages system was geting hang . So i download anjuta-2.4.2
than i select install but it not worked.
Can you tell what can be wrong ?

And yes Thanks in advance.

---

### Post by PaulM1985 on 2008-07-15
Try changing "void main()" to "int main(void)" and "return ;" to "return 0;"  that should work

Paul

---

### Post by Zugzwang on 2008-07-15
Gaurav_Shah, read the stickies (The article "Please <blink>*READ THIS*</blink> before posting" at the top of the list of topics in this forum) . Somewhere there you will find the FAQ about compiling your first C program. Read it, follow the instructions and come back if you have any questions.

EDIT: To make it easier for you, look [here]("http://ubuntuforums.org/showthread.php?t=689635").

---

### Post by ConMan318 on 2008-07-15
In the terminal, type:
```

sudo apt-get install build-essential

```

And I would use
```

gcc filename.c

```
rather than 'cc', though I don't know if it matters.  I know 'gcc' stands for GNU Compiler Collection, so I don't know what you would be compiling with if you use 'cc'.  Both seem to work though, so I suppose it doesn't matter much as long as it works.


Also, as far as your actual program goes, 'main' is generally an 'int' function.  This is because the return value lets you know if there have been any errors.  A return value of 0 means the program completed successfully, so your void function with a void return statement doesn't allow that error checking.  So 'main' should read:
```

int main() {
    printf("Hello from Ubuntu!\n");
    return 0;
}

```

The '\n' at the end of the print statement is to start a new line after it, so the next shell prompt doesn't appear on the same line.  Try both ways and see.

---

### Post by Martin Witte on 2008-07-15
> **PaulM1985 said:**
> Try changing "void main()" to "int main(void)" and "return ;" to "return 0;"  that should work

Using 'void main' is definitely not ANSI standard, see e.g. this [discussion]("http://users.aber.ac.uk/auj/voidmain.shtml"). However - when you got gcc installed as pointed out by other people in this thread the code of op compiles and runs:

```
martin@sony:~$ cat test.c
#include <stdio.h>
void main()
{
	printf("Hello From Ubuntu");
	return ;
}
martin@sony:~$ gcc test.c
test.c: In function &#8216;main&#8217;:
test.c:3: warning: return type of &#8216;main&#8217; is not &#8216;int&#8217;
martin@sony:~$ ./a.out
Hello From Ubuntumartin@sony:~$ 

```

---

### Post by Gaurav_Shah on 2008-07-15
> **ConMan318 said:**
> In the terminal, type:
```

sudo apt-get install build-essential

```

And I would use
```

gcc filename.c

```
rather than 'cc', though I don't know if it matters.  I know 'gcc' stands for GNU Compiler Collection, so I don't know what you would be compiling with if you use 'cc'.  Both seem to work though, so I suppose it doesn't matter much as long as it works.


Also, as far as your actual program goes, 'main' is generally an 'int' function.  This is because the return value lets you know if there have been any errors.  A return value of 0 means the program completed successfully, so your void function with a void return statement doesn't allow that error checking.  So 'main' should read:
```

int main() {
    printf("Hello from Ubuntu!\n");
    return 0;
}

```

The '\n' at the end of the print statement is to start a new line after it, so the next shell prompt doesn't appear on the same line.  Try both ways and see.

Thanks ConMan318 Problem Solved . Thanks a lot

---

### Post by dep0 on 2011-09-29
hi.
i am also new in ubuntu and i would like to ask how can i compile and also how can i run a programm in c++ or c.

---

### Post by Tony Flury on 2011-09-29
dep0 : Please don't restart new threads - especially ones over 3 years old.

If you had read the thread before posting you would have seen Zugzwang refer to the stickies - which you should read before postig to the forums - that advice is still valid.

---

### Post by sffvba[e0rt on 2011-09-29
Back to sleep thread...


404

---

