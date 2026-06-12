---
title: "Advice please"
date: 2009-12-16
forum: Programming Talk
---

### Post by detorresrc on 2009-12-16
Below is my simple template code, can you give me an advice how to improve my template class. Thanks in advance. :D

[PHP]
//============================================================================
// Name        : templating.cpp
// Author      : 
// Version     :
// Copyright   : Your copyright notice
// Description : Hello World in C++, Ansi-style
//============================================================================

#include <iostream>
#include <string.h>
#include <stdio.h>
#include <unistd.h>

using namespace std;

#include "list_template.h"

int main() {
	TList<char> listString;

	while(true){
		for(int a=0; a<=10; a++){
			char *pChar = new char[100];
			sprintf(pChar, "ROMMEL DE TORRES %d", a);

			if( listString.addData(pChar) == false ){
				cout << "Unable to add string." << endl;
			}
		}

		while( listString.eof() == false ){
			char *pString = listString.getData();
			if(!pString) continue;

			cout << pString << endl << endl;
			pString = NULL;
			listString.next();
		}

		listString.moveFirst();

		while( listString.eof() == false ){
			char *pString = listString.getData();
			if(!pString) continue;

			cout << pString << endl << endl;
			pString = NULL;
			listString.next();
		}
		listString.clear();
		usleep(500);
	}
	return 1;
}

[/PHP]

[PHP]
/*
 * list_template.h
 *
 *  Created on: Dec 16, 2009
 *      Author: rommel
 */

#ifndef LIST_TEMPLATE_H_
#define LIST_TEMPLATE_H_

#include <iostream>
#include <string.h>
using namespace std;

template <class T>
class TList{
public:
	TList();
	virtual ~TList();
	bool addData(T *pData);
	T    *getData();
	void next();
	void moveFirst();
	bool eof();
	void clear();
private:
	struct ListData{
		unsigned long index;
		T             *pData;
		ListData      *next;
	};

	typedef struct ListData *pListData;

	pListData head, tail;
	unsigned long index;

	/*
	 *ITERATOR
	 * */
	pListData iterator;
	bool iteratorEOF;
};

template <class T>
TList<T>::TList(){
	head        = NULL;
	tail        = NULL;
	index       = 0;
	iteratorEOF = true;
}

template <class T>
TList<T>::~TList(){
	head      = NULL;
	tail     = NULL;
	iterator = NULL;

	clear();
}

template <class T>
void TList<T>::clear(){
	pListData plist, pListNext;
	for(plist = head; plist!=NULL; plist=pListNext){
		pListNext = plist->next;

		delete plist->pData; plist->pData = NULL;
		delete plist; plist = NULL;
	}
	index       = 0;
	iteratorEOF = true;
	iterator    = NULL;
	head        = NULL;
	tail        = NULL;
	pListNext   = NULL;
}

template <class T>
bool TList<T>::eof(){
	return iteratorEOF;
}

template <class T>
void TList<T>::next(){
	if( iteratorEOF == false && (iterator->next != NULL) ){
		iterator = iterator->next;
	}else{
		iteratorEOF = true;
		iterator    = NULL;
	}
}

template <class T>
void TList<T>::moveFirst(){
	iterator = head;
	if(iterator==NULL)
		iteratorEOF = true;
	else
		iteratorEOF = false;
}

template <class T>
T *TList<T>::getData(){
	if(!iterator){
		return NULL;
	}
	return iterator->pData;
}

template <class T>
bool TList<T>::addData(T *pData){
	pListData pCurrent = new ListData;
	if(!pCurrent){
		pCurrent = NULL;
		return false;
	}

	pCurrent->index = index++;
	pCurrent->pData = pData;

	if(!head){
		iterator    = head = tail = pCurrent;
		iteratorEOF = false;
	}else{
		tail->next = pCurrent;
		tail       = pCurrent;
	}
	return true;
}

#endif /* LIST_TEMPLATE_H_ */

[/PHP]

---

### Post by Zugzwang on 2009-12-16
Here are some minor things:
[LIST]
[*]Format your code in a more legible way. For example, put a space before "{". Also, don't put "template <class T> " on individual lines.
[*]I'm not sure, but I think that "new" never returns "NULL" but rather throws an exception on mem-out, so the "if(!pCurrent){ ... }" block in the "addData" function is redundant. In fact, this also makes the return value of the function unnecessary.
[*] Why using "sprintf" in C++ code? Stringstreams are somewhat nicer and much more c++ish.
[*] Why include "string.h" in the header file?
[*] Uuh, don't use "using namespace std;" in header files. For reasons, see this thread: [http://ubuntuforums.org/showthread.php?t=1356546](http://ubuntuforums.org/showthread.php?t=1356546)
[/LIST]

---

### Post by dwhitney67 on 2009-12-16
Suppose I want a TList of chars... how do I do that??  Using this syntax?
```

TList<char>  tl;

```

Your TList class would assume from my specification above that I wanted a list of char*.  I don't!  I just want a list of char values.

Anyhow, if you are wondering where I'm leading to, just look at your class declaration.  The following is incorrect:
```

template <class T>
class TList
{
...
private:
    struct ListData{
        unsigned long index;
        T             *pData;
        ListData      *next;
    };
};

```
It should be:
```

template <class T>
class TList
{
...
private:
    struct ListData{
        unsigned long index;
        T             pData;
        ListData      *next;
    };
};

```
Of course, the other methods (in the public section) will need to be modified too.

With the corrected code I should be able to have the following:
```

TList<char>        listOfChar;
TList<char*>       listOfCharPointer;
TList<std::string> listOfStrings;

```
Now why in pray tell would anyone choose to use a char* versus an STL string is a different topic beyond the scope of this thread, but hopefully it will make you question your example.  As Zugzwang pointed out, an STL stringstream would be a better choice to formulate your string.
```

#include <sstream>
...
TList<string> list;

stringstream oss;
oss << name << " " << age;

list.add(oss.str());
...


```

---

### Post by johnl on 2009-12-16
Not related to your template class, but I see that you allocate plenty of memory when adding items to your list:
```

char *pChar = new char[100]; 

```

It would be a good idea to free this memory later when you remove it from the list. In this case it doesn't really matter, since your program will end immediately after this, but it's a good habit to get into:

```

cout << pString << endl << endl;
delete[] pString;

```


Also, why is your main() function returning 1? It is normal to return 0 to indicate success and a non-zero value to indicate an error condition.

---

### Post by MadCow108 on 2009-12-16
the c headers in c++ start with a c and have no ending:
cstdio, cstring etc

also your "iterator" can hardly be called an iterator, its just a pointer (which is, unlike the case of array iterators, no adequate iterator for a list)
Adding a proper STL like iterator to the list would be a nice addition to your class.

also adding template specializations for pointers would reduce code bloat of your lists.

I also hope this is just an exercise and should not be used in production code, as the STL list is a lot more versatile than your code.

---

### Post by detorresrc on 2009-12-16
Thanks :D

---

