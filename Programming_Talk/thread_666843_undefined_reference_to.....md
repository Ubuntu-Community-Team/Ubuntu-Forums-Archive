---
title: "undefined reference to...."
date: 2008-01-13
forum: Programming Talk
---

### Post by Crapodino on 2008-01-13
Hi! i am trying to compile/link a simple application that uses a library called OpenDBX. I have already compiled and installed that library. Now, i am trying to do a simple client of it.

The client (Prueba.c) is just like this:
```

#include <stdio.h>
#include <stdlib.h>
#include <stdint.h>
#include <odbx.h>

int main(void) {
	puts("Hello World!!");
	
		int err;
		odbx_t* handle;
	
		if( ( err = odbx_init( &handle, "mysql", "127.0.0.1", "" ) ) < 0 )
		{
		    fprintf( stderr, "odbx_init(): %s\n", odbx_error( handle, err ) );
		    return err;
		}
		
		return EXIT_SUCCESS;
}
```



When i try to compile that program (Prueba.c), i has this error:

cc    -c -o Prueba.o Prueba.c
gcc -O2 -g -Wall -fmessage-length=0 -L/usr/local/lib -L/usr/local/lib/opendbx -L/usr/local/lib/pkgconfig -o Pruebas Prueba.o 
Prueba.o: In function `main':
Prueba.c:(.text+0x3c): undefined reference to `odbx_init'
Prueba.c:(.text+0x57): undefined reference to `odbx_error'
collect2: ld returned 1 exit status
make: *** [Pruebas] Error 1


Those functions (odbx_error and odbx_init are both defined in odbx.h (the header of openDBX y need to include).

I have checked that openDBX libraries are okey. There are in /usr/local/lib ,  /usr/local/lib/opendbx  and /usr/local/lib/pkgconfig.

My makefile is like this:

```

COMPILER = gcc

CCFLAGS =	-O2 -g -Wall -fmessage-length=0 

OBJS =		Prueba.o

LIBS = 

TARGET =	Pruebas

LDFLAGS = -L/usr/local/lib -L/usr/local/lib/opendbx -L/usr/local/lib/pkgconfig

$(TARGET):	$(OBJS)
	${COMPILER} ${CCFLAGS} $(LDFLAGS) -o $(TARGET) $(OBJS) $(LIBS)

all:	$(TARGET)

clean:
	rm -f $(OBJS) $(TARGET)


```

So...can someone please tell what does this error mean ? i think that it doesn't found the library asosiated with de odbx.h, but i am not sure.

Very thanks

Mariano

---

### Post by aks44 on 2008-01-13
**-I** (uppercase **i**) specifies directories where the compiler will search for **#include [COLOR="Red"]<[/COLOR]???[COLOR="Red"]>[/COLOR]** files (not **#include [COLOR="Red"]"[/COLOR]???[COLOR="Red"]"[/COLOR]**) in addition to default locations. eg. **-I/path/to/headers/**

**-L** specifies directories where the linker will search for libraries in addition to default locations. eg. **-L/path/to/libraries/**

**-l** (lowercase **L**) tells the linker what libraries it must link your program to in addition to default libraries. eg. **-lwhatever** will instruct the linker to look for **libwhatever.so** (in the -L directories) and link that library to your program.


In your case, you are missing at least one -l (lowercase L) flag.

---

