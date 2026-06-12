---
title: "newb question = java programming"
date: 2008-02-13
forum: Programming Talk
---

### Post by AlexenderReez on 2008-02-13
hm..i have doen few coding...i hope somebody can guide this newb( me) so that i can make my code working

first code =

first method ..

```
import java.io.*;
import java.util.*;

public class calculate{



public static void main(String [] args){





int i = 1;



while (i == 1){

    System.out.println(" Please choose number of shape of area to calculate= 1.Circle , 2.Square , 3.Triangle");

    Scanner shapeInput = new Scanner(System.in);







shaPe = shapeInput.nextInt();

  if (shaPe = 1){

//--->circle

       Scanner myInput = new Scanner(System.in);

       System.out.println("Please enter the circle radius  =");



  double radius = myInput.nextInt();



  double areaCircle = 3.124 * radius*radius;





	if(radius < 0){

i= 0;

}



		else{

System.out.println("area is =" + areaCircle);

} 

     }



  if (shaPe = 2){

//---> square

Scanner myInput = new Scanner(System.in);

System.out.println("Please enter the square length  =");



 double length = myInput.nextInt();



 double areaCircle = length*length;





if(length < 0){

i= 0;

}



else{

System.out.println("area is =" + areaCircle);

} 

   }



if (shaPe = 3){

//---->tiangle

Scanner myInput = new Scanner(System.in);

System.out.println("Please enter the circle length  =");



 double length = myInput.nextInt();

System.out.println("Please enter the circle high  =");



 double high = myInput.nextInt();

 double areaCircle = length * high;





if(length < 0|| high < 0){

i= 0;

}



else{

System.out.println("area is =" + areaCircle);

}  

 }

   }

    }
     }

```
second method
```
import java.io.*;
import java.util.*;

public class calculate2{



public static void main(String [] args){


calArea circleShape = new calArea();

calArea squareShape = new calArea();

calArea triagleShape = new calArea();
int i = 1;



while (i == 1){

    System.out.println(" Please choose number of shape of area to calculate= 1.Circle , 2.Square , 3.Triangle");

    Scanner shapeInput = new Scanner(System.in);







shaPe = shapeInput.nextInt();

  if (shaPe = 1){

     calArea.circleArea();



     }



  if (shaPe = 2){

     calArea.squareArea();



   }



  if (shaPe = 3){

     calArea.triagleArea();



 }

   }

 void calArea{
 public void squareArea(){
Scanner myInput = new Scanner(System.in);

System.out.println("Please enter the square length  =");



double length = myInput.nextInt();



double areaCircle = length*length;





if(length < 0){

i= 0;

}



else{

System.out.println("area is =" + areaCircle);

} 


   	}
   public void triagleArea(){
  Scanner myInput = new Scanner(System.in);

System.out.println("Please enter the circle length  =");



double length = myInput.nextInt();

System.out.println("Please enter the circle high  =");



double high = myInput.nextInt();

double areaCircle = length * high;





if(length < 0|| high < 0){

i= 0;

}



else{

System.out.println("area is =" + areaCircle);

}  


   	}
public void circleArea(){
       Scanner myInput = new Scanner(System.in);

       System.out.println("Please enter the circle radius  =");



  double radius = myInput.nextInt();



  double areaCircle = 3.124 * radius*radius;





	if(radius < 0){

i= 0;

}



		else{

System.out.println("area is =" + areaCircle);

} 


   	}	
   	
 
 }     

    
    
    
    
    }
     }

```

third method =
```
import java.io.*;
import java.util.*;

public class calculate3{



public static void main(String [] args){


calAreaCircle circleShape = new calAreaCircle();

calAreaSquare squareShape = new calAreaSquare();

calAreaTriagle triagleShape = new calAreaTriagle();
int i = 1;



while (i == 1){

    System.out.println(" Please choose number of shape of area to calculate= 1.Circle , 2.Square , 3.Triangle");

    Scanner shapeInput = new Scanner(System.in);







shaPe = shapeInput.nextInt();

  if (shaPe = 1){

     circleShape.circleArea();



     }



  if (shaPe = 2){

     squareShape.squareArea();



   }



if (shaPe = 3){

     triagleShape.triagleArea();



 }

   }

    }
     }

```

