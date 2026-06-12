---
title: "C++ help"
date: 2007-07-19
forum: Programming Talk
---

### Post by sdmike on 2007-07-19
I'm writing a program that takes change less than a dollar and it shows how many quarters, dimes, nickles, and pennies you get back.

My problem is that it's showing quarters with a decimal and I don't want that as you can see here.

```
Enter an amount less than $1.00: .34
You have 1.36 quarters.
```

If I change quarters from a Float to an Int, the code won't compile.

I thought using modulus would help but that wouldn't even compile.

here's my code.

```
# include <iostream>

float amount;
float quarters;
//float dimes;
//float nickles;
//float pennies;


int main()
{

std::cout << "Enter an amount less than $1.00: ";
std::cin >> amount;



quarters = (amount / 0.25);

//dimes = (amount / 0.10);

//nickles = (amount / 0.05);

//pennies = (amount / 0.01);

std::cout << "You have " << quarters << " quarters" << ".\n";
//std::cout << "You have " << dimes << " dimes" << ".\n";
//std::cout << "You have " << nickles << " nickles" << ".\n";
//std::cout << "You have " << pennies << " pennies" << ".\n";

return (0);

}

```

---

### Post by Wybiral on 2007-07-19
You can cast it...

```

float x = (int)(4.0 / 3.0);

```

EDIT:

I was reminded by another forum member of the fact that C++ users tend to frown on the use of C type casting... So, I'd also like to offer the use of:

```

float x = static_cast<int>(4.0 / 3.0);

```

Which is the typical C++ way. And you can also use the math "floor" operator which shaves off the decimal digits...

```

float x = floor(4.0 / 3.0);

```

(remember to "#include <cmath>" if you use "floor")

---

### Post by sdmike on 2007-07-19
The book says: Given an amount less than $1.00, compute the number of quarters, dimes, nickels, and pennies needed.

Does this look right?

It compiles and runs.

```
# include <iostream>

float amount;
float quarters;
float dimes;
float nickels;
float pennies;


int main()
{
while (true){

std::cout << "Enter an amount less than $1.00: ";
std::cin >> amount;

if (amount == 0)
    break;

quarters = (int)(amount / 0.25);

dimes = (int)(amount / 0.10);

nickles = (int)(amount / 0.05);

pennies = (int)(amount / 0.01);


std::cout << "You have " << quarters << " quarters" << ".\n";
std::cout << "You have " << dimes << " dimes" << ".\n";
std::cout << "You have " << nickels << " nickels" << ".\n";
std::cout << "You have " << pennies << " pennies" << ".\n";
}
return (0);

}
```


```
sdmike@desktop:~/Desktop/programs$ ./change
Enter an amount less than $1.00:0 .97
You have 3 quarters.
You have 9 dimes.
You have 19 nickels.
You have 97 pennies.
Enter an amount less than $1.00: 0
sdmike@desktop:~/Desktop/programs$ 
```

---

### Post by Wybiral on 2007-07-19
It works, but after you cast them to an int, you don't need the variables receiving them to be stored as a float.

---

### Post by jonathanmotes on 2007-07-20
You have way too many dimes! It's been a while since I've done any programming, but you need to do something like this:

dimes = (int)((amount - .25 x quarters) / 0.10);

and so on for the other coins.

---

### Post by sdmike on 2007-07-20
> **jonathanmotes said:**
> You have way too many dimes! It's been a while since I've done any programming, but you need to do something like this:

dimes = (int)(amount / 0.10) - .25 x quarters;

and so on for the other coins.

WAIT - im wrong -- hold on a second!

This was way before you posted this BTW.

I tried it this way, but it would just give me zero's.

So I got frustrated and did it this easy way until I thought out how to do it the correct way.

---

### Post by sdmike on 2007-07-20
> **Wybiral said:**
> It works, but after you cast them to an int, you don't need the variables receiving them to be stored as a float.

If I then change the variables to int, instead of float, the program just looks like it breaks.

---

### Post by Wybiral on 2007-07-20
Amount will still need to be float, but the others should work with ints... Unless I'm overlooking something, but it looks fine to me.

