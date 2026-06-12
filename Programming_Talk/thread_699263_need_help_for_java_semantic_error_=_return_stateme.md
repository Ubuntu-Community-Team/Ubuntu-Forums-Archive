---
title: "need help for java semantic error = return statement error"
date: 2008-02-17
forum: Programming Talk
---

### Post by AlexenderReez on 2008-02-17
main class = MAcDollah.java
```
import java.util.*;



public class MacDollah{

    public static void main(String [] args){



	//class menu

	menu RestMenu = new menu();



	//class order

	order calculatePrice = new order();

	RestMenu.foodList();

	RestMenu.cusData();



	calculatePrice.calTotal();

	calculatePrice.getTotalAmount();

	calculatePrice.displayPrice();

	} 

  }

```

sub class 1= food.java

```
public class food{



	// attributes of a food

	 String name; 

	 double price;

}

```

sub class 2 = order.java

```
import java.util.*;



public class order{

        menu GetFood;

        double Price;

        double overallTotal;

        public order(){

            GetFood = new menu();

            GetFood.foodList();

        }



        public double calTotal(){

        GetFood.selectFood();

        Price += GetFood.selectFood();

        return Price;

        }



        public double getTotalAmount()

        {

        overallTotal = 0;

        return overallTotal += Price * 1.05;



        }



        public void displayPrice(){

        System.out.println("Total Prices need to pay = "+ overallTotal);

        }

}

```

sublass 3 = menu.java

```


import java.util.*;



public class menu

	{

		// attribute done!

	food foodList[] = new food[10];



	public void foodList(){ // to assign values to array



		foodList[0] = new food();

		foodList[0].name = "Mac Beef";

		foodList[0].price = 2.7;

		foodList[1] = new food();

		foodList[1].name = "Mac Fish";

		foodList[1].price = 3.5;

		foodList[2] = new food();

		foodList[2].name = "Cheesy Beef Burger";

		foodList[2].price = 3.5;

		foodList[3] = new food();

		foodList[3].name = "Mac Chicken";

		foodList[3].price = 3.0;

		foodList[4] = new food();

		foodList[4].name = "Mengelembu Fries";

		foodList[4].price = 2.0;

		foodList[5] = new food();

		foodList[5].name = "Combo Meal A";

		foodList[5].price = 5.0;

		foodList[6] = new food();

		foodList[6].name = "Combo Meal B";

		foodList[6].price = 6.5;

		foodList[7] = new food();

		foodList[7].name = "Combo Meal C";

		foodList[7].price = 8.0;

		foodList[8] = new food();

		foodList[8].name = "SoftDrink";

		foodList[8].price = 2.0;

		foodList[9] = new food();

		foodList[9].name = "Ais CreaM";

		foodList[9].price = 1.0;



	

    

}















public void cusData()

	{

	for(int count=0; count<=9; count++)

		{

		System.out.println( (count + 1) +". " + foodList[count].name+ " = " + foodList[count].price);

		}

	}



public double selectFood()

	{

	int i = 1;

	

	while(i == 1) {

		Scanner PriceFood = new Scanner(System.in);

		System.out.println("Please enter your number selection(Enter 0 to end selection)");

		int noPrice = PriceFood.nextInt()- 1;

		if(noPrice >= 0 && noPrice <=9){

			return(foodList[noPrice + 1].price );	

			}

		if(noPrice <= 0 && noPrice >=9){

			i = 0;

		   }

		}



       return 0.0;

 	}

}







```


The program should ask user to choose food and calculate total ..no complication error but ..when run =

[PHP]reez@alexenderreez:~/Desktop/assignment$ java MacDollah
1. Mac Beef = 2.7
2. Mac Fish = 3.5
3. Cheesy Beef Burger = 3.5
4. Mac Chicken = 3.0
5. Mengelembu Fries = 2.0
6. Combo Meal A = 5.0
7. Combo Meal B = 6.5
8. Combo Meal C = 8.0
9. SoftDrink = 2.0
10. Ais CreaM = 1.0
Please enter your number selection(Enter 0 to end selection)
1
Please enter your number selection(Enter 0 to end selection)
2
Total Prices need to pay = 3.6750000000000003
[/PHP]

it ends even user don't ask to end it..and give wrong calculation...i expect this error because of menu.java file and order.java file..please help...

---

### Post by bobrocks on 2008-02-17
I can tell you why it's not working, I leave you to find out how to fix it.

In order.java you have a calTotal method that calls 

[PHP]GetFood.selectFood()[/PHP]

This is where your first request for a food item is coming from, there is some problems inside this selectFood method.

[PHP]
public double selectFood() {

		int i = 1;

		while(i == 1) {

			Scanner PriceFood = new Scanner(System.in);

			System.out.println("Please enter your number selection(Enter 0 to end selection)");

			int noPrice = PriceFood.nextInt()- 1;

			if(noPrice >= 0 && noPrice <=9){

				return(foodList[noPrice + 1].price );
			}

			if(noPrice <= 0 && noPrice >=9){

				i = 0;
			}
		}

		return 0.0;
	}
[/PHP]

you enter a conditional loop at the line
[PHP]while(i == 1) {[/PHP]
This is obviously true the first time through as you have set i = 1.

You get the item number in off the keyboard and correct it for the array index.
[PHP]int noPrice = PriceFood.nextInt()- 1;[/PHP]
nice, then you do some bounds checking, again nice.
[PHP]if(noPrice >= 0 && noPrice <=9){[/PHP]
now your problems begin
[PHP]return(foodList[noPrice + 1].price );[/PHP]
return is used to "return" the methods return value.  This method is set to return a double and thats what return does.  It breaks out of your while look and returns the value foodlist price.  I'm

not sure why you are adding 1 back onto the index here.

[PHP]if(noPrice <= 0 && noPrice >=9){[/PHP]
This is a little strange as && means 'and' so condition a and b must be true but no number can be less than 0 and greater than 9.

And the reason you are getting a second request for a value is because you have
[PHP]Price += GetFood.selectFood();[/PHP]
calling the select food method once again that does the same as above but this time price will be set to whatever was chosen in that last choice.

Hope that gives you enough to try it again.

If you are using an ide I can't recommend enough learning how it's debugger works.  It will allow you to walk through the code and see what it happening.

PS - if you have some time, have a read of the Sun code syntax conventions; capitalise first letter of classes, dont capatalise first letter of variables ect.

---

### Post by AlexenderReez on 2008-02-17
thanks..i manage to solve it

---

