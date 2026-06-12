---
title: "compiling a java program"
date: 2009-08-08
forum: Programming Talk
---

### Post by swappo1 on 2009-08-08
Hello,

I am taking a class in programming in a month and they will be teaching java.  I thought I would start early and familiarize myself with java using a library copy of Sams teach yourself java6 in 21 days.  I was able to get a simple hello world program with one file to compile and run.  When I try to get a program with two files to compile I get some errors.  Here is the errors and files:
```

VolcanoRobot.java
class VolcanoRobot
{
	String status;	//instance variables
	int speed
	float temperature;
	
	void checkTemperature()	//method
	{
		if(temperature > 660)
		{
			status = "returning home";
			speed = 5;
		}
	}
	
	void showAttributes()
	{
		System.out.println("Status: " + status);
		System.out.println("Speed: " + speed);
		System.out.println("Temerature: " + temperature);
	}
}

VolcanoApplication.java
class VolcanoApplication
{
	public static void main(String[] arguments)
	{
		VolcanoRobot dante = new VolcanoRobot();
		dante.status = "exploring";
		dante.speed = 2;
		dante.temperature = 510;
		
		dante.showAttributes();
		System.out.println("Increasing speed to 3.");
		dante.speed = 3;
		dante.showAttributes();
		System.out.println("Changing temperature to 670.");
		dante.temperaure = 670;
		dante.showAttributes();
		System.out.println("Checking the temperature.");
		dante.checkTemperature();
		dante.showAttributes();
	}
}

Errors:
[hopchewer@hopchewer volcanorobot]$ javac VolcanoApplication.java
----------
1. ERROR in VolcanoApplication.java (at line 25)
	VolcanoRobot dante = new VolcanoRobot();
	^^^^^^^^^^^^
VolcanoRobot cannot be resolved to a type
----------
2. ERROR in VolcanoApplication.java (at line 25)
	VolcanoRobot dante = new VolcanoRobot();
	                         ^^^^^^^^^^^^
VolcanoRobot cannot be resolved to a type
----------
2 problems (2 errors)[hopchewer@hopchewer volcanorobot]$ 

```I am using gedit along with the terminal plugin.  The two files are saved in volcanorobot.  Any ideas what I am doing wrong?

---

### Post by baizon on 2009-08-08
First you have to compile VolcanoRobot.java, then VolcanoApplication.java. The error is because the main method is trying to access the VolcanoRobot.class but could not find it.

```

hopchewer@hopchewer volcanorobot]$ javac VolcanoRobot.java
hopchewer@hopchewer volcanorobot]$ javac VolcanoApplication.java

```

P.S.
You got 2 syntax errors in the code.
```

VolcanoApplication.java
dante.temperature = 670;

VolcanoRobot.java
int speed;

```

---

### Post by swappo1 on 2009-08-08
Ok, I fixed my two syntax errors.  I compiled VolcanoRobot.java and now have VolcanoRobot.class in the volcanorobot folder.  When I compile VolcanoApplication, I get the same errors again.
```
[hopchewer@hopchewer volcanorobot]$ javac VolcanoApplication.java
----------
1. ERROR in VolcanoApplication.java (at line 5)
	VolcanoRobot dante = new VolcanoRobot();
	^^^^^^^^^^^^
VolcanoRobot cannot be resolved to a type
----------
2. ERROR in VolcanoApplication.java (at line 5)
	VolcanoRobot dante = new VolcanoRobot();
	                         ^^^^^^^^^^^^
VolcanoRobot cannot be resolved to a type
----------
2 problems (2 errors)[hopchewer@hopchewer volcanorobot]$ 

```

---

