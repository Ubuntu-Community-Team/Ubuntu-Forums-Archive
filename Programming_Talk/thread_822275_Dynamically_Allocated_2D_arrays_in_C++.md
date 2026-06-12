---
title: "Dynamically Allocated 2D arrays in C++"
date: 2008-06-08
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-06-08
I want to dynamically allocate a 2D character array in C++.  For example this is what I want to do:

[PHP]
int rows;
int cols;

cout << "Enter rows: ";
cin >> rows;
cout << "Enter cols: ";
cin >> cols;

char ** = char[row][col];
[/PHP]

I get a compile error on the last line, something about C++ not knowing the size of the array at compile time.  Is there a way around this?  I know about vector and I want to allocate a constant array instead for performance reasons...I am currently using Boost::multi_array as a substitute...it works, but that's a bit of overhead.

---

### Post by DavidBell on 2008-06-08
You can only allocate static arrays at compile time, for dynamic arrays you have to 'new' them

I use these macros sometimes
```

// Easy one dimensional arrays
#define BCDECLAREARRAY_1D(TYPE,NAME)			TYPE *NAME;
#define BCCREATEARRAY_1D(TYPE,NAME,XSIZE)		NAME = new TYPE[(XSIZE)];
#define BCDESTROYARRAY_1D(NAME)			delete[] NAME;

// Easy two dimensional arrays
#define BCDECLAREARRAY_2D(TYPE,NAME)			TYPE **NAME;
#define BCCREATEARRAY_2D(TYPE,NAME,XSIZE,YSIZE)	NAME = new TYPE*[(XSIZE)]; for (int tempi = 0; tempi < (XSIZE); tempi++) NAME[tempi] = new TYPE[(YSIZE)];
#define BCDESTROYARRAY_2D(NAME,XSIZE)		for (int tempi = 0; tempi < (XSIZE); tempi++) delete[] NAME[tempi]; delete[] NAME;

```

Or you can use vector<vector<char> >

---

### Post by Jessehk on 2008-06-08
Isn't that funny: I was going to suggest Boost.MultiArray ;)

I think you're going to have do as DavidBell suggest: perhaps without those ugly macros though. ;)

---

### Post by SNYP40A1 on 2008-06-08
Sorry, I should have compiled before posting, I figured that for something so short, I could not screw it up.  Here's the code which compiles and reflects what I want:

[PHP]
// map::insert
#include <iostream>
using namespace std;

int main ()
{
	int rows;
	int cols;

	cout << "Enter rows: ";
	cin >> rows;
	cout << "Enter cols: ";
	cin >> cols;

	char ** myarray = new char[rows][cols];  
	
	return 0;
}
[/PHP]

Here's what I get when trying to compile:

$ gcc test2.cpp
test2.cpp: In function `int main()':
test2.cpp:15: error: `cols' cannot appear in a constant-expression

---

### Post by SNYP40A1 on 2008-06-08
> **DavidBell said:**
> You can only allocate static arrays at compile time, for dynamic arrays you have to 'new' them

I use these macros sometimes
```

// Easy one dimensional arrays
#define BCDECLAREARRAY_1D(TYPE,NAME)			TYPE *NAME;
#define BCCREATEARRAY_1D(TYPE,NAME,XSIZE)		NAME = new TYPE[(XSIZE)];
#define BCDESTROYARRAY_1D(NAME)			delete[] NAME;

// Easy two dimensional arrays
#define BCDECLAREARRAY_2D(TYPE,NAME)			TYPE **NAME;
#define BCCREATEARRAY_2D(TYPE,NAME,XSIZE,YSIZE)	NAME = new TYPE*[(XSIZE)]; for (int tempi = 0; tempi < (XSIZE); tempi++) NAME[tempi] = new TYPE[(YSIZE)];
#define BCDESTROYARRAY_2D(NAME,XSIZE)		for (int tempi = 0; tempi < (XSIZE); tempi++) delete[] NAME[tempi]; delete[] NAME;

```

Or you can use vector<vector<char> >

Thanks DavidBell, I tried your code here:

[PHP]
// map::insert
#include <iostream>
using namespace std;

// Easy two dimensional arrays
#define BCDECLAREARRAY_2D(TYPE,NAME)			TYPE **NAME;
#define BCCREATEARRAY_2D(TYPE,NAME,XSIZE,YSIZE)	NAME = new TYPE*[(XSIZE)]; for (int tempi = 0; tempi < (XSIZE); tempi++) NAME[tempi] = new TYPE[(YSIZE)];
#define BCDESTROYARRAY_2D(NAME,XSIZE)		for (int tempi = 0; tempi < (XSIZE); tempi++) delete[] NAME[tempi]; delete[] NAME;

