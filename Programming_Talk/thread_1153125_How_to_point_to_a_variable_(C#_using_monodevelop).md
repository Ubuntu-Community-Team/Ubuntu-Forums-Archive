---
title: "How to point to a variable (C# using monodevelop)"
date: 2009-05-08
forum: Programming Talk
---

### Post by bramming on 2009-05-08
Hey. Im currently writing a GUI app to calculate a scheme for Dungeons and dragons roleplay. I figured this would be a good start (since im new to c#). In general my programming experience is limited to working with some simple classes.

The program looks like this:

[[IMG]http://img26.imageshack.us/img26/5261/nyged.th.png[/IMG]](http://img26.imageshack.us/my.php?image=nyged.png)

Each stat (str, dex, etc) has values for "ability score", "ability modifier", "race modifier" and "cost".

All those are represented in global variables. Also each stats has a "+" and "-" button to raise and lower the "ability score".

The thing is, instead of having a billion of methods for each button click, i want to make all button-click-signals to refer to the same method. That method would then based on its sender, perform the calculations and then correct the "right" variables. For instance if i click the "+" button for "str" the variables "str" has (the "abilityscore", etc variables) will then get calculated and changed.

This can easily be done by having each button having its own method, and then calculate everything and change the variables defined in the method. However i think its pretty ineffecient having 2x6 methods running the same code, just writing to different variables.

So what im trying to ask help for is: The 1 method i wanna have to handle all the click signals, has to write to different variables depending on the sender. So coding would roughly look like this:

```
protected virtual void OnPressStats (object sender, System.EventArgs e)
	{

	// if the sender is the "+" or "-" button for "str"
	if (sender == btnStrP || sender == btnStrM)
	{
	(some kind of pointer) = ASstr (the abilityscore variable for strength)		
	}
if (sender == btnDexP || sender == btnDexM)
	{
	(some kind of pointer) = ASdex (the abilityscore variable for dex)		
	}
	(some kind of pointer) = (something based on calculations) 


	}

```
so that in the calculations i can use (some kind of pointer) to get values and set values to the different variables depending on which button is pressed.

This way, the same method can be used for all buttons, because they change different variables (ASstr, ASdex, etc) based on the sender.


I hope i have been able to express myself clearly enough for you to understand. English isnt my native language so there might be some grammatical errors etc.
Please let me know if i have to express myself more clearly,
and **thanks in advance!**

---

### Post by SKLP on 2009-05-08
Sorry If I'm unhelpful, but I didn't clearly understand what you want to do.

I don't really see why you would need a pointer since you can simply store the variables in the class fields(for example). You can cast the "object sender" parameter to a certain type if you need to manipulate the sender object in any way. That way you could check for different buttons...

---

### Post by bramming on 2009-05-09
My problem is like having buttons named 1,2,3,4 and 5.

All buttons have variables named 1a, 1b, 1c, 2a, 2b, 2c etc. so all buttons have 3 variables.

So instead of having a:

```
if (sender == 1)
{
//perform long calculations and change 1a
//perform long calculations and change 1b
//perform long calculations and change 1c
}
if (sender == 2)
{
//perform long calculations and change 2a
//perform long calculations and change 2b
//perform long calculations and change 2c
}
if (sender == 3)
{
//perform long calculations and change 3a
//perform long calculations and change 3b
//perform long calculations and change 3c
}
//etc
```

Then instead having something looking like this:

```
"something" pointtovariablea;
"something" pointtovariableb;
"something" pointtovariablec;
if (sender == 1)
{
pointtovariablea = 1a;
pointtovariableb = 1b;
pointtovariablec = 1c;
}
if (sender == 2)
{
pointtovariablea = 2a;
pointtovariableb = 2b;
pointtovariablec = 2c;
}
if (sender == 3)
{
pointtovariablea = 3a;
pointtovariableb = 3b;
pointtovariablec = 3c;
}

//perform long calculations and change pointtovariablea
//perform long calculations and change pointtovariableb
//perform long calculations and change pointtovariablec
```

So all calculations are only written once, instead of having the calculations written at each button. So im trying to make the calculations change specific variables (1a, 1b, 1c if button 1 is clicked, button 2a, 2b, 2c if button 2 is clicked, etc) without having a ton of "if"'s each having the same calculations just with different variables. Hope thats clear enough :) and thanks for the reply  SKLP :)


Note: The first example might seem shorter code-wise, but the calculations are pretty long so its actually longer. I just left out the specific calculations to avoid confusion :)

---

### Post by SKLP on 2009-05-09
Now I kinda understand what you want to do, but I don't think you can do it in that specific way... Maybe instead use something like this:

```

if (sender == 1)
{
	CalculateStuff(ref 1a, ref 1b, ref 1c);
}
if (sender == 2)
{
	CalculateStuff(ref 2a, ref 2b, ref 2c);
}
if (sender == 3)
{
	CalculateStuff(ref 3a, ref 3b, ref 3c);
}

And create the function that's used above:

private void CalculateStuff(ref int a, ref int b, ref int c)
{
	//perform your calculations
}

```



(This should work, however there are obviously ways to make the code shorter (things like grouping values a,b,c together in a class/struct, and similar things) )

---

### Post by bramming on 2009-05-09
> **SKLP said:**
> Now I kinda understand what you want to do, but I don't think you can do it in that specific way... Maybe instead use something like this:

```

if (sender == 1)
{
	CalculateStuff(ref 1a, ref 1b, ref 1c);
}
if (sender == 2)
{
	CalculateStuff(ref 2a, ref 2b, ref 2c);
}
if (sender == 3)
{
	CalculateStuff(ref 3a, ref 3b, ref 3c);
}

And create the function that's used above:

private void CalculateStuff(ref int a, ref int b, ref int c)
{
	//perform your calculations
}

```



(This should work, however there are obviously ways to make the code shorter (things like grouping values a,b,c together in a class/struct, and similar things) )

YES! :D its exactly what im looking for:D now it all works and i save tons of code and a lot of time :) thanks for the help, much appreciated!

---

