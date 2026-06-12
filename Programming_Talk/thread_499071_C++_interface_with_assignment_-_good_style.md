---
title: "C++ interface with assignment - good style??"
date: 2007-07-12
forum: Programming Talk
---

### Post by c174 on 2007-07-12
I'm writting a program in which I want a Shape-object to represent different kinds of shapes (line, curve, etc). The specific type (line or curve) can be specified upon creation of the Shape-object. Also I want to be able to assign either a line or a curve to an existing Shape.

I have made this implementation (sorry it is a little long)

```
#include <iostream>
#include <typeinfo>
using std::cout;
using std::endl;

/* interface class called "Shape" which is meant to
 * be specialized by a "Line" class and "Curve" class
 */
class Shape {
public:
	Shape() { cout << "Shape constructor" << endl; }
	virtual ~Shape() { cout << "Shape desctructor" << endl; };

	// all "Shapes" must implement this
	virtual double getSlope() = 0;
	virtual void* getData() = 0;

	// specific for "Line"
	virtual int get_x() { cout << "overload this 1" << endl; return 0; }
	virtual int get_y() { cout << "overload this 2" << endl; return 0; }
	virtual void set_x( int x ) { cout << "overload this 3" << endl; }
	virtual void set_y( int y ) { cout << "overload this 4" << endl; }

	// specific for "Curve"
	virtual int get_a() { cout << "overload this 5" << endl; return 0; }
	virtual void set_a( int a ) { cout << "overload this 6" << endl; }

private:
	// never try to copy a "Shape" directly (it doesn't know about subclasses)
	Shape& operator=( Shape& rhs ) { cout << "Shape operator=" << endl; return *this; };
};


/* derived class "Line" based on "Shape"
 */
class Line : public Shape {
public:
	Line() : x(1), y(0) { cout << "Line constructor" << endl; }
	Line( void* rhs ) {
		cout << "Line constructor - initialized" << endl;
		x = ((Line*) rhs)->x;
		y = ((Line*) rhs)->y;
	}
	~Line() { cout << "Line destructor" << endl; }

	// overloaded function supplied by all implementors of "Shape"
	void* getData() { return this; }
	double getSlope() { return ((double) y)/x; }

	// specific functions available for a "Line" object
	int get_x() { return x; }
	int get_y() { return y; }
	void set_x( int xx ) { x = xx; }
	void set_y( int yy ) { y = yy; }
private:
	int x, y;
};

/* derived class "Curve" based on "Shape"
 */
class Curve : public Shape {
public:
	Curve() : a(1) { cout << "Curve constructor" << endl; }
	Curve( void* rhs ) {
		cout << "Curve constructor - initialized" << endl;
		a = ((Curve*) rhs)->a;		
	}
	~Curve() { cout << "Curve destructor" << endl; }
	
	// overloaded functions supplied by all implementors of "Shape"
	void* getData() { return this; }
	double getSlope() { return 2*a; }

	// specific functions available for a "Curve" object
	int get_a() { return a; }
	void set_a( int aa ) { a = aa; }
private:
	int a;
};


/* a wrapper called "SHAPE" which hides pointer and memory operations
 */
class SHAPE {
public:
	SHAPE() {
		cout << "SHAPE constructor default" << endl;
	}
	SHAPE( int n ) {
		switch(n) {
		case 1:
			cout << "SHAPE constructor Line" << endl;
			shape = new Line();			
			break;
		case 2:
			cout << "SHAPE constructor Curve" << endl;
			shape = new Curve();
			break;
		default:
			cout << "SHAPE constructor bad input" << endl;
			break;
		}
	}
	~SHAPE() {
		cout << "SHAPE destructor delete" << endl;
		if( shape )	delete shape;			
	}

	/* assignment */
	SHAPE& operator=( SHAPE& rhs ) {
		cout << "SHAPE operator=" << endl;

		// do nothing if assignment to itself
		if( this == &rhs ) { cout << "self" << endl; return *this; }

		// delete left hand side object
		if( this->shape ) delete this->shape;

		/* switch depending on object type on right hand side. This information is
		 * available through "typeid". Then assign the left hand side pointer to a
		 * newly created object, which is initialized through the constructor. In order
		 * to do this a reference for the right hand side object is passed to the constructor
		 * (accomplished by "getData"). Note that "getData" is overloaded from "Shape" so that
		 * "getData" gets resolved to the derived object instance on the right hand side.
		 */
		if( typeid(*rhs.shape) == typeid(Line) ) { this->shape = new Line(rhs.shape->getData()); }
		if( typeid(*rhs.shape) == typeid(Curve) ) { this->shape = new Curve(rhs.shape->getData()); }	

		// return a reference
		return *this;
	}

	// exposed functions from "any shape"
	double getSlope() { return shape->getSlope(); }

	// exposed from "Line"
	int get_x() { return shape->get_x(); }
	int get_y() { return shape->get_y(); }
	void set_x( int xx ) { shape->set_x(xx); }
	void set_y( int yy ) { shape->set_y(yy); }

	// exposed from "Curve"
	int get_a() { return shape->get_a(); }
	void set_a( int aa ) { shape->set_a(aa); }

private:
	Shape* shape;
};


int main( int argc, char *argv[] ) {	

	SHAPE shape1( 1 ); // a "Line" "Shape"
	SHAPE shape2( 2 ); // a "Curve" "Shape" 

	cout << "shape1: x: " << shape1.get_x() << endl;
	cout << "shape1: y: " << shape1.get_y() << endl;
	cout << "shape1: slope: " << shape1.getSlope() << endl << endl;

	cout << "shape2: a: " << shape2.get_a() << endl;
	cout << "shape2: slope: " << shape2.getSlope() << endl << endl;

	shape2 = shape1; // shape2 is changed from "Curve" "Shape" to "Line" "Shape"
	
	cout << "shape2 (=shape1): x: " << shape2.get_x() << endl;
	cout << "shape2 (=shape1): y: " << shape2.get_y() << endl;
	cout << "shape2 (=shape1): slope: " << shape2.getSlope() << endl << endl;
	
	shape1.set_x( 100 ); // this makes sense (shape1 is a "Line")
	shape2.set_a( 500 ); // this doesnt make sense (shape2 is a "Line")

	cout << "shape1: x: " << shape1.get_x() << endl; // makes sense
	cout << "shape2: x: " << shape2.get_x() << endl; // makes sense
	cout << "shape1: a: " << shape1.get_a() << endl; // no sense
	cout << "shape2: a: " << shape2.get_a() << endl; // no sense
	return 0;
}
```

