---
title: "[SOLVED] Simple java comiling question"
date: 2008-12-07
forum: Programming Talk
---

### Post by andrew222 on 2008-12-07
Hello,

Thank you for reading this question.  I wanted to post it to the 'Absolute Beginner Talk' forum but since it is a specific programming question I thought that I should post it here.  It is a simple question...


I compiled a simple .java file on Eclipse without any compilation or runtime errors.  

However, when I compiled the program by command line I got these errors (output from terminal posted below)


[I][COLOR="Sienna"]andrew@andrew-desktop:~$ cd ./workspace/Three/com/spaceage/array
andrew@andrew-desktop:~/workspace/Three/com/spaceage/array$ javac MyArray.java
andrew@andrew-desktop:~/workspace/Three/com/spaceage/array$ java MyArray
Exception in thread "main" java.lang.NoClassDefFoundError: MyArray (wrong name: com/spaceage/array/MyArray)
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:621)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
	at java.net.URLClassLoader.access$000(URLClassLoader.java:56)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: MyArray.  Program will exit.[/COLOR]

[/I]


The .java file is attached to this post, to run it just comment out the package declaration.

Any help / insight / suggestions are welcome

Thank you for reading this and I look forward to any replies...

---

### Post by tinny on 2008-12-07
Can you please post the code for "MyArray"

Does MyArray have a "main" method?

---

### Post by andrew222 on 2008-12-07
Hello tinny,


I'm sorry, I thought that I had attached it to my previous thread. The code is posted blow and the file should be attached this time to this post.  When using the file just comment out the package declaration....





class One {}
 class Two {}


 class MyArray {
	 
		

	public static void main(String[] args)  {
		// I had to cast the argument to a byte from an int
		Byte byteObj = new Byte((byte) 4);
        //I had to cast the argument to a short from an int
		Short shortObj = new Short((short) 8);
		Character charObj = new Character('@');
		Boolean boolObj = new Boolean("TrUe"); // case is ignored....
		Integer intObj = new Integer(12);
		Long longObj = new Long(512);
		Float floatObj = new Float(3.14);
		// The pi vlue was accepted....interesting
		Double doubleObj = new Double(3.1415926535897932384626433832795028841971693993751058209749445923078164062862089986280348253421170679);
		One o = new One();
		Two t = new Two();
		String str = "one";
		Exception e = new Exception();
		Throwable th = new Throwable();
		Object ob = new Object();
		
		// Making a Class object for use in displaying the contents of the array
		Class clObj;
		
		//I thought I'd use an anonymous array for this one....
		Object [] objArray = {byteObj, shortObj, charObj, boolObj, intObj, longObj, floatObj, doubleObj, o,t, str,e, th, ob };
		
		for (int i = 0; i < objArray.length ; i++)  {
			
			//Using the getClass() method of objArray[] to return a Class object for that object
			// that is referred to by this varaiable.
			clObj = objArray[i].getClass();
			
			//Using the getName() method of the clObj Class object to get the name of the class to 
			// print on the console.
			System.out.println("Element "+i+": is a reference to "+clObj.getName());	
		    /*If I had used getSimpleName it would just print out the class name,
			  by using getName() I'll get the full path "com.spaceage.array.One"
			    instead of "One".........*/
			
			/*It makes no sense to print values out because the array only holds references to objects,
			 * allthough the primitive wrapper objects would show a vlue as for the String object as well.
			 * */
		}	
	}

}

---

### Post by Unterseeboot_234 on 2008-12-07
I use NetBeans, so I reckon there is some similarities to Eclipse. In the IDEs, the environment is controlled for Current Working Directory by the IDE and, in NetBeans at least, we are requested to create packages for the source code.

If you take your code out of the IDE and put the file lose in a folder and you are at conflict with CWD and package. [Assuming your path variable for the java SDK is correct] The IDE will keep the pathnames it needs to switch back and forth between the "build" and the "src". Thus, when you move a java code out of the IDE, your code won't find txt, png, /images/mypic.gif so on. package is the other path problem if you are not in a .jar.

Delete the package statement to your source files, Save and then javac AFTER using terminal to CD into the folder. Then main() becomes a top level method -- myClass.main; instead of org.mycode.myClass.main;

Just a suggestion...

---

### Post by andrew222 on 2008-12-07
Thank you very much...I will try this.

---

### Post by Unterseeboot_234 on 2008-12-07
I apologize, but when Forums times me out or I hit the browser's page refresh button, I get a double post.

---

### Post by andrew222 on 2008-12-07
I did try this and received the same error messages. 

[COLOR="DarkRed"]andrew@andrew-desktop:~$ ./l
javac: file not found: Myarray.java
Usage: javac <options> <source files>
use -help for a list of possible options
Exception in thread "main" java.lang.NoClassDefFoundError: MyArray (wrong name: com/spaceage/array/MyArray)
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:621)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
	at java.net.URLClassLoader.access$000(URLClassLoader.java:56)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: MyArray.  Program will exit.
andrew@andrew-desktop:~$ [/COLOR]





 I used the following shell script to compile / run the code


[I]#!/bin/bash

cd ./workspace/Three/com/spaceage/array

javac Myarray.java

java MyArray
[/I]

---

### Post by Unterseeboot_234 on 2008-12-07
I just tried javac, I don't have JDK connected with an .so link outside my IDE. Anyhow, your source is MyArray and u javac myArray which isn't allowed.

---

### Post by geirha on 2008-12-07
Could you edit the post with the code and add code-tags around it please? Just mark the code and click the # icon on the textbox toolbar. Makes it much easier to read.

Anyway, it compiles and runs for me, so what version of java are you using?
```
javac -version
java -version
```

---

