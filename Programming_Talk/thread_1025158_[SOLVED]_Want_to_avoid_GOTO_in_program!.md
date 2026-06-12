---
title: "[SOLVED] Want to avoid GOTO in program!"
date: 2008-12-29
forum: Programming Talk
---

### Post by Krupski on 2008-12-29
Hi all,

I have a small program which converts encoded ASCII strings into coordinates for lines (i.e. raster line graphics).

I originally wrote the program in GWBASIC and now I just finished "porting" it to C (plain old ANSI C - nothing fancy).

Unfortunately, the program has several GOTO statements in it. I would love to get rid of them and do it the "right" way, but I'm stumped as to how to do it.

Any C programming gurus out there care to take a peek at this?

The GOTO statements I want to get rid of are highlighted in red.

Thanks! I'll greatly appreciate it!

(btw don't laugh at the code... it's still in the "writing" stage - nowhere near complete).

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

char buffer[BUFSIZ];
FILE *infile;
int len, lpos, rpos, width, vertices, n, x, y, x0, y0, x1, y1, flag, c;

void line(int x0, int y0, int x1, int y1);

int main(int argc, char *argv[]) // gonna use argv later
{
    (c = 32);

    infile = fopen("rowmans.jhf", "r");

    if(infile == NULL) { fprintf(stderr, "Can't open file!\n");
        fflush(stderr);
        return(-1);
    }

    while(feof(infile) == 0) {

        fgets(buffer, (BUFSIZ-1), infile);
        len = strlen(buffer);

        lpos = (buffer[8] - 'R'); // left position
        rpos = (buffer[9] - 'R'); // right position
        width = (rpos - lpos); // character width
        vertices = (len - 11); // number of vertices

        (n = 0); (flag = 0);

        fprintf(stdout, ";;;;;;;;;;;;;;;;;;;;;;\n");
        fprintf(stdout, ";; character 0x%2x\n", c );
        fprintf(stdout, ";;;;;;;;;;;;;;;;;;;;;;\n");
        fprintf(stdout, "c%2x", c); (c++);
        fprintf(stdout, "\tdc.b\t%2d,%2d\n", width, 0);
        fflush(stdout);

        while(n < vertices) {

            x = (buffer[10+n+0] - 'R');
            y = (buffer[10+n+1] - 'R');

            if((x == -50) && (y == 0)) { // pen up
                (flag = 1);
                [COLOR="Red"]**goto outer;**[/COLOR]
            }

            (x -= lpos);
            (y = (16 - y));

            (x1 = x); (y1 = y);

            if(flag == 1) {
                (flag = 0);
                [COLOR="Red"]**goto inner;**[/COLOR]
            }

            if(n > 1) {
                line(x0, y0, x1, y1);
            }

            [COLOR="Red"]**inner:**[/COLOR]
                (x0 = x); (y0 = y);
            [COLOR="Red"]**outer:**[/COLOR]
                (n += 2);
        }

    fprintf(stdout, "\tdc.b\t-1,-1\n\n");
    fflush(stdout);

    if(c == 127) { [COLOR="Red"]**goto exit;**[/COLOR] }

    }

    [COLOR="Red"]**exit:**[/COLOR]
        fclose(infile);
        return(0);
}

[COLOR="Blue"]**// nothing to worry about below this line**[/COLOR]

void line(int x0, int y0, int x1, int y1)
{
    int st, deltax, deltay, x, xstep, y, ystep, error;

    st = (abs(y1 - y0) > abs(x1 - x0));

    if (st) {
        x0^=y0; y0^=x0; x0^=y0;
        x1^=y1; y1^=x1; x1^=y1;
    }

    deltax = (x1 - x0);
    deltay = abs(y1 - y0);
    error  = abs(deltax / 2);
    y = y0;

    if (x0 > x1) { xstep = -1; }
    else         { xstep =  1; }

    (deltax *= xstep);

    if (y0 > y1) { ystep = -1; }
    else         { ystep =  1; }

    for ((x = x0); (x != (x1 + xstep)); (x += xstep))
    {
        if (st) { fprintf(stdout, "\tdc.b\t%2d,%2d\n", y, x); }
        else    { fprintf(stdout, "\tdc.b\t%2d,%2d\n", x, y); }

        fflush(stdout);

        (error -= deltay);

        if (error < 0) {
            (y += ystep);
            (error += deltax);
        }
    }
}

