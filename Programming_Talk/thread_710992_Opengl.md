---
title: "Opengl"
date: 2008-02-29
forum: Programming Talk
---

### Post by madfrenzy on 2008-02-29
Hey, I was trying to program opengl with c++ on netbeans but the problem is every time I try to run the program (the program works on visual studio) netbeans says "Running "/usr/bin/make  -f Makefile CONF=Debug" in /media/sda2/projects/C++/pro1/Mad

/usr/bin/make -f nbproject/Makefile-Debug.mk SUBPROJECTS= .build-conf
make[1]: Entering directory `/media/sda2/projects/C++/pro1/Mad'
mkdir -p build/Debug/GNU-Linux-x86
g++    -c -g -o build/Debug/GNU-Linux-x86/mad.o mad.cc
In file included from /usr/include/windef.h:246,
                 from /usr/include/windows.h:48,
                 from mad.cc:1:
/usr/include/winnt.h:1964:2: error: #error "undefined processor type"
/usr/include/winnt.h:1966: error: expected initializer before ‘*’ token
/usr/include/winnt.h:1977: error: ‘PCONTEXT’ does not name a type
/usr/include/winbase.h:1500: error: ‘LPCONTEXT’ has not been declared
/usr/include/winbase.h:1855: error: expected ‘,’ or ‘...’ before ‘*’ token
/usr/include/bits/time.h:69: error: redefinition of ‘struct timeval’
/usr/include/winsock2.h:101: error: previous definition of ‘struct timeval’
/usr/include/sys/select.h:78: error: conflicting declaration ‘typedef struct fd_set fd_set’
/usr/include/winsock2.h:56: error: ‘fd_set’ has a previous declaration as ‘typedef struct fd_set fd_set’
/usr/include/sys/select.h:112: error: declaration of C function ‘int select(int, fd_set*, fd_set*, fd_set*, timeval*)’ conflicts with
/usr/include/winsock2.h:611: error: previous declaration ‘int select(int, fd_set*, fd_set*, fd_set*, const timeval*)’ here
mad.cc:32: error: ‘::main’ must return ‘int’
make[1]: *** [build/Debug/GNU-Linux-x86/mad.o] Error 1
make[1]: Leaving directory `/media/sda2/projects/C++/pro1/Mad'
make: *** [.build-impl] Error 2

Build failed. Exit value 2."

I really need to fix this asap cause I've alot of assignments.  oh and by the way I'm on ubuntu gutsy 7.10

---

### Post by the_unforgiven on 2008-02-29
The errors shown are related to windows-specific files - winnt.h, winbase.h, windows.h, winsock2.h.

I suppose, you also have the WINE sdk installed on your system which is why the compiler is picking up the files - however, these are not required for a linux app to work.

So, I suggest you update your code to do a conditional compile using #if .. #else .. #endif constructs.

HTH.

---

### Post by madfrenzy on 2008-02-29
so there is no way to fix those files to work with ubuntu cause I need them to work on visual studio as wee (cause the instructor use windows :) )

---

### Post by the_unforgiven on 2008-02-29
There is - it's called [Conditional Compilation]("http://en.wikipedia.org/wiki/Conditional_compilation#Conditional_compilation") which is implemented using the C pre-processor.

---

### Post by madfrenzy on 2008-03-01
btw I'm a total newbie so I cant understand what u say :confused: this is the program I'm trying to run
-------------------------------------------
#include<windows.h>
#include<gl/Gl.h>
#include<gl/glut.h>
void myInit(void) {
    glClearColor(1.0, 1.0, 1.0, 0.0);       // set white background color
    glColor3f(0.0f, 0.0f, 0.0f);          // set the drawing color
    glPointSize(1.0);                 // a 'dot' is 4 by 4 pixels
    glMatrixMode(GL_PROJECTION);
    glLoadIdentity();
    gluOrtho2D(0.0, 640.0, 0.0, 480.0);
}
void myDisplay(void) {
    glClear(GL_COLOR_BUFFER_BIT);      // clear the screen
    int x=5;int y=5;
    do{
        //----------------------------------------------
        int z=y;
        z+=5;
//y+=5;
        //y++;
        do{
            
            
            
            glBegin(GL_POINTS);
            glVertex2i(x, y);          // draw the points
            glEnd();
            glFlush();    // send all output to display
            y++;
        }while (y<=z) ;
        //----------------------------------------------
        do{
            
            
            
            glBegin(GL_POINTS);
            glVertex2i(x, y);          // draw the points
            glEnd();
            glFlush();    // send all output to display
            x++;
        }while (x<=634) ;
        //---------------------------------------------
        
        
        z=y;
        z+=5;
//y+=5;
        //y++;
        do{
            
            
            
            glBegin(GL_POINTS);
            glVertex2i(x, y);          // draw the points
            glEnd();
            glFlush();    // send all output to display
            y++;
        }while (y<=z) ;
        
        
        
        //y+=5;
        do{
            
            
            
            glBegin(GL_POINTS);
            glVertex2i(x, y);          // draw the points
            glEnd();
            glFlush();    // send all output to display
            x--;
        }while (x>=5) ;
        
        //-------------------------------------------
    }while (y<=474) ;
}
void main(int argc, char** argv) {
    glutInit(&argc, argv);          // initialize the toolkit
    glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB); // set display mode
    glutInitWindowSize(640, 480);     // set window size
    glutInitWindowPosition(100, 150); // set window position on screen
    glutCreateWindow("MAD lOOP"); // open the screen window
    glutDisplayFunc(myDisplay);     // register redraw function
    myInit();
    glutMainLoop();                 // go into a perpetual loop
}

