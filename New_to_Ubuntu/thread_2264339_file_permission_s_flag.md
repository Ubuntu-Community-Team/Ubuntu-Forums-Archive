---
title: "file permission s flag"
date: 2015-02-06
forum: New to Ubuntu
---

### Post by manfred4 on 2015-02-06
hi all, maybe i wasnt clear on my question in my previous post (see below). what i wanted to know is the following: 

As far as i know you can set a s flag on the file permissions that will have the following effect; if executed by a user the file will be executed as if it were the file owner. This was/is used so that users can execute/modify files which are typically only accessible by admin/root (which would be the owners) and at the same time cant access information from other users.

For this flag the id and the effective id (first should be the user the later should be the file owner id) can be checked. The id and the effective id should be different for a file w/ the s flag set. but if i do this in ubuntu it will not show a difference even if the s flag is set. It seems like setting the s flag does have no effect in ubuntu.

So, is this a security feature (in ubuntu) to prevent the obvious potential exploit possibilities or am i missing something?

Thanks for the help.
Best



hi, i'm currently reading 'Hacking, the art of exploitation' and try to reproduce some of the examples there. One example would be to change the file permissions seeting the s flag on file, so it can be executed by any user as if it would be the file owner. what i'm doing is the following...

> 
[B][I][kbear@HECHTNY]:~/Dev\> ls -la uidcheck
-rwxr-xr-x 1 kbear kbear 8621 Feb  6 15:42 uidcheck
[kbear@HECHTNY]:~/Dev\> ./uidcheck
real uid: 1000
effective uid: 1000
[kbear@HECHTNY]:~/Dev\> sudo chown root:root uidcheck
[kbear@HECHTNY]:~/Dev\> ls -la uidcheck
-rwxr-xr-x 1 root root 8621 Feb  6 15:42 uidcheck
[kbear@HECHTNY]:~/Dev\> sudo chmod u+s uidcheck
[kbear@HECHTNY]:~/Dev\> ls -la uidcheck
-rwsr-xr-x 1 root root 8621 Feb  6 15:42 uidcheck
[kbear@HECHTNY]:~/Dev\> ./uidcheck
real uid: 1000
effective uid: 1000
[kbear@HECHTNY]:~/Dev\> [/I][/B]


the uidcheck file is a simple program that prints the userid as well as the effective userid (using getuid(), geteuid() respectively, see code below). after changing the owner to root and changing the file permission w/ the s flag i would expect the ids to be different and not the same. i did the same thing on the live-cd provided w/ the book and there it seems to work all fine.

Am i missing something or is this a security feature preventing this kind of change of file permissions.

thanks for the help

regards


```

#include <stdio.h>

int main(){
    printf("real uid: %d\n",getuid());
    printf("effective uid: %d\n",geteuid());
}

```

---

