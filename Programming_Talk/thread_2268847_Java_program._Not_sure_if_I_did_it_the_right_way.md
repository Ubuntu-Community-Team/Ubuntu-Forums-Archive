---
title: "Java program. Not sure if I did it the right way"
date: 2015-03-11
forum: Programming Talk
---

### Post by Tristan_Williams on 2015-03-11
I'm just starting to learn Java. I already use Bash. I'm currently learning about arrays and such.
I have a book full of projects, and each project focuses on what you just learned about.

The project I have right now is to take 10 ints as input, and store them in an array.
Then, store even ints in one array, odd ones in another, and negative in another.
I got it done rather quickly, but I was wondering if maybe there's a better way

Here's the code:
```

import  java.util.Scanner;

public class Project10_1
{
    public static void main (String[] args)
    {
        Scanner scan = new Scanner (System.in);
        int[] inputArray = new int[10], evenList = new int[10], oddList = new int[10], negativeList = new int[10];
        
        int itterations = 0;
        int inputNumber = 0;
        int maxItterations = 10;
        
        System.out.println("Enter 10 integers: ");
        while (itterations < maxItterations)    //limit number of inputs
        {
            inputArray[itterations] = scan.nextInt();
            
            if (inputArray[itterations] >= 0)
            {
                if (inputArray[itterations] % 2 == 0)
                    evenList[itterations] = inputArray[itterations];
                else if (inputArray[itterations] % 2 == 1)
                    oddList[itterations] = inputArray[itterations];
                else if (inputArray[itterations] == 0)
                    evenList[itterations] = inputArray[itterations];
                else
                {
                    System.out.println("Not a valid integer!");
                    maxItterations++;
                }
                    
            }
            else if (inputArray[itterations] < 0)
                negativeList[itterations] = inputArray[itterations];
            else
            {
                System.out.println("Not a valid integer!");
                maxItterations++;
            }
            itterations++;
        }
        
        //Clear Linux terminal for better appearance
        System.out.print("\033[H\033[2J");
        
        
        //Output even numbers
        itterations = 0;
        maxItterations = 10;
        System.out.println("\nEven:");
        while (itterations < maxItterations)
        {
            if (evenList[itterations] == inputArray[itterations])
            {
                inputNumber = itterations + 1;
                System.out.print("(" + inputNumber + ") ");
                System.out.println(evenList[itterations]);
            }
            itterations++;
        }
        
        //Output odd numbers
        itterations = 0;
        System.out.println("\nOdd");
        while (itterations < maxItterations)
        {
            if (oddList[itterations] == inputArray[itterations])
                if (oddList[itterations] != 0)
                {
                    inputNumber = itterations + 1;
                    System.out.print("(" + inputNumber + ") ");
                    System.out.println(oddList[itterations]);
                }
            itterations++;
        }
        
        //Output negative numbers
        itterations = 0;
        System.out.println("\nNegative");
        while (itterations < maxItterations)
        {
            if (negativeList[itterations] < 0)
                if (negativeList[itterations] == inputArray[itterations])
                {
                    inputNumber = itterations + 1;
                    System.out.print("(" + inputNumber + ") ");
                    System.out.println(negativeList[itterations]);
                }
            itterations++;
        }
    }
}

```

---

### Post by ofnuts on 2015-03-12
[LIST]
[*]You should keep individual index/counts for the odd/even/negative arrays. Currently these arrays are full of "holes". 
[*]Check your spelling. This is more important than you think. One day you (or someone working with you) will be searching "iterations" in the code and not find your "itterations". 
[*]Loop with counters (typically on arrays) should use the for(... ;...;... )constructs instead of a while loop. 
[*]You are making your life complicated:
[LIST]
[*]instead of hard-coding the max iterations, use the length of your array (inputArray.length), or have the array sized by the maxCount variable (inputArray=new in[maxIterations]); 
[*]bump the iterations counter only if you have valid input instead of bumping the maxIterations counter 
[*]don't read directly into the array, read into a variable, and after the checks, write it to the array 
[/LIST]
  
[*]"Iterations" is a bad name for a variable. You aren't counting iterations but array items (even if you do one iteration for each) 
[*]The code will be cleaner if you do just the input first and once the array is filled, a loop to break it down 
[*]This begs for a function that prints the contents of an array, that you would call three times (odd/even/negative arrays) or may be four (input array) 
[*]Instead of putting "\n" in println() strings, use two println(). 
[/LIST]

---

### Post by Tristan_Williams on 2015-03-12
Thanks! That helped a lot

---

