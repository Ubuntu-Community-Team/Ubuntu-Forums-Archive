---
title: "Java Interfaces"
date: 2012-04-12
forum: Programming Talk
---

### Post by kevinharper on 2012-04-12
[http://docs.oracle.com/javase/tutorial/java/concepts/interface.html](http://docs.oracle.com/javase/tutorial/java/concepts/interface.html)

I understand what they are, I don't fully understand how they are set up.

I looked it up and found this to be the simplest (from [http://www.codemiles.com/java-examples/java-interface-example-t3505.html):](http://www.codemiles.com/java-examples/java-interface-example-t3505.html):)
```

public class Main {
    public static void main(String[] args) {        
          shape circleshape=new circle();          
             circleshape.Draw();
    }
}

interface shape
{
   public String baseclass="shape";     
   public void Draw();
}

class circle implements shape
{

   public void Draw() {
       System.out.println("Drawing Circle here");
   }
}

```

Question 1: Is it conventional to name your main class "Main"? It makes since, just haven't quite gotten to a complete program in the tutorial.

Question 2: Is the code expecting a shape class file in the current directory? Or does "interface shape" substitute the need for "class shape"?

---

### Post by kevinharper on 2012-04-12
Tutorial Exercises:
1) Create new classes for each real-world object that you observed at the beginning of this trail. Refer to the Bicycle class if you forget the required syntax.
Here's what I did:
```

class DimLamp {
	int on = 0;
	int brightness = 0;

	void turnOn(int newValue) {
		on = 1;
		brightness = 1;
	}

	void turnOff(int newValue) {
		on = 0;
		brightness = 0;
	}

	void dimUp(int increment) {
		brightness = brightness + increment;
	}

	void dimDown(int decrement) {
		brightness = brightness - decrement;
	}

	void dimSetting(){
		System.out.println("Brightness: " + brightness);
	}	
}

```

2) For each new class that you've created above, create an interface that defines its behavior, then require your class to implement it. Omit one or two methods and try compiling. What does the error look like?
I created a class that operates DimLight, not an interface.
```

class OperateDimLamp {
	public static void main(String[] args) {
		DimLamp dimLamp1 = new DimLamp();

		dimLamp1.turnOn(1);
		dimLamp1.dimUp(4);
		dimLamp1.dimDown(1);
		dimLamp1.dimSetting();
	}
}

```
Do I need to change the DimLamp class source so that it starts with "interfeace DimLight" instead of "class DimLight"?

---

### Post by satsujinka on 2012-04-12
There is no convention for where to put the main method. You can put it in any class you want. However, it is typical to put main in a class that describes the goal (a recent one I did: public class GenerateAnagrams { ...main...})

You cannot have both a class and an interface with the same name, so there's no need for a shape class (an interface is sort of like an abstract class, except all its methods are abstract and it can't have any attributes.)

---

### Post by kevinharper on 2012-04-12
So my main class name "OperateDimLamp" is ideal because it operates the DimLamp class? BAHM! Thanks!

> You cannot have both a class and an interface with the same name, so there's no need for a shape class (an interface is sort of like an abstract class, except all its methods are abstract and it can't have any attributes.)
Ahhhh! So that explains the example I put up on the fisrt post!

So the interface is like a skeleton? The meat comes from classes that implement it? Can I do this in two files? One main class and other separate classes, where each separate class has an interface and the class that implements it?

:S I don't even know if I'm asking the questions correctly. Please let me know if that last question made no sense so I can reword.

---

### Post by satsujinka on 2012-04-12
Generally, in Java all classes are in separate files. Interfaces being something like an abstract class are no different. So using the shapes example:
```
//file Shape.java
public interface Shape {
...
}
``````
//file Circle.java
public class Circle implements Shape {
...
}
``````
//file Main.java
public class Main {
    public static void main(String[] args) {
        ...
    }
}
```

---

### Post by kevinharper on 2012-04-13
You are awesome Satsujinka!

I created the following 3 files, compiled them, and it worked!
**DimLamp**
```
public interface DimLamp {
	void turnOn(int newValue);
	void turnOff(int newValue);
	void dimUp(int increment);
	void dimDown(int decrement);
	void dimSetting();
}
```

**DimLampOnDesk**
```
class DimLamp {
	int on = 0;
	int brightness = 0;

	void turnOn(int newValue) {
		on = 1;
		brightness = 1;
	}

	void turnOff(int newValue) {
		on = 0;
		brightness = 0;
	}

	void dimUp(int increment) {
		brightness = brightness + increment;
	}

	void dimDown(int decrement) {
		brightness = brightness - decrement;
	}

	void dimSetting(){
		System.out.println("Brightness: " + brightness);
	}	
}
```

**OperateDimLampOnDesk**
```
class OperateDimLamp {
	public static void main(String[] args) {
		DimLamp dimLamp1 = new DimLamp();

		dimLamp1.turnOn(1);
		dimLamp1.dimUp(4);
		dimLamp1.dimDown(1);
		dimLamp1.dimSetting();
	}
}
```

Afterwards I realized that they ran even though I hadn't declared the a couple of the classes as public. I understand why OperateDimLampOnDesk ran and why the interface worked. But if the DimLampOnDesk wasn't declared public, why was it visible? Actually, don't worry. I'm getting ahead of myself. I need to proceed w/ the tutorial - I'm sure this will be explained shortly. :)

