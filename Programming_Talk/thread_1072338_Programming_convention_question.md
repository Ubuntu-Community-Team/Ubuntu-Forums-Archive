---
title: "Programming convention question"
date: 2009-02-17
forum: Programming Talk
---

### Post by Krupski on 2009-02-17
Hi all again...

[B][COLOR="Red"](Note: I am not a student and this is not homework)
[/COLOR][/B]

Quick question:

If I have a function that I wrote, and I pass parameters to it, and the function modifies the parameters, should I allow this or should the function make local copies of the parameters?

For example, I have a function:

```

void linedraw(*x0, *y0, *x1, *y1);

```

Which generates all the points of a line between start x0,y0 and end x1,y1.

In the process of working, the "x" and "y" parameters *might* get swapped so that, if I did this:

```

    // show vars before call
    printf("Before: %d, %d, %d, %d\n", x0, y0, x1, y1);

    // call linedraw function
    linedraw(&x0, &y0, &x1, &y1);

    // show vars after call
    printf("After : %d, %d, %d, %d\n", x0, y0, x1, y1);

```

The result might be:

```

Before: 1, 10, 5, 20
After : 10, 1, 20, 5

---or it could be---

Before: 1, 10, 5, 20
After : 1, 10, 5, 20

```

...depending on if the function needed to swap the variables.

Now, once I call "linedraw", I don't need the variables anymore (that is, if they get swapped I don't care). 

But my question is, for GOOD PROGRAMMING PRACTICE, should my function make local copies of the parameters so that the originals don't get swapped, or is it OK to let whatever happens, happen?

Hope this makes sense... and thanks in advance for info.

-- Roger

---

### Post by japju on 2009-02-17
Why do you want to pass the parameters by reference?

---

### Post by Simian Man on 2009-02-17
It is bad practice.  You should make the linedraw function take its arguments by value, not by pointer.

---

### Post by Krupski on 2009-02-17
> **Simian Man said:**
> It is bad practice.  You should make the linedraw function take its arguments by value, not by pointer.

Well, I did that for two reasons:

(1) I (finally) figured out how pointers work and I wanted to see if I could do it right.

(2) My original version of the program did not use pointers and, upon looking at my code (which was working), I couldn't figure out WHY it was working (i.e. how linedraw was getting it's values).

Since I used the variable names "x0, y0, x1, y1" in both the main program and in the function, it seemed that by accident my program was working - only because the var names were the same.

This seemed fundamentally wrong to me... that's what got me thinking I should use pointers to PASS the parameters to the function.

So... here's exactly what I have so far... please tell me if I'm doing it wrong and if so, how and where.

