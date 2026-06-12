---
title: "How to pass address of buffer to a function?"
date: 2009-02-28
forum: Programming Talk
---

### Post by Krupski on 2009-02-28
Hi all,
[COLOR="Red"][B]
[this is not homework and I am not a student][/B][/COLOR]

I've been trying to figure something out. It's probably easy and I'll probably kick myself when I get the answer, but for now it's got me stumped.

OK, here's what I would like to do:

(1) Define an array of ints... two columns wide by 1000 long (for up to 1000 instances of X,Y coordinate data). I tried this:

int coordinates[2][1000];
coordinates[0][n] = X;
coordinates[1][n] = Y;
n++;

(2) Next thing I need to do is pass the ADDRESS of the array to a sub function so that the sub function can "fill up" the array as it runs.

(3) Upon return from the sub function, the array will be filled and the function will return an int which is the count of how many X/Y pairs are in the array.

My big problem is passing the address TO the function, then GETTING the address inside the function.

I've gone through all my C books and am just not getting it.

Any help or suggestions will be greatly appreciated!

Thanks.

-- Roger

---

### Post by supirman on 2009-02-28
quick/dirty, but I think this is what you're after.  The name of the array is a pointer to the array (the address).

These are synonymous:
&myarray[0]   and    myarray

Both point to the first element in myarray. 

```
#include <stdio.h>

// fill some data into the passed in array
int fillXY(int xy[2][1000])
{
  int i;
  int x,y;
  x = y = 1;

  for(i=0; i<10; i++)
  {
    xy[0][i] = x;
    xy[1][i] = y;
    x = 2*x + 1;
    y = 2*y + 1;
  }

  return 10;
}


int main(void){

  int coords[2][1000];
  int i;
  int numCoords = fillXY(coords);

  printf("num coords is %d\n", numCoords);

  for(i=0; i<numCoords; i++)
    printf("coord: %d, x: %d, y: %d\n", i, coords[0][i], coords[1][i]);


  return 0;
}

```

---

### Post by napsy on 2009-03-01
or you could just pass the first pointer and avoid creating a new array on the function's stack.

> int fillXY(int **xy)

---

### Post by supirman on 2009-03-01
> **napsy said:**
> or you could just pass the first pointer and avoid creating a new array on the function's stack.

No, that doesn't work.  See [http://www.lysator.liu.se/c/c-faq/c-2.html](http://www.lysator.liu.se/c/c-faq/c-2.html) .

  Also, arrays are passed as pointers to the first element -- they don't allocate space on the stack for an entire copy:

```
(gdb) frame
#0  fillXY (xy=0xbfcb7d1c) at jnk.c:10
(gdb) info args
xy = (int (*)[1000]) 0xbfcb7d1c


```

As you can see, its address is passed to the fillXY function.

---

### Post by dwhitney67 on 2009-03-01
Yes, you can pass the address, although it will require that you cast the array.  It also might be prudent to pass the number of elements as well as a second argument; but I'll let you decide if you want to do that.

Btw, your requirements indicated that you wanted an array to store 1000 (x,y) coordinates.  Typically, the array would be defined as:
```

datatype array[num of elements][size of element];

```
where in your case, datatype is an int, num of elements is 1000, and the size of element is 2 (a value for x, another for y).

Anyhow, here's some code you can try wrt passing the array by pointer:
```

void function(int* coords)
{
}

int main()
{
  int coords[1000][2];     // think of this as 1000 (x,y) coordinates

  function((int*)coords);
}

```


P.S.  An alternative to consider:
```

typedef struct
{
  int x;
  int y;
} Coordinate;

const unsigned int MAX_COORDS = 1000;

void function(Coordinate* coords)
{
}

int main()
{
  Coordinate coords[MAX_COORDS];

  function(coords);
}

```

---

### Post by Krupski on 2009-03-01
> **dwhitney67 said:**
> Yes, you can pass the address, although it will require that you cast the array.

I've looked at all the responses so far and I don't "get it".

Let me show you (in pseudo-code) more exactly what I want to do:

```


// prototype for function
int linedraw(int x0, int y0, int x1, int y1, ??coord??);

int main(void)
{
    // a place to put up to 1000 x/y pairs
    int coord[2][1000];

    // how many coordinates were generated
    int count;

    // generic variable
    int n;

    // define a line from (1,10) to (5,20)
    int x0 = 1;
    int y0 = 10; // start point of line

    int x1 = 5;
    int y1 = 20; // end point of a line

    // call the function
    count = linedraw(x0, y0, x1, y1, coord);    

    // got coordinates, print them
    for(n = 0; n < count; n++) {
        printf("X=%2d, Y=%2d\n", coord[0][n], coord[1][n]);
    }

    return 0;
}

int linedraw(int x0, int y0, int x1, int y1, ??coord??)
{
    int c = 0; // how many pairs

    // this generates the points
    (for first to last) {
        coord[0][c] = X; // put points into array who's
        coord[1][c] = Y; // address was passed to us.
        c++
     }

    return c; // return with points count
}

```

I know how to do everything except:

(1) Properly define the 2 by 1000 array.
(2) Setup the array to receive the coordinates.
(3) How to pass the address of the array to the function.


I could also use "int x[1000];" and "int y[1000];", but then I would have to pass the address of BOTH to the function. I figured that making ONE array and passing ONE address would be better.

Hopefully, you can see what I'm trying to do here. I'm sure it's simple, but it's just not sinking in...