int main ()
{
	int rows;
	int cols;

	cout << "Enter rows: ";
	cin >> rows;
	cout << "Enter cols: ";
	cin >> cols;

	BCDECLAREARRAY_2D(char, myarray);
	BCCREATEARRAY_2D(char,myarray,rows,cols);
	
	return 0;
}
[/PHP]

And it compiles fine (my previous post was incorrect because I was using gcc instead of g++).  However, I want to have the array be a member of a class.  Therefore, I can't use BCDECLAREARRAY to declare it.  I am curious as to why I cannot allocate the 2D array simply with the code posted above (in my previous post).

---

### Post by slavik on 2008-06-08
simply do:

```

char blah[rows][cols];

```

I think that's what I used ...

---

### Post by SNYP40A1 on 2008-06-08
That works, but actually, but I want it to be declared dynamically...I might want to change the size later (usually not, but sometimes I will).

---

### Post by Can+~ on 2008-06-08
Before going any further, what are you storing? It will be a matrix like:
```

0 0 0 0 0 0 0 0 0 0 0
0 0 0 0 0 2 0 0 0 0 0
0 0 0 1 0 0 3 0 0 6 0
0 0 8 0 0 1 0 0 2 0 3
5 0 0 7 0 0 0 0 5 0 0
0 0 0 0 3 0 0 0 0 0 0
2 0 0 0 0 0 0 0 1 0 0
0 0 0 0 0 0 0 0 0 0 0
```

In cases like that, it's more efficient to store each value and it's coordinate, instead of allocating a full table.

---

### Post by DavidBell on 2008-06-08
The reason is that your way the compiler creates the resources on the stack at //compile time//, but it can't do that with a dynamic array because it doesn't know how big it will be. Using 'new' it gets created on the heap at //run time// when it knows the size.

You can use my macros in a class something like this

```

class myclass
{protected:
   BCDECLAREARRAY_2D(char, myarray);
   int mrows, mcols;
 public:
   myclass(int rows, int cols)
      {// specialised constructor
          BCCREATEARRAY_2D(char, myarray, rows, cols);
          mrows = rows;
          mcols = cols;
      }
   ~myclass()
      {// clean up in destructor
          BCDESTROYARRAY_2D(char, myarray, mrows);
      }
};

```

@Jessehk, my macros are not ugly they are beautiful :-)

PS, I see your later post you may resize the array, don'r forget to destroy it first or you will get a memory leak, you have to destroy final version at end as well for same reason. DB

---

### Post by Lster on 2008-06-08
[QUOTE=Can+~]In cases like that, it's more efficient to store each value and it's coordinate, instead of allocating a full table.[/QUOTE]

How do you mean?

---

### Post by Can+~ on 2008-06-08
> **Lster said:**
> **WHAT** do you mean?

If you store a table with m*n values, you'll use up m*n*sizeof(type) to store that amount of data. That's fine, but let's say that you store 5 values in a 20x20 matrix, that would produce, 400*sizeof(type) to store 5 important values.

Using a coordinate you save up space:

[PHP]typedef struct
{
	int data;
	unsigned char _x_, _y_; // Guessing that you won't go over 255x255
}coord;[/PHP]

So now, you store the position of each element. A good example is your typical window-creation software (visual studio?), in which you place widgets at an x,y position, storing a huge 2d array for that would be plain dumb.

It all depends on what you're trying to accomplish. Here's how to allocate a 2d dynamic array in C:

[PHP]int main(int argc, char** argv)
{
	int width=4, height=5, i, j;
	
	//Create columns
	char **table = (char**)malloc(sizeof(char*)*height);
	
	//Create rows for each column.
	for (i=0; i<height; i++)
	{
		table[i] = (char*)malloc(sizeof(char)*width);
	}
	
	//Populate
	for (i=0; i<height; i++)
		for (j=0; j<width; j++)
		{
			table[i][j] = i*j;
		}
	
	//Print it
	for (i=0; i<height; i++)
	{
		for (j=0; j<width; j++)
		{
			printf("%d ", table[i][j]);
		}
		printf("\n");
	}
	
	//Free it
	for (i=0; i<height; i++)
	{
		free(table[i]);
	}
	free(table); //Almost forgot about this one.
	
	return 0;
}[/PHP]

