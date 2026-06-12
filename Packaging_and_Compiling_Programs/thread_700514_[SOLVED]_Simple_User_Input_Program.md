---
title: "[SOLVED] Simple User Input Program"
date: 2008-02-18
forum: Packaging and Compiling Programs
---

### Post by stooshbunutu on 2008-02-18
Hello,

I want to make a simple program to run a piece command in terminal with with user input variables, such as file name and path. A simple window to open with two input boxes, a tick box, and a run button would be the kind of thing I want to achieve.

I don't know how easily this can be done but anyone who could point me in the right direction would be very useful.

Thanks for any help given :)

---

### Post by MobiusNZ on 2008-02-18
Do you know any programming languages?

---

### Post by stooshbunutu on 2008-02-18
I've dipped into python from time to time and will soon be learning JAVA

Something simple would be best please

Thanks

---

### Post by MobiusNZ on 2008-02-18
I *think* some scripting languages such a python have a way for showing dialog windows, but you may find the most straight-forward way would be to learn c++ and do it with gtk. It would be a good little project to learn the language.

The problem with this sort of question is it sort of lends itself to basically asking us to code it for you (or tell you how to code, which is really the same thing). Coding something isn't for the faint hearted - do a bit of googling and see if you can find a language and/or framework that would let you do what you want and give it a shot. When you have more specific problems, that is the best time to ask.

Hope that helps

---

### Post by .nedberg on 2008-02-18
You could look into zenity...

Very easy to use from terminal

---

### Post by stooshbunutu on 2008-02-18
To help give a better idea of what I am trying to achieve I made a webpage using javascript inputs as the variables. I want to create this but run the command in terminal rather than just displaying it to copy into terminal. (It will just need to be saved as a .html document to display)

Thanks again:)

---

### Post by brennydoogles on 2008-02-20
> **stooshbunutu said:**
> To help give a better idea of what I am trying to achieve I made a webpage using javascript inputs as the variables. I want to create this but run the command in terminal rather than just displaying it to copy into terminal. (It will just need to be saved as a .html document to display)

Thanks again:)

This would be easy to do in Java. Using the JOptionPane, you can create simple dialog and input boxes, without having to design a whole GUI. [HERE]("http://java.sun.com/docs/books/tutorial/uiswing/components/dialog.html") is a quick tutorial to help you with that, and here is a sample code I wrote for a class to give you an idea of how it is used:
```

import javax.swing.JOptionPane;  // Needed to create Dialog Boxes 
/**
 * -----------------------------------------------------------------------
 * File name:MilesPerGallon2.java
 * Project name: #9, page 109
 * -----------------------------------------------------------------------
 * Creator&#8217; name and email:	Brendon Dugan <wishingforayer@gmail.com					
 * Course-Section:	CSCI 1250-001
 *	Creation Date:		1/30/2008	
 * Date of Last Modification:	1/30/2008	
 * -----------------------------------------------------------------------
 */

// This Program is to determine the MPG of a car
public class MilesPerGallon2
{
	public static void main(String[] args)
	{
		
		int milesDrvn; // Define Miles Driven
		int gasUsed;  //  Define Gas Used
		int mpg;     //   Define Miles Per Gallon
		String name;//    Define name
		String str;//     Define str
		// Get the User's Name
		name = JOptionPane.showInputDialog("Please enter your name.");
		// A greeting
		JOptionPane.showMessageDialog(null,"Hello " + name + ", this program will help you find MPG of gas for your car.");
		//Ask user for Miles Driven (milesDrvn)
		str = JOptionPane.showInputDialog("Please enter how many miles you drove.");
		milesDrvn = Integer.parseInt(str);
		// Print out miles driven
		JOptionPane.showMessageDialog(null,"You drove " + milesDrvn + " miles.");
		// Ask user for the amount of Gas used (gasUsed)
		str = JOptionPane.showInputDialog("Please enter how many gallons of gas you used.");
		gasUsed = Integer.parseInt(str);
		JOptionPane.showMessageDialog(null,"You used " + gasUsed + " gallons of gas.");
		// Calculate MPG with formula mpg = milesDrvn / gasUsed
		mpg = milesDrvn / gasUsed;
		JOptionPane.showMessageDialog(null,"You averaged " + mpg + " miles per gallon on this trip, " + name + ".");
		System.exit(0);
	} // end main
}  // end MilesPerGallon
```

Hope that helps!!

---

### Post by stooshbunutu on 2008-02-21
I'm going to learn java and give that ago.

Cheerz all

---

