---
title: "error stray ‘\342’ in program"
date: 2012-03-24
forum: Programming Talk
---

### Post by thexain on 2012-03-24
**[SIZE=3][COLOR="#FF0000"]Please check this thread for a solution :[/COLOR] [http://ubuntuforums.org/showthread.php?t=2252682](http://ubuntuforums.org/showthread.php?t=2252682)[/SIZE]**

I wrote a program about Hungry eyes when i try to compile i got these erros 
```
hungry.c: In function ‘main’:
hungry.c:10:3: error: stray ‘\342’ in program
hungry.c:10:3: error: stray ‘\200’ in program
hungry.c:10:3: error: stray ‘\234’ in program
hungry.c:10:28: error: expected expression before ‘/’ token
hungry.c:10:28: error: stray ‘\342’ in program
hungry.c:10:28: error: stray ‘\200’ in program
hungry.c:10:28: error: stray ‘\235’ in program
hungry.c:13:24: warning: incompatible implicit declaration of built-in function ‘malloc’ [enabled by default]
hungry.c:19:3: warning: incompatible implicit declaration of built-in function ‘exit’ [enabled by default]

```
My Programing code is under
```
#include <stdio.h>
#include <unistd.h>
#include <string.h>
#include <sys/types.h>

#define LB_SIZE 1024

int main(int argc, char *argv[])
 {
  char fullPathName[] = “/usr/xain/bin/xeyes”;
  char *myArgv[LB_SIZE];  // an array of pointers

  myArgv[0] = (char *) malloc(strlen(fullPathName) + 1);
  strcpy(myArgv[0], fullPathName);

  myArgv[1] = NULL;  // last element should be a NULL pointer

  execvp(fullPathName, myArgv);
  exit(0);  // should not be reached
}
```

---

### Post by lisati on 2012-03-24
*Thread moved to **Programming Talk**.*

---

### Post by codemaniac on 2012-03-24
Hello thexain ,
Welcome to the Ubuntuforums ..

Your NR==10 , i mean line no 10 is contained errorneous characters in the mask of a " .
I replaced left and right quotes with natural double quote at line no 10.

try the below code that should compile .
```

#include <stdio.h>
#include <unistd.h>
#include <string.h>
#include <sys/types.h>

#define LB_SIZE 1024

int main(int argc, char *argv[])
 {
  char fullPathName[] = "/usr/xain/bin/xeyes";
  char *myArgv[LB_SIZE];  // an array of pointers

  myArgv[0] = (char *) malloc(strlen(fullPathName) + 1);
  strcpy(myArgv[0], fullPathName);

  myArgv[1] = NULL;  // last element should be a NULL pointer

  execvp(fullPathName, myArgv);
  exit(0);  // should not be reached
}

```

---

### Post by codemaniac on 2012-03-24
I guess you coded the above piece of source in an editor of windows environment , like notepad or MS Word .Turn off "smart quotes" in your Microsoft programs. That option translates " into either &#8217; or &#8216; or one of the non-defined chars between 128 and 160, depending on the codepage being used, the nearby chars, and the phase of the moon.My terminal tries to paste that non-ASCII sequence as-is, and fails.

---

