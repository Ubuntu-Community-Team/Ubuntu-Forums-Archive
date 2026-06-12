---
title: "Java - A Very Basic Class"
date: 2012-04-10
forum: Programming Talk
---

### Post by kevinharper on 2012-04-10
[http://docs.oracle.com/javase/tutorial/java/concepts/QandE/questions.html](http://docs.oracle.com/javase/tutorial/java/concepts/QandE/questions.html)

Has a couple of exercises at the bottom:
1) Create new classes for each real-world object that you observed at the beginning of this trail. Refer to the Bicycle class if you forget the required syntax.
Answer:
```

class RealWorldClasses {
	public static void main(String[] args) {
		System.out.println("Done!");
	}
}

class DimmerLamp {
	int dimmer = 0;

	void dimUp(int increment) {
		dimmer = dimmer + increment;
	}

	void dimDown(int decrement) {
		dimmer = dimmer - decrement;
	}
}

class Lamp {
	int on = 0;

	void changeOn(int newValue) {
		on = newValue;
	}
}

class Book {
	int page = 1;

	void turnNextPage() {
		page++;
	}

	void turnPrevPage() {
		page--;
	}

	void turnToPage(int newValue) {
		page = newValue;
	}
}

```
I saved it as realworldclasses.java and compiled it successfully. This created the following class files: Book, Lamp, DimmerLamp, and RealWorldClasses.

2) For each new class that you've created above, create an interface that defines its behavior, then require your class to implement it. Omit one or two methods and try compiling. What does the error look like?
Source:
```

public class DeskLamps implements DimmerLamp {
	int dimmer = 0;

	void dimUp(int increment) {
		dimmer = dimmer + increment;
	}

	void dimDown(int decrement) {
		dimmer = dimmer - decrement;
	}
}

public class TallLamps implements Lamp {
	int on = 0;

	void changeOn(int newValue) {
		on = newValue;
	}
}

public class AccountingBooks implements Book {
	int page = 1;

	void turnNextPage() {
		page++;
	}

	void turnPrevPage() {
		page--;
	}

	void turnToPage(int newValue) {
		page = newValue;
	}
}

```
I saved it as implement.java, compiled it and got the following errors:
> 
implement.java:1: class DeskLamps is public, should be declared in a file named DeskLamps.java
public class DeskLamps implements DimmerLamp {
       ^
implement.java:13: class TallLamps is public, should be declared in a file named TallLamps.java
public class TallLamps implements Lamp {
       ^
...
6 errors


Questions:
Should I have included my code for #2 in the same .java file I created for #1? I'm not sure I understand all the different class files that are created.

---

### Post by kevinharper on 2012-04-10
Here ([http://www.coderanch.com/t/410062/java/java/Compiling-java-code-having-different](http://www.coderanch.com/t/410062/java/java/Compiling-java-code-having-different)) it says:
> 
Remember one thing.
You can have as many classes as you want in your *.java file.But among those classes, only one class can have PUBLIC visibility and that class name should match with your java file name.

So should I create a .java file for each one of my implementations?

---

### Post by Some Penguin on 2012-04-11
> **kevinharper said:**
> Here ([http://www.coderanch.com/t/410062/java/java/Compiling-java-code-having-different](http://www.coderanch.com/t/410062/java/java/Compiling-java-code-having-different)) it says:

So should I create a .java file for each one of my implementations?

Since you've made them public classes?  Yes.

You generally should favor one class per file unless they're nested classes; this makes them easier (well, possible!) to find.

---

### Post by kevinharper on 2012-04-11
Awesome.. Thank you! Last night I noticed that I was accidentally skipping content from the online tutorial at java.com so I will be starting over again. I'm sure some of this was covered in the skipped material.

---

