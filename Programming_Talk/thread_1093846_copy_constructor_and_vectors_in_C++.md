---
title: "copy constructor and vectors in C++"
date: 2009-03-12
forum: Programming Talk
---

### Post by Houman on 2009-03-12
hello there, 
I have written a code to better observe how the copy constructors work in conjunction with std vectors and the results are rather puzzling, I was wondering if anyone could explain this, here is the code:

```


#include <iostream>
#include <string>
#include <vector>
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <algorithm>
#include <sstream>
#include <stdexcept>

using namespace std;
 inline std::string stringify(int x)
 {
   std::ostringstream o;
   if (!(o << x))
     cout<<"bad conversion"<<endl;
   return o.str();
 } 

class A
{
public:
    A();
    A(string pstring)
    {
        name=pstring;
    }
    A(const A& pA)
    {
	name=pA.name+"copy";
	cout<<"copy constructor of "<<name<<" is called"<<endl;
        
    }
    ~A(){cout<<"destructor of "<<name<<" is called"<<endl;};
    string name;
};

int main()
{
	int i=0;
    vector<A> ACollection;
   string tempString;


    for (i=0;i<10;i++)
    {
        tempString=stringify(i);
        A tempA(tempString);
        ACollection.push_back(tempA);
	cout<<"currently adding object "<<tempString<<endl;
    }
	cout<<"size of the collection is "<<ACollection.size()<<endl;

    for (i=0;i<10;i++)
    {
        cout<<ACollection[i].name<<endl;
    }
return 0;
}

```

and here is the output:

```

copy constructor of 0copy is called
currently adding object 0
destructor of 0 is called
copy constructor of 0copycopy is called
copy constructor of 1copy is called
destructor of 0copy is called
currently adding object 1
destructor of 1 is called
copy constructor of 0copycopycopy is called
copy constructor of 1copycopy is called
copy constructor of 2copy is called
destructor of 0copycopy is called
destructor of 1copy is called
currently adding object 2
destructor of 2 is called
copy constructor of 3copy is called
currently adding object 3
destructor of 3 is called
copy constructor of 0copycopycopycopy is called
copy constructor of 1copycopycopy is called
copy constructor of 2copycopy is called
copy constructor of 3copycopy is called
copy constructor of 4copy is called
destructor of 0copycopycopy is called
destructor of 1copycopy is called
destructor of 2copy is called
destructor of 3copy is called
currently adding object 4
destructor of 4 is called
copy constructor of 5copy is called
currently adding object 5
destructor of 5 is called
copy constructor of 6copy is called
currently adding object 6
destructor of 6 is called
copy constructor of 7copy is called
currently adding object 7
destructor of 7 is called
copy constructor of 0copycopycopycopycopy is called
copy constructor of 1copycopycopycopy is called
copy constructor of 2copycopycopy is called
copy constructor of 3copycopycopy is called
copy constructor of 4copycopy is called
copy constructor of 5copycopy is called
copy constructor of 6copycopy is called
copy constructor of 7copycopy is called
copy constructor of 8copy is called
destructor of 0copycopycopycopy is called
destructor of 1copycopycopy is called
destructor of 2copycopy is called
destructor of 3copycopy is called
destructor of 4copy is called
destructor of 5copy is called
destructor of 6copy is called
destructor of 7copy is called
currently adding object 8
destructor of 8 is called
copy constructor of 9copy is called
currently adding object 9
destructor of 9 is called
size of the collection is 10
0copycopycopycopycopy
1copycopycopycopy
2copycopycopy
3copycopycopy
4copycopy
5copycopy
6copycopy
7copycopy
8copy
9copy
destructor of 0copycopycopycopycopy is called
destructor of 1copycopycopycopy is called
destructor of 2copycopycopy is called
destructor of 3copycopycopy is called
destructor of 4copycopy is called
destructor of 5copycopy is called
destructor of 6copycopy is called
destructor of 7copycopy is called
destructor of 8copy is called
destructor of 9copy is called

```


why is the copy constructor being called on the same object so many times? I spoke to a friend of mine and he said because the vector has to keep copying itself to a new vector, but that seems very inefficient, what if my objects are very big? I was wondering if that is really the reason for this and how to fix this problem if there is a way;

thank you
H.

---

### Post by eye208 on 2009-03-12
> **Houman said:**
> why is the copy constructor being called on the same object so many times? I spoke to a friend of mine and he said because the vector has to keep copying itself to a new vector, but that seems very inefficient, what if my objects are very big? I was wondering if that is really the reason for this and how to fix this problem if there is a way;
You should increase the vector's capacity prior to adding objects. Insert this before the *for* loop:
```
ACollection.reserve(10);
```

---

### Post by dribeas on 2009-03-12
[QUOTE=Houman;6880635]
why is the copy constructor being called on the same object so many times? I spoke to a friend of mine and he said because the vector has to keep copying itself to a new vector, but that seems very inefficient, what if my objects are very big? I was wondering if that is really the reason for this and how to fix this problem if there is a way;
QUOTE]

As already answered whenever the vector has to grow it needs to copy its contents to a new larger location. That implies performing copies of all the internal elements.

If you know the estimated size of the vector you can create a vector big enough by calling vector<>::reserve( size_t ). That will create enough space so that no reallocations take place.

On the other hand, the amortized cost of the copies is linear on the size of the final vector. If the final size of the vector is N, then at most 2*N copies will be performed if the data is inserted with push_back().

Insertions at the beginning/middle of the vector have higher costs as all the elements from the insertion point to the end of the vector need to be relocated. If you need to perform this kind of operations consider using a std::list or std::deque.

In some cases you might consider using vectors to hold pointers, relocations of pointers is simple and fast, regardless of the size of the pointed object, but I would consider it for performance reasons only if the objects are really really big, and in doing so I would not use raw pointers but std::tr1::shared_ptr or boost::shared_ptr to delegate the destruction responsibility.

---

### Post by Houman on 2009-03-12
thanks everyone for the replies, 

I think I will use a list since the order is not important and as dribeas said its less time consuming to insert objects, i will also reserve the elements, and I think I will use pointers, because the objects are actually very big, around 1 mega byte each, and eventually the list will grow to more than a hundred elements, 
I have to get reading on the boost smart pointers now, 

thank you
H

---

