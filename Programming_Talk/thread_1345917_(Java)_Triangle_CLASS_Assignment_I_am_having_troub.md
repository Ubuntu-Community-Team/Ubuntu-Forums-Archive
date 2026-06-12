---
title: "(Java) Triangle CLASS Assignment I am having trouble with"
date: 2009-12-04
forum: Programming Talk
---

### Post by s3a on 2009-12-04
The first and second code boxes were written by my teacher so they are correct. The third one was worked on by me and seems to be correct but am just mentioning it in case it could be where to look for a problem. The fourth and last code box is what I am working on right now and I'm having trouble with it. My questions are included as comments in the fourth code box.

```
public class PointDemo
{
   public static void main(String[] args)
   {
      Point p = new Point();	// create a point
      System.out.println();
      System.out.println(p);	// Java does this:  System.out.println(p.toString());

      p.translate(2,3);
      System.out.println();
      System.out.println("p = " + p);
      System.out.println();
      System.out.println("length of p = " + p.length());
      Point q = new Point(7, 3);
      System.out.println();
      System.out.println("distance between " + p + " and " + q + " is " + p.distance(q));
      System.out.println();
      System.out.println("dot product of " + p + " and " + q + " is " + p.dotProduct(q));
      Point r = new Point(q);
      System.out.println();
      System.out.println("r = " + r);
      System.out.println();
      System.out.println("it is " + r.equals(q) + " that " + r + " and " + q + " are equal");
      Point s = new Point(5);
      System.out.println();
      System.out.println("s = " + s);
      if( s.equals(q) )
         {
         System.out.println();
         System.out.println("it is true that " + s + " and " + q + " are equal");
         }
      else
         {
			 System.out.println();
			 System.out.println("it is false that " + s + " and " + q + " are equal");
		 }
      Point t = new Point(new Point(1,1));
      System.out.println();
      System.out.println("t = " + t);
      t.move(p);
      System.out.println();
      System.out.println("t = " + t);
      t.move(new Point(3,3));
      System.out.println();
      System.out.println("t = " + t);
      Point u = t.getPoint();
      System.out.println();
      System.out.println("u = " + u);

   }
}
```

```
public class TriangleDemo
{
   public static void main(String[] args)
   {
      Triangle t = new Triangle();
      System.out.println("Triangle t: " + t);
      System.out.println("Perimeter of t: " + t.perimeter());
      System.out.println("Area of t: " + t.area());
      Point p1 = new Point(1,2);
      Point p2 = new Point(2,1);
      Point p3 = new Point(3,4);
      Triangle r = new Triangle(p1, p2, p3);
      System.out.println("Triangle r: " + r);
      System.out.println("SideA of r: " + r.sideA());
      System.out.println("SideB of r: " + r.sideB());
      System.out.println("SideC of r: " + r.sideC());
      Triangle s = new Triangle(t.getB(), t.getC(), t.getA());
      if( s.equals(t) )
         System.out.println("Triangles s and t are equal");
      else
         System.out.println("Triangles s and t are not equal");
      if( s.equals(r) )
         System.out.println("Triangles s and r are equal");
      else
         System.out.println("Triangles s and r are not equal");
   }
}
```

```
public class Point
{
	// Instance fields
	private int x;
	private int y;

	// Mutators:
	public void setX(int p)
	{
		this.x = p;
	}

	public void setY(int p)
	{
		this.y = p;
	}
	// Accessors:
	public double getX()
	{
		return x;
	}
	public double getY()
	{
		return y;
	}
/*
The default (no-arguments) constructor, constructing the point (1; 1).
Usage example: Point p = new Point(); // p = (1,1)
*/
	public Point()
	{
		this.x = 1;
		this.y = 1;
	}
/*
A constructor that can take one value m, constructing the point (m;m).
Usage example: Point p = new Point(5); // p = (5,5)
*/
	public Point(int x)
	{
		this.x = x;
		this.y = x;
	}
/*
A constructor that can take two values m and n, constructing the point (m; n).
Usage example: Point p = new Point(3,7); // p = (3,7)
*/
	public Point(int x, int y)
	{
		this.x = x;
		this.y = y;
	}
 /*
 A constructor that that takes a Point p as a parameter, constructing and initial-
izing a point with the same x and y coordinates as p.
Usage example: Point p = new Point(9,4);
Point q = new Point(p); // q = (9,4)
*/
	public Point(Point p)
	{

		this.x = p.x;
		this.y = p.y;
	}
// Accessor method getPoint() that returns this point.
	//public Point getPoint(int x, int y)
	public Point getPoint()
	{
		//return this.Point; // I think this is one of the errors!!!!!!!!!!!!!!!!!!!
		return new Point(this.x, this.y);	// or equivalently, return new Point(x, y);
											// or equivalently, return new Point(this);
	}
	/*
	 * A toString() method that returns the string (x, y), where x and y are the coordinate
	 * values of this point. (Recall that the this object is the same as the object calling a
	 * method.)
	*/
	//public String toString(Point p)
	public String toString()
	{
		//this.x = p.x;
		//this.y = p.y;
		//String p1 = "( " + this.x + " , " + this.y + " )";
		//return p1; // I think this is one of the errors!!!!!!!!!!!!!!!!!!!!!!
		String result = "POINT (" + x + " , " + y + ")";
		return result;
	}
// A method length() that takes no parameters, and returns the length of this point:
	public double length()
	{
		double distance = Math.sqrt(Math.pow(this.x, 2) + Math.pow(this.y, 2));
		return distance;
	}
	/*
	 * A method distance() that takes a Point p as a parameter and returns the distance
	 * between p and this point.
	 * sqrt((x1 &#8722; x2 )^2 + (y1 &#8722; y2 )^2).The distance between two points (x1 , y1 ) and (x2 , y2 ) is defined as
	*/
    public double distance(Point p)
    {
    	double distance = Math.sqrt(Math.pow((this.x - p.x), 2) + Math.pow((this.y - p.y),2)); // Is the formula implemented properly?
    	return distance;
	}

	/*	A method translate() that takes two double parameters deltaX and deltaY and
	translates the current location of this point (x, y) to (x+deltaX, y+deltaY). */
	public void translate(int deltaX, int deltaY)
	{
		this.x += deltaX;
		this.y += deltaY;
	}
	/* A method move() that takes a Point p as a parameter, and moves this point to p. */
	public void move(Point p)
	{
		//this.x = p.x; // WAS THIS CORRECT?
		//this.y = p.y; // WAS THIS CORRECT?
		p.x = this.x; // IS THIS CORRECT?
		p.y = this.y; // IS THIS CORRECT?
	}
	/* A method dotProduct() that takes a Point p as a parameter and returns the dot
	product of p and this point. The dot product of two points (x1; y1) and (x2; y2) is
	defined as x1x2 + y1y2. */
	public int dotProduct(Point p)
	{
		int dotProduct = (this.x * p.x + this.y * p.y); //what's the difference between this.x and p.x for example?
		return dotProduct;
	}
	 /*
	  * a method equals() that takes an Object obj as a parameter, and returns true if and
	  * only if Object obj is not null and is an instance of Point that has the same x and y
	  * coordinates as this object.
	 */
	public boolean equals(Object obj) // Figure this out!
	{
		boolean result;
		Point q = (Point)obj;
		if(obj == null)
		result = false;
		if(this.x == q.x && this.y == q.y)
		result = true;
		else
		result = false;
		return result;
	}
}
```