Output from the program

```
SHAPE constructor Line
Shape constructor
Line constructor
SHAPE constructor Curve
Shape constructor
Curve constructor
shape1: x: 1
shape1: y: 0
shape1: slope: 0

shape2: a: 1
shape2: slope: 2

SHAPE operator=
Curve destructor
Shape desctructor
Shape constructor
Line constructor - initialized
shape2 (=shape1): x: 1
shape2 (=shape1): y: 0
shape2 (=shape1): slope: 0

overload this 6
shape1: x: 100
shape2: x: 1
overload this 5
shape1: a: 0
overload this 5
shape2: a: 0
SHAPE destructor delete
Line destructor
Shape desctructor
SHAPE destructor delete
Line destructor
Shape desctructor
```
My question is now: Is this a good implementation?? It seems a little complicated... Also, I think I do as much switching based on "typeid" as one would do if

1) In SHAPE the shape* pointer was changed to a void pointer
2) An extra variable (e.g. int) was added to remember the type of Shape (1=line, 2=curve)

So, I'm wondering if I'm doing this correctly? Any feedback/suggestion are appreciated.

---

### Post by GeneralZod on 2007-07-12
I think we're going to have to know a lot more about what exactly you are trying to do here because, as it stands, there is quite a lot wrong with your approach.

