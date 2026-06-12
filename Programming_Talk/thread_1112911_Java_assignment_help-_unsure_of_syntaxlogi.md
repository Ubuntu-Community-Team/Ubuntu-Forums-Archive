---
title: "Java assignment help- unsure of syntax/logi"
date: 2009-04-01
forum: Programming Talk
---

### Post by Garratt on 2009-04-01
Hi,
 so i just hand in my C++ assignment to find out Java is due tomorrow (yAy!... Long story, basically i enrolled 3weeks late then had a baby) In the Java assignment the teacher asks for a fairly specific logic/syntax, and while I have been doing ok so far... I think I have lost where I am up to, or i suppose what i should do with this problem method.

Problem:
```
Aaron, Bob and Charlie had an argument over
which one of them was the greatest puzzler of all time. To end the argument
once and for all, they agreed to a duel to the death. Aaron was a poor shooter
and only hit his target with a probability of 1 in 3. Bob was a little better and hit
his target with a probability of 1 in 2. Charlie was an expert marksman and
never missed. A hit means a kill and the person hit drops out of the duel.
To compensate for the inequities in their marksmanship skills, the three
decided that they would fire in turns, starting with Aaron, followed by Bob, and
then by Charlie. The cycle would repeat until there was one man standing,
and that man would be the Greatest Puzzler of All Time.
An obvious and reasonable strategy is for each man to shoot at the most
accurate shooter still alive, on the grounds that this shooter is the deadliest
and has the best chance of hitting back
Write a program to simulate the duel using this strategy. Your program should
use random numbers and the probabilities given in the problem to determine
whether a shooter hits the target. Create a class named Dueler that contains
the dueler's name, shooting accuracy, a boolean indicating whether the
dueler is still alive, and a method
ShootAtTarget (Dueler target)
that sets the target to dead if the dueler hits his target (using a random
number and the shooting accuracy) and does nothing otherwise.
```

Ok so I get that shootAtTarget(name) needs to use math.random to fire the shot etc, and I know my object "aaron" has 33.33% accuracy. So should I put a switch/case statement in shootAtTarget depending on accuracy or name? or should i do it another way?

2 files MainApp.cpp and Dueler.cpp --- Pretty much just a standard template at the moment, a few technical methods missing.
MainApp.cpp:-
```
/** DSBD152- 7070256400
 * @(#)mainApp.java
 * @(#)Assignment One
 * @author Garratt Campton
 * @version 1.00-01/04/09
 * @date 01/04/2009
 **/

public class MainApp
{
    public static void main(String[] args)
    {
       // create duelers
       Dueler aaron = new Dueler("Arron", true, true, 3);
       Dueler bob = new Dueler("Bob", true, false, 2);
       Dueler charlie = new Dueler("Charlie", true, false, 1);
       int i;
       int aaronWinCount =0;
       int bobWinCount =0;
       int charlieWinCount =0;
       boolean duelOver = true;

       for (i=0;i<10000;++i)
       {
       	while (!duelOver)
       	{
       		if (aaron.getAlive() && aaron.getTurn())
       		{

       			if (charlie.getAlive())
       			{
       				aaron.shootAtTarget(charlie);
       			}
       			else if (bob.getAlive())
       			{
       				aaron.shootAtTarget(bob);
       			}

       			arron.setTurn(false);
       			bob.setTurn(true);
       			if (!charlie.getAlive() && !bob.getAlive())
       			{
       				++aaronWinCount;
       				break;
       			}
       		} // end if

       		if (bob.getAlive() && bob.getTurn())
       		{
       			if (charlie.getAlive())
       			{
       				bob.shootAtTarget(charlie);
       			}
       			if (aaron.getAlive())
       			{
       				bob.shootAtTarget(aaron);
       			}

       			bob.setTurn(false);
       			charlie.setTurn(true);

       			if (!charlie.getAlive() && !aaron.getAlive())
       			{
       				++bobWinCount;
       				break;
       			}
       		}


       		if (charlie.getAlive() && charlie.getTurn())
       		{
       			if (bob.getAlive())
       			{
       				charlie.shootAtTarget(bob);
       			}
       			if (aaron.getAlive())
       			{
       				charlie.shootAtTarget(aaron);
       			}

       			charlie.setTurn(false);
       			aaron.setTurn(true);

       			if (!bob.getAlive() && !aaron.getAlive())
       			{
       				++charlieWinCount;
       				break;
       			}
       		}


       	} // end while
       } // end for
    } // end main
} // end class

```

