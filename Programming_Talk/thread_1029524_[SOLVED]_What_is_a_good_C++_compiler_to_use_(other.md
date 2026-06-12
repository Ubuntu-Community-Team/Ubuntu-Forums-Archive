---
title: "[SOLVED] What is a good C++ compiler to use (other than gcc) for Ubuntu?"
date: 2009-01-03
forum: Programming Talk
---

### Post by Zorgoth on 2009-01-03
I have been working on a computing project in C++ (I'm using a Gateway laptop with an AMD64 processor and 32-bit Ubuntu) and I have found that gcc appears entirely unusable for what I am doing, at least on my computer.  I am using code which compiles and runs perfectly under Dev-C++ in Windows on the same computer, but simply calling *any* function taking a user-defined class as its argument is causing segmentation faults when I use gcc, and I am sick of having to boot into Windows every time I want to test my code.

Help?

Thanks!

---

### Post by kjohansen on 2009-01-03
I know it is possible for gcc and g++ to handle functions with user defined objects.

```

#include <iostream>

class Kjoh
{
public:
  int t;
  int s;
  Kjoh()
  {
    t=390;
    s=3224;
  }
};



int go(Kjoh y)
{
  return y.s;
}

int main()
{
Kjoh kj;

int h=go(kj);

std::cout<<h<<std::endl;
}

```

This works and compiles with g++.  But to answer your original question there are lots of compilers.  Off the top of my head there is icc from intel and tcc.

---

### Post by dwhitney67 on 2009-01-03
> **Zorgoth said:**
> I have been working on a computing project in C++ (I'm using a Gateway laptop with an AMD64 processor and 32-bit Ubuntu) and I have found that gcc appears entirely unusable for what I am doing, at least on my computer.  I am using code which compiles and runs perfectly under Dev-C++ in Windows on the same computer, but simply calling *any* function taking a user-defined class as its argument is causing segmentation faults when I use gcc, and I am sick of having to boot into Windows every time I want to test my code.

Help?

Thanks!

Show an example of your code that is causing you grief.  Maybe it is the culprit, not GCC.

---

### Post by stroyan on 2009-01-03
It would be very interesting if you could reduce the crashing code to a small test case.  That would produce one of two outcomes.
[LIST=1]
[*]You would create a concise defect report to file against g++.  That would be very helpful to the community.
[*]You would find that there is a detail in your implementation that violates the c++ standard.  Many instances of troubled code will "just work" on particular implementations and fail on others.
[/LIST]

---

### Post by shadylookin on 2009-01-03
g++ is what's typically used for c++ code. I'm pretty sure gcc is only a C compiler

---

### Post by Zorgoth on 2009-01-03
Here is an example of the kind of problem I am having.  This code works under Dev-C++ and not under g++, I checked:

```

#include <iostream>
#include <string>

class myclass
{
public:
myclass();
~myclass();
myclass(myclass const & original);
void Clear();
void Resize(int newsize);
int Size() const;
void Write(int position, int value);
int Read(int position) const;
const myclass & operator=(myclass const & original);
bool operator==(myclass const & RightOperand) const;
private:
int size;
int * pointy;
};

inline void myclass::Clear()
{
if (pointy!=0) delete [] pointy;
pointy=0;
}

inline void myclass::Resize(int newsize)
{
if (newsize > 1)
   {
   if (pointy!=0) delete [] pointy;
   pointy = new int[newsize];
   if (pointy!=0)  size=newsize;
   else 
      {
      size=0;
      std::cout << "\nError: Not enough memory.\n";
      }
   }
else if (newsize==0)
   {
   if (pointy!=0) delete [] pointy;
   pointy=0;
   size=0;
   }
else std::cout << "\nThis object cannot have a negative size!\n";
int k=0;
while (k<size)
   {
   pointy[k]=0;
   k++;
   }
}

inline int myclass::Read(int position) const
{
if (position>=0 && position < size) return pointy[position];
else 
   {
   std::cout<<"\nCannot read from " << position << "; size is "<< size << ".\n";
   return -1;
   } 
}

inline void myclass::Write(int position, int value)
{
if (position >=0 && position<size) pointy[position]=value;
else std::cout << "\nCannot write to " << position << "; size is " << size << ".\n";
}

inline int myclass::Size() const
{
return size;
}


inline myclass::myclass()
{
pointy=0;
Resize(0);
}

inline myclass::myclass(myclass const & original)
{
int k=0;
Resize(original.Size());
while (k<size)
   {
   Write(k, original.Read(k));
   k++;
   }
}

inline myclass::~myclass()
{
Clear();
}

inline const myclass & myclass::operator=(myclass const & original)
{
int k=0;
Resize(original.Size());
while (k<size)
   {
   Write(k, original.Read(k));
   k++;
   }
return *this;
}

inline bool myclass::operator==(myclass const & RightOperand) const
{
if (Size()!=RightOperand.Size()) return false;
int k=0;
while (k<size)
   {
   if (Read(k)!=RightOperand.Read(k)) return false;
   k++;
   }
return true;
}

myclass Add(myclass A, myclass B)
{
myclass Sum;
if (A.Size()!=B.Size())
   {
   std::cout << "\nAddition error: Invalid sizes.  Returning error object...\n";
   return Sum;
   }
Sum.Resize(A.Size());
int k=0;
while (k<A.Size())
   {
   Sum.Write(k, A.Read(k)+B.Read(k));
   k++;
   }
return Sum;
}
int main()
{
myclass A, B, C;
B.Resize(6);
A.Resize(6);
C=Add(A,B); 
}

```

The problem arises when a class involving a pointer is taken as an argument of a function.  The code compiles in g++, but any attempt to use the function results in a segmentation fault.

---

### Post by Zorgoth on 2009-01-03
> **shadylookin said:**
> g++ is what's typically used for c++ code. I'm pretty sure gcc is only a C compiler

Isn't GCC GNU Compiler Collection?  That's what I meant, sorry for any confusion.

---

### Post by Sockerdrickan on 2009-01-03
Dev-C++ uses g++ lol

---

### Post by Zorgoth on 2009-01-03
> **Tux0r said:**
> Dev-C++ uses g++ lol

Then Windows vs. Linux

---

### Post by cb951303 on 2009-01-03
> **Zorgoth said:**
> I have been working on a computing project in C++ (I'm using a Gateway laptop with an AMD64 processor and 32-bit Ubuntu) and I have found that gcc appears entirely unusable for what I am doing, at least on my computer.  I am using code which compiles and runs perfectly under Dev-C++ in Windows on the same computer, but simply calling *any* function taking a user-defined class as its argument is causing segmentation faults when I use gcc, and I am sick of having to boot into Windows every time I want to test my code.

Help?

Thanks!

DevC++ uses gcc-3.x, ubuntu uses gcc-4.x. Before changing compilers I recommend you to take a good look to your code. A piece of code compiling in Dev-C++ but not in gcc-4.x doesn't mean anything. There is still a very big chance that you screwed up somewhere on your code.

PS: The code you sent is messy. No indent? no formatting? I refuse to take a look at it :)

---

### Post by shadylookin on 2009-01-03
[PHP]
myclass Add(myclass &A, myclass &B)
{
myclass Sum;
if (A.Size()!=B.Size())
   {
   std::cout << "\nAddition error: Invalid sizes.  Returning error object...\n";
   return Sum;
   }
Sum.Resize(A.Size());
int k=0;
while (k<A.Size())
   {
   Sum.Write(k, A.Read(k)+B.Read(k));
   k++;
   }
return Sum;
}
[/PHP]

if you add the &'s to the parameters the segmentation fault stops, but that's not what you asked for. 

I'm pretty sure intel makes a c++ compiler for linux.

---

### Post by Zorgoth on 2009-01-03
> **shadylookin said:**
> [PHP]
myclass Add(myclass &A, myclass &B)
{
myclass Sum;
if (A.Size()!=B.Size())
   {
   std::cout << "\nAddition error: Invalid sizes.  Returning error object...\n";
   return Sum;
   }
Sum.Resize(A.Size());
int k=0;
while (k<A.Size())
   {
   Sum.Write(k, A.Read(k)+B.Read(k));
   k++;
   }
return Sum;
}
[/PHP]

if you add the &'s to the parameters the segmentation fault stops, but that's not what you asked for. 

I'm pretty sure intel makes a c++ compiler for linux.

Thanks!  Doesn't seem quite elegant, but my code works fine when I use const & for the arguments.  That is a most useful trick, but this does still seem rather like a bug to me...

---

### Post by Bichromat on 2009-01-03
double post

---

### Post by Bichromat on 2009-01-03
The problem is in your deep copy constructor. You call 'Resize(original.Size());' but you have not yet initialized pointy, so it can be non-zero and Resizes tries to free it... segfault! You need to add 'pointy=0;' before you call 'Resize'.
However, I think it's better to pass a 'const &' to 'Add', especially if 'size' can be big, because it will prevent the whole array from being copied.

---

### Post by dwhitney67 on 2009-01-03
> **Zorgoth said:**
> Thanks!  Doesn't seem quite elegant, but my code works fine when I use const & for the arguments.  That is a most useful trick, but this does still seem rather like a bug to me...

It's not a bug; you have merely changed the declaration of Sum() to accept references to A and B, thus obviating the need to create a deep copy of them.  This saves on processing time, and hence should be considered something good.

The crux of the problem is what Bichromat stated in his last post.  In your copy-constructor, you failed to initialize 'pointy' to zero *before* calling Resize().

Consider this:
[php]
myclass(const myclass& other)
  : pointy(0),
    size(0)
{
  Resize(other.size);
  memcpy(pointy, other.pointy, other.size * sizeof(int));
}
[/php]

---

### Post by Zorgoth on 2009-01-03
> **dwhitney67 said:**
> It's not a bug; you have merely changed the declaration of Sum() to accept references to A and B, thus obviating the need to create a deep copy of them.  This saves on processing time, and hence should be considered something good.

The crux of the problem is what Bichromat stated in his last post.  In your copy-constructor, you failed to initialize 'pointy' to zero *before* calling Resize().

Consider this:
[php]
myclass(const myclass& other)
  : pointy(0),
    size(0)
{
  Resize(other.size);
  memcpy(pointy, other.pointy, other.size * sizeof(int));
}
[/php]

Ah thank you!  I feel enlightened.  I had that problem before but somehow it never occured to me that I had to do that in the copy constructor as well as the default constructor...

---

### Post by jmartrican on 2009-01-03
The book Code Complete goes over these types of mishaps.

---

