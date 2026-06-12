---
title: "c++ Access via iterators headaches part 2"
date: 2011-07-22
forum: Programming Talk
---

### Post by muteXe on 2011-07-22
Hiya,

I have a method that takes in 2 objects, uses these objects to calculate some value, then returns the value. I do not change the original objects at all, so I thought it best to pass in by const reference:

```

   double GetVal(const CPosition& pos1,const CPosition& pos2)
   {    
        double fRtn = 0.0f;
        // do the calculations here

        return fRtn;
   }

```

And when i call it i am iterating through a loop, in which the positions change:

```

    std::vector<CPosition*>::iterator i;
    for(i = clList.begin(); i != clList.end(); ++i)
    {      
        CPosition sensorPos(0.0f,0.0f,0.0f);
        double val = GetVal(sensorPos, (*i));
        std::cout << val << std::endl;
    }

```

But it's not liking the way I derefence 'i' and pass it into GetVal().

I know this is something to do with the fact that dereferencing i gives me a pointer to a CPosition, but my method takes a constant ref to a CPosition, but i am not sure how best to resolve this.

At the end of the day I am not modifying the position objects, just using their member variables to do some simple maths and return the result, so I would like to keep the input params const.

Hmm...I've just tried creating a local CPosition variable (after writing myself a proper CPosition copy constructor), like so:

```

        CPosition sensorPos(0.0f,0.0f,0.0f);
        CPosition mPos(**i);
        double fVal= GetVal(sensorPos, mPos);
        std::cout << fVal<< std::endl;

```

and this actually works!  Can someone convince my tiny brain why
```

        CPosition mPos(**i);

``` 

compiles and gives me the right numbers please?

My thanks in advance,

Tom

---

### Post by dwhitney67 on 2011-07-22
You need to dereference the iterator to get to the element contained within the vector.  That element happens to be a *pointer* to a CPosition object.

Thus when you want to pass this element by reference, you need to dereference the element's pointer.  The following should suffice:
```

    std::vector<CPosition*>::iterator i;
    for(i = clList.begin(); i != clList.end(); ++i)
    {      
        CPosition sensorPos(0.0f,0.0f,0.0f);
        double val = GetVal(sensorPos, ****i**);
        std::cout << val << std::endl;
    }

```
Note the extra '*' associated with 'i'.

P.S.  Since it seems your intent is to avoid modifying the contents of the vector, you should employ the use of the 'const_iterator' in lieu of the 'iterator'.

P.S. #2 Consider declaring the constructor for CPosition as the following:
```

CPosition(double x = 0.0, double y = 0.0, double z = 0.0);

```
This would obviate the need to pass coordinates representing the origin to the constructor.  In other words, these would be equivalent:
```

CPosition sensorPos_1(0.0, 0.0, 0.0);

CPosition sensorPos_2;

```

---

### Post by muteXe on 2011-07-22
Thanks again dw, i get it now.
I was also not aware of 'const_iterator'.  It seems that 3 years of C# at work has erased a lot of pointer/reference knowledge.

Thanks again mate,

Tom

In response to your PS#2: I have actually done that. That CPosition sensorPos_1(0.0f, 0.0f, 0.0f) is just an 'quick' test line. Cheers.

---

