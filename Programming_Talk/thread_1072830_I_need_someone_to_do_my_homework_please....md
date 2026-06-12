---
title: "I need someone to do my homework please..."
date: 2009-02-17
forum: Programming Talk
---

### Post by Leo Dragonheart on 2009-02-17
Just kidding. I am just guessing here. I don't know what I am doing and I was wondering if someone would correct this for me so I can see how It would work. I did it myself but can't figure out what is wrong. Remember I said I am guessing here so if the code looks stupid that is cause I am guessing...

```

# include < iostream>

using namespace std;

int main()
{
	int name;

	cout<<"Please enter your name: ";
	cin>> name;
	cin.ignore();
	if ( name )is: "Kelly"; ) {
		cout<<"You have a beautiful name!\n";
	}
	else if ( name )is not "Kelly" ) {
		cout<<"This is not your first name...Please try again.\n";
	if ( cout == "You have a beautiful name!" ) {
		cout<<"Please enter your age...\n";
	if ( age == 32 ) {
		cout<<"Wow, you are beautiful and young...\n";
	}
	else if ( age < 32 ) {
		cout<<"Come on add some yrs...;-)Please enter your true age...\n";
	}
	else if ( age > 32 ) {
		cout<<"You must be younger than this, Please enter your true age...\n";
	}
	if ( cout == "Wow, you are beautiful and young...\n");
		cout<<"Now That was not so bad was it? I just want to say I am happy to have you as a friend...;-)";
	}
	cin.get();
}
	
```

---

### Post by cerealtx on 2009-02-17
probably going to look more like this, my C++ is horrible and i know i have things wrong but mabey this will help
i would suggest reading your txt book, it seems you have a VERY simple assignment, read more on condition statements
```

int main()
{
	int name, iskelly, kellyage;

	cout<<"Please enter your name: ";
	cin>> name;
	if(name == "Kelly" || name == "kelly") 
	{
		kelly = 1;
		cout<<"You have a beautiful name!\n";
	}
	else {
		cout<<"This is not your first name...Please try again.\n";
	}
	if(kelly == 1)
	{
		cout<<"Please enter your age...\n";
		cin>>kellyage;
	}
	
switch (kellyage)
{
	case (kellyage = 32):
		cout<<"Wow, you are beautiful and young...\n";
		break;
	case (kellyage < 32):
		cout<<"Come on add some yrs...;-)Please enter your true age...\n";
		break;
	case (kellyage > 32)
		cout<<"You must be younger than this, Please enter your true age...\n";	
		break;
```

---

### Post by digitalvectorz on 2009-02-17
For starters, remove the spaces in your include
```

# include < iostream>

#include <iostream>       //the correct way; compiler complains your way.

```

Other than that, if you're using g++ as your compiler, it should help you to debug the program as is.

---

### Post by Leo Dragonheart on 2009-02-17
Thanx for the help I will give this a try. It was not homework...I was just messing around and wanted to see if I could make this program for my friend.

Thx for the advise...;-)

---

### Post by Leo Dragonheart on 2009-02-17
> **digitalvectorz said:**
> For starters, remove the spaces in your include
```

# include < iostream>

#include <iostream>       //the correct way; compiler complains your way.

```

Other than that, if you're using g++ as your compiler, it should help you to debug the program as is.

Thanx for that tip also...I see why programers get the big bucks...;-)

---

### Post by digitalvectorz on 2009-02-17
No worries.  I ran the code and compiled it...it gave some weird errors that traced to that line...funny how such a simple mistake can cause a compiler to go hogwild..

There are still a few other errors after recompiling, but it's nothing that you can't sift through on your own.

If you still need help, let me know.

---

### Post by Can+~ on 2009-02-17
[PHP]
#include <iostream>

using namespace std;

int main()
{
	string name;
	bool iskelly=false, iskelly_age=false;
	int kellyage=0;

	while (!iskelly) 
	{
		cout << "Please enter your name: ";
		cin >> name;
		
		if (name == "kelly" || name == "Kelly")
		{
			iskelly = true;
			cout << "You have a beautiful name!" << endl;
		}
		else
		{
			cout << "This is not your first name...Please try again." << endl;
		}
	}
		
	while (!iskelly_age)
	{
		cout << "Please enter your age: ";
		cin >> kellyage;
		
		if (kellyage == 32)
		{
			cout << "Wow, you are beautiful and young...";
			iskelly_age = true;
		}
		else if (kellyage < 32)
			cout << "Come on add some yrs...;-)Please enter your true age...";
		else if (kellyage > 32)
			cout << "You must be younger than this, Please enter your true age...";
				
		cout << endl;
	}
	
	return 0;
}
[/PHP]

Are you learning C++ by yourself? Or is it part of a class?

---

### Post by Leo Dragonheart on 2009-02-17
> **Can+~ said:**
> [PHP]
#include <iostream>

using namespace std;

