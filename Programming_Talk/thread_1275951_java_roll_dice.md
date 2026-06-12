---
title: "java roll dice"
date: 2009-09-26
forum: Programming Talk
---

### Post by nathang1392 on 2009-09-26
i am making a class that simulates rolling a dice and then outputs the probability of each side being rolled. i havent gotten it to exactly work correctly, but i dont understand why. i have been working on it for a while and cant tell if i am over looking something. ```

import java.util.Scanner;
import java.util.Random;

public class DiceProbability
{
    public static void main(String [] args)
    {
        Scanner in;  
        in = new Scanner(System.in);
        
        int counterTrials = 1;
        int counter1 = 1;
        int counter2 = 1;
        int counter3 = 1;
        int counter4 = 1;
        int counter5 = 1;
        int counter6 = 1;
        int counter7 = 1;
        int counter8 = 1;
        int counter9 = 1;
        int counter10 = 1;
        int counter11 = 1;
        
        
        
        System.out.println("Number of Rolls: ");
        int numberOfRolls = in.nextInt();
        
        int randomNumber = ((int)(0+ Math.random()* 11));
        
        
        
         
        
        
        for(int side1 = 0; counterTrials <= numberOfRolls;) 
        randomNumber = ((int)(0+ Math.random()* 11));
        if (randomNumber == 1)
            {
                counter1++;
                
            }
            
            
        
            for(int side2 = 0; counterTrials <= numberOfRolls;) 
            randomNumber = ((int)(0+ Math.random()* 11));
            if (randomNumber == 2)
            {
                
                counter2++;
            }
            
            
                for(int side3 = 0; counterTrials <= numberOfRolls;)
                randomNumber = ((int)(0+ Math.random()* 11));
                if (randomNumber == 3)
                {
                    counter3++;
                    
                }
                
                
                
                
                        for(int side4= 0; counterTrials <= numberOfRolls;) 
                        randomNumber = ((int)(0+ Math.random()* 11));
                        if (randomNumber == 4)
                        {
                            counter4++;
                            
                        }
                        
                            
                        
                            for(int side5 = 0; counterTrials <= numberOfRolls;) 
                            randomNumber = ((int)(0+ Math.random()* 11));
                            if (randomNumber == 5)
                            {
                                counter5++;
                                
                            }
                            
                                
                            
                                for(int side6 = 0; counterTrials <= numberOfRolls;) 
                                randomNumber = ((int)(0+ Math.random()* 11));
                                if (randomNumber == 6)
                                {
                                    counter6++;
                                    
                                }
                               
                                
                                    
                                
                                    for(int side7 = 0; counterTrials <= numberOfRolls;) 
                                    randomNumber = ((int)(0+ Math.random()* 11));
                                    if (randomNumber == 7)
                                    {
                                        counter7++;
                                        
                                    }
                                    
                                        
                                    
                                        for(int side8= 0; counterTrials <= numberOfRolls;)
                                        randomNumber = ((int)(0+ Math.random()* 11));
                                        if (randomNumber == 8)
                                        {
                                            counter8++;
                                            
                                        }
                                        
                                            
                                        
                                            for(int side9 = 0; counterTrials <= numberOfRolls;) 
                                            randomNumber = ((int)(0+ Math.random()* 11));
                                            if (randomNumber == 9)
                                            {
                                                counter9++;
                                                
                                            }
                                            
                                                
                                            
                                                for(int side10 = 0; counterTrials <= numberOfRolls;) 
                                                randomNumber = ((int)(0+ Math.random()* 11));
                                                if (randomNumber == 10)
                                                {
                                                    counter10++;
                                                    
                                                }
                                                
                                                    
                                                
                                                    for(int side11= 0; counterTrials <= numberOfRolls;)
                                                    randomNumber = ((int)(0+ Math.random()* 11));
                                                    if (randomNumber == 11)
                                                    {
                                                        counter11++;
                                                        
                                                    }
                                                    

        
        System.out.print("Sum Of Dice              Probability");
        System.out.print("\n1s" + "                       " + (double) (counter1/numberOfRolls) * 100;) + "%");
        System.out.print("\n2s" + "                       " + (double) (counter2/numberOfRolls) * 100) + "%");
        System.out.print("\n3s" + "                       " + (double) (counter3/numberOfRolls) * 100) + "%");
        System.out.print("\n4s" + "                       " + (double) (counter4/numberOfRolls) * 100) + "%");
        System.out.print("\n5s" + "                       " + (double) (counter5/numberOfRolls) * 100) + "%");
        System.out.print("\n6s" + "                       " + (double) (counter6/numberOfRolls) * 100) + "%");
        System.out.print("\n7s" + "                       " + (double) (counter7/numberOfRolls) * 100) + "%");
        System.out.print("\n8s" + "                       " + (double) (counter8/numberOfRolls) * 100) + "%");
        System.out.print("\n9s" + "                       " + (double) (counter9/numberOfRolls) * 100) + "%");
        System.out.print("\n10s" + "                      " + (double) (counter10/numberOfRolls) * 100) + "%");
        System.out.print("\n11s" + "                      " + (double) (counter11/numberOfRolls) * 100) + "%");                             
        }
        
}
```

---

