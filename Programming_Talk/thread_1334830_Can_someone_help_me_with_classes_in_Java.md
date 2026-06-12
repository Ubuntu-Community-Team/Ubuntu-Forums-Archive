---
title: "Can someone help me with classes in Java?"
date: 2009-11-22
forum: Programming Talk
---

### Post by s3a on 2009-11-22
Here is my "blueprint" or the file that will be accessed from another file (in the second code box):
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
	public int getX()
	{
		return x;
	}
	public int getY()
	{
		return y;
	}
/*
The default (no-arguments) constructor, constructing the point (1; 1).
Usage example: Point p = new Point(); // p = (1,1)
*/
	public Point()
	{
		x = 1;
		y = 1;
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
	public Point getPoint()
	{
		return Point;
	}
	/*
	 * A toString() method that returns the string (x, y), where x and y are the coordinate
	 * values of this point. (Recall that the this object is the same as the object calling a
	 * method.)
	*/
	public toString(int p)
	{
		this.x = p;
		this.y = p;
	}

// A method length() that takes no parameters, and returns the length of this point:
	public Point length()
	{
		int distance = Math.sqrt(x); // will fix math specifics later
		return distance;
	}
	/*
	 * A method distance() that takes a Point p as a parameter and returns the distance
	 * between p and this point.
	 * sqrt((x1 &#8722; x2 )^2 + (y1 &#8722; y2 )^2).The distance between two points (x1 , y1 ) and (x2 , y2 ) is defined as
	*/
    public distance(int p)
    {
    	distance = Math.sqrt(p); // Need to figure out how to implement the formula here.
    	return distance;
	}
	
	/*	A method translate() that takes two double parameters deltaX and deltaY and
	translates the current location of this point (x, y) to (x+deltaX, y+deltaY). */

	public void translate(int deltaX, int deltaY)
	{
		this.x = x + deltaX;
		this.y = y + deltaY;
	}
	/* A method move() that takes a Point p as a parameter , and moves this point to p. */
	public void move(p)
	{
		x = p.x;
		y = p.y;
	}
	/* A method dotProduct() that takes a Point p as a parameter and returns the dot
	product of p and this point. The dot product of two points (x1; y1) and (x2; y2) is
	defined as x1x2 + y1y2. */
	public dotProduct(int p)
	{
		dotProduct = p // Multiplied by "this"? What's "this?"
		return dotProduct;
	}
	 /*
	  * a method equals() that takes an Object obj as a parameter, and returns true if and
	  * only if Object obj is not null and is an instance of Point that has the same x and y
	  * coordinates as this object.
	 */
	public equals()
	{
	}
}
```

From what I've done so far could someone explain to me what I need to change and also give me a concrete definition of what "this" is? (I'm having trouble wrapping my head around the concept)

The following is the code with a main method that will access the code I wrote above (I did not write the following and it supposedly is free of mistakes; I've been told to use the following file to see when my written program is successfully finalized):
```
public class PointDemo
{
   public static void main(String[] args)
   {
      Point p = new Point();	// create a point
      System.out.println("p = " + p);
      p.translate(2,3);
      System.out.println("p = " + p);
      System.out.println("length of p = " + p.length());
      Point q = new Point(7, 3);
      System.out.println("distance between " + p + " and " + q + " is " + p.distance(q));
      System.out.println("dot product of " + p + " and " + q + " is " + p.dotProduct(q));
      Point r = new Point(q);
      System.out.println("r = " + r);
      System.out.println("it is " + r.equals(q) + " that " + r + " and " + q + " are equal");
      Point s = new Point(5);
      System.out.println("s = " + s);
      if( s.equals(q) )
         System.out.println("it is true that " + s + " and " + q + " are equal");
      else
         System.out.println("it is false that " + s + " and " + q + " are equal");
      Point t = new Point(new Point(1,1));
      System.out.println("t = " + t);
      t.move(p);
      System.out.println("t = " + t);
      t.move(new Point(3,3));
      System.out.println("t = " + t);
      Point u = t.getPoint();
      System.out.println("u = " + u);
   }
}
```

Any help would be GREATLY appreciate!
Thanks in advance!

---

### Post by shadylookin on 2009-11-22
the keyword this means this specific instance of a class

public Point getPoint()
	{
		return Point;
	}


perhaps you might want to return this

public Point length()
	{
		int distance = Math.sqrt(x); // will fix math specifics later
		return distance;
	}


you're saying the method is going to return a Point but you return an int



public distance(int p)

public dotProduct(int p)

public toString(int p)
	


no return type. I'm not sure that you get the point of the toString method either. you should override the objects toSring by public String toString() and then return a string that makes sense for tha tobject


You really need to sit down with your class book and read it before asking homework questions

---

