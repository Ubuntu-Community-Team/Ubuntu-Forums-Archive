---
title: "A simple gas calculator cost made in Java by a noobie"
date: 2009-07-29
forum: Programming Talk
---

### Post by Koobelakahn on 2009-07-29
```
 /*
 *      GasCalculator.java
 *      
 *      Copyright 2009 Steven <steven@steven-laptop>
 *      
 *      This program is free software; you can redistribute it and/or modify
 *      it under the terms of the GNU General Public License as published by
 *      the Free Software Foundation; either version 2 of the License, or
 *      (at your option) any later version.
 *      
 *      This program is distributed in the hope that it will be useful,
 *      but WITHOUT ANY WARRANTY; without even the implied warranty of
 *      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 *      GNU General Public License for more details.
 *      
 *      You should have received a copy of the GNU General Public License
 *      along with this program; if not, write to the Free Software
 *      Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
 *      MA 02110-1301, USA.
 * 
 *         If you use this code, and alter it, please credit me.
 *         If you post this code as is, please leave this paragraph, and my comments
 *         in the code
 *         If you love it, want to comment, or you just hate the world, feel 
 *         free to email me at Makkawolf20@yahoo.com or Steveninglese@gmail.com
 * 
 *         *** MY CODE IS (as far as I know) UGLY ***
 *         ***    THE CODE RUNS, AND AS FAR AS I KNOW, I DID EVERYTHING A GOOD PROGRAMMER SHOULDNT***
 *         ***IF SOMEONE COULD CLEAN UP THIS CODE,AND RESEND IT TO ME, IT'D BE APPRECIATED***
 * 
 */
// Imports scanner
import java.util.Scanner;
//seems like the name is perfect for what the program does.
public class GasCalculator {

    public static void main (String args[]) {        
        Scanner scan = new Scanner(System.in);
        //Asks how many mile the user drives
            System.out.println("How many miles do you drive a week?");
        //Initializes the variable
                int miles;
        //Scans the users input, and uses it in the equations below
                miles = scan.nextInt();
            System.out.println("So you drive " + miles +" miles. What is the price of gas");
                double gas;
                gas = scan.nextDouble();
            System.out.println("Ok, so gas costs " + gas +" a gallon. what is the MPG (freeway) on your car? Use whole numbers please");
                int mpgFreeway;
                mpgFreeway = scan.nextInt();
            System.out.println("So, you get " + mpgFreeway +" miles per gallon on the freeway");
                int mpgResidential;
            System.out.println("What is the MPG on residential streets");
                mpgResidential = scan.nextInt();
            System.out.println("ok, you get " +mpgResidential +" miles per gallon on residential streets");
            //If someone can help me so I dont have to have the user use a decimal, please email me the solution.
            System.out.println("what percent of your time driving is spent on the freeway?(please put the numberas a decimal");
            System.out.println("For example, if you drive on the freeway 50% of the time, put it as .50");
                float percentFreeway;
                percentFreeway = scan.nextFloat();
                float percentResidential;
                percentResidential = (1 - percentFreeway);
        
            System.out.println("Calculating...");
            //This is where all the math is done. this is what probably took me the longest to figure out, not due to the fact
            //I dont know what the syntax is, but because I suck at math, and I had to ask a few people to help.
                    double cost = (miles/ mpgFreeway * gas);
                    double finalCostf = ((cost * percentFreeway) * gas );
                    double cost2 = (miles/ mpgResidential * gas);
                    double finalCostR = ((cost2 * percentResidential) * gas);
            //The answer is usually an ugly decimal number. If anyone knows how to fix this, please email me.
            System.out.println("Below is your total cost");
            System.out.println("it costs " + finalCostf + " to drive for a week on the freeway, and " + finalCostR + " to drive on the regular streets.");
    }
}

```


Here you guys go. i thought id post my code. contribute back to the community, ya know:D

help is appreciated.

---

### Post by NovaAesa on 2009-07-29
Looks pretty good to me. Since you asked for a code clean up, this is how I would do it.

