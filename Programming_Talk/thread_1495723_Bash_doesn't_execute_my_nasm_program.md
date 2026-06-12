---
title: "Bash doesn't execute my nasm program"
date: 2010-05-28
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2010-05-28
I want to learn assembler. I'm converting a GLUT template to assembler.

Here's my progress so far (main.asm):
```

%include "opengl.defs"

section .text
	global _start
	global render
	global resize
	global init_gl

_start:
	call glutInit
	push 0x1A ; GLUT_RGBA|GLUT_DOUBLE|GLUT_ALPHA|GLUT_DEPTH
	call glutInitDisplayMode
	push 640
	push 480
	call glutCreateWindow
	pop eax ; window ID
	call glutMainLoop

```

The code compiles without errors nor warnings, but it's not possible to run it:
```

arho@akvaario:~/Source/glut_template_nasm$ tree
.
|-- compile.sh
`-- src
    |-- main.asm
    `-- opengl.defs

1 directory, 3 files
arho@akvaario:~/Source/glut_template_nasm$ ./compile.sh 
Source files: ./src/main.asm
Compiling ./src/main.asm...
Object files: ./src/main.o
Linking...
arho@akvaario:~/Source/glut_template_nasm$ tree
.
|-- compile.sh
|-- glut_template_nasm
`-- src
    |-- main.asm
    |-- main.o
    `-- opengl.defs

1 directory, 5 files
[B]arho@akvaario:~/Source/glut_template_nasm$ ./glut_template_nasm 
bash: ./glut_template_nasm: Tiedostoa tai hakemistoa ei ole[/B]
arho@akvaario:~/Source/glut_template_nasm$ ls -l
yhteensä 12
-rwxr-xr-x 1 arho arho  328 2010-05-28 17:15 compile.sh
-rwxr-xr-x 1 arho arho 2910 2010-05-28 18:29 glut_template_nasm
drwxr-xr-x 2 arho arho 4096 2010-05-28 18:29 src
arho@akvaario:~/Source/glut_template_nasm$ 

```
The bolded error message in english:
> bash: ./glut_template_nasm: No such file or directory
How is this possible? Why won't bash run the file?

Here's compile.sh:
```

#!/bin/bash

src=`ls ./src/*.asm`
echo "Source files: $src"

for file in $src; do
	echo "Compiling $file..."
	nasm -f elf $file
	if [[ $? != 0 ]]; then
		exit $?
	fi
done

obj=`ls ./src/*.o`
echo "Object files: $obj"

echo "Linking..."
ld $obj -o glut_template_nasm -lglut -lGLU -lGL

if [[ $? != 0 ]]; then
	echo "Success."
fi

```
And opengl.defs:
```

%ifndef OPENGL_FUNCTION_DEFS
%define OPENGL_FUNCTION_DEFS

; OpenGL
extern glClear
extern glLoadIdentity
extern glViewport
extern glMatrixMode
extern glOrtho
extern glClearColor
extern glDepthFunc
extern glEnable

; GLUT
extern glutSwapBuffers
extern glutInit
extern glutInitDisplayMode
extern glutInitWindowSize
extern glutCreateWindow
extern glutReshapeFunc
extern glutDisplayFunc
extern glutIdleFunc
extern glutMainLoop

%endif

```

---

### Post by geirha on 2010-05-28
You probably need to pass some more options to ld, though I've never messed about with that command myself. Try linking with gcc; same options
```
gcc -o glut_template_nasm -lglut -lGLU -lGL ./src/*.o
```

Oh, and don't use ls in scripts, it's pointless. With src=`ls ./src/*.asm`, the shell interprets the glob ./src/*.asm and replaces it with the matching files, then executes ls with the filenames as arguments. ls in turn outputs the filenames it was given, which is then caught by the command substitution ``. So ls just acts as a middle man that mangles the filenames into a single string.

Instead, just do 
```

for file in ./src/*.asm; do
  echo "Compiling $file..."
  nasm -f elf "$file" || exit
done

```

---

### Post by crazyfuturamanoob on 2010-05-28
New build script:
```

#!/bin/bash

for file in ./src/*.asm; do
	echo "Compiling $file..."
	nasm -f elf $file
	if [[ $? != 0 ]]; then
		exit $?
	fi
done

echo "Linking..."

gcc -o glut_template_nasm -lglut -lGLU -lGL ./src/*.o

```
Now the program runs: Segmentation Fault! Debugging is going to be lots of fun... :guitar: Thanks.

Edit: It fails at line 10, which calls glutInit. I'm not pushing any arguments to stack because they're already there: argc and argv. What's wrong?

> void glutInit(int *argcp, char **argv);

Edit2: Even this fails:
```

	push 0 ; 0 arguments
	push 0 ; NULL argv
	call glutInit

```

---