```
public class Triangle
{
// Instance Fields
	private Point A;
	private Point B;
	private Point C;
// Two constructors

// The default constructor, creating the triangles with vertices at (1,1), (5,5), and (1,5).
	public Triangle()
	{
**		Point A = getPoint(1,1); // Is this correct?**
**		Point B = getPoint(5,5); // Is this correct?**
**		Point C = getPoint(1,5); // is this correct?**
	}
/*
	* A non-default constructor that can take three Point parameters p1, p2, and p3,
	* initializing the vertices A, B, and C of the triangle under construction to p1, p2,
	* and p3, respectively.
*/
	public Triangle(Point p1, Point p2, Point p3)
	{
**		Point A = new Point(p1); // Is this correct?**
[B]		Point B = new Point(p2); // is this correct?
		Point C = new Point(p3); // is this correct?[/B]
	}
/*
 * three accessors getA(), getB(), and getC() that return the vertices A, B, and C of this
 * triangle, respectively.
 * three mutator setA(), setB(), and setC() that each take a Point as a parameter, and
 * set the vertices A, B, and C to the supplied point, respectively.
*/
	public Point getA()
	{
**		return Point(this.x, this.y); // Is this correct?**
	}
	public int getB()
	{
**		return Point(this.x, this.y); // Is this correct?**
	}
	public int getC()
	{
**		return Point(this.x, this.y); // Is this correct?**
	}
/*
	 * three mutator setA(), setB(), and setC() that each take a Point as a parameter, and
	 * set the vertices A, B, and C to the supplied point, respectively.
*/
	public void setA(Point p)
	{
**		Point A = p; // Is this correct?**
	}
	public void setB(Point p)
	{
**		Point B = p; // Is this correct?**
	}
	public void setC(Point p)
	{
**		Point C = p; // Is this correct?**
	}
// A method sideA() that returns the distance between the vertices B and C.
	public double sideA()
	{
		**double distance = Math.sqrt(Math.pow(((double)B - (double)C), 2)); // Is this correct? (I typecasted in order to return distance as a double - the above is an attempt to use the distance formula "sqrt((x2-x1)^2 + (y2-y1)^2)")**
		return distance;
	}
// A method sideB() that returns the distance between the vertices A and C.
	public double sideB()
	{
		**double distance = Math.sqrt(Math.pow(((double)A - (double)C), 2)); // Is this correct? (I typecasted in order to return distance as a double - the above is an attempt to use the distance formula "sqrt((x2-x1)^2 + (y2-y1)^2)")**
		return distance;
	}
// A method sideC() that returns the distance between the vertices A and B.
	public double sideC()
	{
		**double distance = Math.sqrt(Math.pow(((double)A - (double)B), 2)); // Is this correct? (I typecasted in order to return distance as a double - the above is an attempt to use the distance formula "sqrt((x2-x1)^2 + (y2-y1)^2)")**
		return distance;
	}
// A method perimeter() that returns the perimeter of this triangle.
	public double perimeter()
	{
		double perimeter = sideA() + sideB() + sideC();
		return perimeter;	
	}
// a method area() that returns the area of this triangle.
	public double area()
	{
		double area = 5; // implement actual formula later
		return area;
	}

/* A toString() method that returns a String of the form (x1 , y1 ), (x2 , y2 ), (x3 , y3 ) where
(x1 , y1 ), (x2 , y2 ), and (x3 , y3 ) represent the coordinates of the vertices A, B, and C of this
triangle, respectively.*/
	public String toString()
	{
		String result = "TRIANGLE" + "(" + getA() + ") (" + getB() + ")" + + "(" + getC() + ")";
		return result;
	}

/*  A method equals() that takes an Object obj as a parameter, and returns true if and
only if obj is not null and is an instance of Triangle that has the same area and
perimeter as this object.
*/
	public boolean equals(Object obj)
	{
		Triangle q = (Triangle)obj;
		if(obj == null)
		{
			return true;
		}
		else
		{
			return false;
		}

	}
}
```

Any help would be GREATLY appreciated!
Thanks in advance!

---

### Post by dwhitney67 on 2009-12-04
```

public Triangle()
{
   Point A = getPoint(1,1); // Is this correct?
   Point B = getPoint(5,5); // Is this correct?
   Point C = getPoint(1,5); // is this correct?
}

```
You have already defined A, B, and C as private members of the Triangle class, thus you do not want to define them again.  But you do need to initialize them, like...
```

public Triangle()
{
   A = new Point(1,1);
   B = new Point(5,5);
   C = new Point(1,5);
}

```

For your other question...
```

public Triangle(Point p1, Point p2, Point p3)
{
   A = new Point(p1);
   B = new Point(p2);
   C = new Point(p3);
}

```

---

### Post by s3a on 2009-12-05
Thanks! It makes sense not to define them again. But I still get the same amount of errors:

[B]javac Triangle.java
Triangle.java:12: cannot find symbol
symbol  : method getPoint(int,int)
location: class Triangle
		A = getPoint(1,1);
		    ^
Triangle.java:13: cannot find symbol
symbol  : method getPoint(int,int)
location: class Triangle
		B = getPoint(5,5);
		    ^
Triangle.java:14: cannot find symbol
symbol  : method getPoint(int,int)
location: class Triangle
		C = getPoint(1,5);
		    ^
Triangle.java:35: cannot find symbol
symbol  : variable x
location: class Triangle
		return Point(this.x, this.y);
		                 ^
Triangle.java:35: cannot find symbol
symbol  : variable y
location: class Triangle
		return Point(this.x, this.y);
		                         ^
Triangle.java:39: cannot find symbol
symbol  : variable x
location: class Triangle
		return Point(this.x, this.y);
		                 ^
Triangle.java:39: cannot find symbol
symbol  : variable y
location: class Triangle
		return Point(this.x, this.y);
		                         ^
Triangle.java:43: cannot find symbol
symbol  : variable x
location: class Triangle
		return Point(this.x, this.y);
		                 ^
Triangle.java:43: cannot find symbol
symbol  : variable y
location: class Triangle
		return Point(this.x, this.y);
		                         ^
Triangle.java:64: inconvertible types
found   : Point
required: double
		double distance = Math.sqrt(Math.pow(((double)B - (double)C), 2));
		                                              ^
Triangle.java:64: inconvertible types
found   : Point
required: double
		double distance = Math.sqrt(Math.pow(((double)B - (double)C), 2));
		                                                          ^
Triangle.java:70: inconvertible types
found   : Point
required: double
		double distance = Math.sqrt(Math.pow(((double)A - (double)C), 2));
		                                              ^
Triangle.java:70: inconvertible types
found   : Point
required: double
		double distance = Math.sqrt(Math.pow(((double)A - (double)C), 2));
		                                                          ^
