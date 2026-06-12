---
title: "expected primary-expression before ‘&lt;&lt;’ token"
date: 2007-04-16
forum: Programming Talk
---

### Post by larrybrazos on 2007-04-16
very simple c++ program that i can't compile . . .

> #include <iostream>
#include <iomanip>
using namespace std;

int main()
{
	const double TAX_RATE = 0.0825;
	double 	base_price,
			tax,
			price;
	
	cout << setprecision(2)
		<< setiosflags(ios::fixed)
		<< setiosflags(ios::showpoint);
	
	cout << "Enter the price of the item: ";
	cin >> base_price;
	
	tax = base_price * TAX_RATE;
	price = base_price + tax;
	
	cout << endl;
	cout << "The base price is" << setw(11) << base_price << endl;
	cout << "The tax is" << setw(18) << tax << endl;
	cout << "The price is" << setw(16) << price << endl;
	
	return 0;
}

the error is . . .

> ./dem02-1.cpp:32:2: warning: no newline at end of file
./dem02-1.cpp: In function ‘int main()’:
./dem02-1.cpp:16: error: expected primary-expression before ‘<<’ token


is this a missing library problem?

i have build-essential, libnet1-dev, libantlr-dev, libsdl1.2-dev installed.

thanks for any help.

---

### Post by larrybrazos on 2007-04-16
just compiled this with no errors . . .

so not sure what is wrong with that first one? :( 

> #include <iostream>
#include <iomanip>
using namespace std;

int main()
{
	const double SALES_TAX_RATE = 0.0825;
	
	double 	meal_price,
			sales_tax,
			total,
			amt_tendered,
			change;
	
	cout << setprecision(2)
		<< setiosflags(ios::fixed)
		<< setiosflags(ios::showpoint);
	
	cout << "*** C++-Side Restaurant ***" << endl << endl;
	cout << "Enter the price of the meal: $";
	cin >> meal_price;
	cout << endl;
	
	sales_tax = meal_price * SALES_TAX_RATE;
	total = meal_price + sales_tax;
	
	cout << endl;
	cout << "Price of meal: " << setw(6) << meal_price << endl;
	cout << "Sales tax: " << setw(10) << sales_tax << endl;
	cout << "----------------------------------" << endl;
	cout << "Total amount: " << setw(7) << total << endl;
	
	return 0;
}

---

### Post by xtacocorex on 2007-04-16
This line:
```

	cout << setprecision(2)
		<< setiosflags(ios::fixed)
		<< setiosflags(ios::showpoint);

```
should be:
```
 	cout << setprecision(2) << setiosflags(ios::fixed) << setiosflags(ios::showpoint);
```

You can't start a line with just <<, the compiler output mentions this.

You also need to have a return line at the end of the file.

---

### Post by larrybrazos on 2007-04-16
thanks for the help . . 

switched code to . . .

> #include <iostream>
#include <iomanip>
using namespace std;

int main()
{
	const double TAX_RATE = 0.0825;
	double 	base_price,
			tax,
			price;
	
	cout << setprecision(2) << setiosflags(ios::fixed) << setiosflags(ios::showpoint);
	
	cout << "Enter the price of the item: ";
	cin >> base_price;
	
	tax = base_price * TAX_RATE;
	price = base_price + tax;
	
	cout << endl;
	cout << "The base price is" << setw(11) << base_price << endl;
	cout << "The tax is" << setw(18) << tax << endl;
	cout << "The price is" << setw(16) << price << endl;
	
	return 0;
}
	

and i still get . . .

> dem02-1.cpp:32:2: warning: no newline at end of file
dem02-1.cpp: In function ‘int main()’:
dem02-1.cpp:16: error: expected primary-expression before ‘<<’ token


as far as including new line at end of file, what do you mean by that?

---

### Post by larrybrazos on 2007-04-16
i'm sure i will look back at this post and blush a few months from now :redface:

---

### Post by samjh on 2007-04-16
:confused: 

I can compile your code without a problem.

Completely baffled as to why you're getting that error.

---

### Post by WW on 2007-04-16
Actually, you *can* start a line with <<, but you can't start a statement with it.  For example, this code compiles and runs fine:
```

#include <iostream>

using namespace std;

int main()
{
    double x = 123.456;

    cout << x
         << endl;
    return 0;
}

```
However, if you inadvertently put in an extra semicolon, like this:
```

#include <iostream>

using namespace std;

int main()
{
    double x = 123.456;

    cout << x;
         << endl;
    return 0;
}

```
you will get an error:
```

$ g++ mytest.cpp -o mytest
mytest.cpp: In function ‘int main()’:
mytest.cpp:10: error: expected primary-expression before ‘<<’ token

```

---

### Post by samjh on 2007-04-17
Larrybrazos,

I think this is a problem perculiar to your machine or gcc installation.  As said before, I can compile your code fine.

Looks like you either forgot to save your code before compiling, or your gcc/g++ isn't parsing the source code properly.  Try copy-pasting the code to a different file and compile that.  Or else reinstall gcc/g++.

---

### Post by larrybrazos on 2007-04-17
thanks for the replies everyone, i haven't been able to test it yet, but i think you are on the right track samjh.  i was working on the program then had to bounce and scite was open for nearly 12 hours before i sat down again and worked on it.  so, i'll have to cut and past and save again and see what happens.

---

