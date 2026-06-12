---
title: "C++ Problems"
date: 2010-07-15
forum: Programming Talk
---

### Post by Amorstus on 2010-07-15
OK, this is a little program in C++ I have been making but I cannot seem to figure out what exactly is going wrong (Oh and why it is about cats I have absolutely no idea). The part that is tripping up the compiler is (Right after the comment to be exact)
```

int Total()
{
	//Add all the cats together to get our total number so we can dynamically provide it to the user.
	::user_total + ::hiscat_total = ::TotalCat;
	::hercat_total + ::TotalCat = ::TotalCat;
	
	cout << ::TotalCat;
}

```

It is telling me that "Lvalue required as left operand of assignment." The whole program is a follows:
```

#include <iostream>

using namespace std;

int hercat_total;
int hiscat_total;
int user_total;
int TotalCat;

int ThinkingHer()
{
	using namespace std;
	int her_cats = -1;
	her_cats = her_cats * -2 + 5 - 3;
	cout << "I actually have " << her_cats << " cats!" << endl;
	//Apply the her_cats value from this function to the external variable so we can add it to his cats later.
	her_cats = ::hercat_total;
}
	
int ThinkingHim()
{
	using namespace std;
	int his_cats = -1;
	his_cats = his_cats + 2 * 3;
	cout << "I have " << his_cats << " cats";
	if(his_cats > 3)
	{
		cout << " which is many cats!" << endl;
	}
	else 
	{
		cout << " which is some cats but not many!" << endl;
	}
	his_cats = ::hiscat_total;
}

int UserInput()
{
	using namespace std;
	int user_cats;
	cin >> user_cats;
	if(user_cats > 5)
	{
		cout << user_cats << " cats?" << " Wow, that is more cats than either of us!" << endl;
	}
	else if(user_cats == 5) 
	{
		cout << "Five Cats? You have as many cats as him!" << endl;
	}
	else if (user_cats == 4)
	{
		cout << "Four cats? You have as many cats as her!" << endl;
	}
	else if(user_cats == 3)
	{
		cout << "Three cats? You don't have as many cats as either of us but you still have a lot!" << endl;
	}
	else if(user_cats == 2)
	{
		cout << "Two cats? Hopefully they get along." << endl;
	}
	else if(user_cats == 1)
	{
		cout << "Only one cat? That is surprising." << endl;
	}
	else if(user_cats == 0)
	{
	cout << "No cats? You really should look into getting some!" << endl;
	}
	else if(user_cats < 0)
	{
		cout << "Stop messing with us. You can't have " << user_cats << " cats!" << endl;
		
		//Set user cats to zero so when we add it to the main function, it will not reduce the number.
		user_cats = 0;
	}
	else
	{
		//For some reason, this function is not triggered when using letters. They must default to one.
		cout << "Hm... I didn't understand you there..." << endl;
	}
	user_cats = ::user_total;
}

int Total()
{
	//Add all the cats together to get our total number so we can dynamically provide it to the user.
	::user_total + ::hiscat_total = ::TotalCat;
	::hercat_total + ::TotalCat = ::TotalCat;
	
	cout << ::TotalCat;
}
		
// Conversation and calling of functions for values is handled in next function.
int main()
{
	using namespace std;
	
	cout << "SYSTEM: Hit the Enter bar twice to go to the next line of the conversation" << endl;
	
	//Wait for user to hit key to increase interactivity.
	cin.clear();
	cin.ignore(255, '\n');
	cin.get();
	//End waiting for user area.
	
	cout << "Hello world!" << endl;
	
	//Wait for user to hit key to increase interactivity.
	cin.clear();
	cin.ignore(255, '\n');
	cin.get();
	//End waiting for user area.
	
	cout << "How are you?" << endl;
	
	//Wait for user to hit key to increase interactivity.
	cin.clear();
	cin.ignore(255, '\n');
	cin.get();
	//End waiting for user area.
	
	cout << "I am fine thanks." << endl;
	
	//Wait for user to hit key to increase interactivity.
	cin.clear();
	cin.ignore(255, '\n');
	cin.get();
	//End waiting for user area.
	
	cout << "How many cats do you have?" << endl;
	
	//Wait for user to hit key to increase interactivity.
	cin.clear();
	cin.ignore(255, '\n');
	cin.get();
	//End waiting for user area.
	
	ThinkingHim();
	
	//Wait for user to hit key to increase interactivity.
	cin.clear();
	cin.ignore(255, '\n');
	cin.get();
	//End waiting for user area.
	
	cout << "Wow you have quite a few cats!" << endl;

	//Wait for user to hit key to increase interactivity.
	cin.clear();
	cin.ignore(255, '\n');
	cin.get();
	//End waiting for user area.
	
	cout << "So how many cats do you have?" << endl;
	
	//Wait for user to hit key to increase interactivity.
	cin.clear();
	cin.ignore(255, '\n');
	cin.get();
	//End waiting for user area.
	
	ThinkingHer();
	
	//Wait for user to hit key to increase interactivity.
	cin.clear();
	cin.ignore(255, '\n');
	cin.get();
	//End waiting for user area.
	
	cout << "So user, how many cats do you own?" << endl;
	cout << "SYSTEM: Input the number here and hit Enter." << endl;
	UserInput();
	
	//Wait for user to hit key to increase interactivity.
	cin.clear();
	cin.ignore(255, '\n');
	cin.get();
	//End waiting for user area.
	
	cout << "So how many cats do we have total?" << endl;
	
	//Wait for user to hit key to increase interactivity.
	cin.clear();
	cin.ignore(255, '\n');
	cin.get();
	//End waiting for user area.
	
	cout << "There is " << Total() << " cats total!";
	
	//Wait for user to hit key to increase interactivity.
	cin.clear();
	cin.ignore(255, '\n');
	cin.get();
	//End waiting for user area.
	
	return 0;
}


```

Any ways to solve this and general tips would be greatly appreciated.

---

### Post by Some Penguin on 2010-07-15
LVALUE = value on left of expression; i.e. A in 'A = B+C'.

And 'B+C = A' is not valid; you want 'A=B+C'.  It's assignment, not equality.

---

### Post by Amorstus on 2010-07-15
Well, after changing the one part that I described and a couple more I finally got it to work. Just one more thing, I am wondering what would be the best way to generate a random whole number with a range of like 1 to 10?

---

### Post by dwhitney67 on 2010-07-15
The easiest way to go about generating a "random" number is to use the srand() and rand() C library functions.

For example:
```

#include <cstdlib>
#include <ctime>

int main()
{
   srand(time(0));   // use a large number to seed the random-number generator

   int randomNum = (rand() % 10) + 1;   // number from [1,10]

   // ...
}

```

---