Dueler.cpp:-
```
/** DSBD152- 7070256400
 * @(#)mainApp.java
 * @(#)Assignment One
 * @author Garratt Campton
 * @version 1.00-01/04/09
 * @date 01/04/2009
 **/



public class Dueler
{
	// Dueler Constructor
    public Dueler(String name, boolean alive, boolean turn, int accuracy)
    {
		this.name = name;
		this.alive = alive;
		this.turn = turn;
		this.accuracy = accuracy;
    }
//----------------------------------------------------
//----- getName -----
    public String getName()
    {
    	return this.name;
    }
//----------------------------------------------------
//----- set/getAlive -----
	public void setAlive(boolean alive)
    {
		this.alive = alive;
	}
	public boolean getAlive()
	{
		return this.alive;
	}
//----------------------------------------------------
//----- set/getTurn -----
	public void setTurn(boolean turn)
	{
		this.turn = turn;
	}
	public boolean getTurn()
	{
		return this.turn;
	}
//----------------------------------------------------
//----- getAccuracy -----
	public int getAccuracy()
	{
		return accuracy;
	}
//----------------------------------------------------
//----- shootAtTarget -----
	public void shootAtTarget(name)
	{
		
	}

//----------------------------------------------------
//----------------------------------------------------
//----------------------------------------------------
//----------------------------------------------------
}

```

Thanks for reading thus far.

---

### Post by tribaal on 2009-04-01
You can get the object's accuracy from within the function:
(in pseudocode)
```

public void shootAtTarget(name)
	{
	  if(#random 100%# < this.getAccuracy()){
           //You hit the target
           name.isDead = true;
          }
          // Else you miss
	}

```

Have fun :)

- Trib'

---

### Post by Garratt on 2009-04-01
> **tribaal said:**
> You can get the object's accuracy from within the function:
(in pseudocode)
```

public void shootAtTarget(name)
	{
	  if(#random 100%# < this.getAccuracy()){
           //You hit the target
           name.isDead = true;
          }
          // Else you miss
	}

```

Have fun :)

- Trib'

thanks :mrgreen:

---

### Post by Garratt on 2009-04-01
woops i just took for granted that was right, didn't read it too well though, because accuracy is in MainApp.cpp on initialization of the 3 objects, set to 1, 2, 3.
aaron=3, bob=2, charlie=1. which is how we are told to do it.

see now to me just setting it as double 33.33 makes much more sense >.< but then that would just be too easy...

so, from what i can tell you can not pass values into the parenthises of random, which makes life difficult and... did i mention i hate java.
```

switch (this.getAccuracy)
    case 1:                   // charlie is 100%
        name.setAlive = false;
        break;
    case 2:                   // bob is 50%
        aHit = (int) (Math.random() * 100);
        if (aHit > 50)
          {
            name.setAlive = false;    
          }
        else
           {
            name.setAlive = true;      
           }
            break;
    case 3:                 // aaron is 33%
        aHit = (int) (Math.random() * 100);
        if (aHit < 33)
          {
            name.setAlive = false;    
          }
        else
           {
            name.setAlive = true;
           }
           break;

```
something like this?
looks almost right I went through all the different exercises to find any math.random and could only find one.

I guess I just answered my own question, good for me.

EDIT: I just compile this and for some reason get identifier expected on line 56>
	public void shootAtTarget(name)  <--------- something wrong with saying that ?

---

### Post by dwhitney67 on 2009-04-01
Try
```

public void shootAtTarget(String name)
{
  ...
}

```