For a start: if a method is not applicable to all Shapes (as, I gather, e.g. set_x/ get_x/ set_y/ get_y wouldn't be ... ?) then (IMO) it simply has no place in a base class.

Giving each object a typeid and switching on it is generally considered bad OO form, as classes have these mechanisms built in already, so this is redundant and also means that adding a new class requires a change to the switch statement.  On top of that, the SHAPE class itself seems largely redundant - your example does not need it.

Give us more info on what your ultimate goal is, and we'll see if we can tear all this down and restructure it :)

Edit:

On a hunch - are you familiar with the dynamic_cast operator? If not, do a quick bit of research on it - I suspect it may make your life a little easier :)

---

### Post by c174 on 2007-07-12
Okay, to be more specific:

In my program I need to define a 1-dimensional shape. The most simple thing would be connected line segments: Given (x0, y0), (x1, y1), ... (xN, yN) one can interpolate the value at any "x". Another way to get a 1D curve is to use a cubic spline: Again sets of points are given (x0, y0), ... (xN, yN) plus the slope of the curve at each end: alpha0, alphaN.

My idea is to have some kind of interface in the program, so that I don't have to think about what kind of curve I am dealing with. At any time I want the interpolated y-value I just call some commen VAL-function.

At a later stage when actually running the program, one should be able to select which kind of curve to use.

So, the problem is that line-segments and a cubic spline both share a VAL-function, but these objects depend on different kind of data (alpha0 and alphaN are not needed for a connected line). Therefore they can share the VAL-function but not certain SET or GET function, etc.

--

I included the SHAPE class in the program to hide the shape* pointer - so I guess it is not a redundant class. It is not possible to define an assigment operator in the base class, since it doesn't know about the derived classes. Well... Mayby this is due to my "strange" design.

I agree that the switching part such not be there - this is why I am confused: How can I redesign and get rid of it? :)

--

Never used the dynamic_cast - I will look at it. And thanks! :)

---

### Post by the_unforgiven on 2007-07-12
> **c174 said:**
> Okay, to be more specific:

In my program I need to define a 1-dimensional shape. The most simple thing would be connected line segments: Given (x0, y0), (x1, y1), ... (xN, yN) one can interpolate the value at any "x". Another way to get a 1D curve is to use a cubic spline: Again sets of points are given (x0, y0), ... (xN, yN) plus the slope of the curve at each end: alpha0, alphaN.

My idea is to have some kind of interface in the program, so that I don't have to think about what kind of curve I am dealing with. At any time I want the interpolated y-value I just call some commen VAL-function.

At a later stage when actually running the program, one should be able to select which kind of curve to use.

So, the problem is that line-segments and a cubic spline both share a VAL-function, but these objects depend on different kind of data (alpha0 and alphaN are not needed for a connected line). Therefore they can share the VAL-function but not certain SET or GET function, etc.

--

I included the SHAPE class in the program to hide the shape* pointer - so I guess it is not a redundant class. It is not possible to define an assigment operator in the base class, since it doesn't know about the derived classes. Well... Mayby this is due to my "strange" design.

I agree that the switching part such not be there - this is why I am confused: How can I redesign and get rid of it? :)

--

Never used the dynamic_cast - I will look at it. And thanks! :)

So, a better design would be:

o. Encapsulate point in a struct - as (x,y) are related - they're not separate entities.
o. Line can be treated as a curve with constant slope between any two points - including extrapolated ones.

So a code like:
```

typedef struct
{
	int x, y;
} Point;

/*
 * This is the base curve class - maybe, an interface?
 */
class Curve
{
	public:
		virtual Point extrapolate(int x) = 0;

		virtual ~Curve() {}
};

class Line : public Curve
{
	private:
		std::vector<Point> points;
		int slope;
		int intercept;

	public:
		/*
		 * Constructors....
		 */

		Point extrapolate(int x)
		{
			int _y;
			_y = (slope * x) + intercept;
			Point p = { x, _y };
			points.append(p);
			return p;
		}

		~Line()
		{
			points.clear();
		}
};

class CurveWhatever : public Curve
{
	private:
		std::vector<Point> points;
                std::map<Point, int> slopes;  // This gives the map of points => slope (between pN and pN+1)
		// additional details to implement CurveWhatever...
	public:
		Point extrapolate(int _x)
		{	
			/*
			 * Implement the extrapolation logic
			 * as per the logic of CurveWhatever
			 * as shown in Line.
			 */
		}
                Point extrapolate(int _x, int slope)
                {
			/*
			 * Implement the extrapolation logic
			 * as per the logic of CurveWhatever
			 * as shown in Line.
			 */
                }
};

int main()
{
	Curve *v = new CurveWhatever;
	Curve *line = new Line;
	Point p = v->extrapolate(10);
        Point pNew = v->extrapolate(10, 0.58);
	Point point_on_line = line->extrapolate(10);
}

```
Fill in the blanks - this is not a complete working code, but just enough (hopefully ;)) to show the design ;)
HTH ;)

