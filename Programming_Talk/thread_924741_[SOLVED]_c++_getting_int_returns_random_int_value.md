---
title: "[SOLVED] c++ getting int returns random int value?"
date: 2008-09-19
forum: Programming Talk
---

### Post by chris200x9 on 2008-09-19
Hi I'm fairly new to programming and I am just learning about getter/setter functions I have written a program and I do not understand why I am getting a random int value for the age but the name is fine. I would appreciate any pointers. 

```
 
#include <iostream>
#include <string>
using namespace std;

class Person{
	private:
	string guysname;
	int guysage;
	public:
	Person (string name, int age)
	{
		setGuysName(name);
		setGuysAge(age);
	}
	void	setGuysName(string name) {
		guysname = name;
	}
	string getGuysName()
	{
		return guysname;
	}
	void setGuysAge(int age)
	{
		age = guysage;
	}
	
	int getGuysAge()
	{
		return guysage;
	}
	void displayMessage()
	{
		cout <<"yo' name is: " << getGuysName() << " and you are " << getGuysAge() << endl;
	}
	
	
	
};


int main()
{
	Person a("bob", 30);
	
	 a.displayMessage();
	
	return 0;
}

```

---

### Post by imdano on 2008-09-19
Take a closer look at the SetGuysAge function.

---

### Post by chris200x9 on 2008-09-19
dohhhhhhhhhh!!!!!!!!!! thanx a bunch!

---

### Post by dribeas on 2008-09-20
> **chris200x9 said:**
> ```
 
class Person{
	private:
	string guysname;
	int guysage;
	public:
	Person (string name, int age)
	{
		setGuysName(name);
		setGuysAge(age);
	}
//...
};
```

Also consider using initialization lists and pass-by-reference:

```

class Person
{
//...
   Person( std::string & name, int age ) : guysname( name ), guysage( age )
   {}
};

```

Without initialization lists, the internal data attributes are first default constructed and then copied, while you can use copy construction directly.

Without the pass by reference, each call to your constructor (or any other method as setGuysName() creates a copy of the original:

```

void f( std::string x ) { std::cout << x << std::endl };

void g( std::string const & x ) { std::cout << x << std::endl; };

int main()
{
   std::string very_long_string( "....long data string...." );

   f( very_long_string );
   g( very_long_string );
}

```

The call to f() creates a copy of the very_long_string to be used inside f() as x. The call to g() avoids the copy cost, and very_long_string is used inside g() by the name of x. The net result in both cases is the same: the contents of the string are printed on screen, but f() requires more resources for the task.

---

### Post by the_unforgiven on 2008-09-20
> **dribeas said:**
> ...
```

void f( std::string const & x ) { std::cout << x << std::endl };

void g( std::string x ) { std::cout << x << std::endl; };

int main()
{
   std::string very_long_string( "....long data string...." );

   f( very_long_string );
   g( very_long_string );
}

```

The call to f() creates a copy of the very_long_string to be used inside f() as x. The call to g() avoids the copy cost, and very_long_string is used inside g() by the name of x. The net result in both cases is the same: the contents of the string are printed on screen, but f() requires more resources for the task.

I think, it's the other way round - you get a copy in g() and not in f() because of the ref. used for declaring f().

---

### Post by dribeas on 2008-09-20
> **the_unforgiven said:**
> I think, it's the other way round - you get a copy in g() and not in f() because of the ref. used for declaring f().

:) That is what you get when you don't review :) I am correcting the text above now

---