P.S.  I hate April Fool's Day... the pink background is annoying.

---

### Post by Garratt on 2009-04-01
ok i see where i am going wrong:

in main im passing the objects through to shootAtTarget which is expecting a string.

---

### Post by Garratt on 2009-04-01
> **dwhitney67 said:**
> Try
```

public void shootAtTarget(String name)
{
  ...
}

```

P.S.  I hate April Fool's Day... the pink background is annoying.

ok now it says that every variable in dueler is not found.
Do i need to initialize in the class before the constructor?

cannot find symbol variable name
cannot find symbol variable alive
cannot find symbol variable turn
cannot find symbol variable accuracy
cannot find symbol variable name
cannot find symbol variable alive
cannot find symbol variable alive
cannot find symbol variable turn
cannot find symbol variable turn
cannot find symbol variable accuracy
cannot find symbol variable getAccuracy
cannot find symbol variable setAlive
cannot find symbol variable setAlive
cannot find symbol variable setAlive
cannot find symbol variable setAlive
cannot find symbol variable setAlive

---

### Post by dwhitney67 on 2009-04-01
Umm... yes, just like you would do if you were programming in C++.  Your data members should be declared as private, unless you have a compelling reason to do otherwise.

---

### Post by Garratt on 2009-04-01
thanks :d last one, i think... i changed the setAlive to setAlive()

but still comming up as a variable that cannot be found.

all the: name.setAlive() = false; in the switch statements are wrong.

```
/** DSBD152- 7070256400
 * @(#)mainApp.java
 * @(#)Assignment One
 * @author Garratt Campton
 * @version 1.00-01/04/09
 * @date 01/04/2009
 **/



public class Dueler
{
		int aShot;
		String name;
		boolean alive;
		boolean turn;
		int accuracy;
	
	// Dueler Constructor
    public Dueler(String name, boolean alive, boolean turn, int accuracy)
    {
		this.name = name;
		this.alive = alive;
		this.turn = turn;
		this.accuracy = accuracy;
    }
//----------------------------------------------------
//----- getName -----
    public String getName()
    {
    	return this.name;
    }
//----------------------------------------------------
//----- set/getAlive -----
	public void setAlive(boolean alive)
    {
		this.alive = alive;
	}
	public boolean getAlive()
	{
		return this.alive;
	}
//----------------------------------------------------
//----- set/getTurn -----
	public void setTurn(boolean turn)
	{
		this.turn = turn;
	}
	public boolean getTurn()
	{
		return this.turn;
	}
//----------------------------------------------------
//----- getAccuracy -----
	public int getAccuracy()
	{
		return this.accuracy;
	}
//----------------------------------------------------
//----- shootAtTarget -----
	public void shootAtTarget(String name)
	{
		switch (this.getAccuracy())
		{
		
    	case 1:                   // charlie is 100%
        	name.setAlive() = false;
        	break;
    	case 2:                   // bob is 50%
        	aShot = (int) (Math.random() * 100);
        	if (aShot > 50)
          	{
            	name.setAlive() = false;    
          	}
        	else
          	{
            	name.setAlive() = true;      
           	}
            break;
    	case 3:                 // aaron is 33%
        	aShot = (int) (Math.random() * 100);
        	if (aShot < 33)
          	{
            	name.setAlive() = false;    
          	}
        	else
           	{
            	name.setAlive() = true;
           	}
           	break;
		}
	}

//----------------------------------------------------



//----------------------------------------------------


//----------------------------------------------------


//----------------------------------------------------
}

```

---

### Post by Garratt on 2009-04-01
I got to put up with the pink for the rest of the day?

ouch, they could have given it a post count or refresh count or something so it dissapears after a while... it seems to go back to grey and now and then.

---

### Post by konqueror7 on 2009-04-01
> **Garratt said:**
> thanks :d last one, i think... i changed the setAlive to setAlive()

but still comming up as a variable that cannot be found.

all the: name.setAlive() = false; in the switch statements are wrong.