```

/**
 *      GasCalculator.java
 *      
 *      Copyright 2009 Steven <steven@steven-laptop>
 *      
 *      This program is free software; you can redistribute it and/or modify
 *      it under the terms of the GNU General Public License as published by
 *      the Free Software Foundation; either version 2 of the License, or
 *      (at your option) any later version.
 *      
 *      This program is distributed in the hope that it will be useful,
 *      but WITHOUT ANY WARRANTY; without even the implied warranty of
 *      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 *      GNU General Public License for more details.
 *      
 *      You should have received a copy of the GNU General Public License
 *      along with this program; if not, write to the Free Software
 *      Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
 *      MA 02110-1301, USA.
 * 
 *         If you use this code, and alter it, please credit me.
 *         If you post this code as is, please leave this paragraph, and my comments
 *         in the code
 *         If you love it, want to comment, or you just hate the world, feel 
 *         free to email me at Makkawolf20@yahoo.com or Steveninglese@gmail.com
 * 
 *         *** MY CODE IS (as far as I know) UGLY ***
 *         ***    THE CODE RUNS, AND AS FAR AS I KNOW, I DID EVERYTHING A GOOD PROGRAMMER SHOULDNT***
 *         ***IF SOMEONE COULD CLEAN UP THIS CODE,AND RESEND IT TO ME, IT'D BE APPRECIATED***
 * 
 */
import java.util.Scanner;
public class GasCalculator {

    public static void main (String args[])
    {
        Scanner scan = new Scanner(System.in);
        
        //gets miles per wk
        System.out.println("How many miles do you drive a week?");
        int miles = scan.nextInt();
        System.out.println("So you drive " + miles +" miles.");
        
        //get gas price
        System.out.println("What is the price of gas");
        double gas = scan.nextDouble();
        System.out.println("Ok, so gas costs " + gas +" a gallon.");
        
        //get MPG f/way
        System.out.println("What is the MPG (freeway) on your car? Use whole numbers please.");
        int mpgFreeway = scan.nextInt();
        System.out.println("So, you get " + mpgFreeway +" miles per gallon on the freeway.");
        
        //get MPG residential
        System.out.println("What is the MPG on residential streets");
        int mpgResidential = scan.nextInt();
        System.out.println("ok, you get " +mpgResidential +" miles per gallon on residential streets");
        
        //get type split
        System.out.println("What percent (number between 0 and 100) of your time driving is spent on the freeway?");
        System.out.println("For example, if you drive on the freeway 50% of the time, put it as 50");
        float percentFreeway = (float)scan.nextInt() / 100;
        float percentResidential = (1 - (float)percentFreeway / 100);
    
        //do calculations
        double cost = (miles / mpgFreeway * gas);
        double finalCostf = ((cost * percentFreeway) * gas );
        double cost2 = (miles/ mpgResidential * gas);
        double finalCostR = ((cost2 * percentResidential) * gas);

        //show answer
        System.out.println("Below is your total cost");
        System.out.println(String.format("it costs %6.2f to drive for a week on the freeway, and %6.2f to drive on the regular streets.", finalCostf, finalCostR));
        
    }
}

```

---

### Post by Sockerdrickan on 2009-07-29
lol the disclaimer is almost as long as the sorce code. xD

---

### Post by Koobelakahn on 2009-07-29
> **NovaAesa said:**
> Looks pretty good to me. Since you asked for a code clean up, this is how I would do it.

```

/**
 *      GasCalculator.java
 *      
 *      Copyright 2009 Steven <steven@steven-laptop>
 *      
 *      This program is free software; you can redistribute it and/or modify
 *      it under the terms of the GNU General Public License as published by
 *      the Free Software Foundation; either version 2 of the License, or
 *      (at your option) any later version.
 *      
 *      This program is distributed in the hope that it will be useful,
 *      but WITHOUT ANY WARRANTY; without even the implied warranty of
 *      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 *      GNU General Public License for more details.
 *      
 *      You should have received a copy of the GNU General Public License
 *      along with this program; if not, write to the Free Software
 *      Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
 *      MA 02110-1301, USA.
 * 
 *         If you use this code, and alter it, please credit me.
 *         If you post this code as is, please leave this paragraph, and my comments
 *         in the code
 *         If you love it, want to comment, or you just hate the world, feel 
 *         free to email me at Makkawolf20@yahoo.com or Steveninglese@gmail.com
 * 
 *         *** MY CODE IS (as far as I know) UGLY ***
 *         ***    THE CODE RUNS, AND AS FAR AS I KNOW, I DID EVERYTHING A GOOD PROGRAMMER SHOULDNT***
 *         ***IF SOMEONE COULD CLEAN UP THIS CODE,AND RESEND IT TO ME, IT'D BE APPRECIATED***
 * 
 */
import java.util.Scanner;
public class GasCalculator {

    public static void main (String args[])
    {
        Scanner scan = new Scanner(System.in);
        
        //gets miles per wk
        System.out.println("How many miles do you drive a week?");
        int miles = scan.nextInt();
        System.out.println("So you drive " + miles +" miles.");
        
        //get gas price
        System.out.println("What is the price of gas");
        double gas = scan.nextDouble();
        System.out.println("Ok, so gas costs " + gas +" a gallon.");
        
        //get MPG f/way
        System.out.println("What is the MPG (freeway) on your car? Use whole numbers please.");
        int mpgFreeway = scan.nextInt();
        System.out.println("So, you get " + mpgFreeway +" miles per gallon on the freeway.");
        
        //get MPG residential
        System.out.println("What is the MPG on residential streets");
        int mpgResidential = scan.nextInt();
        System.out.println("ok, you get " +mpgResidential +" miles per gallon on residential streets");
        
        //get type split
        System.out.println("What percent (number between 0 and 100) of your time driving is spent on the freeway?");
        System.out.println("For example, if you drive on the freeway 50% of the time, put it as 50");
        float percentFreeway = (float)scan.nextInt() / 100;
        float percentResidential = (1 - (float)percentFreeway / 100);
    
        //do calculations
        double cost = (miles / mpgFreeway * gas);
        double finalCostf = ((cost * percentFreeway) * gas );
        double cost2 = (miles/ mpgResidential * gas);
        double finalCostR = ((cost2 * percentResidential) * gas);

        //show answer
        System.out.println("Below is your total cost");
        System.out.println(String.format("it costs %6.2f to drive for a week on the freeway, and %6.2f to drive on the regular streets.", finalCostf, finalCostR));
        
    }
}

```

