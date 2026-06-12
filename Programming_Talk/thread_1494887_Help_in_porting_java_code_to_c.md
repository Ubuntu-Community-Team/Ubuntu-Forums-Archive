---
title: "Help in porting java code to c"
date: 2010-05-27
forum: Programming Talk
---

### Post by Zaizeku on 2010-05-27
Hi guys, I need your help, I need to port some code from java to C but I don't know squat from java, I'm pretty lost and I can't seem to find some good reference except from this website [http://www.skytopia.com/project/articles/compsci/programming.html]("http://www.skytopia.com/project/articles/compsci/programming.html").

So I have come here to ask you guys if you have some other references that could help me out here.

Thanks in advance :)

---

### Post by nvteighen on 2010-05-27
> **Zaizeku said:**
> Hi guys, I need your help, I need to port some code from java to C but I don't know squat from java, I'm pretty lost and I can't seem to find some good reference except from this website [http://www.skytopia.com/project/articles/compsci/programming.html]("http://www.skytopia.com/project/articles/compsci/programming.html").

So I have come here to ask you guys if you have some other references that could help me out here.

Thanks in advance :)

I guess the only way out is to learn a reasonable amount of Java... Look at the Sun tutorials: [http://java.sun.com/developer/onlineTraining/index.jsp](http://java.sun.com/developer/onlineTraining/index.jsp)

---

### Post by dwhitney67 on 2010-05-27
> **Zaizeku said:**
> Hi guys, I need your help, I need to port some code from java to C but I don't know squat from java, I'm pretty lost and I can't seem to find some good reference except from this website [http://www.skytopia.com/project/articles/compsci/programming.html]("http://www.skytopia.com/project/articles/compsci/programming.html").

So I have come here to ask you guys if you have some other references that could help me out here.

Thanks in advance :)

Learn Java; here's the API docs: [http://java.sun.com/javase/6/docs/api/](http://java.sun.com/javase/6/docs/api/)

You would probably have an easier time translating from Java to C++, and if there is anything related to GUI (ie swing), then consider using GTK+ or X11/Motif.

---

### Post by Zaizeku on 2010-05-27
> **dwhitney67 said:**
> Learn Java; here's the API docs: [http://java.sun.com/javase/6/docs/api/](http://java.sun.com/javase/6/docs/api/)

You would probably have an easier time translating from Java to C++, and if there is anything related to GUI (ie swing), then consider using GTK+ or X11/Motif.

Yeah thanks I would prefer c++, but it needs to be done specifically in c so yeah... well anyway thanks for your answers, I guess I'll have to learn java](*,)

---

### Post by Queue29 on 2010-05-27
If you are a competent C programmer then learning Java is going to be trivial. However, even if you are knowledgeable in both languages, going from a very high level language like Java down to C is going to be far from easy. In fact, you won't be *translating* anything. You'll be looking at the Java source code as algorithmic psuedo code, and nothing more. Most, if not all of your C code is going to be implemented uniquely.

---

### Post by dwhitney67 on 2010-05-27
> **Zaizeku said:**
> Yeah thanks I would prefer c++, but it needs to be done specifically in c so yeah... well anyway thanks for your answers, I guess I'll have to learn java](*,)

Why, if I may ask, does it have to be in C?  Java is an Object Oriented language that support inheritance, abstract interfaces, and of course polymorphism.  Newer versions of Java support templates.  Translating these features into C will be a huge, if not a monumental, challenge.

If you have the time, here's a simple program that you can try to translate; there is nothing graphical about it.  If translated into C++, it would be a cinch... but not so in C.  As implied earlier by Queue29, you will stray from the task of translation, and instead develop an entirely new beast if you pursue with your plans to use C.

```

abstract class Shape
{
   private double x_coord, y_coord;

   Shape(double x, double y)
   {
      x_coord = x;
      y_coord = y;
   }

   public String toString()
   {
      String str = "Shape is at (" + x_coord + ", " + y_coord + ").  It has an area of " + area();
      return str;
   }

   public abstract double area();
};


class Triangle extends Shape
{
   private double height, width;

   public Triangle(double x, double y, double h, double w)
   {
     super(x, y);

     height = h;
     width  = w;
   }

   public double area()
   {
      return 0.5 * (height * width);
   }
};


class Rectangle extends Shape
{
   private double width, length;

   public Rectangle(double x, double y, double w, double l)
   {
     super(x, y);

     width  = w;
     length = l;
   }

   public double area()
   {
      return width * length;
   }
};


class Square extends Rectangle
{
   public Square(double x, double y, double sideLength)
   {
      super(x, y, sideLength, sideLength);
   }
};


class TestShapes
{
   public static void main(String[] args)
   {
      Shape[] shapes = new Shape[3];

      shapes[0] = new Triangle(1, 2, 4, 5);
      shapes[1] = new Rectangle(6, 7, 3, 7);
      shapes[2] = new Square(2, 4, 5);

      for (int i = 0; i < shapes.length; ++i)
      {
         System.out.println(shapes[i]);
      }
   }
}

```

---

### Post by Queue29 on 2010-05-27
^ +1

Heck, forget polymorphism, there are so many built in libraries to Java, you're going to be spending a lot of overtime implementing them in C if you really plan to do this.

Try implementing something trivial like this in C:

```

import java.util.ArrayList;
import java.util.TreeSet;

public class Sample
{
	public static void main(String[] abc)
	{
		ArrayList<Integer> list = new ArrayList<Integer>();
		TreeSet<Integer> tree = new TreeSet<Integer>();
		list.add(5);
		list.add(7);
		list.add(2);
		list.add(8);
		list.add(7);
		tree.addAll(list);
		
		System.out.println(list);
		System.out.println(tree); // notice this is always in sorted order, and maintains the set property
	}
}

```

This took about 90 seconds to write in Java, and I can assure you, Java programers LOVE to use and abuse the Java API. How long does it take you to convert this to C? Feel free to use all the C libraries you can shake a stick at.

---

### Post by splicerr on 2010-05-27
Or you could port it to Vala and then use valac to compile to C code ... You'll add some dependencies on glib/gobject. But porting is going to be a hell of a lot easier.

---

