---
title: "Am I missing something? (Java inheritance)"
date: 2009-10-09
forum: Programming Talk
---

### Post by nmccrina on 2009-10-09
Ok, so for my programming class we need to have a Shape class, with other classes (such as a circle) inheriting from Shape. The assignment requires that shape have a "number of sides" field, which of course should be inherited. When I make this variable private, the subclass can't read it (I expected this), but when I make it protected it can be accessed by classes outside the inheritance tree, just as if it were public. Why is this? I think C++ makes more sense, protected is basically private except that it can be accessed by subclasses. 

Here's my classes:

```
class Shape
{
    protected int numberOfSides;
}
```

```
class Circle extends Shape
{
    public void print()
    {
        System.out.println("Number of sides: " + this.numberOfSides);
    }
}
```

```
class Driver
{
    public static void main(String[] args)
    {
        Shape shape = new Shape();
        Circle circle = new Circle();
        circle.print();
        // How am I able to access numberOfSides???
        System.out.println("Shape sides: " + shape.numberOfSides);
    }
}
```

---

### Post by shadylookin on 2009-10-09
protected means that anything in the same package can access it.

Since number of sides is dependent entirely on the subclass I would keep that variable inside the subclass

otherwise I'd do something like this

```


public class Shape{

    private int sides;
    
    public Shape(int sides){
        this.sides = sides
    }

    public int getSides(){
        return sides;
    }

}

```

```

public class Square extends Shape{
    public Square(){
        super(4);
    }

    public void print(){
        System.out.println("number of sides: "+super.getSides());
    }
}


```

---

### Post by nmccrina on 2009-10-09
Yeah, I thought about putting the numberOfSides variable in each subclass, but I figured that if this was something that was common to every shape, it had better go in the parent. I think I'll just keep it private and use accessors and mutators like you did above.

---

### Post by nmccrina on 2009-10-09
> **shadylookin said:**
> protected means that anything in the same package can access it.

OK. I suppose this would be useful, but I haven't built any of my own packages yet so I still miss the c++ protected :(

---

### Post by dwhitney67 on 2009-10-09
Consider also declaring the Shape class as abstract, because in theory, one should not be able to instantiate a shape object (as you have done in your app).

Also, just to be picky, a Square _is a_ Rectangle.  Thus the hierarchy should be Shape <- Rectangle <- Square.  A square is a rectangle with equal sides.

---

### Post by shadylookin on 2009-10-09
> **nmccrina said:**
> OK. I suppose this would be useful, but I haven't built any of my own packages yet so I still miss the c++ protected :(

I guess it's a tradeoff you don't have to declare super class methods virtual in java. 

packages aren't a hard concept really, you just right click in an ide and create a new package.

---

### Post by Reiger on 2009-10-09
> protected means that anything in the same package can access it.

Wrong. You can create two public classes in the same package with one class having the protected modifier for a field; and you won't be able to access that field directly from within the other class.

Secondly protected is just a different kind of private: it is private with inheritance (it can be overriden on the sub-class level).

What you are refering to is code like this:
```

package test;
public class Test {
  void test() {
    System.out.println("test.Test#test()");
  }
}

```

This method test is public but only within the package test.

However, interfaces behave differently here: in an interface, methods declared like that transcend package boundaries.

The real problem the OP had was not that his use of protected was wrong; but that protected prevents you from accessing that field/method directly from outside the class-hierarchy. (Anything that isn't a Shape cannot access that field because the field is protected and only Shapes are allowed to access it.)

As already pointed out: when you want something to be protected yet also want to provide means of access to your field the correct way to go about it is to use getter & setter methods. These are so named because they are typically called getFieldName() and setFieldName(Type fieldName) with FieldName the name of the field (e.g. numberOfSides) and Type the Java type of the field.

So:
```

class Shape {
  protected int numberOfSides = 0;
  public void setNumberOfSides(int numberOfSides) { 
    this.numberOfSides = numberOfSides;
  }
  public int getNumberOfSides() {
    return this.numberOfSides;
  }
}

```

---

### Post by shadylookin on 2009-10-09
> **Reiger said:**
> Wrong. You can create two public classes in the same package with one class having the protected modifier for a field; and you won't be able to access that field directly from within the other class.

Secondly protected is just a different kind of private: it is private with inheritance (it can be overriden on the sub-class level).

In java anything in the same package can access protected methods/instance variables as well as any derived class(regardless of package).

---

### Post by dwhitney67 on 2009-10-09
> **dwhitney67 said:**
> Consider also declaring the Shape class as abstract, because in theory, one should not be able to instantiate a shape object (as you have done in your app).

Also, just to be picky, a Square _is a_ Rectangle.  Thus the hierarchy should be Shape <- Rectangle <- Square.  A square is a rectangle with equal sides.

Just to follow up what I was stating above, here are classes for Shape, Rectangle, and Square.

Shape.java:
```

// Declare Shape as an abstract class

abstract class Shape
{
   protected int numSides = 0;

   public Shape(int sides)
   {
      this.numSides = sides;
   }

   public int getNumSides()
   {
      return this.numSides;
   }

   abstract public double getArea();
}

```

Rectangle.java:
```

public class Rectangle extends Shape
{
   private double length;
   private double width;

   public Rectangle(double len, double wid)
   {
      super(4);

      this.length = len;
      this.width  = wid;
   }

   public double getLength()
   {
      return this.length;
   }

   public double getWidth()
   {
      return this.width;
   }

   public double getArea()
   {
      return this.length * this.width;
   }
}

```

Square.java:
```

public class Square extends Rectangle
{
   public Square(double size)
   {
      super(size, size);
   }

   public static void main(String[] args)
   {
      //Shape shape = new Shape(4);    // not possible; Shape is abstract.

      Shape[] shape = new Shape[2];

      shape[0] = new Square(5.0);
      shape[1] = new Rectangle(4.0, 5.0);

      for (int i = 0; i < 2; ++i)
      {
         System.out.println("\nShape " + (i+1));
         System.out.println("Sides:  " + shape[i].getNumSides());
         System.out.println("Area:   " + shape[i].getArea());

         if (shape[i] instanceof Rectangle)
         {
            if (shape[i] instanceof Square)
            {
               System.out.println("Type:   Square");
            }
            else
            {
               System.out.println("Type:   Rectangle");
            }

            Rectangle rect = (Rectangle) shape[i];

            System.out.println("Length: " + rect.getLength());
            System.out.println("Width:  " + rect.getWidth());
         }
      }
   }
}

```

Surely there are other attributes one can define for the Shape object (eg. position, color, etc).  Also one may want to disallow Shapes that have less than 3 sides.

As for packaging the classes, that is something I infrequently use, and thus I tend to leave it for the end, that is, when I am done with my design.

---

### Post by pbrockway2 on 2009-10-09
Check out the JLS [6.6.1 Determining Accessibility]("http://java.sun.com/docs/books/jls/third_edition/html/names.html#102765") and following.

"if the member or constructor is declared protected, then access is permitted only when one of the following is true:
o Access to the member or constructor occurs from within the package containing the class in which the protected member or constructor is declared.
o Access is correct as described in §6.6.2."

---