Triangle.java:76: inconvertible types
found   : Point
required: double
		double distance = Math.sqrt(Math.pow(((double)A - (double)B), 2));
		                                              ^
Triangle.java:76: inconvertible types
found   : Point
required: double
		double distance = Math.sqrt(Math.pow(((double)A - (double)B), 2));
		                                                          ^
Triangle.java:97: operator + cannot be applied to java.lang.String
		String result = "TRIANGLE" + "(" + getA() + ") (" + getB() + ")" + + "(" + getC() + ")";
		                                                                   ^
16 errors[/B]

_On my Point.java program:_
```
// Accessor method getPoint() that returns this point.
	//public Point getPoint(int x, int y)
	public Point getPoint()
	{
		//return this.Point; // I think this is one of the errors!!!!!!!!!!!!!!!!!!!
		return new Point(this.x, this.y);	// or equivalently, return new Point(x, y);
											// or equivalently, return new Point(this);
	}
```

Do I have to change public Point getPoint() to public Point getPoint(int x, int y)? I think it's already right the way it is because if I remember correctly, my teacher changed that for me (but I could be wrong). The reason I am suggesting this is because in the Triangle.java program, _I am calling the getPoint method with two integers as shown here:_
```
A = getPoint(1,1);
B = getPoint(5,5);
C = getPoint(1,5);
```

Or is the code in the Triangle program wrong instead?

As for my other errors, I think the compilation error speaks enough for itself. It would be great if you can help me solve these problems and explain why it is the case that I cannot do what I have done and why it is the case for me to have to do what will be suggested. If the compilation error does not provide you enough information with my problem and you want to know more about "what is going on in my brain," just ask and I'll fill you in.

Thanks!

---

### Post by LKjell on 2009-12-05
A bit inconsistency in

```
	public Point getA()
	{
		return Point(this.x, this.y); // Is this correct?
	}
	public int getB()
	{
		return Point(this.x, this.y); // Is this correct?
	}
	public int getC()
	{
		return Point(this.x, this.y); // Is this correct?
	}

```

---

### Post by s3a on 2009-12-05
Sorry but I don't understand exactly what it is you're trying to tell me.

---

### Post by dwhitney67 on 2009-12-05
> **s3a said:**
> Sorry but I don't understand exactly what it is you're trying to tell me.

I know you are referring to LKjell's post, but let me borrow your time to recant what I posted earlier... which you seemed to have ignored.

When constructing a Triangle, you need to define three Points.  What in pray-tell does getPoint() have to do with this will remain a mystery.  I guess you think in tangents.

You want to construct a Triangle with three points:
```

public class Point
{
   private int x, y;

   public Point(int x, int y)
   {
      this.x = x;
      this.y = y;
   }

   // ...
}

public class Triangle
{
   private Point vertex_A;
   private Point vertex_B;
   private Point vertex_C;

   public Triangle()
   {
      vertex_A = new Point(1, 1);
      vertex_B = new Point(5, 5);
      vertex_C = new Point(1, 5);
   }

   // ...

   static void main(String[] args)
   {
      Triangle bermuda = new Triangle();
   }
}

```
Of course, what would be better would be to have a Triangle constructor that accepted the three Points that define its vertices.  Something like:
```

public Triangle
{
   ...

   public Triangle(Point A, Point B, Point C)
   {
      vertex_A = A.clone();
      vertex_B = B.clone();
      vertex_C = C.clone();
   }

   ...
}

```

---

### Post by s3a on 2009-12-06
Sorry if I am not getting everything you people say. I am not purposely ignoring any comments. Instead of calling it something else like vertex_A etc, I can use "this," right? Also, my teacher would like it more if I did it his way by calling it p1, p2 and p3 instead of something else like A, B and C I would think not that it actually matters (unless I am not understanding correctly).

So what about?:

```
public Triangle(Point p1, Point p2, Point p3)
{
	A = setA(p1);
	B = setB(p2);
	C = setC(p3);
}
```

As for: "When constructing a Triangle, you need to define three Points. What in pray-tell does getPoint() have to do with this..." I changed it to the following and still get many errors:
```
public class Triangle
{
// Instance Fields
	private Point A, B, C;
	
// Two constructors

// The default constructor, creating the triangles with vertices at (1,1), (5,5), and (1,5).
	public Triangle()
	{
		A = setA();
		B = setB();
		C = setC();
		//A = A.getPoint(1,1);
		//B = B.getPoint(5,5);
		//C = C.getPoint(1,5);
	}
/*
	* A non-default constructor that can take three Point parameters p1, p2, and p3,
	* initializing the vertices A, B, and C of the triangle under construction to p1, p2,
	* and p3, respectively.
*/
	public Triangle(Point p1, Point p2, Point p3)
	{
		//this.A = A.Point(p1);
		//this.B = B.Point(p2);
		//this.C = C.Point(p3);
		A = setA(p1);
		B = setB(p2);
		C = setC(p3);
	}
/*
 * three accessors getA(), getB(), and getC() that return the vertices A, B, and C of this
 * triangle, respectively.
 * three mutator setA(), setB(), and setC() that each take a Point as a parameter, and
 * set the vertices A, B, and C to the supplied point, respectively.
*/
	public Point getA()
	{
		return Point(this.x, this.y);
	}
	public int getB()
	{
		return Point(this.x, this.y);
	}
	public int getC()
	{
		return Point(this.x, this.y);
	}
/*
	 * three mutator setA(), setB(), and setC() that each take a Point as a parameter, and
	 * set the vertices A, B, and C to the supplied point, respectively.
*/
	public void setA(Point p)
	{
		Point A = p;
	}
	public void setB(Point p)
	{
		Point B = p;
	}
	public void setC(Point p)
	{
		Point C = p;
	}
// A method sideA() that returns the distance between the vertices B and C.
	public double sideA()
	{
		double distance = Math.sqrt(Math.pow(((double)B - (double)C), 2));
		return distance;
	}
// A method sideB() that returns the distance between the vertices A and C.
	public double sideB()
	{
		double distance = Math.sqrt(Math.pow(((double)A - (double)C), 2));
		return distance;
	}
// A method sideC() that returns the distance between the vertices A and B.
	public double sideC()
	{
		double distance = Math.sqrt(Math.pow(((double)A - (double)B), 2));
		return distance;
	}
// A method perimeter() that returns the perimeter of this triangle.
	public double perimeter()
	{
		double perimeter = sideA() + sideB() + sideC();
		return perimeter;	
	}
// a method area() that returns the area of this triangle.
	public double area()
	{
		double area = 5; // implement actual formula later
		return area;
	}

/* A toString() method that returns a String of the form (x1 , y1 ), (x2 , y2 ), (x3 , y3 ) where
(x1 , y1 ), (x2 , y2 ), and (x3 , y3 ) represent the coordinates of the vertices A, B, and C of this
triangle, respectively.*/
	public String toString()
	{
		String result = "TRIANGLE" + "(" + getA() + ") (" + getB() + ")" + "(" + getC() + ")";
		return result;
	}

/*  A method equals() that takes an Object obj as a parameter, and returns true if and
only if obj is not null and is an instance of Triangle that has the same area and
perimeter as this object.
*/
	public boolean equals(Object obj)
	{
		Triangle q = (Triangle)obj;
		if(obj == null)
		{
			return true;
		}
		else
		{
			return false;
		}

	}
}
```

