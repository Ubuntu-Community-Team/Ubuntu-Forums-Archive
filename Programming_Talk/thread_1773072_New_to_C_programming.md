---
title: "New to C programming"
date: 2011-06-01
forum: Programming Talk
---

### Post by muppy80 on 2011-06-01
Hi all,
i need to learn to program in C. I'm totally new to this language.
I installed Anjuta and made this small program which i took from an on-line tutorial

#include <iostream.h>
int main()
{
cout << "Hello World!" << endl;
return 0;
}

i try to compile it, but it give me an error which says that iostream does not exist.

How to solve this problem ??

Best regards,
Andrea

---

### Post by frankbooth on 2011-06-01
That's C++ code :), a Hello World program written in C should look something like this:
```

#include <stdio.h>
int main()
{
printf ("Hello World!\n");
return 0;
}

```

---

### Post by seawolf167 on 2011-06-01
> **frankbooth said:**
> That's C++ code :), a Hello World program written in C should look something like this:
```

#include <stdio.h>
int main()
{
printf ("Hello World!\n");
return 0;
}

```

Aye :P, and never ever ever use system("pause"), use cin.get() instead!

I also like Geany for coding

```
sudo apt-get install geany
```

---

### Post by The Cog on 2011-06-01
Moved to programming talk.

I also like geany, but since I've never looked at Anjuta I can't offer a comparison.

---

### Post by zobayer1 on 2011-06-01
If you are interested in C++ actually:
```

#include <iostream>

int main() {
    std::cout << "Hello World" << std::endl;
    return 0;
}

```

Or more convenient:
```

#include <iostream>
using namespace std;

int main() {
    cout << "Hello World" << endl;
    return 0;
}

```

Lots of ways to do this, and u should know, every C program is also a C++ program :p

And about geany, its output screen sux, you can change that to normal terminal by doing this:
Go to Edit -> Preference -> Tools , there, in Terminal field, just write gnome-terminal.

---

### Post by ThatCoolGuy220 on 2011-06-02
yes some includes on tutorials are windows base so u must research first 

also this:
```
system("Pause");
```will not work, better to use:
```
cin.get();
```instead this is better also because is cross platform.


oh if you use Geany you can set up your own templates by acceding via terminal to:

```
/usr/share/geany/templates/files
```and gedit:

any of the files you should use or create a new one just remember to keep the right extension..

Also

The above can be done by having root access on nautilus.

---

### Post by zobayer1 on 2011-06-02
Why would someone need to use system("pause"); or cin.get() either?

These are normally used to halt the output screen, which is a problem in Dev C++ in windows, in linux, I don't think they are even necessary, no matter where you code. If you use something like geany, it will hold output screen for you, and if you use terminal, it will not just go away, it will show you the outputs.

---

### Post by ThatCoolGuy220 on 2011-06-02
Well it would not harm either, I include the anyway cause I learned that way though if don't do it it wouldn't harm

---

### Post by zobayer1 on 2011-06-02
> **ThatCoolGuy220 said:**
> Well it would not harm either, I include the anyway cause I learned that way though if don't do it it wouldn't harm

Well, obviously they won't harm. But as I have seen for some of my friends, these are often misleading, I mean, many people uses them without even trying to know why they are using them ...

---

### Post by ThatCoolGuy220 on 2011-06-02
thats a good point

---

