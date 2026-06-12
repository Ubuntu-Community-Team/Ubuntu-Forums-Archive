---
title: "java = need help to explain these errors"
date: 2008-02-17
forum: Programming Talk
---

### Post by AlexenderReez on 2008-02-17
hope anybody can help me correct this -->
file =
```
import java.io.*;
import java.util.*;

public class calculate2{



public static void main(String [] args){

calArea allArea = new calArea();
allArea.circleShape();

allArea.squareShape();

allArea.triagleShape();
int i = 1;



while (i == 1){

    System.out.println(" Please choose number of shape of area to calculate= "+ "1.Circle , 2.Square , 3.Triangle,negative number to exit");

    Scanner shapeInput = new Scanner(System.in);







shaPe = shapeInput.nextInt();

  if(shaPe < 0){
	System.out.println("you choose to exit");
	System.exit (0);

	}

  if (shaPe == 1){

     calArea.circleArea();



     	}



  if (shaPe == 2){

     calArea.squareArea();



   	}



  if (shaPe == 3){

     calArea.triagleArea();



 	}

   }

public void calArea(){
	
	
	
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

System.out.println("Please enter the Triangle length  =");



 double length = myInput.nextInt();

System.out.println("Please enter the Triangle high  =");



 double high = myInput.nextInt();

 double areaCircle = 1/2 *length * high;





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

error =
[PHP]reez@alexenderreez:~/Desktop/assignment$ javac calculate2.java
calculate2.java:40: illegal start of expression
public void calArea(){
^
calculate2.java:44: illegal start of expression
        public void squareArea(){
        ^
calculate2.java:104: class, interface, or enum expected
        }
        ^
3 errors
[/PHP]

---

### Post by CptPicard on 2008-02-17
Your code is so badly formatted my mental parser has issues reading it, but it seems to me you're declaring some methods inside your main() method, which  you aren't allowed to do.

I'd suggest you review the basic structure of a Java class source file.

---

### Post by LaRoza on 2008-02-17
There is a link in the sticky on how to post code on the forums, your code is extremely hard to read.

---

### Post by bobrocks on 2008-02-17
> **CptPicard said:**
> Your code is so badly formatted my mental parser has issues reading it, but it seems to me you're declaring some methods inside your main() method, which  you aren't allowed to do.

I'd suggest you review the basic structure of a Java class source file.

I would agree with this.

You have an inner class declared as a method inside of the main method, which is not going to work.

You also have lots of variables declared without their type.

Out of interest why name shape, shaPe, that must get annoying fast?

---

### Post by plastichero on 2008-02-17
can you plz specify the starting and the ending brace of the main function ? also the while loops? in that case we can understand the code and give you a solution.

---

### Post by pmcastillo on 2008-02-17
Errrr... My brain said... "Stack Overflow"....

I got confused with the opening and closing braces ^_^

---

### Post by jespdj on 2008-02-18
You most likely have missing or extra curly braces.

---

### Post by hod139 on 2008-02-18
I ran your code through an automatic code indentation program (astyle) and now it looks a little better.  I also highlighted the line that is causing the error.  You are declaring a method inside a method.  You can't do that.
```

import java.io.*;
import java.util.*;

public class calculate2
{
    public static void main(String [] args)
    {
        calArea allArea = new calArea();
        allArea.circleShape();

        allArea.squareShape();

        allArea.triagleShape();
        int i = 1;

        while (i == 1)
        {
            System.out.println(" Please choose number of shape of area to calculate= "+ "1.Circle , 2.Square , 3.Triangle,negative number to exit");

            Scanner shapeInput = new Scanner(System.in);

            shaPe = shapeInput.nextInt();

            if (shaPe < 0)
            {
                System.out.println("you choose to exit");
                System.exit (0);
            }

            if (shaPe == 1)
            {
                calArea.circleArea();
            }

            if (shaPe == 2)
            {
                calArea.squareArea();
            }

            if (shaPe == 3)
            {
                calArea.triagleArea();
            }
        }

        public void calArea()
        {
           ** public void squareArea()**
            {
                Scanner myInput = new Scanner(System.in);

                System.out.println("Please enter the square length  =");

                double length = myInput.nextInt();
                double areaCircle = length*length;

                if (length < 0)
                {
                    i= 0;
                }
                else
                {
                    System.out.println("area is =" + areaCircle);
                }
            }

            public void triagleArea()
            {
                Scanner myInput = new Scanner(System.in);

                System.out.println("Please enter the Triangle length  =");

                double length = myInput.nextInt();

                System.out.println("Please enter the Triangle high  =");

                double high = myInput.nextInt();

                double areaCircle = 1/2 *length * high;

                if (length < 0|| high < 0)
                {
                    i= 0;
                }
                else
                {
                    System.out.println("area is =" + areaCircle);
                }
            }

            public void circleArea()
            {
                Scanner myInput = new Scanner(System.in);

                System.out.println("Please enter the circle radius  =");

                double radius = myInput.nextInt();

                double areaCircle = 3.124 * radius*radius;

                if (radius < 0)
                {
                    i= 0;
                }
                else
                {
                    System.out.println("area is =" + areaCircle);
                }
            }
        }
    }
}


```

---

