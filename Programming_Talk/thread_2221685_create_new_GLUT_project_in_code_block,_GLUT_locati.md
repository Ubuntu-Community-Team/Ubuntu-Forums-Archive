---
title: "create new GLUT project in code block, GLUT location?"
date: 2014-05-03
forum: Programming Talk
---

### Post by stormy2 on 2014-05-03
Hello everyone :3

i just started useing Linux Ubuntu 14.04 and want's to learn OpenGL programming.

i have some experiencew with C programming in windows with Code::Blocks IDE. so i use Code::Blocks here in Linux.

the question is:
then i create a new GLUT project in Code::Blocks i it asks: "Please Select GLUT's Location" where is that location.
i try'd to select "usr" folder because it has the subfolders: "include" and "lib" but it did't work.

Please help me out. this is my first post on this forum. i am very new in this linux OS and want's to create software for Linux users (well, that's my dream ;3)

---

### Post by steeldriver on 2014-05-03
Hello and welcome to the forums

If you are referring to the freeglut3-dev headers, they usually go in /usr/include/GL

See [http://packages.ubuntu.com/trusty/amd64/freeglut3-dev/filelist](http://packages.ubuntu.com/trusty/amd64/freeglut3-dev/filelist)

You will need to install that package if you haven't already done so

---

### Post by stormy2 on 2014-05-03
Thank you very much for a quick reply :3


i have installed freeglut3-dev headers and i have all the files display'd in the link.
when i select "/usr/include/GL" it comes with this error:
{
Script error

the path you enterned seems valid, but the wizard can't locate the include directory.
This wizard cannot continue.
}

Related image:
[http://gyazo.com/03687f26494927e752698dad48d6a481](http://gyazo.com/03687f26494927e752698dad48d6a481)

---

### Post by steeldriver on 2014-05-03
Hmm... I've looked into this a bit more, and it seems like the codeblocks glut project wizard is designed to work with glut not freeglut, and just doesn't like the way that freeglut organizes its files - I don't know where to go from there

I suspect it should be possible to create a regular project (ignore the glut wizard) and just set the include and lib paths appropriately - but let's wait and see if someone more knowledgeable chimes in - sorry

---

### Post by stormy2 on 2014-05-03
Oke, Thank you very much for your time :3

---

### Post by steeldriver on 2014-05-03
Actually fwiw I was just able to build and run the demo 'GLUT Shapes Demo' from Code:Blocks 10.05 after simply symlinking the glut libs up to the parent /usr/lib directory and then selecting '/usr' as the GLUT location (like you originally tried)

```

sudo ln -s /usr/lib/i386-linux-gnu/libglut.a /usr/lib/libglut.a

sudo ln -s /usr/lib/i386-linux-gnu/libglut.so.3 /usr/lib/libglut.so.3

```

(that's on a32-bit system obviously - the locations will be something like /usr/x86_64-linux-gnu/ on 64 bit). Ugly solution though - I'd still like to hear from someone more knowledgeable.

---

### Post by stormy2 on 2014-05-03
sorry that i'am not pro in english, i did't quite understand how you did get the 'GLUT Shapes Demo to work', but i try'd the commands you posted in terminal but nothing happen.
and after i try'd that i try'd to create a GLUT Project with selecting this "/usr/x86_64-linux-gnu/" into teh GLUT location (sins i run 64bit). i got the same error massage like i did last time.

i think i found an somewhat solution to this: Create a standard OpenGL project, and then link the GLUT lib filers

this is how i linked the lib files:

- Choose "Properties..." from the "Project" dropdown-menu

- Choose  "Build targets" and click on "Build options..."

- Choose Linker settings

- Click "Add" and then navigate to "x68_64-linux-gnu" folder (usr/lib/x68_64-linux-gnu) then select These files:
"libGL.so", "libglapi.so", "libGLU.a", "libGLU.so", "libglut.a", "libglut.so"

- Click on "Yes" on the messageBox, Then "OK"

after this is done and go back to the main.c file, and start to code in:
#include <GL/glut.h>

it displays GL/glut.h as an alternative.
is GLUT added correctly now??

---

