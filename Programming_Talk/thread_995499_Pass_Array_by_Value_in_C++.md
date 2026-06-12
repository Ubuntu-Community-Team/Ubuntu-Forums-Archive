---
title: "Pass Array by Value in C++"
date: 2008-11-27
forum: Programming Talk
---

### Post by Oddrey on 2008-11-27
I'm writing a tic-tac-toe program and I have a few functions that I wanted to pass an array's values to without changing the original array . Example: int getMove(int currentPos[9], int playerTurn); But after my program gave me really kooky behavior I found out I couldn't? :confused:

Do I need to make a new array in all of the functions I'm passing the original array to and copy the values over to the new arrays? Or is there an easier or more standard way to deal with this?

---

### Post by dwhitney67 on 2008-11-27
Below is an example.  In the future, if you require assistance dealing with compiler errors or runtime errors, post some code!
[php]
#include <iostream>

void function(int* array, size_t arrSize)
{
  for (size_t i = 0; i < arrSize; ++i)
  {
    std::cout << array[i] << " ";
  }
  std::cout << std::endl;
}

int main()
{
  int array[10] = {0,1,2,3,4,5,6,7,8,9};

  function(array, sizeof(array)/sizeof(int));

  return 0;
}
[/php]

---

### Post by terminaldogma on 2008-11-28
> **Oddrey said:**
> I'm writing a tic-tac-toe program and I have a few functions that I wanted to pass an array's values to without changing the original array . Example: int getMove(int currentPos[9], int playerTurn); But after my program gave me really kooky behavior I found out I couldn't? :confused:

Do I need to make a new array in all of the functions I'm passing the original array to and copy the values over to the new arrays? Or is there an easier or more standard way to deal with this?

To be sure i understand, you as passing ONE element (an integer) by value, and NOT wanting it to be altered?

Some example code would be nice, but from what you wrote ( int getMove(int, int) ) you should be fine, and not modifying values in the original array.  IF you were modifying them, you would either be passing them by reference (int &), or as a pointer (int *), which you are not.  You are automatically making a copy of them when you call a function and pass by value.

Consider:

```

int func(int a)
{ 
        a = 50;
        cout << a << endl;
        return a;
}

int main()
{
	int array[5] = { 1, 2, 3, 4, 5 };
	
	cout << array[2] << endl;
	cout << func(array[2]) << endl;
	cout << array[2] << endl;
	
	return 0;
}
```

The output from this will be:

```
3
50
50
3
```

Because you get index 2 from the array (50), pass it to func by value (prints 3), return it as an int and print that (3), then display the original value again (50).

So odd behavior might be another problem, hard to say w/o code.

---