As you probably have noticed, I am lost even though I already did read the whole chapter in my book and actually understand everything the book says but I still get lost when things become a little more complex like in this assignment but the more hints I get and the more I work at it, the more I understand so please don't think I'm just looking for answers...like this is actually helping me.

---

### Post by ve4cib on 2009-12-06
I've edited your code and cleaned it up, made some corrections, and added some comments explaining how things could work.  Most of the code is more-or-less what you already had, with the exception of your get/set methods.  I don't know what you were trying to do before, but it made no sense.

Usually a method like "getA()" will simply return a private field called "a".  Likewise "setA(arg)" will assign the value arg to the private field a.  Get methods are rarely more than a single return statement.  Set methods are often simply one line ("a = arg;" if we use the example from earlier), but sometimes more logic and validation is necessary.

In the code below I've only written setA and getA; you should be able to figure out setB, setC, getB, and getC easily enough.

Your length methods looked a little weird.  If you think back to your junior high/high school linear algebra you'll remember that the equation for the distance between two points on a graph is:

sqrt((x1-x2)^2 + (y1-y2)^2)

You can use that exact formula to calculate the length of each edge of the triangle; you have the points already -- which I assume are X/Y coordinates.

Your equals method also looked kind of weird, but it was mostly on the right track.  I've filled it in a little bit, and made some comments in it below to help you along the rest of the way.

Anyway, hopefully some of what's below will help you out.  Don't just copy-and-paste my code; read it and make sure you understand it.  If you've got more questions post them and we'll see what we can do to answer them.

```

/**
 * A simple triangle, represented by 3 points in two-dimensional space
 **/
public class Triangle
{
    // the three points that form the triangle
    private Point ptA, ptB, ptC;
	

    // The default constructor, creating the triangles with vertices at
    // (1,1), (5,5), and (1,5).
    public Triangle()
    {
        // create the points and store them
        this.ptA = new Point(1,1);
        this.ptB = new Point(5,5);
        this.ptC = new Point(1,5);
    }

    /*
     * A non-default constructor that can take three Point parameters 
     * p1, p2, and p3,
     * initializing the vertices A, B, and C of the triangle under
     * construction to p1, p2, and p3, respectively.
     **/
    public Triangle(Point p1, Point p2, Point p3)
    {
        // we cou;d also create new copies of the points, but I
        // personally think it makes more sense to use the points
        // we were passed in.  See earlier posts for now to clone
        // the Point objects if you need to
        this.ptA = p1;
        this.ptB = p2;
        this.ptC = p3;
    }

    /**
     * three accessors getA(), getB(), and getC() that return the 
     * vertices A, B, and C of this triangle, respectively.
     **/
    public Point getA() 
    {
        // simply return the point.  Alternatively you could return
        // a new copy of the point if necessary (again, see earlier
        // in the thread for how to create a new copy)
        return this.ptA;
    }

    ...

    /**
     * three mutator setA(), setB(), and setC() that each take a Point as 
     * a parameter, and set the vertices A, B, and C to the supplied 
     * point, respectively.
     **/
    public Point setA(Point p)
    {
        // again, we could create a new copy of p and store that, but
        // it's easier to just store the point we were passed in
        this.ptA = p;
    }

    ...

    /**
     * lengthAB(), lengthAC(), and lengthBC(), which calculate and return
     * the distance between the vertices A-B, A-C, and B-C
     **/
    public double lengthAB() 
    {
        // using the pythagorean theorem we can calculate the length
        // of the line segment.  note that i am assuming the Point
        // class has an X and a Y component that is accessible.
        // The distance between two points in 2D space is:
        //   sqrt((x1-x2)^2 + (y1-y2)^2)

        double dX = this.ptA.getX() - this.ptB.getX();  //x1-x2
        double dY = this.ptB.getY() - this.ptB.getY();  //y1-y2

        // sqrt((x1-x2)^2 + (y1-y2)^2)
        return Math.sqrt(Math.pow(dX,2.0) + Math.pow(dY,2.0));
    }

    ...


    // A method perimeter() that returns the perimeter of this triangle.
    public double perimeter()
    {
        // you had this pretty much right; just sum the lengths of each
        // side together and return it.
    }

    // a method area() that returns the area of this triangle.
    public double area()
    {
        // I'm not helping you with this one until you implement your
        // version of the formula and post it
        double area = 5; // implement actual formula later
        return area;
    }

    /**
     * A toString() method that returns a String of the form 
     * "(x1 , y1), (x2 , y2), (x3 , y3)"
     **/
    public string toString()
    {
        // assuming that Point's toString() function returns "(x , y)"
        // then this should work
        string result = "TRIANGLE" + " " + getA() + " , " + getB() + " , " + getC();
        return result;
    }

    /**
     * A method equals() that takes an Object obj as a parameter, and 
     * returns true if and only if obj is not null and is an instance of 
     * Triangle that has the same area and perimeter as this object.
     **/
    public boolean equals(Object obj)
    {
        // first off we need to check if the object is a Triangle
        // we could use instanceof, but it's arguably easier to
        // just try casting it, and if it's not a Triangle then
        // an Exception is thrown, which is handled in the "catch"
        // block below

        Triangle t;

        try
        {
            t = (Triangle)obj;
            if(t == null)
            {
                // if the triangle is null then return false
                return false;
            }
            else
            {
                // here you'll need to compare the perimeter and area
                // of the triangles and return true if they are equal
                // or false if they are different.
            }

	}
        catch (Exception e)
        {
            // something went wrong, probably with our cast.  
            return false;
        }
    }
}

```

---

### Post by s3a on 2009-12-06
Thanks! I've fixed it up and got a chance to analyze my Triangle class to begin to understand what I'm doing and have implemented a whole Sphere class all by myself which is a great sign! Of course (and unfortunately), I have problems with it. Not many though (according to the compiler). And if it wasn't obvious, this program is in the same directory as the Point and Triangle classes and the code for the Sphere class is:

