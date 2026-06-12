---
title: "filling an array list with values"
date: 2009-11-14
forum: Programming Talk
---

### Post by nathang1392 on 2009-11-14
im working on a program that calculates the trajectory of an object given its launch speed and its launch angle. i have two array lists. one for speed, and one for angle. i also have a method that given the speed and angle can calculate the distance that the object will go. i have everything i need besides what actually does the calculations, it gets kind of confusing at this point. i have to take each speed and angle and get the distance to fill a table. i made a new array called distance, what is confusing me though is how to take each value and calculate and so on and so on. i attached a picture of the table so it would be easy to get an idea of what i was talking about. i have been struggling trying to figure this out for the last few days. if you guys can help me figure this out it would be very appreciated.

```

/**
 * Write a description of class Catapult here.
 * 
 * @author (your name) 
 * @version (a version number or a date)
 */
import static java.lang.Math.*;
public class Catapult
{
    public double launchSpeed, launchAngle, distanceFeet, distanceMeters, distance, speed, angle;
    public static final double accelerationDueToGravity = 9.8, speedFeetFactor = 3.28;
    
    
    
    
    

    public Catapult(double speed, double angle)
    {


    }
    
    
    
    public void distanceMeters()
    {
        
        distanceMeters = pow(speed, 2)  * Math.sin(2 * toRadians(angle)) / accelerationDueToGravity;
        
    }
    
    public void distanceFeet()
    {
        distanceFeet = distance * speedFeetFactor;
        
    }
}
```

```

/**
 * Write a description of class CatapultTester here.
 * 
 * @author (your name) 
 * @version (a version number or a date)
 */
import java.util.ArrayList;
public class CatapultTester
{
    public static void main(String[] args)
    {
           ArrayList<Integer> speed = new ArrayList<Integer>();
           speed.add(new Integer(20));
           speed.add(new Integer(25));
           speed.add(new Integer(30));
           speed.add(new Integer(35));
           speed.add(new Integer(40));
           speed.add(new Integer(45));
           speed.add(new Integer(50));
           
           
           ArrayList<Integer> angle = new ArrayList<Integer>();
           angle.add(new Integer(25));
           angle.add(new Integer(30));
           angle.add(new Integer(35));
           angle.add(new Integer(40));
           angle.add(new Integer(45));
           angle.add(new Integer(50));
           angle.add(new Integer(55));
           
           
           

           
           ArrayList<Double> distance = new ArrayList<Double>();
           for(int i = 0; i < angle.size(); i ++)
           {
               
               

               
           }
           
    
            //print header
            System.out.println("                                                 Projectile Distance (feet)");
            System.out.println("  MPH \t 25 deg \t 30 deg \t 35 deg \t 40 deg \t 45 deg \t 50 deg \t 55 deg");
            System.out.println("===============================================================================================================");
            
            
            
            
           
        }
}
```

---

### Post by dwhitney67 on 2009-11-14
It seems that for each velocity, you need to test each at different angles.  Thus I would suspect that you need nested for-loops, to iterate through each of the arrays you have.

Something like:
```

for i :=  [0 ... array1.size)
{
   for j := [0, array2.size)
   {
      // do something with array1[i] and array2[j]
   }
}

```
Note, the code above is an attempt at pseudo-code.

---

### Post by nathang1392 on 2009-11-14
thats mostly the part i dont understand, i mean i know thats what i need to do, but im having trouble getting how to actually perform it. im not really too familiar with array list and how they work. i know that i need to test each velocity against each angle, but...](*,)

basically what im trying to do is have a for loop that takes each velocity and then a for loop inside that takes each angle and plugs them into my method, but i dont know how to actually construct the part that tells the methods which numbers to use.

im having trouble explaining my problem, sorry.

---

