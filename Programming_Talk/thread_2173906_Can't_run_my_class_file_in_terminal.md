---
title: "Can't run my class file in terminal"
date: 2013-09-11
forum: Programming Talk
---

### Post by Joyccccccc on 2013-09-11
This is my code:
```
package mie250;

import java.io.*;


public class project1 {
	
	public static void main(String[] args) throws NumberFormatException, IOException {
		
	    double GROWTH_RATE = 1+0.0111-0.00774+0.00563;
		
		System.out.print("JAVA POPULATION PREDICTOR\n");
		
		BufferedReader cin = new BufferedReader (new InputStreamReader (System.in ));
		
		System.out.print("Enter current population:");
		double pop = Double.parseDouble (cin.readLine ());
		if (pop < 0) {
			System.out.print("\nERROR: Population size must be positive!\n");
			return;
		}
		
		System.out.print("Enter number of years in the future:");
		int yr = Integer.parseInt(cin.readLine());
		if (yr < 0) {
			System.out.print("\nERROR: Number of years must be positive!\n");
			return;
		}
		
		int i;
		double pop1 = pop;
		
		for (i=1; i<=yr; i++){
			pop = pop * GROWTH_RATE;
			System.out.format("Year %d: %.4f\n", i, pop);
		}
		
		System.out.format("Over %d years, the population grows to %.4f, a %.2f%% growth rate.", yr, pop, (pop-pop1)/pop1*100 );
		
		
	}


}



```

And this is what happened when I was trying to run the class file in terminal.
localhost:mie250 joyce$ java project1
```
Exception in thread "main" java.lang.NoClassDefFoundError: project1 (wrong name: mie250/project1)
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClassCond(ClassLoader.java:631)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:615)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:141)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:283)
	at java.net.URLClassLoader.access$000(URLClassLoader.java:58)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:197)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:247)

```

And I can run the code perfectly in eclipse, but just not in terminal.
Can someone give some suggestions?
Thank you very much!!!!

---

### Post by Toz on 2013-09-11
Hello and welcome to the forums.

I'm moving your thread to the **Programming Talk** subforum for better visibility.

---

### Post by 1clue on 2013-09-11
Is your class file in src/java/mie250/project1.java?

Remember Linux filesystem is case sensitive.  By convention your class name should be capitalized, so it would be src/java/mie250/Project1.java and public class Project1.

One problem with Eclipse is it silently corrects a lot of bad behavior.  It shouldn't do that.

---

### Post by ofnuts on 2013-09-12
To start you code:
- the "project1.class" file should be a directory named "mie250"
- the current directory should the parent of "mie250"
- the program can then be started with "java mie250.project1"

As noted above, the Java naming conventions say that your class names should have an initial Capital.

---

### Post by 1clue on 2013-09-12
What's your command line to run this?  Maybe you're missing something like a classpath specifier to the src/java directory?

---

