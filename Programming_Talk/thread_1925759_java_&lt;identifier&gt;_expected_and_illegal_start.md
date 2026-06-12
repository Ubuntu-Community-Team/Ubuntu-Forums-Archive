---
title: "java &lt;identifier&gt; expected and illegal start of type"
date: 2012-02-15
forum: Programming Talk
---

### Post by stephanie904 on 2012-02-15
Im having trouble finding out what is wrong with the code that I have already made...what does this mean ? its gives me this message: Can someone help ?

HealthProfileTest.java:14: <identifier> expected
		System.out.println("Welcome to the Health Profile!");
		                  ^
HealthProfileTest.java:14: illegal start of type
		System.out.println("Welcome to the Health Profile!");



```


import javax.swing.*;



public class HealthProfileTest
{
	public static void main(String[] args) {
}

		// Welcome message
		Scanner in = new Scanner(System.in);
		System.out.println("Welcome to the Health Profile!");
		System.out.println("Please enter your information when prompted.\n");

		

		
		// Promt and obtain user input
		System.out.println("First name: ");
	   String fname = in.readLine();
		
		System.out.println("Last name: ");
		String lName = in.readLine();
		
		System.out.println("Gender: ");
		String pGender = in.readLine();
		
		System.out.println("Year of birth: ");
		int year = Convert.ToInt32(in.readLine());
		
		System.out.println("Month of birth: ");
		int month = Convert.ToInt32(in.readLine());
		
		System.out.println("Day of birth: ");
		int day = Convert.ToInt32(in.readLine());
		
		System.out.println("Height in meters: ");
		double pHeight = Convert.ToDouble(in.readLine());
		
		System.out.println("Weight in kilos: ");
		double pWeight = Convert.ToDouble(in.readLine());
		
		// Create a HealthProfile object
		HealthProfile myHealthProfile = new HealthProfile(fName, lName, pGender, year, 
		                                                  month, day, pHeight, pWeight);
		
		// Print the information from object myHealthProfile
		System.out.println("\nInformation inserted to your health profile:");
		System.out.println("Name: \t\t\t{0} {1}", myHealthProfile.FirstName, myHealthProfile.LastName);
		System.out.println("Gender: \t\t{0}", myHealthProfile.Gender);
		System.out.println("Date of birth: \t\t{0}-{1:00}-{2:00}", 
		                  myHealthProfile.BirthYear, myHealthProfile.BirthMonth, myHealthProfile.BirthDay);
		System.out.println("Height: \t\t{0}", myHealthProfile.Height);
		System.out.println("Weight: \t\t{0}", myHealthProfile.Weight);
		
		// Call method PersonAge to calculate the persons age
		System.out.println("\nWe will now print out your age, BMI, maximum heart " +
			"rate \nand target heart rate range:");
		System.out.println("Your age: \t\t\t{0}", myHealthProfile.PersonAge());
		System.out.println("Your BMI: \t\t\t{0}", myHealthProfile.BodyMassIndex());
		System.out.println("Your maximum heart rate: \t{0}", myHealthProfile.MaxRate());
		System.out.println("Your target heart rate range: \t{0} to {1}", myHealthProfile.MinTarget(), myHealthProfile.MaxTarget());
		
		System.out.println ("\n\nBMI VALUES\nUnderweight:\tless than 18.5\nNormal:\tbetween 18.5 and 24.9");
		System.out.println ("\nUnderweight:\tless than 18.5");
		System.out.println ("Normal:\t\tbetween 18.5 and 24.9");
		System.out.println("Overweight:\tbetween 25 and 29.9");
		System.out.println ("Obese:\t\tbetween 30 or greater");
	}
}


```

---

### Post by muteXe on 2012-02-15
is it just for the first two println lines? Or all of them?

---

### Post by stephanie904 on 2012-02-15
On all of the System.out.println

am i missing something ? im confused

---

