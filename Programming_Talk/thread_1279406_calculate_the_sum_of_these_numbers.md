---
title: "calculate the sum of these numbers"
date: 2009-09-30
forum: Programming Talk
---

### Post by nathang1392 on 2009-09-30
```
import java.util.Scanner;
import java.util.Random;
import java.io.IOException;
import java.io.PrintWriter;
import java.io.File;
public class BottleCapPrize
{
    public static void main(String [] args)throws IOException 
    {
        Scanner in; 
        in = new Scanner(System.in);
       
       
        int numTrials = 10;
        int average = 0;
       
        PrintWriter outFile = new PrintWriter (new File("bottleCap.txt"));
 
      
  
      for (int i = 0; i < numTrials; i++)
  
      {
  
      int counter = 0;
  
      int randomNumber = 0;
 
      
 
      do
 
      {
 
      randomNumber = ((int)(0+ Math.random()* 5));
 
      counter++;
 
      }
 
      while (randomNumber != 1);
 
      
 
      outFile.println(counter);
 
      }
 
      
 
        outFile.close ( );
       
        
        File fileName = new File("bottleCap.txt");
        Scanner inFile = new Scanner("bottleCap.txt");
        
       
        int counter = 0;
        String data = "";
       
        while (inFile.hasNextInt())
        {
            data = inFile.next ( );
            int num = inFile.nextInt ();
            int sum = 
            average = sum/numTrials;
            
            
         }    
    
    
        
       
       inFile.close(); 
       System.out.println(average); 
       
      
                   }
     }

```

at the bottom i am trying to calculate the sum of numbers that i have brought in from a txt file. any help is appreciated.

---

### Post by Tortel on 2009-09-30
sum += num;

or eliminate a variable and just use
sum += inFile.nextInt();

---

### Post by nathang1392 on 2009-09-30
i did it, but my average is still coming out to 0, do you know what may be causing this?

---

### Post by pbrockway2 on 2009-09-30
Declare *sum* before the while loop starts.  Ie remove the "int sum = ..." line and put it before the loop.

Inside the loop update the value of *sum*.

Then after the loop has finished you are in a position to say "average = sum/numTrials;"  Ie move this line as well.

A couple of questions:  where does *numTrials* come from?  I see you make it 10 at the start.  But you also a variable called *counter* which you do nothing with.  Now if you were to also update counter inside the loop it would provide an accurate result for the number of trials whether it was 10 or not.

Secondly, do you really mean "sum/numTrials"?  This will perform integer division - that is it will throw away any "remainder".

---

### Post by pbrockway2 on 2009-09-30
> **nathang1392 said:**
> i did it, but my average is still coming out to 0, do you know what may be causing this?

