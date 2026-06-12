---
title: "how to write a c program in ubuntu 10.04 LTS"
date: 2013-05-14
forum: New to Ubuntu
---

### Post by tanmoygolui on 2013-05-14
wheh i write vi one.c, the vi editor is opened.
But when i write #  (for writing #include<stdio.h>)an error is generated.And the whole thing is lost.Please help me from this problem  :)

---

### Post by squakie on 2013-05-14
Don't you have gedit or one of the other GUI editors?  I'd just use them.  Years ago we "had" to use vi - and I'm not the only one who is glad we don't all have to now.  Some love it, but you have to understand vi to use it - it's not a wysiwig editor.  It can be very powerful, but it can also be a headache.

If you *must* use vi, I would suggest one of the many guides out on the net, like this one: [http://basicconfig.com/linux/vi]("http://basicconfig.com/linux/vi")

---

### Post by Impavidus on 2013-05-14
Before to can start typing in vi or vim (vi is actually a synlink to vim), you have to enter insert mode, for example by pressing i.

I recomment you first download a manual for vim and study it before you try using it. Or just use one of the graphical text editors.

---

### Post by Warren Hill on 2013-05-14
10.04 stopped being supported a few days ago so I suggest you upgrade first.


Once you have installed 12.04 or later install the tools

```
sudo apt-get install build-essential
```

Now if you want to do this in a terminal 

```
nano hello.c
```

or use gedit and save the file as hello.c

It's much easier than learning **vi**

Write your first program

```

#include <stdio.h> 

int main (void){
    printf("Hello World\n");
    return (1);
}

```
Compile it
 
```
gcc -o hello hello.c
``` 
Run it

 
```
./hello
```

You should see

```
Hello World
```

If you do it works.

---