### Post by Unterseeboot_234 on 2008-12-07
Okay, I just slammed this through NetBeans (I will link the path var in /opts later so I can javac outside .jars) Also, I trunicated your Double, which is 32 binary as a plus decimal. Use class BigDecimal which takes a string to put in "paragraph" numbers. Your code works because you have used Wrappers of the primitives.

```

Element 0: is a reference to java.lang.Byte
Element 1: is a reference to java.lang.Short
Element 2: is a reference to java.lang.Character
Element 3: is a reference to java.lang.Boolean
Element 4: is a reference to java.lang.Integer
Element 5: is a reference to java.lang.Long
Element 6: is a reference to java.lang.Float
Element 7: is a reference to java.lang.Double
Element 8: is a reference to test.One
Element 9: is a reference to test.Two
Element 10: is a reference to java.lang.String
Element 11: is a reference to java.lang.Exception
Element 12: is a reference to java.lang.Throwable
Element 13: is a reference to java.lang.Object
BUILD SUCCESSFUL (total time: 0 seconds)

```

I have to say, after I struggled and struggled with Gererics, your code gives me something to think about.

---

### Post by howlingmadhowie on 2008-12-07
if i remember correctly in java, if you have multiple class definitions in one file, the one the file is named after has to be made public.

---

### Post by Unterseeboot_234 on 2008-12-07
public, final, transient, private, abstract and default are the class modifiers. default = empty, no declaration -- any class in the package has access, and we are outside any package. method includes protected and static as a modifier. just FYI.

---

### Post by andrew222 on 2008-12-07
Thank you very much for the replies:


**Unterseeboot_234:**  There was a typo in the shell file, it should have been as 'javac MyArray.java' instead of the 'Myarray' which was previously in there. 

I'll have to get a .jar file for the code and see if that helps compiling by command line...


**Geirha: ** This is the output, per your request.


[I][COLOR="SlateGray"]andrew@andrew-desktop:~$ javac -version
javac 1.6.0_10
andrew@andrew-desktop:~$ java -version
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Client VM (build 11.0-b15, mixed mode, sharing)[/COLOR][/I]


Thank you very much for your replies....

---

### Post by andrew222 on 2008-12-07
**Howlingmadhowie:** I did make the class with the main method public and did continue to recieve the same error messages by compiling through command line...

---

### Post by howlingmadhowie on 2008-12-07
> **Unterseeboot_234 said:**
> public, final, transient, private, abstract and default are the class modifiers. default = empty, no declaration -- any class in the package has access, and we are outside any package. method includes protected and static as a modifier. just FYI.

you're going to have to tell me what the point of a private class could possibly be. a private instance i can understand, but how can you instantiate a private class? if you want to force inheritance, you can use abstract.

---

### Post by howlingmadhowie on 2008-12-07
> **andrew222 said:**
> **Howlingmadhowie:** I did make the class with the main method public and did continue to recieve the same error messages by compiling through command line...

don't make the method public, make the class public:

```
public class MyClass { /* stuff */ 

public static void main(String []args) { ... }
}
```

the compiler needs this


edit ------

sorry, misread you there :)

---

### Post by Unterseeboot_234 on 2008-12-07
use a **private class** as inner and the vars are naked to the enclosing, outer class.

for instance

```
class DisplayPanel extends JPanel {

public DisplayPanel() {
blah, blah, blah
}
public void paintComponent(Graphics g) {
draw( redBall );
}
private class RedBall {
public RedBall()
}
}
}

```

..........

Enjoyed the thread on this. I want to learn java and I did gain something here.

---

### Post by andrew222 on 2008-12-07
Hello Howie,

I did mean to infer that the class was given a public accessor  just as your example implies.

thanks again,

Andrew

---

### Post by drubin on 2008-12-07
> **andrew222 said:**
> Hello tinny,


I'm sorry, I thought that I had attached it to my previous thread. The code is posted blow and the file should be attached this time to this post.  When using the file just comment out the package declaration....


Please use code/php tags in your next posts. I makes things much easier to read, and in turn help you out.

---

### Post by howlingmadhowie on 2008-12-07
then the only thing i can think of is that you're starting the class from the wrong place or compiling it from the wrong place or not setting the right classpath explicitly and all the other problems java has which mandate the use of eclipse or netbeans just to get simple things to work.

end of rant about java.

p.s. i got an scjp a couple of months ago, so i'm allowed to rant about java :)

---

### Post by andrew222 on 2008-12-07
Thank you very much Howie,

Embarrassingly, there was a typo in my shell script (mentioned previously).  After reading your last post, I commented out the package declaration, and it runs just fine.


This was a great thread with a lot of good minds giving great information and ideas. Thank you again and have a great week...


Andrew

---

### Post by geirha on 2008-12-07
You can also compile programs with package declarations from the command-line, but the file must be placed inside directories accordingly. For instance, if you add ```
package foo.bar;
``` to the start of your MyArray.java, then you'll need to move MyArray.java into */foo/bar*:

```
$ mkdir -p foo/bar/
$ echo 'package foo.bar;' > foo/bar/MyArray.java
$ cat MyArray.java >> foo/bar/MyArray.java
$ javac foo/bar/MyArray.java
$ java foo.bar.MyArray
Element 0: is a reference to java.lang.Byte
...
$ cd foo/bar
$ java MyArray
Exception in thread "main" java.lang.NoClassDefFoundError: MyArray (wrong name: foo/bar/MyArray)
...

```

BTW, if you feel this thread is solved, mark it as solved using the Thread Tools dropdown. Helps others with similar problems find a solution to their problem, and also saves people reading through a thread they want to help out on, only to find it has already been solved.

---

### Post by andrew222 on 2008-12-07
Thank you very much geirha, I just clicked a 'Thank You' to you as well.....

---

