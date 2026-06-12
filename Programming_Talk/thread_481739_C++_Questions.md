---
title: "C++ Questions"
date: 2007-06-22
forum: Programming Talk
---

### Post by OhioYJ on 2007-06-22
Ok its been quite a while since I've done any coding, and I'm trying to brush up on my skills now. I'm using Anjuta 1.2.4a. 

First Question:

Can a function return an array? I don't think it can, so at the moment my array is a global variable.

Second Question:

So I have my code in a *.cc file, whats the easiest way to compile my program so it will work in a Windows environment?

---

### Post by yabbadabbadont on 2007-06-22
1) I don't think so, but it can return a reference to an array.  ;)

---

### Post by PandaGoat on 2007-06-22
You can also pass the variable as a reference in the function:
```

string s[500];

void func(string &something[])
{
     *something = somethingelse; // Sets s[500] to somethingelse
}


```

---

### Post by i0Null on 2007-06-22
You can always declare global arrays but I wouldn't recommend doing that.

---

### Post by hod139 on 2007-06-22
You can return an array from a function.  Remember, an array is nothing more than a pointer to the starting address of the array in memory.  I would suggest not using globals nor returning new arrays and do as PandaGoat suggested, pass a reference of the array as an argument to the function.  The reason I don't recommend returning a new array is because ownership of the memory becomes tricky.  Who's job is it to delete the returned array?   Lastly, returning a reference to the array is a very bad idea (unless the array is a member of a class, then it is ok) because you will be returning the address of a temporary variable.  To elucidate all the difference, here is some code:

```

#include <iostream>

// Pass a reference to the array pointer
// This is my prefered choice
void callByRefToPtr(int *&arrayRef, int size)
{
  for (int i = 0; i < size; ++i)
     arrayRef[i] = i;
}

// Pass a pointer to the array pointer
// This is equally fine, but the syntax is a bit uglier
void callByPtrToPtr(int **arrayRef, int size)
{
  for (int i = 0; i < size; ++i)
     (*arrayRef)[i] = i+size;
}

// Pass a copy of the array pointer
// As long as you do not realloc the array, this is fine
void callByPtr(int *arrayRef, int size)
{
  for (int i = 0; i < size; ++i)
     arrayRef[i] = i+2*size;
}

// Different syntax for passing a copy of the array pointer
// Again, just don't attempt a realloc
void callByPtr2(int arrayRef[], int size)
{
  for (int i = 0; i < size; ++i)
     arrayRef[i] = i+3*size;
}

// Returns the pointer to a new array
// Who owns this array?  Who is suppose to delete it?
int* returnArrayPtr(int size)
{
  int *array = new int[size];
  for (int i = 0; i < size; ++i)
     array[i] = i+4*size;
  return array; // returning a copy
}

// Returns a reference to an array
// This is VERY BAD, returns the address of a local variable
int*& returnArrayRef(int size)
{
  int *array = new int[size];
  for (int i = 0; i < size; ++i)
     array[i] = i+5*size;
  return array;
}


/**
 * Main Entry POint
 */
int main(void)
{
  int N = 3;
  int *inArray = new int[N];

  callByRefToPtr(inArray, N);
  for (int i = 0; i < N; ++i)
  {
     std::cout << inArray[i] << ", ";
  }
  std::cout << std::endl;

  callByPtrToPtr(&inArray, N);
  for (int i = 0; i < N; ++i)
  {
     std::cout << inArray[i] << ", ";
  }
  std::cout << std::endl;

  callByPtr(inArray, N);
  for (int i = 0; i < N; ++i)
  {
     std::cout << inArray[i] << ", ";
  }
  std::cout << std::endl;

  callByPtr2(inArray, N);
  for (int i = 0; i < N; ++i)
  {
     std::cout << inArray[i] << ", ";
  }
  std::cout << std::endl;

  int *outArray = returnArrayPtr(N);
  for (int i = 0; i < N; ++i)
  {
     std::cout << outArray[i] << ", ";
  }
  std::cout << std::endl;

  int *&outArrayRef = returnArrayRef(N);
  for (int i = 0; i < N; ++i)
  {  // This may cause a segfault, reading bad memory!
     std::cout << outArrayRef[i] << ", ";
  }
  std::cout << std::endl;


  // clean up arrays
  delete []inArray;
  delete []outArray; // Lets hope no one is using this

  return 0;
}

```Running the code produces:
```


0, 1, 2, 
3, 4, 5, 
6, 7, 8, 
9, 10, 11, 
12, 13, 14, 
15, 4096, 132628,
```

Notice the garbage values on the return by reference function.  I hope this helps.

---

### Post by aks44 on 2007-06-23
```
#include <vector>

void doWhatever(std::vector<int>& vect)
{
  for (std::vector<int>::iterator i=vect.begin(); i!=vect.end(); ++i)
  {
    // whatever
  }
}
```