---

### Post by c174 on 2007-07-12
the_unforgiven: Thank you for your reply! I don't really see the difference between your implementation and mine. I mean

Shape (in my code)  = Curve in our code
Line (in my code) = Line in our code
Curve (in my code) = CurveWhatEver in our code

So what's the difference? Encapsulation of a Point is of course a good idea, but it is not what is giving me problems. My code has extra stuff in order to change a Line and Curve (or CurveWhatEver) after it is created as well as copying - I need this kind of operation.


Did I explain well enough what I am trying to do?

---

### Post by c174 on 2007-07-12
> **GeneralZod said:**
> For a start: if a method is not applicable to all Shapes (as, I gather, e.g. set_x/ get_x/ set_y/ get_y wouldn't be ... ?) then (IMO) it simply has no place in a base class.

Exactly not all methods are appllicable to all Shapes! So should I instead do something like

```

class Line {
public:
    Line() ;
    ~Line() ;
 
    double value( double );
    void set_x( double );
};

class Curve {
public:
    Curve();
    ~Curve();

    double value( double );
    void set_a( double );
};

class Shape {
public:
    Shape();
    ~Shape();

    double value( double x ) {
        switch( type ) {
        case 1:
            return line->value( x ); break;
        case 2:
            return curve->value( x ); break;
        default:
            // error
         }
    }

    void set( double x ) {
        switch( type ) {
        case 1:
             line->set_x( x ); break;
        case 2:
             curve->set_a( x ); break;
        default:
            // error
        }
     }
private:
    int type;
    Line* line;
    Curve* curve;
};

```

This is a handcraftet way I think.... Better in this case mayby??

---

### Post by the_unforgiven on 2007-07-12
> **c174 said:**
> the_unforgiven: Thank you for your reply! I don't really see the difference between your implementation and mine. I mean

Shape (in my code)  = Curve in our code
Line (in my code) = Line in our code
Curve (in my code) = CurveWhatEver in our code

So what's the difference? Encapsulation of a Point is of course a good idea, but it is not what is giving me problems. My code has extra stuff in order to change a Line and Curve (or CurveWhatEver) after it is created as well as copying - I need this kind of operation.


Did I explain well enough what I am trying to do?
There is no difference in the no. of classes - however, the abstractions that you have used are one level above  in the hierarchy than what I have used. This is mainly because I don't think your problem extends beyond that requirement - I mean, currently what you have described only pertains to extrapolation.

Moreover, converting from one form to the other requires quite a lot of code - you need to explicitly write it.
Sort of like implementing type casting operators yourself ;)
I would try to avoid that as far as I can - trying to think about alternative designs, maybe.. ;)

HTH ;)

---

### Post by GeneralZod on 2007-07-12
> **c174 said:**
> the_unforgiven: Thank you for your reply! I don't really see the difference between your implementation and mine. I mean

Shape (in my code)  = Curve in our code
Line (in my code) = Line in our code
Curve (in my code) = CurveWhatEver in our code

So what's the difference? Encapsulation of a Point is of course a good idea, but it is not what is giving me problems. My code has extra stuff in order to change a Line and Curve (or CurveWhatEver) after it is created as well as copying - I need this kind of operation.


Did I explain well enough what I am trying to do?