```

////////////////////////////////////////////
// convert.c
// hershey vector font .jhf file
// to m68hc11 source code converter
// last update 17 feb 2009
// not done by any stretch...
////////////////////////////////////////////

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <math.h>


// globally accessible variables

int accx[1000], // x,y accumulators for dupe check
    accy[1000],
    idx, dupe; // for dupe check

// function prototypes

void line(int *x0, int *y0, int *x1, int *y1);
void swap(int *x, int *y);


int main(int argc, char *argv[])
{
    FILE *infile;
    char buffer[BUFSIZ];
    int len, lpos, rpos, width, vertices,
        x, y, x0, y0, x1, y1, c, n, pen;

    infile = fopen(argv[1], "r"); // try to open file

    if(infile == NULL) {
        fprintf(stderr, "Failed to open '%s' for reading\n", argv[1]);
        exit(1);
    }

    c = 0x20; // first char is a space

    while(feof(infile) == 0) {

        // clear out buffer before each read
        for(n = 0; n < sizeof(buffer); n++) {
            buffer[n] = 0;
        }

        fgets(buffer, BUFSIZ, infile); // read a line

        len = strlen(buffer); // length of line

        // adjust len to ignore cr, lf, null at end of line
        while(buffer[len] == 0x0d ||
              buffer[len] == 0x0a ||
              buffer[len] == 0x00) {
            len--;
        }

        if(len > 0) { // skip blank lines

            vertices = -1; // initialize vertex count

            // vertex count is located at buffer[5,6 and 7]
            // as ascii numbers. space is considered zero.
            // for example ' 38' would be 0x20,0x33,0x38 at
            // buffer[5,6 and 7] respectively.

            for(n = 5; n <= 7; n++) { // characters 5,6 and 7
                if(buffer[n] == 0x20) { buffer[n] = '0'; } // transform space to zero
                buffer[n] -= '0'; // normalize ascii to decimal (i.e. 0x30 == 0x00)
                vertices += buffer[n] * pow(10, 7 - n); // add up 100's, 10's and 1's place
            }

            vertices *= 2; // 2 elements per vertex
            lpos = buffer[8] - 'R'; // left position
            rpos = buffer[9] - 'R'; // right position
            width = rpos - lpos; // character width

            if(vertices != len - 9) { // sanity check
                fprintf(stderr, "Vertex count mismatch - file corrupt\n");
                fclose(infile); // probably not necessary ??
                exit(1);
            }

            n = 0; // initialize buffer index
            pen = 1; // flag "pen down"
            idx = 0; // initialize dupe index

            // write character header and source label
            fprintf(stdout, ";;;;;;;;;;;;;;;;;;;;;\n");
            fprintf(stdout, ";; char 0x%02x (%c)\n", c, c);
            fprintf(stdout, ";;;;;;;;;;;;;;;;;;;;;\n");
            fprintf(stdout, "c%02x\tdc.b\t%2d,%2d\n", c, width, 0);

            while(n < vertices) {

                x = buffer[10 + n + 0] - 'R'; // read point coordinates
                y = buffer[10 + n + 1] - 'R';

                if(x == ' '-'R' && y == 'R'-'R') { // "space-R" = "pen up"
                    pen = 0; // flag "pen up"
                } else {

                    x -= lpos; // don't go past left edge
                    y = 16 - y; // invert for y=positive on crt

                    x1 = x; y1 = y; // make copies of x and y

                    if(!pen) { // if pen=up don't output coordinates
                        pen = 1; // then set pen back down
                    } else {
                        if(n > 1) { // skip first coordinate pair (width)
                            **[COLOR="Red"]line(&x0, &y0, &x1, &y1); // call linedraw[/COLOR]**
                        }
                    }
                }
                x0 = x; y0 = y; // copy previous coordinates
                n += 2; // do next line
            }
            fprintf(stdout, "\tdc.b\t-1,-1\n\n"); // write "end of table" (dc.b -1,-1)
            c++; // do next character
        }
    }

    if(c != 96 + 32) { // another sanity check
        fprintf(stderr, "Char count not 96 - output suspect\n");
    }

    fclose(infile); // all done
    exit(0);
}



void line(int *x0, int *y0, int *x1, int *y1)
{
    int x, cx, dx, xs,
        y, cy, dy, ys,
        er, n, st;

//    fprintf(stdout, "\n;line (%d,%d)-(%d,%d)\n", *x0, *y0, *x1, *y1); // debug

    dx = abs(*x0 - *x1); // delta x
    dy = abs(*y0 - *y1); // delta y

    // flag for largest delta
    st = (dx < dy);

    // if dy < dx then swap x/y and dx/dy
    if (st) {
        swap(x0, y0);
        swap(x1, y1);
        swap(&dx, &dy);
    }

    er = dx / 2; // converge check
    y = *y0; // initial y point

    (*x0 < *x1) ? (xs = 1) : (xs = -1); // derive x step
    (*y0 < *y1) ? (ys = 1) : (ys = -1); // derive y step

    for ((x = *x0); (x != (*x1 + xs)); (x += xs))
    {
        cx = x; cy = y; // copy of x, copy of y

        // if x,y were swapped then swap back
        if (st) { swap(&cx, &cy); }

        dupe = 0; // initialize not a dupe

        for (n = 0; n < idx; n++) { // compare to all previous
            if(accx[n] == cx && accy[n] == cy) {
                dupe = 1; // found a dupe, flag it
                break; // no need to check more
            }
        }

        accx[idx] = cx; accy[idx] = cy; // record coordinates
        idx++; // next index

        if(!dupe) { fprintf(stdout, "\tdc.b\t%2d,%2d\n", cx, cy); }
//        else      { fprintf(stdout, ";\tdc.b\t%2d,%2d\t\t;dupe removed\n", cx, cy); } // debug

        er -= dy; // converge to end of line

        if (er < 0) {
            y += ys; er += dx; // increment y, converge error
        }
    }
}


void swap(int *x, int *y)
{
    int t;
    t = *x;
    *x = *y;
    *y = t;
}

```


Any comments appreciated.

-- Roger

---

### Post by Krupski on 2009-02-17
> **japju said:**
> Why do you want to pass the parameters by reference?

I'm not sure... sorry but I'm a relative newbie at C. Trying to learn.

---

### Post by nvteighen on 2009-02-17
It depends on what you're doing, but usually it's better if you can return something instead of "returning" on pointers.

The idea is always to isolate behaivor. What's your function going to do? You say draw a line, so well, make it draw. So, if I use your function without knowing what it does, maybe the function swapped the data internally, but I don't care as long as it does what I told it to do (draw the line).