```
/** DSBD152- 7070256400
 * @(#)mainApp.java
 * @(#)Assignment One
 * @author Garratt Campton
 * @version 1.00-01/04/09
 * @date 01/04/2009
 **/



public class Dueler
{
		int aShot;
		String name;
		boolean alive;
		boolean turn;
		int accuracy;
	
	// Dueler Constructor
    public Dueler(String name, boolean alive, boolean turn, int accuracy)
    {
		this.name = name;
		this.alive = alive;
		this.turn = turn;
		this.accuracy = accuracy;
    }
//----------------------------------------------------
//----- getName -----
    public String getName()
    {
    	return this.name;
    }
//----------------------------------------------------
//----- set/getAlive -----
	public void setAlive(boolean alive)
    {
		this.alive = alive;
	}
	public boolean getAlive()
	{
		return this.alive;
	}
//----------------------------------------------------
//----- set/getTurn -----
	public void setTurn(boolean turn)
	{
		this.turn = turn;
	}
	public boolean getTurn()
	{
		return this.turn;
	}
//----------------------------------------------------
//----- getAccuracy -----
	public int getAccuracy()
	{
		return this.accuracy;
	}
//----------------------------------------------------
//----- shootAtTarget -----
	public void shootAtTarget(String name)
	{
		switch (this.getAccuracy())
		{
		
    	case 1:                   // charlie is 100%
        	name.setAlive() = false;
        	break;
    	case 2:                   // bob is 50%
        	aShot = (int) (Math.random() * 100);
        	if (aShot > 50)
          	{
            	name.setAlive() = false;    
          	}
        	else
          	{
            	name.setAlive() = true;      
           	}
            break;
    	case 3:                 // aaron is 33%
        	aShot = (int) (Math.random() * 100);
        	if (aShot < 33)
          	{
            	name.setAlive() = false;    
          	}
        	else
           	{
            	name.setAlive() = true;
           	}
           	break;
		}
	}

//----------------------------------------------------



//----------------------------------------------------


//----------------------------------------------------


//----------------------------------------------------
}

```

i think it should look like this, since its already a dueler object, and java is not similar to C# in which you just assign values to its properties, the code should be like this...

```
this.setAlive(false);
```

---

### Post by dwhitney67 on 2009-04-01
The shootAtTarget() method does not appear as if it should be encapsulated within the Dueler() class.  It should be part of the class that manages the "game", and hence manages the 3 Duelers.

You cannot set the 'alive' attribute of a String (e.g. name).  So the function shootAtTarget() does not make sense in its current context.

I think a refactoring of the app needs to take place!

---

### Post by Garratt on 2009-04-01
> **dwhitney67 said:**
> The shootAtTarget() method does not appear as if it should be encapsulated within the Dueler() class.  It should be part of the class that manages the "game", and hence manages the 3 Duelers.

You cannot set the 'alive' attribute of a String (e.g. name).  So the function shootAtTarget() does not make sense in its current context.

I think a refactoring of the app needs to take place!

I'm confused, so I should take out string from shootAtTarget()
and then it would be as if you pass the object through, but that may mean accuracy will be taken from target not the shooter.

The teacher asks for method ShootAtTarget(Dueler, target)
that sets the target to dead if shot or does nothing otherwise.

Or to be more specific:
Create a class named Dueler that contains
the dueler's name, shooting accuracy, a boolean indicating whether the
dueler is still alive, and a method
ShootAtTarget (Dueler target)
that sets the target to dead if the dueler hits his target (using a random
number and the shooting accuracy) and does nothing otherwise...

---

### Post by dwhitney67 on 2009-04-01
> **Garratt said:**
> I'm confused, so I should take out string from shootAtTarget()
and then it would be as if you pass the object through, but that may mean accuracy will be taken from target not the shooter.

The teacher asks for method ShootAtTarget(Dueler, target)
that sets the target to dead if shot or does nothing otherwise.

