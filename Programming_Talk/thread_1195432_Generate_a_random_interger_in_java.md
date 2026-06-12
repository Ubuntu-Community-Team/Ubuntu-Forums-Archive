---
title: "Generate a random interger in java?"
date: 2009-06-23
forum: Programming Talk
---

### Post by Zargoon on 2009-06-23
So I'm fairly new to programming, and I'm trying to create a simply program.  For this program I need to be able to generate a 'random' integer.  Here's how I went about trying to do this:


I created a "Randomint" class that is supposed to make a random integer between 0 and 10.
```

import java.util.Random;

public final class Randomint {
	
	  public static final void main(String... aArgs) {
		  
		  Random randomGenerator = new Random();
		  int rint = randomGenerator.nextInt();
		  int random_number = rint % 10;
		  if (random_number < 1) random_number = random_number + 10;

		  
	  }

}

```

And here's my main argument:
```

public class Problemgenerator {
	
	public static void main(String[] args) {
			
		Randomint rint = new Randomint();
		System.out.println(rint);
		
	}
	
}

```

I think it should work, but when I run it I get an output like:

math.Randomint@158c662c

Which isn't very helpful, obviously.

Well thanks in advance for any light you guys can shed on this!

---

### Post by Reiger on 2009-06-23
Well what does System.out.println(); expect? Answer: a String.
Why does your program compile at all, then? Answer: there is an implicit cast to String.
What type of cast, then? Answer (String)( (Object) rint);
Why the cast from Randomint to Object? Answer: because your object uses the inherited toString() method. That is first the enviroment tries to see if your object has a toString() method (which is what the cast of Object to String uses to obtain a String), and it doesn't. But its super object does.

So the bottom line is that for your design to work as expected you must supply a custom public String toString() method in your Randomint object.

Incidentally I presume (because you use java.util.Random directly) you already knew about Math.random() ?

---

### Post by pbrockway2 on 2009-06-23
A few things:

rint%10 will evaluate to an integer between 0 and 9 inclusive.  Because of the if statement you end up with a number in the range **1** to 10.  And remember that there is another form of the [rint(int) method]("http://java.sun.com/javase/6/docs/api/java/util/Random.html#nextInt(int)") that you could use.

There are lots of println() methods - including one that takes a reference to an Object instance.  (It's not true that there is any casting going on - you can convince yourself of this by trying to cast Randomint to a String).  But as suggested for this to give the output you want, you have to declare a method in the Randomint class that returns the string form that you want to see.

In your case you don't have to even do this.  Get rid of the Randomint class completely.  The main method of Problemgenerator can do what you are doing now in a couple of lines: the first using nextInt(int) to obtain a random int in the correct range, and the second using println() to print that int.

(On the other hand if it is your intention to have a Randomint class that represents a value determined randomly when an instance is created, then you had better read up on constructors and accessor (getter) methods.  Such a class would not typically have a static main() method at all.)

---

### Post by Zargoon on 2009-06-24
Okay, I'll give it a try.  Thanks!

---