It seems like you were writing a function that's actually doing two tasks: adjusting coordinate pairs (according to some criteria) and drawing the line. Write two functions respectively and isolate one functionality from the other... otherwise, it won't be clear what does what in your code.

---

### Post by the_unforgiven on 2009-02-17
The thumb-rule is:
o. pass params by value if those are small (read fundamental) data types which can be accomodated on the stack easily AND you don't care about the values in the caller.
o. pass params by reference/pointer if the params are bigger, complex structures - wasting so much of precious stack space is not a good idea. OR, if you want to retrieve multiple *independent* (which are not related logically so that making a struct out of them looks stupid) return values/care about the modifications to the params in the caller. 

The decision about the struct size is a matter of judgement, but generally, anything greater than 8 bytes *shouldn't* be passed on stack (i.e. by value).

HTH ;)

---

### Post by Krupski on 2009-02-17
> **nvteighen said:**
> It depends on what you're doing, but usually it's better if you can return something instead of "returning" on pointers.

The idea is always to isolate behaivor. What's your function going to do? You say draw a line, so well, make it draw. So, if I use your function without knowing what it does, maybe the function swapped the data internally, but I don't care as long as it does what I told it to do (draw the line).

It seems like you were writing a function that's actually doing two tasks: adjusting coordinate pairs (according to some criteria) and drawing the line. Write two functions respectively and isolate one functionality from the other... otherwise, it won't be clear what does what in your code.

Well, my question was whether or not it's "bad" for a function to modify variables when that modification is not wanted or needed externally.

For example, in the code above, swap() *IS* supposed to modify the variables and return them (swapped) :)

But, linedraw takes 4 parameters and *may* modify them internally, but I don't expect it to return anything to me so I don't care. It just "does it's thing" and then returns.

However, what YOU said makes me think... what if someone else used that function and *THEY* expected the 4 parameters to remain untouched?


This is what led me to ask if the function should make private copies of the passed parameters.

Then... I was told by another person that what I was doing was bad programming practice (that is, passing the parameters the way I did).

THAT I didn't expect and now I'm really confused as to the RIGHT way to do what I'm trying to do.

While I'm here... am I using swap() correctly?

Thanks.

-- Roger

---

### Post by Krupski on 2009-02-17
> **the_unforgiven said:**
> The thumb-rule is:
o. pass params by value if those are small (read fundamental) data types which can be accomodated on the stack easily AND you don't care about the values in the caller.
o. pass params by reference/pointer if the params are bigger, complex structures - wasting so much of precious stack space is not a good idea. OR, if you want to retrieve multiple *independent* (which are not related logically so that making a struct out of them looks stupid) return values/care about the modifications to the params in the caller. 

The decision about the struct size is a matter of judgement, but generally, anything greater than 8 bytes *shouldn't* be passed on stack (i.e. by value).

HTH ;)

I don't exactly understand what you mean by "pass by value".

Do you mean have public variables to pass data between main() and the sub-function()?

---

### Post by Tony Flury on 2009-02-17
Pass by value is where the function is declared like this : 

```

void linedraw( int x0, int y0, int x1, int y1) ; 

```

i.e. the parameters are NOT declared as pointers.

if I were to use your linedraw function i would certainly say that swapping the co-ordinate pairs would not be an expected side effect, and i would be suprised at the use of pointers.

---

### Post by Krupski on 2009-02-17
> **Tony Flury said:**
> Pass by value is where the function is declared like this : 

```

void linedraw( int x0, int y0, int x1, int y1) ; 

```

i.e. the parameters are NOT declared as pointers.

if I were to use your linedraw function i would certainly say that swapping the co-ordinate pairs would not be an expected side effect, and i would be suprised at the use of pointers.

That's how I had it before. The more I try to learn, the further behind I seem to get!  :)

Thanks for the info!

-- Roger

---

### Post by the_unforgiven on 2009-02-17
> **Krupski said:**
> I don't exactly understand what you mean by "pass by value".

Do you mean have public variables to pass data between main() and the sub-function()?
Confining our discussion to C, the way params are passed to a function depends on the signature of the function - which comprises of following criteria:
o. no. of arguments
o. types of arguments
o. sequence of arguments

The compiler tries to match each function call with the signature - C being a strongly typed language, the signature MUST match the call; otherwise the compiler signals an error.

So, when you **declare** a function like: ```
void foo(int a, float b);
``` the signature wrt above definition is (2, (int, float), (int, float)).

Also, the arguments in the declaration/definition of the function are called "formal parameters"; whereas, the actual objects you pass to it during the call are called "actual parameters".