```
public class calAreaSquare{

	public void squareArea(){
Scanner myInput = new Scanner(System.in);

System.out.println("Please enter the square length  =");



double length = myInput.nextInt();



double areaCircle = length*length;





if(length < 0){

i= 0;

}



else{

System.out.println("area is =" + areaCircle);

} 


   	}
		}
```

```
public class calAreaTriagle{

	public void triagleArea(){
  Scanner myInput = new Scanner(System.in);

System.out.println("Please enter the circle length  =");



double length = myInput.nextInt();

System.out.println("Please enter the circle high  =");



double high = myInput.nextInt();

double areaCircle = length * high;





if(length < 0|| high < 0){

i= 0;

}



else{

System.out.println("area is =" + areaCircle);

}  


   	}
		}
```
```
public class circleArea{

	public void circleArea(){
       Scanner myInput = new Scanner(System.in);

       System.out.println("Please enter the circle radius  =");



  double radius = myInput.nextInt();



  double areaCircle = 3.124 * radius*radius;





	if(radius < 0){

i= 0;

}



		else{

System.out.println("area is =" + areaCircle);

} 


   	}
		}
```

---

### Post by AlexenderReez on 2008-02-13
another program
```
public class MacDollah{

    public static void main(String [] args){

//class food

food foodInfo  = new food();
food foodPrice = new food();
//class menu

menu customerData = new menu();

//class order
order calculatePrice = new order();



customerData.cusData();

calculatePrice.calculateTotal();
calculatePrice.getTotalAmount();
calculatePrice.displayPrice();

} 

  }
```

```
public class food{

 public foodInfo{
 String foodData = new String[10];
	foodData[0] = "Mac Beef";
	foodData[1] = "Mac Fish";
	foodData[2] = "Cheesy Beef Burger";
	foodData[3] = "Mac Chicken";
	foodData[4] = "Mengelembu Fries";
	foodData[5] = "Combo Meal A";
	foodData[6] = "Combo Meal B";
	foodData[7] = "Combo Meal C";
	foodData[8] = "SoftDrink";
	foodData[9] = "Ais CreaM";

	double foodPrice = new double[10];
	foodPrice[0] = 2.7;
	foodPrice[1] = 3.5;
	foodPrice[2] = 3.5;
	foodPrice[3] = 3.0;
	foodPrice[4] = 2.0;
	foodPrice[5] = 5.0;
	foodPrice[6] = 6.5;
	foodPrice[7] = 8.0;
	foodPrice[8] = 2.0;
	foodPrice[9] = 1.0;

  }
}
```

```
public class menu implements food{

public double cusData{
	double totalPrice = 0;
	int count = 0;
	while(count < 10){
	System.out.println( (count + 1) + foodData[count]+ " = " + foodPrice[count] );
	}
        int loop = 1;
        while(loop = 1){
        Scanner foodchoice = new Scanner(System.in);
        System.out.println("Please enter your food choice number(to end enter 0");
        //not sure
        choiceno = foodchoice.nextInt();
        }
        choiceno--;
        if(choiceno < 0){
        loop = 0;
        }
        if(choiceno == 0){
        
        totalPrice += foodPrice[0];
        System.out.println("the current price is " + totalPrice);
        }
        if(choiceno == 1){
        System.out.println("the price is " + foodPrice[1]);
        totalPrice += foodPrice[1];
        }
        if(choiceno == 2){
        
        totalPrice += foodPrice[2];
        System.out.println("The current price is " + totalPrice);
        }
        if(choiceno == 3){
        
        totalPrice += foodPrice[3];
        System.out.println("The current price is " + totalPrice);
        }
        if(choiceno == 4){
        
        totalPrice += foodPrice[4];
        System.out.println("The current price is " + totalPrice);
        }
        if(choiceno == 5){
        
        totalPrice += foodPrice[5];
        System.out.println("The current price is " + totalPrice);
        }
        if(choiceno == 6){
        
        totalPrice += foodPrice[6];
        System.out.println("The current price is " + totalPrice);
        }
        if(choiceno == 7){
        
        totalPrice += foodPrice[7];
        System.out.println("The current price is " + totalPrice);
        }
        if(choiceno == 8){
        
        totalPrice += foodPrice[8];
        System.out.println("The current price is " + totalPrice);
        }
        if(choiceno == 9){
        
        totalPrice += foodPrice[9];
        System.out.println("The current price is " + totalPrice);
        }
        


  }
   }
```