### Post by dwhitney67 on 2009-11-14
Since you are developing Java applications, the website detailing the API is a must-have; thus bookmark this URL:
[http://java.sun.com/javase/6/docs/api/](http://java.sun.com/javase/6/docs/api/)

For the ArrayList, click here:
[http://java.sun.com/javase/6/docs/api/java/util/ArrayList.html](http://java.sun.com/javase/6/docs/api/java/util/ArrayList.html)

You are probably going to want to familiarize yourself with:
add(), get(), and size().

P.S.  I can see from your code that you already know about add().

---

### Post by nathang1392 on 2009-11-14
alright, im trying to follow your direction. i looked at the api's and i tried to familiarize myself. i got some code together, but im not sure it is right. 

```
ArrayList<Double> distance = new ArrayList<Double>();
           for(int i = 0; i < angle.size(); i ++)
           {
               for int j = 0; j < speed. size(); j++)
               { 
                   distance[i][j] = catapult.getDistance(speed[i], angle[j])
                }
            }
```
i dont know if this is the right track, but im getting compiler errors.

---

### Post by PaulM1985 on 2009-11-14
Where do you get your compiler errors, can you post the full code.

Paul

---

### Post by nathang1392 on 2009-11-14
```

/**
 * Write a description of class Catapult here.
 * 
 * @author (your name) 
 * @version (a version number or a date)
 */
import static java.lang.Math.*;
public class Catapult
{
    public double launchSpeed, launchAngle, distanceFeet, distanceMeters, distance, speed, angle;
    public static final double accelerationDueToGravity = 9.8, speedFeetFactor = 3.28;
    
    
    
    
    

    public Catapult(double speed, double angle)
    {


    }
    
    
    
    public void distanceMeters()
    {
        
        distanceMeters = pow(speed, 2)  * Math.sin(2 * toRadians(angle)) / accelerationDueToGravity;
        
    }
    
    public void distanceFeet()
    {
        distanceFeet = distance * speedFeetFactor;
        
    }
}
```
```

/**
 * Write a description of class CatapultTester here.
 * 
 * @author (your name) 
 * @version (a version number or a date)
 */
import java.util.ArrayList;
public class CatapultTester
{
    public static void main(String[] args)
    {
           ArrayList<Integer> speed = new ArrayList<Integer>();
           speed.add(new Integer(20));
           speed.add(new Integer(25));
           speed.add(new Integer(30));
           speed.add(new Integer(35));
           speed.add(new Integer(40));
           speed.add(new Integer(45));
           speed.add(new Integer(50));
           
           
           ArrayList<Integer> angle = new ArrayList<Integer>();
           angle.add(new Integer(25));
           angle.add(new Integer(30));
           angle.add(new Integer(35));
           angle.add(new Integer(40));
           angle.add(new Integer(45));
           angle.add(new Integer(50));
           angle.add(new Integer(55));
           
           
           

           
           ArrayList<Double> distance = new ArrayList<Double>();
           for(int i = 0; i < angle.size(); i ++)
           {
               for(int j = 0; j < speed. size(); j++)
               { 
                   distance[i][j] = catapult.getDistance(speed[i], angle[j];
                }
            }
               
               

               
           
           
    
            //print header
            System.out.println("                                                 Projectile Distance (feet)");
            System.out.println("  MPH \t 25 deg \t 30 deg \t 35 deg \t 40 deg \t 45 deg \t 50 deg \t 55 deg");
            System.out.println("===============================================================================================================");
            
            
            
            
           
        }
}
```

i get ")" expected on my line that is inside of my j loop. if you can help it would be very very appreciated.

---

### Post by nathang1392 on 2009-11-14
sorry the ) was needed. i fixed that. now im getting that array is required, but arraylist is found.

---

### Post by dwhitney67 on 2009-11-14
You need to add distance values to your 'distance' array; I do not believe you can set them manually as you have shown earlier.

Consider the following:
```

ArrayList<Double> distance = new ArrayList<Double>();

for (int i = 0; i < angle.size(); ++i)
{
   for (int j = 0; j < speed.size(); ++j)
   { 
      Double dist = new Double(catapult.getDistance(speed[i], angle[j]));

      distance.add(dist);
   }
}

```
To access the values in the 'distance' array list, you will need to perform some basic arithmetic so that you can associate the row/column for your table.  Think of your angle index as being the row number, and the speed index as your column number.

Thus, to print the data of your table:
```

for (int i = 0; i < angle.size(); ++i)
{
   for (int j = 0; j < speed.size(); ++j)
   {
      System.out.print(distance.get((i * speed.size()) + j) + "  ");
   }
   System.out.println();
}

```
Of course, the code above lacks the pretty table to show the relationship between MPH and Angle, but I'll leave that up to you to do.

P.S.  It's been a while since I did Java programming; you may need to convert the Double values in the distance array using toString() before you can print them.

P.S. #2 A lot of your compiler errors are due to poor syntax; pay careful attention when you write code.

---

### Post by nathang1392 on 2009-11-14
im still getting the same problem with the first part of your code, array required, but arraylist found

---

### Post by dwhitney67 on 2009-11-14
Just take a look at the following:
```

import java.util.ArrayList;
import java.lang.Math.*;

public class Catapult
{
   private double speed;
   private double angle;

   private static final double GRAVITY_ACCELERATION = 9.8;
   private static final double SPEED_FEET_FACTOR    = 3.28;
    
   public Catapult(double speed, double angle)
   {
      this.speed = speed;
      this.angle = angle;
   }

   public double getDistance()
   {
      return Math.pow(speed, 2)  * Math.sin(2.0 * Math.toRadians(angle)) / GRAVITY_ACCELERATION;
   }

   public static void main(String[] args)
   {
      ArrayList<Double> speed = new ArrayList<Double>();
      speed.add(new Double(20));
      speed.add(new Double(25));
      speed.add(new Double(30));
      speed.add(new Double(35));
      speed.add(new Double(40));
      speed.add(new Double(45));
      speed.add(new Double(50));
           
      ArrayList<Double> angle = new ArrayList<Double>();
      angle.add(new Double(25));
      angle.add(new Double(30));
      angle.add(new Double(35));
      angle.add(new Double(40));
      angle.add(new Double(45));
      angle.add(new Double(50));
      angle.add(new Double(55));
           
      //ArrayList<Double> distance = new ArrayList<Double>();

      System.out.println("                                                 Projectile Distance (feet)");
      System.out.println("  MPH \t 25 deg \t 30 deg \t 35 deg \t 40 deg \t 45 deg \t 50 deg \t 55 deg");

      for(int i = 0; i < angle.size(); ++i)
      {
         System.out.print("\n" + speed.get(i) + "\t");

         for(int j = 0; j < speed.size(); ++j)
         {
            // A Catapult object needs to be constructed!
            Catapult cat  = new Catapult(speed.get(i), angle.get(j));
            Double   dist = new Double(cat.getDistance());

            //distance.add(dist);
            //System.out.print(distance.get((i*speed.size()) + j) + "\t");

            System.out.print(dist + "\t");
         }
      }
      System.out.println();
   }
}

```

If you require the 'distance' array, then uncomment what I have commented-out above.

Also, do some research on how you can set the precision on the double values so that you yield a result that has no more, and no less, precision than your input data.

---

### Post by nathang1392 on 2009-11-14
thanks so much. it makes alot more sense. your a java pro.

---

