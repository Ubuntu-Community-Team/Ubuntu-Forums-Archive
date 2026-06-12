---
title: "more c++ problems!"
date: 2006-12-08
forum: Programming Talk
---

### Post by Choad on 2006-12-08
ok ill just upload my project this time lol

i cant figure out whats wrong. its deffinately to do with class CDirt. the thing runs fine if i dont execute

dirt = new CDirt();

in main

i am lost :S

compile with

 g++ `sdl-config --cflags --libs` -o mygame newproj.cpp -lSDL -lSDL_image -lSDL_gfx

---

### Post by Choad on 2006-12-09
bump!

ok i dont know what else i can tell you? i have been trying for ages to no avail, i have pretty much commented out every line to do with CDirt one at a time and still havent found the source of the error.

please someone help!

ok heres the relevant code so y'all dont have to download the whole project

```

  // Forward Declarations
  ///////////////////////

class CDirt;
class CObject;

  // Globals
  //////////

CDirt * dirt;

  // Classes
  //////////

class CObject
{
	protected:
	int ID;
	SNode * myNode;
	
	public:
	  // de/constructor
	CObject();
	~CObject();
	
	  // public functions
	virtual void Init();
	virtual void DeInit();
	virtual void Draw();
	virtual void Step();
	virtual void KeyDown();
	virtual void KeyUp();
	int GetID();
	
	  // public variables
	SDL_Rect position;
	SDL_Surface * sprite;
};

class CDirt: public CObject
{
	public:
	  // de/constructor
	CDirt();
	~CDirt();
	
	virtual void Draw();
	
	SDL_Rect spritePosition;
	bool dirt[99][99];
};

CDirt::CDirt()
{
	Init();
	sprite = spriteDirt;
	spritePosition.w = 32;
	spritePosition.h = 32;
}

CDirt::~CDirt()
{
	DeInit();
}

void CDirt::Draw()
{/*
	for (int i = myView.x/32; i <= (myView.x + myView.w)/32; i++)
	{
		for (int o = myView.y/32; o <= (myView.y + myView.h)/32; i++)
		{
			if (dirt[i][o])
			{
				spritePosition.x = ((i+o)%8)*32;
				rectTemp.x = i*32;
				rectTemp.y = o*32;
				SDL_BlitSurface(sprite, 
						&spritePosition, 
						screen, 
						&rectTemp);
			}
		}
	}*/
}

  // Main
  ///////

int main()
{
	Init();

	LoadLevel("level1.txt");
	
	dirt = new CDirt();
	
	player = new CPlayer();
	
	player->position.x = 32;
	player->position.y = 32;
	
	while (!done)
	{
		DrawScene();
		StepEvents();
		HandleInput();
	}
	
	return 0;
}
```

---

### Post by Choad on 2006-12-09
ok i might just end up killing something.... i was sure it compiled when you commented out that line. now i have no workable version!

right... how exactly do you go about debugging a c++ program? i cant keep on relying on forum people

---

### Post by Choad on 2006-12-09
woooh i finally figured it out!

---

### Post by po0f on 2006-12-09
Choad,

I looked at your project yesterday but didn't have time to comment...  You might find it a *lot* easier if you start splitting your classes into different files.  One big source file really isn't the easiest to navigate.  I would have delved deeper into your problem, but really couldn't get over having to separate everything into their own files myself.

---

### Post by Choad on 2006-12-09
> **po0f said:**
> Choad,

I looked at your project yesterday but didn't have time to comment...  You might find it a *lot* easier if you start splitting your classes into different files.  One big source file really isn't the easiest to navigate.  I would have delved deeper into your problem, but really couldn't get over having to separate everything into their own files myself.
yeah! that would make things 50 times easier... but i dont know how to do that??? (help?)

this is my first c++ project

its coming along pretty well now tho. got destructible dirt, scrolling views, animated sprites etc. and the nice thing is it runs smoothly on my **** laptop with an SiS graphics card

