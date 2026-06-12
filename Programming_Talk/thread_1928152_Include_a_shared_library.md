---
title: "Include a shared library"
date: 2012-02-19
forum: Programming Talk
---

### Post by Pierrick584 on 2012-02-19
Greetings, i am trying to compile an example program for raknet with a shared library, the code work well when the source is included, but i would kinda prefer using the shared library, beacause the sources include ALOT of file, so its dirty... also, it is to test if the shared library actualy work since i compiled it myself.

I must say, i NEVER programmed by including a binary library before, so i might be extremely wrong, but couldnt find anything  on google... anyway here is the code.

```

#include <stdio.h>
#include "libraknet.so"

#define MAX_CLIENTS 10
#define SERVER_PORT 60000
using namespace RakNet;
int main(void)
{
    char str[512];
    RakNet::RakPeerInterface *peer = RakNet::RakPeerInterface::GetInstance();
    bool isServer;

    printf("(C) or (S)erver?\n");
    gets(str);
    if ((str[0]=='c')||(str[0]=='C'))
    {
        SocketDescriptor sd;
        peer->Startup(1,&sd, 1);
        isServer = false;
    } else {
        SocketDescriptor sd(SERVER_PORT,0);
        peer->Startup(MAX_CLIENTS, &sd, 1);
        isServer = true;
    }


    // TODO - Add code body here

    RakNet::RakPeerInterface::DestroyInstance(peer);

    return 0;
}


```



And here is everyone's nightmare.... the compiling errors...

```

-------------- Build: Debug in testrak ---------------

Compiling: main.cpp
In file included from /home/pierrick/programming/testrak/main.cpp:3:0:
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\177’ in program
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\2’ in program
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\1’ in program
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\1’ in program
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\3’ in program
/home/pierrick/programming/testrak/libraknet.so:1:9: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\3’ in program
/home/pierrick/programming/testrak/libraknet.so:1:18: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:20: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\1’ in program
/home/pierrick/programming/testrak/libraknet.so:1:22: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\360’ in program
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\5’ in program
/home/pierrick/programming/testrak/libraknet.so:1:28: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘@’ in program
/home/pierrick/programming/testrak/libraknet.so:1:34: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\240’ in program
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\227’ in program
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\21’ in program
/home/pierrick/programming/testrak/libraknet.so:1:44: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘@’ in program
/home/pierrick/programming/testrak/libraknet.so:1:54: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:56: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\7’ in program
/home/pierrick/programming/testrak/libraknet.so:1:58: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘@’ in program
/home/pierrick/programming/testrak/libraknet.so:1:60: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\35’ in program
/home/pierrick/programming/testrak/libraknet.so:1:62: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\34’ in program
/home/pierrick/programming/testrak/libraknet.so:1:64: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\1’ in program
/home/pierrick/programming/testrak/libraknet.so:1:66: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\5’ in program
/home/pierrick/programming/testrak/libraknet.so:1:70: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\241’ in program
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\21’ in program
/home/pierrick/programming/testrak/libraknet.so:1:100: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\241’ in program
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\21’ in program
/home/pierrick/programming/testrak/libraknet.so:1:108: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\1’ in program
/home/pierrick/programming/testrak/libraknet.so:1:122: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\6’ in program
/home/pierrick/programming/testrak/libraknet.so:1:126: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\330’ in program
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\21’ in program
/home/pierrick/programming/testrak/libraknet.so:1:132: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\330’ in program
/home/pierrick/programming/testrak/libraknet.so:1:140: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\330’ in program
/home/pierrick/programming/testrak/libraknet.so:1:148: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\230’ in program
/home/pierrick/programming/testrak/libraknet.so:1:155: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\230’ in program
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\1’ in program
/home/pierrick/programming/testrak/libraknet.so:1:164: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\2’ in program
/home/pierrick/programming/testrak/libraknet.so:1:178: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\6’ in program
/home/pierrick/programming/testrak/libraknet.so:1:182: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\21’ in program
/home/pierrick/programming/testrak/libraknet.so:1:188: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:196: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:204: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\320’ in program
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\1’ in program
/home/pierrick/programming/testrak/libraknet.so:1:211: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\320’ in program
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\1’ in program
/home/pierrick/programming/testrak/libraknet.so:1:219: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\10’ in program
/home/pierrick/programming/testrak/libraknet.so:1:226: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\4’ in program
/home/pierrick/programming/testrak/libraknet.so:1:234: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\4’ in program
/home/pierrick/programming/testrak/libraknet.so:1:238: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\310’ in program
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\1’ in program
/home/pierrick/programming/testrak/libraknet.so:1:243: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\310’ in program
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\1’ in program
/home/pierrick/programming/testrak/libraknet.so:1:251: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\310’ in program
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\1’ in program
/home/pierrick/programming/testrak/libraknet.so:1:259: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:266: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:274: warning: null character(s) ignored [enabled by default]
/home/pierrick/programming/testrak/libraknet.so:1:1: error: stray ‘\4’ in program

```



