---
title: "Obfuscated code thread"
date: 2007-03-06
forum: Programming Talk
---

### Post by Wybiral on 2007-03-06
OK, obfuscated code is ridiculous and impractical. Obviously it won't fly in a real project.
But... That doesn't mean it isn't fun to write!

Post your obfuscated code here, I'm interested to see what people come up with.

Here's my first post, "Hello world!\n" in C:
```

#include     <stdio.h>
#define A     >>     1
#define B     <<     1
#define C(x)  *(a + x)
#define D(x) C(10 + x)
#define E     >> (1 B)
#define F(x,y) (D(x)y)
int     main()       {
char a[ 14 ]; D(3) = ((D(4) = sizeof (a))E) + 1;
C(0)=D(4)*6-D(4)+D(4)/7;C(1)=C(0)+F(4,B)+F(3,E);
C(2)=C(3) = C(1)+F(4,A);C(4) = C(7)=C(3)+F(4,E);
C(5) = F(4,B) + D(3); C(6) = C(1) + D(4) + D(3);
C(8)=(C(9)=C(2))+ D(3)+F(3,A); D(0)=C(3)-F(3,B);
D(1) = F(4,B) + D(3) + F(3,E); D(2) = D(4)-D(3);
D(3)  =  D(4)  =  0; printf("%s", a); return 0;}

```

I know it's not the best, but it was my first experience with obfuscation.

---

### Post by j_g on 2007-03-06
Please don't.

---

### Post by Wybiral on 2007-03-06
> **j_g said:**
> Please don't.

Why not?

People like doing puzzles/mazes for fun... Why can't code be used for fun?

Like I said...
It's useless in a project, but who are you to tell people not to goof around every now and then?

I enjoy reversing obfuscated code... It's like solving a puzzle.

---

### Post by Lord Illidan on 2007-03-06
Didn't understand anything :confused:

---

### Post by lnostdal on 2007-03-06
a quine:
```

((lambda (x) `(,(reverse x) ',x)) '(`(,(reverse x) ',x) (x) lambda)) 

```
..when evaluated/executed it returns:
```

((lambda (x) `(,(reverse x) ',x)) '(`(,(reverse x) ',x) (x) lambda)) 

```
(yes, it returns itself!)

anyone see what's going on? ;)

---

### Post by DavidBell on 2007-03-07
There was a thread a while back about silly code that #defined out things like class {}; statements and made them look like pascal. In isolation it is silly, but I've actually taken it a bit further and do it for real now. So I have a standard .h with 

```

// Kill Curly

#define IF(A)	if(A) {
#define IF_(A)	if(A)
#define ELSE	} else {
#define ELSEIF(A)	} else if(A) {
#define ENDIF	}

#define FOR(A)	for(A) {
#define FOR_(A)	for(A)
#define NEXT	}
#define EXITFOR	break;

// You can keep going, with do, while, switch, class, struct, etc
//
// and functions

#define FUNCTION(A)	A {
#define ENDFUNCTION	}


```

I've never liked curly braces because I loose count of the *closing* brace too easily, and I find something like the following much easier to read than the curly brace equivalent....

```

FUNCTION (void SubRender_PixelatedNut(bcRevRGB24 *tpImageBegin, bcRevRGB24 *tpWorkBegin))
    // Renders using ArrayPixel Values
    FOR (long imy = mArrayHeightMin; imy <= mArrayHeightMax; imy++)
        FOR (long imy2 = 0; imy2 < mSkip; imy2++)
            FOR (long imx = mArrayWidthMin; imx <= mArrayWidthMax; imx++)
                IF (mArrayPixels[imx][imy].L() > 0)
                    FOR (long imx2 = 0; imx2 < mSkip; imx2++)
                        vIWORKXY(imx * mSkip + imx2, imy * mSkip + imy2) = mArrayPixels[imx][imy];
                    NEXT
                ENDIF
            NEXT
        NEXT
    NEXT
ENDFUNCTION

```

I also found in my editor (MS VS.NET) I can set my own list of keywords so my defines get highlighted like their normal alternatives. All this breaks code folding ... but provided I don't use the FUNCTION define I actually prefer the way it folds automatically (too many levels before).

Diehard C people may cringe but I really prefer this, and it cost nothing because it's taken out by the preprocessor anyway.

DB

---

### Post by Wybiral on 2007-03-07
Actually, sometimes I use this:
```

#define elif else if

```
To be more like python because it's shorter and more organized looking.

Only when I'm prototyping things though...
It would be punishment for anyone else working on your project if you used code like that in a serious C/C++ program.

---

### Post by public_void on 2007-03-07
You should look at [http://www.ioccc.org/main.html](http://www.ioccc.org/main.html), and some of the past entries.

---

### Post by Wybiral on 2007-03-07
> **public_void said:**
> You should look at [http://www.ioccc.org/main.html](http://www.ioccc.org/main.html), and some of the past entries.

I've seen those before, they're pretty amusing IMO.

I have another one to submit, it only works with linux i386 machines.
```

int main[]=
{
   0x72680A6A, 0x6821646C, 0x6F77206F, 0x6C654868,
   0x0004B86C, 0x01BB0000,-0x77000000, 0x000DBAE1,
  -0x7F330000, 0x000001B8, 0x0080CD00
};

```
It actually teaches an interesting lesson... Don't think about functions/variables/objects as anything more than data. Because that's exactly what they are. The labels are just placeholders for their placement in memory.

So, in summation, an array of machine code is just machine code, and it can be executed if you can point to it's location in memory.

Likewise, this will also work:
```

int main()
{
   int code[] = {
      0x72680A6A, 0x6821646C, 0x6F77206F, 0x6C654868,
      0x0004B86C, 0x01BB0000,-0x77000000, 0x000DBAE1,
     -0x7F330000, 0x000001B8, 0x0080CD00
   };

   ((void(*)())code)();
};

```
Just a simple function pointer cast and we can execute that machine code.

BTW, I created the machine code digits by concatenating sets of four bytes of machine code into 4 byte integers.

---