```

table (char**)
  0 : char* -> [00, 01, 02, 03, 04, 05 .. n]
  1 : char* -> [10, 11, 12, 13, 14, 15 .. n]
  2 : ......
  3 : ......
  .
  .
  .
  m

```
Each element of the column is formed by a *char, which points to another allocated space. I don't like this approach anyway, maybe use a matrix-like library of C++?

edit:
Another method would be to simulate a 2d array, in which you store a long array of width*height, and consider each "width" as a column. This has the advantage of making just 1 allocation, but harder to realloc later.

---

### Post by Lster on 2008-06-08
EDIT: I did not realize Can+~'s full meaning in his original post.

---

### Post by slavik on 2008-06-08
> **SNYP40A1 said:**
> That works, but actually, but I want it to be declared dynamically...I might want to change the size later (usually not, but sometimes I will).
that will in fact be allocated on the heap.

---

### Post by Can+~ on 2008-06-08
> **Lster said:**
> (but more memory efficient for sparse data)!

That's why I said, "if you have a matrix like this <insert draw of matrix filled with 0s>", dude, read a bit before posting.

I'm not saying he MUST do it with a coordinate system, I'm saying, if it's more effective, then use that other method. And this methods so happens to be far more efficient when dealing on certain tasks. For example, place an image on a 800x600 canvas in flash (for example) what do you do? A 800x600 matrix, or just store (xpos, ypos, data)?

Sheesh..

---

### Post by Lster on 2008-06-08
[QUOTE=Can+~]That's why I said, "if you have a matrix like this <insert draw of matrix filled with 0s>", dude, read a bit before posting.[/QUOTE]

I'm very sorry - I didn't understand.

I know you're not saying it must be done that way and I'm sorry if you took my post negatively - I really didn't mean it like that. I also agree there are good uses for this, but as I said, didn't realize you meant for sparse data.

Again, sorry! :)

---

### Post by SNYP40A1 on 2008-06-08
> **Can+~ said:**
> If you store a table with m*n values, you'll use up m*n*sizeof(type) to store that amount of data. That's fine, but let's say that you store 5 values in a 20x20 matrix, that would produce, 400*sizeof(type) to store 5 important values.

Using a coordinate you save up space:

[PHP]typedef struct
{
	int data;
	unsigned char _x_, _y_; // Guessing that you won't go over 255x255
}coord;[/PHP]

So now, you store the position of each element. A good example is your typical window-creation software (visual studio?), in which you place widgets at an x,y position, storing a huge 2d array for that would be plain dumb.

It all depends on what you're trying to accomplish. Here's how to allocate a 2d dynamic array in C:

[PHP]int main(int argc, char** argv)
{
	int width=4, height=5, i, j;
	
	//Create columns
	char **table = (char**)malloc(sizeof(char*)*height);
	
	//Create rows for each column.
	for (i=0; i<height; i++)
	{
		table[i] = (char*)malloc(sizeof(char)*width);
	}
	
	//Populate
	for (i=0; i<height; i++)
		for (j=0; j<width; j++)
		{
			table[i][j] = i*j;
		}
	
	//Print it
	for (i=0; i<height; i++)
	{
		for (j=0; j<width; j++)
		{
			printf("%d ", table[i][j]);
		}
		printf("\n");
	}
	
	//Free it
	for (i=0; i<height; i++)
	{
		free(table[i]);
	}
	free(table); //Almost forgot about this one.
	
	return 0;
}[/PHP]

```

table (char**)
  0 : char* -> [00, 01, 02, 03, 04, 05 .. n]
  1 : char* -> [10, 11, 12, 13, 14, 15 .. n]
  2 : ......
  3 : ......
  .
  .
  .
  m

```
Each element of the column is formed by a *char, which points to another allocated space. I don't like this approach anyway, maybe use a matrix-like library of C++?

edit:
Another method would be to simulate a 2d array, in which you store a long array of width*height, and consider each "width" as a column. This has the advantage of making just 1 allocation, but harder to realloc later.

I thought about simulating the 2D array with a 1D array.  That works, but I think the the macros posted above are simpler to use.  Originally, I used Boost::multi_array, and it worked well, although I was getting an "out of memory" error after allocating / deallocating a few instances of the template which used it.  I think I probably did not setup the destructor correctly.  Anyway, since I do not resize the array often (in typical usage, the array will only be setup once and never resized).  I figured that the Boost dynamic multi-array template would add a bit of unnecessary overhead.  I do like the multi-array though and look forward to trying more boost templates in the future.

---

