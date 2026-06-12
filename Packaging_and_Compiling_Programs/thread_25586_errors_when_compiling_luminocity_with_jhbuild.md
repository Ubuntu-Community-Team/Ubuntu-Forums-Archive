---
title: "errors when compiling luminocity with jhbuild"
date: 2005-04-10
forum: Packaging and Compiling Programs
---

### Post by garyniger on 2005-04-10
Whenever I try to build luminocity I get the following errors:

/usr/X11R6/lib/libGL.a(glxcmds.o)(.text+0x2eea): In function `glXGetMscRateOML':: undefined reference to `XF86VidModeQueryVersion'
/usr/X11R6/lib/libGL.a(glxcmds.o)(.text+0x2f1a): In function `glXGetMscRateOML':: undefined reference to `XF86VidModeGetModeLine'

I think something's wrong with my opengl libraries.  Does anyone know what's going on here?

---

### Post by garyniger on 2005-04-10
I fixed it.  I needed to install libxxf86vm-dev and add -lXxf86vm to the linker parameter list in the luminocity makefile.

---

### Post by Promethe on 2005-04-15
But now geting this error:
```
*** Installing luminocity *** [24/24]

make   install
Making install in src
make[1]: Wej&#347;cie do katalogu `/home/promethe/luminocity/src/luminocity/luminocity/src'
make  install-am
make[2]: Wej&#347;cie do katalogu `/home/promethe/luminocity/src/luminocity/luminocity/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -D_XOPEN_SOURCE=500 -pthread -I/home/promethe/luminocity/opt/luminocity/include -I/usr/local/kx/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2   -I /usr/X11R6/include -DPKGDATADIR=\"/home/promethe/luminocity/opt/luminocity/share/luminocity\"    -g -O2 -Wall -MT output.o -MD -MP -MF ".deps/output.Tpo" \
  -c -o output.o `test -f 'output.c' || echo './'`output.c; \
