---
title: "Error trying to compile winsock app with mingw"
date: 2007-05-12
forum: Programming Talk
---

### Post by jenkem on 2007-05-12
I am trying to compile a simple windows application on Ubuntu fiesty using mingw-gcc. I am getting the following errors:

```
$ i586-mingw32msvc-gcc -lws2_32 coco.c
coco.c: In function `main':
coco.c:61: warning: return type of 'main' is not `int'
/tmp/ccxABKPU.o:coco.c:(.text+0x2f): undefined reference to `_send@16'
/tmp/ccxABKPU.o:coco.c:(.text+0x78): undefined reference to `_WSAStartup@8'
/tmp/ccxABKPU.o:coco.c:(.text+0x89): undefined reference to `_socket@12'
/tmp/ccxABKPU.o:coco.c:(.text+0xb0): undefined reference to `_inet_addr@4'
/tmp/ccxABKPU.o:coco.c:(.text+0xd4): undefined reference to `_htons@4'
/tmp/ccxABKPU.o:coco.c:(.text+0xec): undefined reference to `_connect@12'
/tmp/ccxABKPU.o:coco.c:(.text+0x12f): undefined reference to `_recv@16'
/tmp/ccxABKPU.o:coco.c:(.text+0x140): undefined reference to `_send@16'
/tmp/ccxABKPU.o:coco.c:(.text+0x172): undefined reference to `_recv@16'
/tmp/ccxABKPU.o:coco.c:(.text+0x1a9): undefined reference to `_send@16'
/tmp/ccxABKPU.o:coco.c:(.text+0x1db): undefined reference to `_recv@16'
/tmp/ccxABKPU.o:coco.c:(.text+0x22b): undefined reference to `_send@16'
/tmp/ccxABKPU.o:coco.c:(.text+0x25a): undefined reference to `_recv@16'
collect2: ld returned 1 exit status

I've tried to link with the wine DLL, with the exact same errors:
$ i586-mingw32msvc-dlltool --input-def libws2_32.def  --dllname WS2_32.DLL --output-lib libws2_32
$ i586-mingw32msvc-gcc libws2_32.a coco.c
coco.c: In function `main':
coco.c:61: warning: return type of 'main' is not `int'
/tmp/ccPOcY4D.o:coco.c:(.text+0x2f): undefined reference to `_send@16'
/tmp/ccPOcY4D.o:coco.c:(.text+0x78): undefined reference to `_WSAStartup@8'
/tmp/ccPOcY4D.o:coco.c:(.text+0x89): undefined reference to `_socket@12'
/tmp/ccPOcY4D.o:coco.c:(.text+0xb0): undefined reference to `_inet_addr@4'
/tmp/ccPOcY4D.o:coco.c:(.text+0xd4): undefined reference to `_htons@4'
/tmp/ccPOcY4D.o:coco.c:(.text+0xec): undefined reference to `_connect@12'
/tmp/ccPOcY4D.o:coco.c:(.text+0x12f): undefined reference to `_recv@16'
/tmp/ccPOcY4D.o:coco.c:(.text+0x140): undefined reference to `_send@16'
/tmp/ccPOcY4D.o:coco.c:(.text+0x172): undefined reference to `_recv@16'
/tmp/ccPOcY4D.o:coco.c:(.text+0x1a9): undefined reference to `_send@16'
/tmp/ccPOcY4D.o:coco.c:(.text+0x1db): undefined reference to `_recv@16'
/tmp/ccPOcY4D.o:coco.c:(.text+0x22b): undefined reference to `_send@16'
/tmp/ccPOcY4D.o:coco.c:(.text+0x25a): undefined reference to `_recv@16'
collect2: ld returned 1 exit status
```


Any idea how I can rectify this problem? Thanks.

---

### Post by Wim Sturkenboom on 2007-05-13
I don't know the finer details of 'cross-compiling', but the error indicates that you're missing a library.

---

### Post by omax on 2008-01-20
I know this is a really old thread, but I had the same problem and couldn't find the answer anywhere...

It's easy, -lws2_32 must come after source. ie:
```
$ i586-mingw32msvc-gcc -o prog.exe prog.c -lws2_32
```

---

### Post by efittery on 2008-08-04
Really, thanks for this tip.  I have been trying to compile socket code with -mno-cygwin flag for 2 weeks.  This suggestion of using the -lws2_32 flag at link time worked great.  I am not sure the code is working, but at least it compiles and links.  Keep on trucking.

---

### Post by swmail on 2009-07-29
Thanks omax wor the cool tip!
For me works too.

---

### Post by Xerxesx on 2010-01-24
With source given below, which I called winsock.cpp. I was able to get a working executable with the following build command (run under MINGW32 bourne):
 
[INDENT]g++ winsock.cpp -lws2_32 -owinsock.exe
[/INDENT]I was able to execute with:
[INDENT]./winsock.exe
PC name: XerxexX
Press any key to continue . . .
[/INDENT]For those of you like me using using slick-edit:
[INDENT]Build->GNU C Options...
under "Link" tab in "Libraries/Objects" add -lws2_32
[/INDENT]//------- winsock.cpp -----------------------------
#include <iostream> 
#include <windows.h>     
#include <stdio.h>       
#include <tchar.h>       
#include <fstream> 
#include <sstream> 
#include <string> 
#include <time.h> 
#include <winsock.h>
#define MAX_SIZE 200
using namespace std;
int main (int argc, char *argv[])
{
    struct WSAData wsa_data; 
    int ret_code; 
 
    char host_name[MAX_SIZE]="unknown\0"; 
    char buf[MAX_SIZE]; 
 
    WSAStartup(MAKEWORD(1, 1), &wsa_data); 
    ret_code = gethostname(buf, MAX_SIZE); 
 
    if (ret_code != SOCKET_ERROR)
    {
       int i=-1;
       do
       {
          i++;
          host_name[i]=buf[i];
       } while (buf[i] > '\0');
    }
    cout<<"PC name: " << host_name << endl; 
    system("pause"); 
 
    WSACleanup();
    return(0);
}

---

### Post by dwhitney67 on 2010-01-24
Why not just strcpy() for this bit of code?:
```

int i=-1;
do
{
i++;
host_name[i]=buf[i];
} while (buf[i] > '\0');

```
Or since you seem to be developing in C++, and you have included the STL string header file, use a string object to hold the results:
```

std::string host_name = buf;

```

---