Copying should be trivial - just add a copy constructor to any class you want copied.  "Extra stuff" goes into the class definition of the type of shape that needs it - not its base class.  E.g. (all untested code)

```

// Abstract base class.
class AbstractCurve
{
public:
     AbstractCurve()  = 0;
     virtual ~Curve() = 0;
     Point extrapolate(int x) = 0;
}

// Line - a special kind of AbstractCurve
class Line : public AbstractCurve
{
public:
     Line(int x1, int y1, int x2, int y2 ) { ... construct line here ... };
     Line(const Line& sourceLine) { ... Copy constructor - construct from source line here ... };
     virtual ~Line() { ... destroy line here ... }
    
     // Overrides.
    Point extrapolate(int x)  { ... implement for line ... };


     // Line specific stuff
    int getX1() { return m_x1;};
    int getX2() {return m_x2;};
    void setX1(int x1) { m_x1 = x1;};
   // etc.
   
private:
    int m_x1, m_y1, m_x2, m_y2;
   // Other implementation details.    
}


// Quadratic curve of the form ax^x + bx + c
class Quadratic: public AbstractCurve
{
public:
     Quadratic(int a, int b, int c) { ... construct line here ... };
     Quadratic(const Quadratic& sourceQuadratic) { ... Copy constructor - construct from source Quadratic here ... };
     virtual ~Quadratic() { ... destroy Quadratic here ... }

     // Overrides.
    Point extrapolate(int x)  { ... implement for quadratic e.g. return m_a * x * x + m_b * x + c or something ... };


     // Quadratic specific stuff
    int geta() { return m_a;};
    int getb() { return m_b;};
    int seta() { return m_a;};
    int setb() { return m_b;};
   // etc.
   
private:
    int m_a, m_b, m_c;
   // Other implementation details.    
}

int main()
{
    Line line(0,0, 10, 10);
    Quadratic quadratic(5,3,4);
   
    line.setX1(5); // Only Line's can do this, but line is a Line, so no error occurs.
    quadratic.seta(3); // Only Quadratics's can do this, but quadratic is a Quadratic, so no error occurs.

    cout << "Line - extrapolating point at x = 3 " << line.extrapolate(3) << endl; // Will automatically call the Line class's implementation of extrapolate(int x);
    cout << "Quadratic - extrapolating point at x = 3 " << quadratic.extrapolate(3) << endl; // Will automatically call the Quadratic class's implementation of extrapolate(int x);
}

```

---

### Post by c174 on 2007-07-12
> **the_unforgiven said:**
> There is no difference in the no. of classes - however, the abstractions that you have used are one level above  in the hierarchy than what I have used. This is mainly because I don't think your problem extends beyond that requirement - I mean, currently what you have described only pertains to extrapolation.

Moreover, converting from one form to the other requires quite a lot of code - you need to explicitly write it.
Sort of like implementing type casting operators yourself ;)
I would try to avoid that as far as I can - trying to think about alternative designs, maybe.. ;)

HTH ;)

What do you mean by "level of abstraction"? I think the only difference is that I included the SHAPE-class, which is merely a wrapper around a pointer.... I don't want pointers directly exposed, because it makes things like copying and memory management much more difficult.

I would really like to think about other designs - but I can only think of those two already shown...! Good ideas a most welcome :)

---

### Post by the_unforgiven on 2007-07-12
> **c174 said:**
> Exactly not all methods are appllicable to all Shapes! So should I instead do something like

```

class Line {
public:
    Line() ;
    ~Line() ;
 
    double value( double );
    void set_x( double );
};

class Curve {
public:
    Curve();
    ~Curve();

    double value( double );
    void set_a( double );
};

class Shape {
public:
    Shape();
    ~Shape();

    double value( double x ) {
        switch( type ) {
        case 1:
            return line->value( x ); break;
        case 2:
            return curve->value( x ); break;
        default:
            // error
         }
    }

    void set( double x ) {
        switch( type ) {
        case 1:
             line->set_x( x ); break;
        case 2:
             curve->set_a( x ); break;
        default:
            // error
        }
     }
private:
    int type;
    Line* line;
    Curve* curve;
};

```

