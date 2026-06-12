---
title: "vector index out of range?"
date: 2009-03-25
forum: Programming Talk
---

### Post by tneva82 on 2009-03-25
Got following error message while trying to compile:

terminate called after throwing an instance of 'std::out_of_range'                                                                     
  what():  vector::_M_range_check  

On GDB's printout last point where it's still in my code says:

#10 0x08056470 in sector (this=0x8a02ab0, sectorX=5, sectorZ=5, sectorWidth=32, sectorHeight=32, masterTerrainList=0x89ff8c4,
    masterTextureList=0x8a02778) at src/sector.cpp:42

And the code in that line is:

```
pieces[x+z*width]=new terrainPiece(masterTerrainList->at(nextData.objectIndex), x*BLOCK_LENGHT, nextData.objectHeight,z*BLOCK_LENGHT, nextData.direction, masterTextureList[nextData.textureIndex], nextData.standHeight, nextData.passable);
```

Now weird thing is that a) I have resized pieces vector:

pieces.resize(width*height);

And as seen above it should therefore contain 32*32 elements. And I put it to print out where it tries into file and last line is:
x: 0, z: 0, width: 32, index: 0 size: 1024

So it should be trying to create new terrainPiece object to index 0 when there's room for 1024 objects.

Is that too many indexes for vector to handle(kinda bummer if it is. I'll be royally screwed if that's the case)? Or where I might be going wrong again?

---

### Post by dwhitney67 on 2009-03-25
What kind of containers are 'masterTerrainList' and 'masterTextureList'?

---

### Post by tneva82 on 2009-03-25
> **dwhitney67 said:**
> What kind of containers are 'masterTerrainList' and 'masterTextureList'?

vector and array. Both which have been initialised before this.

---

### Post by dwhitney67 on 2009-03-25
> **tneva82 said:**
> vector and array. Both which have been initialised before this.

Could the vector, 'masterTerrainList', be the one throwing the exception?  Verify the value of 'nextData->objectIndex' before calling at().

Also, I assume that the 'masterTerrainList' pointer (sigh), is pointing to the vector that you claim is initialized.

P.S.  Pass by reference, and avoid passing by pointer whenever possible.

---

### Post by tneva82 on 2009-03-25
> **dwhitney67 said:**
> Could the vector, 'masterTerrainList', be the one throwing the exception?  Verify the value of 'nextData->objectIndex' before calling at().

Well the objectIndex is 0.

> Also, I assume that the 'masterTerrainList' pointer (sigh), is pointing to the vector that you claim is initialized.

Yup.

> P.S.  Pass by reference, and avoid passing by pointer whenever possible.

Passing by reference would allow object X point to specific object within vector and keep access to it? Note just not another of same type but _the_ same? And alter it if neccessary?

---

### Post by dwhitney67 on 2009-03-25
Well, I cannot make an assessment as to what is causing the application grief.  Maybe if you posted the code for the sector() method?

Try also including <cassert> in your module, and using assert() to weed-out any potential bad indices and possibly bad vector sizes.

```

#include <cassert>

...

assert(pieces.size() == 32*32);
assert(x + z * width < 32*32);
assert(nextData.objectIndex < masterTerrainList->size());
...

```

---

### Post by tneva82 on 2009-03-26
Now this is odd. The vector size is correct in function A of class(specifically constructor) but later when function B is called vector size is empty? Atleast it crashes when I try to print the .size() of vector. Very odd. Aren't class variables supposed to stay untouched across function calls?

---

### Post by dwhitney67 on 2009-03-26
> **tneva82 said:**
> Now this is odd. The vector size is correct in function A of class(specifically constructor) but later when function B is called vector size is empty? Atleast it crashes when I try to print the .size() of vector. Very odd. Aren't class variables supposed to stay untouched across function calls?

Yes, they are.  That means there is probably a bug in your code.  Can you not whittle down the problem space a little and post some code?  It's hard to comment on someone's code with seeing it.

A couple of things that are certain:

1.  The application is doing exactly what you told it to do.
2.  The vector container does not have a bug in it.

Thus all fingers are pointing at you, the s/w developer.

---

### Post by tneva82 on 2009-03-26
> **dwhitney67 said:**
> Yes, they are.  That means there is probably a bug in your code.  Can you not whittle down the problem space a little and post some code.  It's hard to comment on someone's code with seeing it.

