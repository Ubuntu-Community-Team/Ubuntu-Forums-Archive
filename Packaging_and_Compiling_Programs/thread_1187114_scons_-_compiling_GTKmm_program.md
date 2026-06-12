---
title: "scons - compiling GTKmm program"
date: 2009-06-14
forum: Packaging and Compiling Programs
---

### Post by lampak on 2009-06-14
I've written such SConstruct file: 
```

env = Environment()
biblioteki = ["gtk+-2.0", "gtkmm-2.4", "libglademm-2.4", "glibmm-2.4", "gdkmm-2.4"]
#env.Append(LIBPATH = ['/usr/lib', '/usr/local/lib'])
conf = Configure(env)
SaBibl = 1
for x in biblioteki:
	if not conf.CheckLib(x):
		SaBibl = 0
if not SaBibl:
	print "You don't have needed libraries!"
	#Exit(1)
env.Append(LIBS=biblioteki)
env.ParseConfig('pkg-config --cflags --libs gtk+-2.0')
env.ParseConfig('pkg-config --cflags --libs gtkmm-2.4')
env.ParseConfig('pkg-config --cflags --libs libglademm-2.4')
env.ParseConfig('pkg-config --cflags --libs glibmm-2.4')
env.ParseConfig('pkg-config --cflags --libs gdkmm-2.4')
zrodla = Glob("src/*.cpp")
env.Program(target="miernik", source=zrodla)

```

The problems are: 
1) ChceckLib for gtk+-2.0 gives 'no', even though the library is installed and there is 'gkt+-2.0' folder in /usr/lib
2) Compiling at first goes well, but then I get a message: 
> e.o src/main.o src/okno.o -L/usr/lib -L/usr/local/lib -lgtk+-2.0 -lglademm-2.4 -lglademm-2.4 -lgtkmm-2.4 -lglade-2.0 -lgiomm-2.4 -latkmm-1.6 -lgtk-x11-2.0 -lxml2 -latk-1.0 -lpangoft2-1.0 -lfreetype -lfontconfig -lgdkmm-2.4 -lpangomm-1.4 -lgdk-x11-2.0 -lglibmm-2.4 -lcairomm-1.0 -lsigc-2.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -lglib-2.0 -lcairo
/usr/bin/ld: cannot find -lgtk+-2.0


The program compiles well in Code::Blocks and using cmake. Uncommenting the line with LIBPATH doesn't change anything. Commenting ParseConfig lines results in an error when the compiler cannot find a <gtkmm.h> header file. 

Does anyone know what's wrong?

---

### Post by Linteg on 2009-06-14
Have you installed the -dev packages (libgtkmm-2.4-dev etc)?

---

### Post by lampak on 2009-06-14
I have installed them all. As I said, I don't have any problem with compiling it in Code::Blocks. 

And in case I hadn't made it clear - checking all other libraries than gtk+ gives positive results.

EDIT: And pkg-config doesn't fail despite the fact that scons can't see gtk+.

---

### Post by lampak on 2009-06-14
I solved my problem just not including gtk+. It's not needed since gtkmm replaces it. I still don't know what was wrong with the previous code (why didn't scons find the library?), but temporally it doesn't matter.

---

