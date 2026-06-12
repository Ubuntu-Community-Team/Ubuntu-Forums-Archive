---
title: "Help compiling Pygame for Python3"
date: 2011-07-02
forum: Programming Talk
---

### Post by skytreader on 2011-07-02
Hi all. I'm trying to compile Pygame 1.9.1 for Python3 in my system. However, I run into errors from gcc.

GCC errors (from running `python setup.py`):

```

gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -D_REENTRANT -I/usr/X11R6/include -I/usr/include/SDL -I/usr/include/python2.6 -c src/_numericsurfarray.c -o build/temp.linux-i686-2.6/src/_numericsurfarray.o
In file included from src/_numericsurfarray.c:23:
src/pygame.h:75:20: error: Python.h: No such file or directory
In file included from src/_numericsurfarray.c:23:
src/pygame.h:122: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘lenfunc’
src/pygame.h:123: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ssizeargfunc’
src/pygame.h:124: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ssizeobjargproc’
src/pygame.h:125: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ssizessizeargfunc’
src/pygame.h:126: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ssizessizeobjargproc’
src/pygame.h:127: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘readbufferproc’
src/pygame.h:128: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘writebufferproc’
src/pygame.h:129: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘segcountproc’
src/pygame.h:130: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘charbufferproc’
src/pygame.h:234: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/pygame.h:275: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/pygame.h:310: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/pygame.h:349: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/pygame.h:387: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/pygame.h:450: error: expected specifier-qualifier-list before ‘PyObject’
src/pygame.h:457: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/pygame.h:499: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/pygame.h:567: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
In file included from src/_numericsurfarray.c:25:
src/numeric_arrayobject.h:66: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/numeric_arrayobject.h:67: error: expected ‘)’ before ‘*’ token
src/numeric_arrayobject.h:72: error: expected specifier-qualifier-list before ‘PyArray_GetItemFunc’
src/numeric_arrayobject.h:92: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/numeric_arrayobject.h:114: error: expected specifier-qualifier-list before ‘Py_intptr_t’
src/_numericsurfarray.c:28: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/_numericsurfarray.c:100: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/_numericsurfarray.c:140: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/_numericsurfarray.c:189: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/_numericsurfarray.c:290: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/_numericsurfarray.c:431: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/_numericsurfarray.c:536: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/_numericsurfarray.c:651: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/_numericsurfarray.c:835: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/_numericsurfarray.c:1058: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/_numericsurfarray.c:1121: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘surfarray_builtins’
src/_numericsurfarray.c: In function ‘init_numericsurfarray’:
src/_numericsurfarray.c:1148: error: ‘PyObject’ undeclared (first use in this function)
src/_numericsurfarray.c:1148: error: (Each undeclared identifier is reported only once
src/_numericsurfarray.c:1148: error: for each function it appears in.)
src/_numericsurfarray.c:1148: error: ‘_module’ undeclared (first use in this function)
src/_numericsurfarray.c:1148: warning: implicit declaration of function ‘PyImport_ImportModule’
src/_numericsurfarray.c:1148: error: ‘_dict’ undeclared (first use in this function)
src/_numericsurfarray.c:1148: warning: implicit declaration of function ‘PyModule_GetDict’
src/_numericsurfarray.c:1148: error: ‘_c_api’ undeclared (first use in this function)
src/_numericsurfarray.c:1148: warning: implicit declaration of function ‘PyDict_GetItemString’
src/_numericsurfarray.c:1148: warning: implicit declaration of function ‘PyCObject_Check’
src/_numericsurfarray.c:1148: warning: implicit declaration of function ‘PyCObject_AsVoidPtr’
src/_numericsurfarray.c:1148: warning: implicit declaration of function ‘Py_DECREF’
src/_numericsurfarray.c:1149: warning: implicit declaration of function ‘PyErr_Occurred’
src/_numericsurfarray.c:1156: error: ‘numpy’ undeclared (first use in this function)
src/_numericsurfarray.c:1156: error: ‘module_dict’ undeclared (first use in this function)
src/_numericsurfarray.c:1156: error: ‘c_api_object’ undeclared (first use in this function)
src/_numericsurfarray.c:1162: warning: implicit declaration of function ‘Py_InitModule3’
src/_numericsurfarray.c:1162: error: ‘surfarray_builtins’ undeclared (first use in this function)
error: command 'gcc' failed with exit status 1

```

The Setup file generated by config.py:

