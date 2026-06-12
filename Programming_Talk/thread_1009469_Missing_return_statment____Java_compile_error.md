---
title: "Missing return statment??    Java compile error"
date: 2008-12-12
forum: Programming Talk
---

### Post by brian77095 on 2008-12-12
javac Ag.java
Ag.java:175: missing return statement
        }
        ^
1 error


I am having problems finding this error.  It looks like it is telling me I am missing a curly but cant see were....  Any hints were to look  I done a line by line search but cant find anything out of place...

---

### Post by bobrocks on 2008-12-12
It helps when you show the code.

But the error is telling you the method closed by that curly brace is meant to return a value and it does not have a return *something* statement.

---

### Post by mssever on 2008-12-12
> **brian77095 said:**
> javac Ag.java
Ag.java:175: missing return statement
        }
        ^
1 error


I am having problems finding this error.  It looks like it is telling me I am missing a curly but cant see were....  Any hints were to look  I done a line by line search but cant find anything out of place...
How about posting some code?

---

### Post by pp. on 2008-12-12
> **brian77095 said:**
> It looks like it is telling me I am missing a curly but cant see were....

Actually, the text you are showing says plainly "missing return statement". A return statement is a statement which uses the word "return". Hence, the text appears to be saying that there ought to be a "return statement" where there is none.

---

### Post by brian77095 on 2008-12-12
private String evaluate()

    {

        final char beep = '\u0007';



        try

        {

            double A = Integer.parseInt(numStr1);

            double B = Integer.parseInt(numStr2);

            double result = 0;



            switch(op)

            {

            case '+': result = A + B;

                      break;

            case '-': result = A - B;

                      break;

            case '*': result = A * B;

                      break;

            case '/': result = A / B;

	    
            }



//	    if (B == 0.0)
//			throw new DivByZero();



            return String.valueOf(result);

        }




        catch(ArithmeticException e)

           {
	   if (numStr2.equals(0))
	               return "E R R O R: Divide by Zero" + e.getMessage();
	
           }

        catch(NumberFormatException e)

            {

            System.out.print(beep);

            if(numStr1.equals(""))

              return "E R R O R: Invalid First Number" ;

            else

               return "E R R O R: Invalid Second Number" ;

            }

        catch(Exception e)

            {

            System.out.print(beep);

            return "E R R O R";

            }

        }



    public static void main(String[] args)

    {

        Abc4444 C = new Abc4444();

    }





}




this is my code....sorry about not putting it in quotes but I could not seem to get that to work.

This is part of a program for a calculator....
In this code I am trying to get my program to return "error: Divide by Zero"  and I dont think I have it in the right place...

this is for a class so dont tell me the answer just point me in the right direction.

thanks for your help...

---

### Post by dwhitney67 on 2008-12-12
Try defining your function with a local variable, of type String, then change it as necessary in your try and catch blocks.  Finally at the end of the function, return that String.

example:
[php]
public String function()
{
  String rtnStr = NULL;

  try
  {
    // do something

    rtnStr = new String("A-OK");
  }
  catch (Exception e)
  {
    rtnStr = new String("error");
  }

  return rtnStr;
}
[/php]

Anyhow, the java compiler is complaining that you do not have a return statement at the end of the function (as demonstrated above).

---

### Post by pp. on 2008-12-12
> **brian77095 said:**
> sorry about not putting it in quotes but I could not seem to get that to work.

You select the part of your post which is code and click on the icon which wraps [code] tags around the selected text. It looks like the hash character, #.

Sigh.

---

### Post by brian77095 on 2008-12-12
```

private String evaluate()

    {

        final char beep = '\u0007';



        try

        {

            double A = Integer.parseInt(numStr1);

            double B = Integer.parseInt(numStr2);

            double result = 0;



            switch(op)

            {

            case '+': result = A + B;

                      break;

            case '-': result = A - B;

                      break;

            case '*': result = A * B;

                      break;

            case '/': result = A / B;

	    
            }



//	    if (B == 0.0)
//			throw new DivByZero();



            return String.valueOf(result);

        }




        catch(ArithmeticException e)

           {
	   if (numStr2.equals(0))
	               return "E R R O R: Divide by Zero" + e.getMessage();
	
           }

        catch(NumberFormatException e)

            {

            System.out.print(beep);

            if(numStr1.equals(""))

              return "E R R O R: Invalid First Number" ;

            else

               return "E R R O R: Invalid Second Number" ;

            }

        catch(Exception e)

            {

            System.out.print(beep);

            return "E R R O R";

            }

        }



    public static void main(String[] args)

    {

        Abc4444 C = new Abc4444();

    }





}


```


