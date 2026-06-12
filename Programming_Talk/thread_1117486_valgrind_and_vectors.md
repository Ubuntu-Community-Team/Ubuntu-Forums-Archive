---
title: "valgrind and vectors"
date: 2009-04-06
forum: Programming Talk
---

### Post by tneva82 on 2009-04-06
Getting whole bunch of invalid read/write size 4 error messages for following line. Not just one but tons for every one such call completely flooding error lines. What's up with that?

vector<myClass*> myVector;

int objectCount=someNumber;

myVector.resize(objectCount);

the resize is where valgrind reports those invalid read/write size errors. What's up with that? Valgrind having problems with vector? Me doing something wrong here? I can't figure out what the bloody heck is wrong with simple resize of vector that hasn't even been used yet?

---

### Post by Arndt on 2009-04-06
> **tneva82 said:**
> Getting whole bunch of invalid read/write size 4 error messages for following line. Not just one but tons for every one such call completely flooding error lines. What's up with that?

vector<myClass*> myVector;

int objectCount=someNumber;

myVector.resize(objectCount);

the resize is where valgrind reports those invalid read/write size errors. What's up with that? Valgrind having problems with vector? Me doing something wrong here? I can't figure out what the bloody heck is wrong with simple resize of vector that hasn't even been used yet?

Has it even been set yet? What if you do

```
static vector<myClass*> myVector;
```

?

---

### Post by tneva82 on 2009-04-06
> **Arndt said:**
> Has it even been set yet? What if you do

```
static vector<myClass*> myVector;
```

?

Hmm. Not sure if I want it to be static. If it's static there's just one vector for that class containing that vector shared by all the instances of that class right? Each instance should have their own unique myVector. Would change logic of program a "bit" if there's shared myVector.

---

### Post by WakkiTabakki on 2009-04-06
It's probably because you have allocated a reference to the vector-object, but you have not allocated the actual vector-object! You are essentially trying to ask a null-reference to do something....

Assuming its c++:
```

vector<myClass*> myVector; // This just allocates a pointer to a vector object

myVector = new vector<myClass*>(); // This would allocate the actual object,. and ofcourse assign the objects address to the pointer...

int objectCount=someNumber;

// Now, you can call the method of the object (without line 2 above, there is no object to receive the call!
myVector.resize(objectCount);
```


I think this is what Arndt meant with "Has it even been set yet?", also the actual output from valgrind would've been interesting to see....


/N

---

### Post by Arndt on 2009-04-06
> **tneva82 said:**
> Hmm. Not sure if I want it to be static. If it's static there's just one vector for that class containing that vector shared by all the instances of that class right? Each instance should have their own unique myVector. Would change logic of program a "bit" if there's shared myVector.

Yes, I'm not suggesting that it's the correct solution, only wondering if it will make valgrind happy, as a step towards understanding the problem. Sorry for being too terse.

---

### Post by tneva82 on 2009-04-06
> **WakkiTabakki said:**
> ```

vector<myClass*> myVector; // This just allocates a pointer to a vector object

myVector = new vector<myClass*>(); // This would allocate the actual object,. and ofcourse assign the objects address to the pointer...

```



Well here's what I attempted:
```

client.h:

class client {
private:
  vector<object3d*> partMasterList;
};

clientBasic.cpp:

client::setPartList() {
  partMasterList = new vector<object3d*>();   
}

```

and here's what compiler gave me:

```

g++ src/clientBasic.cpp -g -c -o obj/clientBasic.o -lGL -lSDL -lGLU -lSDL_net `sdl-config --cflags` `pkg-config --cflags ftgl`
src/clientBasic.cpp: In member function &#8216;void client::setPartList(const char*)&#8217;:
src/clientBasic.cpp:213: error: no match for &#8216;operator=&#8217; in &#8216;((client*)this)->client::partMasterList = (((std::vector<object3d*, std::allocator<object3d*> >*)operator new(12u)), (<statement>, <anonymous>))&#8217;
/usr/include/c++/4.3/bits/vector.tcc:144: note: candidates are: std::vector<_Tp, _Alloc>& std::vector<_Tp, _Alloc>::operator=(const std::vector<_Tp, _Alloc>&) [with _Tp = object3d*, _Alloc = std::allocator<object3d*>]
make: *** [obj/clientBasic.o] Error 1

```

Can you even call new to non-pointer variables like in that vector allocator? I thought that was for dynamic memory allocation which would require pointers which myVector isn't though might be wrong.

Note that object3d has constructor which doesn't take parameters(though I only use one with parameters myself).

