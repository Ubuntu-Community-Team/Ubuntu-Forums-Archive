---
title: "Segmentation Fault Error"
date: 2009-11-24
forum: Programming Talk
---

### Post by Smackin9 on 2009-11-24
Hello Gents,

Just stumbled upon this community and after reading a few posts, I find it very open and helpful. I am working on a project right now, and I was wondering if I could get assistance on it. It is for school (I read the FAQ regarding this), but I have it 99% finished. The only problem now is getting one bit of command line option handling to work properly. I will paste my code below and then describe a bit about the code and error.

 p, li { white-space: pre-wrap; }  ```

#include <QApplication>
 #include <QtGui>
 #include <stdio.h>
 #include <stdlib.h>
 #include <unistd.h>
 #include <limits.h>
 #include <fstream>
 #include <cctype>
 #include <ctype.h>
 #include "radar.h"
 #include "math.h"
 

#define MAX_BUF 256
 #define MAX_NAME 15
 #define MAX_SYMBOL 3
 #define STR_SIZE 256
 #define MAX_ID 6
 

float tStart;
 int tDisplay;
 float timescale=1;
 

int main(int argc, char *argv[])
 {
     QApplication app(argc, argv);           // create application object
     QWidget *window = new QWidget;          // create a window to hold all sub windows
     window->resize(600, 600);               // set its size
     window->setWindowTitle("ATC Simulator");// and window title
 

    int c=0;
     extern char *optarg;
     char *filename = "test_flight.txt"; /* file to be opened */
     bool filespec=false, startspec=false, stepspec=false, scalespec=false; /*Vars to determine if command line option or default value should be used */ 
 

    while ((c=getopt(argc,argv,"f:t:s:x")) !=EOF)
     {
         switch (c)
         {
             case 'f':
             {
                 filename=optarg;
                 filespec=true;      break;
             }
 

            case 't':
             {
                 tStart=atof(optarg);
                 startspec=true;     break;
             }
 

            case 'x':
             {
                 timescale=atof(optarg); ;/*ERROR */
                 scalespec=true;    break;
             }
 

            case 's':
             {
                 tDisplay=atof(optarg)
                 stepspec=true;      break;
             }
}

```The code obviously goes on after that, but I believe this is where my error lies. It seems to handle everything but case x fine. When I'm debugging, the debugger will not move past the /*ERROR*/ line. When I make the program and run it, it runs properly unless I pass it the -x command. I think I've included all relevant info but if there is something I can clarify more I would be happy to. Thanks for your help!


Thanks,

Smackin9


PS
I know I may be using a mix of c and c++ but the teacher set some stuff up for us in c, and said we could use either c or c++.

---

### Post by dwhitney67 on 2009-11-24
'x' marks the spot; it appears the with the -x option, you are looking for a value (optarg), yet you did not specify that this option required such.

Perhaps you intended this:
```

while ((c=getopt(argc,argv,"f:t:s:x**:**")) !=EOF)
 {
    ...
 }

```
Note the colon (':') character after the 'x'.

---

### Post by Smackin9 on 2009-11-24
Aha, it's always the little things isn't it? Thanks so much for your help I was staring at that for hours missing the obvious.

---

