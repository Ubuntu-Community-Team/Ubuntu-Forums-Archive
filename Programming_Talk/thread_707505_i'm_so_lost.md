---
title: "i'm so lost"
date: 2008-02-25
forum: Programming Talk
---

### Post by Bossco30 on 2008-02-25
I'm taking java (first year) and I'm so lost now. I understood the other things that the Prof was talking about but not now. 

Any how...I have to make a constructor and a tester. Well I thought I was on the right track till now. I can't figure out where to go or find any good examples in  my book or online

I hope someone here and lend out an helping hand

(this is what I got as my constructor)
```

public class MealClass
{
    private final float Appetizer_Cost = 3.25F;      // Declare and set APPETIZER constant
	private final float Entree_Cost = 10.75F;       // Declare and set ENTREE constant
	private final float Dessert_Cost = 4.50F;       // Declare and set DESSERT constant
	private final float Drink_Cost = 1.20F;        // Declare and set DRINK constant
	private final float Meal_Cost =(Appetizer_Cost + Entree_Cost + Dessert_Cost + Drink_Cost ); //Delcare the whole cost
	private final float Tax = .09F;                 // Declare and set TAX constant
	private final float MealCostWithTax = (Meal_Cost * Tax); //Declare the meal cost with  tax
	private final float Tip = .15F;                 // Declare and set TIP constant
	private final float OverallmealCost = (Meal_Cost * Tax *  Tip);



	private String tableNumber;
	private int numberOfPersonsDining;
	private int numberOfDrinks;
	 
	
	
	public MealClass(String Table, int Person, int Drinks)
	{
		Table = tableNumber;
		 Person = numberOfPersonsDining;
		Drinks = numberOfDrinks;
	}
	
	  //sets the input of the number of drinks
	  public void setNumberOfDrinks (int Drinks)
	  {
		numberOfDrinks = Drinks;
	  }
		
	  //
	  public void setNumberOfPersonDining (int Person)
	  {
	    numberOfPersonsDining = Person;
	  }
	  
	  //
	  public void setTableNumber (String Table)
	  {
	     tableNumber = Table;
		 
	  }
	  
	  float setDrink_Cost()
	  {
	    return 1.20f * numberOfDrinks;
	  }
	  //
	  public int getDrinks()
	  {
	    return numberOfDrinks;
	  }
	  
	  //
	  public int getPerson()
	  {
	    return numberOfPersonsDining;
	  }
	  
	  //
	  public String getTable()
	  {
	    return tableNumber;
	  }
	  
	  
	  
	  //
	  
}

```


(and this is my tester which is wroking kinda of)

```

import java.util.Scanner; //needed for the scanner class
import java.text.DecimalFormat; //needed for the decimal class

/**  
  * This program use the mealclass class
  *to calculate an tables bill
  */
  
  public class MealTest
  {
	 
	public static void main(String[] args)
	{
		int Person;        // to hold the number of people dining
		int Drinks;        // to hold the number of drinks
		tring Table;        // to hold the table number
		
		
		//creates a Scanner oblect to read read input .
		Scanner keyboard = new Scanner(System.in);
		
		// Gets the table number
		System.out.println("Enter the table number");
		Table = keyboard.nextString();
		//gets the number people dining
		System.out.println("Enter the number of persons dining");
		Person = keyboard.nextInt();
		// gets the number of drinks
		System.out.println("Enter the number of drinks");
		Drinks = keyboard.nextInt();
		
		
		//sends out the table number 
		System.out.println("Table number              :        " + Table);
		
		//sends the number of persons dining
		System.out.println("Number of persons dining  :        " + Person);
		
		//sends the number of drinks 
		System.out.println("Number of drinks          :        " + Drinks);
		
		// send out the drink total 
		
		//sends out the drink total
		System.out.println("Drink cost                :        " + Drinks * setDrink_Cost);
		
}		
	}	

```


Any help or guides online anything to help me resolve this would be great

---