then mv -f ".deps/output.Tpo" ".deps/output.Po"; \
else rm -f ".deps/output.Tpo"; exit 1; \
fi
In file included from output.c:28:
texture.h:8:49: GL/gl.h: Nie ma takiego pliku ani katalogu
In file included from output.c:28:
texture.h:27: error: syntax error before "GLuint"
texture.h:27: warning: no semicolon at end of struct or union
texture.h:33: error: syntax error before '*' token
texture.h:33: warning: type defaults to `int' in declaration of `tiles'
texture.h:33: warning: data definition has no type or storage class
texture.h:41: error: syntax error before "base_texture"
texture.h:41: warning: type defaults to `int' in declaration of `base_texture'
texture.h:41: warning: data definition has no type or storage class
output.c:30:19: GL/gl.h: Nie ma takiego pliku ani katalogu
output.c:31:20: GL/glu.h: Nie ma takiego pliku ani katalogu
output.c:32:20: GL/glx.h: Nie ma takiego pliku ani katalogu
output.c:44: error: syntax error before "GLXContext"
output.c:44: warning: no semicolon at end of struct or union
output.c:54: error: syntax error before ':' token
output.c:80: error: syntax error before '}' token
output.c: In function `lmc_output_get_type':
output.c:123: error: invalid application of `sizeof' to an incomplete type
output.c: In function `lmc_output_finalize':
output.c:135: error: dereferencing pointer to incomplete type
output.c: In function `lmc_output_init':
output.c:158: error: dereferencing pointer to incomplete type
output.c: At top level:
output.c:169: error: syntax error before "GLXContext"
output.c: In function `make_window':
output.c:171: error: `GLX_RGBA' undeclared (first use in this function)
output.c:171: error: (Each undeclared identifier is reported only once
output.c:171: error: for each function it appears in.)
output.c:172: error: `GLX_RED_SIZE' undeclared (first use in this function)
output.c:173: error: `GLX_GREEN_SIZE' undeclared (first use in this function)
output.c:174: error: `GLX_BLUE_SIZE' undeclared (first use in this function)
output.c:175: error: `GLX_DOUBLEBUFFER' undeclared (first use in this function)
output.c:176: error: `GLX_DEPTH_SIZE' undeclared (first use in this function)
output.c:183: error: `xdisplay' undeclared (first use in this function)
output.c:183: error: `screen' undeclared (first use in this function)
output.c:185: warning: implicit declaration of function `glXChooseVisual'
output.c:185: warning: assignment makes pointer from integer without a cast
output.c:195: error: `colormap' undeclared (first use in this function)
output.c:199: error: `window' undeclared (first use in this function)
output.c:230: error: `name' undeclared (first use in this function)
output.c:237: error: `context' undeclared (first use in this function)
output.c:237: warning: implicit declaration of function `glXCreateContext'
output.c: In function `free_action':
output.c:373: error: dereferencing pointer to incomplete type
output.c: In function `output_thread_func':
output.c:449: error: dereferencing pointer to incomplete type
output.c:453: warning: implicit declaration of function `glXMakeCurrent'
output.c:453: error: dereferencing pointer to incomplete type
output.c:455: warning: implicit declaration of function `glShadeModel'
output.c:455: error: `GL_FLAT' undeclared (first use in this function)
output.c:456: warning: implicit declaration of function `glViewport'
output.c:456: error: dereferencing pointer to incomplete type
output.c:456: error: dereferencing pointer to incomplete type
output.c:458: error: dereferencing pointer to incomplete type
output.c:472: error: dereferencing pointer to incomplete type
output.c:472: error: dereferencing pointer to incomplete type
output.c:472: error: dereferencing pointer to incomplete type
output.c:473: error: dereferencing pointer to incomplete type
output.c:474: error: dereferencing pointer to incomplete type
output.c:476: error: dereferencing pointer to incomplete type
output.c:476: error: dereferencing pointer to incomplete type
output.c:479: error: dereferencing pointer to incomplete type
output.c:479: error: dereferencing pointer to incomplete type
output.c:480: error: dereferencing pointer to incomplete type
output.c:480: error: dereferencing pointer to incomplete type
output.c:482: error: dereferencing pointer to incomplete type
output.c:484: error: dereferencing pointer to incomplete type
output.c:486: error: dereferencing pointer to incomplete type
output.c:493: error: dereferencing pointer to incomplete type
output.c:494: error: dereferencing pointer to incomplete type
output.c:497: error: dereferencing pointer to incomplete type
output.c:499: error: dereferencing pointer to incomplete type
output.c:505: error: dereferencing pointer to incomplete type
output.c:507: error: dereferencing pointer to incomplete type
output.c:508: error: dereferencing pointer to incomplete type
output.c:509: error: dereferencing pointer to incomplete type
output.c:514: error: dereferencing pointer to incomplete type
output.c:514: error: dereferencing pointer to incomplete type
output.c:519: error: dereferencing pointer to incomplete type
output.c:522: error: dereferencing pointer to incomplete type
output.c:524: error: dereferencing pointer to incomplete type
output.c:528: error: dereferencing pointer to incomplete type
output.c:536: error: dereferencing pointer to incomplete type
output.c:541: error: dereferencing pointer to incomplete type
output.c:559: error: dereferencing pointer to incomplete type
output.c:560: error: dereferencing pointer to incomplete type
output.c:563: error: dereferencing pointer to incomplete type
output.c:565: error: dereferencing pointer to incomplete type
output.c:566: error: dereferencing pointer to incomplete type
output.c:567: error: dereferencing pointer to incomplete type
output.c:569: error: dereferencing pointer to incomplete type
output.c:570: error: dereferencing pointer to incomplete type
output.c:571: error: dereferencing pointer to incomplete type
output.c:573: error: dereferencing pointer to incomplete type
output.c:576: error: dereferencing pointer to incomplete type
output.c:584: error: dereferencing pointer to incomplete type
output.c:584: error: dereferencing pointer to incomplete type
output.c:586: warning: implicit declaration of function `glDisable'
output.c:586: error: `GL_SCISSOR_TEST' undeclared (first use in this function)
output.c:590: warning: implicit declaration of function `glEnable'
output.c:591: warning: implicit declaration of function `glScissor'
output.c:591: error: dereferencing pointer to incomplete type
output.c:597: warning: implicit declaration of function `glLoadIdentity'
output.c:599: warning: implicit declaration of function `gluOrtho2D'
output.c:599: error: dereferencing pointer to incomplete type
output.c:599: error: dereferencing pointer to incomplete type
output.c:599: error: dereferencing pointer to incomplete type
output.c:600: error: dereferencing pointer to incomplete type
output.c:600: error: dereferencing pointer to incomplete type
output.c:601: error: dereferencing pointer to incomplete type
output.c:605: warning: implicit declaration of function `glClearColor'
output.c:606: warning: implicit declaration of function `glClear'
output.c:606: error: `GL_COLOR_BUFFER_BIT' undeclared (first use in this function)
output.c:608: error: `GL_TEXTURE_2D' undeclared (first use in this function)
output.c:609: error: dereferencing pointer to incomplete type
output.c:613: warning: implicit declaration of function `glColor3f'
output.c:616: warning: implicit declaration of function `glBegin'
output.c:616: error: `GL_POLYGON' undeclared (first use in this function)
output.c:617: warning: implicit declaration of function `glVertex2i'
output.c:624: warning: implicit declaration of function `glEnd'
output.c:633: error: dereferencing pointer to incomplete type
output.c:633: error: dereferencing pointer to incomplete type
output.c:634: error: dereferencing pointer to incomplete type
output.c:634: error: dereferencing pointer to incomplete type
output.c:641: error: dereferencing pointer to incomplete type
output.c:644: warning: implicit declaration of function `glPushMatrix'
output.c:646: error: dereferencing pointer to incomplete type
output.c:646: error: dereferencing pointer to incomplete type
output.c:649: warning: implicit declaration of function `glPopMatrix'
output.c:672: error: dereferencing pointer to incomplete type
output.c:676: error: dereferencing pointer to incomplete type
output.c:684: error: dereferencing pointer to incomplete type
output.c:699: error: dereferencing pointer to incomplete type
output.c:699: error: dereferencing pointer to incomplete type
output.c:708: warning: implicit declaration of function `glXSwapBuffers'
output.c:711: warning: implicit declaration of function `glFinish'
output.c:725: error: dereferencing pointer to incomplete type
output.c:730: error: dereferencing pointer to incomplete type
output.c: In function `output_idle_wakeup':
output.c:738: error: dereferencing pointer to incomplete type
output.c:740: error: dereferencing pointer to incomplete type
output.c:741: error: dereferencing pointer to incomplete type
output.c:742: error: dereferencing pointer to incomplete type
output.c: In function `output_invalidate_rect':
output.c:792: error: dereferencing pointer to incomplete type
output.c:792: error: dereferencing pointer to incomplete type
output.c: In function `on_expose':
output.c:801: error: dereferencing pointer to incomplete type
output.c:805: error: dereferencing pointer to incomplete type
output.c: In function `on_configure_notify':
output.c:838: error: dereferencing pointer to incomplete type
output.c:838: error: dereferencing pointer to incomplete type
output.c: In function `lmc_output_new':
output.c:881: error: `GLXContext' undeclared (first use in this function)
output.c:881: error: syntax error before "context"
output.c:885: error: `context' undeclared (first use in this function)
output.c:893: error: dereferencing pointer to incomplete type
output.c:894: error: dereferencing pointer to incomplete type
output.c:896: error: dereferencing pointer to incomplete type
output.c:897: error: dereferencing pointer to incomplete type
output.c:899: error: dereferencing pointer to incomplete type
output.c:901: error: dereferencing pointer to incomplete type
output.c:902: error: dereferencing pointer to incomplete type
output.c:904: error: dereferencing pointer to incomplete type
output.c:905: error: dereferencing pointer to incomplete type
output.c:907: error: dereferencing pointer to incomplete type
output.c:910: error: dereferencing pointer to incomplete type
output.c:910: error: dereferencing pointer to incomplete type
output.c:912: error: dereferencing pointer to incomplete type
output.c:928: error: dereferencing pointer to incomplete type
output.c:929: error: dereferencing pointer to incomplete type
output.c:930: error: dereferencing pointer to incomplete type
output.c:930: error: dereferencing pointer to incomplete type
output.c:931: error: dereferencing pointer to incomplete type
output.c:931: error: dereferencing pointer to incomplete type
output.c:933: error: dereferencing pointer to incomplete type
output.c: In function `lmc_output_get_size':
output.c:944: error: dereferencing pointer to incomplete type
output.c:946: error: dereferencing pointer to incomplete type
output.c: In function `lmc_output_queue_bread_crumb':
output.c:956: error: dereferencing pointer to incomplete type
output.c:961: error: dereferencing pointer to incomplete type
output.c:965: error: dereferencing pointer to incomplete type
output.c: In function `lmc_output_get_main_viewport':
output.c:971: error: dereferencing pointer to incomplete type
output.c: In function `lmc_output_add_viewport':
output.c:989: error: dereferencing pointer to incomplete type
output.c:991: error: dereferencing pointer to incomplete type
output.c:991: error: dereferencing pointer to incomplete type
output.c:993: error: dereferencing pointer to incomplete type
output.c:993: error: dereferencing pointer to incomplete type
output.c:995: error: dereferencing pointer to incomplete type
output.c: In function `lmc_output_set_visible_rect':
output.c:1004: error: dereferencing pointer to incomplete type
output.c:1006: error: dereferencing pointer to incomplete type
output.c:1008: error: dereferencing pointer to incomplete type
output.c:1008: error: dereferencing pointer to incomplete type
output.c:1010: error: dereferencing pointer to incomplete type
output.c: In function `lmc_output_get_visible_rect':
output.c:1017: error: dereferencing pointer to incomplete type
output.c:1020: error: dereferencing pointer to incomplete type
output.c:1022: error: dereferencing pointer to incomplete type
output.c: In function `lmc_output_viewport_offset':
output.c:1032: error: dereferencing pointer to incomplete type
output.c:1037: error: dereferencing pointer to incomplete type
output.c:1037: error: dereferencing pointer to incomplete type
output.c:1039: error: dereferencing pointer to incomplete type
output.c: In function `lmc_output_viewport_set_bgcolor':
output.c:1050: error: dereferencing pointer to incomplete type
output.c:1056: error: dereferencing pointer to incomplete type
output.c:1056: error: dereferencing pointer to incomplete type
output.c:1058: error: dereferencing pointer to incomplete type
output.c: In function `lmc_output_destroy':
output.c:1066: error: dereferencing pointer to incomplete type
output.c:1071: error: dereferencing pointer to incomplete type
output.c:1072: error: dereferencing pointer to incomplete type
output.c:1074: error: dereferencing pointer to incomplete type
output.c:1076: error: dereferencing pointer to incomplete type
output.c:1077: error: dereferencing pointer to incomplete type
output.c:1080: error: dereferencing pointer to incomplete type
output.c:1081: error: dereferencing pointer to incomplete type
output.c: In function `lmc_output_freeze':
output.c:1087: error: dereferencing pointer to incomplete type
output.c:1089: error: dereferencing pointer to incomplete type
output.c:1091: error: dereferencing pointer to incomplete type
output.c: In function `lmc_output_thaw':
output.c:1097: error: dereferencing pointer to incomplete type
output.c:1099: error: dereferencing pointer to incomplete type
output.c:1101: error: dereferencing pointer to incomplete type
output.c:1103: error: dereferencing pointer to incomplete type
output.c:1105: error: dereferencing pointer to incomplete type
output.c:1106: error: dereferencing pointer to incomplete type
output.c:1109: error: dereferencing pointer to incomplete type
output.c: In function `output_modify_texture':
output.c:1127: error: dereferencing pointer to incomplete type
output.c:1127: error: dereferencing pointer to incomplete type
output.c:1130: error: dereferencing pointer to incomplete type
output.c:1130: error: dereferencing pointer to incomplete type
output.c:1132: error: dereferencing pointer to incomplete type
output.c:1134: error: dereferencing pointer to incomplete type
output.c:1134: error: dereferencing pointer to incomplete type
output.c: In function `lmc_output_set_background':
output.c:1143: error: dereferencing pointer to incomplete type
output.c:1143: error: dereferencing pointer to incomplete type
output.c:1145: error: dereferencing pointer to incomplete type
output.c:1147: error: dereferencing pointer to incomplete type
output.c:1147: error: dereferencing pointer to incomplete type
output.c:1147: error: dereferencing pointer to incomplete type
output.c:1148: error: dereferencing pointer to incomplete type
output.c:1148: error: dereferencing pointer to incomplete type
output.c:1148: error: dereferencing pointer to incomplete type
output.c:1149: error: dereferencing pointer to incomplete type
output.c:1154: error: dereferencing pointer to incomplete type
output.c:1155: error: dereferencing pointer to incomplete type
output.c:1159: error: dereferencing pointer to incomplete type
output.c:1159: error: dereferencing pointer to incomplete type
output.c: In function `lmc_output_set_cursor':
output.c:1173: error: dereferencing pointer to incomplete type
output.c:1175: error: dereferencing pointer to incomplete type
output.c:1175: error: dereferencing pointer to incomplete type
output.c:1177: error: dereferencing pointer to incomplete type
output.c:1177: error: dereferencing pointer to incomplete type
output.c:1181: error: dereferencing pointer to incomplete type
output.c:1183: error: dereferencing pointer to incomplete type
output.c:1183: error: dereferencing pointer to incomplete type
output.c:1184: error: dereferencing pointer to incomplete type
output.c:1184: error: dereferencing pointer to incomplete type
output.c:1189: error: dereferencing pointer to incomplete type
output.c:1191: error: dereferencing pointer to incomplete type
output.c:1191: error: dereferencing pointer to incomplete type
output.c:1191: error: dereferencing pointer to incomplete type
output.c:1192: error: dereferencing pointer to incomplete type
output.c:1192: error: dereferencing pointer to incomplete type
output.c:1192: error: dereferencing pointer to incomplete type
output.c:1193: error: dereferencing pointer to incomplete type
output.c:1198: error: dereferencing pointer to incomplete type
output.c:1199: error: dereferencing pointer to incomplete type
output.c:1204: error: dereferencing pointer to incomplete type
output.c:1205: error: dereferencing pointer to incomplete type
output.c:1209: error: dereferencing pointer to incomplete type
output.c:1211: error: dereferencing pointer to incomplete type
output.c:1211: error: dereferencing pointer to incomplete type
output.c:1212: error: dereferencing pointer to incomplete type
output.c:1212: error: dereferencing pointer to incomplete type
output.c:1215: error: dereferencing pointer to incomplete type
output.c: In function `lmc_output_set_pager':
output.c:1227: error: dereferencing pointer to incomplete type
output.c:1229: error: dereferencing pointer to incomplete type
output.c:1231: error: dereferencing pointer to incomplete type
output.c:1231: error: dereferencing pointer to incomplete type
output.c:1231: error: dereferencing pointer to incomplete type
output.c:1232: error: dereferencing pointer to incomplete type
output.c:1232: error: dereferencing pointer to incomplete type
output.c:1232: error: dereferencing pointer to incomplete type
output.c:1233: error: dereferencing pointer to incomplete type
output.c:1236: error: dereferencing pointer to incomplete type
output.c:1237: error: dereferencing pointer to incomplete type
output.c:1238: error: dereferencing pointer to incomplete type
output.c:1239: error: dereferencing pointer to incomplete type
output.c:1240: error: dereferencing pointer to incomplete type
output.c:1244: error: dereferencing pointer to incomplete type
output.c:1245: error: dereferencing pointer to incomplete type
output.c:1249: error: dereferencing pointer to incomplete type
output.c:1249: error: dereferencing pointer to incomplete type
output.c:1251: error: dereferencing pointer to incomplete type
output.c: In function `lmc_output_create_window':
output.c:1288: error: dereferencing pointer to incomplete type
output.c:1295: error: dereferencing pointer to incomplete type
output.c:1295: error: dereferencing pointer to incomplete type
output.c:1297: error: dereferencing pointer to incomplete type
output.c: In function `output_window_delete_texture':
output.c:1309: error: dereferencing pointer to incomplete type
output.c:1309: error: dereferencing pointer to incomplete type
output.c:1310: error: dereferencing pointer to incomplete type
output.c:1310: error: dereferencing pointer to incomplete type
output.c: In function `lmc_output_window_destroy':
output.c:1323: error: dereferencing pointer to incomplete type
output.c:1327: error: dereferencing pointer to incomplete type
output.c:1327: error: dereferencing pointer to incomplete type
output.c:1339: error: dereferencing pointer to incomplete type
output.c: In function `lmc_output_window_set_bits':
output.c:1348: error: dereferencing pointer to incomplete type
output.c:1350: error: dereferencing pointer to incomplete type
output.c:1373: error: dereferencing pointer to incomplete type
output.c: In function `lmc_output_window_set_alpha':
output.c:1382: error: dereferencing pointer to incomplete type
output.c:1387: error: dereferencing pointer to incomplete type
output.c: In function `lmc_output_window_set_deformation':
output.c:1397: error: dereferencing pointer to incomplete type
output.c:1411: error: dereferencing pointer to incomplete type
output.c: In function `lmc_output_window_move':
output.c:1421: error: dereferencing pointer to incomplete type
output.c:1433: error: dereferencing pointer to incomplete type
output.c: In function `lmc_output_window_restack':
output.c:1445: error: dereferencing pointer to incomplete type
output.c:1449: error: dereferencing pointer to incomplete type
output.c:1454: error: dereferencing pointer to incomplete type
output.c:1462: error: dereferencing pointer to incomplete type
output.c:1462: error: dereferencing pointer to incomplete type
output.c:1463: error: dereferencing pointer to incomplete type
output.c:1463: error: dereferencing pointer to incomplete type
output.c:1468: error: dereferencing pointer to incomplete type
output.c: In function `lmc_output_window_modify':
output.c:1480: error: dereferencing pointer to incomplete type
output.c:1484: error: dereferencing pointer to incomplete type
output.c: In function `lmc_output_set_show_pager':
output.c:1491: error: dereferencing pointer to incomplete type
output.c:1495: error: dereferencing pointer to incomplete type
output.c:1497: error: dereferencing pointer to incomplete type
output.c:1499: error: dereferencing pointer to incomplete type
output.c:1499: error: dereferencing pointer to incomplete type
output.c:1502: error: dereferencing pointer to incomplete type
make[2]: *** [output.o] B&#322;&#261;d 1
make[2]: Opuszczenie katalogu `/home/promethe/luminocity/src/luminocity/luminocity/src'
make[1]: *** [install] B&#322;&#261;d 2
make[1]: Opuszczenie katalogu `/home/promethe/luminocity/src/luminocity/luminocity/src'
make: *** [install-recursive] B&#322;&#261;d 1
*** error during stage install of luminocity: could not make module *** [24/24]


  [1] rerun stage install
  [2] ignore error and continue to done
  [3] give up on module
  [4] start shell
