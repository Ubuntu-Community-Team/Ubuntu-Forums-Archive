---
title: "Classes in C++"
date: 2008-11-25
forum: Programming Talk
---

### Post by c++learner on 2008-11-25
Hi all!
I'm trying to create a Vector3D that represents a three dimensional vector in c++, and i'm totally confused with constructors/destructors/ and  << >> overloadings.  It compiles but doesnt' work. Could you point what important I'm missing (if you know)?  Thank you very much!
Here is the code:

header:
#ifndef Vector3D_h
#define Vector3D_h
#include <iostream>
using namespace std;

class Vector3D {
	friend ostream& operator<<(ostream& out, const Vector3D& V);//Ouputs Vector3D
	friend istream& operator>>(istream& in, Vector3D& V);

public:
	Vector3D(); //null constructor that initializes the vector to all 0’s
	Vector3D(double x , double y, double z); //constructor that initializes the x, y, and z components
//	Vector3D(Vector3D& V); //constructs copy of Vector3D type V
	~Vector3D(); //deallocates Vector3d array memory
	void Print() const;
  
private:
  double vect[3]; //double array of size 3
};

#endif;

//Vector3D.cpp 
#include <iostream>
using namespace std;
#include "Vector3D.h"

Vector3D::Vector3D() //null constructor that initializes the vector to all 0’s
{
  for (int i = 0; i < 3; i++) vect[i] = 0;
}

Vector3D::Vector3D(double x , double y, double z) //constructor that initializes the x, y, and z components
{
  vect[0] = x;  vect[1] = y;  vect[3] = z;
}
/*
Vector3D::Vector3D(Vector3D& V)
{
  vect[0] = V[0];  vect[1] = V[1];  vect[3] = V[2];
}
*/
Vector3D::~Vector3D() //destructor
{
  delete [] vect; //deallocates array (of any length) 
}
/*
void Vector3D::Print() const
{
	cout << "vector (x, y, z) - components are: (";
	for (int i = 0; i < 3; i++)
		cout << vect[i] << " " ;
	cout << ")" <<endl;
}*/
istream& operator>>(istream& in, Vector3D& V)
{
	double x , y, z;
	in >> x >> y >> z;
	V = Vector3D (x, y, z);
  
  return in;
}

ostream& operator<<(ostream& out, const Vector3D& V)//Outputs Vector3D V
{
	out << "vector (x, y, z) - components are: (";
	for (int i = 0; i < 3; i++)
		out << V.vect[i] << " " ;
	out << ")" << endl;
	return out;
}

//Vector3DTest.cpp
#include <iostream>
using namespace std;
#include "Vector3D.h"

int main(){
	Vector3D V;
	double x, y, z;
	cout << "Please enter your 3D vector ";
	cin >> V;
	cout << endl << V << endl;

	return 0;
}

---

### Post by UpsideDownFace on 2008-11-25
A thing I see that is wrong is "vect[3]" doesnt exist.
Defining a 3-element Vect produces vect[0],vect[1],vect[2]
so if you use "vect[3]=z;" in an assignment you get something like SystemOverflow at runtime, i.e your program crashes.

Another thing I see wrong is you are trying something too large.
If you start off with only a few things, and build up gradually to the full code, you have more chance of getting it right.

---

### Post by thk on 2008-11-25
Using an array here seems to be adding unnecessary complexity.

How about:

class Vect3D
{
  public:
    Vect3D() : x(0), y(0), z(0) {}
    Vect3D(double x, double y, double z)
       : x(x), y(y), z(z) {}
  private:
    double x, y, z;
};

the default constructor and destructor will work fine here.

If you are going to use an array, try the boost::array template.

Also, never call delete on something that was not allocated with new.

---

### Post by c++learner on 2008-11-25
Thank you for your reply, actually vect[3] worked just fine.  the reason the code looked so long was because i needed to see if it prints out correctly, the rest was just constructors/ destructors, couldn't avoid it (and i needed to make 3 different files out of them...).  I tried to start with something small. :-)
what didn't work - i confused with arrays: it's from 0 to 2 and i had even 3, plus >> didn't work.
have a lot of work ahead, thanks again for looking into my code!