### Post by baizon on 2009-08-08
Ah ok, i think i found whats wrong. 
Please change class to "public class".
```

public class VolcanoRobot {
	String status;	//instance variables
	int speed;
	float temperature;
	
	void checkTemperature()	//method
	{
		if(temperature > 660)
		{
			status = "returning home";
			speed = 5;
		}
	}
		
	void showAttributes()
	{
		System.out.println("Status: " + status);
		System.out.println("Speed: " + speed);
		System.out.println("Temerature: " + temperature);
	}
}

```

Edit: Hmm strange, without public its still working when i compile it.
Are both .java files in the same directory?

---

### Post by swappo1 on 2009-08-08
> Please change class to "public class".
I am still getting the same errors with this change.

---

### Post by baizon on 2009-08-08
What (version of) Java are you using?

---

### Post by swappo1 on 2009-08-08
Version:
> [hopchewer@hopchewer ~]$ java -version
java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) Server VM (build 14.0-b16, mixed mode)


---

### Post by baizon on 2009-08-08
Are you sure that the both .java and .class files in the same directory? I've compiled it and on my PC and i didn't get any error messages so the code must be OK.

---

### Post by swappo1 on 2009-08-08
> Are you sure that the both .java and .class files in the same directory?
Yes.
```
[hopchewer@hopchewer volcanorobot]$ ls
VolcanoApplication.java  VolcanoRobot.class  VolcanoRobot.java

```
I use the gnu compiler for C/C++.  Is this using the gnu compiler for java as well?  If so, I usually use gcc or g++ for C and C++.  Is there something like this for java that I shoul be entering to compile and link the files?

---

### Post by baizon on 2009-08-08
Hmm, try to make a package with this two .java files.
Create a folder "temp" and copy that two .java files into it, then add the first line into this two .java files.

```

package temp;
class VolcanoApplication {
	public static void main(String[] arguments) {
		VolcanoRobot dante = new VolcanoRobot();
		dante.status = "exploring";
		dante.speed = 2;
		dante.temperature = 510;
		
		dante.showAttributes();
		System.out.println("Increasing speed to 3.");
		dante.speed = 3;
		dante.showAttributes();
		System.out.println("Changing temperature to 670.");
		dante.temperature = 670;
		dante.showAttributes();
		System.out.println("Checking the temperature.");
		dante.checkTemperature();
		dante.showAttributes();
	}

}

```

---

### Post by swappo1 on 2009-08-08
I added the specified line to VolcanoApplication.java, saved both files to /volcanorobot/temp and I got the same results as before.  I also tried running the program in netbeans and this is what I got:
```
Created dir: /home/hopchewer/NetBeansProjects/volcanorobot/build/classes
Created dir: /home/hopchewer/NetBeansProjects/volcanorobot/build/empty
Compiling 2 source files to /home/hopchewer/NetBeansProjects/volcanorobot/build/classes
/home/hopchewer/NetBeansProjects/volcanorobot/src/volcanorobot/Main.java:19: cannot find symbol
symbol  : class VolcanoRobot
location: class volcanorobot.Main
        VolcanoRobot dante = new VolcanoRobot();
/home/hopchewer/NetBeansProjects/volcanorobot/src/volcanorobot/Main.java:19: cannot find symbol
symbol  : class VolcanoRobot
location: class volcanorobot.Main
        VolcanoRobot dante = new VolcanoRobot();
2 errors
/home/hopchewer/NetBeansProjects/volcanorobot/nbproject/build-impl.xml:363: The following error occurred while executing this line:
/home/hopchewer/NetBeansProjects/volcanorobot/nbproject/build-impl.xml:168: Compile failed; see the compiler error output for details.
BUILD FAILED (total time: 0 seconds)

```
Although, this is the first time I have ever used netbeans and I am not at all familiar with it.

---

### Post by Ragazzo on 2009-08-09
Did you try **javac VolcanoApplication.java VolcanoRobot.java** ie both files as arguments

---

### Post by credobyte on 2009-08-09
Place both files into a separate directory and execute this command from terminal ( don't forget to cd to your newly created directory ):
```
javac *.java

```

---

