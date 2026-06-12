---
title: "Am I being stupid?"
date: 2014-07-19
forum: Programming Talk
---

### Post by Owain_Parry on 2014-07-19
Hi, I'm trying to use GCC to compile a program, but when I run it in the terminal I get no output. The program is:
```

#include <stdio.h>

int main()
{
    printf("Hello, World!\n");

    return 0;
}

```

and to compile it I typed 'gcc -o test main.c'. However when I run the program in the terminal I don't see anything. Have I done something wrong?

---

### Post by steeldriver on 2014-07-19
If the program compiles successfully, gcc will not **output** anything in the terminal - however it should have produced a **file** called 'test' in the current directory

---

### Post by Owain_Parry on 2014-07-19
Sorry, prehaps my wording wasn't clear. When I run test in the terminal I don't get any output. I don't see 'Hello, World!', as I was expecting.

---

### Post by trent.josephsen on 2014-07-19
test is a shell command:
```
$ which test
test: shell built-in command
```

Type ./test to make sure you're running the file in the current directory.

---

### Post by Owain_Parry on 2014-07-19
Thankyou!

---

### Post by ofnuts on 2014-07-19
This is automatic hazing put in Unix from the origins. Every Unix user is bitten by this at least once. You got your first badge, welcome to the club :)

---

### Post by donkyhotay on 2014-07-21
You're not stupid, it's an easy mistake. Test is such an obvious name for a first program, but is actually a pretty bad choice because there is a program called test. For future reference, when coming up with the name of something try typing it into bash first to make certain something else doesn't use it already use it. Or if you really want the name to be something specific, just remember to put a ./ in front of it to specify the program.

---

