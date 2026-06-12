---
title: "how do you refer to &quot;this instance&quot; from within a class?"
date: 2006-11-30
forum: Programming Talk
---

### Post by Choad on 2006-11-30
ok so i have this code

```

struct node
{
	CObject * obj;
	node * next;
};

<snip>

CObject::CObject()
{
	ID = IDC;
	temp = new node;
	**temp->obj** = 
	IDC++;
	x = 0;
	y = 0;
}

```

for the constructor even of class CObject

the bit in bold is unfinished

i need it to refer to it's self. how is this possible? it would be *self or something lol

this is for a linked list of objects :)

---

### Post by Henry Rayker on 2006-11-30
Something in my insides tells me it is *this but I could be wrong...I'll try to remember to check some old code I've written or some texts I have.

---

### Post by Choad on 2006-11-30
> **Henry Rayker said:**
> Something in my insides tells me it is *this but I could be wrong...I'll try to remember to check some old code I've written or some texts I have.
well gedit highlighted the syntax so its worth a punt lol

---

### Post by Henry Rayker on 2006-11-30
let me know how it goes...

---

### Post by Choad on 2006-11-30
> **Henry Rayker said:**
> let me know how it goes...
its good!
more problems tho lol....

```

CObject::CObject()
{
	  // add this instance to the global linked list of objects
	temp = new node;
	temp->obj = *this;
	temp->next = NULL;
	
	if (lastObject == NULL)
	{
		firstObject = temp;
		lastObject = temp;
	} else
	{
		lastObject->next = temp;
		lastObject = temp;
	}
	
	  //
	ID = IDC;
	IDC++;
	x = 0;
	y = 0;
}

```

richard@richard-laptop:~/Desktop$ g++ newproj.cpp
newproj.cpp: In constructor &#8216;CObject::CObject()&#8217;:
newproj.cpp:56: error: &#8216;temp&#8217; was not declared in this scope


????

---

### Post by po0f on 2006-11-30
Choad,

Post CObject's definition, if you would.

---

### Post by Choad on 2006-11-30
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
};

  // Classes
  //////////
  
class CObject
{
	int ID;
	
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
	temp = new node;
	temp->obj = *this;
	temp->next = NULL;
	
	if (lastObject == NULL)
	{
		firstObject = temp;
		lastObject = temp;
	} else
	{
		lastObject->next = temp;
		lastObject = temp;
	}
	
	  //
	ID = IDC;
	IDC++;
	x = 0;
	y = 0;
}

CObject::~CObject()
{
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
	return 0;
}

```

---

### Post by Choad on 2006-11-30
oh crap i see what ive done... or not done

---

### Post by Choad on 2006-11-30
ok even if i add in a 

node * temp;

before the other stuff in CObject's contructor, i still get an error

richard@richard-laptop:~/Desktop$ g++ newproj.cpp
newproj.cpp: In constructor &#8216;CObject::CObject()&#8217;:
newproj.cpp:58: error: cannot convert &#8216;CObject&#8217; to &#8216;CObject*&#8217; in assignment

---

### Post by po0f on 2006-11-30
Choad,

[FONT="Courier New"]this[/FONT] is itself a pointer, no need to dereference it.

Also, consider adding IDC as a static member of CObject.  That way, there will still only be one copy of the variable, but it will be private to CObject.
```
[FONT="Courier New"]class CObject {
/* snip */
private:
    int ID;
    static int IDC = 0;
};

CObject::CObject() {
    /* snip */
    ID = ++IDC;
}[/FONT]
```

---

### Post by Choad on 2006-11-30
awesome u guys are the best!

---

