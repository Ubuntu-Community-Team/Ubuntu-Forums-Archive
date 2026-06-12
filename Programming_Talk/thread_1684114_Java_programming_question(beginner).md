---
title: "Java programming question(beginner)"
date: 2011-02-08
forum: Programming Talk
---

### Post by copelandtml on 2011-02-08
I am coding a program that will figure out the amount of paint needed to paint a room. I have to subtract the sq. ft. of the windows and doors. Doors are going to a constant of 20 sq. ft. and windows are all different sizes so that input will be provided by the user. So if there is 1 window I will then ask for the height and width but if the user enters 0 for number of windows I do not want the height or width question to be asked. How would I go about doing that?

---

### Post by worksofcraft on 2011-02-08
> **copelandtml said:**
> I am coding a program that will figure out the amount of paint needed to paint a room. I have to subtract the sq. ft. of the windows and doors. Doors are going to a constant of 20 sq. ft. and windows are all different sizes so that input will be provided by the user. So if there is 1 window I will then ask for the height and width but if the user enters 0 for number of windows I do not want the height or width question to be asked. How would I go about doing that?

If you put the question in the window constructor then it only asks it for each window object you create, so...

simply ask how many windows and then create an array of that many and it will call the constructor for each window... IDK if Java lets you make 0 length arrays. If not you might have to put an if statement in there to test > 0 before making the array.

---

### Post by copelandtml on 2011-02-08
Is there a way of doing this without using arrays just an if statement?

---

### Post by GregBrannon on 2011-02-08
You need this program because you're a painter, right?  Or you work for a general contractor who needs your help figuring out how much paint to buy?  Say, "Yes."

Yes, you can program what you've described using 'if' statements, but you might need some other statements, too.  I suggest you make an effort.  Write the code using what you know, and then ask for help when you need it.

When you come back for help, show what you've coded and describe what you need help with, including any error messages or problems with the way the code works (or doesn't).

---

### Post by cgroza on 2011-02-08
Why not just check if it is 0  and do the rest of the operations.

---

### Post by copelandtml on 2011-02-08
Yes!

And here is what I have so far:
/**
Program Name: HowMuchPaint.java
Purpose:
Coder:
Date:
 */
import java.util.Scanner;

public class HowMuchPaint {
	public static void main(String[] args) {
		
	//create Scanner
	Scanner input = new Scanner(System.in);
	
	//create variables
	String roomName;
	double widthOfRoom;
	double lengthOfRoom;
	double heightOfRoom;
	int numberOfDoors;
	int numberOfWindows;
	double widthOfWindow = 0;
	double heightOfWindow = 0;
	double surfaceArea;
	final double AREA_OF_DOOR = 20;
	double totalSurfaceArea;
	double windowsAndDoorsArea;
	double gallonsOfPaint;
	int numberOfCans;
	
	//title
	System.out.println("*** PAINT USAGE CALCULATOR ***");
	System.out.println("--------------------------------------");
	
	//ask user for room name
	System.out.print("Enter a short description for the room (enter 'quit' to exit program):");
	roomName = input.nextLine();
	///////////////(having trouble here trying to get the program to exit when quit is entered)
	
	//ask user for room dimensions
	System.out.println("Enter the room dimensions in feet.");
	System.out.print("	Width:");
	widthOfRoom = input.nextDouble();
	System.out.print("	Length:");
	lengthOfRoom = input.nextDouble();
	System.out.print("	Height:");
	heightOfRoom = input.nextDouble();
	
	//ask user for number of doors
	System.out.print("Enter the number of doors in the room:");
	numberOfDoors = input.nextInt();
	
	//ask user for number of windows and window dimensions
	System.out.print("Enter the number of windows in the room:");
	numberOfWindows = input.nextInt();
	
	////////////(having trouble with this) - window dimensions if number of windows is not blank
	
	//ask user for surface are that can be painted
	System.out.print("Enter the surface area in sq. ft. that can be painted with a can of paint:");
	surfaceArea = input.nextDouble();
	
	//calculations
	//area of windows and doors
	windowsAndDoorsArea = (widthOfWindow * heightOfWindow) + AREA_OF_DOOR;
	//total surface area to be painted
	totalSurfaceArea = surfaceArea + windowsAndDoorsArea;
	//gallons of paint needed
	gallonsOfPaint = totalSurfaceArea / 250;
	//number of cans needed
	//////////////(also having trouble with this)numberOfCans = (int) Math.ceil(totalSurfaceArea); 
	
	//print out
	System.out.println("The surface area to be painted is "+ totalSurfaceArea +" sq. ft.");
	System.out.println("To paint the "+ roomName +" "+ gallonsOfPaint +" or "+ numberOfCans +" cans of paint are required");
	
	}//end main
}//end class





Thanks for the help!!

---

### Post by GregBrannon on 2011-02-08
```
//ask user for room name
System.out.print("Enter a short description for the room (enter 'quit' to exit program):");
roomName = input.nextLine();
///////////////(having trouble here trying to get the program to exit when quit is entered)
```

Use code tags when you enter code.  Either type them or use the # editor tool.

For this problem, you could use an if statement:

```

    if( roomName.equals( "quit" )
    {
        System.exit(0);
    }

```

I don't understand your problem comment at the number of windows part, but I think you could use a for statement that will get the window dimensions for each window.  Since you don't use arrays, you can total the window area as you calculate them, something like:

pseudo code:

```

get number of windows
for the number of windows
{
    get window dimensions
    windowArea += ( w * h );
}

```

And the number of cans needed is (total paintable surface area of the room in square feet) / (the square feet of coverage in a can)

If you calculate 500 square feet of paintable surface area in the room and each can of paint covers 250 square feet, then you need 2 cans of paint.

---

### Post by copelandtml on 2011-02-08
Sorry code tags will be used next time and thanks for the feedback, i`ll give that stuff a try!!!

---

