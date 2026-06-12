---
title: "Kdeveloper semi-automake yes/no?"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by Clive McCarthy on 2008-06-14
I have an OpenGL C application that is running on XP which I developed using and old Borland 6 compiler. I want to port the application to Ubuntu. I've installed build-essential, kdeveloper, automake etc. but things seem somewhat messy. There always seems to be just-one-more-package to add. I keep on installing things, without really understanding what I'm buying into, which makes me queasy. The Kdeveloper documentation frequently ends in: "(to be written)"

Whenever I ask Kdeveloper to build the project I get a dialog box that asks me if I want to run automake which seems redundant. Clearly I haven't got my set-up configured properly. I also get a warning that AM_PROG_LIBTOOL is not found in the library -- I'll admit I'm thrashing and I don't have a clue.

I'd like to move ahead quickly, there is obviously a lot of _actual_ porting work to be done. I haven't even figured out how to explicitly add C files to the IDE's (make system's ?) list of files in the project. Will the Automake thing ALWAYS redundantly ask me if I want to make the project? Should I hand-edit a template makefile and skip the automake thing entirely? Where do I set the warning/error flags for GCC within Kdevelop?

:confused:](*,)

---

### Post by the_doc on 2008-06-14
A little background first!  The programmer will write something called a **makefile.am** file, by running the automake program these are then converted to **makefile.in**.  These **makefile.in** files contain place holders that will be replaced by actual values when the user runs the configure program, generating the **makefiles** that make then runs.

Most open source packages use the libtool/autoconf/automake combo to generate the makefiles, but this just makes the process of constructing the makefile easier.  You could, as you say write you own makefile directly, but for a sizeable project this can take some effort.

Edit:

If it's not a mammoth task then you could create your own makefile (I'll help), which would also contain the required gcc compiler flags, and run it directly from the command line.

---

### Post by Clive McCarthy on 2008-06-14
My application uses the following libraries:

**libtiff**    Tiff image I/O
**libjpeg**    Jpeg image I/O
**opengl**     Graphics Language (via X-windows I guess for Ubuntu)
**glu**        Library functions for OpenGL (as above)
**glut**       An application framework for OpenGL (freeGlut for Ubuntu)

Then there is my own code, which is in a small number of files. Nothing too hard. As you can imagine, it's frustrating to get messages that report "Can't find file STDIO.H" I'm not sure where I will find the pre-compiled tiff & jpeg libs for Ubuntu.

So far my experience of Ubuntu has been a surprise, a really good surprise. It isn't as crude as I imagined it would be.

I can guess that the auto-tools can figure out some (many) dependencies but surely I have to declare certain things and I don't see where? Do I hand edit the makefile, as in days gone by? Is the query about automake merely a veiled threat that is about to trash a hand-edited makefile?

So far this hasn't proved to be as miserable as VC++ and all of it's nonsense.

:confused:

I've just found libjpeg-dev; libtiff-dev & libglut3-dev so these look like the libraries (I hope?) I did a web search for the "lib names" along with "Ubuntu" and found my way to these...

---

### Post by the_doc on 2008-06-15
I decided to install the kdevelop package to see if I could help you a little better, and ended up with the same errors you did.

However, kdevelop handles all the autmake/autoconf/makefile madness for you, so you don't need to worry about it too much.  I also got the whole **AM_PROG_LIBTOOL** error.  Here's what I did.

Installed autoconf and automake via synaptic (as you did), I made sure I had **build-essential** installed which I think takes care of the **AM_PROG_LIBTOOL** error, but even if it doesn't selecting build project again should take care of it (worked for me!).  After that the project built without further error and generated all of the makefile and configure scripts automagically.

After I tried to execute I received a **/bin/sh: konsole: not found ** error, which I resolved by installing **konsole** via synaptic.  After that the test program executed as expected.

With regards to including all of your header files I think there is an option to include them when you create the project, or just **#include** them if necessary.

Also if you click on Project -> Project Options then select Configure Options (on the lefthand side), then select the C tab (in the middle), you can set your GCC compiler flags/options from there.

Hope this helps.

---

### Post by Clive McCarthy on 2008-06-15
I've obviously set some thing wrong. GCC can't find any of the library headers!

I get:
/home/clive/helloworld/src/helloworld.c:18:37: error: ASSERT.H: No such file or directory
/home/clive/helloworld/src/helloworld.c:19:19: error: CTYPE.H: No such file or directory
/home/clive/helloworld/src/helloworld.c:20:19: error: ERRNO.H: No such file or directory
/home/clive/helloworld/src/helloworld.c:21:19: error: FLOAT.H: No such file or directory
/home/clive/helloworld/src/helloworld.c:22:20: error: LIMITS.H: No such file or directory
/home/clive/helloworld/src/helloworld.c:23:18: error: MATH.H: No such file or directory
/home/clive/helloworld/src/helloworld.c:24:20: error: SETJMP.H: No such file or directory
/home/clive/helloworld/src/helloworld.c:25:20: error: SIGNAL.H: No such file or directory
/home/clive/helloworld/src/helloworld.c:26:20: error: STDARG.H: No such file or directory
/home/clive/helloworld/src/helloworld.c:27:20: error: STDDEF.H: No such file or directory
/home/clive/helloworld/src/helloworld.c:28:19: error: STDIO.H: No such file or directory
/home/clive/helloworld/src/helloworld.c:29:20: error: STDLIB.H: No such file or directory
/home/clive/helloworld/src/helloworld.c:30:20: error: STRING.H: No such file or directory
/home/clive/helloworld/src/helloworld.c:31:18: error: TIME.H: No such file or directory