Working under codeblock and ubuntu 11.10 by the way

---

### Post by gardnan on 2012-02-19
There are two main problems that I can see with your code.

1: You are 'including' the binary file. The #include directive is meant  for including header files (.h files), which contain C or C++  definitions of functions and data types. The include directive basically  works by taking the file specified and sticking it at the top of the  file. In this case, you are including a binary file, not C code, which  is why the compiler is reporting a bunch of random stray characters. If  you want to link to the library, the proper way is to include the  corresponding header file, and then link the library like this gcc -o  executable ... -l*libraryname. *This will cause the linker to link the library in the linking stage.

2: The RakNet Library you are using appears to be written in C++, not C. However, most of your code is in C, eg, printf, gets (don't use gets, but that is another topic), etc. This makes me think that the compiler may be getting confused. I know that gcc is supposed to compile correctly based on the filetype, but somehow this has never worked for me for C++. I would recommend trying to compile with g++, and changing the program so that it is written more in C++ rather than C.

---

### Post by Pierrick584 on 2012-02-19
> **gardnan said:**
> 
2: The RakNet Library you are using appears to be written in C++, not C. However, most of your code is in C, eg, printf, gets (don't use gets, but that is another topic), etc. This makes me think that the compiler may be getting confused. I know that gcc is supposed to compile correctly based on the filetype, but somehow this has never worked for me for C++. I would recommend trying to compile with g++, and changing the program so that it is written more in C++ rather than C.


Thanks alot for the clarification on how to use a dynamic lib, i started to read on google a few things with gave me much worse solution.... 

About my code, it is actualy raknet's tutorial's sample, and it works 100% fine with the source include (i changed the raknet include to a binary include, thats it).


Now though, i tried to add the library to the codeblock's project links, give me errors, does not recognise the library it seems...

```
/home/pierrick/programming/testrak/main.cpp|6|error: ‘RakNet’ is not a namespace-name|
/home/pierrick/programming/testrak/main.cpp|6|error: expected namespace-name before ‘;’ token|
/home/pierrick/programming/testrak/main.cpp||In function ‘int main()’:|
/home/pierrick/programming/testrak/main.cpp|10|error: ‘RakNet’ has not been declared|
/home/pierrick/programming/testrak/main.cpp|10|error: ‘peer’ was not declared in this scope|
/home/pierrick/programming/testrak/main.cpp|10|error: ‘RakNet’ has not been declared|
/home/pierrick/programming/testrak/main.cpp|17|error: ‘SocketDescriptor’ was not declared in this scope|
/home/pierrick/programming/testrak/main.cpp|17|error: expected ‘;’ before ‘sd’|
/home/pierrick/programming/testrak/main.cpp|18|error: ‘sd’ was not declared in this scope|
/home/pierrick/programming/testrak/main.cpp|21|error: ‘SocketDescriptor’ was not declared in this scope|
/home/pierrick/programming/testrak/main.cpp|21|error: expected ‘;’ before ‘sd’|
/home/pierrick/programming/testrak/main.cpp|22|error: ‘sd’ was not declared in this scope|
/home/pierrick/programming/testrak/main.cpp|29|error: ‘RakNet’ has not been declared|
||=== Build finished: 12 errors, 0 warnings ===|

```


Sincerely, thanks for your help, i'm struggleing at making raknet work since a few weeks, and trying to find a suitable network library to program with on linux since years (last time i actualy did some programming with result was like 5 years ago on windows with winsock, when i switched to linux, never made it to get a working networking library :( )

---

### Post by gardnan on 2012-02-20
Sorry for the delay.
Well, comparing your code and that of the tutorial, it appears like your code should work.

Please post your revised #include line so that we can verify that it is correct.

I would say to post your compilation line so that we can check that too, but since you are using Code::Blocks I don't really know how to ensure that you are linking the program correctly.

---

### Post by Pierrick584 on 2012-02-20
I tried to compile it directly with gcc, just so we can realy see whats wrong. here are my few try, the library file is named libraknet.so by the way

```
gcc main.cpp -lraknet -o rak

``````
gcc main.cpp -llibraknet.so -o rak

``````
gcc main.cpp -l libraknet.so -o rak
```here the output, same for every different attempt i've made

```
main.cpp: In function &#8216;int main()&#8217;:
main.cpp:10:2: error: &#8216;RakNet&#8217; has not been declared
main.cpp:10:28: error: &#8216;peer&#8217; was not declared in this scope
main.cpp:10:35: error: &#8216;RakNet&#8217; has not been declared
main.cpp:17:3: error: &#8216;SocketDescriptor&#8217; was not declared in this scope
main.cpp:17:20: error: expected &#8216;;&#8217; before &#8216;sd&#8217;
main.cpp:18:20: error: &#8216;sd&#8217; was not declared in this scope
main.cpp:21:3: error: &#8216;SocketDescriptor&#8217; was not declared in this scope
main.cpp:21:20: error: expected &#8216;;&#8217; before &#8216;sd&#8217;
main.cpp:22:31: error: &#8216;sd&#8217; was not declared in this scope
main.cpp:29:2: error: &#8216;RakNet&#8217; has not been declared

```
and finaly, here is the exact code of main.cpp

```
#include <stdio.h>

#define MAX_CLIENTS 10
#define SERVER_PORT 60000

int main(void)
{
        char str[512];
        RakNet::RakPeerInterface *peer = RakNet::RakPeerInterface::GetInstance();
        bool isServer;

        printf("(C) or (S)erver?\n");
        gets(str);
        if ((str[0]=='c')||(str[0]=='C'))
        {
                SocketDescriptor sd;
                peer->Startup(1,&sd, 1);
                isServer = false;
        } else {
                SocketDescriptor sd(SERVER_PORT,0);
                peer->Startup(MAX_CLIENTS, &sd, 1);
                isServer = true;
        }


        // TODO - Add code body here

        RakNet::RakPeerInterface::DestroyInstance(peer);

        return 0;
}


```
the code is a plain copy/paste of [http://www.raknet.com/raknet/manual/tutorialsample1.html](http://www.raknet.com/raknet/manual/tutorialsample1.html)

minus the source include that i removed  (the original source miss a namespace raknet for some reason, but realy, that is not the actual issue considering it doesnt recognise the fully declared functions too)


And if you or anyone else feel like doing in-deep test, i've uploaded my files on a server, here the links
[http://205.234.200.42/libraknet.so](http://205.234.200.42/libraknet.so)
[http://205.234.200.42/main.cpp](http://205.234.200.42/main.cpp)
[http://205.234.200.42/testrak.cbp](http://205.234.200.42/testrak.cbp)

here is the project i used to make the .so
[http://205.234.200.42/raknetlib.cbp](http://205.234.200.42/raknetlib.cbp)
(just need to add the source folder of raknet)

---

### Post by gardnan on 2012-02-20
It does not appear that you are including the header file associated with the library. So, the way that linked libraries usually work is through two components, the header file (.h file), and the object file, the .so file in this case. In order to use the library, you want to 'include' the header file to declare all of the functions, namespaces, objects, and whatever, and then you want to link to the library using the -l compiler option. When I said that #include"libraknet.so" was wrong, I meant that you should be including the header file instead. So, according the the RakNet tutorial, I believe you should have a header file called "RaknetPeerInterface.h" that you need to include in order to get the definitions of the objects contained in the library. [FONT=Geneva, Verdana, Arial, Helvetica, sans-serif][SIZE=1][COLOR=#111122]
[/COLOR][/SIZE][/FONT]

---

### Post by Pierrick584 on 2012-02-20
Ohh... i see! Ill try that when i get home, thanks alot :D

---

