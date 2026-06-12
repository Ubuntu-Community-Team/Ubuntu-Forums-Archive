---
title: "[SOLVED] does this dynamic mem not need freed?"
date: 2007-09-15
forum: Programming Talk
---

### Post by nonewmsgs on 2007-09-15
i'm reviewing my old C++ books and in this one example the author does not free it :confused:

is it unnessary in this case for some reason or is it just a slip

#include <iostream>

using namespace std;


int main()
{
	int numTests;
	
	cout << "Enter the number of test scores: ";
	cin >> numTests;
	
	int* iPtr=new int[numTests];
	
	for(int i=0;i<numTests;i++){
		cout << "Enter test score #"
			<< i+1<< " : ";
		cin >> iPtr[i];
	}
	// why isnt there a delete statement right here???
	return 0;
}

---

### Post by CptPicard on 2007-09-15
Yep, he's got a bug there. I suspect he initially wrote it as an array, or is going to demostrate later on that this is going to need a delete :)

---

### Post by nonewmsgs on 2007-09-15
thanks mate!  i think he is showing that next, but he doesn't seem to go back to referencing that one.

---

