---
title: "C++ Shows everything at once."
date: 2009-02-01
forum: Programming Talk
---

### Post by Vandorin on 2009-02-01
Probably something small that I am not seeing, but I was writing this code, and I have all of the math figure out, but for some reason, whenever anyone enters a number, no matter what it it, it always just tells you the first number of the code. So if you were to enter "Three" it would tell you the price of "Four". Here is my code so far.

```

#include <iostream>
#include <iomanip>
using namespace std;

void main()
{
	float DVDnumb;
	float four;
	float DVDfour;
	float D4;
	float three;
	float DVDthree;
	float D3;
	float two;
	float DVDtwo;
	float D2;
	float one;
	float DVDone;
	float D1;
	float five;

	four =19.99 * .07;
	DVDfour =19.99 + four;
	D4 =DVDfour;

	three =16.99 * .07;
	DVDthree =16.99 + three;
	D3 =DVDthree;
	
	two =13.99 * .07;
	DVDtwo =13.99 + two;
	D2 =DVDtwo;

	one =8.99 * .07;
	DVDone =8.99 + one;
	D1 =DVDone;
	

	cout << fixed << setprecision (2);
	cout << "Welcome to Netflix movie Rental! Please choose how many DVDs you would like to rent each month." << endl;
	cout << "Netflix movie rental has several different options to choose from : " << endl;
	cout << setw(10) << "4 DVD at-a-time" << setw(3) << "      " << setw(10) << "Unlimited!" << setw(2) << "$19.99" << endl;
	cout << setw(10) << "3 DVD at-a-time" << setw(3) << "      " << setw(10) << "Unlimited!" << setw(2) << "$16.99" << endl;
	cout << setw(10) << "2 DVD at-a-time" << setw(3) << "      " << setw(10) << "Unlimited!" << setw(2) << "$13.99" << endl;
	cout << setw(10) << "1 DVD at-a-time" << setw(3) << "      " << setw(10) << "Unlimited!" << setw(2) << "$8.99" << endl;
	cout << "*plus any applicable tax" << endl;

	cout << "Please type the number of DVDs you would like to rent" << endl;
	cin >> DVDnumb;
	
	

	if ( four = DVDnumb ) {
		cout << "Thank you! Your total cost will be:" << "  $" << D4 << endl;
	} else if ( three = DVDnumb ) {
		cout << "Thank you! Your total cost will be:" << "  $" << D3 << endl;
	} else if ( two = DVDnumb ) {
		cout << "Thank you! Your total cost will be:" << "  $" << D2 << endl;
	} else if ( one = DVDnumb ) {
		cout << "Thank you! Your total cost will be:" << "  $" << D1 << endl;
	}

	system("pause");
}

```

I would appreciate any help, or if you know what I did wrong, Thanks :D

---

### Post by dribeas on 2009-02-01
The fast answer is in your if condition: if ( four = DVDnumb ). You probably meant if ( four == DVDnumb ), but then again, you don't want to do that either... for two reasons:

Floating point numbers are a little tricky with regard to comparisons. Google a bit and you'll learn why.

I don't think you want to compare the 'number of DVDs you want to rent' with the value 19.99 * 0.7 that is stored inside the four variable. Go back to your code and try to figure out what it is doing (get a piece of paper and execute the code yourself).

---

### Post by mdurham on 2009-02-01
if ( four = DVDnumb )   should be   if ( four == DVDnumb ) and that goes for the other comparisons too.
Cheers, Mike

---

### Post by Vandorin on 2009-02-01
> **dribeas said:**
> The fast answer is in your if condition: if ( four = DVDnumb ). You probably meant if ( four == DVDnumb ), but then again, you don't want to do that either... for two reasons:

Floating point numbers are a little tricky with regard to comparisons. Google a bit and you'll learn why.

I don't think you want to compare the 'number of DVDs you want to rent' with the value 19.99 * 0.7 that is stored inside the four variable. Go back to your code and try to figure out what it is doing (get a piece of paper and execute the code yourself).

I do want it to by times .07 because I am adding tax in, and as for the rest of your post, I don't think its very helpful sorry :(.

---

### Post by Vandorin on 2009-02-01
> **mdurham said:**
> if ( four = DVDnumb )   should be   if ( four == DVDnumb ) and that goes for the other comparisons too.
Cheers, Mike

When I do this, and execute it, When i enter the number, nothing happens, and all it tells me is to press any button to continue.

---

### Post by mdurham on 2009-02-01
> **Vandorin said:**
> When I do this, and execute it, When i enter the number, nothing happens, and all it tells me is to press any button to continue.
That's probably because you didn't follow dribeas' advice about comparing floating point numbers and comparing DVDnumb with something that you shouldn't be comparing it with.
Cheers, Mike