This is a handcraftet way I think.... Better in this case mayby??
You seem to be trying to access everything via the Shape interface - which I don't think is right.
A Shape interface should give access to only the required functionality.

If you're talking about curve functionality, use a concrete curve object.
If you need the line functionality, use the concrete line object. A shape cannot be everything at the same time.

For example, if we were to use the relationships (ISA/HAS-A), a Line IS A Shape, but a Shape may not be a line. At the same time, a Shape cannot HAVE a line - what you seem to be doing in the code above.
 
I hope I clarify your doubts at least to some extent. ;)

BTW, I'm just trying to help you - in no way I want to sound offensive to you.

---

### Post by c174 on 2007-07-12
> **the_unforgiven said:**
> BTW, I'm just trying to help you - in no way I want to sound offensive to you.

I think I should be saying this - about sounding offensive :(  Sorry

Well, I think I am getting it little by little: My design is "bad".

GeneralZod: I think you did what the_unforgiven just said, only use a Line-object for a line and a Quadratic-object for a quadratic curve. So I guess I'm just asking too much.

My idea was to allow for things like:

```

class Box {
public:
    Box( SHAPE left, SHAPE right, SHAPE bottom, SHAPE top );

   .... more stuff
};

int main( .... ) {

    Box first( Line(...), Line(...), Quadratic(...), Line(...) );
    Box second( Quadratic(...), Quadratic(...), Quadratic(...), Quadratice(...) );
   // other kinds of boxes....
}

```

But mayby this is only possible in the "hacking"-way I did it...?

---

### Post by the_unforgiven on 2007-07-12
> **c174 said:**
> What do you mean by "level of abstraction"? I think the only difference is that I included the SHAPE-class, which is merely a wrapper around a pointer.... I don't want pointers directly exposed, because it makes things like copying and memory management much more difficult.

I would really like to think about other designs - but I can only think of those two already shown...! Good ideas a most welcome :)
If I understand you correctly, what you have been using is following:
```

		Shape
		  |
	---------------------
	|		    |
	\/		    \/
	Line		  Curve
			    |
		     ---------------
		     |		   |
		     \/		   \/
		Quadratic	Cubic Spline

```

Whereas what I have in mind is:
```

		Curve
		  |
	----------------------------    
	|	     	|		   |	
	\/	 	\/		   \/
	Line 	    Quadratic		Cubic Spline

```
I guess, now the "level of abstractions" are clear ;)

---

### Post by c174 on 2007-07-12
> **the_unforgiven said:**
> 
For example, if we were to use the relationships (ISA/HAS-A), a Line IS A Shape, but a Shape may not be a line. At the same time, a Shape cannot HAVE a line - what you seem to be doing in the code above.

Using the "typeid" C++ can actually tell that a "Shape" IS A "Line" - only at runtime though. Probably this has misled my way of thinking

---

### Post by aquavitae on 2007-07-12
Line and Curve are inherited from Shape.  Shape defined pure virtual functions that are common between Line and Curve (e.g. value(int x)).  A new shape object (in this case a Line) can be declared as:
Shape* newshape = new Line();
Since it is a pointer to a Shape, and the common functions are virtual, it can be used for either Lines or Curves, and the function value(int x) can be used accurately regardless of whether it is a Line or a Curve. dynamic_cast can be used if you require a function specific to Line (e.g. set_x(int x)).

I think this is what the_unforgiven is doing.

---

