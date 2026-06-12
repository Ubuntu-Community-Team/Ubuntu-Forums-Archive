---
title: "[C++] How to compile this?"
date: 2006-06-25
forum: Programming Talk
---

### Post by Laterix on 2006-06-25
Hi, 

It's me again and still learning C++. I came up with this problem recently and I can't think of any solutions. So, I have something like this UML (not a good design, but let's not talk about that now).

[IMG]http://personal.inet.fi/cool/laterix/example.png[/IMG]

So, I have two classes and both have pointers to each other as class attributes. How am I supposed to compile this or is it even possible? If i include ClassA before ClassB then the compiler complains that ClassB is not known type when it sees type ClassB pointer declaration in ClassA. And if I include ClassB before ClassA samething happends, of course.

---

### Post by asimon on 2006-06-25
Use a forward declaration.

```
class B;   // forward declaration

class A {
        B *ptrB;
};

class B {
        A *prtA;
};

```

---

### Post by glinsvad on 2006-06-25
Actually you will have to divide the code into five parts. The three suggested by asimon, and the separate declarations of the member functions later on.

This code should demonstrate it:
```

#include <iostream>
using namespace std;

// Forward declaration of second class
class ClassB;

// Prototype of first class
class ClassA
	{
	public:
	ClassA(void) : pCB(NULL) { }
	ClassA(ClassB *_pCB) : pCB(_pCB) { }
	~ClassA() { }

	ClassB* GetBuddy(void); 
	void SetBuddy(ClassB *_pCB);

	const char* GetText(void) const { return "This is ClassA alright!"; }

	private:
	ClassB *pCB;
	};

// Prototype of second class
class ClassB
	{
	public:
	ClassB(void) : pCA(NULL) { }
	ClassB(ClassA *_pCA) : pCA(_pCA) { }
	~ClassB() { }

	ClassA* GetBuddy(void);
	void SetBuddy(ClassA *_pCA);

	const char* GetText(void) const { return "Then this must be ClassB."; }

	private:
	ClassA *pCA;
	};

// Member functions for first class
ClassB* ClassA::GetBuddy(void) { if(!pCB) pCB = new ClassB(this); return pCB; }
void ClassA::SetBuddy(ClassB *_pCB) { if(pCB) delete pCB; pCB = _pCB; }

// Member functions for second class
ClassA* ClassB::GetBuddy(void)  { if(!pCA) pCA = new ClassA(this); return pCA; }
void ClassB::SetBuddy(ClassA *_pCA) { if(pCA) delete pCA; pCA = _pCA; }


int main(int nArgs,char **szArgs)
{

ClassA *pCA = new ClassA();

ClassB *pCB = pCA->GetBuddy();

pCB->SetBuddy(pCA);

cout << "First class says:\t\"" <<pCA->GetText() <<"\"" <<endl;
cout << "It's buddy says:\t\"" <<(pCA->GetBuddy())->GetText() <<"\"" <<endl;
cout <<endl;
cout << "Second class says:\t\"" <<pCB->GetText() <<"\"" <<endl;
cout << "It's buddy says:\t\"" <<(pCB->GetBuddy())->GetText() <<"\"" <<endl;

delete pCA;
delete pCB;

return 0;
}

```

For some reason you cannot specify the actual code of the member functions before the "skeleton" of the two classes are defined as prototypes (otherwise the compiler only knows that the classes exist, but not what they contain/do to each other).

Man, this was pretty educational ;)

---

### Post by Laterix on 2006-06-25
[QUOTE=glinsvad]
Man, this was pretty educational ;)
[/QUOTE]
This was very educational for me! Thanks both of you. And it's such a simple answer after all. It just didn't pop in to my head.

---

