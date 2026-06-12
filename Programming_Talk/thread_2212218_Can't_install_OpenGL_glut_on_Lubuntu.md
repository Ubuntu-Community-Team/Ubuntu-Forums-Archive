---
title: "Can't install OpenGL glut on Lubuntu?"
date: 2014-03-20
forum: Programming Talk
---

### Post by Akoman on 2014-03-20
Hi,

I did spend quite some time trying to install all the librairies that I need to run OpenGL programs on my laptop but it just doens't seem to work, I am using Lubuntu atm.

I had installed the following:

Freeglut3 Freeglut3-dev
Build-essential
Binutils-gold ( Lubuntu installed Binutils instead)

my make looks something like this : 
```
CXXFLAGS += -I/usr/X11/include -I/opt/local/include -W -Wall -Wno-unused-parameter -Wno-deprecated-declarations
LDFLAGS += -L/usr/X11/lib -L/opt/local/lib

SRC = main.cpp chargertex.cpp fctsUtiles.cpp
all : main.exe
main.exe : $(SRC:.cpp=.o)
	$(CXX) $(LDFLAGS) -lglut -lGLU -lGL -lGLEW -o$@ $(SRC:.cpp=.o)

SOL = main_solution.cpp chargertex.cpp fctsUtiles.cpp
sol : main_solution.exe
main_solution.exe : $(SOL:.cpp=.o)
	$(CXX) $(LDFLAGS) -lglut -lGLU -lGL -lGLEW -o $@ $(SOL:.cpp=.o)

clean:
	-\rm *.o *.exe

chargertex.o: chargertex.cpp chargertex.h bitmap.h
fctsUtiles.o: fctsUtiles.cpp fctsUtiles.h
main.o: main.cpp varglob.h fctsUtiles.h chargertex.h
main_solution.o: main_solution.cpp varglob.h fctsUtiles.h chargertex.h

```

It is a school assignement that I am doing and I just can't seem to be able to run my OpenGl program. It does generate the .o but it is unable to link to the librairies. I get the following error : 

