---
title: "Java help"
date: 2008-10-05
forum: Programming Talk
---

### Post by Bon Mots on 2008-10-05
I am doing a mini-project using java to determine the cost of a speeding ticket:

```
// Import of scanner
import java.util.Scanner;

public class SpeedingTicket 
{
	public static void main(String[] args) 
	{
		// Cost of each fee (Constants)
		final int MIN_FEE = 50;
		final int SCHOOL_FEE = 12;
		final int NORMAL_FEE = 6;
		final int SPEED_THRESHOLD = 30;
		final int SUPER_SPEEDING = 150;		
		
		// Input data
		Scanner scan = new Scanner(System.in);
		
		System.out.print("Enter driver's name: ");
		String driverName = scan.nextLine();
		
		System.out.print("Enter driver's speed: ");
		int driverSpeed = scan.nextInt();
		
		System.out.print("Enter speed limit: ");
		int speedLimit = scan.nextInt();
		
		System.out.print("Was driver in school zone: ");
		String schoolZone = scan.next();
		
		System.out.println();		
		
		// Calculation of speeding ticket cost
	 	int baseFee = MIN_FEE;
                int schoolSpeeding = SCHOOL_FEE * (driverSpeed - speedLimit);
                int normalSpeeding = NORMAL_FEE * (driverSpeed - speedLimit);
                int superSpeeding = SUPER_SPEEDING;
                
		if (driverSpeed > speedLimit)
		{
       		baseFee = MIN_FEE;
                }
		
		String yes = new String("yes");
		if (schoolZone.equalsIgnoreCase(yes))
		{
			schoolSpeeding = SCHOOL_FEE * (driverSpeed - speedLimit);
		}
		else
		{
			normalSpeeding = NORMAL_FEE * (driverSpeed - speedLimit);
		}
		
		if (driverSpeed > (speedLimit + SPEED_THRESHOLD))
		{
			superSpeeding = SUPER_SPEEDING;
		}
				
		// Display of speeding ticket information
		System.out.printf("Speed traveled:  %-3d \n", driverSpeed);
		System.out.printf("Speed limit:     %-6d \n", speedLimit);
		System.out.printf("In school zone:  %-3s \n", schoolZone);
		System.out.print(driverName + " owes $"); 
                System.out.println(baseFee + schoolSpeeding + normalSpeeding + superSpeeding);
                System.out.println();
				
	}
}		
```

That's the code, however, once it's run and values are inputed, the output of the total ticket price does not make sense. Can anyone help?

---

### Post by kjohansen on 2008-10-05
the last if statement makes no sense.  you declare the value of the schoolspeeding outside of the if and then redclare it.

also you are summing up all of the costs even if they arent true.  you need to keep a running total and only add that up.

Try the below:

```

final int MIN_FEE = 50;
		final int SCHOOL_FEE = 12;
		final int NORMAL_FEE = 6;
		final int SPEED_THRESHOLD = 30;
		final int SUPER_SPEEDING = 150;		
		
		// Input data
		Scanner scan = new Scanner(System.in);
		
		System.out.print("Enter driver's name: ");
		String driverName = scan.nextLine();
		
		System.out.print("Enter driver's speed: ");
		int driverSpeed = scan.nextInt();
		
		System.out.print("Enter speed limit: ");
		int speedLimit = scan.nextInt();
		
		System.out.print("Was driver in school zone: ");
		String schoolZone = scan.next();
		
		System.out.println();		
		
		// Calculation of speeding ticket cost
	 	int baseFee = MIN_FEE;
                int schoolSpeeding = SCHOOL_FEE * (driverSpeed - speedLimit);
                int normalSpeeding = NORMAL_FEE * (driverSpeed - speedLimit);
                int superSpeeding = SUPER_SPEEDING;
                int runningTotal=0;
                
                
		if (driverSpeed > speedLimit)
		{
       		baseFee = MIN_FEE;
                }
		
		String yes = new String("yes");
		if (schoolZone.equalsIgnoreCase(yes))
		{
			runningTotal+=schoolSpeeding;
		}
		else
		{
			runningTotal+=normalSpeeding;
		}
		
		if (driverSpeed > (speedLimit + SPEED_THRESHOLD))
		{
			runningTotal+=superSpeeding;
		}
				
		// Display of speeding ticket information
		System.out.printf("Speed traveled:  %-3d \n", driverSpeed);
		System.out.printf("Speed limit:     %-6d \n", speedLimit);
		System.out.printf("In school zone:  %-3s \n", schoolZone);
		System.out.print(driverName + " owes $"); 
                System.out.println(baseFee + runningTotal);
                System.out.println();

```

---

### Post by zhuxiaonuan on 2008-10-05
:guitar:
[ultrasound gel]("http://www.xinyangmed.net")

---

### Post by bapoumba on 2008-10-06
Moved from "Education and Sciences" to "Programming Talk".

---

### Post by drubin on 2008-10-06
> **kjohansen said:**
> the last if statement makes no sense.  you declare the value of the schoolspeeding outside of the if and then redclare it.

This is not called redeclaring, it is re-assigning. There is a difference. This can leed to confusing about vars having the incorrect values due to scope of visibility. 

as for the program out putting the incorrect restults? Do you want the drivers owe value equal to the sum of all those results? or just list those fines?

---

### Post by leg on 2008-10-06
Show us what value you are getting for an input. I have agree with the first reply in that it looks like you are adding up everything regardless of what the circumstances are.

As an aside why do you bother to create a String object to use in your comparison with SchoolZone. 
```
schoolZone.equalsIgnoreCase("yes")
```would work just as well and you wouldn't create a new string object on the heap for no reason.

anyway post some figures.

---

### Post by leg on 2008-10-06
Tried it with speed travelled = 70 speed limit = 50 shool zone = no and I was told I owed $560. You are adding up everything even if it doesn't applly. declare yourself a running total variable and add to it inside the if statements.

You do also seem to be unnecessarily re-initialising your variables.
```
// Calculation of speeding ticket cost
int baseFee = MIN_FEE;
int schoolSpeeding = SCHOOL_FEE * (driverSpeed - speedLimit);
int normalSpeeding = NORMAL_FEE * (driverSpeed - speedLimit);
int superSpeeding = SUPER_SPEEDING;

```

and then you set the values to be the same inside your if statements.

Do something like
```

if (schoolZone.equalsIgnoreCase("yes"))
{
     totalFine += SCHOOL_FEE * (driverSpeed - speedLimit);
}

```

Just like kjohansen said.

---

### Post by tinny on 2008-10-06
This thread has your answer...

[http://ubuntuforums.org/showthread.php?t=717011](http://ubuntuforums.org/showthread.php?t=717011)

---

### Post by drubin on 2008-10-06
> **tinny said:**
> This thread has your answer...

[http://ubuntuforums.org/showthread.php?t=717011](http://ubuntuforums.org/showthread.php?t=717011)

The OP is not asking us to do the home work only to point out why it is not working. I consider this more of a learning thread then a giveme_i_want_now thread :)

---

