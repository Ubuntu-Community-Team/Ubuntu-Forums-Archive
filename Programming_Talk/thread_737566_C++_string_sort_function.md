---
title: "C++ string sort function"
date: 2008-03-27
forum: Programming Talk
---

### Post by Ojan on 2008-03-27
Hello all. I'm new to the forum, so please treat me nice ;) Should this topic be in the wrong forum or something, please move it to the right place :)

Anyway, my problem: I have a bunch of strings that I want sorted alphabetically. I have on teh internets found just the code to do this, and it works like a charm. However, for the life of me, I can't understand why it works. 

```

#include <string>
#include <iostream>
using namespace std;

void selectionSort(string [], int);
void showArray(string [], int);

int main()
{
	const int SIZE = 20;
	
	string name[SIZE] =
	{ "Collins, Bill", "Smith, Bart", "Michalski, Jacob",
"Griffin, Jim", "Sanchez, Manny", "Rubin, Sarah",
"Taylor, Tyrone", "Johnson, Jill", "Allison, Jeff",
"Moreno, Juan", "Wolfe, Bill", "Whitman, Jean",
"Moretti, Bella", "Wu, Hong", "Patel, Renee",
"Harrison, Rose", "Smith, Cathy", "Conroy, Patrick",
"Kelly, Sean", "Holland, Beth" };

	cout << "\tThe unsorted string is: \n";
	showArray(name, SIZE);
	selectionSort(name, SIZE);
	cout << "\n\tThe sorted string is: \n";
	showArray(name, SIZE);
	
	return 0;
}


void selectionSort(string name[], int elems)
{
	int startScan, minIndex;
	string strName;
	for(startScan = 0; startScan < (elems - 1); startScan++)
	{
		minIndex = startScan;
		strName = name[startScan];
		for(int index = startScan + 1; index < elems; index++)
		{
			if(name[index] < strName)
			{
				strName = name[index];
				minIndex = index;
			}
		}
		name[minIndex] = name[startScan];
		name[startScan] = strName;
	}
}


void showArray(string name[], int elems)
{
	for(int count = 0; count < elems; count++)
		cout << count << ": " << name[count] << endl;
}


```

selectionSort is a void-function, there are no global variables, and we don't touch pointers or anything. How can "name" stay sorted when we showArray again?

The "name" in selectionSort appears to be a local copy, right? And I don't see how selectionSort can make "name" changed when we return to main. And yet it works. :p


Any help and explanations would be greatly appreciated :)

---

### Post by luisromangz on 2008-03-27
In C and C++, arrays are always pointers. Declaring the parameter string name[] or string name* should have the same effect.

---

### Post by keelerm on 2008-03-27
Arrays are passed by reference.  An array name is nothing more than a pointer to the beginning of the array.  You can deference arrays by using pointer notation if you want, such as . . .
```
*(array+3)
```
which is equivalent to 
```
array[3]
```
So you really are working with pointers.  You just didn't know it.

---

### Post by Ojan on 2008-03-27
Ah, that explains it! Thank you very much!

Would that be true for a vector<string> as well? Just passing a vector<string> to a function would mean that function can modify it without return values, just the same way as in the code above?

---

### Post by Zeroaegis on 2010-09-26
I apologize for dredging up an old thread, but I was searching google for an answer to my question when I came across this post. I am replying here because this is the exact program I have to make, with the exception that the array of strings is a 2D char array.

I cant figure out how to convert the char array into an array of strings for the sorting process.

Any help is much appreciated.

---

