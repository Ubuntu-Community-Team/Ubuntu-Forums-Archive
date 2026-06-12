---
title: "Basic C++ Calculator Works only 99.5% of Time"
date: 2012-02-09
forum: Programming Talk
---

### Post by earthpigg on 2012-02-09
Code is below. Intro to programming level class.

The idea is to tell the cashier how much change to give by coin type. EG: Bill is $10.50, customer hands you a $20, program tells user to give "Dollars: 9, Quarters: 2, Dimes: 0, Nickels: 0, Pennies: 0" to the customer.

It works, pretty much in every case. Unless the bill is $10 and the customer for some reason decides to hand over $20.15.

Expected:
```
Dollars: 10
Quarters: 0
Dimes: 1
Nickels: 1
Pennies: 0
```

Actual:
```
Dollars: 10
Quarters: 0
Dimes: 1
Nickels: [COLOR="Red"]0[/COLOR]
Pennies: [COLOR="Red"]4[/COLOR]
```


Where did that $0.01 go? You can do $10 and $20.16 or $10 and $20.14 and it works as expected. But if you put in $10 and $20.15, it steals a penny from the customer and only gives him $10.14 back!

I've kind-of-but-not-really traced the problem. The lines with "DEBUG:" return the following, stretched  --

```
Enter money owed:       $10
Enter money paid:       $20.15

DEBUG: paid: 2015.00000000
DEBUG: owed: 1000.00000000
DEBUG: debt: 1015.00000000
DEBUG: debtInt: 1014

The change is:
Dollars:        10
Quarters:       0
Dimes:          1
Nickels:        0
Pennies:        4

```

How is it that turning 1015.00000000 into an integer yields 1014? But 1016.00000000 correctly yields 1016, and 1014.00000000 correctly yields 1014?

(Click [here for pastebin]("http://pastebin.com/nzmv2X49") with contextual highlighting for C++ if you prefer)

```
#include <iostream>
#include <iomanip>
using namespace std;

int main()
{
	double owed = 0.0;
	double paid = 0.0;
	double debt = 0.0;
	int dollars = 0;
	int quarters = 0;
	int dimes = 0;
	int nickels = 0;
	int pennies = 0;
	//Input
	cout << "Enter money owed:\t$";
	cin >> owed;
	owed = owed * 100;

	cout << "Enter money paid:\t$";
	cin >> paid;
	paid = paid * 100;

	if (paid < owed)
	{
		cout << "ERROR: Ask customer for more money." << endl;
	}

	else
	{
	cout << "DEBUG: paid:" << fixed << setprecision(8) << paid << endl; //debug
	cout << "DEBUG: owed:" << fixed << setprecision(8)<< owed << endl;	//debug
	debt = paid - owed; //calculate debt in cents
	cout << "DEBUG: debt:" << fixed << setprecision(8) << debt << endl; //debug

	int debtInt;
	debtInt = debt; //use an int so modulus doesn't whine
	cout << "DEBUG: debtInt:\t" << debtInt << endl; //debug
	cout << endl << "The change is:\t" << endl;

	dollars = debtInt / 100;
	cout << "Dollars:\t" << dollars << endl; 
	debtInt = debtInt % 100;
	
	quarters = debtInt / 25;
	cout << "Quarters:\t" << quarters << endl; 
	debtInt = debtInt % 25;
	
	dimes = debtInt / 10;
	cout << "Dimes:  \t" << dimes << endl; 
	debtInt = debtInt % 10;
	
	nickels = debtInt / 5;
	cout << "Nickels:\t" << nickels << endl;
	debtInt = debtInt % 5;
	
	pennies = debtInt;
	cout << "Pennies:\t" << pennies << endl;

	
	}
	//system ("pause");
	return 0;
}


```

---

### Post by schauerlich on 2012-02-09
I'm guessing there's a rounding issue since you read in paid and owed as doubles. What prints as 1015.0000 might actually be stored as 1014.9999, and when you cast to int it truncates as 1014.

---

