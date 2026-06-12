---
title: "Java programing class help"
date: 2009-01-14
forum: Programming Talk
---

### Post by Epeeman on 2009-01-14
I'm taking a JAVA programing class and we have a .bat file (prompt.bat) that is supposed to open our programs for compilation (I think) I wanted to know if it could be changed to run on Ubuntu because it's gonna be hard to be in the comp labs enough to get these assignments done. Here's the file (promt.bat):

> 
set path=C:\Program Files\Java\jdk1.6.0_02\bin;C:\WINDOWS\System32;C:\Program Files\Java\jdk1.6.0_03\bin;C:\Program Files\Java\jdk1.5.0_15\bin;C:\Program Files\Java\jdk1.6.0_10\bin;

set classpath=C:\Documents and Settings\ecslogon\Desktop;.;

dir *.java

cmd


Also I'm having trouble getting JAVA SE 6 update 11 JDK to install dose anyone have the command prompt line I should be using?

Thanks,
~~Eman

---

### Post by Geekkit on 2009-01-14
> **Epeeman said:**
> I'm taking a JAVA programing class and we have a .bat file (prompt.bat) that is supposed to open our programs for compilation (I think) I wanted to know if it could be changed to run on Ubuntu because it's gonna be hard to be in the comp labs enough to get these assignments done. Here's the file (promt.bat):



Also I'm having trouble getting JAVA SE 6 update 11 JDK to install dose anyone have the command prompt line I should be using?

Thanks,
~~Eman

That batch file is very Windows specific and is only meant to set up the environment for Windows (you don't need this since you're using Ubuntu/Linux and also assuming you've set up Sun's Java 6 via the repositories which is the best choice IMO), you don't need to use this since Ubuntu sets up the path and classpath for you already (feel free to gloat at your Windows neighbors).

Also, if you want to just use a basic IDE, use Geany (get it from the repositories). If you want a full blown IDE, take a look at both Netbeans and Eclipse. Geany might be a good place to start.

Assuming you're not using packages, you can just change directory (cd) to the directory that contains your java source code files and type: javac *.java and that will attempt to compile all of your Java source code files.

Happy coding!

---

### Post by leg on 2009-01-14
I would advise looking into Geany for simple Java programming. You can install it from the repos in Ubuntu and you can also get a Windows version. This means you can use the same editor across platforms.

---

### Post by jespdj on 2009-01-14
To install the Sun Java 6 JDK:
```
sudo apt-get install sun-java6-jdk
```

---

### Post by drubin on 2009-01-14
> **Epeeman said:**
> Also I'm having trouble getting JAVA SE 6 update 11 JDK to install dose anyone have the command prompt line I should be using?

Thanks,
~~Eman

The prefered method for installing stuff on Linux/ubuntu is with the Package management system  see this [link]("https://help.ubuntu.com/community/InstallingSoftware")

> **leg said:**
> I would advise looking into Geany for simple Java programming. You can install it from the repos in Ubuntu and you can also get a Windows version. This means you can use the same editor across platforms.

How is this productive to learning how to actually compile Java applications. The OP is ***learning*** java as part of a Course telling them to just use an pre-build GUI application will more then likely not help them in an exam when asked to describe the proccess of running/compiling an Java application.

@Epeeman Stick with the CLI way still you have that down and sorted then move onto the more lazy ways to programming. Good luck

---

### Post by Epeeman on 2009-01-14
Ah, you guys are great! but i guess i'm still confused on how to get stuff going in ubuntu. so i program in text editor, then save to the desktop as programX.java then do what to compile it? at which point it will be programX.class right? and will that save to the desktop as well? 
~~Eman

---

### Post by dwhitney67 on 2009-01-14
> **Epeeman said:**
> Ah, you guys are great! but i guess i'm still confused on how to get stuff going in ubuntu. so i program in text editor, then save to the desktop as programX.java then do what to compile it? at which point it will be programX.class right? and will that save to the desktop as well? 
~~Eman
Familiarize yourself with *nix commands and the gnome-terminal (or an xterm).  That is the only way to learn the nuts-n-bolts of *nix.  This is also the preferred way to learn how to compile and run your Java application as you learn to program.