ahh well at least I learned that to day LOL

---

### Post by geirha on 2008-12-12
Your ```
catch (Exception e)
``` should catch all other exceptions that might be thrown from the try-block, but I don't think the compiler accepts that catch as a catch all, and thus complains that your function may in some cases not return anything. From what I can tell, it always will though, so just add a ```
return "This should never happen"
``` or something at the end of the function, and the compiler should be pleased.

---

### Post by drubin on 2008-12-13
> **dwhitney67 said:**
> Try defining your function with a local variable, of type String, then change it as necessary in your try and catch blocks.  Finally at the end of the function, return that String.

example:
[php]
public String function()
{
  String rtnStr = NULL;

  try
  {
    // do something

    rtnStr = new String("A-OK");
  }
  catch (Exception e)
  {
    rtnStr = new String("error");
  }

  return rtnStr;
}
[/php]

Anyhow, the java compiler is complaining that you do not have a return statement at the end of the function (as demonstrated above).

I would recommend using 
```
String x="error";
```
instead of 
```
String x=new String("error");
```

---

### Post by brian77095 on 2008-12-13
ok I tried to make the changes you guys outlined but, it was still giving me the same error.

Missing return statment
     }

so I looked back at past saves to go back a few steps and it works with the following changes....


```




        catch(ArithmeticException e)

           {
//	   if (numStr2.equals(0))
//	               return "E R R O R: Divide by Zero" + e.getMessage();
	    System.out.print(beep);
	    return "ERROR:" + e.getMessage();
	
           }

        catch(NumberFormatException e)

            {

            System.out.print(beep);

            if(numStr1.equals(""))

              return "E R R O R: Invalid First Number" ;

            else

               return "E R R O R: Invalid Second Number" ;

            }

        catch(Exception e)

            {

            System.out.print(beep);

            return "E R R O R";

            }

        }


```

All I did was comment out the if statement and add the system.out and return statement.  The problem I am having is that I need that if statement for the / by zero and, I am not sure where or how to put it in.

sorry if you already told me the right way to do it but I did not get it..

b

---

### Post by pp. on 2008-12-13
The error message you reported in your first post gives you quite some information about the error:

[LIST]
[*]java expects a return statement in a place you didn't supply one
[*]the class where the return statement is expected
[*]the line number where java detected that the return statement was missing
[*]the token which was encountered in the place where java expected the return statement.
[/LIST]

Also, the Java language definition states quite clearly that every function must have a return statement as the last executable statement. I do believe that java accepts ***if*** statements at the end of the function body provided that every case terminates with a return statement.

---

### Post by brian77095 on 2008-12-13
```


        catch(ArithmeticException e)

           {
	   if (numStr2.equals(0))
//	               return "E R R O R: Divide by Zero" + e.getMessage();
	    System.out.print(beep);
	    return "ERROR:" + e.getMessage();
	
           }



```

OK ugly but it compiles like this....now 

what I am doing is trying to retro fit if you will a calculator program with a "."  so that I can add subtract multiply with decimals.

the program compiles and works if I try to do 3+3 or 3/6 but if I do .5 + 3 then I get an error "ERROR: Invalid Second Number"   form my catch (numberformatException 3).

why is it doing that??

It also does not matter if I do 3+.3 or .3+3 I still get the ERROR Second number...

---

### Post by brian77095 on 2008-12-13
[PHP]
   private String evaluate()

    {

        final char beep = '\u0007';



        try

        {

            double A = Double.parseDouble(numStr1);

            double B = Double.parseDouble(numStr2);

            double result = 0;



            switch(op)

            {

            case '+': result = A + B;

                      break;

            case '-': result = A - B;

                      break;

            case '*': result = A * B;

                      break;

            case '/': result = A / B;

	    
            }




            return String.valueOf(result);

        }




        catch(ArithmeticException e)

           {
	   if (numStr2.equals(0.0))
//	               return "E R R O R: Divide by Zero" + e.getMessage();
	    System.out.print(beep);
	    return "ERROR:" + e.getMessage();
	
           }

        catch(NumberFormatException e)

            {

            System.out.print(beep);

            if(numStr1.equals(""))

              return "E R R O R: Invalid First Number" ;

            else

               return "E R R O R: Invalid Second Number" ;

            }

        catch(Exception e)

            {

            System.out.print(beep);

            return "E R R O R";

            }

        }



    public static void main(String[] args)

    {

        A454 C = new A454();

    }





}

[/PHP]

Ok the reason it was not working is because I was trying to declare

double a = int.parseint....and that does not work....

now it works fine but...when I divide by 0 it gives me a result of infinity and I need it to give my error message....

---

