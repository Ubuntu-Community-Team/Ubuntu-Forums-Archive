---
title: "Java confusion"
date: 2011-04-20
forum: Programming Talk
---

### Post by Bachstelze on 2011-04-20
This has been puzzling me for days, hopefully someone can help me with this. :p

So I have an interface named Point2D, which represents a point in two dimensions, implemented by a class named Point2DCartesien that implements a point using cartesian coordinates. Amon other methods, Point2D specifies an equals() method to check whether a point is equal to another. I have a program named TestPoint2DCartesien, which shows me that my equals() method works as intended.

Now I have an interface named Triangle, which represents a triangle as an array of three Point2D's, implemented by a class named TriangleDef. It also specifies an equals() method, to check whether two triangles are equal. I have a TestTriangle program to check it, and that's where things go wild.

The problem : I want to use the equals() method of Point2D to check whether all the points in the array of a Triangle are equal to those in the array of another Triangle. However, when I call the equals() method of Point2D from inside the equals() method of Triangle, it always returns false and I have absolutely no idea which code is actually run, because a println I have there is not called.

Code attached, any help would be greatly appreciated.

---

### Post by simeon87 on 2011-04-20
It indeed always returns false and that's because it is not using your equals method of TriangleDef. Instead, it is using the equals method of Object, which has the following signature:

```
public boolean equals(Object o)
```

and not:

```
public boolean equals(Triangle o)
```

Also, your equals method in Point2DCartesien is not used for the same reason. You have:

```
public boolean equals(Point2DCartesien p)
```

while the Point2D interface specifies:

```
public boolean equals(Object o)
```

You need to make sure that these method signatures are the same, otherwise it'll run a different method. Each class automatically has an equals(Object o) method from the Object class as each class in Java is automatically a subclass of the class Object. So it will call that method instead because your method does not override it.

If you change ```
public boolean equals(Triangle o)
``` to ```
public boolean equals(Object o)
``` in TriangleDef then you'll notice that it does run your method because it overrides the equals(Object o) method of Object. It's the similar for your equals() method in Point2DCartesien.

---

### Post by Bachstelze on 2011-04-20
Thanks for answering. The problem was indeed the discrepancy between the signatures in the interface and in the implementation, but the fix is the other way around. If I change Triangle to Object in the implementation, the code will not compile (if I understand correctly, because Object has no points() method, so it complains of a missing symbol). Putting Triangle instead of Object in both the interface and the implementation seems to do the trick. 

Thanks again.

---

### Post by anieruddha on 2011-04-20
Hi,

1. You dont need to declare 'public String toString' and 'public boolean equals' in the any interface.

2. The equal method signature should be 'public boolean equals(Object o)' in both classes i.e. in TriangleDef and in Point2DCartesien.

3. in the equals method do boxing
```

   in Point2DCartesien
    public boolean equals(Object o)
    {
        Point2DCartesien p = (Point2DCartesien) o;
        return Math.abs(this.x - p.getx()) < EPSILON &&
               Math.abs(this.y - p.gety()) < EPSILON;
    }
    in TriangleDef
    public boolean equals(Object o)
    {
        Triangle t = (Triangle) o;
        return this.points[0].equals(t.points()[0]);
    }  

```

4. override public int hashCode method in both class.
just for example I can override like
```

   in Point2DCartesien
    public int hashCode(){
      Double d = x+y;
      return d.intValue();
    }
    in TriangleDef
    public int hashCode(){
      return 1;
    } 

```

---

### Post by Some Penguin on 2011-04-20
An equals() method should check for class equality before it casts -- i.e. oneObject.equals(objectOfDifferentCast) should return false, not throw a ClassCastException.  Best to attach an @Override and be explicit about it.

Multiple IDEs can generate equals() and hashCode() methods for you; Eclipse and Intellij IDEA can both do this.  It's particularly useful for objects with many fields -- this is normally a highly mechanical task, so letting the IDE build 'em is nice.

---