```
main.o: In function `animer(int)':
main.cpp:(.text+0x11): undefined reference to `glutGet'
main.cpp:(.text+0x4d): undefined reference to `glutTimerFunc'
main.cpp:(.text+0x62): undefined reference to `glutPostRedisplay'
main.o: In function `initialisation()':
main.cpp:(.text+0x1c8): undefined reference to `glClearColor'
main.cpp:(.text+0x1d2): undefined reference to `glEnable'
main.cpp:(.text+0x1dc): undefined reference to `glEnable'
main.cpp:(.text+0x1eb): undefined reference to `glLightModeli'
main.cpp:(.text+0x1fa): undefined reference to `glLightModeli'
main.cpp:(.text+0x204): undefined reference to `glEnable'
main.o: In function `definirEclairage()':
main.cpp:(.text+0x228): undefined reference to `glLightfv'
main.cpp:(.text+0x23c): undefined reference to `glLightfv'
main.cpp:(.text+0x250): undefined reference to `glLightfv'
main.cpp:(.text+0x25a): undefined reference to `glEnable'
main.o: In function `afficherModele()':
main.cpp:(.text+0x333): undefined reference to `__glewUseProgram'
main.cpp:(.text+0x344): undefined reference to `__glewUniform1i'
main.cpp:(.text+0x356): undefined reference to `__glewGetUniformLocation'
main.cpp:(.text+0x373): undefined reference to `__glewUniform1i'
main.cpp:(.text+0x385): undefined reference to `__glewGetUniformLocation'
main.cpp:(.text+0x3a2): undefined reference to `__glewUniform1i'
main.cpp:(.text+0x3b4): undefined reference to `__glewGetUniformLocation'
main.cpp:(.text+0x3d3): undefined reference to `__glewUseProgram'
main.cpp:(.text+0x3e4): undefined reference to `glEnable'
main.cpp:(.text+0x4c9): undefined reference to `glMaterialfv'
main.cpp:(.text+0x4e2): undefined reference to `glMaterialfv'
main.cpp:(.text+0x4fb): undefined reference to `glMaterialfv'
main.cpp:(.text+0x514): undefined reference to `glMaterialfv'
main.cpp:(.text+0x52d): undefined reference to `glMaterialfv'
main.cpp:(.text+0x532): undefined reference to `glPushMatrix'
main.cpp:(.text+0x669): undefined reference to `glRotated'
main.cpp:(.text+0x68c): undefined reference to `glRotated'
main.cpp:(.text+0x6af): undefined reference to `glRotated'
main.cpp:(.text+0x6cc): undefined reference to `glScalef'
main.cpp:(.text+0x707): undefined reference to `glEnableClientState'
main.cpp:(.text+0x725): undefined reference to `glVertexPointer'
main.cpp:(.text+0x739): undefined reference to `glDrawArrays'
main.cpp:(.text+0x743): undefined reference to `glDisableClientState'
main.cpp:(.text+0x752): undefined reference to `glPushAttrib'
main.cpp:(.text+0x75c): undefined reference to `glFrontFace'
main.cpp:(.text+0x769): undefined reference to `glutSolidTeapot'
main.cpp:(.text+0x76e): undefined reference to `glPopAttrib'
main.cpp:(.text+0x7b4): undefined reference to `glutSolidTorus'
main.cpp:(.text+0x7e1): undefined reference to `glutSolidSphere'
main.cpp:(.text+0x7e8): undefined reference to `glPushMatrix'
main.cpp:(.text+0x805): undefined reference to `glScalef'
main.cpp:(.text+0x80a): undefined reference to `glutSolidDodecahedron'
main.cpp:(.text+0x80f): undefined reference to `glPopMatrix'
main.cpp:(.text+0x816): undefined reference to `glPushMatrix'
main.cpp:(.text+0x833): undefined reference to `glScalef'
main.cpp:(.text+0x838): undefined reference to `glutSolidIcosahedron'
main.cpp:(.text+0x83d): undefined reference to `glPopMatrix'
main.cpp:(.text+0x843): undefined reference to `glPopMatrix'
main.cpp:(.text+0x84d): undefined reference to `glDisable'
main.cpp:(.text+0x857): undefined reference to `glDisable'
main.cpp:(.text+0x85e): undefined reference to `__glewUseProgram'
main.o: In function `afficherAxes()':
main.cpp:(.text+0x892): undefined reference to `glPushAttrib'
main.cpp:(.text+0x89f): undefined reference to `glLineWidth'
main.cpp:(.text+0xa22): undefined reference to `glEnableClientState'
main.cpp:(.text+0xa2c): undefined reference to `glEnableClientState'
main.cpp:(.text+0xa4a): undefined reference to `glVertexPointer'
main.cpp:(.text+0xa65): undefined reference to `glColorPointer'
main.cpp:(.text+0xa79): undefined reference to `glDrawArrays'
main.cpp:(.text+0xa83): undefined reference to `glDisableClientState'
main.cpp:(.text+0xa8d): undefined reference to `glDisableClientState'
main.cpp:(.text+0xa92): undefined reference to `glPushMatrix'
main.cpp:(.text+0xad3): undefined reference to `glTranslatef'
main.cpp:(.text+0xaf0): undefined reference to `glColor3f'
main.cpp:(.text+0xb18): undefined reference to `glutSolidSphere'
main.cpp:(.text+0xb1d): undefined reference to `glPopMatrix'
main.cpp:(.text+0xb22): undefined reference to `glPopAttrib'
main.o: In function `afficherScene()':
main.cpp:(.text+0xb40): undefined reference to `glClear'
main.cpp:(.text+0xb4a): undefined reference to `glMatrixMode'
main.cpp:(.text+0xb4f): undefined reference to `glLoadIdentity'
main.cpp:(.text+0xbb4): undefined reference to `gluPerspective'
main.cpp:(.text+0xc90): undefined reference to `glOrtho'
main.cpp:(.text+0xd43): undefined reference to `glOrtho'
main.cpp:(.text+0xd4d): undefined reference to `glMatrixMode'
main.cpp:(.text+0xd52): undefined reference to `glLoadIdentity'
main.cpp:(.text+0xdb0): undefined reference to `gluLookAt'
main.cpp:(.text+0xdc4): undefined reference to `glutSwapBuffers'
main.o: In function `redimensionnement(int, int)':
main.cpp:(.text+0xdff): undefined reference to `glViewport'
main.cpp:(.text+0xe04): undefined reference to `glutPostRedisplay'
main.o: In function `clavier(unsigned char, int, int)':
main.cpp:(.text+0xe43): undefined reference to `glutDestroyWindow'
main.cpp:(.text+0xe62): undefined reference to `glutPostRedisplay'
main.cpp:(.text+0xeba): undefined reference to `glutPostRedisplay'
main.cpp:(.text+0xee5): undefined reference to `glutPostRedisplay'
main.cpp:(.text+0xf2f): undefined reference to `glutPostRedisplay'
main.cpp:(.text+0xf79): undefined reference to `glutPostRedisplay'
main.cpp:(.text+0xfd4): undefined reference to `glLightModeli'
main.cpp:(.text+0xfd9): undefined reference to `glutPostRedisplay'
main.cpp:(.text+0x104d): undefined reference to `glutPostRedisplay'
main.cpp:(.text+0x10c2): undefined reference to `glutPostRedisplay'
main.cpp:(.text+0x1144): undefined reference to `glutPostRedisplay'
main.cpp:(.text+0x11c7): undefined reference to `glutPostRedisplay'
main.o:main.cpp:(.text+0x11de): more undefined references to `glutPostRedisplay' follow
main.o: In function `clavier(unsigned char, int, int)':
main.cpp:(.text+0x1385): undefined reference to `glPolygonMode'
main.cpp:(.text+0x1396): undefined reference to `glPolygonMode'
main.cpp:(.text+0x139b): undefined reference to `glutPostRedisplay'
main.cpp:(.text+0x13ed): undefined reference to `glutPostRedisplay'
main.o: In function `sourisMouvement(int, int)':
main.cpp:(.text+0x15cb): undefined reference to `glutPostRedisplay'
main.o: In function `main':
main.cpp:(.text+0x15ef): undefined reference to `glutInit'
main.cpp:(.text+0x15f9): undefined reference to `glutInitDisplayMode'
main.cpp:(.text+0x160e): undefined reference to `glutInitWindowSize'
main.cpp:(.text+0x1618): undefined reference to `glutCreateWindow'
main.cpp:(.text+0x1628): undefined reference to `glutDisplayFunc'
main.cpp:(.text+0x1632): undefined reference to `glutReshapeFunc'
main.cpp:(.text+0x163c): undefined reference to `glutKeyboardFunc'
main.cpp:(.text+0x1646): undefined reference to `glutSpecialFunc'
main.cpp:(.text+0x1650): undefined reference to `glutMotionFunc'
main.cpp:(.text+0x165a): undefined reference to `glutMouseFunc'
main.cpp:(.text+0x165f): undefined reference to `glewInit'
main.cpp:(.text+0x167e): undefined reference to `glutMainLoop'
chargertex.o: In function `ChargerTexture(std::string, unsigned int&)':
chargertex.cpp:(.text+0x142): undefined reference to `glGenTextures'
chargertex.cpp:(.text+0x157): undefined reference to `glBindTexture'
chargertex.cpp:(.text+0x1b1): undefined reference to `glTexImage2D'
chargertex.cpp:(.text+0x1c5): undefined reference to `glTexParameteri'
chargertex.cpp:(.text+0x1d9): undefined reference to `glTexParameteri'
chargertex.cpp:(.text+0x1f0): undefined reference to `glTexParameterf'
chargertex.cpp:(.text+0x207): undefined reference to `glTexParameterf'
fctsUtiles.o: In function `VerifierErreurGL(std::string)':
fctsUtiles.cpp:(.text+0x1b): undefined reference to `gluErrorString'
fctsUtiles.cpp:(.text+0x89): undefined reference to `glGetError'
fctsUtiles.o: In function `afficherShaderInfoLog(unsigned int, std::string)':
fctsUtiles.cpp:(.text+0x1b2): undefined reference to `__glewGetShaderiv'
fctsUtiles.cpp:(.text+0x1ec): undefined reference to `__glewGetShaderInfoLog'
fctsUtiles.o: In function `afficherProgramInfoLog(unsigned int, std::string)':
fctsUtiles.cpp:(.text+0x294): undefined reference to `__glewGetProgramiv'
fctsUtiles.cpp:(.text+0x2ce): undefined reference to `__glewGetProgramInfoLog'
fctsUtiles.o: In function `compilerNuanceurs(char const*, char const*)':
fctsUtiles.cpp:(.text+0x353): undefined reference to `__glewCreateProgram'
fctsUtiles.cpp:(.text+0x35f): undefined reference to `__glewCreateShader'
fctsUtiles.cpp:(.text+0x37d): undefined reference to `__glewShaderSource'
fctsUtiles.cpp:(.text+0x397): undefined reference to `__glewCompileShader'
fctsUtiles.cpp:(.text+0x3a5): undefined reference to `__glewAttachShader'
fctsUtiles.cpp:(.text+0x402): undefined reference to `__glewCreateShader'
fctsUtiles.cpp:(.text+0x420): undefined reference to `__glewShaderSource'
fctsUtiles.cpp:(.text+0x43a): undefined reference to `__glewCompileShader'
fctsUtiles.cpp:(.text+0x448): undefined reference to `__glewAttachShader'
fctsUtiles.cpp:(.text+0x4a5): undefined reference to `__glewLinkProgram'
collect2: error: ld returned 1 exit status
make: *** [main.exe] Error 1

```

