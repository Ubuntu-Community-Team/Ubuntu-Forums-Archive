---
title: "Input validation, getchar, fgets and trailing newlines"
date: 2008-06-14
forum: Programming Talk
---

### Post by spadewarrior on 2008-06-14
I've been struggling with learning how to account for users entering incorrect data.

For instance, in the following piece of code, a string containing an integer containing numbers is expected. If anything else is entered then a message is displayed and the while loop restarts. 

However, when a number is entered after having entered a non-number, it has to be entered twice. I cannot fathom the cause of this. Can anybody help? 

Note that the first while loop exists as I have used getchar() in the code before this and it was stopping anything being entered.

[PHP]printf("\nEnter number of bikes:  \n\n");
	
     while((c = getchar()) != '\n' && c != EOF );
     {
		while(bikes <= 0)
		{
			fgets(bikeStr, sizeof(bikeStr), stdin);
			
			bikeStrLength = strlen(bikeStr);
			
			for (n=0; n < bikeStrLength; n ++) 
			{
				if ( (!isdigit(bikeStr[n]) &&bikeStr[n+1] =='\n'))
				{
					printf("That is not a valid number.\n");
					getchar(); // pick up trailing return key
				}
			
			}
			sscanf(bikeStr, "%i", &bikes);
			
		}
	
		
	}
	printf("%i bikes selected.\n", bikes); // print number of bikes after error-checking loop broken
[/PHP]

---

### Post by Lux Perpetua on 2008-06-14
Your validation is incorrect: your code checks if the last character (the one right before the newline) is a non-digit. Your use of getchar there is also confused. 

The strtol and strtoul functions are reliable ways to convert a string to an integer. They also effectively do your validation for you, since they give you a pointer to the first character that could not be converted. They even tell you if your input caused an overflow: check errno after the call.

---

### Post by spadewarrior on 2008-06-14
I'll have a look into strtol again. 

Thanks for having a look. :)

---

### Post by spadewarrior on 2008-06-14
That was certainly good advice.

At the moment this code does the trick:

[PHP]	while(bikes <= 0)
	{
		fgets(bikeStr, sizeof(bikeStr), stdin);
		
		bikes = strtol(bikeStr, &bikePointer, 10);
		
	}[/PHP]

I'm sure it's not as good as it could be, but it's a lot simpler than what I was doing before.

I still don't really understand what the pointer aspect of strtol is for though. Is it just for debugging?

---

### Post by mike_g on 2008-06-14
> I still don't really understand what the pointer aspect of strtol is for though. Is it just for debugging?
Yeah, you can check if the conversion was successful by checking where if the end pointer has changed.

You can also pass the end pointer into subsequent strtol calls to parse multiple numbers. If youre not going to use the edited pointer I think you can pass NULL as the second argument for strtol. That would save a variable and help make what the code does a little more obvious. Apart from that your validation looks good to me.

---

### Post by spadewarrior on 2008-06-14
Ah, didn't realise that you could use NULL there. That makes it a bit nicer.

---

### Post by Lux Perpetua on 2008-06-15
> **spadewarrior said:**
> I still don't really understand what the pointer aspect of strtol is for though. Is it just for debugging?No, in this context, it is for *validation*, which is apparently one of your main goals here. It lets you know if there were extra characters in the string that didn't get parsed as part of the integer that was returned, which effectively tells you if the string was a valid integer or not.

---

### Post by nvteighen on 2008-06-15
Just for reference, strtol converts strings to **long int**, which in **some** architectures is the same as an integer. If you plan to use it, declare the variable where you store the converted as a long or perform a (int) cast, so you don't get different results in different platforms.

To convert to "strict" integers, use atoi(). It has less functionality (it doesn't gives you the pointer to the first non-convertable character), but may be enough for simple tasks as this.

Anyway, here's a lot of choice. Do what you like most! ;)

---

