---
title: "Qt simple cpp project doesn't build"
date: 2011-02-24
forum: Programming Talk
---

### Post by Nerdcore Steve on 2011-02-24
I've just installed Qt. I've got an old copy of C for dummies and thought I'd go through it and my C++ for dummies books before moving on to gui programming. But I can't build anything. Here's my code:

```

#include <stdio.h>

void main()
{
    printf("Goodbye cruel world!\n");
}


```

when I mouseover the include statment there is a "no such file or directory" message. Also the build menu is completely grayed out. Do I need to install minGW? I tried that with eclipse and then got distracted by other stuff.

What's the best way to get this running?

---

### Post by Vox754 on 2011-02-24
> **Nerdcore Steve said:**
> I've just installed Qt. I've got an old copy of C for dummies and thought I'd go through it and my C++ for dummies books before moving on to gui programming. But I can't build anything. Here's my code:

```

#include <stdio.h>

void main()
{
    printf("Goodbye cruel world!\n");
}


```

when I mouseover the include statment there is a "no such file or directory" message. Also the build menu is completely grayed out. Do I need to install minGW? I tried that with eclipse and then got distracted by other stuff.

What's the best way to get this running?

What do you mean you have "just installed Qt"?

Qt is not a program, it is a wide collection of libraries to program graphical user interfaces and many other things.

In general, it is best to learn to compile from the command line before attempting to use an IDE like Qt Creator or Eclipse.

Programming is hard. So you should expect to read a lot and learn by yourself before attempting to creating any meaningful graphical program.

See, for example, the sticky threads in this forum, which you missed: [Programming Tools and References](http://ubuntuforums.org/showthread.php?t=1006662), and [FAQ: Compiling your first C or C++ programs ](http://ubuntuforums.org/showthread.php?t=689635).

---

### Post by Nerdcore Steve on 2011-02-24
Yes, it's Qt creator, and I'm no stranger to GUI programming, just c and c++. I'm used to ide's working as soon as they're installed.

---

### Post by Vaphell on 2011-02-25
do you have build-essential package installed? It provides compilers, standard libraries, headers and whatnot.

---

### Post by Nerdcore Steve on 2011-02-25
I hadn't, but I've just installed it and restarted. This hasn't changed anything.

---

### Post by Nerdcore Steve on 2011-02-25
I've just successfully run a Qt example, so that must mean there's something I don't understand how to do in order to get a simple console program running.

hrm....

I think I'll take Vox754's advice after all and start with a text editor and the console.

Thanks guys.:)

---

### Post by Nerdcore Steve on 2011-02-28
I've figured out how to make a console app work in Qt Creator and it's really simple.

Just go to

file->New File or Project

Scroll down to Projects and choose Qt4 Console Application. Once the project is created, open main.cpp or whatever you named it, erase what's in there and paste in this code:

```

#include <stdio.h>

int main()
{
    printf("Yo yo! I'm all up in the console!");

    return 0;
}

```

Then right click on the project, build it. Right click again, and run that sucker! The output is on the bottom.

So... How do I marked this as solved?

---

### Post by Nerdcore Steve on 2011-02-28
Ah, I see

[http://ubuntuforums.org/showthread.php?t=954716]("http://ubuntuforums.org/showthread.php?t=954716")

---

