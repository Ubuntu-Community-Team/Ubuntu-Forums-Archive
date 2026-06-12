---
title: "C++ problem"
date: 2008-09-23
forum: Programming Talk
---

### Post by Fuzar on 2008-09-23
i am a beginner to C++ programming and id really appreciate it if somebody could help me out with the following code:)..

#include <iostream>
#include <cmath>
#include<stdlib.h>
using namespace std;

class Point_class
{
friend double distance(Point_class & ,double ,double , double );
public:
	Point_class(double=0,double=0,double=0)
    {}  //default constructor initializes x,y,z valus to zero

	void Point_Class(char*,double, double, double);

	void setCoords(double , double , double );

	void setName(char*);

	void printCoord() const;

private:
	double xcoord;
	double ycoord;
	double zcoord;
	char id[10];

};

void Point_class::setCoords(double xco, double yco, double zco)
{
	xcoord=xco;
	ycoord=yco;
	zcoord=zco;
}
void Point_class::setName(char*name)
{
	id[10]=*name;
}

void Point_class::printCoord() const
{
	cout<< "X-Coordinate is  "<< xcoord <<endl;
    cout<< "Y-Coordinate is  "<< ycoord <<endl;
     cout<< "Z-Coordinate is  "<< zcoord <<endl;

	cout<< "Name is " <<&id[10]<<endl;

}
void Point_class::Point_Class(char*name,double xco,double yco,double zco)
{     
      name=name;
      xcoord=xco;
      ycoord=yco;
      zcoord=zco;
}

double distance(Point_class &a,double x, double y,  double z)
{   
    double x1,x2,y1,y2,z1,z2,dist;
    a.xcoord=pow((x1-x2),2);
    a.ycoord=pow((y1-y2),2);
    a.zcoord=pow((z1-z2),2);
    return dist=sqrt(x+y+z);
    
    
}

int main()
{
	double myDistance;
    Point_class dist;

	dist.setCoords(1.0,2.5,3.0);
	dist.setName("A");
	dist.printCoord();
	myDistance=distance(Point_class &a,double x,double y,double z);
cout<<"The Distance is "<<myDistance<<endl;
system ("Pause");
return 0;
}

---

### Post by kjohansen on 2008-09-23
you need to give more details... what do you mean help?  is something broken? what is it supposed to do?

---

### Post by dwhitney67 on 2008-09-23
Here are some comments:

1.  Instead of stdlib.h, use cstdlib

2.  When declaring functions and constructors within a class definition, provide names for the parameters, or at least at a minimum, document each function so that the reader (that is me) does not have to refer to the implementation to determine what each parameter is.

3.  You have not fully implemented your default constructor.  You need to set your member data to the values given (if any).  If no values (parameters) are given, then defaulting the coordinates to zero is ok.  It is helpful if you heed comment #2 above.

Essentially, one should be able to construct a Point_class like the following:
[php]
Point_class dist( 1.0, 2.5, 3.0 );
[/php]

4.  Your class member data 'id' should more appropriately defined to be an STL string.  Otherwise you will need to rely on C-library functions to handle setting the char array.
[php]
#include <string>
...
  private:
    std::string id;
...
[/php]

5.  The setName() method is implemented incorrectly.  If 'id' is a string (see comment #4), then the following will work:
[php]id = name;[/php]

6.  In printCoord(), you do not need to place an & before 'id'.

7.  Do not declare your variables (in the main program or wherever) until they are needed, and when you declare something, initialize it immediately.  For example:
[php]double myDistance = distance( dist, // etc. ); [/php]

8.  You need to pass values to distance(); you are passing declarations for x, y, and z!  For example:
[php]
myDistance = distance( dist, 1.0, 2.0, 3.0 );
[/php]

9.  Consider providing more white-space in your code.  For instance:
[php]
double x1, x2, y1, y2, z1, z2;

// And the values for x1, x2, y1, y2, z1, and z2 are what???

a.xcoord = pow((x1 - x2), 2);
a.ycoord = pow((y1 - y2), 2);
a.zcoord = pow((z1 - z2), 2);

return sqrt(x + y + z);   // note, dist not needed
[/php]

10.  Do not use system("pause").  It is not portable.  If you require the program to halt so that you can view the output, then prompt the operator to press 'enter' or something similar.  Use cin or a simple getchar().


Well, that's 10 comments.  That should give you something to do.  I look forward to the next evolution of your code.

---

### Post by dribeas on 2008-09-23
Agree with @dwhitney67, some other things to consider:

11. I would remove suffixes (_class for the class, coord for coordinates) and add others (suffix or prefix _ to identify that they are private members).

12. Your constructor is problematic, it allows constructing with any number of parameters from 0 to 3, and what is worse, it allows implicit conversions from double. Consider providing two constructors:

```

class Point
{
public:
   Point() : x_(0), y_(0), z_(0) {}
   Point( double x, double y, double z ) : x_(x), y_(y), z(z) {}
};

```

Or if you do need to build Points with just one coordinate (??) mark the constructor as explicit to disallow implict conversions:

```

class Point
{
public:
   explicit Point( double x = 0, double y = 0, double z = 0 ); //...
};
void f( Point const & x );
void g()
{
   f( 5 ); // error
}

```

If the constructor above was not 'explicit' g() would compile and silently convert 5 into a point with x coordinate 5, which is error prone.

13. You will probably want to have accessors to your coordinates, if you provide them, then distance() does not need to be a friend anymore.

14. Consider changing your print() signature and adding operator<< to:
```

class Point
{
   void print( std::ostream& o ) const;
};
std::ostream& operator<<( std::ostream& o, Point const & p )
{
   p.print( o );
   return o;
}

```

This will allow you to output your Point to stdout/stderr/fstream with just one method and 'naturally'.

15. Reread your pointer knowledge, this code snippets says that you don't have those concepts clear (even if you should as @dwhitney67 already said and change the data element to std::string):
```

id[10]=*name;
cout<< "Name is " <<&id[10]<<endl;

```

---