[[IMG]http://img120.imageshack.us/img120/7847/screenshot9ll7.th.png[/IMG]](http://img120.imageshack.us/my.php?image=screenshot9ll7.png)

---

### Post by po0f on 2006-12-09
Choad,

Oww, my head really hurts.  I've been trying to break down your big source file into multiple source files, but I've only got this so far:

```
[FONT="Courier New"]
// CObject.hpp

#ifndef COBJECT_HPP
#define COBJECT_HPP

class CObject {
public:
	CObject();
	~CObject();

	/* I think you are missing the point of constructors/destructors.  You don't need to
	 * call Init() in CObject() _or_ DeInit() in ~CObject because the ctors/dtors are
	 * automatically init and deinit functions.
	 */
	//virtual void Init();
	//virtual void DeInit();
	virtual void Draw();

	/* If you don't want to implement functions for a base class, but want to force derived
	 * classes to use the interface defined, you can declare pure-virtual functions.  They're
	 * virtual because derived classes can override them, and there pure becase in the base class,
	 * they have no implementation, so the derived class _has_ to override them, specifically
	 * for that class.
	 */
	/* Actually, I just noticed that only class CPlayer implements these functions.  The good thing
	 * about inheritance is that you can inherit from a base class, but then add more functionality
	 * to the class.  I'll leave these here, just know they really belong in CPlayer.  (Taking away
	 * pureness of function, so other derived classes don't have to override them.)  Just so you
	 * know, a pure-virtual declaration looks like:
	 *
	 *   virtual <return_type> function_name(<argument_list>) = 0;
	 */
	virtual void Step();
	virtual void KeyUp();
	virtual void KeyDown();

	/* Accessor member functions, to get at your private parts.  :)
	 * Declared const, because we don't need to change the object to just read data.
	 */
	int GetID() const;
	SDL_Rect *GetPosition() const;
	SDL_Surface *GetSprite() const;

private:
	static int IDC; // Clean up global namespace, add IDC here
	int ID;
	SNode *myNode;

	/* You want these to be private, but you don't know it yet.  ;)
	 */
	SDL_Rect *position;
	SDL_Surface *sprite;
};

#endif // COBJECT_HPP

[/FONT]
```

```
[FONT="Courier New"]
// CObject.cpp

#include "CObject.hpp"

/* This member is declared static in CObject.hpp, which means only one declaration is allowed.
 * That doesn't mean that the value can't be changed, there is just one copy of this variable lying
 * around (just like it was global), but it is private to CObject.  Since only CObjects (and derived
 * classes) need to care about this variable, make it private and static to the class.
 */
int CObject::IDC = 0;

CObject::Cobject() {
	// I actually don't know jack squat about linked lists.  :)
	myNode = new SNode;
	myNode->obj = this;
	myNode->next = NULL;
	myNode->prev = NULL;

	/* Since we're testing to see if lastObject points to anything, we can just use the variable
	 * itself as the condition, since NULL == false.  :)
	 */
	if (lastObject) {
		firstObject = myNode;
		lastObject = myNode;
	} else {
		lastObject->next = myNode;
		myNode->prev = lastObject;
		lastObject = myNode;
	}

	// ID gets the current value of IDC, then IDC is incremented. Awesome!
	ID = IDC++;

	/* I think the reason you wanted position to be public is so you can change the values.
	 * But it doesn't have to be public to change the values from inside the class.
	 */
	position.x = 0;
	position.y = 0;
	position.w = 32;
	position.h = 32;

	// Why is sprite a part of this class if it isn't used?
	sprite = NULL;
}

CObject::~CObject() {
	if (myNode == firstObject)
		firstObject = myNode->next;

	if (myNode == lastObject)
		lastObject = myNode->prev;

	// Use our new trick learned above for these if's.
	if (myNode->prev)
		myNode->prev->next = myNode->next;

	if(sprite)
		SDL_FreeSurface(sprite);
}

void CObject::Draw() {
	if (sprite) {
		if (InView(&myView, this) {
			rectTemp.x = position.x - myView.x;
			rectTemp.y = position.y - myView.y;
			SDL_BlitSurface(sprite, NULL, screen, &rectTemp);
		}
	}
}

// Simple functions don't need to be spread across 4 lines.  ;)
int CObject::GetID() const { return ID; }

SDL_Rect *CObject::GetPosition() const { return position; }

SDL_Surface *CObject::GetSprite() const { return sprite; }

[/FONT]
```

(Now I know what they mean about looking at other people's source.)

---

### Post by Choad on 2006-12-10
> **po0f said:**
> Choad,

Oww, my head really hurts.  I've been trying to break down your big source file into multiple source files, but I've only got this so far:

```
[FONT="Courier New"]
// CObject.hpp

#ifndef COBJECT_HPP
#define COBJECT_HPP

class CObject {
public:
	CObject();
	~CObject();

	/* I think you are missing the point of constructors/destructors.  You don't need to
	 * call Init() in CObject() _or_ DeInit() in ~CObject because the ctors/dtors are
	 * automatically init and deinit functions.
	 */
	//virtual void Init();
	//virtual void DeInit();
	virtual void Draw();

	/* If you don't want to implement functions for a base class, but want to force derived
	 * classes to use the interface defined, you can declare pure-virtual functions.  They're
	 * virtual because derived classes can override them, and there pure becase in the base class,
	 * they have no implementation, so the derived class _has_ to override them, specifically
	 * for that class.
	 */
	/* Actually, I just noticed that only class CPlayer implements these functions.  The good thing
	 * about inheritance is that you can inherit from a base class, but then add more functionality
	 * to the class.  I'll leave these here, just know they really belong in CPlayer.  (Taking away
	 * pureness of function, so other derived classes don't have to override them.)  Just so you
	 * know, a pure-virtual declaration looks like:
	 *
	 *   virtual <return_type> function_name(<argument_list>) = 0;
	 */
	virtual void Step();
	virtual void KeyUp();
	virtual void KeyDown();

	/* Accessor member functions, to get at your private parts.  :)
	 * Declared const, because we don't need to change the object to just read data.
	 */
	int GetID() const;
	SDL_Rect *GetPosition() const;
	SDL_Surface *GetSprite() const;

private:
	static int IDC; // Clean up global namespace, add IDC here
	int ID;
	SNode *myNode;

	/* You want these to be private, but you don't know it yet.  ;)
	 */
	SDL_Rect *position;
	SDL_Surface *sprite;
};

#endif // COBJECT_HPP

[/FONT]
```

```
[FONT="Courier New"]
// CObject.cpp

#include "CObject.hpp"

/* This member is declared static in CObject.hpp, which means only one declaration is allowed.
 * That doesn't mean that the value can't be changed, there is just one copy of this variable lying
 * around (just like it was global), but it is private to CObject.  Since only CObjects (and derived
 * classes) need to care about this variable, make it private and static to the class.
 */
int CObject::IDC = 0;

CObject::Cobject() {
	// I actually don't know jack squat about linked lists.  :)
	myNode = new SNode;
	myNode->obj = this;
	myNode->next = NULL;
	myNode->prev = NULL;

	/* Since we're testing to see if lastObject points to anything, we can just use the variable
	 * itself as the condition, since NULL == false.  :)
	 */
	if (lastObject) {
		firstObject = myNode;
		lastObject = myNode;
	} else {
		lastObject->next = myNode;
		myNode->prev = lastObject;
		lastObject = myNode;
	}

	// ID gets the current value of IDC, then IDC is incremented. Awesome!
	ID = IDC++;

	/* I think the reason you wanted position to be public is so you can change the values.
	 * But it doesn't have to be public to change the values from inside the class.
	 */
	position.x = 0;
	position.y = 0;
	position.w = 32;
	position.h = 32;

	// Why is sprite a part of this class if it isn't used?
	sprite = NULL;
}

CObject::~CObject() {
	if (myNode == firstObject)
		firstObject = myNode->next;

	if (myNode == lastObject)
		lastObject = myNode->prev;

	// Use our new trick learned above for these if's.
	if (myNode->prev)
		myNode->prev->next = myNode->next;

	if(sprite)
		SDL_FreeSurface(sprite);
}

void CObject::Draw() {
	if (sprite) {
		if (InView(&myView, this) {
			rectTemp.x = position.x - myView.x;
			rectTemp.y = position.y - myView.y;
			SDL_BlitSurface(sprite, NULL, screen, &rectTemp);
		}
	}
}

// Simple functions don't need to be spread across 4 lines.  ;)
int CObject::GetID() const { return ID; }

SDL_Rect *CObject::GetPosition() const { return position; }

SDL_Surface *CObject::GetSprite() const { return sprite; }

[/FONT]
```

(Now I know what they mean about looking at other people's source.)
wow! ok just read the first bit and

I think you are missing the point of constructors/destructors.  You don't need to call Init() in CObject() _or_ DeInit() in ~CObject because the ctors/dtors are automatically init and deinit functions.

i have Init and DeInit because de/constructors are not inherited, according to the tutorial i was reading, so instead of write the same initialisation code again and again i made a function

i will keep reading tho thx for this!

---

### Post by Choad on 2006-12-10
```
// CObject.hpp

#ifndef COBJECT_HPP
#define COBJECT_HPP

```
ok first off.... wtf?

```

class CObject {
public:
	CObject();
	~CObject();

	/* I think you are missing the point of constructors/destructors.  You don't need to
	 * call Init() in CObject() _or_ DeInit() in ~CObject because the ctors/dtors are
	 * automatically init and deinit functions.
	 */
	//virtual void Init();
	//virtual void DeInit();
	virtual void Draw();

```
already said about this
```

	/* If you don't want to implement functions for a base class, but want to force derived
	 * classes to use the interface defined, you can declare pure-virtual functions.  They're
	 * virtual because derived classes can override them, and there pure becase in the base class,
	 * they have no implementation, so the derived class _has_ to override them, specifically
	 * for that class.
	 */
	/* Actually, I just noticed that only class CPlayer implements these functions. 

```
...at the moment.

it might be helpful to tell you i am following in the footsteps of [www.gamemaker.nl](www.gamemaker.nl) which is what got me in to programming. basically, where ever i need to implement something, i do it the way mark overmars did in gamemaker. probably not the best way or most efficient, but it does work and is highly adaptable.
```
 The good thing
	 * about inheritance is that you can inherit from a base class, but then add more functionality
	 * to the class.  I'll leave these here, just know they really belong in CPlayer.  (Taking away
	 * pureness of function, so other derived classes don't have to override them.)  Just so you
	 * know, a pure-virtual declaration looks like:
	 *
	 *   virtual <return_type> function_name(<argument_list>) = 0;
	 */

```
cool! good to know
```

	virtual void Step();
	virtual void KeyUp();
	virtual void KeyDown();

	/* Accessor member functions, to get at your private parts.  :)
	 * Declared const, because we don't need to change the object to just read data.
	 */
	int GetID() const;
	SDL_Rect *GetPosition() const;
	SDL_Surface *GetSprite() const;

private:
	static int IDC; // Clean up global namespace, add IDC here
	int ID;
	SNode *myNode;

	/* You want these to be private, but you don't know it yet.  ;)
	 */
        SDL_Rect *position;
	SDL_Surface *sprite;

```
do i? because i pretty much wanted anything to be able to mess with this. these are not integral to the game engine, so it doesnt matter what has control over it... i thought i'd leave it flexible... unless you can tell me why they want to be private? i *know* that making them private will totally **** with my program as it stands
```

	
};

#endif // COBJECT_HPP
```

1 sec ill reply to the other bit....

```
// CObject.cpp

#include "CObject.hpp"

/* This member is declared static in CObject.hpp, which means only one declaration is allowed.
 * That doesn't mean that the value can't be changed, there is just one copy of this variable lying
 * around (just like it was global), but it is private to CObject.  Since only CObjects (and derived
 * classes) need to care about this variable, make it private and static to the class.
 */
int CObject::IDC = 0;

```
CObject does not have a variable IDC

IDC stands for id counter, and it is a global used to give objects a token id, then is incremented by 1
```

CObject::Cobject() {
	// I actually don't know jack squat about linked lists.  :)
	myNode = new SNode;
	myNode->obj = this;
	myNode->next = NULL;
	myNode->prev = NULL;

	/* Since we're testing to see if lastObject points to anything, we can just use the variable
	 * itself as the condition, since NULL == false.  :)
	 */

```
well then it would want to be if (!lastObject) surely?
```

	if (lastObject) {
		firstObject = myNode;
		lastObject = myNode;
	} else {
		lastObject->next = myNode;
		myNode->prev = lastObject;
		lastObject = myNode;
	}

	// ID gets the current value of IDC, then IDC is incremented. Awesome!
	ID = IDC++;

```
funky!
```

	/* I think the reason you wanted position to be public is so you can change the values.
	 * But it doesn't have to be public to change the values from inside the class.
	 */

	position.x = 0;
	position.y = 0;
	position.w = 32;
	position.h = 32;

	// Why is sprite a part of this class if it isn't used?
	sprite = NULL;
}

```
because most derived classes WILL have a sprite
```

CObject::~CObject() {
	if (myNode == firstObject)
		firstObject = myNode->next;

	if (myNode == lastObject)
		lastObject = myNode->prev;

	// Use our new trick learned above for these if's.
	if (myNode->prev)
		myNode->prev->next = myNode->next;

	if(sprite)
		SDL_FreeSurface(sprite);

```
this bit here i noticed is actually very bad! i should really send you my latest source file because this is old if this is not changed. i just commented it out with a big warning
```

  // this would be bad
	/*if (sprite != NULL)
	  SDL_FreeSurface(sprite);*/

```
lol
```

}

void CObject::Draw() {
	if (sprite) {
		if (InView(&myView, this) {
			rectTemp.x = position.x - myView.x;
			rectTemp.y = position.y - myView.y;
			SDL_BlitSurface(sprite, NULL, screen, &rectTemp);
		}
	}
}

// Simple functions don't need to be spread across 4 lines.  ;)
int CObject::GetID() const { return ID; }

```
yeah i suppose. i still prefer to have everything uniform. i suppose i can make an exception for exceptionally small functions :)
```

SDL_Rect *CObject::GetPosition() const { return position; }

SDL_Surface *CObject::GetSprite() const { return sprite; }
```


well..... after all that im not exactly sure what we have ahcieved! :S

thanks alot tho, that must have taken u ages!

attached is the latest version. i wont do any more till it is separated in to different files i dont think :)

---

### Post by Choad on 2006-12-10
ok, i lied, i added something more. just a boolean variable that sets whether an object should animate it's sprite automatically or not

so for the gems, i have made a whole load of different gems in 1 sprite resource, but i dont want it to animate because that would just look wierd, i want it to stick to a randomly assigned frame

also, if you wanted to help me make this you are more than welcome. i am basically just making this to teach myself c++ and sdl, and hopefully when its done, release it under the gpl and get it included with ubuntu

that would be teh awesomes. i would be a propper oss dev hahaha

the game is trying to be a clone of this [http://en.wikipedia.org/wiki/Boulder_Dash](http://en.wikipedia.org/wiki/Boulder_Dash)

but will be cooler!

---