```
public class order implements menu{

   public double calTotal(){

return double calculateTotal = totalPrice;
}

   public double getTotalAmount(){
return double overallTotal = calculateTotal * 1.05;

}
  public void displayPrice{
System.Out.println("Total Prices need to pay = "+ overallTotal;
 }
    }
```

any help will be appreciate....

---

### Post by johnnyb1726 on 2008-02-13
Could you please elaborate on the problems you are having when you try to run this code?

---

### Post by Zugzwang on 2008-02-14
First of all, please
[LIST]
[*]Be precise as far as your problem is concerned. We can't guess what your program is supposed to do or how you are compiling the program, so please give details on *what* is wrong (as johnnyb1726 suggested).
[*]Before posting any code, please reformat it such that it is readable well.
[*]If you have got a problem with some code, make a copy and shorten the program as much as you can. It doesn't matter if your program doesn't do what it should afterwards as long as your problem is still present. Nobody will figure out how your code works here.
[/LIST]

Anyway, there is one striking thing:

```
public class food{

 public foodInfo{
 String foodData = new String[10];
	foodData[0] = "Mac Beef";
	foodData[1] = "Mac Fish";
	foodData[2] = "Cheesy Beef Burger";
	foodData[3] = "Mac Chicken";
	foodData[4] = "Mengelembu Fries";
	foodData[5] = "Combo Meal A";
	foodData[6] = "Combo Meal B";
	foodData[7] = "Combo Meal C";
	foodData[8] = "SoftDrink";
	foodData[9] = "Ais CreaM";

	double foodPrice = new double[10];
	foodPrice[0] = 2.7;
	foodPrice[1] = 3.5;
	foodPrice[2] = 3.5;
	foodPrice[3] = 3.0;
	foodPrice[4] = 2.0;
	foodPrice[5] = 5.0;
	foodPrice[6] = 6.5;
	foodPrice[7] = 8.0;
	foodPrice[8] = 2.0;
	foodPrice[9] = 1.0;

  }
}
```

What is this code supposed to do? If you want your class to have variables, you have to declare it outside of a function. And by the way, your function does not have a return value. Do you probably want to use a constructor? Finally, in the line "String foodData = new String[10];" you don't match the type of the variable "foodData". So try:

```
public class food{

 protected String foodData[];
 protected double foodPrice[]
 public food() {
 
        foodData = new String[10];
        foodPrice = new double[10];

	foodData[0] = "Mac Beef";
	foodData[1] = "Mac Fish";
	foodData[2] = "Cheesy Beef Burger";
	foodData[3] = "Mac Chicken";
	foodData[4] = "Mengelembu Fries";
	foodData[5] = "Combo Meal A";
	foodData[6] = "Combo Meal B";
	foodData[7] = "Combo Meal C";
	foodData[8] = "SoftDrink";
	foodData[9] = "Ais CreaM";

	foodPrice[0] = 2.7;
	foodPrice[1] = 3.5;
	foodPrice[2] = 3.5;
	foodPrice[3] = 3.0;
	foodPrice[4] = 2.0;
	foodPrice[5] = 5.0;
	foodPrice[6] = 6.5;
	foodPrice[7] = 8.0;
	foodPrice[8] = 2.0;
	foodPrice[9] = 1.0;

  }
}
```

---

### Post by AlexenderReez on 2008-02-14
thanks...for concern...i finally solve it...

:)  :KS :)

---

