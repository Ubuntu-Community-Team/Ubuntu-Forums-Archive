---
title: "&quot;Undefined Reference&quot; Error From ld"
date: 2007-06-15
forum: Programming Talk
---

### Post by ankursethi on 2007-06-15
I got an old MSDOS program (in C) from somewhere. It's dated 1990. After a lot of fixing, I finally managed to remove all syntax errors. Now I get just this :
```
/tmp/ccK3UyYQ.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
```

WTH?

---

### Post by WW on 2007-06-15
The same error is discussed in this thread: [http://ubuntuforums.org/showthread.php?t=462153](http://ubuntuforums.org/showthread.php?t=462153)

By any chance have you given your C program the extension .cpp?  I can create the same error by creating this file, called **basic.cpp**:
```

#include <stdio.h>

main()
{
    int x;
    x = 100;
    printf("x = %d\n",x);
}

```
and compiling it with gcc:
```

$ gcc basic.cpp -o basic
/tmp/ccsMTkb2.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
$

```
But if I instead call the file basic.c, all is well:
```

$ cp basic.cpp basic.c
$ gcc basic.c -o basic
$ ./basic
x = 100
$

```
Conclusion: don't use the .cpp extension for C files.

---

### Post by ankursethi on 2007-06-15
Strange. The file was named .C initially. But after renaming it to basic.c from BAS-INT.c solved the problem. Do you think the "-" in BAS-INT.c was causing the problem?

PS : The program is not working :-(. Looks like I'll need to hack it some more.

---

### Post by WW on 2007-06-15
Was the extension .c or .C?  Linux file names are case-sensitive, and .C is a common extension used for C++.  If I use the extension .C, I get the error:
```

$ cp basic.c basic.C
$ gcc basic.C -o basic
/tmp/ccQ5SKGa.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
$

```

---

### Post by ankursethi on 2007-06-15
Erp! It *was* C. Sheesh, gcc is too touchy about small things.

Since I don't want to create yet another thread, can somebody familiar with ncurses tell me what's wrong with this code : 
```
#include <ncurses.h>

int main (int argc, char* argv[]) {
    WINDOW* MainWin ;
    int startX, startY, width, height ;
    initscr() ; cbreak () ; noecho() ;
    
    height = 3 ; width = 10 ;
    startY = (LINES - height)/2 ;
    startX = (LINES - width)/2 ;
    printw ("Hit 'x' to exit.") ;
    MainWin = newwin (height, width, startY, startX) ;
    box (MainWin, 0, 0) ;
    wprintw (MainWin, "This be a window!") ;
    wrefresh(MainWin) ;
    while (getch() != 'x') { continue ; }
    endwin() ;
}   
```

It's supposed to create a small window with a border. Strangely, it doesn't. wborder() doesn't work either.

---

### Post by ankursethi on 2007-06-15
Okay. Got it. It seems that the newwin() function doesn't work in the main() function. Can somebody explain why? Is it illegal to have 2 windows within the same scope (function)?

EDIT : Dang! It stopped working *again*! I don't really know what the problem is. Help!

---

### Post by ankursethi on 2007-06-15
Okay, this is getting *verry* annoying. It works if I refresh() the window BEFORE creating the new window, but if I refresh AFTER creating the new window, nothing happens. What in the name of Tux is going on here?

---

### Post by jestinjoy on 2010-08-17
I also had the same problem with the .C file written in Windows.

What I did was renamed it to <filename>.c. Usually it come as <filename>.C in windows Turbo C. That is just change it to small letters.

Otherwise compile with -lstdc++ option

gcc <sourcefile> -lstdc++

Hope this will help you.

---

