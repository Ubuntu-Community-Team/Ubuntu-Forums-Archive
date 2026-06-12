---
title: "c++ problems"
date: 2009-12-08
forum: Programming Talk
---

### Post by karimruan on 2009-12-08
Decided to learn c++ instead of digging around to find a free basic that suited me. So, I am using Geany to write, build, and compile the code. But, I get the following errors on my code:

```

mat@mat-laptop:~$ g++ friendbot.cpp -o code
friendbot.cpp: In function ‘int main()’:
friendbot.cpp:56: error: ‘yesNo’ was not declared in this scope
friendbot.cpp:63: error: ‘talk’ was not declared in this scope
friendbot.cpp:68: error: ‘talk’ was not declared in this scope
friendbot.cpp:73: error: ‘talk’ was not declared in this scope
friendbot.cpp:76: error: ‘talk’ was not declared in this scope

```


here is the block of code that the error resides in:


```

#include <iostream>
#include <string>
using namespace std;

int main()
{
	string name;  // calls string variable called name
	cout << "Hello, my new found friend!\n";
	cout << " My name is FriendBot, what is yours?\n\n\n\n";
	getline (cin, name);    //this will get the whole line, not just the first word
	cout <<"\n\nHello " << name <<", It is good to meet you!\n";
	cout <<"How are you feeling today?\n\n\n\n";
	string feeling;  // calls the string variable called feeling
	getline (cin, feeling);
	cout <<"\nYou make me feel " <<feeling <<" too!\n";
	cout <<"\n  ";
	cout <<"\n\n\n\n";
	cout <<"So what do you want to talk about?\n\n\n\n";
	string subject;
	getline(cin, subject);
	cout <<"Well, as for " <<subject <<", I personally don't like it.\n\n";
	cout <<"What is your mothers first name?\n\n\n\n";
	string momFirstName;
	getline(cin, momFirstName);
	cout <<"Oh, I remember " <<momFirstName <<"! She was playing with me last night!\n\n";
	cout <<"\nIs there something you want to say?\n\n\n\n\n";
	string youSay;
	getline(cin, youSay);
	cout <<"Oh, so you say, " <<youSay <<" huh?\n\n";
	cout <<youSay <<" back at ya bub!\n";
	cout <<"\n\n\n\n";
	cout <<"Do you like movies?";
	string yesNO;
	getline(yesNo);
	if (yesNo == "yes"){
		cout <<"So, you say you like movies?\n";
		cout <<"What's your favourite?\n";
		string favMovie;
		getline(cin, favMovie);
		cout <<favMovie <<"? That sounds like a porno!\n";
		talk();
	}
	
	else if (yesNo == "no"){
		cout <<"Only a terd doesn't like movies.\n";
		talk();
	}
	
	else {
		cout <<"What does " <<yesNo <<" mean?\n";
		talk();
	}
	
	talk();
}
	
	
int talk()
{
	cout <<"COMING SOON!\n";
	
	
	
	return 0;
}

```


Any ideas what i am doing wrong? I have only been studying for a day.

---

### Post by Simon17 on 2009-12-08
You declared the string "yesNO" but later you wrote "yesNo"

---

### Post by RiceMonster on 2009-12-08
You need to add a function prototype for talk before main

```
void talk ();
```

also, making this function have a return type of int is useless if you're not actually returning anything. Use void as seen above, and remove "return 0" from the function.

Edit:

Why are you using getline to read a string?

Do this:
```
cin >> YesNO;
```

Stop adding "\n" to the ends of you're lines as well. You should do this in c++:
```
cout << "hello world!" << endl;
```

You also don't have return 0; in main.

---

### Post by cta16 on 2009-12-08
> **RiceMonster said:**
> You need to add a function prototype for talk before main

```
void talk ();
```

also, making this function have a return type of int is useless if you're not actually returning anything. Use void as seen above, and remove "return 0" from the function.



Another way to solve the 'talk' problem would be to move the talk function above the main function. That way, you won't have to add a prototype.

---

### Post by karimruan on 2009-12-08
> **RiceMonster said:**
> You need to add a function prototype for talk before main

```
void talk ();
```

also, making this function have a return type of int is useless if you're not actually returning anything. Use void as seen above, and remove "return 0" from the function.

Edit:

Why are you using getline to read a string?

Do this:
```
cin >> YesNO;
```

Stop adding "\n" to the ends of you're lines as well. You should do this in c++:
```
cout << "hello world!" << endl;
```

You also don't have return 0; in main.


I am using getlin to read strings because it is the only way i know. Can i use cin >> to return a string?

UPDATE:

I now get the following error message after correcting the above errors:

```

mat@mat-laptop:~$ g++ friendbot.cpp -o code
friendbot.cpp: In function &#8216;int main()&#8217;:
friendbot.cpp:63: error: cannot convert &#8216;std::string&#8217; to &#8216;char**&#8217; for argument &#8216;1&#8217; to &#8216;__ssize_t getline(char**, size_t*, FILE*)&#8217;
mat@mat-laptop:~$ 

```

I really don't understand this one, I think it is telling me I wrote my if...else if statement wrong.

Here is the code block with the error...

```

string yesNo;
	getline(yesNo);
	if (yesNo == "yes"){
		cout <<"So, you say you like movies?\n";
		cout <<"What's your favourite?\n";
		string favMovie;
		getline(cin, favMovie);
		cout <<favMovie <<"? That sounds like a porno!\n";
		talk();
	}
	
	else if (yesNo == "no"){
		cout <<"Only a terd doesn't like movies.\n";
		talk();
	}
	
	else {
		cout <<"What does " <<yesNo <<" mean?\n";
		talk();
	}
	
	talk();
}

```

---

### Post by lisati on 2009-12-08
> **karimruan said:**
> I am using getlin to read strings because it is the only way i know. Can i use cin >> to return a string?

cin is a "standard" C++ way of getting input from stdin, and roughly means "console input".

---

### Post by dwhitney67 on 2009-12-08
getline(), if used properly in C++, should be used in a format resembling one of these two function declarations:
```

istream& getline ( istream& is, string& str, char delim );
istream& getline ( istream& is, string& str );

```
By default, the delimiter that is used is the newline character.

Thus the OP requires something similar to:
```

string yesNo;
...
getline(cin, yesNo);

```
One uses getline() when it is desirable to capture all the input from the console leading up to the delimiter.  Thus if multiple words are given, then each of these will be stored into the target string.

If the user types in at the prompt "Mary had a little lamb", then the following statement would only catch the first word of the phrase.
```

cin >> yesNo;

```
This could affect subsequent operations that rely on cin, since the remaining portion of the input ("had a little lamb") is still sitting in the input stream.

In conclusion, when reading input from the console, use getline().

---

### Post by karimruan on 2009-12-08
Thank you, that helps alot. I still need help with my latest error message, posted above, though.

---

### Post by whirlwind on 2009-12-09
Since you're doing this sort of stuff and running into these sorts of problems, reading about cin.clear() and cin.ignore() could not hurt. :)

whirlwind

---

### Post by dwhitney67 on 2009-12-09
> **karimruan said:**
> Thank you, that helps alot. I still need help with my latest error message, posted above, though.

I have no idea what is causing your latest compiler error, because you have not provided updated code.

In your OP, the code you provided had two compiler errors.  One is related to the declaration of the string 'yesNO' and its usage as 'yesNo'.  I recommend that you fix the declaration to correspond with the variable name that you are attempting to use.

The second compiler error was related to the non-existent function prototype for the function talk().  Place a function prototype declaration statement above main() that appears as the following, and that will sort out the issue.
```

int talk();

int main()
{
   ...
}

int talk()
{
   ...
}

```
**_Both_** of these issues have been discussed earlier.

After you have fixed these, you will then be left with another error:
```

friendbot.cpp: In function &#8216;int main()&#8217;:
friendbot.cpp:36: error: no matching function for call to &#8216;getline(std::string&)

```
In my previous post, I explained why the usage of "getline(yesNo)" was incorrect; did you not read this post?  It seems that you are familiar with the usage of getline() because you used it correctly at other places in your program.

P.S.  As another has mentioned, use **endl** to terminate your **cout** statements.

---

### Post by karimruan on 2009-12-09
I got it, here is my updated code. 