Where though it could be? Vectors contents aren't modified anywhere but constructor of class(haven't got around that part yet). Rest just use it in read only style(more accuratly calling functions from classes contained in the vector). Only places where it's modified are:

constructor: resize, insert stuff
destructor: clear the vector.

That's it.

---

### Post by eye208 on 2009-03-26
Buffer overflow.

---

### Post by dwhitney67 on 2009-03-26
Let's see your code.

See, something like this took only a few minutes to code...
```

#include <vector>
#include <algorithm>
#include <tr1/memory>
#include <iostream>


class Object
{
  public:
    Object() {}

    void doSomething()
    {
      std::cout << "doing something..." << std::endl;
    }
};

class Foo
{
  public:
    typedef std::tr1::shared_ptr<Object> ObjectPtr;

    Foo(int height, int width)
    {
      m_vec.resize(height * width);

      for (int i = 0; i < (height * width); ++i)
      {
        m_vec[i] = ObjectPtr(new Object);
      }
    }

    void performAction()
    {
      std::for_each(m_vec.begin(), m_vec.end(), action);
    }

  private:
    static void action(const ObjectPtr& o)
    {
      o->doSomething();
    }

    std::vector<ObjectPtr> m_vec;
};

int main()
{
  Foo foo(5, 5);
  foo.performAction();
}

```

---

### Post by eye208 on 2009-03-26
I guess the vector has been overwritten. If a call to size() results in a crash, the vector is not empty, but gone.

---

### Post by tneva82 on 2009-03-26
> **eye208 said:**
> Buffer overflow.

index(0) could hardly be buffer overflow when there's supposed to be(atleast that's what it gives in constructor and match what I'm trying to create) 1024 indexes.

---

### Post by tneva82 on 2009-03-26
> **eye208 said:**
> I guess the vector has been overwritten. If a call to size() results in a crash, the vector is not empty, but gone.

Only problem with that is that there's no code after constructor's test print's where I add anything to vector or do anything with vector except call class functions of objects contained in vector. Well except destructor but if that would get accidently called it would crash before it would get to size().

I have gone through code checking every single line where that vector is mentioned(find is handy feature) and there's *no* line that alters it after I print to file size of sector in constructor.

---

### Post by eye208 on 2009-03-26
> **tneva82 said:**
> Only problem with that is that there's no code after constructor's test print's where I add anything to vector or do anything with vector except call class functions of objects contained in vector.
Look at this code:
```
#include <iostream>
#include <cstring>

using namespace std;

class HelloWorld {
private:
        char s[256];
public:
        HelloWorld() {
                strcpy(s, "Hello World!");
        }
        void print() {
                cout << s << endl;
        }
};

int main() {
        HelloWorld hw;
        char b[16];
        hw.print();
        strcpy(b, "Let's make this buffer overflow!");
        hw.print();
        return 0;
}
```

If you run it, its output will look like this:
```
Hello World!
buffer overflow!
```

Duh! What's going on here? How can a private class variable be altered by a completely unrelated function?

The same thing happened to your vector object. The size() function crashes because the vector's internal pointers have been overwritten with garbage. You keep using C functions in your C++ code and never check array boundaries, so this had to happen sooner or later.

---

### Post by tneva82 on 2009-03-26
> **eye208 said:**
> The same thing happened to your vector object. The size() function crashes because the vector's internal pointers have been overwritten with garbage. You keep using C functions in your C++ code **and never check array boundaries**, so this had to happen sooner or later.

Sorry, nothing even remotely similar there. Of course since there are array boundaries in place(and top of that I have nothing even CLOSE of maximum sizes applied anyway) hardly suprising.

Sorry, strcpy to too small array doesn't explain since I check the array's for size.

Bolded part is flat out lie.

---

### Post by eye208 on 2009-03-26
> **tneva82 said:**
> Bolded part is flat out lie.
You have been using strcpy(), sprintf() and similar functions without bounds checking in all your previous code. dwhitney67 has told you numerous times to use the C++ string class instead of raw char arrays.

You refuse to learn even the most basic stuff. How are we supposed to help you? You even refuse to post your buggy code so we can sort it out for you.

If you know what's wrong with your code better than we do, why ask for help? Go and fix it yourself.

---