----------------------------------------------

and I have another question is there any program that can run this as it is (as it would run on visual studio on windows I mean??)

---

### Post by Kazade on 2008-03-01
<windows.h> is a Windows only header file, it has no place in a Linux program that is why it is failing compilation.

Remove the #include <windows.h> line, or do something like:

#ifdef WIN32
#include <windows.h>
#endif

then the program will using windows.h on Windows, but not on any other platform.

---

### Post by madfrenzy on 2008-03-01
when I remove windows.h it says"newfile11.cc:77: error: ‘::main’ must return ‘int"
and the program runs perfectly on windows so are there any header files I have to add or something??

---

### Post by Kazade on 2008-03-01
Just change the return type of main from void to int. Int is technically correct, normally main will return 0 on success and 1 (or some other number) on failure.

So change it to:

```

int main(int argc, char** argv) {
glutInit(&argc, argv); // initialize the toolkit
glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB); // set display mode
glutInitWindowSize(640, 480); // set window size
glutInitWindowPosition(100, 150); // set window position on screen
glutCreateWindow("MAD lOOP"); // open the screen window
glutDisplayFunc(myDisplay); // register redraw function
myInit();
glutMainLoop(); // go into a perpetual loop
return 0;
}

```

---

### Post by madfrenzy on 2008-03-01
when I did so it gives me 

Running "/usr/bin/make  -f Makefile CONF=Debug" in /home/madfrenzy/NetBeansProjects/Application_1

/usr/bin/make -f nbproject/Makefile-Debug.mk SUBPROJECTS= .build-conf
make[1]: Entering directory `/home/madfrenzy/NetBeansProjects/Application_1'
mkdir -p dist/Debug/GNU-Linux-x86
g++     -o dist/Debug/GNU-Linux-x86/application_1 build/Debug/GNU-Linux-x86/newfile11.o  
build/Debug/GNU-Linux-x86/newfile11.o: In function `myDisplay()':
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:15: undefined reference to `glClear'
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:27: undefined reference to `glBegin'
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:28: undefined reference to `glVertex2i'
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:29: undefined reference to `glEnd'
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:30: undefined reference to `glFlush'
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:38: undefined reference to `glBegin'
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:39: undefined reference to `glVertex2i'
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:40: undefined reference to `glEnd'
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:41: undefined reference to `glFlush'
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:55: undefined reference to `glBegin'
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:56: undefined reference to `glVertex2i'
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:57: undefined reference to `glEnd'
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:58: undefined reference to `glFlush'
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:69: undefined reference to `glBegin'
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:70: undefined reference to `glVertex2i'
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:71: undefined reference to `glEnd'
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:72: undefined reference to `glFlush'
build/Debug/GNU-Linux-x86/newfile11.o: In function `myInit()':
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:7: undefined reference to `glClearColor'
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:8: undefined reference to `glColor3f'
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:9: undefined reference to `glPointSize'
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:10: undefined reference to `glMatrixMode'
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:11: undefined reference to `glLoadIdentity'
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:12: undefined reference to `gluOrtho2D'
build/Debug/GNU-Linux-x86/newfile11.o: In function `main':
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:80: undefined reference to `glutInit'
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:81: undefined reference to `glutInitDisplayMode'
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:82: undefined reference to `glutInitWindowSize'
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:83: undefined reference to `glutInitWindowPosition'
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:84: undefined reference to `glutCreateWindow'
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:85: undefined reference to `glutDisplayFunc'
/home/madfrenzy/NetBeansProjects/Application_1/newfile11.cc:87: undefined reference to `glutMainLoop'
collect2: ld returned 1 exit status
make[1]: *** [dist/Debug/GNU-Linux-x86/application_1] Error 1
make[1]: Leaving directory `/home/madfrenzy/NetBeansProjects/Application_1'
make: *** [.build-impl] Error 2

Build failed. Exit value 2.

---

### Post by Kazade on 2008-03-01
Cool, that means the code compiled but just didn't link. You'll need to link the program to libGL.so and libGLUT.so (I think or something like that)

---

### Post by madfrenzy on 2008-03-01
so how to do that?? (srry but I'm a newbie here)

---

### Post by slavik on 2008-03-01
add -lgl as an option :)

---

### Post by madfrenzy on 2008-03-01
add it where?? and how??

---

### Post by madfrenzy on 2008-03-04
what are the header files required for this program?? in ubuntu ofcorse

---

### Post by Lster on 2008-03-04
This may possibly help. Especially Wybiral's post (it is the second one):

[http://ubuntuforums.org/showthread.php?t=395396&highlight=lster+wybiral+opengl](http://ubuntuforums.org/showthread.php?t=395396&highlight=lster+wybiral+opengl)

---

### Post by WW on 2008-03-04
Somehow madfrenzy has to tell Netbeans to add the options **-lGLU -lGL** (or something similar) to the g++ command that links the program.  I've never used Netbeans, but it appears from the output shown above that it creates a Makefile and uses make to compile and link the code.  Can someone help madfrenzy figure out how to tell Netbeans to use the OpenGL libraries?

---

### Post by Can+~ on 2008-03-04
The correct way to add them is:

> #include <GL/glut.h>
#include <GL/gl.h>
(notice the uppercase on GL)

You can check if you have the files if there is a folder:
> ls -l /usr/include/GL

If it isn't,get them with the freeglut3-dev package, and it should install everything. I just installed this and I can include glut.h and gl.h on C
> sudo apt-get install freeglut3-dev

*Yeah, I was right, I uninstalled the freeglut3-dev and glut.h disappeared. So that's the correct package.

---

