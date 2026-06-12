---
title: "C++ Restart Application code"
date: 2008-03-19
forum: Programming Talk
---

### Post by joseph_rothwell on 2008-03-19
Hi. I have only been learning C++ for a couple of weeks, so I am still a bit low-levelled.

Anyway, my question is as thus;

Is there a piece of code that can restart an application?

Here is a sample of my code;
[QUOTE="code"]
	cout << "Would you like to restart this application. Type 'yes' or 'no'";
	getline(cin, strrestart)
	
	if (strrestart == "yes")
	{
		//I haven't got a clue as to what to put here.
		cout << "Just putting a sentence here so it has something to do";
	}
	else
	{cout << "Thanks for using the application";
	return 0;}[/QUOTE]

Just so you know, I have already started the string strrestart, so it works. I just need to know if there is a piece of code I can use to start the application again.
Thanks, Joseph Rothwell.

NOTE: The program is a dictionary run through the terminal. Because of this, I need a restart so people can type a word, get the answer, then type a new one. However, rather than have lots and lots of code, I want to just be able to restart the app.

Thanks for the help in advance.

-------------------------------------
SUPPORT OPEN SOURCE

---

### Post by LaRoza on 2008-03-19
If you want to do something repeatedly, use a loop.

```

while QUIT == FALSE:
    DO task

```

---

### Post by tht00 on 2008-03-19
Yeah, your best bet is to use a while-loop.

Syntax looks something like this:

```

while(condition){
     //do something;
}
```


Modifying your code, it would look something like this:```

strrestart == "yes";

while(strrestart == "yes"){
     //do something;
     
     cout << "Restart loop?  yes/no";
     getline(cin, strrestart);
}
return 0;
```

I'm not sure that code will work as expected... I remember strings comparison being trickier than that in C++, but that's the idea.

Loops are vital to know in programming and allow you to repeat parts of code continuously.
--*For-loop*, you can loop code a set number of times.  Useful for looping through known amounts of variables for comparisons, sorting, etc.
Real application -- Yahtzee.  You roll 6 dice.  Rather than calling a 'roll_die' function 6 times, you could use a for-loop, since you know how many time you want it repeated (6).

--*While-loops* are perfect for looping through something until a *condition* is met.  Loop until the user enters something specific.  Loop until any condition is true/false.
Real application -- Yahtzee again.  You want to loop until the game is completed, so, you could set up a function that checks if the game is finished (all values are filled).  If not, you'd want to continue the game (roll more dice).


There are other ways to repeat sections of code (like recursion), but these two types of loops (for, while) are incredibly useful and important in controlling program flow.  And it's possible to create infinite loops... loops that never end.  They happen once in a while.  Good to be aware of them.

Infinite loop:
```
while(true){
   cout << "Weeeee!!";
}
```

---

