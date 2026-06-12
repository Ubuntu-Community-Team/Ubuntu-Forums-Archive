---
title: "Java Vector Object Help"
date: 2009-04-20
forum: Programming Talk
---

### Post by mikemcleanuk on 2009-04-20
Hey im trying to complete some basic java questions and i have become stumped. I am trying to run an method of an object that is stored in a Vector. Below is my code:

```
class KillerRobot
{
	String name, mainWeapon;
	int numberOfKills;
	
	KillerRobot(String n, String mw, int k)
	{	
		name = n;
		mainWeapon = mw;
		numberOfKills = k;
	}

	void robotSummary()
	{
		System.out.println("The Robot" + name + " uses a " + mainWeapon + " and has " + numberOfKills + " total kills.");		
	}
}

```


```
import java.util.Vector;
import java.util.Scanner;

public class TestVector2
{
	public static void main(String[] args) 
	{
		Scanner myInput = new Scanner(System.in);
		
		String name ="", mainWeapon;
		int numberOfKills;
		Vector <Object> robotCollection = new Vector <Object>();
		
		while (!name.equals("Q"))
		{
			System.out.println("Please enter the name of the Killer Robot or Q to finish.");
			name = myInput.next();
			if(!name.equals("Q"))
			{
				System.out.print("Robot Weapon: ");
				mainWeapon = myInput.next();
				System.out.print("Robot Kills: ");
				numberOfKills = myInput.nextInt();

				KillerRobot robot = new KillerRobot(name, mainWeapon, numberOfKills);
				robotCollection.add(robot);
			}
		}	
		
		for(Object robots : robotCollection)
		{
			robots.robotSummary();
		}
	}
}

```

I am getting the following error on compile:

> C:\JPR\Lab13>javac TestVector2.java
TestVector2.java:32: cannot find symbol
symbol  : method robotSummary()
location: class java.lang.Object
                        robots.robotSummary();
                              ^
1 error

Any help would be apprechiated.

Thanks
Mike

---

### Post by simeon87 on 2009-04-20
The line with the problem:

```

for(Object robots : robotCollection)
		{
			robots.robotSummary();
		}

```

Earlier, you're adding objects of the class KillerRobot to robotCollection but you're using Object when you're walking over this collection. This means Java thinks it's an arbitrary Object so you can only use methods of the class Object. The method robotSummary is part of the KillerRobot class so if you want Java to recognize that the method robotSummary is available, you'll need to change Object to KillerRobot in this for loop. This also means you need to change the declaration of the collection:

```

Vector <Object> robotCollection = new Vector <Object>();

```

becomes:

```

Vector <KillerRobot> robotCollection = new Vector <KillerRobot>();

```

Also, the Vector class is a bit outdated; it's more common to use ArrayList for this.

---

### Post by mikemcleanuk on 2009-04-20
thanks that fixed it

---

