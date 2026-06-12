---
title: "NetBeans 5.5.1 C++ Pack (problem with code completion)"
date: 2007-06-23
forum: Programming Talk
---

### Post by gohatto on 2007-06-23
Hi!

Maybe someone here would be so kind and try to help me...
I'm using Ubuntu 7.04 and I have a problem with code completion in NetBeans 5.5.1 CND and I'm a little bit frustrated right now....

I installed Netbeans, then CND, Created new C++ Project. Added new source file, with #include <GL/glut.h> directive. 
Whole code was compiled without errors, and that's fine. 
There were some problems with linking but I've added "glut", "GL", "GLU" string to linker parameters in Project Properties.

The main problem is the code assistant. When I'm hitting "glut" and press ctrl+space it shows functions from glut library but when I type "gl" (to type "glColor3ub...") and try to show the code completion pop-up it shows "No suggestions". The same thing is with GLU library.

I've installed GL, GLU, glut libraries (they all sit calmly in /usr/include/GL).
I've added the /usr/include and /usr/include/GL to C++ section.
I think that the Netbeans is able to find those *.h files because, as I said before, the glut (and the glX) functions are shown properly but there is no sign of "gl" and "glu" functions in code completion...

I don't have idea why glut and glX are working fine, and gl and glu aren't... If anyone have similar problem, know where to look for an answer or have some suggestions I would be much obliged...

---

### Post by kknd on 2007-06-23
Code completion in NetBeans C++ pack are not good. CC in the eclipse plugin for C/C++ aren't so good either.

The best code completion thing that i've found for C/C++ was when I used Vim + icomplete + icomplete plugin.

---

### Post by gohatto on 2007-06-23
Yea, ok. There is VIM, there is Emacs, but in fact after writing a C project in VIM I would like to use something more user friendly. 
I've tried kDevelop but it's rather poor when it comes to code assistant. 
CDT is, like Eclipse itself, extremely slow to me.
Anjuta is too poor to be a full IDE in my opinion. 
So there is NetBeans - much faster than Eclipse, user-friendly but with code completion working in 50%...

Don't get me wrong - I want to use NetBeans C++ Pack and I would like to know if someone had problem like this or know what could it be caused by...

---

### Post by kknd on 2007-06-24
I used Netbeans C/C++ for a long time, and I had this same problem. I've had the same result as you, the code completion worked + / -.

I think the best IDE with code completion is the new KDevelop version (you tested the "new" or some old version?).

I dont liked Anjuta 1.* too, but 2.* seems promising.

---

### Post by gohatto on 2007-06-24
I've tested kDevelop 3.4.0, It's fine if it comes to loading headers of external libraries and add ing it to the kDevelop indexer but it's not as user-friendly as in Eclipse of Netbeans.
I mean when you type few letters it will complete your func name, and show what arguments you need to pass. The problem is that you see all those arguments at one time, and when I try to input for example second one (from 8 to pass) the pop-up dissapears... Also when I type the arguments it doesn't show me which one I'm passing right now and what type it should be.
I know maybe I'm expecting too much from IDE, but after writing in Eclipse (Java project) (where the CC wasn't as slow as in C++ where I think he indexes all the libraries in the world, and when I type "glu(ctrl+space)" it takes about 20 seconds of 100% CPU used till CC pop-up appears) I am looking for something like this...

I don't want to use Visual C++, but it looks like I don't really have a choice :(

===================
EDIT
===================

Since yesterday I've been looking for the reason why the GL and GLU aren't indexed properly by the Netbeans CC and I've found something.

The GLU library was indexed after deleting
```
#include <GL/gl.h>
```
directive. So it means that the gl.h library is messing up.

I've checked whole file (gl.h) and noticed that the only part which is in conflict with NetBeans is this one:

```
#elif defined(__GNUC__) && (__GNUC__ * 100 + __GNUC_MINOR__) >= 303
# define GLAPI __attribute__((visibility("default")))
# define GLAPIENTRY
```

I'm using GCC 4.1 so the expression value is 401, so the GLAPI define looks like the line above.

gl.h is indexed properly by NetBeans when it is representing "extern", so it should look like

```
# define GLAPI extern
```

It is working fine if you delete this part of gl.h or for example (which I've done) add predefined macro (or change the existing one)
```
__GNUC_MINOR__=-200
```

I know that it isn't very clean solution... I'm not happy with cheating NetBeans about the version of installed GCC but unfortunately I am not a specialist in GNU C so maybe someone would find more elegant solution.
As far as I know the __attribute__ feature makes the GCC more verbose (warnings, errors) but I don't know how much functionality am I loosing in fact...

---

### Post by kknd on 2007-06-26
Well, Anjuta 2.2 (stable) is out.

I download Anjuta and its dependencies, compiled && instaled then.
After some hours trying it,  it crashed 4 times, changed the panels randomly. Code completion dont give sign of life. 

I uninstalled it...

Trying again NetBeans 5.5.1 C/C++ Pack:

Afetr changing some configuration in Options -> C/C++, the code completion worket very, very nice! Now it worked good (very quick too).

Also, the gdb integration are working flawlessly.

---

### Post by kingmanowar on 2007-07-03
I quickly tried eclipse + CDT 4 yesterday night and code completion is working really well and a lot faster than previous versions.
I have to test it with bigger projects now but it looks promising.

---