My post was too slow ;(

But the answer to this is probably in my second question.

---

### Post by nathang1392 on 2009-09-30
> **pbrockway2 said:**
> Declare *sum* before the while loop starts.  Ie remove the "int sum = ..." line and put it before the loop.

Inside the loop update the value of *sum*.

Then after the loop has finished you are in a position to say "average = sum/numTrials;"  Ie move this line as well.

A couple of questions:  where does *numTrials* come from?  I see you make it 10 at the start.  But you also a variable called *counter* which you do nothing with.  Now if you were to also update counter inside the loop it would provide an accurate result for the number of trials whether it was 10 or not.

Secondly, do you really mean "sum/numTrials"?  This will perform integer division - that is it will throw away any "remainder".

```
/**The purpose of this program is to write the number of wins of a drink prize game to a text file, close it, open it again, and use these figures to calculate the
 * probability of winning the game. 
 *
 * Nathan Gibson 
 * 09-27-09
 */


import java.util.Scanner;
import java.util.Random;
import java.io.IOException;
import java.io.PrintWriter;
import java.io.File;
public class BottleCapPrize
{
    public static void main(String [] args)throws IOException 
    {
        Scanner in; 
        in = new Scanner(System.in);
       
       
        int numTrials = 10;
        
       
        PrintWriter outFile = new PrintWriter (new File("bottleCap.txt"));
 
      
  
      for (int i = 0; i < numTrials; i++)
  
      {
  
      int counter = 0;
  
      int randomNumber = 0;
 
      
 
      do
 
      {
 
      randomNumber = ((int)(0+ Math.random()* 5));
 
      counter++;
 
      }
 
      while (randomNumber != 1);
 
      
 
      outFile.println(counter);
 
      }
 
      
 
        outFile.close ( );
       
        
        File fileName = new File("bottleCap.txt");
        Scanner inFile = new Scanner("bottleCap.txt");
        
        
        int sum = 0;
        int counter = 0;
        int average = 0;
        String data = "";
        average = sum/numTrials;
       
        while (inFile.hasNextInt())
        {
            data = inFile.next ( );
            int num = inFile.nextInt ();
            sum += num;
            counter++;
            
            
                 
           
            
         }    
            
    
        
       System.out.println(average); 
       inFile.close(); 
         
       
      
                   }
     }

```
i have updated the code to fit your previous descriptions, but i still get 0 for an output. i just dont know what it could be...

---

### Post by nathang1392 on 2009-09-30
i have diagnosed the problem. the thing i am using to calculate sum isnt working. i printed the value of it and it was zero.

---

### Post by pbrockway2 on 2009-09-30
The calculation of *sum* looks OK.  It's the calculation of *average* that's the problem.  You are attempting to calculate the average before you have read any data from the file.

Move the line "average = sum/numTrials;" to a more sensible place.

And consider alternatives, like "average=sum/counter" and/or making average a floating point number.

---

### Post by nathang1392 on 2009-09-30
how do you calculate the sum in this situation?

---

### Post by nathang1392 on 2009-09-30
i moved the average calculation to the bottom. i got the error " cant divide by zero" im suspecting that is my sum. i dont think its adding correctly. here is the updated.
```
  int sum = 0;
        int newCounter = 0;
        int average = 0;
        String data = "";
        
       
        while (inFile.hasNextInt())
        {
            data = inFile.next ( );
            int num = inFile.nextInt ();
            sum =+num;
            newCounter++;
         }    
            
    
       average =  sum/newCounter;
       System.out.println(average); 
       inFile.close(); 
         
       
      
                   }
     }
```

---

### Post by pbrockway2 on 2009-09-30
> **nathang1392 said:**
> how do you calculate the sum in this situation?

Like I said the calculation of the sum is fine ... providing you are actually reading some data.

You can check this by printing, eg, the value of *counter*.  If this comes out a zero then you are not actually reading any data.  In that case you should:

(1) Check that the data file exists and has the data you expect.

(2) Think about how you construct the Scanner.  Read its [API documentation]("http://java.sun.com/javase/6/docs/api/java/util/Scanner.html") and make sure you are actually scanning the file for data, and not doing something silly.

---

### Post by pbrockway2 on 2009-09-30
Our posts are crossing!

That error message is very good.  Because it shows that *newCounter* is zero.  And that means you are not reading any data.

So it's time to check that scanner...

---

### Post by falconindy on 2009-09-30
I know you're not at this point yet, but you'll be there soon enough...

To get a meaningful average, you'll probably to declare your variable 'average' as a double or a float, instead of an integer. When you do the division to find the average, you'll also need to cast one of the operands to a double or float (same as your average's variable type) in order to do floating point arithmetic. In other words:

```
double average;
/*
    loopy business here
*/

    average = (double)sum/newCounter;
```
Without the cast, you'll be doing integer arithmetic and truncating your result.

---

### Post by nathang1392 on 2009-09-30
> **pbrockway2 said:**
> Our posts are crossing!

That error message is very good.  Because it shows that *newCounter* is zero.  And that means you are not reading any data.

So it's time to check that scanner...

i did this, which i think would test to see if the numbers are there, i also tried sum, i got zero for both. i have no clue how to fix this :confused:
```
  while (inFile.hasNextInt())
        {
            data = inFile.next ( );
             num = inFile.nextInt ();
            sum = + num;
            newCounter++;
         }    
            
    

       System.out.println(num); 
       inFile.close(); 
         
       
      
                   }
     }
```

---

### Post by pbrockway2 on 2009-09-30
> **nathang1392 said:**
> i have no clue how to fix this 

I've already given you a big clue.  We have established (back when you got the divide by zero error: it refers to the denominator) that you are currently not reading any data.  Hence *sum* is zero, *newCounter* is zero and *average* explodes.

Now assuming that the file exists and contains good data (and if it were me I would check these things), the problem would appear to be with the scanner.

```

File fileName = new File("bottleCap.txt");
Scanner inFile = new Scanner("bottleCap.txt");

```

*These lines are wrong.*  Read the API documentation linked to above to see what you are actually scanning to get your data.  And to see what that second line should really be.

---

### Post by nathang1392 on 2009-09-30
haaaaaaaaaaaaaaa. i got it. thhhhaaanannnnkkkkkk you.. words cannot describe my emotions right now.

---

### Post by nathang1392 on 2009-09-30
haha wait. i got sum to partially  work, it took about three seconds for me to reaalize that the number i was getting was way too small.

---

### Post by pbrockway2 on 2009-09-30
Post your updated code if that might be the problem.

Otherwise another debugging trick is to actually print the value of *data* inside the loop before you add it on to get the sum.  That way you can check you are reading exactly the numbers you think you should.

And there's the point about integer division that has been raised before.  But this won't cause errors in the average > 1.

---

### Post by nathang1392 on 2009-09-30
```
       Scanner inFile = new Scanner(new File("bottleCap.txt"));
        
        int num = 0;
        int sum = 0;
        int newCounter = 0;
        double average = 0;
        String data = "";
        
       
        while (inFile.hasNextInt())
        {
            data = inFile.next( );
            num = inFile.nextInt ();
            sum = + num;
            newCounter++;
         }    
            
    
       average = sum/newCounter;
       System.out.println(sum); 
       inFile.close(); 
         
       
      
                   }
     }
```

i have this but when i get sum and print it to test i only get like a single digit number, when it should be triple or quad digits.

---

### Post by pbrockway2 on 2009-09-30
> ```

sum = + num

```

umm... don't you mean

```

sum += num;

```

Here's what I mean about debugging:

```

while (inFile.hasNextInt())
{
    data = inFile.next( );
    num = inFile.nextInt ();
    sum = + num;
    newCounter++;
    /**/System.out.printf("newCounter=%d data=%d sum=%d%n", newCounter, data, sum);
}  

```

It will catch a lot of problems.

---

### Post by nathang1392 on 2009-09-30
ohhhhhhh okay. okay. but seriously thank you. i have been working on this for days.

---

### Post by pbrockway2 on 2009-09-30
You're welcome.

---

### Post by lisati on 2009-09-30
> **pbrockway2 said:**
> 
Here's what I mean about debugging:

```

while (inFile.hasNextInt())
{
    data = inFile.next( );
    num = inFile.nextInt ();
    sum = + num;
    newCounter++;
    /**/System.out.printf("newCounter=%d data=%d sum=%d%n", newCounter, data, sum);
}  

```

It will catch a lot of problems.
+1: Using something like the line beginning /**/ is a useful technique for seeing if your code is doing what you expect, which can easily be commented out once you're happy with it.

Good luck everyone!

---

