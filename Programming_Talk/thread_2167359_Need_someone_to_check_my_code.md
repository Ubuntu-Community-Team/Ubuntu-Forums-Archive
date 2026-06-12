---
title: "Need someone to check my code"
date: 2013-08-13
forum: Programming Talk
---

### Post by Ninja&gt;Master on 2013-08-13
Hi,
After I saw the Programming Challenges in this forum, I got real excited. I started solving from Beginner's Challenge #2. It was after I completed, I saw that the thread was closed. So I want someone to check the code, that took me a while of hard work to make perfect. According to me it has zero bugs and can't be broken no matter what the user inputs. Any comment is greatly appreciated.
Here is the code (in C#):
```

using System;


public class Challenge_2
{
	static string myName;
	static string myAge;
	static string myUserID;
	
	//The main function
    public static void Main()
    {
		Console.WriteLine("Please answer all questions wisely.");
		Console.WriteLine("Type 'quit' anytime to exit.");
		Console.WriteLine(" ");
		name();
		Console.WriteLine(" ");
		age();
		Console.WriteLine(" ");
		userID();
		Console.WriteLine(" ");
		string nextAge = Convert.ToString(Convert.ToInt32(myAge)+1);
		string nextID = Convert.ToString(Convert.ToInt32(myUserID)+1);
		Console.WriteLine("You are {0}, aged {1} next year you will be {2}, with user ID {3}, the next user is {4}.", myName, myAge, nextAge, myUserID, nextID);
	}
	//Function for checking whether Username has 0 chars or starts with a space or not
	public static bool check_for_space(string s)
	{
		if(s.Length == 0)
		{
			return true;
		}
		if(s.Substring(0, 1) == " ")
		{
			return true;
		}
		else
		{
			return false;
		}
	}
	//Function that handles the name input
	public static void name()
	{
		Console.WriteLine("What is your forum name?");
		Console.Write(">> ");
		myName = Console.ReadLine();
		if(myName.ToLower() == "quit")
		{
			Environment.Exit(0);
		}
		if(myName.Length > 20)
		{
			myName = myName.Substring(0, 20);
		}
		while(check_for_space(myName) == true)
		{
			Console.WriteLine("Name can't begin with space/have 0 length.");
			Console.Write("Please enter a valid forum name: ");
			myName = Console.ReadLine();
			if(myName.Length > 20)
			{
				myName = myName.Substring(0, 20);
			}
			if(myName.ToLower() == "quit")
			{
				Environment.Exit(0);
			}
		}
	}
	//Function that converts a string to int and checks whether its in the given limit or not
	public static bool limit_checker(string x, int lim_x, int lim_y)
	{
		try
		{
			int _age_ = Convert.ToInt32(x);
			if(_age_ <= lim_x || _age_ > lim_y)
			{
				return false;
			}
			else
			{
				return true;
			} 
		}
		catch
		{
			return false;
		}
	}
	//Function that handles the age input
	public static void age()
	{
		Console.WriteLine("What is your age?");
		Console.Write(">> ");
		myAge = Console.ReadLine();
		if(myAge.ToLower() == "quit")
		{
			Environment.Exit(0);
		}
		while(limit_checker(myAge, 0, 120) != true)
		{
			Console.WriteLine("That isn't a valid age!");
			Console.Write("Please enter your age: ");
			myAge = Console.ReadLine();
			if(myAge.ToLower() == "quit")
			{
				Environment.Exit(0);
			}
		} 
	}
	//Function that handles the userID input
	public static void userID()
	{
		Console.WriteLine("What is your User ID?");
		Console.Write(">> ");
		myUserID = Console.ReadLine();
		if(myUserID.ToLower() == "quit")
		{
			Environment.Exit(0);
		}
		while(limit_checker(myUserID, 0, 999999) != true)
		{
			Console.WriteLine("UserID must be in the range: 0 < x < 1000000.");
			Console.Write("Please enter a valid user ID: ");
			myUserID = Console.ReadLine();
			if(myUserID.ToLower() == "quit")
			{
				Environment.Exit(0);
			}
		}
	}
}

```

---

### Post by Ninja&gt;Master on 2013-08-13
Come on, someone please?

---

### Post by david40 on 2013-08-13
What exactly are you doing? I compiled it and it works flawlessly, but it did nothing other than ask for some information. Then close once it got the userid.

---

### Post by Ninja&gt;Master on 2013-08-14
> **david40 said:**
> What exactly are you doing? I compiled it and it works flawlessly, but it did nothing other than ask for some information. Then close once it got the userid.

You might want to read this then: [http://ubuntuforums.org/showthread.php?t=881152](http://ubuntuforums.org/showthread.php?t=881152) <-- This is what I'm doing.

You have to open it via CMD (on Windows) or Terminal (on Unix/Linux).

On Windows (open up CMD):
```

cd /path/to/the/compiled/file
compiled_file.exe

```

On Linux (Open Terminal):
```

cd /path/to/the/compiled/file
mono compiled_file.exe

```

You couldn't read the output because it closed exactly after showing the output.

---

### Post by david40 on 2013-08-14
Gotcha. Just call ReadLine:

```
[FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]        
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Console[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].WriteLine([/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"You are {0}, aged {1} next year you will be {2}, with user ID {3}, the next user is {4}."[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2], myName, myAge, nextAge, myUserID, nextID);[/SIZE][/FONT][/SIZE][/FONT]
[FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]
        
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Console[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].ReadLine();
```[/SIZE][/FONT][/SIZE][/FONT]
[FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT]

What that will do is keep the name, age, next age, id, next id until some key is pressed. Once a key is entered the application will close.

---

### Post by trent.josephsen on 2013-08-14
Don't do that. Just run it from the command line like it's supposed to be run.

That said...

I don't have Mono or Windows so I'll just throw some general advice at you:

1) Functions have return values for a reason. Don't let name() modify a global (class) variable; have it return the name and store the return value in a local variable inside Main(). (Same goes for age and userID.)

2) Functions also take arguments for a reason. Observe that age() and userID() both do the same thing, merely with a different prompt and different bounds on the return value. Consider making a helper function like get_checked_int(lower_bound, upper_bound).

3) I think C#'s strings are dynamically allocated, so there's no really good reason to impose a 20-character limit. I know it was allowed as part of the challenge, but that was more for the sake of people using unmanaged languages like C.

4) Jeanne Calment would have had trouble using your program. She died before C# was a thing, but you might run into trouble again in a few years. Think about whether the hard limits your program imposes make sense.

5) If you post a new thread, and nobody's responded after a few hours, don't bump it by posting again. Knowledgeable people will not be encouraged to help you if you come across as annoying or needy. Some people were at work or asleep when you posted your original question. Some people only browse UF on the weekends. You should give it at least a few days of inactivity before giving up.

I have some other thoughts but they depend on how you rewrite the program. I'll be happy to share any that still apply if you rewrite it and post the new code.

---

