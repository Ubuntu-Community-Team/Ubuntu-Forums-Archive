---
title: "Stuck with Java, please help! [-o&lt;"
date: 2008-10-09
forum: Programming Talk
---

### Post by Igniteflow on 2008-10-09
I'm currently learning Java and am trying to write a simple program which would allow the user to input the length of an edge/side of a square to which the program would return the square's area.  Very simple I know!  Here is what I have so far:

**Square.java**

public class Square                    		// Class Header
{
    private int length;                		// Instance variables
    
    public Square(int l)    			// Constructor method
    {
        length = l;
            }

    public int calculateSurfaceArea()        	// Access method
    {
        return (length*2)*6;
    }      					// Calculates area
}  	

---------------------------------------------------------

SquareUser.java

import java.io.*;
import java.lang.Integer.*;

public class SquareUser 	{
	public static void main(String argv[]) throws IOException	{
		BufferedReader input = new BufferedReader
		(new InputStreamReader (System.in));
		String inputString;
	int square1;
		
	System.out.print("Input edge length:  ");
	inputString = input.readLine();
	square1 = Integer.parseInt("");
	
	System.out.println("square1 area " +
		square1.calculateSurfaceArea());
    		
	}
}

My problem is the compiler throws me:
pppp@power-desktop:~/Square$ javac SquareUser.java
SquareUser.java:9: ';' expected
	int square1
	           ^
1 error
phil@power-desktop:~/Square$ javac SquareUser.java
SquareUser.java:16: int cannot be dereferenced
		square1.calculateSurfaceArea());
		       ^
1 error
	
Could someone please tell me how to solve this; it's driving me insane!

---

### Post by skeeterbug on 2008-10-09
-

---

### Post by Reiger on 2008-10-09
If find a couple of things vaguely intriguing about your code:
```

square1 = Integer.parseInt(**""**); /* which will yield an NumberFormatException, I presume?
... omitted sensible code
*/
System.out.println("square1 area " +
**square1.calculateSurfaceArea()**);
/* Since when did the primitive type int have any methods? */

```

I think what you mean is something like this ...
```

import java.io.*; /* The Java.lang.Integer import is redundant */
public HomeWorkSample { /* Isn't it? ;) */

public static void main(String [] args) {
  String read=null;
  try {
    System.out.println("Please enter your numeric input:");
    BufferedReader reader= new BufferedReader(new InputStreamReader(System.in));
    read=reader.readLine();
    if(read == null)
       throw new NullPointerException("Bad user? You didn't give me input!");
    if(read.equals(""))
       throw new NumberFormatException("Bad user was here!");
    Square thing=new Square(Integer.parseInt(read));
    System.out.println("The area of your square is: "+thing.calculateSurfaceArea());
    br.close();
  }
  catch(Exception e) {
    if(e instanceof NumberFormatException) // No integer given!
      System.out.println("Bad user! This ain't no integer! (This being: \""+read+"\")");
    else {
      System.out.println("Sorry, something went wrong -- see below for details:");
      System.out.println(e.toString());
    }
  }
  System.out.close();
  System.exit(0);
}

}

```

---

### Post by sanskaras on 2008-10-09
Here's a fix to your code.

```
import java.io.*;
import java.lang.Integer.*;

public class SquareUser {

    public static void main(String argv[]) throws IOException {
        BufferedReader input = new BufferedReader(new InputStreamReader(System.in));
        String inputString;

                //square1 one has to of type Square

        Square square1;          

        System.out.print("Input edge length: ");
        inputString = input.readLine();

               //Create a new instance of object Square and pass
               //the length to the contructor

        square1 = new Square(Integer.parseInt(inputString)); 

               //No errors now that square1 is a Square object.

        System.out.println("square1 area " +
                square1.calculateSurfaceArea());

    }
}
```

---

### Post by drubin on 2008-10-09
When posting stuff it would be nicer to use the [NOPARSE][PHP][/PHP][/NOPARSE] php tags, it adds colours to the post and makes it easier to spot mistakes start/end of methods and stuch.

[PHP]
public static void main(String [] args){
     System.out.println("test");
}
[/PHP]
^^ simple but makes the code easier to read

---

### Post by wrtpeeps on 2008-10-09
Try 

int square1=0;

---

### Post by mosty friedman on 2008-10-09
you have a few errors, the first one is in inputting the integer value in the main method,
[php] 
inputString = input.readLine();
length = Integer.parseInt(""); //it should be 
length = Integer.parseInt( inputString );
[/php] becuase you're converting the String inputString into an integer, in the statement that you did, u were trying to convert an empty String "" into an integer...
the other thing was, you cannot call the method calculateSurfaceArea the way you did because you declared the method as an instance method which means that it needs to be invoked on an object and you did not create a new Square object in the main method
so
[php]
Square square1 = new Square( length ); // this calls the constructor of class Square and instantiates the Square square1 with a length value which the user entered
System.out.println( "surface area = " + square1.calculateSurfaceArea() );
[/php]
another tip is, you dont have to import any class from java.lang package because it is implicitly imported by the compiler so that should save you a lil typing..

---

