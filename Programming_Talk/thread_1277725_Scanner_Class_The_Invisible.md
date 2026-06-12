---
title: "Scanner Class: The Invisible"
date: 2009-09-28
forum: Programming Talk
---

### Post by Joseph Schwenker on 2009-09-28
Hey everyone!  I have been trying to learn how to program Java in Eclipse, but am having a problem with compiling this Java program:

> import java.util.Scanner;

class EchoLine {
	
	public static void main(String args[]) {
		Scanner myScanner = new Scanner(System.in);
			
		System.out.prinln(myScanner.nextLine());
	}
}

It gives me errors on lines one and six, both errors regarding not being able to import the scanner class.  I have been getting help from Barry Burd, and from his help, I am able to see that the scanner class is not present, even though I have the latest version of Java installed and set to be used by Eclipse.  I installed it from Synaptic (sun-java6, or whatever).  If there is an alternate version of Java that I should install?  Thanks!

---

### Post by PaulM1985 on 2009-09-28
I think one of the problems with line 6 is that you have System.out.prinln rather than System.out.println.

Not sure what the problem is with the import.

Paul

---

### Post by PaulM1985 on 2009-09-28
sudo apt-get install build-essential
usually helps.  It installs various programming stuff, compilers and the like I think.

Paul

---

### Post by Reiger on 2009-09-28
Sounds like your Eclipse is using the GCJ which is well known for being simply incomplete. You can more or less program Java 1.4 if you don't mind not using Swing. Otherwise it's all pains and no gains with that java.

Fortunately you can configure Eclipse to use other Java versions, i.e. Java 1.5 or Java 1.6 from sun or openjdk respectively... Since I currently use Netbeans for my Java development (haven't touched Eclipse in quite a while) I may be a little inaccurate or outdated w.r.t. how this configuring is done but IIRC there is some kind of "Window" menu which also lists Configuration/Options among its entries and that entry will give you a dialog/frame with settings for just about everything Eclipse. (There's a search function to make life easier too.) 

Alternatively you can stick to configure build environment on a per project basis. 

In either way: your *current* project which fails to build with Scanners will continue to fail to build because it is now doomed to use GCJ as part of its configuration. I do not know whether or not you can alter that mid-project.

---

### Post by Reiger on 2009-09-28
> **PaulM1985 said:**
> sudo apt-get install build-essential
usually helps.  It installs various programming stuff, compilers and the like I think.

Paul

Not applicable since Java compilers aren't part of the dependencies of the meta-package that is build-essential. Furthermore, the OP can get Eclipse to run (impossible without some kind of JVM/JDK set up) and he can use a compiler otherwise he wouldn't have gotten those error messages. :P

---

