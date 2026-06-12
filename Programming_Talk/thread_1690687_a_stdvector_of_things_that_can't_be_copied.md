---
title: "a std::vector of things that can't be copied?"
date: 2011-02-18
forum: Programming Talk
---

### Post by worksofcraft on 2011-02-18
I wanted to fill a C++ vector with things that contained a constant field and eventually it became a vector of things
that can't be copied.. but just can't work out how :confused:

The following won't compile :(

[php]

// g++ constmember.cpp
#include <vector>

struct mcu_component {
	mcu_component(char iDent): iD(iDent) { }
private:
	const char iD;
	// other members elided for brevity

	// preclude copy
	mcu_component(const mcu_component &);
	mcu_component & operator= (const mcu_component &);
};

int main() {
	std::vector<mcu_component> aVector;
	aVector.push_back(mcu_component('G'));
	return 0;
}
[/php]

---

### Post by MadCow108 on 2011-02-18
elements in vectors must have copy semantics so you can't make the copy functions private.
This is required for many of the operations on vectors e.g. erasing from the front, sorting etc.
additionally you have to write your own assignment function which does not change the const member.

if that is not what you want you must remove the const or use (smart) pointers to the objects in the vector

btw my random c++x0 fact I always tend to give in your posts:
this "hidden" copy semantics problem was intended to be "solved" by concepts:
[http://en.wikipedia.org/wiki/Concepts_(C%2B%2B](http://en.wikipedia.org/wiki/Concepts_(C%2B%2B))
but this feature got removed a short while ago (in timescale of the standard) as it got too complex and there was not working implementation in wide use.

---

### Post by cgroza on 2011-02-18
This should not be private, it needs to be accessed by the vector.
```

mcu_component(const mcu_component &); 
```

---

### Post by worksofcraft on 2011-02-18
> **MadCow108 said:**
> elements in vectors must have copy semantics so you can't make the copy functions private.
This is required for many of the operations on vectors e.g. erasing from the front, sorting etc.
additionally you have to write your own assignment function which does not change the const member.

if that is not what you want you must remove the const or use (smart) pointers to the objects in the vector

btw my random c++x0 fact I always tend to give in your posts:
this "hidden" copy semantics problem was intended to be "solved" by concepts:
[http://en.wikipedia.org/wiki/Concepts_(C%2B%2B](http://en.wikipedia.org/wiki/Concepts_(C%2B%2B))
but this feature got removed a short while ago (in timescale of the standard) as it got too complex and there was not working implementation in wide use.

OK thanks for that info, both of you :)

In that case I decided std::vector is not suitable: It's quite important that once I put these things into the vector they don't get moved about or assigned to in this application and since it is being used in an mpeg decoder I want minimal overhead.

So evidently it's back to an array because I do need to index them. Thus the question becomes how to construct an array of things that need assorted parameters for their constructor :confused:

I'm kind of thinking about placement new... IDK anyone have suggestions?

---

### Post by MadCow108 on 2011-02-18
instead of going low level, is maybe a const vector<T> enough?
else I don't really see the the problem. A vector is easy enough to understand where the copies are.

but maybe you find something useful in this post:
[http://ubuntuforums.org/showthread.php?t=1687888](http://ubuntuforums.org/showthread.php?t=1687888)

its about using the features of the <memory> header, uninitialized array allocation and copy, placement new, ...
but this gets a bit tricky at times, I needed a bunch of edits to get it (probably) right ;)

---

### Post by worksofcraft on 2011-02-18
> **MadCow108 said:**
> instead of going low level, is maybe a const vector<T> enough?
else I don't really see the the problem. A vector is easy enough to understand where the copies are.

but maybe you find something useful in this post:
[http://ubuntuforums.org/showthread.php?t=1687888](http://ubuntuforums.org/showthread.php?t=1687888)

its about using the features of the <memory> header, uninitialized array allocation and copy, placement new, ...
but this gets a bit tricky at times, I needed a bunch of edits to get it (probably) right ;)

Hum.. thanks, but no they are not compile time initializers.
The mpeg file provides the details of each luminance/color/transparency component that it encodes into it's minimum coded units (mcu)... then I want to create some kind of array of these components to represent the mcu because of chroma sub sampling... z0mg I know I could do it all with type casts and macros like other mpeg decoders do :( but I just want to push the limits on how useful all these advanced language constructs actually are in practice :shock:

---

### Post by worksofcraft on 2011-02-19
Incidentally, here is how it can be done with arrays and placement new. What I really DON'T like about this is the fact it actually has to construct dummy ones and then overwrite them without ever destructing the dummys :shock:
[php]

// g++ constmember.cpp
#include <cstdio>
#include <new> //for placement new

struct mcu_component {
	mcu_component(): iD(0) {} // create an empty dummy
	// ^it is intention these get overwritten!

	mcu_component(char iDent): iD(iDent) { 
		printf("constructing %p, iD=%c\n", this, iD);
	}
	~mcu_component() {
		printf("destructing %p, iD=%c\n", this, iD);
	}
private:
	const char iD;
	char dummy_load[15];
	// other members elided for brevity

	// preclude copy
	mcu_component(const mcu_component &);
	mcu_component & operator= (const mcu_component &);
};

int main() {
	mcu_component * qComponents = new mcu_component[4];
	for (int i = 0; i < 4; ++i) {
		// now construct the real ones over the top of the dummys
		new(&qComponents[i]) mcu_component('A'+i);
	}
	// delete the array the usual way
	delete [] qComponents;

	return !printf("and it didn't even crash yet!\n");
}
[/php]

Meh... if anyone knows a better way I be keen to hear it... so to recap, the objective is to create an indexable aggregate (vector, array, whatever) of objects that cannot be copied or moved elsewhere (because I'm creating and processing references and pointers to them). They also have to be able to contain constant member fields.:popcorn:

---

### Post by slavik on 2011-02-19
really? why doesn't an array work?

what about realloc calls?

---

### Post by worksofcraft on 2011-02-19
> **slavik said:**
> really? why doesn't an array work?

what about realloc calls?

The size of my array is not known until I process the data stream headers that say how many components they have in their units, so it can't be statically allocated. However once that is known I have no need to change the number of these instances that I need, but meanwhile a constructor that takes no parameters is to be called on each array element. Alas then it doesn't construct the right values for the constant members of those objects...

However the BIG advantage of an array over a vector is IMO that I can preclude copying of the instances. That way they are guaranteed not to be unexpectedly moved or reallocated once I'm working with references and pointers to them further down.

However I decided to use a separate initialize method instead of placement new and even "const_cast" is probably over kill so I simply didn't make them const and used accessors to access them :)

p.s. here is modified example shows perhaps better what I'm trying to achieve by using argc and argv of main
[php]
// g++ constmember.cpp
#include <cstdio>

struct mcu_component {
	mcu_component(): iD(0), pText("error") {} // create an empty dummy

	void init(char iDent, const char *pT) {
		const_cast<char &> (iD) = iDent;
		const_cast<const char * &> (pText) = pT;
		printf("initialized %p, iD=%d, Text=%s\n", this, iD, pText);
	}
	~mcu_component() {
		printf("destructing %p, iD=%d, Text=%s\n", this, iD, pText);
	}
private:
	const char iD;
	const char * const pText;
	// other members elided for brevity

	// preclude copy
	mcu_component(const mcu_component &);
	mcu_component & operator= (const mcu_component &);
};

int main(int argc, char *argv[]) {
	mcu_component * qComponents = new mcu_component[argc];
	for (int i = 0; i < argc; ++i) {
		qComponents[i].init(i, *argv++);
	}
	// delete the array the usual way
	delete [] qComponents;

	return !printf("and it didn't even crash yet!\n");
}
[/php]

---

### Post by slavik on 2011-02-21
WHY?!

Why would someone move your data around? I really don't understand this itch you have about this. If you don't want data to move, just don't move it. C++ allows dynamic allocation of arrays, as in:

```

...
cin>>somevar;
int myarr[somevar];
...

```

---

### Post by worksofcraft on 2011-02-21
> **slavik said:**
> WHY?!

Why would someone move your data around? I really don't understand this itch you have about this. If you don't want data to move, just don't move it. C++ allows dynamic allocation of arrays, as in:

```

...
cin>>somevar;
int myarr[somevar];
...

```


[php]
// g++ moved.cpp
#include <cstdio>
#include <vector>

using namespace std;


int iCount = 0;

struct thingy {
	int id;
	thingy(): id(++iCount) {}
};

vector<thingy> gVector;
	
int main(int argc, char *argv[], char *envp[]) {
	gVector.push_back(thingy());
	thingy *pThing1 = &gVector.front();
	printf("front thingy is %d at %p\n", pThing1->id, pThing1);
	// conceptually this doesn't do anything to Thing1
	while (&gVector.front() == pThing1) gVector.push_back(thingy());

	printf("front thingy is now %d at %p\n", gVector.front().id, &gVector.front());
	printf("but pThing1 still points to %d at %p\n", pThing1->id, pThing1);
}
[/php]

```

$ ./a.out
front thingy is 1 at 0x164c010
front thingy is now 1 at 0x164c030
but pThing1 points to 0 at 0x164c010

```

if you are processing a data structure using references and/or pointers and elsewhere adding things into the vector that contains it, the object referred to can unpredictably be copied and moved elsewhere in memory. Thus your pointer is left dangling without warning or you may simply be processing duplicate entities when you thought they were the same thing.

---

### Post by slavik on 2011-02-21
But above you say that once you know the number of object, you don't need to change anything.

Next thing: Do not pass references to objects. Implement a copy constructor for the objects and pass the whole object.

The final idea: Pipeline your code, so that you are adding things and then processing them in a separate step.

---

### Post by forrestcupp on 2011-02-21
Can't you just place the vector inside a struct or class as a private member and have a simple method to pass data into that private vector?

---

### Post by dwhitney67 on 2011-02-21
> **worksofcraft said:**
> Incidentally, here is how it can be done with arrays and placement new.
Why don't you just declare a vector that contains pointers to the objects that you allocate.  Or better yet, a smart-pointer.

```

class Foo
{
public:
   Foo() {}
private:
   Foo(const Foo*);
   Foo& operator(const Foo&);
};

int main()
{
   std::vector<Foo*> aVec;
   aVec.push_back(new Foo);
}

// or

int main()
{
   std::vector<boost::shared_ptr<Foo> > aVec;
   aVec.push_back(boost::shared_ptr<Foo>(new Foo));
}

```

To avoid having any of your other code copy, manipulate, or otherwise "infect" the contents of the vector, just write good code.

---

### Post by worksofcraft on 2011-02-21
> **dwhitney67 said:**
> Why don't you just declare a vector that contains pointers to the objects that you allocate.  Or better yet, a smart-pointer.

```

class Foo
{
public:
   Foo() {}
private:
   Foo(const Foo*);
   Foo& operator(const Foo&);
};

int main()
{
   std::vector<Foo*> aVec;
   aVec.push_back(new Foo);
}

// or

int main()
{
   std::vector<boost::shared_ptr<Foo> > aVec;
   aVec.push_back(boost::shared_ptr<Foo>(new Foo));
}

```

To avoid having any of your other code copy, manipulate, or otherwise "infect" the contents of the vector, just write good code.

I don't think there is anything "good" about a vector full of shared pointers when a simple array does exactly what is needed. You'll be telling me to program it all in Java next :confused:

Declaring some class member as "const" and others (e.g. my copy constructors) as "private" is all part of expressing appropriate properties of a class. I was just surprised I couldn't put such objects in a vector.

---

### Post by worksofcraft on 2011-02-21
... anyway I put the two strategies to the test:
```

$ g++ -std=c++0x -O3 sharedptr.cpp
$ ./a.out
memory overhead: sizeof(shared_ptr)=16, sizeof(void *)=8
vector check=56153, time=8.210000 seconds
array check=56153, time=0.560000 seconds
exits normally

```

So implementation with an array is about 1466 % times faster :popcorn:

The code for those interested:
[php]
// g++ -std=c++0x -O3 sharedptr.cpp
#include <cstdio>
#include <vector>
#include <cstdlib>
#include <ctime>
#include <tr1/memory>

using namespace std;

enum { cRepeats = 10000, cLength = 4000 };

struct foo_struct {
	const unsigned short iFoo;
	// this is the constructor I wanted
	foo_struct(unsigned short me): iFoo(me) {}

	// in the array I need to separate constructor and initialization :/
	void init(unsigned short me) { const_cast<unsigned short &> (iFoo) = me; }
	foo_struct(): iFoo(0) {}
};

unsigned short test_shared_ptr() {
	vector<shared_ptr<foo_struct> > aFooContainer;

	for (int i = 0; i < cLength; i++) aFooContainer.push_back(
		shared_ptr<foo_struct> (new foo_struct(rand()) )
	);

	unsigned short iCheckSum = 0;
	for (auto iT = aFooContainer.begin(); iT != aFooContainer.end(); ++iT) {
		iCheckSum += (*iT)->iFoo;
	}
	return iCheckSum;
}

unsigned short test_array() {
	foo_struct aFooContainer[cLength];

	for (int i = 0; i < cLength; i++) aFooContainer[i].init(rand());

	unsigned short iCheckSum = 0;
	for (auto iT = aFooContainer; iT != &aFooContainer[cLength]; ++iT) {
		iCheckSum += iT->iFoo;
	}
	return iCheckSum;
}
			
int main() {
	// memory footprint
	printf("memory overhead: sizeof(shared_ptr)=%zu, sizeof(void *)=%zu\n",
		sizeof(shared_ptr<foo_struct>), sizeof(void *)
	);

	// performance
	clock_t iStart; // for tracking processor time
	unsigned short iCheckSum; // to make sure we doing same thing

	iCheckSum = 0;
	iStart = clock();
	srand(2011);
	for (int i = 0; i < cRepeats; ++i) iCheckSum += test_shared_ptr();
	printf("vector check=%u, time=%f seconds\n", iCheckSum, float(clock()-iStart)/CLOCKS_PER_SEC);

	iCheckSum = 0;
	iStart = clock();
	srand(2011);
	for (int i = 0; i < cRepeats; ++i) iCheckSum += test_array();
	printf("array check=%u, time=%f seconds\n", iCheckSum, float(clock()-iStart)/CLOCKS_PER_SEC);

	return !printf("exits normally\n");
}
[/php]

---