---

### Post by sdmike on 2007-07-20
When I try it this way. It compiles but it's still out of whack.

For example if someone gave me 86 cents,

3 quarters
1 dime
0 nickel
1 pennies

```
# include <iostream>

float amount;
float quarters;
float dimes;
float nickels;
float pennies;


int main()
{
while (true){

std::cout << "Enter an amount less than $1.00: ";
std::cin >> amount;

if (amount == 0)
    break;

quarters = (int)(amount / 0.25);

dimes = (int)(amount - (quarters * 0.25) / 0.10);

nickels = (int)(amount - (dimes * .10) / 0.05);

pennies = (int)(amount - (nickels * 0.05) / 0.01);


std::cout << "You have " << quarters << " quarters" << ".\n";
std::cout << "You have " << dimes << " dimes" << ".\n";
std::cout << "You have " << nickels << " nickels" << ".\n";
std::cout << "You have " << pennies << " pennies" << ".\n";
}
return (0);

}

```

---

### Post by sdmike on 2007-07-20
lets say for dimes:

dimes = (int) (0.10 / (amount - (quarters * 0.25)));

lets say 0.87
mathematically this works but the out put is saying 0 dimes when there should be 1.

---

### Post by slavik on 2007-07-20
```

#include <iostream>
using namespace std;
int main() {
  float t; cin>>t;
  int change = static_cast<int> (t * 100);
  int q = change / 25; change %= 25;
  int d = change / 10; change %= 10;
  int n = change / 5; change %= 5;
  int p = change;

  cout>>q>>" ">>d>>" ">>n>>" ">>p>>endl;
  return 0;
}
```

---

### Post by sdmike on 2007-07-20
> **slavik said:**
> ```

#include <iostream>
using namespace std;
int main() {
  float t; cin>>t;
  int change = static_cast<int> (t * 100);
  int q = change / 25; change %= 25;
  int d = change / 10; change %= 10;
  int n = change / 5; change %= 5;
  int p = change;

  cout>>q>>" ">>d>>" ">>n>>" ">>p>>endl;
  return 0;
}
```

Is there another way of doing this without using using "namespace std;" because I haven't gotten that far in the book were they explain what that does.

---

### Post by jonathanmotes on 2007-07-20
You might need more parenthesizes. For example,

dimes = (int)(amount - (quarters * 0.25) / 0.10);

Maybe should be:

dimes = (int)( (amount - (quarters * 0.25) ) / 0.10);