### Post by earthpigg on 2012-02-09
What else would I use? Are there triples that I am unaware of?!

---

### Post by schauerlich on 2012-02-09
You should store the dollar amounts as cents using ints.

---

### Post by earthpigg on 2012-02-09
I did!

---

### Post by tjoff on 2012-02-09
Consider how C++ casts a double to an integer. Does it use rounding or truncate the decimals? Then consider what schauerlich wrote about the actual stored value of the doubles.

---

### Post by earthpigg on 2012-02-09
I don't know who Schauerlich is, being a first time programmer.

As for the truncating, I was taught that it simply chops them off and does no rounding at all.

---

### Post by muteXe on 2012-02-09
Schauerlich is the guy that replied to your first post...

---

### Post by tjoff on 2012-02-09
> As for the truncating, I was taught that it simply chops them off and does no rounding at all. 

Is that what you want it to do in your case?

(...he asked rhetorically ;))

---

### Post by jwbrase on 2012-02-09
> **schauerlich said:**
> You should store the dollar amounts as cents using ints.

I tried doing that with his code (still inputing as doubles but storing immediately as ints), and got the rounding error on paid instead of debt. Rounding the number between multiplying it by 100 and storing it as an int sorted things out.

Also, if you do ((round(paid * 100) - paid * 100) * 0x40000000000), you get 1.0, which means that paid * 100 is getting skewed off its true value by exactly one part in 2^42.

EDIT: Actually, it's paid, not (paid * 100) that's being skewed. 20.15, when converted to binary or hexadecimal, is a repeating fraction, and thus can't be represented by a floating point value with a finite number of bits. So paid, instead of being set to 20.15, is being set to a bit less than 20.15. When we multiply that by 100 without rounding, we get a bit less than 2015, and when we convert that to an int, it gets truncated from 2014.9999999... to 2014.

Fiddle around with this calculator to see what's happening: [http://babbage.cs.qc.edu/IEEE-754/](http://babbage.cs.qc.edu/IEEE-754/)

---

### Post by Tony Flury on 2012-02-09
If you want to definitely avoid rounding errors - don't read into a double at all - you technique of multiplying by 100 may solve the one test case you have but there might be others that you still get bitten by.

I would read the input into a string buffer, and then parse that directly into an integer - and do validation at the same time if you want.

That way your ammounts never go anywhere near a double, and no rounding errors will bite you.

---

### Post by earthpigg on 2012-02-09
> 20.15, when converted to binary or hexadecimal, is a repeating fraction, and thus can't be represented by a floating point value with a finite number of bits. So paid, instead of being set to 20.15, is being set to a bit less than 20.15. When we multiply that by 100 without rounding, we get a bit less than 2015, and when we convert that to an int, it gets truncated from 2014.9999999... to 2014.

The professor chuckled when I demonstrated this to him, and told him that everyone sitting around me with similar code was experiencing identical results. Hrmmm.

> Is that what you want it to do in your case?

Not if it's going to lie to me about what I mean when I say to give me a zillion decimal points of accuracy!

@Tony Flury:

I like the idea of going from string to int.

---

### Post by Tony Flury on 2012-02-09
> **earthpigg said:**
> Not if it's going to lie to me about what I mean when I say to give me a zillion decimal points of accuracy!


A bit of pedantry here, but strictly speaking precission is not the same as accuracy.

Precision is related to the number of significant figures that you work with - i.e. The sun is 93 million miles away - precision here is 2 significant figures. In general in a calculation you should never have a result which is more precise than any of your inputs.

Accuracy : How close your answer is to the right answer. You could calculate a very precise answer (say 10 significant figures), but it may not be very accurate. This is effectively what is happening in your case - The double is trying to store your input in a very precise form 10.149999999999.... but the end result is not accurate.

---

### Post by schauerlich on 2012-02-09
> **tony flury said:**
> if you want to definitely avoid rounding errors - don't read into a double at all - you technique of multiplying by 100 may solve the one test case you have but there might be others that you still get bitten by.

I would read the input into a string buffer, and then parse that directly into an integer - and do validation at the same time if you want.