Oh and totally unrelated but have to vent a bit: STUPID WAVEFRONT! You have all the letters available and yet have to put 2 different formats to one letter in .obj file? Gee. Wondered why there's odd outputs in my converter which turns bunch of .obj files to own file format(that gets rid of few redundant data which previous files from animation gave me already and packs full animation to one file. Nothing fancy but just bit of restructuring of data to be more suitable for my needs). Well I looked at .obj file more closely and sure enough after whole bunch of f x/x/x x/x/x x/x/x lines there was f x x line. Gee. What the heck is that doing there? Now I need to figure out how to filter those ones out. No wonder output was all weird...Couldn't they have implemented line(I presume that's line and numbers are vertex and vertex) to be under different letter like l? Would sure make things easier!

(of course I COULD just edit manually those offending lines but 2x49+4x29 lines to be removed across LARGE files...Uhhuh. And this for simple objects. Not good. More preferably converter should do that thing automaticly).

Edit: And elsewhere. How on earth can one get double free or corruption error message when deleting non-NULL pointer?

```

object3d::~object3d() {
  if(myFrames!=NULL) {
    for(int i=0;i<frameCount;i++) {
      if(myFrames!=NULL) {
	printf("myFrames isn't NULL!\n");
      }
      if(myFrames[i].vertexTable != NULL) {
	printf("vertex table isn't NULL!\n");
      }
      if(myFrames[i].vertexTable != NULL) delete[] myFrames[i].vertexTable;
      if(myFrames[i].normalTable != NULL) delete[] myFrames[i].normalTable;
      if(myFrames[i].normalIndexes != NULL) delete[] myFrames[i].normalIndexes;
    }

    if(myFrames!=NULL) delete[] myFrames;
    if(myPolygons!=NULL) delete[] myPolygons;
    if(uMapTable!=NULL) delete[] uMapTable;
    if(vMapTable!=NULL) delete[] vMapTable;
  }
}
```

Goes haywire on trying to delete vertexTable. myFrames is frame *myFrames; and frame is:

```

struct frame {
  vertex *vertexTable;
  normalVector *normalTable;
  int *normalIndexes;
  int normalCount;
};

```

(vertex is just struct with 3 float values).

Only one place in code where object3d classes gets destroyed(destructor of client which loops through vector containing these objects deleting them if not NULL) so there shouldn't be any rogue destructor calls as far as I can tell. And unless I'm mistaken those if clauses should prevent any attempt to delete NULL pointers.

Even more weird is that other section of code that works pretty much identically works...Go figure. Variable names change and location of functions change but that's it.

edit: Found post in forum which suggested typing in console before running:

export MALLOC_CHECK_=0

and sure enough no crash then. Okay so anything I can do codewise to prevent this? Or do I have to wrap executable into script to ensure that's run before running? What's causing this that above prevents it? Is it just hiding symptoms? What's going on here?

---

### Post by Zugzwang on 2009-04-06
> **tneva82 said:**
> Getting whole bunch of invalid read/write size 4 error messages for following line. Not just one but tons for every one such call completely flooding error lines. What's up with that?

vector<myClass*> myVector;

int objectCount=someNumber;

myVector.resize(objectCount);

the resize is where valgrind reports those invalid read/write size errors. What's up with that? Valgrind having problems with vector? Me doing something wrong here? I can't figure out what the bloody heck is wrong with simple resize of vector that hasn't even been used yet?

I don't think that that's the problem. Here is an example program that works well:

[PHP]
#include <vector>

using namespace std;

class myClass {
	int h;
	int j;
};


int main() {
	vector<myClass*> myVector;

	int objectCount=100000;

	myVector.resize(objectCount);
}
[/PHP]

The reason why the code in your last post did not work is also quite simple: You tries to assign a pointer to a vector to a vector object. Drop the "new" and it should at least compile (you also might have to drop the "()" after the "vector<object3d*>").

---

### Post by dwhitney67 on 2009-04-06
> **WakkiTabakki said:**
> It's probably because you have allocated a reference to the vector-object, but you have not allocated the actual vector-object! You are essentially trying to ask a null-reference to do something....

Assuming its c++:
```

vector<myClass*> myVector; // This just allocates a pointer to a vector object

myVector = new vector<myClass*>(); // This would allocate the actual object,. and ofcourse assign the objects address to the pointer...

int objectCount=someNumber;

// Now, you can call the method of the object (without line 2 above, there is no object to receive the call!
myVector.resize(objectCount);
```


I think this is what Arndt meant with "Has it even been set yet?", also the actual output from valgrind would've been interesting to see....


/N

-1.

The vector is not a pointer, and thus does not need to be allocated.  The vector will *contain* pointers.

---

### Post by eye208 on 2009-04-06
> **tneva82 said:**
> How on earth can one get double free or corruption error message when deleting non-NULL pointer?
It happens when a pointer is not NULL _and_ not pointing to a valid heap block. Check your pointer initialization code.

Or, even better, use smart pointers and forget about deallocation. Oh well, I must have said that a dozen times already...

---

### Post by Sockerdrickan on 2009-04-06
maybe valgrind is telling you that the contents (the pointers) are being lost or something when the vector is resized, try other methods like insert and push back

---

### Post by dwhitney67 on 2009-04-06
The "double free" does imply that the object was previously deleted.  When an pointer to an object is used to free the object, the pointer is not implicitly set to null (0).  The application must do that manually.

When using delete, a check for null is not required.

Here's some simple code that takes care of freeing the vector's contents:
```

#include <vector>
#include <cassert>


struct Foo
{
  Foo()
    : value1(new int[100]),
      value2(0)
  {
  }

  ~Foo()
  {
    delete [] value1;
  }

  int* value1;   // perhaps a vector should be used here
  int  value2;
};


int main()
{
  typedef std::vector<Foo*> FooVec;

  FooVec fvec;
  int    fcnt = 0;

  fvec.resize(10);

  assert(fvec.size() == 10);

  fvec[ fcnt++ ] = new Foo;
  fvec[ fcnt++ ] = new Foo;
  fvec[ fcnt++ ] = new Foo;
  fvec[ fcnt++ ] = new Foo;

  assert(fcnt == 4);

  // Using fcnt in the conditional is not necessary, but done in an effort to reduce
  // the number of iterations performed.  Also, we want fcnt to be zero (not less) if,
  // and this is the case here, the vector has a different size than fcnt.
  // Anyhow, there are a dozen and half ways to 'skin the cat', and this is just one
  // of them.
  for (FooVec::iterator it = fvec.begin(); it != fvec.end() && fcnt > 0; ++it, --fcnt)
  {
    delete *it;
  }

  assert(fcnt == 0);
  assert(fvec.size() == 10);
}

```

---

### Post by tneva82 on 2009-04-06
[QUOTE=eye208;7022463]It happens when a pointer is not NULL _and_ not pointing to a valid heap block. Check your pointer initialization code./QUOTE]