Thank you a bunch.
I want another simple project to work on. something at this level of java expertise. Any assignments? (im on a long vacation, and i need stuff to do)

---

### Post by NovaAesa on 2009-07-29
Maybe you could make a programme to calculate the area of a triange given 3 of its sides? It should be easy enough to find the formula somewhere on the net.

---

### Post by Koobelakahn on 2009-07-29
I was away from the internet for a while (car trip) but i wrote this little usefully useless program. its not as good as my other, but i still like it

Can someone help me with the "User must put percentage as decimal" issue?

```

/*
 *      TipCalc.java
 *      
 *      Use me, abuse me, but leave feedback, and a bit of credit to me please =D
 *         any questions, comments, or you just hate the world, email me at StevenInglese@gmail.com
 *         seriously... email me... I get lonely too O_o
 */
import java.util.Scanner;

public class TipCalc {

    public static void main (String args[]) {        
        Scanner scan = new Scanner(System.in);
            System.out.println("This program is a tip calculator");
            System.out.println("How much was the meal total (including tax)?");
            double mealCost;
            mealCost = scan.nextDouble();
            System.out.println("Ok, how good was the service? The percentage is equal to a decimal.");
                System.out.println("Excellent (.20)");
                System.out.println("Great (.18)");
                System.out.println("Good (.15)");
                System.out.println("Fair (.10)");
                System.out.println("Poor (.5)");
                System.out.println("These decimals are not the only ones to choose from. If the service was better");
                System.out.println("or worse than the #'s displayed here, just put the percentage you want to tip asa decimal");
            double tip;
            tip = scan.nextDouble();
            
            double tipTotal = (mealCost * tip);
            double totalWithtip = (mealCost * tip + mealCost);
            System.out.println("The tip would cost " +tipTotal+ " and the meals total cost would be " +totalWithtip+ ".");
            
            
    }
}

```

Notice the shorter legal ?
i have learned =D

---

### Post by NovaAesa on 2009-07-29
When you want to enter a percentage as an integer rather than a decimal, simply input the decimal, i.e. used ```
scan.nextInt()
``` but then divide that number by 100, and there you have your decimal number.

---

### Post by hyperAura on 2009-07-30
[FONT=Verdana]i think its simpler if u exclude scan for parsing the parameters from the command line.. u can just replace it [/FONT][FONT=Verdana]by declaring the variables just like this from the beginning.. u just have to know the number of the parameter which ofc u r the one making these decisions..[/FONT][FONT=Verdana][COLOR=#7f0055][B]

int [/B][/COLOR][/FONT][FONT=Verdana][COLOR=#000000]a = Integer.parseInt[/COLOR][/FONT][FONT=Verdana][COLOR=#000000]([/COLOR][/FONT][FONT=Verdana][COLOR=#000000]args[/COLOR][/FONT][FONT=Verdana][COLOR=#000000][[/COLOR][/FONT][FONT=Verdana][COLOR=#990000]0[/COLOR][/FONT][FONT=Verdana][COLOR=#000000]])[/COLOR][/FONT][FONT=Verdana][COLOR=#000000];[/COLOR][/FONT][FONT=Verdana]
[/FONT] [FONT=Verdana][COLOR=#7f0055]**int **[/COLOR][/FONT][FONT=Verdana][COLOR=#000000]b = Integer.parseInt[/COLOR][/FONT][FONT=Verdana][COLOR=#000000]([/COLOR][/FONT][FONT=Verdana][COLOR=#000000]args[/COLOR][/FONT][FONT=Verdana][COLOR=#000000][[/COLOR][/FONT][FONT=Verdana][COLOR=#990000]1[/COLOR][/FONT][FONT=Verdana][COLOR=#000000]])[/COLOR][/FONT][FONT=Verdana][COLOR=#000000];

this is just the way to use for integers.. for doubles
[/COLOR][/FONT][COLOR=#7f0055][/COLOR]
double a = Double.parseDouble(args[0]);

---