---

### Post by c++learner on 2008-11-25
Hi thk!

Just saw our thread. Now, i'm confused - do you mean i need to delete destructor {delete [] vect;} since i never allocated memory with new?
i couldn't use vectors, since the assignment was to use array of 3. isn't it more sufficient, btw, to use array if we know that the size will never change?
Thank you!

---

### Post by dwhitney67 on 2008-11-25
If you plan to instantiate your array on the stack (which is what you have done), then you do not need to call 'delete' in the destructor.

Btw, you could collapse your two constructors into just one with something like:
[php]
class Vector3D
{
  public:
    // assign default value of zero to each parameter
    Vector3D(double x = 0, double y = 0, double z = 0);
    ...
  private:
    double vect[3];
};

Vector3D::Vector3D(double x, double y, double z)
{
  vect[0] = x;
  vect[1] = y;
  vect[2] = z;
}
...
int main()
{
  Vector3D v1;           // x = y = z = 0
  Vector3D v2(1);        // x = 1, y = z = 0
  Vector3D v3(1, 2);     // x = 1, y = 2, z = 0
  Vector3D v4(1, 2, 3);  // x = 1, y = 2, z = 3
}
[/php]

Don't forget to implement the copy-constructor, which you currently have commented out.  It will prove useful.

---

### Post by thk on 2008-11-26
> **c++learner said:**
> Hi thk!

Just saw our thread. Now, i'm confused - do you mean i need to delete destructor {delete [] vect;} since i never allocated memory with new?
i couldn't use vectors, since the assignment was to use array of 3. isn't it more sufficient, btw, to use array if we know that the size will never change?
Thank you!

Since you did not call new, you do not need to call delete. The static array will be deallocated when the class goes out of scope.

---

### Post by dribeas on 2008-11-26
The code above has problems with indexes. Indexes into arrays start in 1. Also, as pointed by @thk, you can use three variables instead of 1 array to hold the three. You will get a slight advantage during object construction, that while it will not compensate for a high number of elements for three seems fine:

```

class Vector3D
{
public:
   Vector3D( double x, double y, double z ) 
      : x_( x ), y_( y ), z_( z ) 
   {}
private:
   double x_;
   double y_;
   double z_;
};

```

Initialization lists makes the compiler inject the values during construction. In your code, all elements in the array are first initialized with 0 just to be overwritten with the real value inside the constructor block.

As pointed by many, new and delete (similarly new[] and delete[]) go together. You should never delete (delete[]) anything that was not acquired with new (new[])

Nobody commented on the 'using' directive in a header file: don't do it. If you declare a using directive in a header file you are also declaring it in all compilation units that include your header, whether you like it or not. This can end in name collisions for an unexpected user that will be required to disambiguate:

> 
#include "your_header.h"

char endl = '\n';

std::cout << endl; // is this std::endl or the local endl?


On @dwitney67 collapse of constructors I cannot really agree:

> **dwhitney67 said:**
> 
[php]
class Vector3D
{
  public:
    // assign default value of zero to each parameter
    Vector3D(double x = 0, double y = 0, double z = 0);
    ...
  private:
    double vect[3];
};
[/php]


The semantics of the code above allow the user to create a Vector3D out of three or no arguments, as the OP code, but it also allows the user to create a Vector3D out of 1 or 2 arguments which might not be what the user wanted. The only way of forcing the user to enter either three or no values is coding the two constructors. 

There may also be a subtle problem in the code above: if you don't mark the constructor as explicit you are allowing the compiler to generate implicit conversions, which probably are unwanted. This is more graphically presented with a code sample:

```

void op_on_v( Vector3D const & v );
void op_on_d( double d );

int main()
{
   operation_on_v( 5.0 ); // meant operation_on_d, but misspellings happen
};

```

The compiler will not warn you of that mistake, it will silently construct a Vector3D using the one argument constructor (filling y and z with 0) and then call operation_on_v, as the user requested.

---