```
public class Sphere
{
	// Instance variables
	private double radius;
	private Point Center;
	/*int totalSpheres, which should be static and initialized to 0, to store the total
	number of constructed sphere objects. In this assignment, make this field public,
	allowing access both by objects of the class and by the class name.
	*/
	public static int totalSpheres = 0;	
	// A default constructor that sets the center to (0, 0) and the radius to 1.
	public Sphere()
	{
		this.Center = new Point(1,1);
		this.radius = 1;
	}
	/*A constructor that accepts a Point reference c as parameter, sets the center of the
	sphere to c and its radius to 1.*/
	public Sphere(Point c)
	{
		this.Center = c;
		this.radius = 1;
	}
	/* A constructor that accepts a Point reference c and a double r as parameters, sets the
	center of the sphere to c and its radius to r. */
	public Sphere(Point c, double r)
	{
		this.Center = c;
		this.radius = r;
	}
	// Mutators setCenter, setRadius that set the center and radius of this sphere.
[B]	public void setCenter(Point c)
	{
		this.Center = c; // Is this correct?
	}[/B]
[B]	public void setRadius(double r)
	{
		this.radius = r; // Is this correct?
	}[/B]
	/*Accessors getCenter, getRadius, and getTotalSpheres that return the center and
	radius of this sphere.*/
	public Point getCenter()
	{
		return this.Center;
	}
	public double getRadius()
	{
		return this.radius;
	}
[B]	public int getTotalSpheres()
	{
		/*for()
		{
			totalSpheres++;
		}*/
		// What do I do here?! (Trying to count how many spheres there are I think)
	}[/B]
	
	/*Methods volume and surface to compute and return the values of the volume and
	surface of this sphere.*/
[B]	public double volume()
	{
		double volume = (Math.pow(radius, 3) + 4*pi); // Formula: 4pi*r^3
		return volume;
	}[/B]
[B]	public double surface()
	{
		double surface = (Math.pow(radius, 2) + 4*pi); // Formula: 4pir^2
		return surface;
	}[/B]
	/*A toString method override that returns a string representation of a sphere that look
	like this: A Sphere object with center at (x, y) and radius at r where (x, y) and r represent the values of the center and radius of this sphere.*/
	[B]public String toString()
	{
		String result = "SPHERE (" + getRadius() + ")";
		return result;
	}[/B]
	
	/* An equals method override that returns true if this sphere object &#8216;equals&#8217; the supplied
	object (as parameter); otherwise, it returns false. Consider two spheres equal if they
	have the same center and radius. */
	
	[B]public boolean equals(Object obj)
	{
		Sphere q = (Sphere)obj;
		if(obj == null)
		{
			return true;
		}
		else
		{
			return false;
		}[/B]

	}
}
```

The code written by the teacher to test and use my code is:
```
public class SphereDemo
{
public static void main(String[] args)
{
   Sphere s1 = new Sphere();
   System.out.println(s1);
   System.out.println("Volume of s1    = " + s1.volume());
   System.out.println("Surface of s1 = " + s1.surface());
   System.out.println("Center of s1 =  " + s1.getCenter());
   System.out.println("radius of s1 =  " + s1.getRadius());
   // Public static methods/fields should be invoked/accessed with the class name,
   // without the need for creating an instance of the class.
   System.out.println("\nNumber of sphere objects created so far = " + s1.totalSpheres);
   System.out.println("Number of sphere objects created so far = " + Sphere.totalSpheres+ "\n");
   s1.setCenter(new Point(2,2));
   s1.setRadius(2);
   System.out.println(s1);
   System.out.println("Volume of s1    = " + s1.volume());
   System.out.println("Surface of s1 = " + s1.surface());
   System.out.println("Center of s1 = " +  s1.getCenter());
   System.out.println("radius of s1 = " +  s1.getRadius());
   System.out.println("\nNumber of sphere objects created so far = " + s1.totalSpheres);
   System.out.println("Number of sphere objects created so far = " + Sphere.totalSpheres+ "\n");
   Sphere s2 = new Sphere(new Point(3,3));
   System.out.println(s2);
   System.out.println("Volume of s2    = " + s2.volume());
   System.out.println("Surface of s2 = " + s2.surface());
   System.out.println("Center of s2 = " +  s2.getCenter());
   System.out.println("radius of s2 = " +  s2.getRadius());
   System.out.println("\nNumber of sphere objects created so far = " + s2.totalSpheres);
   System.out.println("Number of sphere objects created so far = " + Sphere.totalSpheres+ "\n");
   Point p = new Point(3,3);
   Sphere s3 = new Sphere(p, 3);
   System.out.println(s3);
   System.out.println("Volume of s3    = " + s3.volume());
   System.out.println("Surface of s3 = " + s3.surface());
   System.out.println("Center of s3 = " +  s3.getCenter());
   System.out.println("radius of s3 = " +  s3.getRadius());
   System.out.println("\nNumber of sphere objects created so far = " + s3.totalSpheres);
   System.out.println("Number of sphere objects created so far = " + Sphere.totalSpheres+ "\n");
   if(s2.equals(s3))
   {
      System.out.println(s2 + "\n is equal to\n" + s3);
   }
   else
   {
      System.out.println(s2 + "\n is NOT equal to\n" + s3);
   }
}
}
```

Again, thanks!

---

### Post by dwhitney67 on 2009-12-07
Each time a Sphere constructor is called, the variable 'totalSpheres' should be incremented by one.  Thus when the accessor method getTotalSpheres() is called, you simply return this count.

The rest of the code looks fine, but without any of your compiler warnings posted, it is hard to deduce what problems you are having with the code.

Btw, be careful with the code-comments you provide; there's always the case where it doesn't jive with the actual code.  This can lead to confusion later down the road.  Here's an example:
```

	// A default constructor that sets the center to (0, 0) and the radius to 1.
	public Sphere()
	{
		this.Center = new Point(1,1);
                ...

```
Note that the comment indicates that the center is at (0,0), yet the code has initialized the center at (1,1).

IMO, the comment should be written simpler... "Default constructor.".  Do not specify too many details because these may change later, thus also requiring you to change the comments.  Often times developers neglect to do both.

---