myFrames[i].vertexTable=new vertex[vertexCount];

That's the allocation part.

---

### Post by tneva82 on 2009-04-06
> **Tux0r said:**
> maybe valgrind is telling you that the contents (the pointers) are being lost or something when the vector is resized, try other methods like insert and push back

I don't think that solves it. Afterall vector  is initialised with size X. If push back causes it to go larger(very likely) doesn't it do resize internally anyway thus causing the error again?

However something that occured to me. Does vector do any COPYING inside and could lack of copy constructor be causing these issues? Since I don't need copy constructor myself haven't done it but does vector class require it for proper working?

---

### Post by dwhitney67 on 2009-04-06
> **tneva82 said:**
> I don't think that solves it. Afterall vector  is initialised with size X. If push back causes it to go larger(very likely) doesn't it do resize internally anyway thus causing the error again?

However something that occured to me. Does vector do any COPYING inside and could lack of copy constructor be causing these issues? Since I don't need copy constructor myself haven't done it but does vector class require it for proper working?

You are storing pointers (4-byte address values), so no, you do not need to worry about what the vector does internally wrt copying.

Clean up your code, and look for a (simple) mistake.  I do not see in plausible reason why object3d is deleting member data of struct frame.  The struct should have a constructor and a destructor to manage it's own resources.

P.S.  One of the things that becomes fairly obvious after programming in C++ for a while, is that the need to define/use arrays is moot, considering that there are STL containers to choose from that help manage the storage of data.  Your struct frame (which would be better if named "Frame"), should probably use a vector instead of a C-style array to hold the data.

---

### Post by eye208 on 2009-04-06
> **tneva82 said:**
> However something that occured to me. Does vector do any COPYING inside and could lack of copy constructor be causing these issues? Since I don't need copy constructor myself haven't done it but does vector class require it for proper working?
Yes. Copy constructor and assignment operator must be implemented to perform a "deep" copy (i.e. including all objects referenced by raw pointers). Otherwise the object cannot be stored in a STL container, because any reallocation will result in destructor calls (and therefore multiple delete calls on the pointers).

Alternatively you can implement reference counting for each pointer. Again, this is where smart pointers come in handy. Boost's shared_ptr and shared_array will perform these tasks automatically.

---

### Post by tneva82 on 2009-04-06
> **dwhitney67 said:**
>   The struct should have a constructor and a destructor to manage it's own resources.

Hum that's of course possible. The struct is just container for that class though. Bit easier to manage those variables through struct than having array of arrays. Just bit of internal containers to make the code easier to read.