```




#include <iostream>
#include <string>
using namespace std;

int talk()
{
	cout << "\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n";
	cout << "Are you still there?";
	string yesNo;
	cin >> (yesNo);
	if (yesNo == "yes"){
		cout << "That sucks. Well, I have to get get laid by\n";
		cout << "another program.";
		// adding break; here doesn't work, errors
	}
	else if (yesNo == "no"){
		cout << "Good. I need to go to bed anyways.\n";
		cout << "TERMINATING PROGRAM............\n";
		// adding break; here doesn't worl, erros
	}
	
	
	return 0;
}

int main()
{
	string name;  // calls string variable called name
	cout << "Hello, my new found friend!\n";
	cout << " My name is FriendBot, what is yours?\n\n\n\n";
	getline (cin, name);    //this will get the whole line, not just the first word
	cout <<"\n\nHello " << name <<", It is good to meet you!\n";
	cout <<"How are you feeling today?\n\n\n\n";
	string feeling;  // calls the string variable called feeling
	getline (cin, feeling);
	cout <<"\nYou make me feel " <<feeling <<" too!\n";
	cout <<"\n  ";
	cout <<"\n\n\n\n";
	cout <<"So what do you want to talk about?\n\n\n\n";
	string subject;
	getline(cin, subject);
	cout <<"Well, as for " <<subject <<", I personally don't like it.\n\n";
	cout <<"What is your mothers first name?\n\n\n\n";
	string momFirstName;
	getline(cin, momFirstName);
	cout <<"Oh, I remember " <<momFirstName <<"! She was playing with me last night!\n\n";
	cout <<"\nIs there something you want to say?\n\n\n\n\n";
	string youSay;
	getline(cin, youSay);
	cout <<"Oh, so you say, " <<youSay <<" huh?\n\n";
	cout <<youSay <<" back at ya bub!\n";
	cout <<"\n\n\n\n";
	cout <<"Do you like movies?";
	string yesNo;
	cin >> (yesNo);
	if (yesNo == "yes"){
		cout <<"So, you say you like movies?\n";
		cout <<"What's your favourite?\n";
		string favMovie;
		getline(cin, favMovie);
		cout <<favMovie <<"? That sounds like a porno!\n";
		talk();
	}
	
	else if (yesNo == "no"){
		cout <<"Only a terd doesn't like movies.\n";
		talk();
	}
	
	else {
		cout <<"What does " <<yesNo <<" mean?\n";
		talk();
	}
	
	talk();
}
	
	

```

I still need to learn to use break; because everytime i use it i get an error message. I will definitely look up the clear and ignore options of cin. Thanks alot, and any suggestions are welcome and appreciated! I am learning, and put this together on my second day of studying c++. If I was in school, it would probably be easier to learn this! But I don't need another degree.....

---

### Post by Xyro on 2009-12-09
You don't want to use break where you've tried. 'break' is used to break out of loops (or switch statements), not functions. Use return instead.

EDIT: In fact, in the way you've written the function 'talk()', it doesn't require anything where you've tried to use break. It will execute the branch according to the value of 'yesNo' and exit the function at 'return 0;'. You may wish to insert an 'else' statement after your 'else if' to handle the case where the user inputs something other than "yes" or "no".

---

### Post by TheBuzzSaw on 2009-12-09
Do not use cin >> aString; as someone suggested. Go back to using getline(cin, aString); as you were before. The problem with doing direct cin >> on a string is that if someone inserts more stuff ("yes no maybe"), the extra input will flood over into another cin statement without even asking.

---

### Post by karimruan on 2009-12-09
Thanks you guys, I will add the else statement. Thanks for everything! What do you guys think of my first program?

---

### Post by Can+~ on 2009-12-09
> **karimruan said:**
> Thanks you guys, I will add the else statement. Thanks for everything! What do you guys think of my first program?

That you should not be doing C++ as first language. Take a look at the stickies.

---

### Post by karimruan on 2009-12-09
> **Can+~ said:**
> That you should not be doing C++ as first language. Take a look at the stickies.

It isn't my first language, it is my second (Not counting javascript). My first was Python. By first program, I meant in c++!

---

### Post by TheBuzzSaw on 2009-12-09
> **Can+~ said:**
> That you should not be doing C++ as first language. Take a look at the stickies.

Sorry, but this is complete garbage. I hear this claim a lot, and frankly, it is just a lot of FUD. C++ is not *that hard* to learn. Yes, there are many advanced topics in C++. It can become very complicated very quickly, but C++ can be used on a simple level too. I grew up using C++. I survived. I must be some anomaly...

Obviously, a lot depends on what a person wants to accomplish with a language, but if someone wants to work toward something relevant in C++ (game development, etc.), there is absolutely nothing wrong with learning C++ as a first language.

No one expects a novice to swallow advanced memory management on day one. Starting with simple number guessing games is good enough for students of the language.

---

### Post by karimruan on 2009-12-10
> **TheBuzzSaw said:**
> Sorry, but this is complete garbage. I hear this claim a lot, and frankly, it is just a lot of FUD. C++ is not *that hard* to learn. Yes, there are many advanced topics in C++. It can become very complicated very quickly, but C++ can be used on a simple level too. I grew up using C++. I survived. I must be some anomaly...

Obviously, a lot depends on what a person wants to accomplish with a language, but if someone wants to work toward something relevant in C++ (game development, etc.), there is absolutely nothing wrong with learning C++ as a first language.

No one expects a novice to swallow advanced memory management on day one. Starting with simple number guessing games is good enough for students of the language.


Thank you!:popcorn:

---