### Post by doas777 on 2009-09-26
hmmm. well, the probability of any given dice rolll is 1/n where n is the number of sides. dice rolls do not stack with repition because you start out wiht the same pool size for each roll. the only differance with physical dice, is that they are never perfectly ballenced. if the java rand lib is decent, you won;t find an analogue to that phenoma via code.

I wrote a dice roller for tabletop RPGs thats very nice. i did tweak the probabilities a bit though to make the dice "roll well"... don't tell my GM/DM!

---

### Post by falconindy on 2009-09-26
In addition to the above suggestions:

1) You're not actually using the java.util.Random library here. you're using Math.random, which is a separate class. While it's not adding any overhead to your program, why include it?
2) Consider using arrays to store your results. It's much cleaner.

This can be written comfortably in about 25-30 lines of code.

---

### Post by nathang1392 on 2009-09-26
i have been told to use arrays, but im in a class and we havent went over them yet. what i am trying to do is make a random number for each side of the dice and if the random number and the side of the dice match, that is 1 match, and repeat for each side for the amount of rolls. after that i am trying to caculate the probability of each side by dividing the number of matches by the number of rolls and multiplying times 100. in theory it should work, but its not. and im getting an error on my print statements ')' expected. very confused.

---

### Post by lisati on 2009-09-26
I haven't looked at the code in depth but it looks like you're initialising your counters to 1. Wouldn't starting off at zero be better?

---

### Post by nathang1392 on 2009-09-26
my problem with that is if  i start them at zero and then nothing is added to them i get "cant divide by zero" and im alright if they are just one off.

---

### Post by nathang1392 on 2009-09-26
i changed the probability calculations to go like ```
probability1 = counter1 / numberOfRolls * 100;
        probability2 = counter2 / numberOfRolls * 100;
        probability3 = counter3 / numberOfRolls * 100;
        probability4 = counter4 / numberOfRolls * 100;
        probability5 = counter5 / numberOfRolls * 100;
        probability6 = counter6 / numberOfRolls * 100;
        probability7 = counter7 / numberOfRolls * 100;
        probability8 = counter8 / numberOfRolls * 100;
        probability9 = counter9 / numberOfRolls * 100;
        probability10 = counter10 / numberOfRolls * 100;
        probability11 = counter11 / numberOfRolls * 100;
        
        System.out.print("Sum Of Dice              Probability");
        System.out.print("\n1s" + "                       " + probability1 + "%");
        System.out.print("\n2s" + "                       " + probability2 + "%");
        System.out.print("\n3s" + "                       " + probability3 + "%");
        System.out.print("\n4s" + "                       " + probability4 + "%");
        System.out.print("\n5s" + "                       " + probability5 + "%");
        System.out.print("\n6s" + "                       " + probability6 + "%");
        System.out.print("\n7s" + "                       " + probability7 + "%");
        System.out.print("\n8s" + "                       " + probability8 + "%");
        System.out.print("\n9s" + "                       " + probability9 + "%");
        System.out.print("\n10s" + "                      " + probability10 + "%");
        System.out.print("\n11s" + "                      " + probability11 + "%");                             
```

it still wont work though. for some reason the counters just wont take in the right values.

---

### Post by Can+~ on 2009-09-26
```
System.out.print("\n1s" + "                       " + (double) (counter1/numberOfRolls) * 100**;)** + "%");
```

open, open, close, open, close, **close**, close.

As for the syntax:

```
        for(int side1 = 0; counterTrials <= numberOfRolls;) 
        **randomNumber = ((int)(0+ Math.random()* 11));**
        if (randomNumber == 1)
            {
                counter1++;
                
            }

```

Your `for' doesn't have a {}, so it will execute the bold line only. On the other hand, if you want to execute all that chunk:

[PHP]        for(int side1 = 0; counterTrials < numberOfRolls;)
        { 
            randomNumber = ((int)(0+ Math.random()* 11));
            if (randomNumber == 1)
            {
                counter1++;
            }
        }[/PHP]

And I'm not sure why are you indenting that much. 

Now, the big thing about computing, is that you can describe a repetitive task once and tell it to repeat as much as you want, therefore, having 1 `for' for each face is... dumb.

You're better off putting everything inside a big for (1 to 12) and using an array. Something like:

[PHP]
for(int side=0; side < maxsides; side++)
{
    for(int trials=0; trials < maxtrials; trials++)
    { 
        roll = (int)(0+Math.random()*maxsides);
        if (roll == side)
        {
            counter[side]++;
        }
    }
}[/PHP]

Now, I know jack about Java, but I remember a java library for handling random integers better than the Math.random way.

---

### Post by nathang1392 on 2009-09-26
lol @ "dumb" i know my code is horrible, but its not all my fault. im taking a distance learning class in high school, and i dont really have anywhere to go except forums. anyways, the reason im using so many loops is because the lesson is on nested loops. i updated my code to what you suggested. what could cause this to happen: i run the program, it asks me how many rolls. i enter a number and it just stops.

---

### Post by doas777 on 2009-09-26
though I have no idea what your goals are, you can do a single dice roll with this algorithm (psudocode, not java):

```

roll = Round(ABS(random)) % N

```just gen a number as absolute, and modulo it via the number of sides.

Edit: ahh, gotcha. loops are an important lesson. you;ll look back on this in 6months and wonder how you could have had trouble. good luck, and have fun.

---