```

---

### Post by kjohansen on 2008-12-29
for the go to exit you can use a break.

for the other two you could use a boolean flag to know if you should go to inner or outer

---

### Post by Krupski on 2008-12-29
> **kjohansen said:**
> for the go to exit you can use a break.

for the other two you could use a boolean flag to know if you should go to inner or outer

I was hoping for a more "elegant" solution using break or if-else or something. 

Setting control flags seems clumsier than the GOTO statements themselves... :confused:

I do see the last one though... must have been tired. Break is obvious there!  :D

-- Roger

---

### Post by SledgeHammer_999 on 2008-12-29
I am no coding guru but here is what I came up with. Note: the "break" after the "return(0)" maybe isn't needed.
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

char buffer[BUFSIZ];
FILE *infile;
int len, lpos, rpos, width, vertices, n, x, y, x0, y0, x1, y1, flag, c;

void line(int x0, int y0, int x1, int y1);

int main(int argc, char *argv[]) // gonna use argv later
{
    (c = 32);

    infile = fopen("rowmans.jhf", "r");

    if(infile == NULL) { fprintf(stderr, "Can't open file!\n");
        fflush(stderr);
        return(-1);
    }

    while(feof(infile) == 0) {

        fgets(buffer, (BUFSIZ-1), infile);
        len = strlen(buffer);

        lpos = (buffer[8] - 'R'); // left position
        rpos = (buffer[9] - 'R'); // right position
        width = (rpos - lpos); // character width
        vertices = (len - 11); // number of vertices

        (n = 0); (flag = 0);

        fprintf(stdout, ";;;;;;;;;;;;;;;;;;;;;;\n");
        fprintf(stdout, ";; character 0x%2x\n", c );
        fprintf(stdout, ";;;;;;;;;;;;;;;;;;;;;;\n");
        fprintf(stdout, "c%2x", c); (c++);
        fprintf(stdout, "\tdc.b\t%2d,%2d\n", width, 0);
        fflush(stdout);

        while(n < vertices) {

            x = (buffer[10+n+0] - 'R');
            y = (buffer[10+n+1] - 'R');

            if((x == -50) && (y == 0)) { // pen up
                (flag = 1);
                [COLOR="Red"]**(n += 2);**[/COLOR]
            }
            else{
                 (x -= lpos);
                 (y = (16 - y));

                 (x1 = x); (y1 = y);

                 if(flag == 1) {
                     (flag = 0);
                     [COLOR="Red"]**(x0 = x); (y0 = y);**[/COLOR]
                 }
                 else{
                      if(n > 1) {
                          line(x0, y0, x1, y1);
                      }
                 }
            }                 
        }

    fprintf(stdout, "\tdc.b\t-1,-1\n\n");
    fflush(stdout);

    if(c == 127) { 
        [COLOR="Red"][B]fclose(infile);
        return(0);
        break;[/B][/COLOR]//maybe this isn't needed
    }

    }

    
        
}

[COLOR="Blue"]**// nothing to worry about below this line**[/COLOR]

void line(int x0, int y0, int x1, int y1)
{
    int st, deltax, deltay, x, xstep, y, ystep, error;

    st = (abs(y1 - y0) > abs(x1 - x0));

    if (st) {
        x0^=y0; y0^=x0; x0^=y0;
        x1^=y1; y1^=x1; x1^=y1;
    }

    deltax = (x1 - x0);
    deltay = abs(y1 - y0);
    error  = abs(deltax / 2);
    y = y0;

    if (x0 > x1) { xstep = -1; }
    else         { xstep =  1; }

    (deltax *= xstep);

    if (y0 > y1) { ystep = -1; }
    else         { ystep =  1; }

    for ((x = x0); (x != (x1 + xstep)); (x += xstep))
    {
        if (st) { fprintf(stdout, "\tdc.b\t%2d,%2d\n", y, x); }
        else    { fprintf(stdout, "\tdc.b\t%2d,%2d\n", x, y); }

        fflush(stdout);

        (error -= deltay);

        if (error < 0) {
            (y += ystep);
            (error += deltax);
        }
    }
}

```