---

### Post by r-senior on 2012-04-13
> **kevinharper said:**
> Afterwards I realized that they ran even though I hadn't declared the a couple of the classes as public. I understand why OperateDimLampOnDesk ran and why the interface worked. But if the DimLampOnDesk wasn't declared public, why was it visible? Actually, don't worry. I'm getting ahead of myself. I need to proceed w/ the tutorial - I'm sure this will be explained shortly. :)
Before you move on, you haven't quite got this right. You've declared an interface but never used it. Which is a shame because the interface looks great. Your DimLamp class should implement the interface:

```
public class DimLamp implements DimLamp ...
```

But then there's a problem. You can't have an interface and a class with the same name. Sometimes interfaces and their implementations naturally have completely different names and it's not a problem. But in this case you need a better name for the class:

```
public class DimLampOnDesk implements DimLamp
```

So that's a dimmer for your desk lamp. You could then have a:

```
public class DimLampInCeiling implements DimLamp
```

Which is a different implementation of the same thing. The point is that the operations on the lamp are the same regardless of the type of lamp ... because it's still an implementation of the DimLamp interface.

```
DimLamp dimLamp = new DimLampOnDesk()
dimLamp.turnOn()
```

Which is easily changed to:

```
DimLamp dimLamp = new DimLampInCeiling()
dimLamp.turnOn()
```

Notice how the interface establishes that these lamps can have the same operations invoked on them, but the result is different. Notice also that the type of variable is declared as the interface, not the implementing class.

You'll see later why this is fundamentally important in Java programming but, for the time being, just note that you only need to change DimLampOnDesk to DimLampInCeiling in one place. In larger applications, that reduces a complex rats-nest of code that is difficult to untwine.

Your implementations should probably be public. The reason things work without public is that classes without a public designator are accessible to classes in the same package. If you haven't got to packages, don't worry. But these classes would usually be public.

Because a public class must be declared in a file of the same name, that will force you to have your interface and classes in three files:

[LIST=1]
[*]DimLamp.java (the DimLamp interface)
[*]DimLampOnDesk.java (the DimLampOnDesk class)
[*]OpeateDimLampOnDesk.java (the OperateDimLampOnDesk class)
[/LIST]

Sorry to pause you after you thought this was solved, but this is so important. Understanding interfaces is one of the keys to writing well-structured and easily maintained Java code. You may see the term "programming to interfaces" and this is what you are doing. It's fundamental to all sorts of advanced techniques like factories that make large applications easier to maintain.

---

### Post by kevinharper on 2012-04-14
> You've declared an interface but never used it. Which is a shame because the interface looks great. Your DimLamp class should implement the interface:
I realized that afterwards. Great catch!

> But then there's a problem. You can't have an interface and a class with the same name
Same thing. I saw only a single class and when I looked I saw that they both had the exact name. Again, great catch!

> You'll see later why this is fundamentally important in Java programming but, for the time being, just note that you only need to change DimLampOnDesk to DimLampInCeiling in one place. In larger applications, that reduces a complex rats-nest of code that is difficult to untwine.
Totally agree! That was actually why I initially decided to identify it as the one on the desk as opposed to the one on the fan (for example).

I have edited the classes and the interface, compiled, and ran successfully.

> Sorry to pause you after you thought this was solved, but this is so important
DO NOT APOLOGIZE! LOL, are you kidding! This was an awesome response! And I did not want to go on until I had an understanding of interfaces because, as you've pointed out, they are important.

Here is how it all looks now:
**DimLamp**
```
public interface DimLamp {
	void turnOn(int newValue);
	void turnOff(int newValue);
	void dimUp(int increment);
	void dimDown(int decrement);
	void dimSetting();
}
```

**DimLampOnDesk**
```
public class DimLampOnDesk implements DimLamp {
	int on = 0;
	int brightness = 0;

	public void turnOn(int newValue) {
		on = 1;
		brightness = 1;
	}

	public void turnOff(int newValue) {
		on = 0;
		brightness = 0;
	}

	public void dimUp(int increment) {
		brightness = brightness + increment;
	}

	public void dimDown(int decrement) {
		brightness = brightness - decrement;
	}

	public void dimSetting(){
		System.out.println("Brightness: " + brightness);
	}	
}
```

**OperateDimLampOnDesk**
```
class OperateDimLampOnDesk {
	public static void main(String[] args) {
		DimLamp dimLamp = new DimLampOnDesk();

		dimLamp.turnOn(1);
		dimLamp.dimUp(4);
		dimLamp.dimDown(1);
		dimLamp.dimSetting();
	}
}
```

Question: I had to make the methods in DimLampOnDesk public because I kept getting an "attempting to assign weaker access privileges" error when compiling. Did the methods within the interface automatially become public because the interface itself is declared public?

---

### Post by satsujinka on 2012-04-14
All method's of an interface must be public. Basically, if someone where to get your interface and try to implement it, but there were protected or private methods they couldn't do it. So in order for interfaces to work they can/must only specify the public capabilities that any implementation must have.

---

### Post by kevinharper on 2012-04-14
Awesome! Makes perfect sense! Thank You!

---

