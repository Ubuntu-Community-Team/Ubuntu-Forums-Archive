---
title: "Help with a Java program"
date: 2007-03-02
forum: Programming Talk
---

### Post by the.dark.lord on 2007-03-02
Can anyone translate this Java program written for Windows into Mac language? Thanks in advance.

```

import java.io.*;

public class areasquarerect

{

	public static void main(String[] args) throws IOException

	{

		BufferedReader keyin = new BufferedReader(new InputStreamReader(System.in));

		String instr;

		double l,b,a;

		l=b=a=0;

		System.out.println("enter the length of a side of a square: ");

		instr=keyin.readLine();

		a=Double.parseDouble(instr);

		System.out.println("enter the length a rectangle: ");

		instr=keyin.readLine();

		l=Double.parseDouble(instr);

		System.out.println("enter the breadth of a rectangle : ");

		instr=keyin.readLine();

		b=Double.parseDouble(instr);

		System.out.println("area of square  = "+(4*a*a));

		System.out.println("area of rectangle = "+(2*(l+b)));

	}

}

```

---

### Post by lnostdal on 2007-03-02
sure, here:
```

import java.io.*;

public class areasquarerect

{

	public static void main(String[] args) throws IOException

	{

		BufferedReader keyin = new BufferedReader(new InputStreamReader(System.in));

		String instr;

		double l,b,a;

		l=b=a=0;

		System.out.println("enter the length of a side of a square: ");

		instr=keyin.readLine();

		a=Double.parseDouble(instr);

		System.out.println("enter the length a rectangle: ");

		instr=keyin.readLine();

		l=Double.parseDouble(instr);

		System.out.println("enter the breadth of a rectangle : ");

		instr=keyin.readLine();

		b=Double.parseDouble(instr);

		System.out.println("area of square  = "+(4*a*a));

		System.out.println("area of rectangle = "+(2*(l+b)));

	}

}

```

```

lars@ibmr52:~/programming/java$ javac areasquarerect.java 
lars@ibmr52:~/programming/java$ java areasquarerect
enter the length of a side of a square: 
2
enter the length a rectangle: 
4
enter the breadth of a rectangle : 
5
area of square  = 16.0
area of rectangle = 18.0

```

oh, and it works on linux too .. so both windows, linux and mac then

---

### Post by Ramses de Norre on 2007-03-02
> **the.dark.lord said:**
> Can anyone translate this Java program written for Windows into Mac language? Thanks in advance.

I think you're missing one of the most important features of java: it's platform independent.
If you use only standard classes (or other *well designed* classes) your program will run on every computer which has a jre installed.

---

### Post by the.dark.lord on 2007-03-02
Thanks Ramses adI'm quite new to programming, I know it is was platform independent. But, it wouldn't work when I tried it out on this iMac. Does mac has JRE installed by default?

---

### Post by maxamillion on 2007-03-02
> **the.dark.lord said:**
> Thanks Ramses adI'm quite new to programming, I know it is was platform independent. But, it wouldn't work when I tried it out on this iMac. Does mac has JRE installed by default?

Yes, OS X comes with Java by default.

---

### Post by Ramses de Norre on 2007-03-02
Why didn't it work? Because it didn't found the java executable or because it threw an exception?
If java -version returns somethings and it's not an error you've got a JRE.

---

### Post by the.dark.lord on 2007-03-02
Hey, I got it working now. :) :) :). You've been great people, thanks for the help.

---