Now, when the function call is evaluated, the actual parameters are copied onto the call stack frame of the function - be it simple objects of fundamental data types or pointers (pointers are nothing but long integers that store address of other memory locations). However, the critical difference between them is that pointers can be de-referenced giving you the access to the object to which they point. This object generally lies outside of the call stack frame - only its address (a number) is copied onto the call stack - and therefore, out-lives the function call. This is how the modifications to such objects persist beyond the function call. The call stack frame is destroyed when the function returns destroying all the objects that reside on it.

To give you an example:
```
void add(int* ptr, int val) {
    printf("Received args: (%p, %d)\n", ptr, val);
    (*ptr) += val;
}

int main() {
    int a = 10;
    printf("A(addr, val): (%p, %d)\n", &a, a);
    add(&a, 5);
    printf("A(addr, val): (%p, %d)\n", &a, a);
    return 0;
}
```
When you call add(), both the 'actual' parameters (&a and 5) get copied onto the call stack frame of add(). But, since a is passed by reference, the modifications made to it in add() persist beyond the life of add() - as can be seen from the second printf() in main() - pay attention to the address of a printed in all three printf()s.

HTH ;)

---

### Post by mriedel on 2009-02-17
Regarding the key question:

> Well, my question was whether or not it's "bad" for a function to modify variables when that modification is not wanted or needed externally.

Yes, that is the very incarnation of "bad". Never modify data outside the local scope (of the function) if that isn't explicitly what the function is meant to do.

As was said before, the point of functions is to isolate behavior. A function should produce a defined result from a defined input and should never affect any other scope but its own if it isn't explicitly stated (i.e. in the documentation) that it does. Any other programmer should be able to use your function intuitively as soon as they know **what** it does. It should not be necessary to know **how** the function accomplishes that task. By no means should a programmer using your function end up having his variables modified by it without him even knowing that's happening. It's a bitch to debug ;)

---

### Post by Can+~ on 2009-02-17
It makes sense to use referenced passed variables to adjust a set of complex data, such as an image, a matrix, whatever. With single integers it doesn't make any sense, you're making your code more difficult for little, to no gain.

Example of when to use a reference:

[PHP]void transpose(int *matrix)
{
    // Gibberish
}[/PHP]

A good practice is to add comments to specify how the function works with data, either x->f(x)->return, or in-place modification.

---

### Post by Krupski on 2009-02-17
> **the_unforgiven said:**
> 
To give you an example:
```
void add(int* ptr, int val) {
    printf("Received args: (%p, %d)\n", ptr, val);
    (*ptr) += val;
}

int main() {
    int a = 10;
    printf("A(addr, val): (%p, %d)\n", &a, a);
    add(&a, 5);
    printf("A(addr, val): (%p, %d)\n", &a, a);
    return 0;
}
```
When you call add(), both the 'actual' parameters (&a and 5) get copied onto the call stack frame of add(). But, since a is passed by reference, the modifications made to it in add() persist beyond the life of add() - as can be seen from the second printf() in main() - pay attention to the address of a printed in all three printf()s.

HTH ;)

Thank you so much! I was sure I knew what you were talking about, then I compiled and stepped through your example and saw exactly what's going on. I'm getting it, slowly but surely!

Thanks again!

-- Roger

---

### Post by Krupski on 2009-02-17
> **mriedel said:**
> Regarding the key question:

Yes, that is the very incarnation of "bad". Never modify data outside the local scope (of the function) if that isn't explicitly what the function is meant to do.
..............
By no means should a programmer using your function end up having his variables modified by it without him even knowing that's happening. It's a bitch to debug ;)

Makes sense. I do lots of assembler programming and one big "rule" is that subroutines should not "destroy" any registers that it uses (unless it's meant to return a value using one). Obviously, the same goes for C.

I'm learning...

---

### Post by the_unforgiven on 2009-02-18
> **Krupski said:**
> Makes sense. I do lots of assembler programming and one big "rule" is that subroutines should not "destroy" any registers that it uses (unless it's meant to return a value using one). Obviously, the same goes for C.

I'm learning...
If you're comfortable with ASM, then, I think looking at the compiler-generated assembly code should make it easier for you to understand the C semantics.

To convert the C code into ASM using gcc:
```
gcc -S test.c -o test.s
```
However, note that GNU assembler (the backend of gcc - gas) uses AT&T style ASM syntax by default instead of Intel style. 
To generate ASM in Intel style syntax, use the following command:
```
gcc -S test.c **-masm=intel** -o test.s
```

HTH ;)

---

