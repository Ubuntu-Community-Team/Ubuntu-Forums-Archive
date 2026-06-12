---
title: "[SOLVED] cannot run C file..."
date: 2007-08-27
forum: Programming Talk
---

### Post by amirseg on 2007-08-27
Hi,
I am trying to compile a c file, I can compile it but not run it.... I got no clue what the problem is.
What I am writing is:
[I]amirseg@amirseg-PC:~/Desktop/C$ more test.c

#include <stdio.h>

int main(){
        printf("start");

        return 0;
}

amirseg@amirseg-PC:~/Desktop/C$ gcc -Wall test.c -o test
amirseg@amirseg-PC:~/Desktop/C$ test
amirseg@amirseg-PC:~/Desktop/C$ 
[/I]

I would be glad if you could help me

Amir

---

### Post by Lord Illidan on 2007-08-27
Try typing

```
./test
```If that doesn't work, you might have to set the permissions with > chmod 775 test before you execute it.

Also, I would do ```
printf("start\n")
``` in order to start a new line afterwards, otherwise it will look messy..

---

### Post by raijinsetsu on 2007-08-27
You have to type "./test" from the Desktop directory.
Or, you could time "/home/YourUserName/Desktop/test" from anywhere.

The reason: your Desktop directory is not in the systems PATH variable(and you wouldn't want it to be).
When you type "test", your terminal(Bash Shell) will search the PATH, in order, for the first match, and run that.

---

### Post by amirseg on 2007-08-27
Lord Illidan, raijinsetsu thanks, it did worked when I wrote ./test

Now, is there a way I could add the folder /home/YourUserName/Desktop/C to the path? so I could run the files just by their name? (even if under that directory I hav more sub-directories)?

---

### Post by raijinsetsu on 2007-08-27
I wouldn't suggest it. This is the default behavior because of security concerns.
But, if you really want it:
edit "~/profile"
add "set PATH=$PATH;/home/YourUserName/Desktop" at the bottom

It's strongly suggested you DON'T do this though.

---

### Post by amirseg on 2007-08-27
I guess that I should not do it if you said twich thet  you don't suggest it :)
thanks! :)

---

### Post by CptPicard on 2007-08-27
An even more obvious solution is not to name your executable "test", because it's a shell builtin, that gets run instead :)

This is a really classic problem, you know; I guess almost everyone has once tried running a test program called.. test. :)

---

