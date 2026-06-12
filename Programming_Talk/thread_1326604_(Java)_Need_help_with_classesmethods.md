---
title: "(Java) Need help with classes/methods"
date: 2009-11-14
forum: Programming Talk
---

### Post by s3a on 2009-11-14
I am learning how to deal with classes and stuff now and I am confused as to why the bolded line causes a compilation error. I am following what the third and fourth code boxes show which is source code bundled with my "Starting out with Java" book's CD-ROM. (The first and second code boxes' .java files are saved in the same directory and the same applies for the third and fourth code boxes in their own respective directory)

```
public class Point
{

	public static void main (String [] args)

	{

		Point p = new Point(); // p = (1,1)

[B]		System.out.print(p.getX());
[/B]
	}

}

```

```
public class Point2
{
	private int x;
	private int y;
	
	public Point2(int i, int j)
		{
			x = i;
			y = j;
		}
	public void setX(int i)
		{
			x = i;
		}
	public void setY(int j)
		{
			y = j;
		}
	public double getX()
		{
			return x;
		}
	public double getY()
		{
			return y;
		}
}
```

```
/**

   This program demonstrates the Rectangle class's

   constructor.

*/



public class ConstructorDemo

{

   public static void main(String[] args)

   {

      // Create a Rectangle object, passing 5.0 and

      // 15.0 as arguments to the constructor.

      Rectangle box = new Rectangle(5.0, 15.0);



      // Display the length.

      System.out.println("The box's length is " +

                         box.getLength());



      // Display the width.

      System.out.println("The box's width is " +

                         box.getWidth());



      // Display the area.

      System.out.println("The box's area is " +

                         box.getArea());

   }

}

```

```
/**

   Rectangle class, phase 5

*/



public class Rectangle

{

   private double length;

   private double width;



   /**

      Constructor

      @param len The length of the rectangle.

      @param w The width of the rectangle.

   */



   public Rectangle(double len, double w)

   {

      length = len;

      width = w;

   }



   /**

      The setLength method stores a value in the

      length field.

      @param len The value to store in length.

   */



   public void setLength(double len)

   {

      length = len;

   }



   /**

      The setWidth method stores a value in the

      width field.

      @param w The value to store in width.

   */



   public void setWidth(double w)

   {

      width = w;

   }



   /**

      The getLength method returns a Rectangle

      object's length.

      @return The value in the length field.

   */



   public double getLength()

   {

      return length;

   }



   /**

      The getWidth method returns a Rectangle

      object's width.

      @return The value in the width field.

   */

   

   public double getWidth()

   {

      return width;

   }



   /**

      The getArea method returns a Rectangle

      object's area.

      @return The product of length times width.

   */



   public double getArea()

   {

      return length * width;

   }

}

```

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by PaulM1985 on 2009-11-14
In your first file, the Point class, you have created a Point object using the variable p.

In the Point class, you have only defined one method called main(String args[]).  You do not have a getX() method, so the compiler is erroring because it cannot find the getX() method.

Did you mean to create a Point2 object.  The class has getX() in it.  Also, notice the Point2 class you have defined only has a constructor (the function which creates the object) with two arguments.  So in the place of:

Point p = new Point();

you may need:

Point2 p = new Point2(1, 1);  // This puts the point in (1, 1) which you defined in your comment in your original post.

Is this code something you have copied from the CD, or is it something that you have put together?  Check the way it is written in the book/CD if you are completing an example and make sure it matches correctly.

(As an aside, I personally would have the Point class called something else, maybe called Main, or MyApp, because it is not actually a point.  I would then call Point2 Point.)

Hope some of this helps.

Paul

---

### Post by s3a on 2009-11-25
I made a new version of the program and still get errors:
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
	public Point getPoint()
	{
		return this.Point;
	}
	/*
	 * A toString() method that returns the string (x, y), where x and y are the coordinate
	 * values of this point. (Recall that the this object is the same as the object calling a
	 * method.)
	*/
	public String toString(String p)
	{
		this.x = p.x;
		this.y = p.y;
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
		this.x = p.x + deltaX;
		this.y = p.y + deltaY;
	}
	/* A method move() that takes a Point p as a parameter, and moves this point to p. */
	public void move(Point p)
	{
		this.x = p.x;
		this.y = p.y;
	}
	/* A method dotProduct() that takes a Point p as a parameter and returns the dot
	product of p and this point. The dot product of two points (x1; y1) and (x2; y2) is
	defined as x1x2 + y1y2. */
	public int dotProduct(Point p)
	{
		int dotProduct = (this.x * p.x + this.y * p.y);
		return dotProduct;
	}
	 /*
	  * a method equals() that takes an Object obj as a parameter, and returns true if and
	  * only if Object obj is not null and is an instance of Point that has the same x and y
	  * coordinates as this object.
	 */
	/*public equals() // Figure this out!
	{
	}*/
}
```

I was hoping you could point out my mistakes on this one as well, please.

---

### Post by issih on 2009-11-25
```
// Accessor method getPoint() that returns this point.
	public Point getPoint()
	{
		return this.Point;
	}


```

You have no Point field defined on the Point class..nor do you define a return type for the method... not sure what its for unless its a new special method I'm not aware of (I'm quite out of date with java)

```

	/*
	 * A toString() method that returns the string (x, y), where x and y are the coordinate
	 * values of this point. (Recall that the this object is the same as the object calling a
	 * method.)
	*/
	public String toString(String p)
	{
		this.x = p.x;
		this.y = p.y;
	}

```

You shouldn't be passing in an object to the toString method, and what you do here is nothing to do with making a string statement.

```


	/*	A method translate() that takes two double parameters deltaX and deltaY and
	translates the current location of this point (x, y) to (x+deltaX, y+deltaY). */

	public void translate(int deltaX, int deltaY)
	{
		this.x = p.x + deltaX;
		this.y = p.y + deltaY;
	}


```
You have no variable p within this method yet you access one with p.x and p.y....you should just have "this.x = this.x + deltaX" or probably a bit better as "setX(getX() + deltaX)"


There might be other errors, I just did a quick scan

---

