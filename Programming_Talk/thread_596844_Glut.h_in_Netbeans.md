---
title: "Glut.h in Netbeans"
date: 2007-10-30
forum: Programming Talk
---

### Post by Lord C on 2007-10-30
I have installed GLUT (FreeGL), NetBeans, and the NetBeans C++ plugin.

I created a very simple little OpenGL program in Uni (MS Visual Studio :\).
I am trying to edit my little .cpp file.

When I run gcc -lglut truck.cpp the only error I get is an int to double conversion error.

When I try to build the code in NetBeans, I get a load of undefined references to all the gl commands.

I tried adding /usr/X11R6/include,  /usr/X11R6/lib, /usr/include/GL, and /usr/include to the "Options > C++ > C++ Compile" in NetBeans.

I get the feeling I need to point NetBeans to the Glut.h file, but I'm not sure exactly where/how to do this.

Thanks in advance for any replies.

PS: The reason I am using NetBeans is because I used this in Uni for my Java classes, and I don't know any specific linux C++ IDEs. I also figured if I can use NetBeans for all my coding, that would be an obvious advantage.

---

### Post by hecato on 2007-10-30
undefinied references are the (and have nothing to do with the compiler in most cases see a little explanation here: [**Re: c++ compiling and linking help**]("http://ubuntuforums.org/showthread.php?p=3651570#post3651570"))

```
-lthingLibrary
```taht you pass to g++ or gcc at the end, they call the linker passing those arguments that where not handled by the compiler.

Yes you have added the include directories to the project, but are you sure you have added the lybraries and the library paths if necessary? ;).

---

### Post by Lord C on 2007-10-30
I have done everything that I knew how to do.

I havn't been programming OpenGL/C++ that long, and I have never been doing it in Linux.
At Uni, glut was installed, and using #include <GL/glut> worked fine in MS VS. So I don't have a clue...

I checked the thread your linked to. But it didn't help me.

g++ truck.cpp -lglut
Works fine,  it isn't giving any Glut errors, like NetBeans does.

I know I can use gEdit, but I really need a debugger.

---

### Post by Tomosaur on 2007-10-30
While I agree that netBeans is great for Java - I think you may find it more appealing to use Eclipse or KDevelop for C++ (Eclipse will also require a plugin, it being designed to develop Java apps). I think netBeans is too 'Java-oriented' to stand up on its own with other languages. Eclipse is abstract enough to let you get on with things. KDevelop is intentionally designed as a multi-language IDE.

---

### Post by hecato on 2007-10-30
OK, you need to go where you have put the paths for search for include files those are the compiler options. Then you should locate the linker options, there you can add the libraries, the ones that you pass in cmd line like **-lglut** but in this case is only necessary to write the name **glut** of the library without the -l flag, it is write automatically, also dont remember if you need to add the path to where the libraries are included, but I hope and guess not IIRC.

That is why I link to that thread, for you to see than a compiler and a linker are different things, thus adding the include paths and #include <GL/glut.h> doesn't make any impact on the linker paths, input files or general behaviour.

---

### Post by Qrikko on 2008-02-18
Ok, if you are new to this, I hope I can explain it very simple :) because it is simple :)


The Problem is that your makefile don't link to GL, GLU and glut (I prefere to link them all in even if I don't need it, glut should be enough if you are using glut)

So what to do?
it's pretty simple, you can right-click your project folder in netbeans (I am using 6.0.1 but I really don't see that there should be any difference from 5.5.x) And choose properties.

here you go to Linker | Libraries
and add library (will open a dialog)
choose Add option and other option
and type in: -lglut

hope it's not to confusing and that it helps

(Observe that you can put other dependencies here as well.. if you need GL or GLU for example you just put -lGL and/or -lGLU)

---

### Post by indikakumara on 2010-03-13
open netbens IDE New Project->C/C++ ->C++ Application
then open Properties for that project
go to Linker under the library add option  -lglut -lGL -lGLU -lGLEW

before that you must install the openGL libraries

---