Thanks!

-- Roger

---

### Post by supirman on 2009-03-01
My first example did exactly what you just said -- did you look at it?  See the parameter to fillXY for your ??coord??

The fillXY function is just like your linedraw, without the x0,y0,x1,y1 passed in.  

A 2x1000 array is defined in main().

It is passed to fillXY.  

fillXY puts some data into it and returns the count (hardcoded to 10 for the example).

numCoords receives the value 10, then we iterate over those 10 elements and print them.

That's just about exactly what you just posted again... 

I'm confused about where you're confused...

---

### Post by Krupski on 2009-03-01
> **supirman said:**
> My first example did exactly what you just said -- did you look at it?  See the parameter to fillXY for your ??coord??

The fillXY function is just like your linedraw, without the x0,y0,x1,y1 passed in.  

A 2x1000 array is defined in main().

It is passed to fillXY.  

fillXY puts some data into it and returns the count (hardcoded to 10 for the example).

numCoords receives the value 10, then we iterate over those 10 elements and print them.

That's just about exactly what you just posted again... 

I'm confused about where you're confused...

Oh boy... I must have been 1/2 asleep. I looked at your code again and now it makes sense. What confused me (please don't laugh) is that you had the function on top and main() on the bottom!

Now I get it (I think)... let me try it. Thanks!

-- Roger

---

### Post by dwhitney67 on 2009-03-01
When passing an array to a function, you need to pass the address... which is what you are doing.  When it comes time to access that array, then things get a little tricky.

Here's an example of what I mean:
```

#include <stdio.h>

const int MAX_COORDS = 4;

int linedraw(int x0, int y0, int x1, int y1, int* coord)
{
  printf("inside linedraw()...\n");
  for (int i = 0; i < MAX_COORDS; ++i)
  {
    printf("\t(%d,%d)\n", coord[(i*2) + 0], coord[(i*2) + 1]);
  }
  return 0;
}

int main()
{
  int coord[MAX_COORDS][2];

  // setup bogus values for test purposes
  for (int i = 0; i < MAX_COORDS; ++i)
  {
    coord[i][0] = (i+1) * 2;
    coord[i][1] = (i+1) * 3;
  }
  printf("inside main()...\n");
  for (int i = 0; i < MAX_COORDS; ++i)
  {
    printf("\t(%d,%d)\n", coord[i][0], coord[i][1]);
  }

  linedraw(0,0,1,1,(int*)coord);
}

```

---

### Post by Krupski on 2009-03-01
> **dwhitney67 said:**
> When passing an array to a function, you need to pass the address... which is what you are doing.  When it comes time to access that array, then things get a little tricky.

I finally got it with your help and with **supirman**'s help.

Here's my test program which seems to be working... please comment (especially on the parts in red):

```

// linedraw.c - test program for Bresenham's algorithm

#include <stdio.h>
#include <stdlib.h>

[COLOR="Red"]**int line(int, int, int, int, int [2][1000]);**[/COLOR] // prototype

void swap(int*, int*); // swap(x, y);

int main(int argc, char *argv[])
{
	if(argc != 5) {
		fprintf(stderr, "error: exactly 4 params required\n");
		fprintf(stderr, "usage: line x0 y0 x1 y1\n");
		return 1;
	}

	int x0 = atoi(argv[1]);
	int y0 = atoi(argv[2]);
	int x1 = atoi(argv[3]);
	int y1 = atoi(argv[4]);

	[COLOR="Red"]**int coords[2][1000];**[/COLOR]
	int x, count;

	// call linedraw
	[COLOR="Red"]**count = line(x0, y0, x1, y1, coords);**[/COLOR]

	for(x = 0; x < count; x++) {
		fprintf(stdout, "X=%2d, Y=%2d\n", coords[0][x], coords[1][x]);
	}

	return 0;
}



// Bresenham's line draw algorithm.
// (modified to generate points in the
// same direction that they are specified).

[COLOR="Red"]**int line(int x0, int y0, int x1, int y1, int xy[2][1000])**[/COLOR]
{
	int x, cx, dx, xs,
	y, cy, dy, ys,
	er, n, st;

	dx = abs(x0 - x1); // delta x
	dy = abs(y0 - y1); // delta y

	// flag for largest delta
	st = (dx < dy);

	// if dy < dx then swap x/y and delta x/y
	if (st) {
		swap(&x0, &y0);
		swap(&x1, &y1);
		swap(&dx, &dy);
	}

	er = dx / 2; // converge check
	y = y0;

	(x0 < x1) ? (xs = 1) : (xs = -1); // derive x step
	(y0 < y1) ? (ys = 1) : (ys = -1); // derive y step

	n = 0; // initialize coordinate count

	for (x = x0; x != (x1 + xs); x += xs)
	{
		cx = x; cy = y; // copy of x, copy of y

		// if x,y were swapped then swap back
		if (st) { swap(&cx, &cy); }

               // copy points to array
		[COLOR="Red"]**xy[0][n] = cx; xy[1][n] = cy; n++;**[/COLOR]

		er -= dy; // converge to end of line

		if (er < 0) {
			y += ys; er += dx; // increment y, converge
		}
	}
	return n; // n = coordinate count
}


void swap(int *x, int *y)
{
	*x ^= *y; // swap without temp
	*y ^= *x;
	*x ^= *y;
}

```


Thanks to all of you for the help!

-- Roger

---

