---
title: "c++ inheritence help"
date: 2006-12-04
forum: Programming Talk
---

### Post by Choad on 2006-12-04
ok heres my object code

```

  // Class Functions
  //////////////////
  
CObject::CObject()
{
	Init();
}

CObject::~CObject()
{
	DeInit();
}

void CObject::Init()
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
	
	  // set other variables
	ID = IDC;
	IDC++;
	x = 0;
	y = 0;
	sprite = NULL;
}

void CObject::DeInit()
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
	if (sprite != NULL)
	{
		SDL_FreeSurface(sprite);
	}
}

int CObject::GetID()
{
	return ID;
}

void CObject::Draw()
{
	if (sprite != NULL)
	{
		  // draw my sprite
		rectTemp.x = x;
		rectTemp.y = y;
		SDL_BlitSurface(sprite, 
				NULL, 
				screen, 
				&rectTemp);
	}
}

void CObject::Step()
{
}

void CObject::KeyDown()
{
}


void CObject::KeyUp()
{
}

CBlock::CBlock()
{
	Init();
}

CBlock::~CBlock()
{
	DeInit();
}
```

and heres the error i get when compiling

```
richard@richard-laptop:~/Desktop$ g++ `sdl-config --cflags --libs` -o mygame newproj.cpp -lSDL -lSDL_image
newproj.cpp:186: error: definition of implicitly-declared ‘CBlock::CBlock()’
newproj.cpp:190: error: definition of implicitly-declared ‘CBlock::~CBlock()’
richard@richard-laptop:~/Desktop$ 

```

this is to do with my newly added class CBlock... i am just learning so i dont know what i did wrong. thx in advance for any help!

---

### Post by EntropicTundra on 2006-12-04
You need to add prototypes for CBlock::CBlock and CBlock::~CBlock in the declaration for CBlock. Example:
```

class CBlock
{
    public:
    CBlock();
    ~Cblock();

    // etc
}

```
The compiler doesn't complain about the same issue in CObject, so you must have done it right there. Take a look at the CObject declaration.

---

### Post by Choad on 2006-12-04
ahh legend!

---

