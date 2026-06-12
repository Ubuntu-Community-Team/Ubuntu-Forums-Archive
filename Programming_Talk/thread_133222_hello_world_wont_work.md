---
title: "hello world wont work"
date: 2006-02-19
forum: Programming Talk
---

### Post by jswan on 2006-02-19
```

#include <stdlib.h>
#include <stdio.h>

int main() {
   printf("helllo\n");
   return 0;
}

```

```
gcc test.c -o test
```
After i compile this and run the output it never prints to the screen
What could cause this?  I've been using my schools linux boxes for programming in the past and I am just starting to get my own up and running.

thanks!

---

### Post by skirkpatrick on 2006-02-19
Are you running it from a terminal window?  Double-clicking it in Nautilus will not cause a terminal window to open and show you the results.

---

### Post by darth_vector on 2006-02-19
you do know that there is a program called test, dont you? try running```
./test
```

---

### Post by Jessehk on 2006-02-19
First step: open text editor.

type in the following:

```


#include <stdio.h>

int main()
{
    printf("Hello, world!\n");

    return 0;
}


```

Save the file as hello.c

enter the following in a terminal window:

```

gcc hello.c -o hello

```

While in the terminal window, type ./hello to run.

---

### Post by jswan on 2006-02-19
thanks darth_vector, it worked

definately a rookie mistake

---

### Post by darth_vector on 2006-02-19
no worries mate. i've done that too :D

---

### Post by Plank117 on 2006-02-20
May the favor of the compiler be with you, o' seeker of wisdom.

---

### Post by scourge on 2006-02-20
Yet another programmer reinventing the wheel.
If people would just learn to use apt-get they wouldn't have to write their own hello world app, and they could instead spend that time optimizing Linux kernel.

> sudo apt-get install hello
hello

:D

---

### Post by HwyXingFrog on 2006-03-25
[QUOTE=Jessehk]First step: open text editor.

type in the following:

```


#include <stdio.h>

int main()
{
    printf("Hello, world!\n");

    return 0;
}


```

Save the file as hello.c

enter the following in a terminal window:

```

gcc hello.c -o hello

```

While in the terminal window, type ./hello to run.[/QUOTE]
It is so simple it was difficult to find something this basic on the forums.

For some reason i was trying to run it without ./ and the first time I tried it with the ./ it said the file was not found. So i deleted everything and started over, then it worked for some reason.  Sounds like something that would happen on Windows, I know.

Thanks, I was starting to think I wouldn't be able to to it.

---

### Post by sharperguy on 2006-03-25
[QUOTE=scourge]Yet another programmer reinventing the wheel.
If people would just learn to use apt-get they wouldn't have to write their own hello world app, and they could instead spend that time optimizing Linux kernel.



:D[/QUOTE]

d8=

Thanks, I was just looking for a useless program such as that.

Wouldnt this make more sense though:

```
#include <stdio.h>

int main()
{
    printf("Please to not attempt to talk to the command line\n");

    return 0;
}

```

Then stick it in /usr/bin

---

### Post by Drakx on 2006-03-25
lmao

---

