---
title: "Help using Ncurses"
date: 2007-09-10
forum: Programming Talk
---

### Post by Yes on 2007-09-10
Well, I'm trying to teach myself how to use the Ncurses library, but I'm already having trouble with the Hello World program.  When I try running it, I get these errors:

[img]http://harrypottermovie7.com/upload/images/cqs1189458956c.png[/img]

I have no idea what that means...the "multiple definitions" seems sorta like I have multiple versions of Ncurses installed, and they're conflicting with each other, but that's just an uneducated guess.  So, does anyone know what my problem might be?

Thanks.

---

### Post by slavik on 2007-09-10
post the code please (surrounded by code tags)

---

### Post by Wybiral on 2007-09-10
Yeah, if you post the code and the command you are using to compile it then we can definitely help figure out whats wrong.

---

### Post by Yes on 2007-09-10
```
#include <iostream>

#include <cstdlib>

#include <ncurses.h>

using namespace std;

int main()
{
	initscr();			
	printw("Hello World !!!");	
	refresh();			
	getch();			
	endwin();			

	return 0;
}
```

---

### Post by Yes on 2007-09-11
The guide I'm using is written for C, and I'm using C++, would that be my problem?

---

### Post by robdor on 2007-09-11
No, that shouldn't be a problem.  What is the command that you are using the compile it?  I used the command below to compile and everything worked as expected.

```
g++ -lncurses -o test ncurses_test.cpp
```

---

### Post by Yes on 2007-09-11
My build command is 

```
g++ -Wall -lncurses -o "%f"
```

where "%f" is replaced with the file name.  Now I get these build errors:

```
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status
```

---

### Post by xtacocorex on 2007-09-11
Don't think you need the cstdlib.h in your includes.

---

### Post by Yes on 2007-09-11
Yeah, I know.  But that's not what's causing the errors.

---

### Post by dwhitney67 on 2007-09-12
> **Yes said:**
> My build command is 

```
g++ -Wall -lncurses -o "%f"
```

where "%f" is replaced with the file name.  Now I get these build errors:

```
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status
```

xtacocorex is right, you do not need to include cstdlib.h.

Aside from that, I tried your program on my system and it compiles and runs fine.  I compiled using:

[FONT="Courier New"]g++ -Wall ncurses.cpp -lncurses[/FONT]

Then I ran "a.out".

You may want to consider re-installing "build-essentials".

---

### Post by Lux Perpetua on 2007-09-13
> **Yes said:**
> My build command is 

```
g++ -Wall -lncurses -o "%f"
```

where "%f" is replaced with the file name.  Now I get these build errors:

```
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status
```

You're probably just forgetting to specify a source file. "-o file.cpp" means the compiled executable is to be called file.cpp, not that you want to compile file.cpp. Fixing that should fix your problem.

---

### Post by Yes on 2007-09-13
Ugh, I'm an idiot.  I had my execute arguments screwed up.  Thank's, it's all sorted out now.

---