Or to be more specific:
Create a class named Dueler that contains
the dueler's name, shooting accuracy, a boolean indicating whether the
dueler is still alive, and a method
ShootAtTarget (Dueler target)
that sets the target to dead if the dueler hits his target (using a random
number and the shooting accuracy) and does nothing otherwise...

Yes, something like that.

The way I interpret the issue, is that a Dueler A will participate in combat with another Dueler B.  Will B survive or not?  That's what the random number generator is for... to ascertain whether Dueler A is a good shot or not.

As for each of the 3 Dueler objects, these will be managed by the Game object, for lack of a better description.  A round-robin of duels will take place, where one Dueler attempts to kill another.  The purpose of ShootAtTarget() is to manage this situation.

ShootAtTarget() can be implemented in one of two ways:
```

public class Game
{
  ...

  public void ShootAtTarget(Dueler shooter, Dueler target)
  {
     "shooter" will attempt to kill "target"
     ...
  }
}
// or

public class Dueler
{
   ...

   public void ShootAtTarget(Dueler target)
   {
      "this" will attempt to kill "target"
      ...
   }
}

```

It is up to you to decide which approach to take, although if you want a good mark on your project, your instructor's preference should be the one taken!  :-)

---

### Post by Garratt on 2009-04-01
I think i might think about it... while i sleep :P

thanks for all your help guys.

---

### Post by Garratt on 2009-04-01
regurgitating what i have already said:

public class Dueler
{
   ...

   public void ShootAtTarget(Dueler target)
   {
      "this" will attempt to kill "target"
      ...
   }
}

This is the logic part I do not understand, if "target" is not a String name, then what is it? 
would be good if i could somehow say:

public class Dueler
{
   ...

   public void ShootAtTarget(obj.dueler)
   {
      // being that shootAtTarget is called by
      // aaron.shootAtTarget(charlie)
      ...
   }
}

OR what i should be doing is maybe making another boolean variable called target which is pretty much a dummy variable
just so i can pass the object through.

---

### Post by shadylookin on 2009-04-02
> **Garratt said:**
> regurgitating what i have already said:

public class Dueler
{
   ...

   public void ShootAtTarget(Dueler target)
   {
      "this" will attempt to kill "target"
      ...
   }
}

This is the logic part I do not understand, if "target" is not a String name, then what is it? 
would be good if i could somehow say:

public class Dueler
{
   ...

   public void ShootAtTarget(obj.dueler)
   {
      // being that shootAtTarget is called by
      // aaron.shootAtTarget(charlie)
      ...
   }
}

OR what i should be doing is maybe making another boolean variable called target which is pretty much a dummy variable
just so i can pass the object through.

target is an instance of a Dueler 

for example
[PHP]
import java.util.Random;
public class Dueler{

    public boolean isAlive;
    private Random random;
    private int percentage;

    public Dueler(int p){
        percentage = p;
    }

    public void ShootAtTarget(Dueler target){
        random = new Random();
        if(random.nextInt(100) < percentage){
            target.isAlive = false;
        }
    }  
    

    public static void main(String args[]){
        Dueler A = new Dueler(33);
        Dueler B = new Dueler(50);

        A.shootAtTarget(B);
    }

}

[/PHP]

Telling Dueler A to shoot at Dueler B

I'm rusty but I'm pretty sure it's the c++ equivalent to 

Dueler::shootAtTarget(Dueler &target){
//blah blah blah
}

---

### Post by Garratt on 2009-04-02
i decided to try another way that seems a little simpler much like myself. added another boolean to dueler called aHit. set aHit to false on all duelers so now my switch statement simply sets aHit to true if they get aShot. :)
Now if i change main to simple if bob.aHit(true) then charlie.Alive(false) statements it should work, also I really don't need case 1... as charlie always hits it is not needed.

Just means I probably won't get credit/honors, but then I won't get a headache either. So a pass is fine.


```
 public static void main(String[] args)
    {
       // create duelers
       Dueler aaron = new Dueler("Arron", true, true, 3, false);
       Dueler bob = new Dueler("Bob", true, false, 2, false);
       Dueler charlie = new Dueler("Charlie", true, false, 1, false);
...
```