### Post by GeneralZod on 2007-07-12
> **c174 said:**
> I think I should be saying this - about sounding offensive :(  Sorry

Well, I think I am getting it little by little: My design is "bad".

GeneralZod: I think you did what the un_forgiven just said, only use a Line-object for a line and a Quadratic-object for a quadratic curve. So I guess I'm just asking too much.

My idea was to allow for things like:

```

class Box {
public:
    Box( SHAPE left, SHAPE right, SHAPE bottom, SHAPE top );

   .... more stuff
};

int main( .... ) {

    Box first( Line(...), Line(...), Quadratic(...), Line(...) );
    Box second( Quadratic(...), Quadratic(...), Quadratic(...), Quadratice(...) );
   // other kinds of boxes....
}

```

But mayby this is only possible in the "hacking"-way I did it...?

We're confusing two different things, here - class hierarchies, and ways of encapsulating pointers.  The former isn't too hard; the latter comes under general memory management which is a huge topic that largely depends on precisely what you want to do.

```

// 4-sided shape.
class Box
{
public:
     enum Side {Left = 0, Right = 1, Top = 2, Bottom = 3}; // The numbering here is redundant, but is added for clarity
     Box(AbstractCurve* left, AbstractCurve* right, AbstractCurve* top, AbstractCurve* bottom) { // store left as m_sides[Left], etc }
     ~Box() { // Either call delete on each element of m_sides etc or leave that to the caller - your docs should stipulate which }
     Point extrapolateSide(Side side, int x) { return m_sides[side]->extrapolate(x);}; // This will automatically call the correct override of extrapolate(int x), depending on the run-time type of m_sides[side]
private:
     AbstractCurve* m_sides[4];
}


int main()
{
    Line *pLine1 = new Line(...blah...);
    Line *pLine2 = new Line(...blah...);
    Quadratic *pQ1 = new Quadratic(...blah...);
    Quadratic *pQ2 = new Quadratic(...blah...);
   Box box(pLine1, pQ2, pLine2, pQ1);
   cout << "Top side at x = 3 " << box.extrapolateSide(Box::Left, 3) << endl;
   // May or may not need to delete pLine1, pLine2 etc depending on whether Box does this when it is destroyed.
}

```

---

### Post by the_unforgiven on 2007-07-12
> **c174 said:**
> Using the "typeid" C++ can actually tell that a "Shape" IS A "Line" - only at runtime though. Probably this has misled my way of thinking
Yes, that is correct - you're misled.
What typeid returns is the actual type of object pointed to by the pointer - not the relationship.
So, if you do something like:
```

	Shape* line = new Line();
	Shape* curve = new Curve();

```
typeid(line) will say "Line", whereas typeid(curve) will say "Curve" - the way it translates into relationships is a Shape IS A Line and a Shape IS A Curve at the same time - which is wrong in the relationships term. The correct way to interpret typeid info is "The object pointed to by the pointer line IS A Line (which IS A Shape - that's why it could be pointed to by the Shape pointer) and the object pointed to by the pointer curve IS A Curve (which also IS A Shape)" 

I hope now it's clear to you ;)

Please feel free to ask questions even if it's not clear yet. We're here to help you ;)

---

### Post by c174 on 2007-07-12
> **the_unforgiven said:**
> If I understand you correctly, what you have been using is following:


Hehe, what I have done is the following
```


              SHAPE    --->      Shape
                                   |
                  -------------------------
                  |                      |
                  \/                     \/
                 Line              Curve (or QuadraticCurve - I did not use this term in the first posting)
```

The horizontal arrow is supposed to mean Aggregation. Don't know if this is common terminology/graphical representation

---

### Post by the_unforgiven on 2007-07-12
> **aquavitae said:**
> Line and Curve are inherited from Shape.  Shape defined pure virtual functions that are common between Line and Curve (e.g. value(int x)).  A new shape object (in this case a Line) can be declared as:
Shape* newshape = new Line();
Since it is a pointer to a Shape, and the common functions are virtual, it can be used for either Lines or Curves, and the function value(int x) can be used accurately regardless of whether it is a Line or a Curve. dynamic_cast can be used if you require a function specific to Line (e.g. set_x(int x)).

