---
title: "ISO C++ forbids declaration of ‘link’ with no type"
date: 2008-12-26
forum: Programming Talk
---

### Post by jyaan on 2008-12-26
What's going on with this code? It's taken directly out of a textbook by Robert Lafore : OOP in C++. GCC claims "ISO C++ forbids declaration of ‘link’ with no type", yet link is defined directly above with a struct... No other errors are given, aside from later references to pointers of type link. The typedef keyword does not make any difference.

[PHP]// linklist.cpp
// linked list
#include <iostream>
using namespace std;

struct link				// one element of list
	{
	int data;			// data item
	link *next;			// pointer to next link
	};

class linklist			// a list of links
	{
	private:		
		link *first;	// pointer to first link
	public:	
		linklist()
			{ first = NULL; }	// no first link
		void additem(int d);	// add data item (one link)
		void display();			// display all links
	};
	
void linklist::additem(int d)
	{
	link *newlink = new link;	// make a new link
	newlink->data = d;			// give it data
	newlink->next = first;		// it points to next link
	first = newlink;			// now first points to this
	}
	
void linklist::display()
	{
	link *current = first;					// set ptr to first link
	while (current != NULL)					// quit on last link
		{
		cout << current->data << endl;		// print data
		current = current->next;			// move to next link
		}
	}
	
int main()
	{
	linklist li;
	
	li.additem(25);
	li.additem(36);
	li.additem(49);
	li.additem(64);
	li.display();
	return 0;
	}[/PHP]

---

### Post by jyaan on 2008-12-26
Okay.... I replaced all occurrences of 'link' with 'node' and now it is fine. Does anyone know the reason for this? It definitely isn't a reserved word.

---

### Post by dwhitney67 on 2008-12-26
After 10 minutes of research into your question, I found the answer.  "link" is a function name as defined in unistd.h.  Refer to the manpage for more detail.
```

man 2 link

```

When you include iostream in your application, it in turn includes bits/c++config.h.  This file just so happens to include unistd.h, and hence the conflict with the definition it defines and the struct you attempted to define.

Btw, bits/c++config.h is located at the following path under my Fedora 9 system; I do not have my Ubuntu system booted at this time, otherwise I would give you that path.
```

/usr/include/c++/4.3.0/i386-redhat-linux

```

---

