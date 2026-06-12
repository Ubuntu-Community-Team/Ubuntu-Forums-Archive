---
title: "Getting Started With Eclipse"
date: 2009-03-20
forum: Programming Talk
---

### Post by darksideforge on 2009-03-20
[B][I]On the workbench.
Attempted the tutorial...still not getting it.
Created a new package.
Opened a new class.

Here's what I'm looking at now:[/I][/B]

```
package hw4;

class HelloWorld {

	/**
	 * @param args
	 */
	public static void main(String[] args) {
		// TODO Auto-generated method stub

	}

}
```

***Now...where do I enter/cut/paste***

```
System.out.printIn(HelloWorld);
```

???

(and I'm not sure I remembered that exactly so correct me please)

---

### Post by shatterblast on 2009-03-20
I like mine better.

```

public class WazzupWorld {
	// Like... it says "hello" and stuff!
	public static void main(String args[]) {
		System.out.print("Wazzup mah world!  I be chilling in da output screen, yo.\n");
	}
	// End of ridiculous "hello world" app.
	// @Good example of what not to do. Who wrote this anyway?
}
```

---

### Post by simeon87 on 2009-03-20
It's better to get some tutorials and follow them because this is really basic :popcorn:

---

### Post by aszxcv on 2009-03-20
use these [http://eclipsetutorial.sourceforge.net/totalbeginner.html](http://eclipsetutorial.sourceforge.net/totalbeginner.html)

[http://sourceforge.net/project/showfiles.php?group_id=200662&package_id=275814](http://sourceforge.net/project/showfiles.php?group_id=200662&package_id=275814)

---

### Post by jespdj on 2009-03-20
[Sun's Java Tutorials](http://java.sun.com/docs/books/tutorial/) is the best place online to start learning how to program in Java.

---

### Post by darksideforge on 2009-03-20
> **shatterblast said:**
> I like mine better.

```

public class WazzupWorld {
	// Like... it says "hello" and stuff!
	public static void main(String args[]) {
		System.out.print("Wazzup mah world!  I be chilling in da output screen, yo.\n");
	}
	// End of ridiculous "hello world" app.
	// @Good example of what not to do. Who wrote this anyway?
}
```

FINALLY!!! Thank you!  It's not as pretty as yours but it didn't have any errors either and when I ran it, it printed in the small screen in the bottom!
```

/**
 * 
 */

/**
 * @author darkside
 *
 */
class WazzupWorld1 {

	/**
	 * @param args
	 */
	public static void main(String[] args) {System.out.print("wazzupworld!");}
	
		// TODO Auto-generated method stub

	}
```

---

### Post by darksideforge on 2009-03-20
Thanks everybody, for putting these links up...I'm on 'em now!:popcorn:

---

### Post by simeon87 on 2009-03-20
> **darksideforge said:**
> FINALLY!!! Thank you!  It's not as pretty as yours but it didn't have any errors either and when I ran it, it printed in the small screen in the bottom!
```

/**
 * 
 */

/**
 * @author darkside
 *
 */
class WazzupWorld1 {

	/**
	 * @param args
	 */
	public static void main(String[] args) {System.out.print("wazzupworld!");}
	
		// TODO Auto-generated method stub

	}
```

Be careful with the layout: the second } actually closes the class, not the method as one would expect at first glance.

---

### Post by shatterblast on 2009-03-20
Also if you plan on sharing your code often, you might check out the Format commands in NetBeans or Eclipse.  (I like NetBeans, but I really can't tolerate its way of handling the Tab key.)  In Eclipse you can choose your project, then go to Source then Format.  It helped me learn about organizing code.  I personally adapted to Java faster by avoiding Swing at first.  ;)

---