EDIT: if you keep with the your original technique (sorry i didn't see the last 2 posts)

---

### Post by Wybiral on 2007-07-20
> **sdmike said:**
> Is there another way of doing this without using using "namespace std;" because I haven't gotten that far in the book were they explain what that does.

The namespace is just to allow you him to use "cout" and "cin" without needing "std::cout"

You'll eventually get to that good stuff...

---

### Post by sdmike on 2007-07-20
My calculations suck because lets say if there is 0.01 then everything goes to zero.

back to the drawing board.

---

### Post by sdmike on 2007-07-20
```

#include <iostream>
using namespace std;
int main() {
  float t; cin>>t;
  int change = static_cast<int> (t * 100);
  int q = change / 25; change %= 25;
  int d = change / 10; change %= 10;
  int n = change / 5; change %= 5;
  int p = change;

  cout>>q>>" ">>d>>" ">>n>>" ">>p>>endl;
  return 0;
}

```

When I tried using modulus  (%) I got errors everytime.

Can this code be changed into, what I kind of have?

---

### Post by Wybiral on 2007-07-20
The modulus should work... Those ">>" operators are backwards though...

How about this:
```

#include <iostream>
#include <cmath>

int main()
{
    float t;

    std::cin >> t;

    int c = (int)floor(t*100);

    int q = c / 25;
    c %= 25;
    int d = c / 10;
    c %= 10;
    int n = c / 5;
    c %= 5;
    int p = c;
    std::cout << q << " " << d << " " << n << " " << p << sdt::endl;
    return 0;
}

```

---

### Post by WebDrake on 2007-07-20
> **sdmike said:**
> When I try it this way. It compiles but it's still out of whack.

For example if someone gave me 86 cents,

3 quarters
1 dime
0 nickel
1 pennies

```
# include <iostream>

float amount;
float quarters;
float dimes;
float nickels;
float pennies;


int main()
{
while (true){

std::cout << "Enter an amount less than $1.00: ";
std::cin >> amount;

if (amount == 0)
    break;

quarters = (int)(amount / 0.25);

dimes = (int)(amount - (quarters * 0.25) / 0.10);

nickels = (int)(amount - (dimes * .10) / 0.05);

pennies = (int)(amount - (nickels * 0.05) / 0.01);


std::cout << "You have " << quarters << " quarters" << ".\n";
std::cout << "You have " << dimes << " dimes" << ".\n";
std::cout << "You have " << nickels << " nickels" << ".\n";
std::cout << "You have " << pennies << " pennies" << ".\n";
}
return (0);

}

```

The lines calculating the amount of coins don't calculate what you think they do.  For example,
```
dimes = (int)(amount - (quarters * 0.25) / 0.10);
```
is the same as,
```
dimes = (int)(amount - ((quarters * 0.25) / 0.10) );
```
when what you intended was,
```
dimes = (int)( (amount - (quarters * 0.25)) / 0.10);
```

Look up "operator precedence"!

But in any case that approach is wrong as the quarters are only subtracted for the purpose of this calculation---by the time you get along to nickels, the "quarter amount" is still left in the total and is not subtracted.  You should be *permanently subtracting* the quarters, dimes, nickels etc. as they are accounted for.  (This is implicit in Slavik's code.)

```

# include <iostream>

float amount;
float quarters;
float dimes;
float nickels;
float pennies;


int main()
{
	while (true){
		
		std::cout << "Enter an amount less than $1.00: ";
		std::cin >> amount;
		
		if (amount == 0)
			break;
		
		quarters = (int)(amount / 0.25);
		amount -= (quarters * 0.25);
		
		dimes = (int)(amount / 0.10);
		amount -= (dimes * 0.10);
		
		nickels = (int)(amount / 0.05);
		amount -= (nickels * 0.05);
		
		pennies = (int)(amount / 0.01);
		
		
		std::cout << "You have " << quarters << " quarters" << ".\n";
		std::cout << "You have " << dimes << " dimes" << ".\n";
		std::cout << "You have " << nickels << " nickels" << ".\n";
		std::cout << "You have " << pennies << " pennies" << ".\n";
	}
	return (0);
	
}

```

See the difference?

---

### Post by WebDrake on 2007-07-20
> **slavik said:**
> ```

#include <iostream>
using namespace std;
int main() {
  float t; cin>>t;
  int change = static_cast<int> (t * 100);
  int q = change / 25; change %= 25;
  int d = change / 10; change %= 10;
  int n = change / 5; change %= 5;
  int p = change;

  cout>>q>>" ">>d>>" ">>n>>" ">>p>>endl;
  return 0;
}
```

The reason you get errors with Slavik's code is because he uses the wrong operator with cout, he was using >> instead of <<.  It should be,

```

#include <iostream>
using namespace std;
int main() {
	float t; cin>>t;
	int change = static_cast<int> (t * 100);
	int q = change / 25; change %= 25;
	int d = change / 10; change %= 10;
	int n = change / 5; change %= 5;
	int p = change;
	
	cout << q <<" " << d << " " << n << " " << p << endl;
	return 0;
}

```

A slightly nicer version (which includes the output statements you desire, and omits the "using namespace std" since you seem to want to avoid that) is,

```

#include <iostream>

int main() {
	float t;
	std::cout << "Enter an amount less than $1.00: ";
	std::cin >> t;
	int change = static_cast<int> (t * 100);
	int q = change / 25; change %= 25;
	int d = change / 10; change %= 10;
	int n = change / 5; change %= 5;
	int p = change;
	
	std::cout << "You have " << q << " quarters" << std::endl;
	std::cout << "You have " << d << " dimes" << std:: endl;
	std::cout << "You have " << n << " nickels" << std::endl;
	std::cout << "You have " << p << " pennies" << std::endl;
	
	return 0;
}

```

***EDIT:** Sorry Wybiral, didn't read closely enough ;)  BTW I approve of your using floor(), it seems a safer bet to me than just an int cast.*

---

### Post by sdmike on 2007-07-20
> **WebDrake said:**
> The reason you get errors with Slavik's code is because he uses the wrong operator with cout, he was using >> instead of <<.  It should be,

```

#include <iostream>
using namespace std;
int main() {
	float t; cin>>t;
	int change = static_cast<int> (t * 100);
	int q = change / 25; change %= 25;
	int d = change / 10; change %= 10;
	int n = change / 5; change %= 5;
	int p = change;
	
	cout << q <<" " << d << " " << n << " " << p << endl;
	return 0;
}

```

A slightly nicer version (which includes the output statements you desire, and omits the "using namespace std" since you seem to want to avoid that) is,

```

#include <iostream>

int main() {
	float t;
	std::cout << "Enter an amount less than $1.00: ";
	std::cin >> t;
	int change = static_cast<int> (t * 100);
	int q = change / 25; change %= 25;
	int d = change / 10; change %= 10;
	int n = change / 5; change %= 5;
	int p = change;
	
	std::cout << "You have " << q << " quarters" << std::endl;
	std::cout << "You have " << d << " dimes" << std:: endl;
	std::cout << "You have " << n << " nickels" << std::endl;
	std::cout << "You have " << p << " pennies" << std::endl;
	
	return 0;
}

```

***EDIT:** Sorry Wybiral, didn't read closely enough ;)  BTW I approve of your using floor(), it seems a safer bet to me than just an int cast.*

What is "static_cast<int>"?

---

### Post by WebDrake on 2007-07-20
> **sdmike said:**
> What is "static_cast<int>"?

It's a way of type casting, that is, converting data from one of C++'s number types to another.  In this case you want to convert from a float to an int.

In C you would write,
```
change = (int) (t*100)
```
but I think in C++ the use of static_cast<> is safer.

[http://www.codeproject.com/cpp/static_cast.asp](http://www.codeproject.com/cpp/static_cast.asp)

---

### Post by umairsario on 2013-04-17
Problem is at 
pennies = (int)(amount / 0.01);

if you want in INT you will always have answer in 0; so you cant calculate pennies.

so  you have to change it to..

pennies = (amount / 0.01);

now another thing to do is.. make it round ....

int roundingp = pennies+0.5;

and then 
pennies = roundingp;

if i paste your program after making some change here it will be !```


# include <iostream.h>
#include<conio.h>

float amount;
float quarters;
float dimes;
float nickels;
float pennies;


int main()
{
cout << "Enter an amount less than $1.00: ";
cin >> amount;

//if (amount == 0)


quarters = (int)(amount / 0.25);
amount -= (quarters * 0.25);

dimes = (int)(amount / 0.10);
amount -= (dimes * 0.10);

nickels = (int)(amount / 0.05);
amount -= (nickels * 0.05);


pennies = (amount / 0.01);
//cout<< pennies;

cout << "You have " << quarters << " quarters" << ".\n";
cout << "You have " << dimes << " dimes" << ".\n";
cout << "You have " << nickels << " nickels" << ".\n";
int roundingp = pennies+0.5;
pennies = roundingp;
cout << "You have " << pennies << " pennies" << ".\n";


getch();
return 0;

}
```

Result Snapshopt
where input is 0.11

Enter an amount less then $1.00: 0.11
You have 0 quaters.
You have 1 dimes.
You have 0 quaters.
You have 1 pennies.




Reply if having any difficulty !

---

### Post by howefield on 2013-04-17
Old thread closed.

---

### Post by Bucky Ball on 2013-04-17
[B][I]Thread Closed

Reason:[/I][/B] Necromancy.

Welcome to the forums. This thread is *reeealllly* old, hasn't seen any action in nearly six years, so better left to sleep. As you're a newcomer you might like to read the Code of Conduct, if you haven't already. Here is an excerpt:

> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

Good luck.

---

