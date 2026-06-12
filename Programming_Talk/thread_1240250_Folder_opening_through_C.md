---
title: "Folder opening through C"
date: 2009-08-14
forum: Programming Talk
---

### Post by veda87 on 2009-08-14
I have written a code to open a folder ```
#include <stdio.h>

int main() {

        char str[] = "/home/veda/myhand/";
        printf("%s\n", str);
        system(str);
        return 0;
}

```
I got an error while executing it ```
veda@veda-desktop:~/myhand/langu$ ./a.out 
/home/veda/myhand/
sh: /home/veda/myhand/: Permission denied

```
Even as a ROOT(SuperUser) I got the same output.... i think I had made a mistake....

Can anyone point it out....

---

### Post by MadCow108 on 2009-08-14
your missing the "cd"
also note that only the subshell that that system called is in that directory
another system call will again be in the working directory of the program

use chdir(str); to change the working directory of the executable (may not be portable)

---

### Post by credobyte on 2009-08-14
You can't execute a folder ( [COLOR=DarkOrange]cd <location>[/COLOR], not [COLOR=DarkOrange]<location>[/COLOR] ) ;)

---

### Post by cmay on 2009-08-14
edit: never mind i did not see what the question really was . disregard this.

---

