---
title: "Is it impossible to use _T or _TEXT on gcc compiler?"
date: 2016-02-13
forum: Programming Talk
---

### Post by bshi02 on 2016-02-13
I had tried to compile below source code but compiler([COLOR=black][FONT=monospace]i586-mingw32msvc) [/FONT][/COLOR]said 

||=== Build: Debug in codeblocks (compiler: cross complier) ===|
/home/sh/codeblocks/main.c||In function ‘main’:|
/home/sh/codeblocks/main.c|11|error: ‘_T’ undeclared (first use in this function)|
/home/sh/codeblocks/main.c|11|error: (Each undeclared identifier is reported only once|
/home/sh/codeblocks/main.c|11|error: for each function it appears in.)|
/home/sh/codeblocks/main.c|11|error: expected ‘,’ or ‘;’ before ‘{’ token|
||=== Build failed: 4 error(s), 0 warning(s) (0 minute(s), 0 second(s)) ===|

I even had tried to compile that source code with [Cross Compiling]("http://wiki.codeblocks.org/index.php?title=Cross_Compiling_wxWidgets_Applications_on_Linux") but it [COLOR=#000000][FONT=Arial]didn’[/FONT][/COLOR][COLOR=#2A2A2A][FONT=verdana]t[/FONT][/COLOR][COLOR=#000000][FONT=Arial] [/FONT][/COLOR][COLOR=#2A2A2A][FONT=verdana]work[/FONT][/COLOR][COLOR=#000000][FONT=Arial] [/FONT][/COLOR][COLOR=#2A2A2A][FONT=verdana]out[/FONT][/COLOR][COLOR=#000000][FONT=Arial], [/FONT][/COLOR][COLOR=#2A2A2A][FONT=verdana]either..
Is there any workaround to succeed to compile below source code?[/FONT][/COLOR]


#define UNICODE
#define _UNICODE


#include <stdio.h>
#include <string.h>
#include <tchar.h>
#include <windows.h>


int main()
  {
 TCHAR str[]=_T{"1234567"};
 int size=sizeof(str) ;
 printf("string length:%d\n",size);
 return 0;
}

---

### Post by mfvpcrec on 2016-02-13
I guess that this link help you
[http://stackoverflow.com/questions/28200648/t-not-recognized-porting-tchar-h-from-microsoft-to-gcc](http://stackoverflow.com/questions/28200648/t-not-recognized-porting-tchar-h-from-microsoft-to-gcc)
Bye!

---

### Post by bshi02 on 2016-02-13
I just realized that I mistook to use'{' instead of'(' in front of _T macro..
But Thank you very much for your helpful information Anyway.

---