choice:
```

People, please, help me!

(*Nie ma takiego pliku ani katalogu* means *There aren't any file nor directory like this*)

FIXED: Installed one library :]

---

### Post by Promethe on 2005-04-15
I think, then this is last error which I'll recive:
```
bject-2.0 -lgmodule-2.0 -lglib-2.0 -lXdamage -lXcomposite -lXfixes -lXtst -lXext -lXcursor -lXrender -lX11 -ldl   -L /usr/X11R6/lib -lGL -lGLU
/usr/X11R6/lib/libGL.a(glxcmds.o)(.text+0x2eea): In function `glXGetMscRateOML':: undefined reference to `XF86VidModeQueryVersion'
/usr/X11R6/lib/libGL.a(glxcmds.o)(.text+0x2f1a): In function `glXGetMscRateOML':: undefined reference to `XF86VidModeGetModeLine'
collect2: ld returned 1 exit status
make[3]: *** [luminocity] B&#322;&#261;d 1
make[3]: Opuszczenie katalogu `/home/promethe/luminocity/src/luminocity/luminocity/src'
make[2]: *** [all] B&#322;&#261;d 2
make[2]: Opuszczenie katalogu `/home/promethe/luminocity/src/luminocity/luminocity/src'
make[1]: *** [all-recursive] B&#322;&#261;d 1
make[1]: Opuszczenie katalogu `/home/promethe/luminocity/src/luminocity/luminocity'
make: *** [all] B&#322;&#261;d 2
*** error during stage build of luminocity: could not build module *** [24/24]
```
HELP!