```

// Dueler Constructor
    public Dueler(String name, boolean alive, boolean turn, int accuracy, boolean aHit)
    {
		this.name = name;
		this.alive = alive;
		this.turn = turn;
		this.accuracy = accuracy;
                this.aHit = aHit;
    }
//----------------------------------------------------
//----------------------------------------------------
public void shootAtTarget()
{
	switch (this.getAccuracy())
		{
		
    	case 1:                   // charlie is 100%
        	aHit = true;
        	break;
    	case 2:                   // bob is 50%
        	aShot = (int) (Math.random() * 100);
        	if (aShot > 50)
          	{
            	aHit = true;    
          	}
        	else
          	{
            	aHit = false;      
           	}
            break;
    	case 3:                 // aaron is 33%
        	aShot = (int) (Math.random() * 100);
        	if (aShot < 33)
          	{
            	aHit = true;    
          	}
        	else
           	{
            	aHit = false;
           	}
           	break;
		}
}

//----------------------------------------------------
```

---

### Post by Garratt on 2009-04-02
So I have almost finished it but something is wrong with my for/while loops in MainApp.cpp I thought my break; statements would exit out of my while loops and being that I am able to run a test run I would say this is true. but once I add the for loop nothing happens.

I will post both files in the hope someone can see the problem.

i ran it about 50 times without the for loops and each times it printed a winner and it was very random each person won about 33% of time.

MainApp.cpp

```
/** DSBD152- 7070256400
 * @(#)mainApp.java
 * @(#)Assignment One
 * @author Garratt Campton
 * @version 1.00-01/04/09
 * @date 01/04/2009
 **/

public class MainApp
{
    public static void main(String[] args)
    {
       // create duelers
       Dueler aaron = new Dueler("Arron", true, true, 3, false);
       Dueler bob = new Dueler("Bob", true, false, 2, false);
       Dueler charlie = new Dueler("Charlie", true, false, 1, false);
       int i;
       int aaronWinCount =0;
       int bobWinCount =0;
       int charlieWinCount =0;
       boolean duelOver = false;

//       for (i=0;i<100;++i)
//       {
       	while (!duelOver)
       	{
       		if (aaron.getAlive() && aaron.getTurn())
       		{
				// checks who to shoot at
       			if (charlie.getAlive())
       			{
       				aaron.shootAtTarget();
       				if (aaron.getAHit())
       				{
       					charlie.setAlive(false);
       					aaron.setAHit(false);
       				}
       			}
       			else if (bob.getAlive())
       			{
       				aaron.shootAtTarget();
       				if (aaron.getAHit())
       				{
       					bob.setAlive(false);
       					aaron.setAHit(false);
       				}
       			}

       			aaron.setTurn(false);
       			// now checks for whos turn is next
       			if (bob.getAlive())
       			{
       				bob.setTurn(true);
       			}
       			else if (charlie.getAlive())
       			{
       				charlie.setTurn(true);
       			}
       			// add to win count if both dead
       			if (!charlie.getAlive() && !bob.getAlive())
       			{
       				++aaronWinCount;
       				break;
       			}
       		} // end if
			
			// checks who to shoot at
       		if (bob.getAlive() && bob.getTurn())
       		{
       			if (charlie.getAlive())
       			{
       				bob.shootAtTarget();
       				if (bob.getAHit())
       				{
       					charlie.setAlive(false);
       					bob.setAHit(false);
       				}
       			}
       			else if (aaron.getAlive())
       			{
       				bob.shootAtTarget();
       				if (bob.getAHit())
       				{
       					aaron.setAlive(false);
       					bob.setAHit(false);
       				}
       			}
				
       			bob.setTurn(false);
       			// now checks for whos turn is next
       			if (charlie.getAlive())
       			{
       				charlie.setTurn(true);
       			}
       			else if (aaron.getAlive())
       			{
       				aaron.setTurn(true);
       			}
				// add to win count if both dead
       			if (!charlie.getAlive() && !aaron.getAlive())
       			{
       				++bobWinCount;
       				break;
       			}
       		}

			// checks who to shoot at
       		if (charlie.getAlive() && charlie.getTurn())
       		{
       			if (bob.getAlive())
       			{
       				bob.setAlive(false);
       			}
       			else if (aaron.getAlive())
       			{
       				aaron.setAlive(false);
       			}
				
       			charlie.setTurn(false);
       			// now checks for whos turn is next
       			if (aaron.getAlive())
       			{
       				aaron.setTurn(true);
       			}
       			else if (bob.getAlive())
       			{
       				bob.setTurn(true);
       			}
				// add to win count if both dead
       			if (!bob.getAlive() && !aaron.getAlive())
       			{
       				++charlieWinCount;
       				break;
       			}
       		}
       	} // end while
//       } // end for
       System.out.printf("Aarrons win count: %d\n", aaronWinCount);
       System.out.printf("Bobs win count: %d\n", bobWinCount);
       System.out.printf("Charlies win count: %d\n", charlieWinCount);
    } // end main
} // end class

```

