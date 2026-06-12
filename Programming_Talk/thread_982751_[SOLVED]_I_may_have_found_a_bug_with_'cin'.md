---
title: "[SOLVED] I may have found a bug with 'cin'"
date: 2008-11-15
forum: Programming Talk
---

### Post by hessiess on 2008-11-15
recently I have had to produce some very simple programs for a course module, and wanting to get them done as quickly as possible I constructed the interfaces using cout/cin i.e.

[PHP]#include<iostream>

using namespace std;

int main()
{
	for(;;)
	{
		int selection = 0;

		cout<<"    What food do you like?"<<endl;
		cout<<"        1) Curry"<<endl;
		cout<<"        2) Pizza"<<endl;
		cout<<"        3) Burger"<<endl;
		cout<<"        4) Hot dog"<<endl<<endl;

		cin>>selection;

		cout<<"You like ";

		if(selection == 1)
		{
			cout<<"curry!";
			break;
		}

		else if(selection == 2)
		{
			cout<<"Pizza!";
			break;
		}

		else if(selection == 3)
		{
			cout<<"Burger!";
			break;
		}
	
		else if(selection == 4)
		{
			cout<<"Hot dog!";
			break;
		}

		else
		{
			cout<<endl<<"Not a valid selection"<<endl;
		}
	}
}[/PHP]

If you enter a number everything works as it should, but if you enter some other character, the program goes into an infanate loop repeatedly displaying the options.

---

### Post by phantomgunex on 2008-11-15
Sorry accidentally posted on the wrong thread!

---

### Post by rye_ on 2008-11-15
Afraid not;

you've got an infinite loop in all circumstances when "selection" is not 1 to 4.

Ryan

---

### Post by Tony Flury on 2008-11-15
it is not a bug - well it is, but not in cin - the bug is in your design.

your line cin >> selection is asking the system to look for a valid integer value on stdin - when you don't type anything that is valid (i.e. a letter) it can't store than in a integer - so you get what you think is your bug.

What you probably need to do is read in characters, and then test to see if the characters are in fact valid choices.

you also might want to look at the C construct called switch to make your code nicer (rather than all those ifs).

---

### Post by hessiess on 2008-11-15
> **rye_ said:**
> Afraid not;

you've got an infinite loop in all circumstances when "selection" is not 1 to 4.

Ryan

If it is not between 1 and 4 it should display 'Not a valid salection' and ask again, try entering 7 for example. But if a character is entered the cin object seems to refuse any more input and the program just keeps looping.

---

### Post by samjh on 2008-11-15
Again, it's your code, not the cin.

Your code says that an integer should be extracted from the input stream.  However if the value in the input stream is of the wrong type, then the value cannot be extracted, a failbit will be set to 1, and further operations on that stream will be ignored.  This is why your program will not stop at the next cin>>selection; it is ignored because of the type error.

In order to return the input stream to a normal state, you need to do a cin.clear() and cin.ignore(), like this:
```
...
		else
		{
			cout<<endl<<"Not a valid selection"<<endl;
			cin.clear();
			cin.ignore(1, ' ');
		}
...
```

More about [cin.clear()](http://www.cplusplus.com/reference/iostream/ios/clear.html)
More about [cin.ignore(streamsize, int)](http://www.cplusplus.com/reference/iostream/istream/ignore.html)

---

### Post by hessiess on 2008-11-15
I can see why cin returns an error if something went wrong, like the user entering a character into an integer. But completely disabling the stream, refusing more input and thus creating an infinite loop, 
that just isn't logical...

---

### Post by dwhitney67 on 2008-11-15
> **hessiess said:**
> ...and thus creating an infinite loop, 
that just isn't logical...
The infinite loop is in YOUR code.  See this statement:
[php]
for(;;)
[/php]
That is what is causing the infinite loop.  Samjh has provided the information needed to clear the input stream.  However, I would recommend that you clear a lot more than just one character when calling cin.ignore().  After all, the operator could type in multiple characters (i.e. a string) at the prompt.
[php]
cin.ignore(1024, '\n');   // use a '\n'; it is the last character the user will enter.
[/php]

---