---

### Post by Dali on 2005-06-20
I've been getting the same errors as you, which is quite frustrating considering I managed to nagivate through all the steps so far involving compiling jhbuild, etc.

Can ANYONE help with the install of Luminocity on Hoary???

This is where I'm stuck:

cvs -z3 -q -d :pserver:anonymous@anoncvs.gnome.org:/cvs/gnome update -dP -A .
*** Building luminocity *** [19/19]

make
make  all-recursive
make[1]: Entering directory `/home/dali/cvs/gnome2/luminocity'
Making all in src
make[2]: Entering directory `/home/dali/cvs/gnome2/luminocity/src'
make  all-am
make[3]: Entering directory `/home/dali/cvs/gnome2/luminocity/src'
gcc  -g -O2 -Wall   -o luminocity  async.o bits.o decoration.o display.o events.o gui.o lmc-marshal.o main.o output.o root.o texture.o toplevel.o utils.o window.o spring-model.o -pthread -L/home/dali/prefix/lib -L/usr/local/kx/lib -lgthread-2.0 -lgdk_pixbuf-2.0 -lm -lpangoft2-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -lglib-2.0 -lXdamage -lXcomposite -lXfixes -lXtst -lXext -lXcursor -lXrender -lX11 -ldl   -L /usr/X11R6/lib -lGL -lGLU
/usr/X11R6/lib/libGL.a(glxcmds.o)(.text+0x2eea): In function `glXGetMscRateOML':
: undefined reference to `XF86VidModeQueryVersion'
/usr/X11R6/lib/libGL.a(glxcmds.o)(.text+0x2f1a): In function `glXGetMscRateOML':
: undefined reference to `XF86VidModeGetModeLine'
collect2: ld returned 1 exit status
make[3]: *** [luminocity] Error 1
make[3]: Leaving directory `/home/dali/cvs/gnome2/luminocity/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/dali/cvs/gnome2/luminocity/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dali/cvs/gnome2/luminocity'
make: *** [all] Error 2
*** error during stage build of luminocity: could not build module *** [19/19]

If anyone has figured this out, I'd love to know how to fix it.  

Cheers,

dali

---

### Post by afonit on 2005-07-07
[QUOTE=garyniger]I fixed it.  I needed to install libxxf86vm-dev and add -lXxf86vm to the linker parameter list in the luminocity makefile.[/QUOTE]


which makefile did you add -lXxf86vm to?  I searched in the luminocity directory and ton's of make files showed up, and where in the make file did you add it, can you post sample code?

---