Dueler.cpp

```
/** DSBD152- 7070256400
 * @(#)mainApp.java
 * @(#)Assignment One
 * @author Garratt Campton
 * @version 1.00-01/04/09
 * @date 01/04/2009
 **/



public class Dueler
{
		int aShot;
		boolean aHit;
		String name;
		boolean alive;
		boolean turn;
		int accuracy;
		
		
//----------------------------------------------------
//----- Dueler Constructor -----
    public Dueler(String name, boolean alive, boolean turn, int accuracy, boolean aHit)
    {
		this.name = name;
		this.alive = alive;
		this.turn = turn;
		this.accuracy = accuracy;
    }
//----------------------------------------------------
//----- getName -----
    public String getName()
    {
    	return this.name;
    }
//----------------------------------------------------
//----- set/getAlive -----
	public void setAlive(boolean alive)
    {
		this.alive = alive;
	}
	public boolean getAlive()
	{
		return this.alive;
	}
//----------------------------------------------------
//----- set/getTurn -----
	public void setTurn(boolean turn)
	{
		this.turn = turn;
	}
	public boolean getTurn()
	{
		return this.turn;
	}
//----------------------------------------------------
//----- getAccuracy -----
	public int getAccuracy()
	{
		return this.accuracy;
	}
//----------------------------------------------------
//----- set/getAHit -----
	public void setAHit(boolean aHit)
	{
		this.aHit = aHit;
	}
	public boolean getAHit()
	{
		return this.aHit;
	}

//----------------------------------------------------
//----- shootAtTarget -----
	public void shootAtTarget()
	{
		switch (this.getAccuracy())
			{
			
	    	case 1:                   // charlie is 100%
	        	this.setAHit(true);
	        	break;
	    	case 2:                   // bob is 50%
	        	aShot = (int) (Math.random() * 100);
	        	if (aShot > 50)
	          	{
	            	this.setAHit(true);    
	          	}
	        	
	            break;
	    	case 3:                 // aaron is 33%
	        	aShot = (int) (Math.random() * 100);
	        	if (aShot < 33)
	          	{
	            	this.setAHit(true);    
	          	}
	        	
	           	break;
			}
	}

//----------------------------------------------------

}



//----------------------------------------------------

//	public void shootAtTarget()
//	{
//		switch (this.getAccuracy())
//		{
//		
//    	case 1:                   // charlie is 100%
//        	name.setAlive(false);
//        	break;
//    	case 2:                   // bob is 50%
//        	aShot = (int) (Math.random() * 100);
//        	if (aShot > 50)
//          	{
//            	name.setAlive(false);    
//          	}
//        	else
//          	{
//            	name.setAlive(true);      
//           	}
//            break;
//    	case 3:                 // aaron is 33%
//        	aShot = (int) (Math.random() * 100);
//        	if (aShot < 33)
//          	{
//            	name.setAlive(false);    
//          	}
//        	else
//           	{
//            	name.setAlive(true);
//           	}
//           	break;
//		}
//	}

```

