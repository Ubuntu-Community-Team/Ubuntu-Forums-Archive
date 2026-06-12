---
title: "Java Generics Question"
date: 2010-11-17
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-11-17
I'm stumped.  First of all, I read this post, but don't see how to apply it to my case:

[http://stackoverflow.com/questions/75175/create-instance-of-generic-type-in-java](http://stackoverflow.com/questions/75175/create-instance-of-generic-type-in-java)

I have a class which contains a couple HashMap<Double, NumberBucket> objects.  I want number bucket to be a generic object that I can pass into my class at construction.  Number bucket looks like this:

[PHP]
public class NumberBucket {
	private double value;
	
	public NumberBucket(double value) {
		this.value = value;
	}
	
	public NumberBucket() {
		this.value = 0.0;
	}
		
	public void setValue(double value) {
		this.value = value;
	}

	public double getValue()
	{
		return value;
	}
}[/PHP]

Basically, I'm just using it to store a Double for now, but I want to make it generic so that it can do more complicated things later.  For example, a subclass of NumberBucket might hold a distribution and getValue() might be programmed to return the median of the distribution.  

Here's some example code that I'm struggling with...everything compiles except when I have to create a new generic object, I want to instantiate a new type T...how can I use interfaces to get the code below to instantiate a generic T.  I'm fine with using the default constructor and then setting the value as an extra step:

[PHP]
import java.util.HashMap;

public class ExampleClass <T extends NumberBucket> {
	private HashMap<Integer, T> hmap;
	
	public ExampleClass()
	{
		hmap = new HashMap<Integer, T>(); //ok so far
	}
	
	public void printStuff()
	{
		System.out.println("Integer 5 mapped to: " + hmap.get(5).getValue()); //a little clunky, but still works
	}
	
	public void setStuff()
	{
		hmap.put(5, new T(5)); //nope!
	}
}
[/PHP]

---

### Post by Some Penguin on 2010-11-17
What you're running into is a consequence of type erasure -- what T is will not be known at run-time, therefore cannot be instantiated like that  (and what if T were an interface -- you can't do new List(), for instance).  You'd need pass in a reference to the class (to pull out the constructor), or to pass in a builder of some sort.

---

### Post by SNYP40A1 on 2010-11-17
Humm...then Java generics leave a lot to be desired...

---

### Post by Reiger on 2010-11-17
Well it's slightly more complex than this: the types are definitely known at runtime:

```

public class Test<O> {
  private Object field = null;
  public void setField(Object value) { this.field=value; }
  @SuppressWarnings("unchecked")
  public O getField() { return (O) field; }
}

```

That code only works because of the cast, which is performed at runtime on arbitrary data... 

Instead the real problem here is that you are not asserting something about the Type T (generics), but rather about the *implementation of a constructor*.
```

public void setStuff() 
    { 
        hmap.put(5, new T(5)); //nope! 
    }

```

More simply: generics are not templates/macro's, they do not -conceptually- generate code; it's merely a limited form of type inference.

---

### Post by SNYP40A1 on 2010-11-17
The work-around that I am using is to simply pass in an instance of the object that I want to use, and then implement a clone() method in that instance which returns another instance of the same object.  Not the ideal solution, but I think this will work.  When I extend the NumberBucket object, I will also re-write the clone method to return an instance of the subclass.

---

### Post by Some Penguin on 2010-11-17
> **Reiger said:**
> Well it's slightly more complex than this: the types are definitely known at runtime:

```

public class Test<O> {
  private Object field = null;
  public void setField(Object value) { this.field=value; }
  @SuppressWarnings("unchecked")
  public O getField() { return (O) field; }
}

```

You don't understand the difference between individual objects and generic classes, apparently, and it seems likely that you don't understand type erasure.  

The parameter '5' isn't a problem.

```

new T();

```

is going to be illegal anyway.

[http://stackoverflow.com/questions/1090458/instantiating-a-generic-class-in-java]("http://stackoverflow.com/questions/1090458/instantiating-a-generic-class-in-java")

---

### Post by Reiger on 2010-11-17
Types are definitely known at runtime. Which is why you can call getClass() on an object and query it; which is why something referred to by a supertype (as shown) keeps its actual type.

Type erasure is about the container object not knowing the type of whatever it contains. Type erasure is what causes &#8220;obj instanceof G&#8221; to fail.

T(), again is a highly specific constructor. If you build the expression tree in your mind you can see that the symbol T() or the symbol T(int) is nothing to do with generics, and everything to do with the fact that *this symbol is not defined*. T here is not a type, it is part of the signature of a constructor call. Different syntax element, different semantics, different error.

Syntactically the symbol T() or T(int) is similar to T.someMethod() or T.someMethod(int), semantically a constructor is of course not equivalent to a static method call.

Even if Java suddenly had reified generics this still would not work because, to repeat once more, the symbol T()/T(int) is still not defined (imported) in the general case. Consider:
```

public class Test<T> {
 private T field;
 public Test() { field = new T(); }
 
 public static class TestField {
   public TestField(int something) { }
 }

 // how is T() going to work with TestField(int) ???
 static final Test<TestField> test = new Test<TestField>();
}

```

---

