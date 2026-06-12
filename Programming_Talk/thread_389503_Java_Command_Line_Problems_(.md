---
title: "Java Command Line Problems :("
date: 2007-03-20
forum: Programming Talk
---

### Post by ClinicalMistake on 2007-03-20
Hey everyone, I'm in an intro to java class and it seems that when I tried to compile my program, I encountered some strange errors.  I don't think my code is wrong, but I am still an intro student so I don't like to assume.  First off, here's my code.

```
/*Justin B.
CSCI 1236
Mar 19 */
public class Saluton {
	public static void main(String[] args) {
		String greeting = "Hello World!";
		System.out.println(greeting);
	}
}
```

I first compiled it in Eclipse and everything worked pretty well.  However I then tried to compile it in command line using the javac command.  When I tried to run it though, I encountered this error.

```
Exception in thread "main" java.lang.NoClassDefFoundError: Saluton/java

```

I'm assuming I'm missing either a library (I think it's called this) or something isn't linked right.  Any help would be greatly appreciated.  I'm new to linux and I'd really like to be able to do my CS homework on this computer, instead of using the school's machines.

Thanks!

---

### Post by monkeyking on 2007-03-20
What have you called your file,
and what do you type in at the promt?

When you want to compile just should type in
```

javac Salution.java

```
And when you want to run it you should type in
```

java Salution

```

---

### Post by Tomosaur on 2007-03-20
It looks like you tried to run it like this:
```

java Saluton.java

```
right?

Java **source** files follow the pattern 'file.java'

When you want to compile a java source file, you type:
```

javac file.java

```

The compiler runs and creates a file called 'file.class'. In you case, you will have a file called 'Saluton.class'

When you want to RUN your program, you just type:
```

java program_name

```

Where 'program_name' is the name of the class with the main method in. In your case then, you would type:

```

java Saluton

```

Note that you do not need to type the full filename. If you type:
```

java Saluton.java

```

or

```

java Saluton.class

```

Then you will get the error you described above.

The reason for this is that in Java, the . character means 'inside'. So, if you look at your System.out.println line, what the Java virtual machine actually reads this as, is:
```

Pass the 'greeting' string to the 'println' method which is INSIDE the 'out' class, which is inside the 'System' package.

```

So, when you run your program like this:
```

java Saluton.java

```

The Java vm THINKS you are trying to tell it the following:
```

Run the 'java' method, which is INSIDE the 'Saluton' class

```.

Obviously, this will not work. It's a little different from that, but that should explain the error anyway.

Any more problems, don't hesitate to ask here :)

---

### Post by blastus on 2007-03-20
If the current directory is the directory Saluton.java resides...

```
javac Saluton.java
java Saluton
```

You can also use...

```
javac -cp . Saluton.java
java -cp . Saluton
```

If the current directory is one up from where Saluton.java resides and Saluton.java resides in a directory called src you can...

```
javac src/Saluton.java
java -cp src Saluton
```

---

### Post by ClinicalMistake on 2007-03-20
Wow, thanks everyone for the quick response!  It turns out that I was running java Saluton.class instead of java Saluton!

Now that I've seen the error you're talking about, I can see the mistake I made.  It really shows that I'm more of a newb than I thought!

Thanks monkeyking, Tomosaur & blastus! :D

---

