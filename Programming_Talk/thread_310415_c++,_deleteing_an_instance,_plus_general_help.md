---
title: "c++, deleteing an instance, plus general help"
date: 2006-12-01
forum: Programming Talk
---

### Post by Choad on 2006-12-01
heres my code

```

  // includes
  ///////////
  
#include <iostream>

  // Prototypes
  /////////////
  
  // Forward Declarations
  ///////////////////////
  
struct node;
class CObject;
  
  // Globals
  //////////
  
  // ID counter. so each object has a unique id
int IDC = 0;

  // pointer to the first and last objects in our linked list of objects.
node * firstObject = NULL;
node * lastObject = NULL;


  // Data Structures
  //////////////////
  
struct node
{
	CObject * obj;
	node * next;
	node * prev;
};

  // Classes
  //////////
  
class CObject
{
	int ID;
	node * myNode;
	
	public:
	CObject();
	~CObject();
	int GetID();
	
	int x, y;
};

  // Class Functions
  //////////////////
  
CObject::CObject()
{
	  // add this instance to the global linked list of objects
	myNode = new node;
	myNode->obj = this;
	myNode->next = NULL;
	myNode->prev = NULL;
	
	if (lastObject == NULL)
	{
		firstObject = myNode;
		lastObject = myNode;
	} else
	{
		lastObject->next = myNode;
		myNode->prev = lastObject;
		lastObject = myNode;
	}
	
	  //
	ID = IDC;
	IDC++;
	x = 0;
	y = 0;
}

CObject::~CObject()
{
	if (myNode == firstObject)
	{
		firstObject = myNode->next;
	} 
	if (myNode == lastObject)
	{
		lastObject = myNode->prev;
	}
	if (myNode->next != NULL)
	{
		myNode->next->prev = myNode->prev;
	}
	if (myNode->prev != NULL)
	{
		myNode->prev->next = myNode->next;
	}
}

int CObject::GetID()
{
	return ID;
}

  // Functions
  ////////////


  // Main
  ///////

int main()
{
	CObject myObj1;
	CObject myObj2;
	
	std::cout << myObj2.GetID() <<std::endl << myObj1.GetID() << std::endl;
	
	delete myObj1;
	
	return 0;
}

```

i would be very appreciative if someone could have a look through and see if i am doing things right. basically, there is a base "object" class called CObject that all the rest of the objects in my "game to be" will derive from. there is also a linked list, starting at firstObject, ending at lastObject that points to every CObject instance

the error im getting is because of the bit in bold. i wanted to test the destructor code of CObject (i assume delete is the way you execute that code)

the error i get is

richard@richard-laptop:~/Desktop$ g++ newproj.cpp
newproj.cpp: In function ‘int main()’:
newproj.cpp:120: error: type ‘class CObject’ argument given to ‘delete’, expected pointer


but i would appreciate comments on any part of this. i want to get it right from the ground up :)

---

### Post by Gustav on 2006-12-01
To delete objects they must be pointers and instanciated with new.

Change```
	CObject myObj1;
	CObject myObj2;
```to```
	CObject *myObj1 = new CObject();
	CObject *myObj2 = new CObject();
```and try again.

(And you'll have to change ```
std::cout << myObj2.GetID() <<std::endl << myObj1.GetID() << std::endl;
```to```
std::cout << myObj2->GetID() <<std::endl << myObj1->GetID() << std::endl;
```)

(But if you don't use pointers and new you don't have to delete anything, just skip the delete-lines)

---

### Post by Choad on 2006-12-01
cool thx

---

### Post by Gustav on 2006-12-01
And you should make IDC static inside the CObject class instead of global.

---