That way your ammounts never go anywhere near a double, and no rounding errors will bite you.

+1

---

### Post by xytron on 2012-02-09
I'm going to work on this, it just seems like I ought to be able to solve this by using only integers.

I don't think using literal constants such as 0.05, 0.10,0.25 should introduce the rounding errors.

This is one of those problems that look so simple until one begins to analyze it.

---

### Post by schauerlich on 2012-02-09
> **xytron said:**
> I don't think using literal constants such as 0.05, 0.10,0.25 should introduce the rounding errors.

Being a literal value or a calculated value does not matter. There is no way to represent an infinite amount of real numbers with a finite amount of bits. There will always be some values that cannot be represented and thus must be rounded.

---

### Post by xytron on 2012-02-09
> **schauerlich said:**
> Being a literal value or a calculated value does not matter. There is no way to represent an infinite amount of real numbers with a finite amount of bits. There will always be some values that cannot be represented and thus must be rounded.

Yes, but his solution almost worked.  I think the problem is he mixed doubles and integers in his solution, he ought to have used only integers.

---

### Post by lisati on 2012-02-09
I agree that "all ints" would be the way to go in order to avoid rounding problems. However, I'm not sufficiently proficient in C++ to suggest how to do this when converting an input string that might include decimals to integer.

---

### Post by Bachstelze on 2012-02-09
Actually, even a value seemingly very simple like 0.1 is rounded:

```
firas@dhcp-v041-181 ~ % gcc -std=c99 -pedantic -Wall -o test2 test2.c        
firas@dhcp-v041-181 ~ % cat test2.c                                  
#include <stdio.h>

int main(void)
{
    double d = 0.1;
    unsigned char *p = (unsigned char *) &d;
    for (int i=0; i<sizeof(double); i++) {
        printf("%02X ", *p++);
    }
    printf("\n");
}
firas@dhcp-v041-181 ~ % ./test2                                      
9A 99 99 99 99 99 B9 3F 
```

So the stored value is 1.1001100110011001100110011001100110011001100110011011*2^{&#8212;4}

Notice how 1001 becomes 1011 at the end, which obviously means that rounding occurred (just like in decimal 0.666666... would be rounded to 0.666667). This is of course because computers operate in binary. Representing 1/10 in binary is like representing 2/3 in decimal: not possible.

---

### Post by earthpigg on 2012-02-09
Someone suggested that I simply add a minuscule decimal value to the thing before converting it to an int and that seems to work.

With what I actually know how to do, that seems to make it work well enough.

---

### Post by xytron on 2012-02-09
> **earthpigg said:**
> Someone suggested that I simply add a minuscule decimal value to the thing before converting it to an int and that seems to work.

With what I actually know how to do, that seems to make it work well enough.

You will make it simpler if you just accept all input as an integer, that is without decimal points. So that for example

 $ 1.99 is 199

 $ 100.50  is 10050

 $ 0.99  is 99

and so on, actually this also makes it easier on the user to enter the data faster as you don't have to bother with decimal points.

This way you can have the program work will all integers, and you never bother with fractional numbers at all and eliminate rounding errors.

---

### Post by dwhitney67 on 2012-02-10
> **earthpigg said:**
> Someone suggested that I simply add a minuscule decimal value to the thing before converting it to an int and that seems to work.

I would recommend that the minuscule value be 0.005, or 1/2 of one cent.

I would also recommend that you consider checking for input errors when you prompt a user to enter data.  Make sure the values aren't negative, and only accept values with a precision no greater than 1/100th of a dollar.  If your application were used within a cash register, you wouldn't want someone entering an amount of 20.155.

---

### Post by nvteighen on 2012-02-10
Very convenient post that was blogged exactly today:

[http://blog.sesse.net/blog/tech/2012-02-10-19-20_rant_your_custom_rounding_code_is_wrong.html](http://blog.sesse.net/blog/tech/2012-02-10-19-20_rant_your_custom_rounding_code_is_wrong.html)

---