I think this is what the_unforgiven is doing.
No, dynamic_cast<> is best avoided - it is not trapped by the compiler.
Also, it MAY result in [object-slicing]("http://www.linuxtopia.org/online_books/programming_books/thinking_in_c++/Chapter15_017.html") (be ready for surprises ;)).
And, cross-hierarchy typecasts are never safe - e.g. typecasting a pointer to Line to a pointer to Curve (using OP's terminology) would definitely result in surprises.
That is, something like 
```

Shape* line = new Line();
Shape* curve = new Curve();
doSomething(curve);
....

void doSomething(Shape* line)
{
        Line* l = dynamic_cast<Line*>(line);
        l->foo();
}

```
is very much possible and dangerous. I mean, by mistake, instead of passing line to doSomething() if we pass curve, the compiler will never complain and we'd have surprises ;)
That is precisely why Java doesn't allow cross-casting - it only allows upcasting (and to some extent downcasting using explicit casts).

---

### Post by c174 on 2007-07-12
> **GeneralZod said:**
> ```

// 4-sided shape.
class Box
{
public:
     enum Side {Left = 0, Right = 1, Top = 2, Bottom = 3}; // The numbering here is redundant, but is added for clarity
     Box(AbstractCurve* left, AbstractCurve* right, AbstractCurve* top, AbstractCurve* bottom) { // store left as m_sides[Left], etc }
     ~Box() { // Either call delete on each element of m_sides etc or leave that to the caller - your docs should stipulate which }
     Point extrapolateSide(Side side, int x) { return m_sides[side]->extrapolate(x);}; // This will automatically call the correct override of extrapolate(int x), depending on the run-time type of m_sides[side]
private:
     AbstractCurve* m_sides[4];
}


int main()
{
    Line *pLine1 = new Line(...blah...);
    Line *pLine2 = new Line(...blah...);
    Quadratic *pQ1 = new Quadratic(...blah...);
    Quadratic *pQ2 = new Quadratic(...blah...);
   Box box(pLine1, pQ2, pLine2, pQ1);
   cout << "Top side at x = 3 " << box.extrapolateSide(Box::Left, 3) << endl;
   // May or may not need to delete pLine1, pLine2 etc depending on whether Box does this when it is destroyed.
}

```

This is nice.... I now realize that I was not thinking clear from the beginning. The above is what I need. Now I get it, I can't even explain what I was trying to do, because it doesn't make sense :) But I can sketch it - mayby you'll smile

```
class Box {
public:
    Box( ... );

    void set_edge( int n, double* xdata, double* ydata ) {
        adjust edge "n" to the data contained in "xdata" and "ydata"
        "somehow" be aware of the type of edge so that calling
        
             edge[n].setData( xdata, ydata )
        
       gets resolved to either a "Line" or "Quadratic" shape
     }
private:
     SHAPE edge[4];
};
```

Of course this can 'never' work. 1) The type of edge must be initialized. 2) The data to "set_edge" depends on the kind of edge I'm dealing with. 3) something extra is needed in order to specify the kind of shape.

 It *could* probably work with function-overloading and manipulations similar to the program in the first posting.

However, it is much better to create the new Shape first, and then pass that to the set-function.

Well, thank you for your advice and patience. I will review what I actually need and how I organise the various object... ;)

---

### Post by aquavitae on 2007-07-12
> **the_unforgiven said:**
> No, dynamic_cast<> is best avoided - it is not trapped by the compiler.
Also, it MAY result in [object-slicing]("http://www.linuxtopia.org/online_books/programming_books/thinking_in_c++/Chapter15_017.html") (be ready for surprises ;)).
And, cross-hierarchy typecasts are never safe - e.g. typecasting a pointer to Line to a pointer to Curve (using OP's terminology) would definitely result in surprises.
That is, something like 
```

Shape* line = new Line();
Shape* curve = new Curve();
doSomething(curve);
....

void doSomething(Shape* line)
{
        Line* l = dynamic_cast<Line*>(line);
        l->foo();
}

```
is very much possible and dangerous. I mean, by mistake, instead of passing line to doSomething() if we pass curve, the compiler will never complain and we'd have surprises ;)
That is precisely why Java doesn't allow cross-casting - it only allows upcasting (and to some extent downcasting using explicit casts).

I'm aware of the dangers of dynamic casting, but I couldn't see another way in this case.  I generally try to design classes so that I don't need to downcast, but don't always get it right :D.  Still, at least I check the cast before doing it using dynamic_cast<...>(...) == 0.

---