```

#This Setup file is used by the setup.py script to configure the
#python extensions. You will likely use the "config.py" which will
#build a correct Setup file for you based on your system settings.
#If not, the format is simple enough to edit by hand. First change
#the needed commandline flags for each dependency, then comment out
#any unavailable optional modules in the first optional section.


SDL = -I/usr/X11R6/include -I/usr/include/SDL -D_REENTRANT -L/usr/lib -lSDL 
FONT = -lSDL_ttf
IMAGE = -lSDL_image
MIXER = -lSDL_mixer
SMPEG = -I/usr/include/smpeg -I/usr/include/SDL -D_REENTRANT -L/usr/lib -lsmpeg -L/usr/lib -lSDL 
PNG = -I/usr/include -L/usr/lib  -lpng
JPEG = -I/usr/include -L/usr/lib  -ljpeg
SCRAP = -L/usr/lib  -lX11
PORTMIDI = -lportmidi
PORTTIME = -lporttime

#DEBUG = -C-W -C-Wall
DEBUG = 

#the following modules are optional. you will want to compile
#everything you can, but you can ignore ones you don't have
#dependencies for, just comment them out

#imageext src/imageext.c $(SDL) $(IMAGE) $(PNG) $(JPEG) $(DEBUG)
#font src/font.c $(SDL) $(FONT) $(DEBUG)
#mixer src/mixer.c $(SDL) $(MIXER) $(DEBUG)
#mixer_music src/music.c $(SDL) $(MIXER) $(DEBUG)
_numericsurfarray src/_numericsurfarray.c $(SDL) $(DEBUG)
#_numericsndarray src/_numericsndarray.c $(SDL) $(MIXER) $(DEBUG)
movie src/movie.c $(SDL) $(SMPEG) $(DEBUG)
scrap src/scrap.c $(SDL) $(SCRAP) $(DEBUG)
_camera src/_camera.c src/camera_v4l2.c src/camera_v4l.c $(SDL) $(DEBUG)
#pypm src/pypm.c $(SDL) $(PORTMIDI) $(PORTTIME) $(DEBUG)

GFX = src/SDL_gfx/SDL_gfxPrimitives.c 
#GFX = src/SDL_gfx/SDL_gfxBlitFunc.c src/SDL_gfx/SDL_gfxPrimitives.c 
gfxdraw src/gfxdraw.c $(SDL) $(GFX) $(DEBUG)



#these modules are required for pygame to run. they only require
#SDL as a dependency. these should not be altered

base src/base.c $(SDL) $(DEBUG)
cdrom src/cdrom.c $(SDL) $(DEBUG)
color src/color.c $(SDL) $(DEBUG)
constants src/constants.c $(SDL) $(DEBUG)
display src/display.c $(SDL) $(DEBUG)
event src/event.c $(SDL) $(DEBUG)
fastevent src/fastevent.c src/fastevents.c $(SDL) $(DEBUG)
key src/key.c $(SDL) $(DEBUG)
mouse src/mouse.c $(SDL) $(DEBUG)
rect src/rect.c $(SDL) $(DEBUG)
rwobject src/rwobject.c $(SDL) $(DEBUG)
surface src/surface.c src/alphablit.c src/surface_fill.c $(SDL) $(DEBUG)
surflock src/surflock.c $(SDL) $(DEBUG)
time src/time.c $(SDL) $(DEBUG)
joystick src/joystick.c $(SDL) $(DEBUG)
draw src/draw.c $(SDL) $(DEBUG)
image src/image.c $(SDL) $(DEBUG)
overlay src/overlay.c $(SDL) $(DEBUG)
transform src/transform.c src/rotozoom.c src/scale2x.c src/scale_mmx.c $(SDL) $(DEBUG) -D_NO_MMX_FOR_X86_64
mask src/mask.c src/bitmask.c $(SDL) $(DEBUG)
bufferproxy src/bufferproxy.c $(SDL) $(DEBUG)
pixelarray src/pixelarray.c $(SDL) $(DEBUG)
_arraysurfarray src/_arraysurfarray.c $(SDL) $(DEBUG)

```

Can anyone help me make sense of this? Also, will I really be able to install it for Python 3 if I am invoking `python` in the command line and not `python3` (invoking `python3 setup.py` returns with an error due to a call to raw_input(). I'm adamant in converting it using 2to3 as I might break some dependencies.)?

---

### Post by skytreader on 2011-07-03
*bump*

I followed the instructions at [http://ubuntuforums.org/showpost.php?p=10306768&postcount=2](http://ubuntuforums.org/showpost.php?p=10306768&postcount=2) so that I could install Pygame in Python 3 but the error I described above persists.

---

### Post by Upp3r on 2011-08-16
Pygame does not currently support Python 3. You may be able to get a hack job working but I would advise using Python 2.7 until the pygame team updates.

---

