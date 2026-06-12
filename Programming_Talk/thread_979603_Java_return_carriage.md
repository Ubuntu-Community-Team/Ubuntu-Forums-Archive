---
title: "Java return carriage"
date: 2008-11-12
forum: Programming Talk
---

### Post by pcjunkie on 2008-11-12
I am writing a script for Uni and I would like to add a feature or function that would return to the begging of a script / class if a data input does not match what I need.

For eg the operator enters a number 1 to 4
if the number is not a number or is > 4 then I would like the script to skip back to the beginning or return to the start of the input sequence using scanner.class

I would prefer this than just simply outputting (invalid input) and then have the program stop.

Can that be done?

---

### Post by geirha on 2008-11-12
You typically use a while loop for that. A little pseudu code:

```

print "some request for user input"
answer = get_input()
while (answer is not acceptable)
{
    print "invalid input, please try again"
    answer = get_input()
}
print "Excellent!"

```

---

### Post by odyniec on 2008-11-12
I don't know if this applies to your case, as you didn't post your code, but, in general, you can place the user input code in a while loop and keep repeating it until whatever the user enters is valid. Example:

```
while (true) {

    /* ... user input code goes here ... */
  
    /* check input validity */
    if (number < 4)
        /* number is valid -- break out of the loop */
        break;
}

/* ... do something with number ... */
```

---

### Post by pcjunkie on 2008-11-12
Ahh cheers I think I read the internet looking for a simple answer to a wanted catch / retry situation

Just call the constructor / class again?

What I have (rough concept yet to be cleaned up) I need to assign pay rates to a given number. The given number is user input based so I check through using an array but all I have gathered in class so far is hot to print the error 

```
if (Payid == 1) { pr= 55.00; }  
			
		else if (Payid == 2) { pr = 33.00; } 
		
		else if (Payid == 3) { pr = 25.00; } 
			
		else if (Payid == 4) { pr = 20.00; }
			
		else if ((Payid <=0) || ( Payid >= 5)) 
		{
		System.out.println("invalid Input!"); 
		System.out.println("\nError! Your brain has encoutered a problem and will now close"); 
		System.out.println("Please contact the System Administrator"); 
		System.out.println("Page Fault in ED0000x0000 FE0000x0000 location at " + fname + " " +lname +"'s Brain32.DLL");
		}  Etc...



```


What I am attempting and the above should do it I think...


```


constructor get-if(payid)
if (Payid == 1) { pr= 55.00; }  
			
		else if (Payid == 2) { pr = 33.00; } 
		
		else if (Payid == 3) { pr = 25.00; } 
			
		else if (Payid == 4) { pr = 20.00; }
			
		else if ((Payid <=0) || ( Payid >= 5)) 
		{
		  get-if (payid)
		}

```

---

### Post by Tomosaur on 2008-11-12
> **pcjunkie said:**
> Ahh cheers I think I read the internet looking for a simple answer to a wanted catch / retry situation

Just call the constructor / class again?

What I have (rough concept yet to be cleaned up) I need to assign pay rates to a given number. The given number is user input based so I check through using an array but all I have gathered in class so far is hot to print the error 

```
if (Payid == 1) { pr= 55.00; }  
            
        else if (Payid == 2) { pr = 33.00; } 
        
        else if (Payid == 3) { pr = 25.00; } 
            
        else if (Payid == 4) { pr = 20.00; }
            
        else if ((Payid <=0) || ( Payid >= 5)) 
        {
        System.out.println("invalid Input!"); 
        System.out.println("\nError! Your brain has encoutered a problem and will now close"); 
        System.out.println("Please contact the System Administrator"); 
        System.out.println("Page Fault in ED0000x0000 FE0000x0000 location at " + fname + " " +lname +"'s Brain32.DLL");
        }  Etc...



```What I am attempting and the above should do it I think...


```


constructor get-if(payid)
if (Payid == 1) { pr= 55.00; }  
            
        else if (Payid == 2) { pr = 33.00; } 
        
        else if (Payid == 3) { pr = 25.00; } 
            
        else if (Payid == 4) { pr = 20.00; }
            
        else if ((Payid <=0) || ( Payid >= 5)) 
        {
          get-if (payid)
        }

```

Ouch!
Use a switch statement instead:
```

public void setPr(pr){
    Scanner input = new Scanner(System.in);
    boolean validPayid = false;
    int Payid = 0; //Assign to an invalid value to avoid unassigned variable error due to try/catch.
    while(!validPayid){
        try{
            Payid = input.nextInt();
        }
        catch(InputMismatchException ime)
        {
            //We'll only end up here if the user inputs something stupid like 'hello' instead of an actual number.
            //Do nothing, our switch statement provides for this
        }
        switch(Payid){
            case 1:
                //Executed if the value of Payid is 1.
                pr = 55.00;
                validPayid = true;
                break;
            case 2:
                //Executed if the value of Payid is 2.
                pr = 33.00;
                validPayid = true;
                break;
            case 3:
                //As above
                pr = 25.00;
                validPayid = true;
                break;
            case 4:
                //As above
                pr = 20.00;
                validPayid = true;
                break;
            default:
                /*Executed if Payid does not match any other case
                **Since the input must be invalid if we arrive here, just inform the user
                **and return to the while loop!*/
                System.out.println("Invalid input, please try again!");
                break;
        }
    }
}

```Much more readable and does what you want with the minimum of fuss :)

EDIT: Of course, if pr can only ever be one of those values, you may want to look into using an enumeration rather than dealing with these magic numbers. Here's a nice page explaining some neat tricks you can use with Java enums: [http://ajaxonomy.com/2007/java/making-the-most-of-java-50-enum-tricks](http://ajaxonomy.com/2007/java/making-the-most-of-java-50-enum-tricks)

---

### Post by pcjunkie on 2008-11-15
Thank you. 

Yes if statements (for a noob) are good to proof with I guess, but do while and for loops work better.

Thanks for the help.

---