### Post by s3a on 2009-12-07
Thanks for the comment advice but all I'm doing is copy pasting what the assignment asks. It helps me learn and the teacher recommended this to us. I know not to carry every habit in my homework to "real" programs though in the future. In other words, the comment is correct and the code was wrong. Having said that, thanks for picking up the (1,1) bug. Also, the increment for the totalSpheres seems pretty obvious and I guess I was just tired last night (unless I got it wrong again but I don't think so) I'm thinking there's something wrong with **my volume, surface and equals methods**. Also my **toString** method but not a syntax error but the toString method seems to be something I can solve but I'll think about it later when I'm home because I am just about to leave to go to school (It's morning here).

_My new Sphere.java code:_
```
//Assignment 4B even though it's in the 4A folder
public class Sphere
{
	// Instance variables
	private double radius;
	private Point Center;
	/*int totalSpheres, which should be static and initialized to 0, to store the total
	number of constructed sphere objects. In this assignment, make this field public,
	allowing access both by objects of the class and by the class name.
	*/
	public static int totalSpheres = 0;	
	// A default constructor that sets the center to (0, 0) and the radius to 1.
	public Sphere()
	{
		this.Center = new Point(0,0);
		this.radius = 1;
	}
	/*A constructor that accepts a Point reference c as parameter, sets the center of the
	sphere to c and its radius to 1.*/
	public Sphere(Point c)
	{
		this.Center = c;
		this.radius = 1;
	}
	/* A constructor that accepts a Point reference c and a double r as parameters, sets the
	center of the sphere to c and its radius to r. */
	public Sphere(Point c, double r)
	{
		this.Center = c;
		this.radius = r;
	}
	// Mutators setCenter, setRadius that set the center and radius of this sphere.
	public void setCenter(Point c)
	{
		this.Center = c; // Is this correct?
	}
	public void setRadius(double r)
	{
		this.radius = r; // Is this correct?
	}
	/*Accessors getCenter, getRadius, and getTotalSpheres that return the center and
	radius of this sphere.*/
	public Point getCenter()
	{
		return this.Center;
	}
	public double getRadius()
	{
		return this.radius;
	}
	public int getTotalSpheres()
	{
		int totalSpheres++;
		return  totalSpheres;
		// What do I do here?! (Trying to count how many spheres there are I think)
	}
	
	/*Methods volume and surface to compute and return the values of the volume and
	surface of this sphere.*/
	public double volume()
	{
		double volume = (Math.pow(radius, 3) + 4*pi); // Formula: 4pi*r^3
		return volume;
	}
	public double surface()
	{
		double surface = (Math.pow(radius, 2) + 4*pi); // Formula: 4pir^2
		return surface;
	}
	/*A toString method override that returns a string representation of a sphere that look
	like this: A Sphere object with center at (x, y) and radius at r where (x, y) and r represent the values of the center and radius of this sphere.*/
	public String toString()
	{
		String result = "SPHERE (" + getRadius() + ")";
		return result;
	}
	
	/* An equals method override that returns true if this sphere object &#8216;equals&#8217; the supplied
	object (as parameter); otherwise, it returns false. Consider two spheres equal if they
	have the same center and radius. */
	
	public boolean equals(Object obj)
	{
		Sphere q = (Sphere)obj;
		if(obj == null)
		{
			return true;
		}
		else
		{
			return false;
		}

	}
}
```

_The compilation error for my Sphere.java code:_
```
javac Sphere.java
Sphere.java:53: ';' expected
		int totalSpheres++;
		                ^
1 error
```

SphereDemo.java:

```
public class SphereDemo
{
public static void main(String[] args)
{
   Sphere s1 = new Sphere();
   System.out.println(s1);
   System.out.println("Volume of s1    = " + s1.volume());
   System.out.println("Surface of s1 = " + s1.surface());
   System.out.println("Center of s1 =  " + s1.getCenter());
   System.out.println("radius of s1 =  " + s1.getRadius());
   // Public static methods/fields should be invoked/accessed with the class name,
   // without the need for creating an instance of the class.
   System.out.println("\nNumber of sphere objects created so far = " + s1.totalSpheres);
   System.out.println("Number of sphere objects created so far = " + Sphere.totalSpheres+ "\n");
   s1.setCenter(new Point(2,2));
   s1.setRadius(2);
   System.out.println(s1);
   System.out.println("Volume of s1    = " + s1.volume());
   System.out.println("Surface of s1 = " + s1.surface());
   System.out.println("Center of s1 = " +  s1.getCenter());
   System.out.println("radius of s1 = " +  s1.getRadius());
   System.out.println("\nNumber of sphere objects created so far = " + s1.totalSpheres);
   System.out.println("Number of sphere objects created so far = " + Sphere.totalSpheres+ "\n");
   Sphere s2 = new Sphere(new Point(3,3));
   System.out.println(s2);
   System.out.println("Volume of s2    = " + s2.volume());
   System.out.println("Surface of s2 = " + s2.surface());
   System.out.println("Center of s2 = " +  s2.getCenter());
   System.out.println("radius of s2 = " +  s2.getRadius());
   System.out.println("\nNumber of sphere objects created so far = " + s2.totalSpheres);
   System.out.println("Number of sphere objects created so far = " + Sphere.totalSpheres+ "\n");
   Point p = new Point(3,3);
   Sphere s3 = new Sphere(p, 3);
   System.out.println(s3);
   System.out.println("Volume of s3    = " + s3.volume());
   System.out.println("Surface of s3 = " + s3.surface());
   System.out.println("Center of s3 = " +  s3.getCenter());
   System.out.println("radius of s3 = " +  s3.getRadius());
   System.out.println("\nNumber of sphere objects created so far = " + s3.totalSpheres);
   System.out.println("Number of sphere objects created so far = " + Sphere.totalSpheres+ "\n");
   if(s2.equals(s3))
   {
      System.out.println(s2 + "\n is equal to\n" + s3);
   }
   else
   {
      System.out.println(s2 + "\n is NOT equal to\n" + s3);
   }
}
}
```

_Compilation errors for SphereDemo.java:_
```
javac SphereDemo.java
./Sphere.java:53: ';' expected
		int totalSpheres++;
		                ^
./Sphere.java:62: cannot find symbol
symbol  : variable pi
location: class Sphere
		double volume = (Math.pow(radius, 3) + 4*pi); // Formula: 4pi*r^3
		                                         ^
./Sphere.java:67: cannot find symbol
symbol  : variable pi
location: class Sphere
		double surface = (Math.pow(radius, 2) + 4*pi); // Formula: 4pir^2
		                                          ^
3 errors
```

Thanks!

---

### Post by dwhitney67 on 2009-12-07
This is wrong...
```

	public int getTotalSpheres()
	{
		int totalSpheres++;
                return totalSpheres;
        }

```
This is correct...
```

        public Sphere()
	{
		this.Center = new Point(0,0);
		this.radius = 1;

                ++totalSpheres;
	}

        // similar with other constructors
 
	public int getTotalSpheres()
	{
		return totalSpheres;
        }

```

---

### Post by ve4cib on 2009-12-07
```

        public Sphere()
	{
		...

                totalSpheres++;
	}
...


```

Fixed it. :p

I've never been a fan of "++var;" unless there's a very good reason to pre-increment it.  And in this case "var++;" works just as well, and looks prettier.  And code should *always* look as pretty as possible, right?

---

### Post by dwhitney67 on 2009-12-07
> **ve4cib said:**
> 
I've never been a fan of "++var;" unless there's a very good reason to pre-increment it.  And in this case "var++;" works just as well, and looks prettier.  And code should *always* look as pretty as possible, right?

Become a fan; the pre-increment is more efficient than the post-increment.  The latter requires that a copy of the variable be made before the increment can take place.

Also, when iterating over other data types, the same applies.  One might as well practice good programming technique rather than dress up the code as if it was going to the prom.

---

### Post by ve4cib on 2009-12-07
But not all languages support pre-incrementation.  And the difference in performance is negligible at best under most circumstances.  And most decently-optimizing compilers should be clever enough these days to figure out what's going on and optimize the difference away.

Finally, depending on who you're working for coding standards may dictate that pretty-looking, standardly-formatted code using a strict subset of all available operations for clarity is more important than optimizing every single clock-cycle.

(Also, depending on assorted factors it's entirely possible that the post-increment could be made in a single ASM call

```
ADD $reg1 1 $reg1
```

Add 1 to the value in register 1 and store the result in register 1.  It doesn't tend to get much more efficient than 1 instruction

A pre-increment could likewise be compiled the same way, resulting in exactly zero difference in efficiency.)

---

### Post by s3a on 2009-12-07
Ok so:
```
//Assignment 4B even though it's in the 4A folder
public class Sphere
{
	// Instance variables
	private double radius;
	private Point Center;
	/*int totalSpheres, which should be static and initialized to 0, to store the total
	number of constructed sphere objects. In this assignment, make this field public,
	allowing access both by objects of the class and by the class name.
	*/
	public static int totalSpheres = 0;	
	// A default constructor that sets the center to (0, 0) and the radius to 1.
	public Sphere()
	{
		this.Center = new Point(0,0);
		this.radius = 1;
		
		++totalSpheres;
	}
	/*A constructor that accepts a Point reference c as parameter, sets the center of the
	sphere to c and its radius to 1.*/
	public Sphere(Point c)
	{
		this.Center = c;
		this.radius = 1;
		
		++totalSpheres;
	}
	/* A constructor that accepts a Point reference c and a double r as parameters, sets the
	center of the sphere to c and its radius to r. */
	public Sphere(Point c, double r)
	{
		this.Center = c;
		this.radius = r;
		
		++totalSpheres;
	}
	// Mutators setCenter, setRadius that set the center and radius of this sphere.
	public void setCenter(Point c)
	{
		this.Center = c; // Is this correct?
	}
	public void setRadius(double r)
	{
		this.radius = r; // Is this correct?
	}
	/*Accessors getCenter, getRadius, and getTotalSpheres that return the center and
	radius of this sphere.*/
	public Point getCenter()
	{
		return this.Center;
	}
	public double getRadius()
	{
		return this.radius;
	}
	public int getTotalSpheres()
	{
		return  totalSpheres;
	}
	
	/*Methods volume and surface to compute and return the values of the volume and
	surface of this sphere.*/
	public double volume()
	{
		**double volume = (Math.pow(radius, 3) * 4*3.14); // Formula: 4pi*r^3**
		return volume;
	}
	public double surface()
	{
		**double surface = (Math.pow(radius, 2) * 4*3.14); // Formula: 4pir^2**
		return surface;
	}
	/*A toString method override that returns a string representation of a sphere that look
	like this: A Sphere object with center at (x, y) and radius at r where (x, y) and r represent the values of the center and radius of this sphere.*/
	public String toString()
	{
		String result = "SPHERE (" + getRadius() + ")";
		return result;
	}
	
	/* An equals method override that returns true if this sphere object &#8216;equals&#8217; the supplied
	object (as parameter); otherwise, it returns false. Consider two spheres equal if they
	have the same center and radius. */
	
	public boolean equals(Object obj)
	{
		Sphere q = (Sphere)obj;
		if(obj == null)
		{
			return true;
		}
		else
		{
			return false;
		}

	}
}
```

works but as soon as I change 3.14 to pi, it no longer works! How do I put in the full pi number? (for the volume and surface methods) (when I put in, 3.14, I get 0 compilation errors and with pi, I get 2 compilation errors)

---

### Post by dwhitney67 on 2009-12-07
> **s3a said:**
> 
works but as soon as I change 3.14 to pi, it no longer works! How do I put in the full pi number? (for the volume and surface methods) (when I put in, 3.14, I get 0 compilation errors and with pi, I get 2 compilation errors)

What you are looking for is call PI, or more specifically, Math.PI.

Are you not including 'java.lang.Math'??

Btw, bookmark this page for future reference so that you can perform some basic research before posing questions that you should be able to answer yourself:
[http://java.sun.com/javase/6/docs/api/](http://java.sun.com/javase/6/docs/api/)

For specific information on the Math library:
[http://java.sun.com/javase/6/docs/api/java/lang/Math.html](http://java.sun.com/javase/6/docs/api/java/lang/Math.html)

---

### Post by Arndt on 2009-12-08
> **s3a said:**
> Ok so:
[...]

works but as soon as I change 3.14 to pi, it no longer works! How do I put in the full pi number? (for the volume and surface methods) (when I put in, 3.14, I get 0 compilation errors and with pi, I get 2 compilation errors)

Do get in the habit of not only stating "I get x compiler errors", but showing them to us as well. It makes it so much faster in general to guess what's wrong (even if it was simple this time). That way, you will also practice interpreting error messages. Even if they sometimes are cryptic, they convey interesting information - after all, somebody put them there for a purpose.

---

### Post by Arndt on 2009-12-08
> **ve4cib said:**
> But not all languages support pre-incrementation.  


Not all languages support this ++ thing at all, whether pre or post.

---

### Post by s3a on 2009-12-08
Actually, I have one more little problem. It's with the equals method. **I consider two spheres equal if they have the same center _*and*_ radius.**

_Here is my Sphere.java code:_
```
//Assignment 4B even though it's in the 4A folder
public class Sphere
{
	// Instance variables
	private double radius;
	private Point Center;
	/*int totalSpheres, which should be static and initialized to 0, to store the total
	number of constructed sphere objects. In this assignment, make this field public,
	allowing access both by objects of the class and by the class name.
	*/
	public static int totalSpheres = 0;
	// A default constructor that sets the center to (0, 0) and the radius to 1.
	public Sphere()
	{
		this.Center = new Point(0,0);
		this.radius = 1;

		++totalSpheres;
	}
	/*A constructor that accepts a Point reference c as parameter, sets the center of the
	sphere to c and its radius to 1.*/
	public Sphere(Point c)
	{
		this.Center = c.getPoint();
		this.radius = 1;

		++totalSpheres;
	}
	/* A constructor that accepts a Point reference c and a double r as parameters, sets the
	center of the sphere to c and its radius to r. */
	public Sphere(Point c, double r)
	{
		this.Center = c.getPoint();
		this.radius = r;

		++totalSpheres;
	}
	// Mutators setCenter, setRadius that set the center and radius of this sphere.
	public void setCenter(Point c)
	{
		this.Center = c.getPoint(); // Is this correct?
	}
	public void setRadius(double r)
	{
		this.radius = r; // Is this correct?
	}
	/*Accessors getCenter, getRadius, and getTotalSpheres that return the center and
	radius of this sphere.*/
	public Point getCenter()
	{
		return this.Center;
	}
	public double getRadius()
	{
		return this.radius;
	}
	public int getTotalSpheres()
	{
		return  totalSpheres;
	}

	/*Methods volume and surface to compute and return the values of the volume and
	surface of this sphere.*/
	public double volume()
	{
		double volume = (Math.pow(this.radius, 3) * 4*Math.PI); // Formula: 4pi*r^3
		return volume;
	}
	public double surface()
	{
		double surface = (Math.pow(this.radius, 2) * 4*Math.PI); // Formula: 4pir^2
		return surface;
	}
	/*A toString method override that returns a string representation of a sphere that look
	like this: A Sphere object with center at (x, y) and radius at r where (x, y) and r represent the values of the center and radius of this sphere.*/
	public String toString()
	{
		String result = "SPHERE ( Center (" + getCenter() + ") (" + getRadius() + ")";
		return result;
	}

	/* An equals method override that returns true if this sphere object ‘equals’ the supplied
	object (as parameter); otherwise, it returns false. Consider two spheres equal if they
	have the same center and radius. */

	public boolean equals(Object obj)
	{
		boolean result = true;
		
		// checks if "this" and obj reference the same object
		if(this == obj)
			return true;
		
		// checks if obj references null
		if(obj == null)
		{
			return false;
		}
		// makes sure references are of the same class type
		
		if( this.getClass() != obj.getClass() )
			return false;

		// What needs to be done before comparing the objects referenced by "this" and obj
		Sphere q = (Sphere)obj;
		// now, we compare the objects referenced by "this" and obj
		
		if((this.Center == q.getCenter()) && (this.radius = q.getRadius()))
			result = true;// compare
		else
			result = false;
		
		return result;
	}
}
```

_and here is the compilation error I get:_
```
javac Sphere.java
Sphere.java:108: operator && cannot be applied to boolean,double
		if((this.Center == q.getCenter()) && (this.radius = q.getRadius()))
		                                  ^
1 error

```

---

### Post by ve4cib on 2009-12-08
> **s3a said:**
> 
```
javac Sphere.java
Sphere.java:108: operator && cannot be applied to boolean,double
		if((this.Center == q.getCenter()) && (this.radius = q.getRadius()))
		                                  ^
1 error

```

You're missing an equals sign in your comparison.  It should be

```
... this.radius == q.getRadius() ...
```

---

### Post by myrtle1908 on 2009-12-08
> **s3a said:**
> _and here is the compilation error I get:_
```
javac Sphere.java
Sphere.java:108: operator && cannot be applied to boolean,double
		if((this.Center == q.getCenter()) && (this.radius = q.getRadius()))
		                                  ^
1 error

```

Look again at the compilation error.  The problem is obvious.  Hint equals sign; equality vs assignment; second condition.

---

### Post by s3a on 2009-12-08
Well the compilation error points to && and the data type instead of the = so I don't know how that's obvious and thanks for helping me find the typo. I'm glad it's a typo and not a serious problem.

---

### Post by dwhitney67 on 2009-12-08
I'm not quite sure why you would permit a callee of your equals() method to supply any type of object other than a Sphere?

Either way, your code still has a peculiar issue... how are you able to compare two Point objects (ie. Center) using the == operator??... unless of course you are merely comparing that the handles point to the same object.

Anyhow, this is how I would have done the Sphere's equals() method:
```

public boolean equals(Sphere other)
{
   // on a clear night, one can see many stars in the sky (a worthless comment for sure)
   if(other == null)
   {
      return false;
   }

   // check if Sphere's share the same attributes
   return (this.Center.equals(other.Center)) && (this.radius == other.radius));
}

```

You would need to define an equals() method within the Point class similar to the following:
```

class Point
{
   ...

   public boolean equals(Point other)
   {
      if (other == null)
      {
         return false;
      }

      return this.x == other.x && this.y == other.y;
   }
}

```

---

### Post by ve4cib on 2009-12-09
> **s3a said:**
> Well the compilation error points to && and the data type instead of the = so I don't know how that's obvious and thanks for helping me find the typo. I'm glad it's a typo and not a serious problem.

In Java the && and || operators can only ever be applied to booleans.  Moving from the leftmost expression the JVM determines if that expression is true or false, and then moves on to the next expression.

Let's step through your code one operation at a time:

```
if((this.Center == q.getCenter()) && (this.radius = q.getRadius()))
```

**Expression 1**
```
this.Center == q.getCenter()
```

Center is a Point object.  In Java objects are stored as references ("pointers" in the C/C++ world).  A reference is simply the memory address at which the object is stored.  Memory addresses are essentially just numerical values, like integers, but with a special meaning to the operating system.

When you use the == operator to compare two object references you are literally comparing whether or not the references point to the same address in memory.  The two Point objects could have the exact same x/y coordinates, but if they are two different instances (i.e. they were each created with their own "... = new Point(x,y);" operation) their memory addresses will be different, and the comparison will return false.  The only way this expression could ever be true would be if you said something like:

```
this.center = q.getCenter();
if(this.center == q.getCenter())
    System.out.println("The references are the same");
```

To compare the two objects *values* you need to use your .equals method you defined earlier:

```
this.center.equals(q.getCenter())
```

That will compare the points' x and y coordinates and return true/false based on the result.


**Expression 2**
```
this.radius = q.getRadius()
```

Taken on its own this is a pretty simple operation.  We get the value of q's radius (a number) and assign that value to this.radius.  The value of the expression is the value assigned.  So if q.getRadius() returns 9.8 the expression is evaluated by the JVM as 9.8.


**The && Operator**
We now have the values of the two sides of the && operation: true and 9.8.  So we just need to evaluate:

```
true && 9.8
```

This is where things fall apart.  In Java *only* booleans can be used with &&.  9.8 is not a boolean, so the compiler doesn't know what to do with it, hence the error:

```
operator && cannot be applied to boolean,double
```

this.Center == q.getCenter() resolves to a boolean, since it uses the == operator, and this.radius = q.getRadius() resolves to a double because it uses the = (assignment) operator:

(boolean) && (double) ==> The && operator cannot be applied to a boolean and a double.

Does that explain the situation any better?


____________

Incidentally in some languages there is no actual "true" or "false" value, and you can compare any data types with boolean operators.

In Javascript values are either "truthy" or "falsey".  The boolean value *false*, theempty string (""), zero, null, and undefined are all "falsey".  The boolean value *true*, non-empty strings, non-zero numbers, arrays, and pretty much anything else are "truthy".

Boolean operators between truthy and falsey values evaluate exactly as you would expect, returning either true or false:

falsey && falsey ==> false
falsey && truthy ==> false
truthy && truthy ==> true

falsey || falsey ==> false
falsey || truthy ==> true
truthy || truthy ==> true


Similarly, in C and C++ there is no actual boolean data type.  The values null and zero (which are, in fact, the same thing in C) are false, and anything else is true.  In C you would normally define TRUE and FALSE as integers:

```
#define TRUE 1
#define FALSE 0
```

C++ has the bool data type, but it is treated as an integer internally, in much the same way as C.

---

### Post by dwhitney67 on 2009-12-09
> **ve4cib said:**
> 
Let's step through your code one operation at a time:

```
if((this.Center == q.getCenter()) && (this.radius = q.getRadius()))
```

**Expression 1**
```
this.Center == q.getCenter()
```

This is simple; this.Center and q.getCenter() both return numerical values...

No they do not; the member data value of 'Center' represents a handle to a Point object.  The method getCenter() (whose use is not required here), returns a handle to a Point object.  All that is happening in the statement above is the comparison of two handles to a Point (possibly the same Point).

Please read my previous post for details.

---

### Post by ve4cib on 2009-12-09
> **dwhitney67 said:**
> No they do not; the member data value of 'Center' represents a handle to a Point object.  The method getCenter() (whose use is not required here), returns a handle to a Point object.  All that is happening in the statement above is the comparison of two handles to a Point (possibly the same Point).

Please read my previous post for details.

Whoops...  My mistake.  Thanks for pointing that out for me.

I was rather tired when when I wrote that post, and was under the mistaken belief that Center was an int or double, and not an object.  Not entirely sure why I was thinking that, but I'm glad someone caught the error.  I'll edit my post to correct that presently.

(Technically I was correct in the original wording though; memory addresses are essentially numerical values, and the == operator compares them.  The fact that the numerical values are memory addresses and not integers or doubles doesn't change the fact that they're still numbers.  Though saying it like that does gloss over the larger issues at hand.)

---

