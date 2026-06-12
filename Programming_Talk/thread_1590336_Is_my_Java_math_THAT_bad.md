---
title: "Is my Java math THAT bad?"
date: 2010-10-07
forum: Programming Talk
---

### Post by Benchamoneh on 2010-10-07
I've been learning to use Java and have gotten as far as writing a simple application for a unit converter, however the end values are all wrong! I've heard that Java is bad a maths so I'm just wondering, is this bad logic on my part or Java? How would I go about fixing it? I've attached the code as well as copying it out here:
```
import java.util.Scanner;

public class converter {
	
	public static void main(String[] args) {
		
		// Values of different distance units. Base value is METERS
		final double MILLIMETERS = 1000;
		final double CENTIMETERS = 100;
		final double METERS = 1;
		final double KILOMETERS   = 0.001;
		
		// Values submitted by the user
		double valueIn;
		int unitType;
		
		// Used in calculation
		double baseValue;
		double[] valueOut = new double[4];
		
		// Take input from user
		Scanner sc = new Scanner(System.in);
		
		// Get the unit type from user
		System.out.print("Enter the base unit type:\n"+
				"  1. Millimeters\n"+
				"  2. Centimeters\n"+
				"  3. Meters\n"+
				"  4. Kilometers\n"+
				"Your selection (int): ");
		try {
			unitType = sc.nextInt();
		} catch (Exception e) {
			System.out.println("Unrecognised int, set to millimeters.");
			unitType = 1;
		}
		
		
		// Get the unit amount from user
		System.out.print("Enter the unit amount: ");
		try {
			valueIn = sc.nextDouble();
		} catch (Exception e) {
			System.out.println("Unrecognised double, set to 1.");
			valueIn = 1;
		}
		
		
		// Get the converted values (provided the valueIn is valid)
		if(valueIn != 0) {
			baseValue = 0;
			
			// Convert valueIn to METERS based on which value specified
			if (unitType==1) {
				baseValue = MILLIMETERS / valueIn;
			} else if (unitType==2) {
				baseValue = CENTIMETERS / valueIn;
			} else if (unitType==3) {
				baseValue = METERS / valueIn;
			} else if (unitType==4) {
				baseValue = KILOMETERS / valueIn;
			} else {
				System.out.println("Could not detect unit type:"+unitType);
			}
			
			//
			valueOut[0] = MILLIMETERS * baseValue;
			valueOut[1] = CENTIMETERS * baseValue;
			valueOut[2] = METERS * baseValue;
			valueOut[3] = KILOMETERS * baseValue;
		
		// If valueIn was 0
		} else {
			// Set all values to 0
			for (int i=0; i<valueOut.length; i++) {
				valueOut[i] = 0;
			}
		}
		
		// Output the converted values
		System.out.println("Millimeters value: "+valueOut[0]);
		System.out.println("Centimeters value: "+valueOut[1]);
		System.out.println("Meters value: "+valueOut[2]);
		System.out.println("Kilometers value: "+valueOut[3]);
		
		
	}
}
```
Feel free to correct my mistakes, but please remember - I'm new to this! :)

---

### Post by Some Penguin on 2010-10-07
It's you.  Your constants are 1/x over what they should be, and you're dividing where you should be multiplying.

---

### Post by Queue29 on 2010-10-07
Java is no worse at math than any other IEE-754 conforming language, which is pretty much all of them.

---

