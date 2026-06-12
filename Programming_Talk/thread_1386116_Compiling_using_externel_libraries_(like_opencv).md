---
title: "Compiling using externel libraries (like opencv)"
date: 2010-01-20
forum: Programming Talk
---

### Post by 7raTEYdCql on 2010-01-20
I am trying to compile a simple opencv code. Am facing some difficulty compiling the code, and think that the external opencv libraries aren't getting loaded.

This is my opencv code.
```

#include “highgui.h”

int main(int argc, char* argv[])
{
    IplImage* img = cvLoadImage( argv[1] );
    cvNamedWindow( “Example1”, CV_WINDOW_AUTOSIZE );
    cvShowImage( “Example1”, img );
    cvWaitKey(0);
    cvReleaseImage( &img );
    cvDestroyWindow( “Example1” );
}


```

Compiling using the standard gcc filename.c gives the following error
> 
8@timon:~/Documents/examples$ gcc openpic.c
openpic.c:1:10: error: #include expects "FILENAME" or <FILENAME>
openpic.c: In function ‘main’:
openpic.c:5: error: ‘IplImage’ undeclared (first use in this function)
openpic.c:5: error: (Each undeclared identifier is reported only once
openpic.c:5: error: for each function it appears in.)
openpic.c:5: error: ‘img’ undeclared (first use in this function)
openpic.c:6: error: stray ‘\342’ in program
openpic.c:6: error: stray ‘\200’ in program
openpic.c:6: error: stray ‘\234’ in program
openpic.c:6: error: stray ‘\342’ in program
openpic.c:6: error: stray ‘\200’ in program
openpic.c:6: error: stray ‘\235’ in program
openpic.c:6: error: ‘Example1’ undeclared (first use in this function)
openpic.c:6: error: ‘CV_WINDOW_AUTOSIZE’ undeclared (first use in this function)
openpic.c:7: error: stray ‘\342’ in program
openpic.c:7: error: stray ‘\200’ in program
openpic.c:7: error: stray ‘\234’ in program
openpic.c:7: error: stray ‘\342’ in program
openpic.c:7: error: stray ‘\200’ in program
openpic.c:7: error: stray ‘\235’ in program
openpic.c:10: error: stray ‘\342’ in program
openpic.c:10: error: stray ‘\200’ in program
openpic.c:10: error: stray ‘\234’ in program
openpic.c:10: error: stray ‘\342’ in program
openpic.c:10: error: stray ‘\200’ in program
openpic.c:10: error: stray ‘\235’ in program
9@timon:~/Documents/examples$ 



I checked the build-all.sh script that comes with the opencv examples. Here was the line which compiles all the c codes, within the present directory.
```

gcc -ggdb `pkg-config --cflags opencv` -o `basename $i .c` $i `pkg-config --libs opencv`;

```

So i think, the only problem is with the inclusion of the external opencv libraries. Can someone please help.

---

### Post by dwhitney67 on 2010-01-20
The double-quote characters in your code are not standard.  Replace them.

For ease in viewing your code, edit it using an editor that provides color-highlighting of the syntax.  The issue with the quotes should become quite apparent (well, at least it did on my system).

P.S.  I used vim as my editor.

---

### Post by 7raTEYdCql on 2010-01-20
I've replaced the "" with <>, and there is still no difference in the output. The examples in the opencv code also include header files in the same manner.

From the error log, and the example code compilation command, i think it is something to do with the compilation command i'm executing i.e. gcc filename.c. There should be some more options which declare the use of the opencv library, how is that done??

---

### Post by dwhitney67 on 2010-01-21
My previous post was not very clear.  When I indicated to replace the double-quote characters, I meant with the *proper* double-quote character as available on a typical keyboard.

The ones that are in the file you posted do *not* correspond with the US-keyboard double-quote character that is located just to the left of the <return> key on the keyboard.

Here's the modified code, which if you copy/paste from here, should (hopefully) compile for you.  Although this code *appears* to be the same as yours, it is not:
```

#include "highgui.h"                                    /* changed quotes here */

int main(int argc, char* argv[])
{
    IplImage* img = cvLoadImage( argv[1] );
    cvNamedWindow( "Example1", CV_WINDOW_AUTOSIZE );    /* changed quotes here */
    cvShowImage( "Example1", img );                     /* changed quotes here */
    cvWaitKey(0);
    cvReleaseImage( &img );
    cvDestroyWindow( "Example1" );                      /* changed quotes here */
}

```

Note:  If the code does not compile, please post the exact compiler errors, because it will be for reasons other than you posted earlier.

---

### Post by Some Penguin on 2010-01-21
Read the 'gcc' man page.  Pay attention to '-L'.

---

### Post by dwhitney67 on 2010-01-21
> **Some Penguin said:**
> Read the 'gcc' man page.  Pay attention to '-L'.
I'm going to go out on a limb to assume that the following statement, which was part of the OP's gcc command, covers this:
```

`pkg-config --libs opencv`

```

---

### Post by 7raTEYdCql on 2010-01-22
I changed the quotes in my code, and on running the bash script command on my code, it is working fine. Good thing!!

I compiled the code myself, with the command
```

gcc openpic.c $(pkg-config --cflags --libs opencv)

```

Thanks everyone.

---