The text editor (gedit) is a fine editor; you can also consider vim.  When you feel that you have reached a level of proficiency with either, then you can move on to the "eye-candy" editors that many new-school programmers tend to use.  I'm old-school, so I detest IDEs.

Anyhow, once you launch a gnome-terminal, run the following commands:
```

1.  gedit MyProgram.java &
   (after writing program and saving, continue with step 2)

2.  javac MyProgram.java

3.  java MyProgram

```
Of course for more complicated programs, the steps will be different.  For example, you may need to provide a CLASSPATH.

---

### Post by jespdj on 2009-01-14
Have a look at [Sun's Java Tutorials](http://java.sun.com/docs/books/tutorial/), specifically the [Hello World tutorial](http://java.sun.com/docs/books/tutorial/getStarted/cupojava/unix.html).

It explains step by step how to create, compile and run your first Java program.

On Ubuntu, gedit is the default text editor, and it has syntax highlighting for Java.

---

### Post by leg on 2009-01-14
> **drubin said:**
> ...
How is this productive to learning how to actually compile Java applications. The OP is ***learning*** java as part of a Course telling them to just use an pre-build GUI application will more then likely not help them in an exam when asked to describe the proccess of running/compiling an Java application.
...Well on Windows it is not that straight forward as you have to set up the path in one of the menus so a bit of understanding of them is required to work it. I do take your point however and using the CLI for compiling is certainly a very good option.

---

### Post by Epeeman on 2009-01-14
And the Gnome terminal is Applications -> Accessories -> Terminal ?

---

### Post by jespdj on 2009-01-14
> **Epeeman said:**
> And the Gnome terminal is Applications -> Accessories -> Terminal ?
Yes.

---

### Post by dwhitney67 on 2009-01-14
> **Epeeman said:**
> And the Gnome terminal is Applications -> Accessories -> Terminal ?

Yes.

---

### Post by Epeeman on 2009-01-15
Ok, this is the (VERY in progress) program I'm working on. 

> 
// File name: Lab2Winter09.java
// MY NAME
// Lab Section 06

import java.io.*;
import java.util.Scanner;
import javax.swing.JOptionPane;
import java.text.DecimalFormat; 

public class Lab2Winter09
{
   public static void main (String [] args)
   {
      DecimalFormat formatter = new DecimalFormat("$#,##0.00");
      Scanner input = new Scanner(System.in);
      **//Variable declaration**
      [i]System.out.println ("Please input the car's BASE COST" );
      **integerBasecost = input.nextInt ();**
      System.out.println ("Please input the TOTAL COST OF ALL OPTIONS" );
      **integerOptioncost = input.nextInt ();**
      System.out.println ("Please input the total SHIPPING AND HANDLING COSTS" );
      **integerSnhcost = input.nextInt ();**[/i]
      //Perform Calculations
      // for this read the calculations information given in the assignment
      //JOptionPane Output Message
      // for this read the output information given in the assignment
   } //End of main method
} //End of class

Where it says **//Variable declaration** (Instructions to myself of what needs to go there, not part of the program) what do I put there? aren't these the variables?: 
> integerBasecost = input.nextInt ();
      integerOptioncost = input.nextInt ();
      integerSnhcost = input.nextInt ();
so do I declare them before this section?:
> integerBasecost = input.nextInt ();
      System.out.println ("Please input the TOTAL COST OF ALL OPTIONS" );
      integerOptioncost = input.nextInt ();
      System.out.println ("Please input the total SHIPPING AND HANDLING COSTS" );
      integerSnhcost = input.nextInt ();
Or is that section the declaration of the variables?

Also this:
> integerBasecost = input.nextInt ();
will promt the user to enter an integer, correct?


Sorry, I know that's a LOT of questions, but thanks!
~~Eman

---

### Post by dwhitney67 on 2009-01-15
You have not declared the following variables:
```

integerBasecost = input.nextInt ();
integerOptioncost = input.nextInt ();
integerSnhcost = input.nextInt ();

```

To declare an integer, one use the 'int' keyword.  Consider these examples:
```

int variableName;

```
or
```

int variableName = ...;

```

IMO, it is very un-Java-like to to specify the variable type in the variable name.  So for your variables, the following would be more common to see:
```

int basecost = input.nextInt ();
int optioncost = input.nextInt ();
int snhcost = input.nextInt (); 

```

---

### Post by drubin on 2009-01-15
> **dwhitney67 said:**
> 
imo, it is very un-java-like to to specify the variable type in the variable name.  So for your variables, the following would be more common to see:

+1

---

### Post by Kilon on 2009-01-15
I advice getting a book to make your life alot easier.

---

### Post by Epeeman on 2009-01-15
Thakns SO much dwhitney67, and yeah, I'm working on getting the book but it's expensive and I'm broke lol

---

### Post by Temposs on 2009-01-15
Epeeman, there is a very good FREE book on Java by Bruce Eckel. It was used in one of my CS courses some years ago. I suspect it will serve your needs.

Here's where to download it: [http://www.mindviewinc.com/Books/](http://www.mindviewinc.com/Books/)

Here's a direct link to the book files: [http://www.mindviewinc.com/downloads/TIJ-3rd-edition4.0.zip](http://www.mindviewinc.com/downloads/TIJ-3rd-edition4.0.zip)

---

### Post by Kilon on 2009-01-15
> **Epeeman said:**
> Thakns SO much dwhitney67, and yeah, I'm working on getting the book but it's expensive and I'm broke lol

then try this , you will find loads of free books. 

[http://www.scribd.com/](http://www.scribd.com/)

---

### Post by Epeeman on 2009-01-20
Ok, I've finally got this whole thing hammered out, I think. but now that it's time to compile when I type javac Lab2Winter09.java it says file not found. What directory is it looking in and how do I change that to the desktop?

BTW the up-to-date code (just for shits 'n giggles):
```

// File name: Lab2Winter09.java
// MY NAME
// Lab Section 06

import java.io.*;
import java.util.Scanner;
import javax.swing.JOptionPane;
import java.text.DecimalFormat; 

/**
This program is designed for a car dealership to calculate the cost of a car to be purchased
*/
public class Lab2Winter09
{
   /**
   This program is used to calculate the cost of a new car + options + transit costs + tax and dealsership profit
   */
   public static void main (String [] args)
   {
      //Declare Variables
      DecimalFormat formatter = new DecimalFormat("$#,##0.00");
      double baseCost = 0.0;   //Base cost of the car purchased
      double optionsCost = 0.0; //Cost of the desired options
      double snhCost = 0.0;    //Cost of Shipping and handling
      double totalCost = 0.0;   //Total Cost of the car

      //Declare constants
      final double taxRate = .0725;    //Tax rate (7.25%)
      final double profitRate = .1;   //Profit margin (10%)

      //Declare input value
      Scanner input = new Scanner(System.in);

      //Gather user input
      System.out.println ("Please input the car's base cost. (Between $20,000.00 and $30,000.00) ");
      baseCost = input.nextDouble ();
      System.out.println ("Please input the total cost of all options (Between $0.00 and $6,000.00) ");
      optionsCost = input.nextDouble ();
      System.out.println ("Please input the total shipping and handling costs (Between $0.00 and $300.00) ");
      snhCost = input.nextDouble ();

      //Run calculations
      totalCost = (baseCost + optionsCost + snhCost) * taxRate * profitRate;

      //Output resluts
      String outputMsg = "The cost of the car you chose\n" + "plus options, taxes, delivery fees, etc. is " + dollar.format(totalCost);
      JOptionPane.showMessageDialog(null, outputMsg);
   } //End of main method
} //End of class

```

Also, if your more experienced eyes see any glaring errors, please don't hesitate to point them out to me! :P

---

### Post by kavon89 on 2009-01-21
Just a formatting note:
```

baseCost = input.nextDouble ();

public static void main (String [] args)

```
Most people don't put that many spaces when dealing with their parentheses for methods and brackets with arrays:
```

baseCost = input.nextDouble();

public static void main(String[] args)

```

I'm not a fan of the curly brace style you have but that is a topic of strong debate and flaming about which is better.

Good commenting other than this:
```
//Output resluts
```

Wildcard imports are discouraged, and I'm not even sure if you used anything in java.io.

---

### Post by Kilon on 2009-01-21
> **Epeeman said:**
> Ok, I've finally got this whole thing hammered out, I think. but now that it's time to compile when I type javac Lab2Winter09.java it says file not found. What directory is it looking in and how do I change that to the desktop? 

Why don't you use an IDE like ECLIPSE ? It will make your life much easier.

---

### Post by bruce89 on 2009-01-21
> **kavon89 said:**
> Wildcard imports are discouraged, and I'm not even sure if you used anything in java.io.

Indeed, Eclipse found it to be unused. Also, 

```
DecimalFormat formatter = new DecimalFormat("$#,##0.00");
```

had to be changed to

```
DecimalFormat dollar = new DecimalFormat("$#,##0.00");
```

> **kavon89 said:**
> Just a formatting note:
I'm not a fan of the curly brace style you have but that is a topic of strong debate and flaming about which is better.


I was going to say it is unusal to find people using the correct brace style, especially in Java; but that's for another day.

---

### Post by Epeeman on 2009-01-21
> **kavon89 said:**
> Just a formatting note:
```

baseCost = input.nextDouble ();

public static void main (String [] args)

```
Most people don't put that many spaces when dealing with their parentheses for methods and brackets with arrays:
```

baseCost = input.nextDouble();

public static void main(String[] args)

```

I'm not a fan of the curly brace style you have but that is a topic of strong debate and flaming about which is better.


Well, as far as that stuff goes the extra spaces and curly brackets etc... that's the format the instructor wants, so whatever, can't do much about it.

> 
Good commenting other than this:
```
//Output resluts
```


whops! results! not reSLUTS! lol!! thanks!

> 
Wildcard imports are discouraged, and I'm not even sure if you used anything in java.io.


Meh, there was a block of imports that we were supposed to include and java.io was one of them

> **bruce89 said:**
> Indeed, Eclipse found it to be unused. Also, 

```
DecimalFormat formatter = new DecimalFormat("$#,##0.00");
```

had to be changed to

```
DecimalFormat dollar = new DecimalFormat("$#,##0.00");
```


Ah, thanks. Fixed.

> 
I was going to say it is unusal to find people using the correct brace style, especially in Java; but that's for another day.

once again, class format

I don't think the question was answered (yes, I know there are other apps that make life a LOT easier, but this is for a course I'm taking so I have to do it a certain way). Is there a way to point the compiler to my desktop to find files I've saved there?
And also, so far as the book site quibble, I don't care I managed to scrape up enough for the course text.

Good news! it compiles now! (on a Windows machine at least) but I have a logical error: when I entered Base cost: 20,000.00 Options cost: 1,000.00 Shipping/Handling cost: 200.00 and ran the calculations the cost of the car is $153.70 LOL I pity the dealership that uses MY program!! time to find me a math major lol

---

### Post by Rocket2DMn on 2009-01-21
I jailed a bunch of posts in this thread, as they are off topic, distracting, and generally degrading to this thread.  Please stay on topic, I don't want to close this thread if I don't need to since it seems that real and good work is being done in it.  Thank you.

---

### Post by Epeeman on 2009-01-21
thanks, Rocket2DMn


Now, back on topic, how do I point the compiler to my desktop?

---

### Post by Shin_Gouki2501 on 2009-01-21
by poiting to that directory to that your destop poitns?
Got the pointer?
:)

---

### Post by drubin on 2009-01-21
> **Epeeman said:**
> thanks, Rocket2DMn

Now, back on topic, how do I point the compiler to my desktop?

either ```
cd Desktop 
javac javafiles.java
``` or ```
javac Desktop/javafiles.java
```

the first one moves your current directory to your Desktop and then runs the compiler. The second one just runs the compiler on an absolute path. 

Does this answer you question?

> **Shin_Gouki2501 said:**
> by poiting to that directory to that your destop poitns?
Got the pointer?
:)

And that helps how?

---