---

### Post by dwhitney67 on 2009-04-02
I did a quick spot-check of the code, but I could not find anything.  Maybe later I can copy/paste it, compile it, then see if I can determine why it fails to meet your requirements.

Btw, never make a statement like:
> 
Just means I probably won't get credit/honors, but then I won't get a headache either. So a pass is fine.

If you do not care enough about the quality of your work, then no one else will either... well, maybe the exception of the person grading your work.

The adding of the 'aHit' boolean was not necessary; there are no injuries in this game, but only two states:  alive and dead.

You could have made the game more flexible to support more than 3 Duelers, without the convoluted if-else checks as seen in the main() function.  When a Dueler has its turn to shoot, it will always have combat with the "strongest" remaining survivor.  That was one of the hints given to you in the problem description.

A quick check of an array, or a list, of remaining survivors and their marksmanship proficiency will determine who will be the next target, bearing in mind that the shooter cannot shoot themselves... although that would be a funny bug.

When looking for the next shooter, just go through the list of duelers again... find the shooter that is still alive.  Then continue searching for the target that is still alive and who is the greatest marksman.  If no "alive" targets can be found, then a winner can be determined and the game is over!

P.S.  The words "array" and "list" do not necessary imply that you consider using these types of containers.  There are other types of containers that could be used.  Since it appears you have a hard-requirement to support only 3 Duelers, an array probably would suffice.

---

### Post by Garratt on 2009-04-02
> **dwhitney67 said:**
> I did a quick spot-check of the code, but I could not find anything.  Maybe later I can copy/paste it, compile it, then see if I can determine why it fails to meet your requirements.

Btw, never make a statement like:

If you do not care enough about the quality of your work, then no one else will either... well, maybe the exception of the person grading your work.

The adding of the 'aHit' boolean was not necessary; there are no injuries in this game, but only two states:  alive and dead.

You could have made the game more flexible to support more than 3 Duelers, without the convoluted if-else checks as seen in the main() function.  When a Dueler has its turn to shoot, it will always have combat with the "strongest" remaining survivor.  That was one of the hints given to you in the problem description.

A quick check of an array, or a list, of remaining survivors and their marksmanship proficiency will determine who will be the next target, bearing in mind that the shooter cannot shoot themselves... although that would be a funny bug.

When looking for the next shooter, just go through the list of duelers again... find the shooter that is still alive.  Then continue searching for the target that is still alive and who is the greatest marksman.  If no "alive" targets can be found, then a winner can be determined and the game is over!

P.S.  The words "array" and "list" do not necessary imply that you consider using these types of containers.  There are other types of containers that could be used.  Since it appears you have a hard-requirement to support only 3 Duelers, an array probably would suffice.

Yes I get that, but also if I take your advice, train of logic probe you to give the answers it's not my work... At least I'm trying to solve the problem myself using my own logic but with your help, which is a little different :P

While I would like to achieve the same result using the methods etc the instructor has asked us to and in turn get a credit/honor w/e, I have about 4 hours until I need to send this off as of now so...
The reason i added aHit variable was so i could pass that to main and then main could turn that into alive/dead I realize after reading your comments i could have easily just done that using alive and less if statements in main, but for the sake of making it my own I may as well stick with my own logic.

Also we are not up to arrays yet. While i have used them before, in java as well... probably best not getting too advanced.

There's probably many ways to do this and if i had the time I probably could have come up with a lot better logic, but I'm already writing the reports etc, being that its due in a couple hours unfortunately i don't have time to change it.

---

### Post by Garratt on 2009-04-02
forgot to reset turns... yay with 20minutes to spare :D :D :D :D

---

### Post by shadylookin on 2009-04-02
You're making life way more complicated than it needs to be. If you just pass the Dueler in shoot at target your life you can modify the Duelers directly without adding confusing extra variables. It won't matter for your grade now, but if your professor expects it then you might as well learn it because it won't get any easier as you go along.

---