---

### Post by fiddler616 on 2008-12-29
C isn't my forte, but I second (third?) the use of break. Try continue too. 
If all else fails, you can always get a bit sloppy with while statements--starting one where your label should be, and ending them where the goto should be, using a break to hold it all together. That's far from ideal though, we just had a discussion about this [here]("http://ubuntuforums.org/showthread.php?t=1015450").

---

### Post by Krupski on 2008-12-29
> **SledgeHammer_999 said:**
> I am no coding guru but here is what I came up with. Note: the "break" after the "return(0)" maybe isn't needed.


I just pasted it into my compiler. It's getting stuck somewhere... I'm going to have to single step through it to see why.

I see what you're getting at though and I think it's on the right track.

Thanks!

-- Roger

---

### Post by Krupski on 2008-12-29
> **SledgeHammer_999 said:**
> I am no coding guru but here is what I came up with. Note: the "break" after the "return(0)" maybe isn't needed.


OK found it! Due to re-arranging the loops, the variable "n" wasn't getting incremented all the time.

Here's the code that works (addition shown in blue):

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

char buffer[BUFSIZ];
FILE *infile;
int len, lpos, rpos, width, vertices, n, x, y, x0, y0, x1, y1, flag, c;

void line(int x0, int y0, int x1, int y1);

int main(int argc, char *argv[]) // gonna use argv later
{
    (c = 32);

    infile = fopen("rowmans.jhf", "r");

    if(infile == NULL) { fprintf(stderr, "Can't open file!\n");
        fflush(stderr);
        return(-1);
    }

    while(feof(infile) == 0) {

        fgets(buffer, (BUFSIZ-1), infile);
        len = strlen(buffer);

        lpos = (buffer[8] - 'R'); // left position
        rpos = (buffer[9] - 'R'); // right position
        width = (rpos - lpos); // character width
        vertices = (len - 11); // number of vertices

        (n = 0); (flag = 0);

        fprintf(stdout, ";;;;;;;;;;;;;;;;;;;;;;\n");
        fprintf(stdout, ";; character 0x%2x\n", c );
        fprintf(stdout, ";;;;;;;;;;;;;;;;;;;;;;\n");
        fprintf(stdout, "c%2x", c); (c++);
        fprintf(stdout, "\tdc.b\t%2d,%2d\n", width, 0);
        fflush(stdout);

        while(n < vertices) {

            x = (buffer[10+n+0] - 'R');
            y = (buffer[10+n+1] - 'R');

            if((x == -50) && (y == 0)) { // pen up
                (flag = 1);
                [COLOR="Red"]**(n += 2);**[/COLOR]
            }
            else{
                 (x -= lpos);
                 (y = (16 - y));

                 (x1 = x); (y1 = y);

                 if(flag == 1) {
                     (flag = 0);
                     [COLOR="Red"]**(x0 = x); (y0 = y);**[/COLOR]
                 }
                 else{
                      if(n > 1) {
                          line(x0, y0, x1, y1);
                      }
                 }
                 [SIZE="4"][COLOR="Blue"]**(n += 2);**[/COLOR][/SIZE]
            }                 
        }

    fprintf(stdout, "\tdc.b\t-1,-1\n\n");
    fflush(stdout);

    if(c == 127) { 
        [COLOR="Red"][B]fclose(infile);
        return(0);
        break;[/B][/COLOR]//maybe this isn't needed
    }

    }

    
        
}