This is what I get from glxinfo :

```
main.o: In function `animer(int)':
main.cpp:(.text+0x11): undefined reference to `glutGet'
main.cpp:(.text+0x4d): undefined reference to `glutTimerFunc'
main.cpp:(.text+0x62): undefined reference to `glutPostRedisplay'
main.o: In function `initialisation()':
main.cpp:(.text+0x1c8): undefined reference to `glClearColor'
main.cpp:(.text+0x1d2): undefined reference to `glEnable'
main.cpp:(.text+0x1dc): undefined reference to `glEnable'
main.cpp:(.text+0x1eb): undefined reference to `glLightModeli'
main.cpp:(.text+0x1fa): undefined reference to `glLightModeli'
main.cpp:(.text+0x204): undefined reference to `glEnable'
main.o: In function `definirEclairage()':
main.cpp:(.text+0x228): undefined reference to `glLightfv'
main.cpp:(.text+0x23c): undefined reference to `glLightfv'
main.cpp:(.text+0x250): undefined reference to `glLightfv'
main.cpp:(.text+0x25a): undefined reference to `glEnable'
main.o: In function `afficherModele()':
main.cpp:(.text+0x333): undefined reference to `__glewUseProgram'
main.cpp:(.text+0x344): undefined reference to `__glewUniform1i'
main.cpp:(.text+0x356): undefined reference to `__glewGetUniformLocation'
main.cpp:(.text+0x373): undefined reference to `__glewUniform1i'
main.cpp:(.text+0x385): undefined reference to `__glewGetUniformLocation'
main.cpp:(.text+0x3a2): undefined reference to `__glewUniform1i'
main.cpp:(.text+0x3b4): undefined reference to `__glewGetUniformLocation'
main.cpp:(.text+0x3d3): undefined reference to `__glewUseProgram'
main.cpp:(.text+0x3e4): undefined reference to `glEnable'
main.cpp:(.text+0x4c9): undefined reference to `glMaterialfv'
main.cpp:(.text+0x4e2): undefined reference to `glMaterialfv'
main.cpp:(.text+0x4fb): undefined reference to `glMaterialfv'
main.cpp:(.text+0x514): undefined reference to `glMaterialfv'
main.cpp:(.text+0x52d): undefined reference to `glMaterialfv'
main.cpp:(.text+0x532): undefined reference to `glPushMatrix'
main.cpp:(.text+0x669): undefined reference to `glRotated'
main.cpp:(.text+0x68c): undefined reference to `glRotated'
main.cpp:(.text+0x6af): undefined reference to `glRotated'
main.cpp:(.text+0x6cc): undefined reference to `glScalef'
main.cpp:(.text+0x707): undefined reference to `glEnableClientState'
main.cpp:(.text+0x725): undefined reference to `glVertexPointer'
main.cpp:(.text+0x739): undefined reference to `glDrawArrays'
main.cpp:(.text+0x743): undefined reference to `glDisableClientState'
main.cpp:(.text+0x752): undefined reference to `glPushAttrib'
main.cpp:(.text+0x75c): undefined reference to `glFrontFace'
main.cpp:(.text+0x769): undefined reference to `glutSolidTeapot'
main.cpp:(.text+0x76e): undefined reference to `glPopAttrib'
main.cpp:(.text+0x7b4): undefined reference to `glutSolidTorus'
main.cpp:(.text+0x7e1): undefined reference to `glutSolidSphere'
main.cpp:(.text+0x7e8): undefined reference to `glPushMatrix'
main.cpp:(.text+0x805): undefined reference to `glScalef'
main.cpp:(.text+0x80a): undefined reference to `glutSolidDodecahedron'
main.cpp:(.text+0x80f): undefined reference to `glPopMatrix'
main.cpp:(.text+0x816): undefined reference to `glPushMatrix'
main.cpp:(.text+0x833): undefined reference to `glScalef'
main.cpp:(.text+0x838): undefined reference to `glutSolidIcosahedron'
main.cpp:(.text+0x83d): undefined reference to `glPopMatrix'
main.cpp:(.text+0x843): undefined reference to `glPopMatrix'
main.cpp:(.text+0x84d): undefined reference to `glDisable'
main.cpp:(.text+0x857): undefined reference to `glDisable'
main.cpp:(.text+0x85e): undefined reference to `__glewUseProgram'
main.o: In function `afficherAxes()':
main.cpp:(.text+0x892): undefined reference to `glPushAttrib'
main.cpp:(.text+0x89f): undefined reference to `glLineWidth'
main.cpp:(.text+0xa22): undefined reference to `glEnableClientState'
main.cpp:(.text+0xa2c): undefined reference to `glEnableClientState'
main.cpp:(.text+0xa4a): undefined reference to `glVertexPointer'
main.cpp:(.text+0xa65): undefined reference to `glColorPointer'
main.cpp:(.text+0xa79): undefined reference to `glDrawArrays'
main.cpp:(.text+0xa83): undefined reference to `glDisableClientState'
main.cpp:(.text+0xa8d): undefined reference to `glDisableClientState'
main.cpp:(.text+0xa92): undefined reference to `glPushMatrix'
main.cpp:(.text+0xad3): undefined reference to `glTranslatef'
main.cpp:(.text+0xaf0): undefined reference to `glColor3f'
main.cpp:(.text+0xb18): undefined reference to `glutSolidSphere'
main.cpp:(.text+0xb1d): undefined reference to `glPopMatrix'
main.cpp:(.text+0xb22): undefined reference to `glPopAttrib'
main.o: In function `afficherScene()':
main.cpp:(.text+0xb40): undefined reference to `glClear'
main.cpp:(.text+0xb4a): undefined reference to `glMatrixMode'
main.cpp:(.text+0xb4f): undefined reference to `glLoadIdentity'
main.cpp:(.text+0xbb4): undefined reference to `gluPerspective'
main.cpp:(.text+0xc90): undefined reference to `glOrtho'
main.cpp:(.text+0xd43): undefined reference to `glOrtho'
main.cpp:(.text+0xd4d): undefined reference to `glMatrixMode'
main.cpp:(.text+0xd52): undefined reference to `glLoadIdentity'
main.cpp:(.text+0xdb0): undefined reference to `gluLookAt'
main.cpp:(.text+0xdc4): undefined reference to `glutSwapBuffers'
main.o: In function `redimensionnement(int, int)':
main.cpp:(.text+0xdff): undefined reference to `glViewport'
main.cpp:(.text+0xe04): undefined reference to `glutPostRedisplay'
main.o: In function `clavier(unsigned char, int, int)':
main.cpp:(.text+0xe43): undefined reference to `glutDestroyWindow'
main.cpp:(.text+0xe62): undefined reference to `glutPostRedisplay'
main.cpp:(.text+0xeba): undefined reference to `glutPostRedisplay'
main.cpp:(.text+0xee5): undefined reference to `glutPostRedisplay'
main.cpp:(.text+0xf2f): undefined reference to `glutPostRedisplay'
main.cpp:(.text+0xf79): undefined reference to `glutPostRedisplay'
main.cpp:(.text+0xfd4): undefined reference to `glLightModeli'
main.cpp:(.text+0xfd9): undefined reference to `glutPostRedisplay'
main.cpp:(.text+0x104d): undefined reference to `glutPostRedisplay'
main.cpp:(.text+0x10c2): undefined reference to `glutPostRedisplay'
main.cpp:(.text+0x1144): undefined reference to `glutPostRedisplay'
main.cpp:(.text+0x11c7): undefined reference to `glutPostRedisplay'
main.o:main.cpp:(.text+0x11de): more undefined references to `glutPostRedisplay' follow
main.o: In function `clavier(unsigned char, int, int)':
main.cpp:(.text+0x1385): undefined reference to `glPolygonMode'
main.cpp:(.text+0x1396): undefined reference to `glPolygonMode'
main.cpp:(.text+0x139b): undefined reference to `glutPostRedisplay'
main.cpp:(.text+0x13ed): undefined reference to `glutPostRedisplay'
main.o: In function `sourisMouvement(int, int)':
main.cpp:(.text+0x15cb): undefined reference to `glutPostRedisplay'
main.o: In function `main':
main.cpp:(.text+0x15ef): undefined reference to `glutInit'
main.cpp:(.text+0x15f9): undefined reference to `glutInitDisplayMode'
main.cpp:(.text+0x160e): undefined reference to `glutInitWindowSize'
main.cpp:(.text+0x1618): undefined reference to `glutCreateWindow'
main.cpp:(.text+0x1628): undefined reference to `glutDisplayFunc'
main.cpp:(.text+0x1632): undefined reference to `glutReshapeFunc'
main.cpp:(.text+0x163c): undefined reference to `glutKeyboardFunc'
main.cpp:(.text+0x1646): undefined reference to `glutSpecialFunc'
main.cpp:(.text+0x1650): undefined reference to `glutMotionFunc'
main.cpp:(.text+0x165a): undefined reference to `glutMouseFunc'
main.cpp:(.text+0x165f): undefined reference to `glewInit'
main.cpp:(.text+0x167e): undefined reference to `glutMainLoop'
chargertex.o: In function `ChargerTexture(std::string, unsigned int&)':
chargertex.cpp:(.text+0x142): undefined reference to `glGenTextures'
chargertex.cpp:(.text+0x157): undefined reference to `glBindTexture'
chargertex.cpp:(.text+0x1b1): undefined reference to `glTexImage2D'
chargertex.cpp:(.text+0x1c5): undefined reference to `glTexParameteri'
chargertex.cpp:(.text+0x1d9): undefined reference to `glTexParameteri'
chargertex.cpp:(.text+0x1f0): undefined reference to `glTexParameterf'
chargertex.cpp:(.text+0x207): undefined reference to `glTexParameterf'
fctsUtiles.o: In function `VerifierErreurGL(std::string)':
fctsUtiles.cpp:(.text+0x1b): undefined reference to `gluErrorString'
fctsUtiles.cpp:(.text+0x89): undefined reference to `glGetError'
fctsUtiles.o: In function `afficherShaderInfoLog(unsigned int, std::string)':
fctsUtiles.cpp:(.text+0x1b2): undefined reference to `__glewGetShaderiv'
fctsUtiles.cpp:(.text+0x1ec): undefined reference to `__glewGetShaderInfoLog'
fctsUtiles.o: In function `afficherProgramInfoLog(unsigned int, std::string)':
fctsUtiles.cpp:(.text+0x294): undefined reference to `__glewGetProgramiv'
fctsUtiles.cpp:(.text+0x2ce): undefined reference to `__glewGetProgramInfoLog'
fctsUtiles.o: In function `compilerNuanceurs(char const*, char const*)':
fctsUtiles.cpp:(.text+0x353): undefined reference to `__glewCreateProgram'
fctsUtiles.cpp:(.text+0x35f): undefined reference to `__glewCreateShader'
fctsUtiles.cpp:(.text+0x37d): undefined reference to `__glewShaderSource'
fctsUtiles.cpp:(.text+0x397): undefined reference to `__glewCompileShader'
fctsUtiles.cpp:(.text+0x3a5): undefined reference to `__glewAttachShader'
fctsUtiles.cpp:(.text+0x402): undefined reference to `__glewCreateShader'
fctsUtiles.cpp:(.text+0x420): undefined reference to `__glewShaderSource'
fctsUtiles.cpp:(.text+0x43a): undefined reference to `__glewCompileShader'
fctsUtiles.cpp:(.text+0x448): undefined reference to `__glewAttachShader'
fctsUtiles.cpp:(.text+0x4a5): undefined reference to `__glewLinkProgram'
collect2: error: ld returned 1 exit status
make: *** [main.exe] Error 1

```

In the hope that someone can help!!!!

---

### Post by spjackson on 2014-03-20
You need the libraries after the objects. So
```

    $(CXX) $(LDFLAGS)  -o $@ $(SOL:.cpp=.o) -lglut -lGLU -lGL -lGLEW

```
Well, I don't know whether the libraries are in the right order or whether you need extra ones, but putting them after the objects is a start.

---

### Post by Akoman on 2014-03-20
.....

Thanks Spackson, it actually worked. This is very strange as it was a makefile provided by the professor :S.

Thanks again, it works now.

---