Using C++, there are very seldom reasons to use raw C arrays. We have the STL, and if it isn't enough we can always write our own RAII wrappers.

Managing memory by hand is just asking for trouble...


Concerning question (2) : I use the mingw toolchain from the comfort of Linux, as well as Qt4 (KDE user here :p) which provides a very good cross-platform abstraction IMHO.

---

### Post by Soybean on 2007-06-23
I agree with aks44... a std::vector is a much better idea than a C-style array. To be fair, though, it wasn't until about 6 months ago that I got over my distrust of that "newfangled STL stuff" that they added in the 1998 standard. :D

---

### Post by hod139 on 2007-06-23
I wholeheartedly agree with Soybean and aks44, when using C++ you should use the STL containers.

---

### Post by xtacocorex on 2007-06-23
Another STL vector example where you don't pass the vector back is shown here:
```

// genLocX_Equi
// Generates a vector of x locations that are equally spaced
std::vector<double> genLocX_Equi(int nPoints, int nPan)
{
    // Variable Declaration
    std::vector<double> x;

    // Figure out where i is at in the range
    for (int i = 1; i <= nPoints; i++)
    {
        if(i == 1 || i == nPoints)
        {
            x.push_back(double(1.0));
        }
        else if(i > 1 && i < (nPan/2)+1)
        {
            x.push_back(std::fabs(std::fabs((double(i)-1.0)/(double(nPan)/2.0)) - 1.0));
        }
        else if(i > (nPan/2)+1 && i < nPoints)
        {
            x.push_back(std::fabs(1.0 - std::fabs((double(i)-1.0)/(double(nPan)/2.0))));
        }
        else if(i == (nPan/2)+1)
        {    
            x.push_back(double(0.0));
        }
    }

    // Return x
    return x;
    
} // End genLocX_Equi

```I pulled this out of a code of mine that does airfoil generation.

---

### Post by aks44 on 2007-06-23
The very reason IMO why one shouldn't return a vector (or whatever other STL container) from a function, is that a deep copy is made when returning from the function. Depending on the vector size and the contained class, this can quickly become extremely expensive.

Even though most modern compilers are able to do Return Value Optimization, one shouldn't rely on it, as it is not mandatory.

What if someone calls genLocX_Equi with a very large number of points? :(

This could of course be avoided using boost::shared_ptr. However, I prefer avoiding boost::shared_ptr unless I really need to have several simultaneous references on the object.

I'd rather have written something more like this :

```
void genLocX_Equi(int nPoints, int nPan, std::vector<double>& output)
{
    std::vector<double> x;
    // preallocate the memory to avoid useless reallocation and copying
    // as we already know the number of elements the vector will contain
    x.reserve(nPoints);

    // Figure out where i is at in the range
    for (int i = 1; i <= nPoints; i++)
    {
        if(i == 1 || i == nPoints)
        {
            x.push_back(double(1.0));
        }
        else if(i > 1 && i < (nPan/2)+1)
        {
            x.push_back(std::fabs(std::fabs((double(i)-1.0)/(double(nPan)/2.0)) - 1.0));
        }
        else if(i > (nPan/2)+1 && i < nPoints)
        {
            x.push_back(std::fabs(1.0 - std::fabs((double(i)-1.0)/(double(nPan)/2.0))));
        }
        else if(i == (nPan/2)+1)
        {    
            x.push_back(double(0.0));
        }
    }

    // now we can swap output and x at no cost
    // of course we could have worked directly on output
    // but it wouldn't have been exception safe
    output.swap(x);
}
```

Just my 2 cents. ;)

---

### Post by hod139 on 2007-06-23
> **aks44 said:**
> The very reason IMO why one shouldn't return a vector (or whatever other STL container) from a function, is that a deep copy is made when returning from the function. Depending on the vector size and the contained class, this can quickly become extremely expensive.

It's even worse than this, because as far as I know a shallow copy is made, not a deep.  So for example, if you had a vector of user defined class pointers, I don't think the return statement would work as expected.  Passing the container as a reference to the method is the safest and fastest solution.

---

### Post by xtacocorex on 2007-06-23
So this might be getting off topic, but you're saying that it's not good to create functions that return any type (int, double, bool)?

Granted, I wouldn't have done that bit of code the same way in FORTRAN, but I figured that since std::vector is a type, you could have it be a function return.  

I don't know what the shallow/deep copy's are that you two are talking about. 

At least I learned that you can preallocate memory for std::vectors.

---

### Post by hod139 on 2007-06-23
A std::vector is not a type, it is a container.  Shallow versus deep copy is a bit off topic, and next time I see you on irc we can discuss it.  If the vector contains a primitive type (e.g. int, char, bool) the return will work, but it will be inefficient since it has to copy the entire vector, that is each element of the vector.

---

