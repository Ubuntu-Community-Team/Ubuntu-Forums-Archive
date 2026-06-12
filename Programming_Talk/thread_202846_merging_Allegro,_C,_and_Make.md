---
title: "merging Allegro, C, and Make"
date: 2006-06-24
forum: Programming Talk
---

### Post by dave_567 on 2006-06-24
[CENTER]:confused: [/CENTER]

This is something simple, but I'm just not getting it.  I'm trying to compile one of the allegro examples and I keep getting errors to many undefined references.  I can't figure out why the library is not linking properly.  

The precompiled version fo the example works.  So I think all system configurations re OK.

Here is the makefile and some of thelong list of errors.  Any ideas? ](*,) 

  # default compiler
CC=gcc

# define object files 
my_objects = ex3d.o

# define source files
my_source = ex3d.c

# Linking object files
allegtest: $(my_objects)
	$(CC) -o allegtest $(my_objects) -lalleg
	echo ~~~~ sample: creating executble file

# Compiling source files
ex3d.o: $(my_source) 
	$(CC) -c $(my_source)
	echo ~~~~ sample: creating object files

# Removing the executable and the object files
clean: 
	rm *.o
	echo ~~~~~~~~~ clean: make complete


dave@ubuntu:~/Code/SystemWars/Code02$ make
gcc -o allegtest ex3d.o -lalleg
/usr/lib/gcc/x86_64-linux-gnu/4.0.2/../../../../lib64/liballeg.a(color.o): In function `hsv_to_rgb':
: undefined reference to `fmod'
/usr/lib/gcc/x86_64-linux-gnu/4.0.2/../../../../lib64/liballeg.a(gfx.o): In function `do_arc':
: undefined reference to `cos'
/usr/lib/gcc/x86_64-linux-gnu/4.0.2/../../../../lib64/liballeg.a(gfx.o): In function `do_arc':
: undefined reference to `sin'
/usr/lib/gcc/x86_64-linux-gnu/4.0.2/../../../../lib64/liballeg.a(gfx.o): In function `do_arc':
: undefined reference to `cos'
/usr/lib/gcc/x86_64-linux-gnu/4.0.2/../../../../lib64/liballeg.a(gfx.o): In function `do_arc':
: undefined reference to `sin'
/usr/lib/gcc/x86_64-linux-gnu/4.0.2/../../../../lib64/liballeg.a(math.o): In function `fixhypot':
: undefined reference to `hypot'
/usr/lib/gcc/x86_64-linux-gnu/4.0.2/../../../../lib64/liballeg.a(math3d.o): In function `get_x_rotate_matrix_f':
: undefined reference to `cos'
/usr/lib/gcc/x86_64-linux-gnu/4.0.2/../../../../lib64/liballeg.a(math3d.o): In function `get_x_rotate_matrix_f':
: undefined reference to `sin'
/usr/lib/gcc/x86_64-linux-gnu/4.0.2/../../../../lib64/liballeg.a(math3d.o): In function `get_y_rotate_matrix_f':

---

### Post by hod139 on 2006-06-24
All the undefines appear to be from the math library.  You can try adding
```
-lm
```
to link against the math libs.  Hopefully that works.

---

### Post by dave_567 on 2006-06-24
No luck.  Now it misses all the references.



# default compiler
CC=gcc

# define object files 
my_objects = ex3d.o

# define source files
my_source = ex3d.c

# Linking object files
allegtest: $(my_objects)
	$(CC) -o allegtest $(my_objects) -lmalleg
	echo ~~~~ sample: creating executble file

# Compiling source files
ex3d.o: $(my_source) 
	$(CC) -c $(my_source)
	echo ~~~~ sample: creating object files

# Removing the executable and the object files
clean: 
	rm *.o
	echo ~~~~~~~~~ clean: make complete



dave@ubuntu:~/Code/SystemWars/Code02$ make
gcc -o allegtest ex3d.o -lmalleg
/usr/bin/ld: cannot find -lmalleg
collect2: ld returned 1 exit status
make: *** [allegtest] Error 1
dave@ubuntu:~/Code/SystemWars/Code02$

---

### Post by hod139 on 2006-06-26
[quote=dave_567]
# Linking object files
allegtest: $(my_objects)
    $(CC) -o allegtest $(my_objects) -lmalleg
    echo ~~~~ sample: creating executble file
[/quote]
This is wrong.  Try 
```

$(CC) -o allegtest $(my_objects) -lm -lalleg

```

---