> Your struct frame (which would be better if named "Frame"), should probably use a vector instead of a C-style array to hold the data.

Why though? Those structs don't change size ever and could be replaced just as well by reqular arrays except this way it's bit cleaner than arrays of arrays. Also can vector contain multiple DIFFERENT types of values? Frame structure contains 3 arrays(2 struct arrays and int array) and int value inside it. 

Of course I could solve that by having 4 vectors, one for each separate data type, but sure seems messy.

So how you would turn this:

```
struct frame {
  vertex *vertexTable; //vertex contains 3 float values
  normalVector *normalTable; // ditto. Named same just for clarity purpose
  int *normalIndexes;
  int normalCount;
};
```

into vector? Yeah vector of classes could do it but class seems like overkill for thing that's supposed to just contain information for quick access. How much extra memory usage there's with class(with it's accompanying functions) over structures anyway? And does it slow program to get variables via get methods(and if data is public then in the end what difference does it make wether to use class or struct except possible extra memory usage?).

---

### Post by tneva82 on 2009-04-06
> **eye208 said:**
> Yes. Copy constructor and assignment operator must be implemented to perform a "deep" copy (i.e. including all objects referenced by raw pointers). Otherwise the object cannot be stored in a STL container, because any reallocation will result in destructor calls (and therefore multiple delete calls on the pointers).

Okay so issue solved then pretty much. Copy constructor implemented now for object3d, now another one to character part and character.

Live and learn.

Edit: Gah. Bit more to do than I thought. Come to think of I'm using vectors quite a bit so there's more copy constructors to build than I thought.

I presume same goes for list then?

Guess I know what I'll be doing tomorrow then ;-) (that and solve why on earth only first object is used rather than all 4, one for different parts. And alter .xof format bit more. Seems I need to store x, y and z offsets for each characterpart so I can move the camera correctly before drawing the part least they all get drawn to same space(NOT right!). But atleast I have finally got object drawn. Huzah!).

---

### Post by dwhitney67 on 2009-04-06
```

struct Frame
{
  Frame(const size_t vsize, const size_t nvsize, const size_t isize)
    : vertexTable(new Vertex[vsize]),
      normalTable(new NormalVector[nvsize]),
      normalIndexes(new int[isize]),
      normalCount(0),
      vsize(vsize),
      nvsize(nvsize),
      isize(isize)
  {
  }

  Frame(const Frame& other)
    : vertexTable(new Vertex[other.vsize]),
      normalTable(new NormalVector[other.nvsize]),
      normalIndexes(new int[other.isize]),
      normalCount(other.normalCount),
      vsize(other.vsize),
      nvsize(other.nvsize),
      isize(other.isize)
  {
    memcpy(vertexTable, other.vertexTable, sizeof(Vertex) * vsize);
    ...
  }

  ~Frame()
  {
    delete [] vertexTable;
    delete [] normalTable;
    delete [] normalIndexes;
  }

  Vertex*       vertexTable;
  NormalVector* normalTable;
  int*          normalIndexes;
  int           normalCount;
  size_t        vsize;
  size_t        nvsize;
  size_t        isize;
};

```

OR

```

struct Frame
{
  std::vector<Vertex>       vertexTable;
  std::vector<NormalVector> normalTable;
  std::vector<int>          normalIndexes;
  int                       normalCount;      // needed???
};

```

---

### Post by eye208 on 2009-04-07
> **tneva82 said:**
> Yeah vector of classes could do it but class seems like overkill for thing that's supposed to just contain information for quick access. How much extra memory usage there's with class(with it's accompanying functions) over structures anyway? And does it slow program to get variables via get methods(and if data is public then in the end what difference does it make wether to use class or struct except possible extra memory usage?).
Classes and structs are the same thing. The only difference is that class members are private by default, struct members are public by default. But you can make struct members private just as you can make class members public (or protected). Both classes and structs can (and should) have methods to work on their contents. A method is nothing but a function with a hidden parameter "this" to access the class/struct instance. The following two declarations are functionally identical:
```
void write(struct File *this, struct String *s); // standalone function, C style

void File::write(String &s); // class method, C++ style
```

The memory and CPU load overhead of class vs. struct is zero.

Accessing private class variables through public get/set methods is recommended because it simplifies debugging. For example, you can make variables read-only or write-only this way, do access logging etc. If you define get/set methods inline, there is no overhead vs. accessing public variables directly.

Another advantage of get/set methods is that they can do transformations on class/struct data on the fly. For example, a class to store birthdates can also have a method get_age(), because the age can be derived from the birthdate (class variable) and the current time (system call).

---

