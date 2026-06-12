---
title: "C++ Operator Overloading Problems"
date: 2010-06-04
forum: Programming Talk
---

### Post by MrStill on 2010-06-04
I am having an issue with operator overloading. I don't usually program in C++; so, I imagine that my issue is fairly simple. Here is what I have:

```

...
Row & Row::operator +(const Row& toAdd){
    return add(toAdd);
}
...
Row & Row::add(const Row& toAdd){
    double *out_elements = new double[length];
    for(int x = 0; x < length; x++){
        out_elements[x] = elements[x] + toAdd.elements[x];
    }
    Row temp(out_elements, length);
    Row &out = temp;
    return out;
}
...

```

And main:

```

    ...
    cout << "Enter Row 1" << endl;
    cin >> r1;
    cout << "Enter Row 2" << endl;
    cin >> r2;
    cout << endl << "Now, we add: " << endl;
    cout << r1  << endl << r2 << endl;
    cout << r1 + r2 << endl;
    ...

```

I am thinking this could be an error with references. I generally code in Java; so, references are taken care of for me. The output I get is strange. I have tested *out* before returning it from *add()*and it prints correctly. However, when I attempt to print *add(toAdd)* in *operator +()* the values are no longer correct. Here is an example of output:

```
Now, we add: 
     2.0000      1.0000      4.0000 
     4.0000      5.0000      6.0000 
     6.0000      0.0000      0.0000      0.0000      0.0000 

```

Any advise would be great.

---

### Post by Some Penguin on 2010-06-04
References to objects allocated on the stack won't be very useful once you leave the scope where the referent is defined.

---

### Post by PabloH on 2010-06-05
Well, operator+ by convention should operate on the object it refers to, not just a temporary that it returns. It would seem that add() should work this way as well, since it returns a reference. 

In your example you are making a new object and not changing the existing object at all. 

If you wanted add to make a new object, say so: get rid of the reference return type and declare the whole method const to give the caller a hint that the object is not being modified, but a new one created. i.e. definition should be:

Row add(const Row & toAdd) const; 

On the other hand, if you really wanted to modify the object itself, then just do so:

Row & Row::add(const Row& toAdd){
// not really needed, you can modify variable elements directly
double temp;

for (int x = 0; x < length; x++){
   temp = elements[x] + toAdd.elements[x];

   elements[x] = temp;
}

// I think this is correct, don't have a compiler
// you may need to cast this
return *this;
}

In your version, note that if Row's constructor does not take ownership of the pointer and delete it at some point, that out_elements is leaked. Not sure if you are doing that or not.

---

### Post by MrStill on 2010-06-07
> **PabloH said:**
> Well, operator+ by convention should operate on the object it refers to, not just a temporary that it returns. It would seem that add() should work this way as well, since it returns a reference. 

In your example you are making a new object and not changing the existing object at all. 

If you wanted add to make a new object, say so: get rid of the reference return type and declare the whole method const to give the caller a hint that the object is not being modified, but a new one created. i.e. definition should be:

Row add(const Row & toAdd) const;
...


Thanks for the reply. I changed the add function and operator + to return the new row; removing the reference and calling the function const. I understand that this is against convention; however, I am attempting to write a row-reduction algorithm and fear I might not always want to change the row during the addition process.

These changes fix the run time errors I was having. But, I notice a strange compile error arise;

```

cout << r1 + r2 << endl;

``` 

This line will not compile; it is no big deal, as I can make a third row receive the output from r1 + r2 and it compiles and prints with no issue. 

> **PabloH said:**
> 
...
In your version, note that if Row's constructor does not take ownership of the pointer and delete it at some point, that out_elements is leaked. Not sure if you are doing that or not.

I think I have handled this problem:

```

Row::Row(double *elements, int length){
    double *new_elements = new double[length];
    this->length = length;
    for(int x = 0; x < length; x++){ new_elements[x] = elements[x]; }
    this->elements = new_elements;
    delete[] elements;
}

``` 

Memory leaks are not something I am accustomed to. So I must ask, If I were to write something like:

```

bool output = (r3 + r2) == r1;

```

I am imagining that the object created by r3 + r2 is never deleted and thus causes a memory leak. Am I correct in this assumption?

---

### Post by dwhitney67 on 2010-06-07
> **MrStill said:**
> 
I am imagining that the object created by r3 + r2 is never deleted and thus causes a memory leak. Am I correct in this assumption?

Examine this version of the code; note that I avoid allocating frivolously my initial arrays of doubles in the main() function.  If I had though, I would not have given ownership to the Row class; I would have deleted them myself after constructing the Row object.

```

#include <iostream>
#include <algorithm>

class Row
{
public:
   // constructor
   Row(const double* elements, const size_t length);

   // copy constructor
   Row(const Row& other);

   // destructor
   ~Row();

   // operator+
   Row operator+(const Row& rhs_row) const;

   // for outputing Row object to ostream
   friend std::ostream& operator<<(std::ostream& os, const Row& row);

private:
   double* myElements;
   size_t  myLength;
};


// constructor
Row::Row(const double* elements, const size_t length)
   : myElements(new double[length]),
     myLength(length)
{
   std::copy(elements, elements + myLength, myElements);
}


// copy constructor
Row::Row(const Row& other)
   : myElements(new double[other.myLength]),
     myLength(other.myLength)
{
   std::copy(other.myElements, other.myElements + myLength, myElements);
}


// destructor
Row::~Row()
{
   delete [] myElements;
   myLength = 0;
}


// operator+
Row Row::operator+(const Row& rhs_row) const
{
   Row new_row(*this);

   for (size_t i = 0; i < new_row.myLength; ++i)
   {
      new_row.myElements[i] += rhs_row.myElements[i];
   }

   return new_row;
}


// outputs a Row object to the given ostream
std::ostream& operator<<(std::ostream& os, const Row& row)
{
   for (size_t i = 0; i < row.myLength; ++i)
   {
      os << row.myElements[i] << " ";
   }

   return os;
}


// main
int main()
{
   double values1[] = { 1.2, 2.4, 3.1 };
   double values2[] = { 3.8, 2.6, 1.9 };

   Row row1(values1, sizeof(values1)/sizeof(double));
   Row row2(values2, sizeof(values2)/sizeof(double));

   Row row3 = row1 + row2;

   std::cout << row3          << std::endl;
   std::cout << (row1 + row2) << std::endl;

   return 0;

   // here the Row destructor takes care of freeing allocated memory
}

```

---

### Post by dribeas on 2010-06-07
Saying that you now have an error in:

```

std::cout << r1 + r2 << std::endl;

```

Is hardly as helpful as writing the actual error that the compiler is giving. I can only assume that the signature of your overloaded ' operator<<'  is something like:

```

std::ostream& operator<<( std::ostream&, Row& );

```

and that the error is that you cannot bind a temporary to a non-const reference. If that is the case, then change the signature so that it takes the Row argument by const reference:

```

std::ostream& operator<<( std::ostream&, Row const& );

```

The dump operator should not modify the object being dumped so it makes sense to pass a constant reference, and that at the same time will allow you to call that operator on temporaries.

---

### Post by TheStatsMan on 2010-06-08
Just making the point, which is quite possibly irrelevant for your problem, that you shouldn't really be using that approach to overload the + operator (or any element by element operator) if you are using the code in any computationally demanding situations. You can avoid the construction of the temporary array using a template based approach (expression templates) yet still maintain the same level of abstraction. The only downside is a moderate increase in complexity in the array class.

---