### Post by ofnuts on 2012-02-15
> **stephanie904 said:**
> On all of the System.out.println

am i missing something ? im confusedYour codes starts with
```

public class HealthProfileTest {     
      public static void main(String[] args) { 
} 

```So most of your code is outside main(). Variable declarations are OK (there are seen as default initializations of attributes, but "naked" function calls are not...

So remove that extra closing brace.

---

### Post by muteXe on 2012-02-15
good spot.
i hate incorrect indentation :(

---

### Post by stephanie904 on 2012-02-15
> **ofnuts said:**
> Your codes starts with
```

public class HealthProfileTest {     
      public static void main(String[] args) { 
} 

```So most of your code is outside main(). Variable declarations are OK (there are seen as default initializations of attributes, but "naked" function calls are not...

So remove that extra closing brace.



i have tried it 

what exactly did you mean ?

sorry im dumb :(

---

### Post by muteXe on 2012-02-15
```

import javax.swing.*;



public class HealthProfileTest
{
	public static void main(String[] args) {
}  <== REMOVE THIS BRACE

		// Welcome message
		Scanner in = new Scanner(System.in);
		System.out.println("Welcome to the Health Profile!");
		System.out.println("Please enter your information when prompted.\n");

		

		
		// Promt and obtain user input
		System.out.println("First name: ");
	   String fname = in.readLine();
		
		System.out.println("Last name: ");
		String lName = in.readLine();
		
		System.out.println("Gender: ");
		String pGender = in.readLine();
		
		System.out.println("Year of birth: ");
		int year = Convert.ToInt32(in.readLine());
		
		System.out.println("Month of birth: ");
		int month = Convert.ToInt32(in.readLine());
		
		System.out.println("Day of birth: ");
		int day = Convert.ToInt32(in.readLine());
		
		System.out.println("Height in meters: ");
		double pHeight = Convert.ToDouble(in.readLine());
		
		System.out.println("Weight in kilos: ");
		double pWeight = Convert.ToDouble(in.readLine());
		
		// Create a HealthProfile object
		HealthProfile myHealthProfile = new HealthProfile(fName, lName, pGender, year, 
		                                                  month, day, pHeight, pWeight);
		
		// Print the information from object myHealthProfile
		System.out.println("\nInformation inserted to your health profile:");
		System.out.println("Name: \t\t\t{0} {1}", myHealthProfile.FirstName, myHealthProfile.LastName);
		System.out.println("Gender: \t\t{0}", myHealthProfile.Gender);
		System.out.println("Date of birth: \t\t{0}-{1:00}-{2:00}", 
		                  myHealthProfile.BirthYear, myHealthProfile.BirthMonth, myHealthProfile.BirthDay);
		System.out.println("Height: \t\t{0}", myHealthProfile.Height);
		System.out.println("Weight: \t\t{0}", myHealthProfile.Weight);
		
		// Call method PersonAge to calculate the persons age
		System.out.println("\nWe will now print out your age, BMI, maximum heart " +
			"rate \nand target heart rate range:");
		System.out.println("Your age: \t\t\t{0}", myHealthProfile.PersonAge());
		System.out.println("Your BMI: \t\t\t{0}", myHealthProfile.BodyMassIndex());
		System.out.println("Your maximum heart rate: \t{0}", myHealthProfile.MaxRate());
		System.out.println("Your target heart rate range: \t{0} to {1}", myHealthProfile.MinTarget(), myHealthProfile.MaxTarget());
		
		System.out.println ("\n\nBMI VALUES\nUnderweight:\tless than 18.5\nNormal:\tbetween 18.5 and 24.9");
		System.out.println ("\nUnderweight:\tless than 18.5");
		System.out.println ("Normal:\t\tbetween 18.5 and 24.9");
		System.out.println("Overweight:\tbetween 25 and 29.9");
		System.out.println ("Obese:\t\tbetween 30 or greater");
	}
}

```

---

### Post by stephanie904 on 2012-02-15
```
import java.util.Scanner;
import javax.swing.*;



public class HealthProfileTest
{
	public static void main(String[] args) }


		// Welcome message
		Scanner in = new Scanner(System.in);
		System.out.println("Welcome to the Health Profile!");
		System.out.println("Please enter your information when prompted.\n");

		

		
		// Promt and obtain user input
		System.out.println("First name: ");
	   String fname = in.readLine();
		
		System.out.println("Last name: ");
		String lName = in.readLine();
		
		System.out.println("Gender: ");
		String pGender = in.readLine();
		
		System.out.println("Year of birth: ");
		int year = Convert.ToInt32(in.readLine());
		
		System.out.println("Month of birth: ");
		int month = Convert.ToInt32(in.readLine());
		
		System.out.println("Day of birth: ");
		int day = Convert.ToInt32(in.readLine());
		
		System.out.println("Height in meters: ");
		double pHeight = Convert.ToDouble(in.readLine());
		
		System.out.println("Weight in kilos: ");
		double pWeight = Convert.ToDouble(in.readLine());
		
		// Create a HealthProfile object
		HealthProfile myHealthProfile = new HealthProfile(fName, lName, pGender, year, 
		                                                  month, day, pHeight, pWeight);
		
		// Print the information from object myHealthProfile
		System.out.println("\nInformation inserted to your health profile:");
		System.out.println("Name: \t\t\t{0} {1}", myHealthProfile.FirstName, myHealthProfile.LastName);
		System.out.println("Gender: \t\t{0}", myHealthProfile.Gender);
		System.out.println("Date of birth: \t\t{0}-{1:00}-{2:00}", 
		                  myHealthProfile.BirthYear, myHealthProfile.BirthMonth, myHealthProfile.BirthDay);
		System.out.println("Height: \t\t{0}", myHealthProfile.Height);
		System.out.println("Weight: \t\t{0}", myHealthProfile.Weight);
		
		// Call method PersonAge to calculate the persons age
		System.out.println("\nWe will now print out your age, BMI, maximum heart " +
			"rate \nand target heart rate range:");
		System.out.println("Your age: \t\t\t{0}", myHealthProfile.PersonAge());
		System.out.println("Your BMI: \t\t\t{0}", myHealthProfile.BodyMassIndex());
		System.out.println("Your maximum heart rate: \t{0}", myHealthProfile.MaxRate());
		System.out.println("Your target heart rate range: \t{0} to {1}", myHealthProfile.MinTarget(), myHealthProfile.MaxTarget());
		
		System.out.println ("\n\nBMI VALUES\nUnderweight:\tless than 18.5\nNormal:\tbetween 18.5 and 24.9");
		System.out.println ("\nUnderweight:\tless than 18.5");
		System.out.println ("Normal:\t\tbetween 18.5 and 24.9");
		System.out.println("Overweight:\tbetween 25 and 29.9");
		System.out.println ("Obese:\t\tbetween 30 or greater");
	}
}
```


thanks, ok i fixed the main method :)


why does it tell me that it cannot find symbol ?? i have import java.util.Scanner;

---

### Post by doobrie on 2012-02-15
What's the error message?  What symbol can't it find?

---

### Post by ofnuts on 2012-02-15
> **stephanie904 said:**
> thanks, ok i fixed the main method :)
No you didn't, you have a wrong brace:
```

public class HealthProfileTest
{
    public static void main(String[] args) }  <-------- should be "{" not "}"
    ....

}

```

---

### Post by muteXe on 2012-02-15
arggggh

---

### Post by stephanie904 on 2012-02-15
hey thanks everyone 

I fixed Scanner readLine() to nextLine() but it doesnt work for Convert.ToDouble(in.nextLine()) which gives me this message ?


HealthProfileTest.java:41: cannot find symbol
symbol  : variable Convert
location: class HealthProfileTest
		double pHeight = Convert.ToDouble(in.nextLine());

```
import java.util.Scanner;
import javax.swing.*;



public class HealthProfileTest
{
	public static void main(String[] args) 
	{


		// Welcome message
		Scanner in = new Scanner(System.in);
		System.out.println("Welcome to the Health Profile!");
		System.out.println("Please enter your information when prompted.\n");

		

		
		// Promt and obtain user input
		System.out.println("First name: ");
      String fName = in.nextLine();
		
		System.out.println("Last name: ");
		String lName = in.nextLine();
		
		System.out.println("Gender: ");
		String pGender = in.nextLine();
		
		System.out.println("Year of birth: ");
		int year = Convert.ToInt32(in.nextLine());
		
		System.out.println("Month of birth: ");
		int month = Convert.ToInt32(in.nextLine());
		
		System.out.println("Day of birth: ");
		int day = Convert.ToInt32(in.nextLine());
		
		System.out.println("Height in meters: ");
		double pHeight = Convert.ToDouble(in.nextLine());
		
		System.out.println("Weight in kilos: ");
		double pWeight = Convert.ToDouble(in.nextLine());
		
		// Create a HealthProfile object
		HealthProfile myHealthProfile = new HealthProfile(fName, lName, pGender, year, 
		                                                  month, day, pHeight, pWeight);
		
		// Print the information from object myHealthProfile
		System.out.println("\nInformation inserted to your health profile:");
		System.out.println("Name: \t\t\t{0} {1}", myHealthProfile.FirstName, myHealthProfile.LastName);
		System.out.println("Gender: \t\t{0}", myHealthProfile.Gender);
		System.out.println("Date of birth: \t\t{0}-{1:00}-{2:00}", 
		                  myHealthProfile.BirthYear, myHealthProfile.BirthMonth, myHealthProfile.BirthDay);
		System.out.println("Height: \t\t{0}", myHealthProfile.Height);
		System.out.println("Weight: \t\t{0}", myHealthProfile.Weight);
		
		// Call method PersonAge to calculate the persons age
		System.out.println("\nWe will now print out your age, BMI, maximum heart " +
			"rate \nand target heart rate range:");
		System.out.println("Your age: \t\t\t{0}", myHealthProfile.PersonAge());
		System.out.println("Your BMI: \t\t\t{0}", myHealthProfile.BodyMassIndex());
		System.out.println("Your maximum heart rate: \t{0}", myHealthProfile.MaxRate());
		System.out.println("Your target heart rate range: \t{0} to {1}", myHealthProfile.MinTarget(), myHealthProfile.MaxTarget());
		
		System.out.println ("\n\nBMI VALUES\nUnderweight:\tless than 18.5\nNormal:\tbetween 18.5 and 24.9");
		System.out.println ("\nUnderweight:\tless than 18.5");
		System.out.println ("Normal:\t\tbetween 18.5 and 24.9");
		System.out.println("Overweight:\tbetween 25 and 29.9");
		System.out.println ("Obese:\t\tbetween 30 or greater");
	}

}



```

---

### Post by dwhitney67 on 2012-02-15
> **stephanie904 said:**
> hey thanks everyone 

I fixed Scanner readLine() to nextLine() but it doesnt work for Convert.ToDouble(in.nextLine()) which gives me this message ?


HealthProfileTest.java:41: cannot find symbol
symbol  : variable Convert
location: class HealthProfileTest
		double pHeight = Convert.ToDouble(in.nextLine());


What part of "cannot find symbol" is impeding you from understanding that the variable Convert is not defined within your program?

There is no class available in the Java API called Convert, so if you have not defined this class, naturally you will get compile errors.

Perhaps you meant to use the "parse" suite of methods that are available with Integer, Double, etc.

For example:
```

String yearAsString = "2008";

int yearAsInteger = Integer.parseInt(yearAsString);

```

It also appears that you will have additional issues with your code since it appears that you have not defined the constructor for HealthProfile.  Perhaps you have it defined within another .java module?

---

