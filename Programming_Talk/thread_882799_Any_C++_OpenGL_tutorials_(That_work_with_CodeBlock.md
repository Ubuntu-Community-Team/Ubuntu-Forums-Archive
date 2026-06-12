---
title: "Any C++ OpenGL tutorials? (That work with Code::Blocks)"
date: 2008-08-07
forum: Programming Talk
---

### Post by Newuser1111 on 2008-08-07
Any C++ OpenGL tutorials that work with Code::Blocks IDE?

And is there anything better than OpenGL that also works with Windows?

---

### Post by Zugzwang on 2008-08-07
Essentially all the tutorials work with Code::Blocks as well. You will just have to figure out how to include the libraries to your project. You can read another tutorial (or the docs or Code::Blocks) for that.

If there's anything better than OpenGL depends on what you are actually trying to do with it.

---

### Post by Newuser1111 on 2008-08-07
Why doesn't "glut" work?

---

### Post by Zugzwang on 2008-08-08
> **Newuser1111 said:**
> Why doesn't "glut" work?
Your post is lacking every detail that might help to fix that problem:

1. How did you check that its not working (example code, command used to compile), how you ran
2. Which error messages do you get (*Please* copy&paste)
3. Did you really read the FAQ (read [this]("http://ubuntuforums.org/showthread.php?t=691451"))?

---

### Post by nrs on 2008-08-08
Well, what do you mean by C++? Object-oriented code? Code that is just compilable by a C++ compiler?  

What's wrong with the nehe C/SDL ports?

---

### Post by POW R TOC H on 2008-08-08
Everything works with Code::Blocks. Code::Blocks is just an IDE, not a compiler. It uses GCC (or other compilers, but GCC by default).
Simply see what libs you must link with, and add them to your project's build options.

---

### Post by Newuser1111 on 2008-08-08
EDIT:
GLAUX:
```

||=== OpenGL_tut1, Debug ===|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|1|error: windows.h: No such file or directory|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|4|error: GL/glaux.h: No such file or directory|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|5|error: &#8216;HGLRC&#8217; does not name a type|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|6|error: &#8216;HDC&#8217; does not name a type|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|7|error: &#8216;HWND&#8217; does not name a type|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|8|error: &#8216;HINSTANCE&#8217; does not name a type|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|10|error: &#8216;TRUE&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|11|error: &#8216;TRUE&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|12|error: &#8216;LRESULT&#8217; does not name a type|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|30|error: &#8216;<anonymous>&#8217; has incomplete type|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|30|error: invalid use of &#8216;GLvoid&#8217;|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp||In function &#8216;int InitGL(<type error>)&#8217;:|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|38|error: &#8216;TRUE&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|40|error: &#8216;<anonymous>&#8217; has incomplete type|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|40|error: invalid use of &#8216;GLvoid&#8217;|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp||In function &#8216;int DrawGLScene(<type error>)&#8217;:|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|44|error: &#8216;TRUE&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|46|error: &#8216;<anonymous>&#8217; has incomplete type|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|46|error: invalid use of &#8216;GLvoid&#8217;|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp||In function &#8216;GLvoid KillGLWindow(<type error>)&#8217;:|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|50|error: &#8216;ChangeDisplaySettings&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|51|error: &#8216;TRUE&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|51|error: &#8216;ShowCursor&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|53|error: &#8216;hRC&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|55|error: &#8216;wglMakeCurrent&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|57|error: &#8216;MB_OK&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|57|error: &#8216;MB_ICONINFORMATION&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|57|error: &#8216;MessageBox&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|59|error: &#8216;wglDeleteContext&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|61|error: &#8216;MB_OK&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|61|error: &#8216;MB_ICONINFORMATION&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|61|error: &#8216;MessageBox&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|65|error: &#8216;hDC&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|65|error: &#8216;hWnd&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|65|error: &#8216;ReleaseDC&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|67|error: &#8216;MB_OK&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|67|error: &#8216;MB_ICONINFORMATION&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|67|error: &#8216;MessageBox&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|70|error: &#8216;hWnd&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|70|error: &#8216;DestroyWindow&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|72|error: &#8216;MB_OK&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|72|error: &#8216;MB_ICONINFORMATION&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|72|error: &#8216;MessageBox&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|75|error: &#8216;hInstance&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|75|error: &#8216;UnregisterClass&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|77|error: &#8216;MB_OK&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|77|error: &#8216;MB_ICONINFORMATION&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|77|error: &#8216;MessageBox&#8217; was not declared in this scope|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|81|error: &#8216;BOOL&#8217; does not name a type|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|227|error: &#8216;LRESULT&#8217; does not name a type|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1/main.cpp|281|error: expected initializer before &#8216;WinMain&#8217;|
||=== Build finished: 48 errors, 0 warnings ===|

```

GLUT:
```
obj/Debug/main.o||In function `display':|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1_2/main.c|8|undefined reference to `gluLookAt'|
obj/Debug/main.o||In function `main':|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1_2/main.c|13|undefined reference to `glutInit'|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1_2/main.c|14|undefined reference to `glutInitDisplayMode'|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1_2/main.c|15|undefined reference to `glutInitWindowSize'|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1_2/main.c|16|undefined reference to `glutInitWindowPosition'|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1_2/main.c|17|undefined reference to `glutCreateWindow'|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1_2/main.c|18|undefined reference to `glutDisplayFunc'|
/home/djk/Documents/DEV/CodeBlocks/OpenGL_tut1_2/main.c|19|undefined reference to `glutMainLoop'|
||=== Build finished: 8 errors, 0 warnings ===|

```

---

### Post by moma on 2008-08-08
@Newuser1111, follow this guide. 
[http://www.futuredesktop.org/codeblocks_on_ubuntu_8.04.html](http://www.futuredesktop.org/codeblocks_on_ubuntu_8.04.html)

Install the Code::Blocks IDE as instructed and 
read + perform the command(s) in [COLOR="Red"][Note 1][/COLOR] (it is; install the freeglut library and create a simple GLUT-project).

Then come back here, so I will help you to create and study other OpenGL projects. Ok?
;-)

---

### Post by Newuser1111 on 2008-08-08
> **moma said:**
> @Newuser1111, follow this guide. 
[http://www.futuredesktop.org/codeblocks_on_ubuntu_8.04.html](http://www.futuredesktop.org/codeblocks_on_ubuntu_8.04.html)

Install the Code::Blocks IDE as instructed and 
read + perform the command(s) in [COLOR="Red"][Note 1][/COLOR].

Then come back here, so I will help you to create a real OpenGL project. Ok?
;-)There's a problem,
The terminal wont open.

---

### Post by moma on 2008-08-08
Re-hello,

Can you press ALT + F2. It will open a "Run application" dialog.  
Then type "gnome-terminal" or type "xterm".  One of them should work. (I suppose you run GNOME desktop).
Then copy&paste the commands from the guide.

---

