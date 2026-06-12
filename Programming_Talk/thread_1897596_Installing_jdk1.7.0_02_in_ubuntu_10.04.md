---
title: "Installing jdk1.7.0_02 in ubuntu 10.04"
date: 2011-12-19
forum: Programming Talk
---

### Post by Sahasrahla on 2011-12-19
I've downloaded the tar.gz from the oracle site and unpacked it. I've attempted to use javac both with and without specifying the path to where I unpacked the tar.gz and I have no luck. The best I've gotten is a response in terminal telling me to sudo apt-get install a jdk 6 which failed due to some of the sources having a 404. 

[http://docs.oracle.com/javase/7/docs/webnotes/install/linux/linux-jdk.html](http://docs.oracle.com/javase/7/docs/webnotes/install/linux/linux-jdk.html)

These are the instructions from the website and I've been looking at other instructions that state how to install from a tarball. It seems as though I need the name of a specific file to invoke with make install but I can't for the life of me figure out what I need to do at this point. I would appreciate some help if anyone would be so kind.

---

### Post by Sahasrahla on 2011-12-20
Well, I was able to install the gcj4 package in terminal so that I could follow the java tutorials for a certain distance. I'm not exactly sure what the issue is when dealing with this array example. The program compiles but when I try to start it I get errors and such.

Exception in thread "main" java.lang.NoClassDefFoundError: array
   at gnu.java.lang.MainThread.run(libgcj.so.10)
Caused by: java.lang.ClassNotFoundException: array not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.10)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.10)
   at java.lang.ClassLoader.loadClass(libgcj.so.10)
   at java.lang.ClassLoader.loadClass(libgcj.so.10)
   at gnu.java.lang.MainThread.run(libgcj.so.10)

This is what I get when I try to run it. Is it because I have an outdated java compiler/runtime environment? If so, would anybody be able to help me figure out what exactly I need to do in order to update this. I tried going through the ubuntu software center in order to get the openjdk6 package but it reported that I need to check my internet connection because it couldn't get all of the files needed but I know that my connection isn't the issue.

I don't know if this will be of any help but here is the code I compiled.

class ArrayDemo {
	public static void main(String[] args) {
		// declares an array of integers
		int[] anArray;
		// allocates memory for 10 integers
		anArray = new int[5];

		// initialize first element
		anArray[0] = 100;
		// initialize second element
		anArray[1] = 200;
		// etc.
		anArray[2] = 300;
		anArray[3] = 400;
		anArray[4] = 500;
		anArray[5] = 600;
	System.out.println("Element at index 0: "
				+ anArray[0]);
	System.out.println("Element at index 1: "
				+ anArray[1]);
	System.out.println("Element at index 2: "
				+ anArray[2]);
	System.out.println("Element at index 3: "
				+ anArray[3]);
	System.out.println("Element at index 4: "
				+ anArray[4]);
	System.out.println("Element at index 5: "
				+ anArray[5]);
	}
}

Any help would be greatly appreciated.

---

### Post by Sahasrahla on 2011-12-20
I figured out what my issues were. I was opening ArrayDemo.class by trying to enter java array because that's what I named my .java file. I assumed that's what the .class file would be named. I was also having the issue of not including 0 as a part of my array amount. I had 6 variables with only 5 slots.

---

### Post by Sahasrahla on 2011-12-22
If I could get any help with my original problem of installing the jdk se 7 I would greatly appreciate it. There's features that I would like to use that are currently unavailable to me. Namely, I can't use string data types inside of switch statements.

---

### Post by ratcheer on 2011-12-22
These instructions worked for me in Oneiric:

[http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)

Tim

---

### Post by Sahasrahla on 2011-12-29
Thank you sir, that got it working for me.

---

### Post by ratcheer on 2011-12-29
You are welcome.

Tim

---

