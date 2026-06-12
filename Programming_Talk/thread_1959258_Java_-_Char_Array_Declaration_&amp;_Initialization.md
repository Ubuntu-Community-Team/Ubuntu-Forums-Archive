---
title: "Java - Char Array Declaration &amp; Initialization"
date: 2012-04-15
forum: Programming Talk
---

### Post by kevinharper on 2012-04-15
For an int array, I could do:
```
		//declare array
		int[] anArray;

		//allocate mem for array
		anArray = new int[3];

		//set values
		anArray[0] = 10;
		anArray[1] = 20;
		anArray[2] = 30;
```
And it works.

But I can't seem to do something similar w/ char arrays. I get compilation errors with:
```

//declare arrays
char[] srcArray;
char[] desArray;

//initialize arrays
srcArray = {'K', 'E', 'V', 'I', 'N'};
desArray = new char[5];

```

I get less compilation errors when I add "[]" after the array names when initializing them. But it won't compile.

Question: Do char arrays need to be declared and initialized in the same line?

---

### Post by kevinharper on 2012-04-15
I think I'm getting ahead of myself. I am supposed to be learning about arrays, not strings. That comes up a lot later in the tutorial.

---

### Post by jespdj on 2012-04-15
You're not using the correct syntax. You can initialize a char array in exactly the same way as you did with an int array:
```

char[] srcArray;

srcArray = new char[5];

srcArray[0] = 'K';
srcArray[1] = 'E';
srcArray[2] = 'V';
srcArray[3] = 'I';
srcArray[4] = 'N';

```
Or declare and initialize it like this:
```

char[] srcArray = new char[] { 'K', 'E', 'V', 'I', 'N' };

```
That last syntax also works with int arrays:
```

int[] example = new int[] { 2, 5, 7 };

```

---

### Post by kevinharper on 2012-04-16
WOW! I don't know how I missed that! Thank you!

Here's how it ended up (I was omitting "new char[]" before KEVIN char values):
```
		//declare arrays
		char[] srcArray;
		char[] desArray;

		//initiate arrays
		srcArray = new char[] {'K', 'E', 'V', 'I', 'N'};
		desArray = new char[5];
```
Question: Although it's allowed & it compiles, what does convention dictate? Should I just do as you did on your second code example? (BTW, that's what I meant when I asked if "char arrays need to be declared and initialized in the same line".

---

### Post by PaulM1985 on 2012-04-16
I recommend just sticking with what is clearest for the reader.

For example:
```

char[] alphaStr = new char[] { 'a', 'l', 'p', 'h', 'a'};

```

is fairly clear, where as:
```

// not very clear
double[] movement = new double[] { 0.5*a*t*t + v0*t + d0, a*t + v0, a};

// clearer
int MOVEMENTS = 3;
int DISTANCE_IDX = 0;
int VELOCITY_IDX = 1;
int ACCELERATION_IDX = 2;

double[] movement = new double[MOVEMENTS];
movement[DISTANCE_IDX] = 0.5*a*t*t + v0*t + d0;
movement[VELOCITY_IDX] = a*t + v0;
movement[ACCELERATION_IDX] = a;

```

I think initialising on one line is probably quicker, but I don't know for certain.

Paul

---

### Post by kevinharper on 2012-04-16
Sound good. Thank you.

---

### Post by Damascushead on 2012-04-19
Kevinharper,
 
To answer your question about initializing in the same line as the declaration, it is probably fine for the bit of code that you are showing.
 
When you get in to creating classes and are declaring public field variables, convention might dictate that you declare your field variables first in one line, and then initialize them(assign value) in the constructor of that class.
 
Peace

---

### Post by kevinharper on 2012-04-20
Thank you for the information, Damascushead.

---