---

### Post by Vandorin on 2009-02-01
> **dribeas said:**
> The fast answer is in your if condition: if ( four = DVDnumb ). You probably meant if ( four == DVDnumb ), but then again, you don't want to do that either... for two reasons:

Floating point numbers are a little tricky with regard to comparisons. Google a bit and you'll learn why.

I don't think you want to compare the 'number of DVDs you want to rent' with the value 19.99 * 0.7 that is stored inside the four variable. Go back to your code and try to figure out what it is doing (get a piece of paper and execute the code yourself).

Dear god you are right, Im sorry I said you were not helpful before, I definatly see what you mean now, and THANKS for pointing that out, I was thinking that four was D4. Thank you!

---

### Post by Vandorin on 2009-02-01
New code

```

#include <iostream>
#include <iomanip>
using namespace std;

void main()
{
	float DVDnumb;
	float four;
	float DVDfour;
	float D4;
	float three;
	float DVDthree;
	float D3;
	float two;
	float DVDtwo;
	float D2;
	float one;
	float DVDone;
	float D1;


	D4 = 19.99 * .07;
	DVDfour = 19.99 + D4;
	four = DVDfour;

	D3 = 16.99 * .07;
	DVDthree = 16.99 + D3;
	three = DVDthree;

	D2 = 13.99 * .07;
	DVDtwo = 13.99 + D2;
	two = DVDtwo;

	D1 = 8.99 * .07;
	DVDone = 8.99 + D1;
	one = DVDone;


	cout << fixed << setprecision (2);
	cout << "Welcome to Netflix movie Rental! Please choose how many DVDs you would like to rent each month." << endl;
	cout << "Netflix movie rental has several different options to choose from : " << endl;
	cout << setw(10) << "4 DVD at-a-time" << setw(3) << "      " << setw(10) << "Unlimited!" << setw(2) << "$19.99" << endl;
	cout << setw(10) << "3 DVD at-a-time" << setw(3) << "      " << setw(10) << "Unlimited!" << setw(2) << "$16.99" << endl;
	cout << setw(10) << "2 DVD at-a-time" << setw(3) << "      " << setw(10) << "Unlimited!" << setw(2) << "$13.99" << endl;
	cout << setw(10) << "1 DVD at-a-time" << setw(3) << "      " << setw(10) << "Unlimited!" << setw(2) << "$8.99" << endl;
	cout << "*plus any applicable tax" << endl;

	cout << "Please type the number of DVDs you would like to rent" << endl;
	cin >> DVDnumb;
	
	
	
	if ( four = DVDnumb ) {
		cout << "Thank you! Your total cost will be:" << "  $" << DVDfour << endl;
	} else if ( three = DVDnumb ) {
		cout << "Thank you! Your total cost will be:" << "  $" << DVDthree << endl;
	} else if ( two = DVDnumb ) {
		cout << "Thank you! Your total cost will be:" << "  $" << DVDtwo << endl;
	} else if ( one = DVDnumb ) {
		cout << "Thank you! Your total cost will be:" << "  $" << DVDone << endl;
	}

	system("pause");
}

```

Not sure If i've done that right, I hope so.

EDIT: nope, still doing the same as the last one. Can anyone please tell me what I am supposed to do?

---

### Post by Krupski on 2009-02-01
> **Vandorin said:**
> I do want it to by times .07 because I am adding tax in, and as for the rest of your post, I don't think its very helpful sorry :(.

All comparisons require the double ==

For example, if you do this:  if(x = max)

All that does is set x to "max".

What you need is if(x == max)

By the way, in your code you could probably get a cleaner program by using "case" instead of all those "if" comparisons.

Also, you can do the tax all in one step. Instead if "price = price * 0.07" you can just do "(price *= 1.07);"

Hope this is answering your question...

-- Roger

---

### Post by Krupski on 2009-02-01
> **Vandorin said:**
> Probably something small that I am not seeing, but I was writing this code, and I have all of the math figure out, but for some reason, whenever anyone enters a number, no matter what it it, it always just tells you the first number of the code. So if you were to enter "Three" it would tell you the price of "Four". Here is my code so far.



I patched up your code a bit... it's still in need of a lot of TLC, but I think it does what you want and hopefully it will put you on the right path:


