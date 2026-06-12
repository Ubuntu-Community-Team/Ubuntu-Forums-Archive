---
title: "Error Protection reading ints from user - Java"
date: 2009-10-30
forum: Programming Talk
---

### Post by MCBTunes on 2009-10-30
I am having trouble making my program robust against user error. For example, I tell the user to enter an integer between 1-5. If the user enters 9 I can catch it and reprompt for a new number however if the user enters something like 'a' then the program crashes.


Right now I am doing this
```

try{
	do{
		do{
			System.out.println("Enter anumber between 1-5 ");
		    	input = br.readLine();
		}while(input.equals("") || input.contains(" "));

    		choice = Integer.parseInt(input);
    		if(choice<=0 || choice >5){
			System.out.println("Invalid Entry, try again\n");
    		}

    	}while(choice<=0 || choice >5);

}catch (IOException ioe){
	System.out.println("IO error trying to read your Number");
    	System.exit(1);
}


```

So it reads the input in as a string, then parses it to an int. The important thing is I want the program to recognize when invalid input has been entered and reprompt the user, not just sit there until proper input is received.

---

### Post by PaulM1985 on 2009-10-30
I have not tested this, but could you create two strings:


String zeroStr = new String("0");
String fiveStr = new String("5");

and use:

while ((test.compareTo(zeroStr) < 0 && test.compareTo(fiveStr) > 0) || test.length() != 1)

The compareTo should compare unicode string values.

This may not be exactly the right solution but it may be on the right lines, the compareTo() method in String in the API might explain the idea better.

Hope it helps.

Paul

---

### Post by dwhitney67 on 2009-10-30
> **MCBTunes said:**
> I am having trouble making my program robust against user error. For example, I tell the user to enter an integer between 1-5. If the user enters 9 I can catch it and reprompt for a new number however if the user enters something like 'a' then the program crashes.

It would be very beneficial to your programming adventures if you would take the time to read the API for the functions that you employ in your programs.

Here's the URL for Integer.parseInt():
[http://java.sun.com/javase/6/docs/api/java/lang/Integer.html#parseInt(java.lang.String](http://java.sun.com/javase/6/docs/api/java/lang/Integer.html#parseInt(java.lang.String))

Pay careful attention to the type of exception that this method throws upon detecting an error.  Does your program catch this?  Nope!

---

### Post by MCBTunes on 2009-10-30
Thank you both for the help. It works now.

and dwhitney. I am going to try my best to use your advice, I am new to java and it would help me learn the ropes as well as improve my programs.

---