int main()
{
	string name;
	bool iskelly=false, iskelly_age=false;
	int kellyage=0;

	while (!iskelly) 
	{
		cout << "Please enter your name: ";
		cin >> name;
		
		if (name == "kelly" || name == "Kelly")
		{
			iskelly = true;
			cout << "You have a beautiful name!" << endl;
		}
		else
		{
			cout << "This is not your first name...Please try again." << endl;
		}
	}
		
	while (!iskelly_age)
	{
		cout << "Please enter your age: ";
		cin >> kellyage;
		
		if (kellyage == 32)
		{
			cout << "Wow, you are beautiful and young...";
			iskelly_age = true;
		}
		else if (kellyage < 32)
			cout << "Come on add some yrs...;-)Please enter your true age...";
		else if (kellyage > 32)
			cout << "You must be younger than this, Please enter your true age...";
				
		cout << endl;
	}
	
	return 0;
}
[/PHP]

Are you learning C++ by yourself? Or is it part of a class?

All by myself...from here: [http://cprogramming.com/](http://cprogramming.com/) and thanx for the help. I just like to try things out and see if I can figure it out. I get tired of reading and reading...I am starting with Loops in C++ tomorrow.

---

### Post by Can+~ on 2009-02-17
> **Leo Dragonheart said:**
> All by myself...from here: [http://cprogramming.com/](http://cprogramming.com/) and thanx for the help. I just like to try things out and see if I can figure it out. I get tired of reading and reading...

Are you sure you want to start with C++? It's a common misconception that people want to use the language because it's popular. But in reality, it's not popular because it's good, it's because it's flexible but it can be tough for newcomers.

In fact, even though I've helped you with this questions about C++, I despise it.

Since you're already in ubuntu, why don't you give Python a spin? Writing a python script is as easy as typing [FONT="Courier New"]print "Hello world"[/FONT] in a text file and doing and [FONT="Courier New"]python helloworld.py[/FONT] in the shell.

---

### Post by digitalvectorz on 2009-02-17
Awesome.  If the issue is resolved, glad to hear it!  If you could please mark this post as solved (if/when it's solved), thanks. :-)

---

### Post by Leo Dragonheart on 2009-02-17
> **Can+~ said:**
> Are you sure you want to start with C++? It's a common misconception that people want to use the language because it's popular. But in reality, it's not popular because it's good, it's because it's flexible but it can be tough for newcomers.

In fact, even though I've helped you with this questions about C++, I despise it.

Since you're already in ubuntu, why don't you give Python a spin? Writing a python script is as easy as typing [FONT="Courier New"]print "Hello world"[/FONT] in a text file and doing and [FONT="Courier New"]python helloworld.py[/FONT] in the shell.

I tried Python but could not get the programs to run... but now that I know more about how to do it I will go back and give it a try. A problem I have is that allot of my friends have windows and I didn't think if I used Python they would be able to run my apps... By the way thanx for all your help Can+~ and everyone else that helped me...

---

### Post by Leo Dragonheart on 2009-02-17
Can I make this so I can send it to my friend to use? She has windows though...

---

### Post by Can+~ on 2009-02-17
> **Leo Dragonheart said:**
> Can I make this so I can send it to my friend to use? She has windows though...

She would need to install the python interpreter.
[http://www.python.org/download/](http://www.python.org/download/)

In windows, it's double click to a python file once the interpreter is installed.

---

### Post by Leo Dragonheart on 2009-02-17
Thanx again... and then I can just e-mail her the file?

---

### Post by Phenax on 2009-02-17
> **Leo Dragonheart said:**
> Thanx again... and then I can just e-mail her the file?

Yes, and then she can run it if she has already installed Python. While most Linux distributions come with Python pre-installed, Microsoft Windows does not, so they must install it before they can run Python programs.

---

### Post by Tony Flury on 2009-02-18
And if you had built it using C++ then you would have had to cross compiler it (not sure how, but i know you would have to) because an binary built on Linux will not work on Windows.

---

### Post by lukjad on 2009-02-18
Heehee. Funny title.

---

### Post by SledgeHammer_999 on 2009-02-18
> **Leo Dragonheart said:**
> All by myself...from here: [http://cprogramming.com/](http://cprogramming.com/) and thanx for the help. I just like to try things out and see if I can figure it out. I get tired of reading and reading...I am starting with Loops in C++ tomorrow.

In my opinion you should instead check this tutorial. [link](http://www.cplusplus.com/doc/tutorial/)
I think it explains it better than cprogramming and it is far easier because it focuses only on C++.

---

### Post by Leo Dragonheart on 2009-02-18
> **SledgeHammer_999 said:**
> In my opinion you should instead check this tutorial. [link](http://www.cplusplus.com/doc/tutorial/)
I think it explains it better than cprogramming and it is far easier because it focuses only on C++.

Thanx for the link SledgeHammer. Looks promising, I am checking it out now...

---

