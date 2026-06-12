---
title: "Beginner Problems with gcc"
date: 2007-07-18
forum: Programming Talk
---

### Post by meanburrito920 on 2007-07-18
I'm new to programing in C and I was trying to compile the basic Hello World Prog. with cpp. the code is ```

#include <stdio.h>

int main()
{
  printf( "Hello World! \n");
  getchar();
  return 0;
}


```

however, when i try and compile this, gcc gives me the error ```
myfirstprogram.c:1:20: error: studio.h: No such file or directory

```

Anyone have any idea what is going on? Sorry for being such a noob.

---

### Post by meanburrito920 on 2007-07-19
I figured out that it was the fact that i hadnt installed build-essential- but now with the same code it is telling me "newline unexpected" help please.

---

### Post by Jessehk on 2007-07-19
This is not entirely relevant, but according to this [this reference]("http://c-faq.com/ansi/maindecl.html"), the proper code for your snippet (specifically, the **main()** function) would be:

```

#include <stdio.h>

int main( void ) {
    printf( "Hello, world!\n" );
    getchar();
    return 0;
}

```

The only change is the **void** to specifiy that **main()** takes no parameters.

:)

---

### Post by meanburrito920 on 2007-07-19
i tried it, gave same error:
/usr/bin/ld: 2: Syntax error: newline unexpected
collect2: ld returned 2 exit status

any other ideas?

---

### Post by yabbadabbadont on 2007-07-19
```
/media/projects/temp $ cat go.c 
#include <stdio.h>

int main()
{
  printf( "Hello World! \n");
  getchar();
  return 0;
}
/media/projects/temp $ gcc -o go go.c 
/media/projects/temp $ ls -l
total 12
-rwxr-xr-x 1 daffy daffy 6769 2007-07-19 22:43 go
-rw-r--r-- 1 daffy daffy   90 2007-07-19 22:42 go.c
/media/projects/temp $ ./go
Hello World! 


```
Works fine here.

---

### Post by meanburrito920 on 2007-07-19
Is there a library i am missing or something? I am using nano, and installed the build-essential package...

---

### Post by Mr. C. on 2007-07-20
Show the output of 

```
od -bc myfirstprogram.c
```

MrC

---

### Post by biky2004indra on 2008-12-23
Hi,
I am in a big problem. Please help me. my problem is that when i am trying to compile any c/c++ program using the command g++ -lm sample.c -o sample, where sample.c is my c program name, the the following error message is giving : /usr/bin/ld: 1: Syntax error: newline unexpected
collect2: ld returned 2 exit status
I am using UBUNTU 8.10 and it was updated regularly. I have tried in various way to debug, but no one is working. How can i solve it. someone suggested to uninstall everything and reinstall again. i have already uninstalled g++ and gcc & then reinstalled again. but no positive result. can anyone tell me how can i solve it without formatting the ubuntu.
Thanks and waiting.

---

### Post by slavik on 2008-12-24
have you tried using gcc to compile C programs instead of g++?

---

### Post by monkeyking on 2008-12-24
try posting the output of

```
cat -A yourcode.c
```

Where yourcode.c should be your code.

I think you have som strange nonvisible chars in your code.

---

### Post by namegame on 2008-12-24
Necromancy is frowned upon by many modern civilizations.


Anyhoo, I've had some IDEs complain if you accidentally press the return key after the last valid line of your code. My advice would be to, in your editor of choice, go to the last character of your code, in your case "}" and delete all characters after it, including spaces.

---

### Post by Mr. C. on 2008-12-24
Save your file using Unix-style newline endings

---