### Post by skeeterbug on 2008-02-25
```
public MealClass(String Table, int Person, int Drinks)
{
Table = tableNumber;
Person = numberOfPersonsDining;
Drinks = numberOfDrinks;
}
```


Should be

```
public MealClass(String Table, int Person, int Drinks)
{
tableNumber = Table;
numberOfPersonsDining = Person;
 numberOfDrinks = Drinks;
}
```

Your constructor does not set the member variables correctly.


EDIT:

I also don't see where you are even using the MealClass in Main(). You should be collecting the keyboard input from the user, and passing it into the MealClass like so:

```

MealClass meal = new MealClass(Table, Person, Drinks);

//sends out the drink total
System.out.println("Drink cost : " + meal.setDrink_Cost());

```

---

### Post by Bossco30 on 2008-02-25
Thank you for the info I'm going to try it out

---

### Post by rendon on 2008-02-26
Bossco30,

I can see by your code that you are not understanding the concept of the constructor, this is the important thing.  Or perhaps you do "understand" but don't understand the "implementation" of it.

lets shorten the code first

```


// here is the class
public class MealClass
{

        //here are my private variables
	private String tableNumber;
	private int numberOfPersonsDining;
	private int numberOfDrinks;

	// here is the constructor
	public MealClass(String TABLE, int PERSON, int DRINKS)
	{
		tableNumber = TABLE;
		numberOfPersonsDining = PERSON;
		numberOfDrinks = DRINKS;
	}

}

```

skeeterbug is right, you got your constructor arguments mixed up with your private variables.

The 'arguments' are going to be passed to the class when you make a new class.  Remember, the reason we make classes is so that we can call them again and again, and they will do some job for us over and over, so the programmer doesn't get tired typing the same code over and over.

In this your class is saving some information (tableNumber, numberOfPersonsDining, and numberOfDrinks) which we can refer to later.

So when you make a new class like this:
(excuse my psuedo code, I haven't used Java in a long time)
```

MealClass CUSTOMER = new MealClass("3",2,2);

```

now you have a new MealClass which you called CUSTOMER, and CUSTOMER has these 3 variables saved in it ("3",2,2);

these variables:
```

	private String tableNumber;
	private int numberOfPersonsDining;
	private int numberOfDrinks;

```

are the variables that will save the information, so when you call the constructor, you will set THEM not the arguments.

These are the arguments:
```

	// here is the constructor
	public MealClass(String TABLE, int PERSON, int DRINKS)

```

They are just temporary variables that will "pass" the information to the private variables which save the information in the class.

Now that the information is saved in the 3 private variables, you can get the information with these three functions:
```

          public int getDrinks()
	  {
	    return numberOfDrinks;
	  }
	  
	  //
	  public int getPerson()
	  {
	    return numberOfPersonsDining;
	  }
	  
	  //
	  public String getTable()
	  {
	    return tableNumber;
	  }

```

by stating:

```

String table = CUSTOMER.getTable();
int person = CUSTOMER.getPerson();
int drinks = CUSTOMER.getDrinks();

```

Because these functions are returning the values of the variables which saved your info in the constructor.


I don't understand why your tester is calling the class Scanner instead of MealClass, and why your tester has the same name as your class... but that maybe just because I don't know this aspect of Java, or I don't know your project too well.

I hope my input about the constructor usage was helpful.

I will also tell you that with this current code I believe you MUST insert the numbers when you call the class like this:

```

MealClass CUSTOMER = new MealClass("3",2,2);  // or some other numbers...

```

(at least that's how I recall things when I used Java)

because you only have 1 constructor. and that constructor requires these variables.  If you want to call a MealClass as empty at first like this:
```

MealClass CUSTOMER = new MealClass();  // no numbers yet!

```

then you should probably add ANOTHER constructor in the class which is empty like this.

```

        public MealClass(){  // no arguments here

               // do nothing here or do something meaningless such as:
               numberOfPersonsDining = 0;
        }

```


hope that helps a little, ... and somebody please verify me or correct me if I'm wrong!

---

### Post by Bossco30 on 2008-02-26
ok that does make alot sense now ty

---

