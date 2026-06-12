---
title: "How to link header files??"
date: 2008-07-05
forum: Programming Talk
---

### Post by ima998 on 2008-07-05
hi,

Im trying to link client.o file ,I get these error messages

client.cpp: (.text+0x16d): undefined reference to `rcss::net::Addr::ANY'
client.cpp: (.text+0x17c): undefined reference to`rcss::net::Addr::Addr (unsigned short, unsigned int)'

and many more similar errors,

'rcss' is implemented in .hpp files which are in a different directory  (/home/imantha/rcss/rcssbase-12.1.0/rcssbase/net)

and the client.cpp has these include lines

#include <rcssbase/thread.h>
#include <rcssbase/messagequeue.h>
#include <rcssbase/sharedvar.h>
#include <rcssbase/net/socketstreambuf.hpp>
#include <rcssbase/net/udpsocket.hpp>
#include <rcssbase/gzip/gzstream.hpp>

Can anybody please help me with it?

---

### Post by CptPicard on 2008-07-05
See the -I option of the compiler, it specifies header file directories.

---

### Post by ima998 on 2008-07-05
thanks for the reply

well I can compile it with

g++ client.cpp -c 

without errors ,but errors come when I try to link the object file with others . 
I tried the -I option but still no luck

any suggestions??

---

### Post by ima998 on 2008-07-05
Ok let me be clear here

how can I link client.o and random.lo (library object file) files? 
two files are in _different folders_

many thanks

---

### Post by ceclauson on 2008-07-05
All of my experience is in linking against static libraries.  I don't know if that's the same as what you're trying to do, but I'll describe it really fast, and hopefully it will be helpful.

In order to do this, you use the -l switch on the command line, followed by the name of the library you want to link against.  There's a caveat though: generally a library's name starts with "lib", some name, and then an extension like ".a" or ".la".  When you specify a library on the command line, you omit the "lib" prefix and the extension.  For example, libSDL.a would be identified with the switch -lSDL, liblua.la would be -llua, etc.

Usually libraries are searched for in the usr/lib folder.  If its somewhere else, you can use a full pathname with the -l switch.  For example, -l/home/me/Desktop/myfolder/mylib.

Again, I don't know if this was helpful.  Hopefully it was.

Cooper

---

### Post by ima998 on 2008-07-05
what seems to be the problem is that my program is using the 'rcss' namespace , which is implemented in a different file ,compiler doesnt seems to identify the implementation of it hhen I use that namespace.

---

