---
title: "Global Variables in OpenGL"
date: 2010-03-04
forum: Programming Talk
---

### Post by daemon3 on 2010-03-04
From the examples I've seen of OpenGL, the programmer uses global variables for things that are going to be update, such as the angle of a rotating object.  i.e.:
```
 int _angle = 0.0f; //Outside any function or class.
void update(int value)
{
     _angle += 5.0f
}

int main (int argc, char **argv)
{
     /*....*/
     GLTimerFunc(....,update....);
     /*.....*/
}

```

I've heard from many programmers that global variables are a no-no in programming.  Are there cases where global variables are necessary, like in OpenGl?  Thanks.

---

### Post by DougB1958 on 2010-03-04
More often than not, global variables are worse than the problem they "solve," because parts of your program can affect each other in unintended ways by reading and writing globals. But there aren't absolutes in programming any more than in any other part of life. Using OpenGL through a window library such as GLUT (which looks about like what you're doing, although I don't recognize your example "GLTimerFunc" function) that has a fairly simple set of callbacks to handle events, you (a) almost certainly need those callbacks to communicate with each other, and (b) have no way beside global variables to do it. So you bite the bullet and think very carefully about how the globals will be used....

---

### Post by daemon3 on 2010-03-05
Sorry, I meant glutTimerFunc.  Man, you'd think the developers could stick to one name. :P

Is there a way to completely avoid global variables in updating with timers in OpenGL?

---

### Post by DougB1958 on 2010-03-05
> **daemon3 said:**
> Is there a way to completely avoid global variables in updating with timers in OpenGL?

As a practical matter, not if you're using GLUT for handling windows and events. The timer callback almost certainly needs to update some state that the display callback will use to decide what to display, and pretty much the only way you can share that state through GLUT is globals.

As a theoretical matter, you can probably find a language that has OpenGL bindings and lets you define callback functions in a scope that "sees" the necessary state variables while hiding them from the rest of the program. For example, you could do this by using static member functions of a C++ class as the callbacks. But well-documented code with global variables and a little self-discipline about only using the globals to communicate necessary state between callbacks is probably easier to develop, more reliable, and clearer than such a solution.

Also, don't confuse GLUT with OpenGL. GLUT is a library that provides simple access to windows and input events for OpenGL, but there are other libraries that do that too. For instance, I've used an OpenGL extension for GTk+ (it's called gtkglext, but I don't remember right off where to find it or who wrote it) that allows you to use GTk+ for windowing and event handling; most GTk+ callbacks take a piece of user-defined data as an argument, which you could probably use to pass around a pointer to a block of non-global state information. But here again, if what you're looking for is a simple entre into OpenGL programming rather than a professional user interface library (and its learning curve), you're better off with the globals.

---