[COLOR="Blue"]**// nothing to worry about below this line**[/COLOR]

void line(int x0, int y0, int x1, int y1)
{
    int st, deltax, deltay, x, xstep, y, ystep, error;

    st = (abs(y1 - y0) > abs(x1 - x0));

    if (st) {
        x0^=y0; y0^=x0; x0^=y0;
        x1^=y1; y1^=x1; x1^=y1;
    }

    deltax = (x1 - x0);
    deltay = abs(y1 - y0);
    error  = abs(deltax / 2);
    y = y0;

    if (x0 > x1) { xstep = -1; }
    else         { xstep =  1; }

    (deltax *= xstep);

    if (y0 > y1) { ystep = -1; }
    else         { ystep =  1; }

    for ((x = x0); (x != (x1 + xstep)); (x += xstep))
    {
        if (st) { fprintf(stdout, "\tdc.b\t%2d,%2d\n", y, x); }
        else    { fprintf(stdout, "\tdc.b\t%2d,%2d\n", x, y); }

        fflush(stdout);

        (error -= deltay);

        if (error < 0) {
            (y += ystep);
            (error += deltax);
        }
    }
}

```


Thanks so much... I feel a lot better now without those "goto" statements!  :D

-- Roger

---

### Post by Cracauer on 2008-12-30
I think that C's goto is fine in two situations:

1) break out of inner loops in nested loops, a strict use like "break <tagname>;" like other languages have but C doesn't :)

2) jump to the end of a function where cleanup such as memory deallocation is done.  I like this better than the usual copy-n-paste of the cleanup statements and use "return". In C++ you obviously don't need this.

Note that both are strict forward-use.

And hey, it's still better than "come-from" :)

---

### Post by dwhitney67 on 2008-12-30
@OP

In your final solution, you have the statement "n += 2" in the if-block and the else-block.  This statement is needed regardless of the condition necessary to enter the if-block, so therefore why not just place the "n += 2" after the else-block.

When c is 127, just break from the outer while loop.  See code in blue below.

Btw, you should move the global declarations you have into the main-function.  There is no practical reason to have them declared where they currently are.

```

while(feof(infile) == 0) {
  ...
  while (n < vertices) {
    ...
    if((x == -50) && (y == 0)) { // pen up
      ...
    }
    else {
      ...
    }
    [COLOR="Blue"]n += 2;[/COLOR]
  }
  ...
  if (c == 127) {
    fclose(infile);
    [COLOR="Blue"]break;              // break out of while (feof(infile) == 0) loop[/COLOR]
  }
}
...