---

### Post by the_doc on 2008-06-15
I take it you're trying to build the sample Hello World program?  I've just inlcuded all of the files you listed in my test file and it compiles fine.

Can you paste the source file if it isn't too big?

---

### Post by Clive McCarthy on 2008-06-15
Sure:

/*-----------------------------------------------------------------------------


-------------------------------------------------------------------------------
	program name:	Art_Show.exe				module name: main
-------------------------------------------------------------------------------
copyright (c) 2008					author: Clive McCarthy

description:

revision history:

$Log:	$
-----------------------------------------------------------------------------*/
#define FALSE 0
#define TRUE  (!FALSE)

#include <ASSERT.H>		// ANSI X3J11 C
#include <CTYPE.H>
#include <ERRNO.H>
#include <FLOAT.H>
#include <LIMITS.H>
#include <MATH.H>
#include <SETJMP.H>
#include <SIGNAL.H>
#include <STDARG.H>
#include <STDDEF.H>
#include <STDIO.H>
#include <STDLIB.H>
#include <STRING.H>
#include <TIME.H>

//#include <WINDOWS.H>    // must include this before GL/gl.h or GL/glut.h
#include "glee.h"       // must include this before GL/gl.h or GL/glut.h
#include <GL/glut.h>

/*------------------------------------------------------------------------------

------------------------------------------------------------------------------*/
#include "art_show.h"

/*------------------------------------------------------------------------------

------------------------------------------------------------------------------*/
void glut_OpenGL_display(void)
{
    OpenGL_error_check(__FILE__, __LINE__);
    glutSwapBuffers();
}
/*------------------------------------------------------------------------------

------------------------------------------------------------------------------*/
void glut_OpenGL_reshape(int width, int height)
{
    double aspect_ratio;

    height = max(height, 1);
    width  = max(width, 1);
    aspect_ratio = width/(double)height;
    glMatrixMode(GL_PROJECTION);
    glLoadIdentity();
    glViewport(0, 0, width, height);
    glOrtho(0.0, ORTHO_WIDTH, 0.0, ORTHO_WIDTH / aspect_ratio, -10, 10);
    glMatrixMode(GL_MODELVIEW);
    glLoadIdentity();
    glTranslated(0.375, 0.375, 0.0);
    glutPostRedisplay();
}
/*------------------------------------------------------------------------------
    run full screen if exactly three command line parameters: -f -s100 (and name)

------------------------------------------------------------------------------*/
void main(int argc, char **argv)
{
    char *images;

    if(argc == 3) full_screen = TRUE;
    glutInit(&argc, argv);
    glutInitDisplayMode(GLUT_RGBA | GLUT_DOUBLE | GLUT_DEPTH);
    glutCreateWindow("The Art of Kinetic Photography");
    if(full_screen)
    {
        glutFullScreen();
        frame_delay = 100; // slow down to run
    }
    else
    {
        display_sign_on_message();
        set_debug_window_size();
        frame_delay = 1; // speed up
    }
    glutKeyboardFunc(glut_OpenGL_ascii_keys);
	glutSpecialFunc(glut_OpenGL_function_keys);
	glutDisplayFunc(glut_OpenGL_display);
    glutReshapeFunc(glut_OpenGL_reshape);
    glutIdleFunc(glut_OpenGL_idle);
    // timer callback for repeated calling set to 30fps
    glutTimerFunc(frame_delay, glut_OpenGL_timer, 1);
    //display_OpenGL_version();
    use_default_image_directory();
    OpenGL_error_check(__FILE__, __LINE__);
    glutMainLoop();
}
/*------------------------------------------------------------------------------

------------------------------------------------------------------------------*/

---

### Post by Clive McCarthy on 2008-06-15
It's clearly something silly, but what ?:confused:

---

### Post by the_doc on 2008-06-15
Put all of the header file names in lower case.

---

### Post by Clive McCarthy on 2008-06-15
Oh yes! I forgot that Unix/Linux file names are case sensitive, whereas DOS & Windows are not... aha!

---

### Post by the_doc on 2008-06-15
So you all sorted now?!

---

### Post by Clive McCarthy on 2008-06-16
Next: the current problem I'm having is figuring _where_ Ubuntu has put the libtiff, libjpeg, and libglut stuff, and what the files are _actually_ called! For all the electro-magic of Kdevelop and the library retrieval process, specifying the libraries is clunky with Kdevelop/GCC.

Some help with this would be good. :popcorn:

:-({|=Of course I have to whine a bit too:

I was also bemused that GCC needed a -lm flag to use the math library. This is clearly an anachronism. I was at first very perplexed by errors from ceil(), floor(), sqrt() calls despite including math.h -- At first I thought it was a C99 issue. The payload of the math library can't be that heavy so I wonder why Kdevelop doesn't have the flag on by default?

---

