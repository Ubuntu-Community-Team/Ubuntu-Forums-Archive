---
title: "glut and freeglut"
date: 2010-11-08
forum: Programming Talk
---

### Post by EarthVsMe on 2010-11-08
Hey guys, I'm brand new to linux, I just downloaded the Ubuntu 10.10 netbook remix edition. I've already set up the opengl and sdl libraries. 

My question: Is there a big difference between the glut for windows and freeglut? I have programmed in opengl / glut on windows prior. I get them to compile on command line but when I execute them to run it gives me an error.

here's the source code for one of my files. just should draw a sphere


#include <GL/glut.h>
#include <stdio.h>


/// Simple prototypes for the callbacks
void RenderScene(void);
void HandleTimer(int ID);
void FunctionKeys(int key, int x, int y);
void Keyboard(unsigned char key, int x, int y);
void ChangeSize(GLsizei w, GLsizei h);


void main(int argc, char **argv){
    
       glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB );
    glutInitWindowSize(500, 500);
    glutCreateWindow("This is the window title");

    /// Java does the same sort of thing here, 
    /// simply pass the name of a function that should
    /// be called whenever an event occurs. 
    glutReshapeFunc(ChangeSize);
    glutDisplayFunc(RenderScene);
    glutKeyboardFunc(Keyboard);
    glutSpecialFunc(FunctionKeys);
    glutTimerFunc(1000,HandleTimer,1);/// See HandleTimer(...)

    

    glutMainLoop(); /// This starts the main loop which will 
                    /// call the appropreate subroutine 
                    /// given the event
}



/// If the window changes size this subroutine will be called 
/// note: This subroutine will be called upon the creation of the window since, logically,
/// the window has changed from nothing to something        
void ChangeSize(GLsizei w, GLsizei h){
    glViewport(0,0,w,h);
    glMatrixMode(GL_PROJECTION);
    glLoadIdentity();
    GLfloat aspectRatio = (GLfloat)w /(GLfloat)h;
    if(w < h){
        glOrtho(-10.0,10.0,-10.0 / aspectRatio, 10.0 / aspectRatio,10.0,-10.0);
    }else{
        glOrtho(-10.0* aspectRatio,10.0 * aspectRatio,-10.0 , 10.0 ,10.0,-10.0);
    }
}

/// Whenever the scene needs to be redrawn this function is called
void RenderScene(void){
    
    glClear(GL_COLOR_BUFFER_BIT);/// Clears the screen

    /// PLACE DRAWING CODE HERE
    
    //glTranslated(0.0,0.1,0.0);
    //glRotated(0.4,0.0,1.0,0.0);
    glutWireSphere(2.0,20,20);
    //glutWireTeapot(2.0);
    glFlush(); ///Shove everything through the "pipeline" 
}

void HandleTimer(int ID){


    /// This function send a message to the main loop that it's time to call
    /// the DisplayFunc which I called "RenderScene"
    glutPostRedisplay();
    /// The first value is the number of millseconds before the next event
    /// The second arg is a pointer to the callback function
    /// The third is the ID number of this timer     
    glutTimerFunc(16,HandleTimer,1);
}



void FunctionKeys(int key, int x, int y){
    /// this function is called whenever a button off the standard keybord is pressed
    /// for example the function keys or the arrow keys - hint
    /// Look for the following
        if(key == GLUT_KEY_UP) printf("UP arrow\n");
        /// GLUT_KEY_DOWN
        /// GLUT_KEY_RIGHT
        /// GLUT_KEY_LEFT
}



void Keyboard(unsigned char key, int x, int y){
    printf("%c<%d> %d %d\n",key,key,x,y);
    if(key=='q' || key=='Q' || key == 27) exit(0);
    
}



It compiles just fine when I use gcc openGL.cpp -o openGL -lglut -lGL
but when I run the file ./main.cpp  it gives me this error

freeglut  ERROR:  Function <glutCreateWindow> called without first calling 'glutInit'.

---

### Post by abhilashm86 on 2010-11-08
hi!! 
In OpenGL programming on linux, in the main() function, you need to initialize passing parameters first, mainly command line arguements, to do that 

```

void main(int argc, char **argv){

//this is init function
glutInit(&argc, argv);

//then your rest of code follows 

glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB );
glutInitWindowSize(500, 500);
glutCreateWindow("This is the window title");

/// Java does the same sort of thing here,
/// simply pass the name of a function that should
/// be called whenever an event occurs.
glutReshapeFunc(ChangeSize);
glutDisplayFunc(RenderScene);
glutKeyboardFunc(Keyboard);
glutSpecialFunc(FunctionKeys);
glutTimerFunc(1000,HandleTimer,1);/// See HandleTimer(...)



glutMainLoop(); /// This starts the main loop which will
/// call the appropreate subroutine
/// given the event
}
```

---

### Post by EarthVsMe on 2010-11-08
OHhhh Thank you very much :D

---

### Post by $uraj on 2011-05-12
Thanks a lot :) its working like a charm in Linux :) so fast compilation wen compared to Microsoft Visual C++ :)

---