```

---

### Post by Krupski on 2008-12-31
> **dwhitney67 said:**
> @OP

In your final solution, you have the statement "n += 2" in the if-block and the else-block.  This statement is needed regardless of the condition necessary to enter the if-block, so therefore why not just place the "n += 2" after the else-block.

When c is 127, just break from the outer while loop.  See code in blue below.

Btw, you should move the global declarations you have into the main-function.  There is no practical reason to have them declared where they currently are.



Thanks! I found that out after going over the code. Here is the final version which I think is 100% ok. I also moved the data declarations as you suggested. Tell me what you think.

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

void line(int x0, int y0, int x1, int y1);

int main(int argc, char *argv[])
{
    char buffer[BUFSIZ];
    FILE *infile;
    int len, lpos, rpos, width, vertices, n, x, y, x0, y0, x1, y1, flag, c;

    infile = fopen(argv[1], "r");

    if(infile == NULL) { fprintf(stderr, "Can't open file!\n");
        fflush(stderr);
        return(-1);
    }

	(c = 32); // first char is a space

    while(feof(infile) == 0) {

        fgets(buffer, (BUFSIZ), infile);
        len = strlen(buffer);

        lpos = (buffer[8] - 'R'); // left position
        rpos = (buffer[9] - 'R'); // right position
        width = (rpos - lpos);    // character width
        vertices = (len - 11);    // number of vertices

        (n = 0); (flag = 0);

        fprintf(stdout, ";;;;;;;;;;;;;;;;;;;;;;\n");
        fprintf(stdout, ";; character 0x%02x\n", c );
        fprintf(stdout, ";;;;;;;;;;;;;;;;;;;;;;\n");
        fprintf(stdout, "c%02x", c); (c++);
        fprintf(stdout, "\tdc.b\t%2d,%2d\n", width, 0);
        fflush(stdout);

        while(n < vertices) {

            x = (buffer[10+n+0] - 'R');
            y = (buffer[10+n+1] - 'R');

            if((x == -50) && (y == 0)) { // pen up
                (flag = 1);
//                fprintf(stdout, "Pen Up\n"); // debug
//                fflush(stdout);
            }
            else {
                (x -= lpos); // don't go past left edge
                (y = (16 - y)); // invert for y=positive

                (x1 = x); (y1 = y);

                if(flag == 1) {
                    (flag = 0);
                }
                else {
                    if(n > 1) {
//                        fprintf(stdout, "X0=%02d, Y0=%02d, X1=%02d, Y1=%02d\n", x0, y0, x1, y1); // debug
//                        fflush(stdout);
                        line(x0, y0, x1, y1);
                    }
                }
            }
            (x0 = x); (y0 = y);
			(n += 2);
        }

        fprintf(stdout, "\tdc.b\t-1,-1\n\n");
        fflush(stdout);

        if(c == 127) { // for oversize file
            fclose(infile);
            return(0);
        }
    }
    fclose(infile);
    return(0);
}


void line(int x0, int y0, int x1, int y1)
{
    int st, deltax, deltay, x, xstep, y, ystep, error;

    st = (abs(y1 - y0) > abs(x1 - x0));

    if (st) {
        x0^=y0; y0^=x0; x0^=y0; // swap(x0, y0);
        x1^=y1; y1^=x1; x1^=y1; // swap(x1, y1);
    }

    deltax = abs(x1 - x0);
    deltay = abs(y1 - y0);
    error  = (deltax / 2);
    y = y0;

    if (x0 > x1) { xstep = -1; }
    else         { xstep =  1; }

    if (y0 > y1) { ystep = -1; }
    else         { ystep =  1; }

    for ((x = x0); (x != (x1 + xstep)); (x += xstep))
    {
        if (st) { fprintf(stdout, "\tdc.b\t%2d,%2d\n", y, x); }
        else    { fprintf(stdout, "\tdc.b\t%2d,%2d\n", x, y); }

        fflush(stdout);

        (error -= deltay);

        if (error < 0) {
            (y += ystep);
            (error += deltax);
        }
    }
}

```



Thanks!

-- Roger

---

### Post by dwhitney67 on 2008-12-31
You have duplicate code here:
```

        ...
        if(c == 127) { // for oversize file
            fclose(infile);
            return(0);
        }
    }
    fclose(infile);
    return(0);
}

```
IMO, I think you should remove the fclose() and the return() statements from the if-block, and instead insert a 'break' statement.  The latter will get your application out of the outer while-loop so that the application can tidy up with the fclose() and return() at the end of the main function.

---

### Post by Krupski on 2008-12-31
> **dwhitney67 said:**
> You have duplicate code here:
```

        ...
        if(c == 127) { // for oversize file
            fclose(infile);
            return(0);
        }
    }
    fclose(infile);
    return(0);
}

```
IMO, I think you should remove the fclose() and the return() statements from the if-block, and instead insert a 'break' statement.  The latter will get your application out of the outer while-loop so that the application can tidy up with the fclose() and return() at the end of the main function.

Yeah you're right. It's a left-over from my "translation" from GWBASIC to C.

This was a quicky filter program meant to be used one-shot and that's it... so I didn't care much about completely proper C style. I DO, however, despise the GOTO statement which is why I wanted to get rid of them... and file away the info for future programs.

Thanks again for all your help!

-- Roger

---

