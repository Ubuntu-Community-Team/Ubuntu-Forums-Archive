---
title: "A new library instance for each new seat?"
date: 2013-10-26
forum: Programming Talk
---

### Post by kangaba on 2013-10-26
Hi,
On Linux the X.org server runs on seat 7 by default and I can start a new (parallel) desktop session say on seat four: Ctrl+Alt+F4.
I wonder if the new session starts its own library instances or uses the same ones from seat seven, ... is there any documentation/policy on this?

For example, in this case is there a parallel Qt library (or Gtk or whatever libraries are installed) running on seat four?

---

### Post by Bachstelze on 2013-10-26
Shared libraries are thus named for a reason. When several programs use the same shared library, only one copy of the library is loaded in memory, and all programs use it (since it is the same code, there is no purpose in loading it several times). The same is true for programs, by the way: if you run a program several times, only one copy of it is loaded in memory.

---

### Post by kangaba on 2013-10-26
Thanks,
I'm somewhat confused,
I just changed a function in Qt 5.2 beta (QDir::homePath()) into a singleton, recompiled and installed it (to /usr/local) and checked with a Qt app of mine that it works: QDir indeed returns a cached QString of my home path: "/home/fox".
Then I created a new seat (login as James) and used my Qt app again to check what QDir::homePath() returns, and it returns "/home/James".

Since it returns different results it kinda seems to indicate it's a different Qt instance, could you please explain?


```

QString QDir::homePath()
{
    static QString home_path = QFileSystemEngine::homePath();
    qDebug() << "QDir::homePath(): returning: " << home_path;
    return home_path;
   //OLD VERSION ==>
    //return QFileSystemEngine::homePath();
  //<== OLD VERSION
}



```

---

### Post by Bachstelze on 2013-10-26
Well, it seems the function basically returns the home directory of the current user. I could give you a program that does the same thing :

```

#include <stdio.h>
#include <stdlib.h>

int main(void)
{
    char *p = getenv("HOME");
    printf("%s\n", p);
    return 0;
}

```
Of course, if you run it as different users, it will print different things, but it's still the same program.

---

### Post by kangaba on 2013-10-26
That's not the point, the point is that it's a singleton using internally a cached static QString, so since it's the same library instance on both seats, as you say, why does it return different values on different seats?

---

### Post by ofnuts on 2013-10-26
> **kangaba said:**
> 

Since it returns different results it kinda seems to indicate it's a different Qt instance, could you please explain?

You share code (executable and libraries), but not data. Even "static" data in the modules is distinct between execution instances(*).

(*) it's actually common until written to (this is known as "copy on write")

---

### Post by kangaba on 2013-10-26
> **ofnuts said:**
> You share code (executable and libraries), but not data. Even "static" data in the modules is distinct between execution instances(*).

(*) it's actually common until written to (this is known as "copy on write")

That explains it, thanks a lot.

---

