---
title: "Choosing a random string?"
date: 2007-10-18
forum: Programming Talk
---

### Post by sdmike on 2007-10-18
I want the program to chose a random word or string from my file. How do I do that? 

So if the user gets 6 wrong the program closes but if they get it right it loops and grabs a random word from the file.


my data file looks like this:
```
apple orange watermelon pineapple cherry guava pomegranate grape avocado tomatoe
```

```
#include <iostream>
#include <iomanip>
#include <fstream>
#include <string>
#include <cmath>

using namespace std;

int point;

int main()
{

string guess;
int point =0;
int trys = 0;

ifstream inFile;
inFile.open("answers.dat");

string one, two, three, four, five, six, seven, eight, nine, ten;

inFile >> one >> two >> three >> four >> five >> six >> seven >> eight >> nine >> ten;

inFile.close();

cout << "welcome to Guess it, now lets begin" << endl;

while (trys < 6 )
{
cout << "what kind of fruit am I thinking of? Note not to use plural words!" << endl;
cin >> guess;

if (guess == one)
{
cout << "you guessed correctly" << endl;
point++;
}

else
{
trys++;
}

}

cout << "Sorry you lost because you couldn't answer in " << trys << " trys" << endl;

return 0;
}
```

---

### Post by pmasiar on 2007-10-18
And now, something completely different: solution in Python:
[php]
import random
choices = 'apple orange watermelon pineapple cherry guava pomegranate grape avocado tomatoe'.split(' ')
x = random.choice(choices)
[/php]
(nobody expects Inquisition :-) )

---

### Post by sdmike on 2007-10-18
> **pmasiar said:**
> And now, something completely different: solution in Python:
[php]
import random
choices = 'apple orange watermelon pineapple cherry guava pomegranate grape avocado tomatoe'.split(' ')
x = random.choice(choices)
[/php]
(nobody expects Inquisition :-) )

why are the choices being listed when they are going to be grabbed from the file?

Also would this be put inside the loop or the function?

Is there another way this can be done?

---

### Post by Wybiral on 2007-10-18
1. Indent your source code!
2. Use an STL vector (manually defining those variables is wasteful)
3. (after you have them in a vector) look up the "rand()" function.

If this fails, resort to an easier language (especially one that will teach you how to indent your code, such as Python).

---

### Post by pmasiar on 2007-10-18
> **sdmike said:**
> why are the choices being listed when they are going to be grabbed from the file?

My goal was to show (off :-) ) the random.choice() function.

If you want to read choices from file:

choices = open('answers.dat').read().split(' ')

> Also would this be put inside the loop or the function?

Obviously outside: choices do not change inside the loop, so why repeated file reading?

> Is there another way this can be done?

Obviously. It is "matter of simple programming". :-) It is software, everything can be changed. It was all joke.  I noticed how hard to have to work in C to make it happen, if C is not hard requirement, Python is **much** simpler to learn, and have fun doing it.

---

### Post by NiklasV on 2007-10-18
This should do it. Read up on vectors (a dynamic type of array) and the rand() function. Note that without seeding, the rand() function will return the same numbers every time. To rectify this, you can seed the random values generator with the current time to get different pseudo-random integers every time you run the program.

[php]
#include <iostream>
#include <fstream>
#include <string>
#include <vector>

using namespace std;

int point;

int main()
{
	string guess,randomAnswer;
	int point =0;
	int trys = 0;
	
	ifstream inFile;
	inFile.open("answers.dat");
	
	vector<string> answers; //replace the different variables with one vector, this will make the program a whole lot easier to write
	string tmp;
	
	while(!inFile.eof()) { //Loop until the file ends (When that happens, the eof() function will return true)
		inFile >> tmp; //put the next word into the temporary variable.
		answers.push_back(tmp); //add the temp variable to the vector.
	}

	int numberOfAnswers = answers.size() - 1;
	
	inFile.close();
	
	cout << "welcome to Guess it, now lets begin" << endl;
	while(trys < 6) {
		int randomInteger = rand() % numberOfAnswers; //This will return the remainder of division of the psuedo-random floating point number between 0 and 1 with the numberOfAnswers variable, ie an integer between 0 and numberOfAnswers
		trys=0;
		while (trys < 6 )
		{
			cout << "what kind of fruit am I thinking of? Note not to use plural words!" << endl;
			cin >> guess;
			
			if (guess == answers[randomInteger])
			{
				cout << "you guessed correctly" << endl;
				point++;
				break; //Break this loop and go on to the next question.
			}
			
			else
			{
				trys++;
			}
			
		}
	}
		
	cout << "Sorry you lost because you couldn't answer in " << trys << " trys" << endl << "Total points: " << point;

	return 0;
}
[/php]

---

### Post by cwaldbieser on 2007-10-19
> **sdmike said:**
> why are the choices being listed when they are going to be grabbed from the file?

Also would this be put inside the loop or the function?

Is there another way this can be done?

[http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/59865]("http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/59865")

---

### Post by Siph0n on 2007-10-19
Not a big deal, but you spelt tomato wrong ;)

---

### Post by sdmike on 2007-10-20
> **NiklasV said:**
> This should do it. Read up on vectors (a dynamic type of array) and the rand() function. Note that without seeding, the rand() function will return the same numbers every time. To rectify this, you can seed the random values generator with the current time to get different pseudo-random integers every time you run the program.

[php]
#include <iostream>
#include <fstream>
#include <string>
#include <vector>

using namespace std;

int point;

int main()
{
	string guess,randomAnswer;
	int point =0;
	int trys = 0;
	
	ifstream inFile;
	inFile.open("answers.dat");
	
	vector<string> answers; //replace the different variables with one vector, this will make the program a whole lot easier to write
	string tmp;
	
	while(!inFile.eof()) { //Loop until the file ends (When that happens, the eof() function will return true)
		inFile >> tmp; //put the next word into the temporary variable.
		answers.push_back(tmp); //add the temp variable to the vector.
	}

	int numberOfAnswers = answers.size() - 1;
	
	inFile.close();
	
	cout << "welcome to Guess it, now lets begin" << endl;
	while(trys < 6) {
		int randomInteger = rand() % numberOfAnswers; //This will return the remainder of division of the psuedo-random floating point number between 0 and 1 with the numberOfAnswers variable, ie an integer between 0 and numberOfAnswers
		trys=0;
		while (trys < 6 )
		{
			cout << "what kind of fruit am I thinking of? Note not to use plural words!" << endl;
			cin >> guess;
			
			if (guess == answers[randomInteger])
			{
				cout << "you guessed correctly" << endl;
				point++;
				break; //Break this loop and go on to the next question.
			}
			
			else
			{
				trys++;
			}
			
		}
	}
		
	cout << "Sorry you lost because you couldn't answer in " << trys << " trys" << endl << "Total points: " << point;

	return 0;
}
[/php]

Thank you for the comments, this made a lot of sense.

---