```

#include <iostream>
#include <iomanip>
#include <stdlib.h>

using namespace std;

int main()
{
        float DVDnumb;
        float four, DVDfour;
        float three, DVDthree;
        float two, DVDtwo;
        float one, DVDone;
//      float five;

        four = 4; // for comparison to user input
        DVDfour = 19.99 * 1.07; // 19.99 plus 7% tax

        three = 3;
        DVDthree = 16.99 * 1.07;

        two = 2;
        DVDtwo = 13.99 * 1.07;

        one = 1;
        DVDone = 8.99 * 1.07;


        cout << fixed << setprecision (2);
        cout << "Welcome to Netflix movie Rental! Please choose how many DVDs you would like to rent each month." << endl;
        cout << "Netflix movie rental has several different options to choose from : " << endl;
        cout << setw(10) << "4 DVD at-a-time" << setw(3) << "      " << setw(10) << "Unlimited!" << setw(2) << "$19.99" << en$
        cout << setw(10) << "3 DVD at-a-time" << setw(3) << "      " << setw(10) << "Unlimited!" << setw(2) << "$16.99" << en$
        cout << setw(10) << "2 DVD at-a-time" << setw(3) << "      " << setw(10) << "Unlimited!" << setw(2) << "$13.99" << en$
        cout << setw(10) << "1 DVD at-a-time" << setw(3) << "      " << setw(10) << "Unlimited!" << setw(2) << "$8.99" << end$
        cout << "*plus any applicable tax" << endl;

        cout << "Please type the number of DVDs you would like to rent" << endl;
        cin >> DVDnumb;


        if ( four == DVDnumb ) {
                cout << "Thank you! Your total cost will be:" << "  $" << DVDfour << endl;
        } else if ( three == DVDnumb ) {
                cout << "Thank you! Your total cost will be:" << "  $" << DVDthree << endl;
        } else if ( two == DVDnumb ) {
                cout << "Thank you! Your total cost will be:" << "  $" << DVDtwo << endl;
        } else if ( one == DVDnumb ) {
                cout << "Thank you! Your total cost will be:" << "  $" << DVDone << endl;
        }

    // there should be something that responds to illegal input
    // rather than just falling through and printing nothing.

        system("sleep 1");
        return 0;
}

```

---

### Post by dwhitney67 on 2009-02-01
Try replacing those if-else statements with:
```

...

switch (DVDnumb)
{
  case 1: // do something...
          break;

  case 2: // do something...
          break;

  case 3: // do something...
          break;

  case 4: // do something...
          break;

  default: // illegal input for DVDnumb, which probably should be
           // checked way before getting to this point.
}

...

```

P.S.  And DVDnumb should be declared as an unsigned int or an int, not a float.  After all, a person cannot rent 3.456 DVDs at a time.

---

### Post by Krupski on 2009-02-01
Having nothing better to do on a Sunday night, I whipped up this little program. It's in plain old ANSI C (I so do hate C++). Comments should help you understand what's going on.


```

#include <stdio.h>
#include <stdlib.h>
#define TAX 7.00 // 7 percent government ripoff

int main()
{
    char buffer[BUFSIZ];
    int sel = 0; // customer selection (initialized to 0)
    float price; // final price with tax
    char *prices[5]={"0.00", "8.99", "13.99", "16.99", "19.99"}; // 0.00 dummy cause index is 1-4
    char *plural[5]={"", "", "s", "s", "s"}; // plural "s" for DVD

    while(sel == 0) {

        // customer prompt
        fprintf(stdout,"\n");
        fprintf(stdout,"Welcome to Netflix Movie Rental!\n\n");
        fprintf(stdout,"Netflix Movie Rental has several different options to choose from.\n\n");
        fprintf(stdout,"4 DVD at-a-time    -    UNLIMITED!\n");
        fprintf(stdout,"3 DVD at-a-time    -    UNLIMITED!\n");
        fprintf(stdout,"2 DVD at-a-time    -    UNLIMITED!\n");
        fprintf(stdout,"1 DVD at-a-time    -    UNLIMITED!\n");
        fprintf(stdout,"\n");
        fprintf(stdout,"Please select the number of DVDs you would like to rent: ");
        fflush(stdout);

        fgets(buffer, BUFSIZ, stdin); /* read from stdin console */

        fprintf(stdout, "\n"); // new line
        fflush(stdout);

        sel = atoi(buffer); // read integer input

        if((sel < 1) || (sel > 4)) { // input must be 1, 2, 3 or 4
            sel = 0; // reflag to 0 for while loop above
            fprintf(stderr, "\a"); // "a" is alert (a beep)
            fprintf(stderr, "Input error - please enter 1 through 4 only\n");
            fprintf(stderr, "\n");
            fflush(stderr);
        }
    }

    price = (atof(prices[sel]) * (1 + (TAX / 100))); // extract price from string then add tax
    fprintf(stdout, "Thank you for selecting %d DVD%s. The total price will be $%.2f\n", sel, plural[sel], price);
    fprintf(stdout, "\n\n");
    return(0);
}

```

---

