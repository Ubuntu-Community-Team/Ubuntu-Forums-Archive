---
title: "javac errors:cannot resolve symbol"
date: 2006-07-18
forum: Programming Talk
---

### Post by mabuti on 2006-07-18
HI! 
I have just started learning Java recently. I installed the compiler(Java) via Synaptic package manager and everything went well I think. How weirdly, the first code below gives me errors when I compile and no ERRORs on the second code. What could be the problem, please help.

Testing.java:5: cannot resolve symbol
symbol  : class Scanner
location: class Testing
        Scanner scan = new Scanner(System.in);
        ^
Testing.java:5: cannot resolve symbol
symbol  : class Scanner
location: class Testing
        Scanner scan = new Scanner(System.in);
                           ^
2 errors




import java.util.*;

public class Testing{



	public static void main(String[] args){

	Scanner scan = new Scanner(System.in);

	String str;

	str = scan.next();

	System.out.println(str);

	

	

	}







}




public class Escape_charactor{


	
	public static void main(String[] args){
	String var = "World_wide_web";
	System.out.print("again and again\n");
	var += " is good";
	var += " is good";
	var += " is good";
	var += " is good";
	var += " is good";
	System.out.println(var);
	}


	





}

---

### Post by ape on 2006-07-18
Almost sounds like you aren't using a 1.5x version of Java.  What version number do you get back when you issue the command
'javac -version'?

The java.util.Scanner class was not available in any version of Java lower than 1.5x.

---

### Post by mabuti on 2006-07-18
xine@ubuntu:~$ java -version
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)


oh, so I need to install java 1.5. How to do install?

---

### Post by ape on 2006-07-19
The package sun-java5-jdk is available in the Dapper multiverse repository.  Just add multiverse to your /etc/apt/sources.list like this:

  deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

After editing sources.list, issue the following commands:

  'apt-get update'
  'apt-get install sun-java5-jdk'

You should now have a jdk 1.5_06 install on your box.

---

