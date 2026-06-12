---
title: "[SOLVED] JCreator in ubuntu"
date: 2008-08-26
forum: Programming Talk
---

### Post by Eremis on 2008-08-26
Hi, I am trying to run JCreator through wine in Ubuntu, (I know you can use eclipse, etc...) but after i installed JCreator, and made the program this is what i get: 

Please reply, thanks 

// My program

import java.util.Scanner;
import java.io.File;
import java.io.PrintWriter;

public class Prog2_5
{
	public static void main (String[] args) throws Exception
	{
		double num1;
		double kilometers;
			
		Scanner keyB= new Scanner (System.in);
		
		System.out.print("\nPlease enter the number of miles:");
		num1 = keyB.nextDouble ();
		kilometers = (num1 * 1.60935);
		System.out.print("\nThe number of kilometers: " + kilometers);
		
		PrintWriter outProg2_5 = new PrintWriter(new File("outProg2_5.txt"));
 		outProg2_5.println("Andrey ******"); 
 		outProg2_5.println("Purpose: Write an application that converts miles into kilometers");
 		outProg2_5.println("\nmiles = " + num1 + " \nkilometers= " + kilometers); 
 			
 		outProg2_5.close();
	}
}


// This is what i get after i compile:

--------------------Configuration: Chapter 2 - <Default> - <Default>--------------------
Error : Invalid path, \bin\javac.exe -classpath "Z:\home\andriy\Documents\My JAVA\Chapter 2" -d Z:\home\andriy\Documents\My" JAVA\Chapter "2 Z:\home\andriy\Documents\My" JAVA\Chapter 2\Prog2_5.java 

Process completed.




 Someone please help!  :confused:

---

### Post by thomasaaron on 2008-08-26
Wine uses its own ...sort of... virtual filesystem. It is probably confusing java.exe.

To do cross-platform stuff with Java, it's probably best to use either a dual-boot or virtualized windows setup.

VirtulBox works quite well and doesn't break down with every kernel upgrade like vmware does.

---

### Post by DaymItzJack on 2008-08-26
> **thomasaaron said:**
> 
VirtulBox works quite well and doesn't break down with every kernel upgrade like vmware does.

Does my system suck or did you just mixup VirtualBox and vmware because my VirtualBox has to be reinstalled after every kernal upgrade.

---

### Post by Eremis on 2008-08-26
Thanks, actually i found this program "Geany" i like it even better (because i have used eclipse, and i hated it)

---

### Post by Sorivenul on 2008-08-27
Geany is great if you don't want a whole lot of hand-holding while you work.  NetBeans is a good piece of software as well.  The nice thing about Geany is the number of languages it recognizes.  If you're just looking for syntax highlighting, FTE is also a fine piece of work and is available in the repos.

---

