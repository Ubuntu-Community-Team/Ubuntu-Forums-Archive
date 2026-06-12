---
title: "[Java] Completely clueless"
date: 2008-03-17
forum: Programming Talk
---

### Post by zephyrus17 on 2008-03-17
I've been looking at it for 2 hours and I think it's something to do with the the braces. Because the code works by itself as it's own Java thingy.
Here's the portion of my code that's giving me the problems:
```
{		
drivetrain=ShowMessageDialog(null, "Drivetrain?",  "Forza Calculator 1.3", 1);
	button = new JButton("AWD");
    button.addActionListener(new MyAction());
    JPanel panel = new JPanel();
    panel.add(button);
    button = new JButton("FWD");
    button.addActionListener(new MyAction());
    panel.add(button);
    button = new JButton("RWD");
    button.addActionListener(new MyAction());
    panel.add(button);
    frame.add(panel);
    frame.setSize(350, 100);
    frame.setVisible(true);
    frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
}

{
String str = ae.getActionCommand();
      if(str.equals("AWD"))
	System.out.println("Front Accel 50%; Decel 0%. Rear Accel 75%; Decel 25%");
      else if(str.equals("FWD"))
        System.out.println("Accel 65%; Decel 15%");
      else if(str.equals("RWD"))
        System.out.println("Accel 75%; Decel 25%");	
}
```
And my error messages:
```
ForzaTune.java:33: cannot find symbol
symbol  : method ShowMessageDialog(<nulltype>,java.lang.String,java.lang.String,int)
location: class ForzaTune
                drivetrain=ShowMessageDialog(null, "Drivetrain?",  "Forza Calculator 1.3", 1);
                           ^
ForzaTune.java:35: cannot find symbol
symbol  : variable button
location: class ForzaTune
        button = new JButton("AWD");
        ^
ForzaTune.java:35: cannot find symbol
symbol  : class JButton
location: class ForzaTune
        button = new JButton("AWD");
                     ^
ForzaTune.java:36: cannot find symbol
symbol  : class MyAction
location: class ForzaTune
    button.addActionListener(new MyAction());
                                 ^
ForzaTune.java:36: cannot find symbol
symbol  : variable button
location: class ForzaTune
    button.addActionListener(new MyAction());
    ^
ForzaTune.java:37: cannot find symbol
symbol  : class JPanel
location: class ForzaTune
    JPanel panel = new JPanel();
    ^
ForzaTune.java:37: cannot find symbol
symbol  : class JPanel
location: class ForzaTune
    JPanel panel = new JPanel();
                       ^
ForzaTune.java:38: cannot find symbol
symbol  : variable button
location: class ForzaTune
    panel.add(button);
              ^
ForzaTune.java:39: cannot find symbol
symbol  : variable button
location: class ForzaTune
    button = new JButton("FWD");
    ^
ForzaTune.java:39: cannot find symbol
symbol  : class JButton
location: class ForzaTune
    button = new JButton("FWD");
                 ^
ForzaTune.java:40: cannot find symbol
symbol  : class MyAction
location: class ForzaTune
    button.addActionListener(new MyAction());
                                 ^
ForzaTune.java:40: cannot find symbol
symbol  : variable button
location: class ForzaTune
    button.addActionListener(new MyAction());
    ^
ForzaTune.java:41: cannot find symbol
symbol  : variable button
location: class ForzaTune
    panel.add(button);
              ^
ForzaTune.java:42: cannot find symbol
symbol  : variable button
location: class ForzaTune
    button = new JButton("RWD");
    ^
ForzaTune.java:42: cannot find symbol
symbol  : class JButton
location: class ForzaTune
    button = new JButton("RWD");
                 ^
ForzaTune.java:43: cannot find symbol
symbol  : class MyAction
location: class ForzaTune
    button.addActionListener(new MyAction());
                                 ^
ForzaTune.java:43: cannot find symbol
symbol  : variable button
location: class ForzaTune
    button.addActionListener(new MyAction());
    ^
ForzaTune.java:44: cannot find symbol
symbol  : variable button
location: class ForzaTune
    panel.add(button);
              ^
ForzaTune.java:45: cannot find symbol
symbol  : variable frame
location: class ForzaTune
    frame.add(panel);
    ^
ForzaTune.java:46: cannot find symbol
symbol  : variable frame
location: class ForzaTune
    frame.setSize(350, 100);
    ^
ForzaTune.java:47: cannot find symbol
symbol  : variable frame
location: class ForzaTune
    frame.setVisible(true);
    ^
ForzaTune.java:48: cannot find symbol
symbol  : variable JFrame
location: class ForzaTune
    frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
                                   ^
ForzaTune.java:48: cannot find symbol
symbol  : variable frame
location: class ForzaTune
    frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    ^
ForzaTune.java:52: cannot find symbol
symbol  : variable ae
location: class ForzaTune
String str = ae.getActionCommand();
             ^
24 errors

```
If you still can't find any problems with that, here's the WHOLE thing for those of you who like to burden yourselves. But without the extra code, it works fine:
```
import javax.swing.JOptionPane;
import java.awt.event.*;
import java.awt.*;

public class ForzaTune
{
	public static void main(String[] args)
	{

//This script takes the weight and front bias data of the car and outputs the various spring rates
       
        	double frontSpring;
        	double rearSpring;
        	double frontBump;
        	double rearBump;
        	double frontRebound;
        	double rearRebound;    	
		String inputWeight;
        	String inputBias;
		String inputHorsepower;
		String drivetrain;

    	//Collects horsepower, weight, weight bias and drivetrain data of car
		inputHorsepower=JOptionPane.showInputDialog(null, "Horsepower?",  "Forza Calculator 1.2.2", 1);
		double horsepower=Double.parseDouble(inputHorsepower);        	
		
		inputWeight=JOptionPane.showInputDialog(null, "Weight of car?",  "Forza Calculator 1.2.2", 1);
        	double weight=Double.parseDouble(inputWeight);

        	inputBias=JOptionPane.showInputDialog(null, "Weight front?",  "Forza Calculator 1.2.2", 1);
        	double bias=Double.parseDouble(inputBias);


{		
drivetrain=ShowMessageDialog(null, "Drivetrain?",  "Forza Calculator 1.3", 1);
	button = new JButton("AWD");
    button.addActionListener(new MyAction());
    JPanel panel = new JPanel();
    panel.add(button);
    button = new JButton("FWD");
    button.addActionListener(new MyAction());
    panel.add(button);
    button = new JButton("RWD");
    button.addActionListener(new MyAction());
    panel.add(button);
    frame.add(panel);
    frame.setSize(350, 100);
    frame.setVisible(true);
    frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
}

{
String str = ae.getActionCommand();
      if(str.equals("AWD"))
	System.out.println("Front Accel 50%; Decel 0%. Rear Accel 75%; Decel 25%");
      else if(str.equals("FWD"))
        System.out.println("Accel 65%; Decel 15%");
      else if(str.equals("RWD"))
        System.out.println("Accel 75%; Decel 25%");	
}


//First, some housekeeping
		System.out.println();		
		System.out.println("________________________________________________________________________________");
		System.out.println("Forza Tuning Calculator 1.2.2");		
		System.out.println("________________________________________________________________________________");	
        
		System.out.print("	Weight:                  ");
		System.out.print(weight);
		System.out.println("lbs");		
		System.out.print("	");        	
		System.out.println("Weight front:            "+bias+"%");
		System.out.println("        Power to weight:         "+horsepower/weight+"hp/lbs");
		System.out.println(); 
		
	//Calculations for suspension
		//Front Spring
		frontSpring=weight*bias/100*0.3828;
		System.out.print("	");
		System.out.print("Front Spring:            ");
		System.out.println(frontSpring);
		
		//Rear Spring
		rearSpring=weight*(100-bias)/100*.3828;
		System.out.print("	");		
		System.out.print("Rear Spring:             ");
		System.out.println(rearSpring);
		
		//Front Bump Damping
		frontBump=frontSpring*0.00734;
		System.out.print("	");
		System.out.print("Front Bump Damping:      ");
		System.out.println(frontBump);
			
		//Rear Bump Damping
		rearBump=rearSpring*0.00718;
		System.out.print("	");
		System.out.print("Rear Bump Damping:       ");		
		System.out.println(rearBump);

		//Front Rebound Damping
		frontRebound=frontBump*1.97;
		System.out.print("	");
		System.out.print("Front Rebound Damping:   ");
		System.out.println(frontRebound);

		//Rear Rebound Damping
		rearRebound=rearBump*2;
		System.out.print("	");
		System.out.print("Rear Rebound Damping:    ");
		System.out.println(rearRebound);
		System.out.println();
	
	//General differential guidelines for various drivetrains
		System.out.print("	");
		System.out.println("RWD: Accel 75%; Decel 25%");
		System.out.print("	");
		System.out.println("FWD: Accel 65%; Decel 15%");
		System.out.print("	");
		System.out.println("AWD: Front Accel 50%; Decel 0%. Rear Accel 75%; Decel 25%");
		
	//More housekeping
		System.out.println("________________________________________________________________________________");
		System.out.println("Copyright 2008 Gary Cai");		
		System.out.println("________________________________________________________________________________");
		System.out.println();
		System.out.println();
		System.exit(0);
	}
}
```

Thanks in advance.

---

### Post by jespdj on 2008-03-17
The error messages should give you a clue to what's wrong.

First of all, you do not have a method named 'ShowMessageDialog' in your class, so the compiler ofcourse complains that it can't find this method. Did you mean JOptionPane.showMessageDialog(...)?

Second, you have not declared a variable called 'button' anywhere, so the compiler complains that it doesn't know what 'button' is.

You did not import classes JButton and JPanel, so the compiler complains about it (these are in the package javax.swing).

You are using a class named 'MyAction' but there is no class 'MyAction'.

---

