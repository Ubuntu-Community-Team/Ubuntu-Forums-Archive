---
title: "Looking for opinion on my code"
date: 2007-06-14
forum: Programming Talk
---

### Post by TreeFinger on 2007-06-14
I have been reading my C++ book. I am just getting into chapter two which covers control structures. After reading some and getting some useful information I headed back to some of the problems from Ch. 1 and did them. I am wondering if you experienced programmers out there could tell me if my code is readable? I know an important thing is for code to be readable to find bugs, etc. 

Here is a program I wrote that finds if a number is a multiple of the other.
```

// 2 integers first & second, finds if second is multiple of first

#include <iostream>

using std::cout;
using std::cin;
using std::endl;

int main()
{
int first;
int second;
int multiple;
int cont = 1;	// 1 Means to Continue, 0 means end program

	while (cont == 1)
	{
	cout << "Enter the greater integer: ";
	cin >> first;
	cout << endl;
	cout << "Enter number to find if it is multiple of the first: ";
	cin >> second;

multiple = first % second;

	if ( multiple == 0 )
		{
			cout << second << " is a multiple of " << first << endl;
			cout << "Enter 1 to find multiple of another number, 0 to exit\n";
			cin >> cont;
		}
	else
		{
			cout << second << " is NOT a multiple of " << first << endl;
			cout << "Enter 1 to find multiple of another number, 0 to exit\n";
			cin >> cont;
		}
	}
return 0;
}

```

It works perfectly as far as I can tell. This program makes me curious about data types. I would like to be able to use numbers with decimals in the program. Any tips on how to do that? Thanks in advance.

---

### Post by TreeFinger on 2007-06-14
I wanted to fix a bug where if user accidentally presses something other than 1 or 0 for entering another set of numbers the program would go into infinite while loop. So I did :)

```

// 2 integers first & second, finds if second is multiple of first

#include <iostream>

using std::cout;
using std::cin;
using std::endl;

int main()
{
int first;
int second;
int multiple;
int cont = 1;	// 1 Means to Continue, 0 means end program

	if (cont == 1)
	{
	cout << "Enter the greater integer: ";
	cin >> first;
	cout << endl;
	cout << "Enter number to find if it is multiple of the first: ";
	cin >> second;

multiple = first % second;

	if ( multiple == 0 )
		{
			cout << second << " is a multiple of " << first << endl;
			cout << "Enter 1 to find multiple of another number, any other key to exit\n";
			cin >> cont;
		}
	else
		{
			cout << second << " is NOT a multiple of " << first << endl;
			cout << "Enter 1 to find multiple of another number, any other key to exit\n";
			cin >> cont;
		}	
	}
	else
		return 0;
}

```

---

### Post by GeneralZod on 2007-06-14
Not bad at all for Chapter 2 :)

I don't like the indentation style at all, but this is a) personal and b) easily fixed in any case.  I would definitely use the variable name  "remainder" instead of the name "multiple", though, as "multiple" is not an accurate description of the value of "first % second".

Edit:

Also, I think that "first % second" will likely crash if "second" is 0, so you should guard against this and let the user know that you can't do this.

---

### Post by Mathiasdm on 2007-06-14
I'm going to have to agree on the indentation style, it's very confusing ;)

```


//first & second, finds if second is multiple of first

#include <iostream>

using std::cout;
using std::cin;
using std::endl;

/* You can replace the 3 lines above by 'using namespace std', but it's not required */

int main()
{
int first;
int second;
int multiple;
int cont = 1;	// 1 Means to Continue, 0 means end program
//You can also use a 'bool' instead of an 'int' for the 'cont' variable, that way you only have the value 'true' or 'false'

	while (cont == 1) { //It needs to be 'while' instead of 'if' to go in an infinite loop
		cout << "Enter the greater integer: ";
		cin >> first;
		cout << endl;
		cout << "Enter number to find if it is multiple of the first: ";
		cin >> second;

		multiple = first % second;

		if ( multiple == 0 ) {
			cout << second << " is a multiple of " << first << endl;
			cout << "Enter 1 to find multiple of another number, any other key to exit\n";
			cin >> cont;
		}
		else {
			cout << second << " is NOT a multiple of " << first << endl;
			cout << "Enter 1 to find multiple of another number, any other key to exit\n";
			cin >> cont;
		}	
	}
	return 0;
}

```

If you want to work with numbers like 0.1 or 3.1415, you'll need to use 'double' or 'float' instead of 'int' for the numbers.

---

### Post by xtacocorex on 2007-06-14
One of the big things I see with new programmers is a lack of indentation, where you have a lot.  The indentation may be a bit much (like the others have said before), **but** it is far more readable than a code that is not indented.

I'm glad to see someone learn to program with is caring about readability.

---

### Post by pmasiar on 2007-06-14
> **Mathiasdm said:**
> I'm going to have to agree on the indentation style, it's very confusing ;)

LOL and then people say that having indentation fixed (part of syntax) like Python has is bad. 

Freeform indentation is exactly the kind of freedom you don't need -- to avoid empty discussions like the one above :-)

Sorry I could not resist :-)

---

### Post by ruy_lopez on 2007-06-14
Since you are factorising, you might as well find all factors and be done with it.

```


// factorise n

int main()
{
        int n, i;

        cout << "number to factorise: ";
        cin >> n;

        for (i = n; i > 0; i--)
                if (n % i == 0)
                        cout << i << "\n";
        return;
}
```

As far as I'm concerned, though, your program suffers from a more serious flaw: it's written in C++. ; )

---

### Post by Mathiasdm on 2007-06-14
> **pmasiar said:**
> LOL and then people say that having indentation fixed (part of syntax) like Python has is bad. 

Freeform indentation is exactly the kind of freedom you don't need -- to avoid empty discussions like the one above :-)

Sorry I could not resist :-)

The reason I say this, is because some indented parts in the same loop are not indented the same amount. That's confusing, and, when skimming code, can be rather annoying. ;)

> **ruy_lopez said:**
> 
As far as I'm concerned, though, your program suffers from a more serious flaw: it's written in C++. ; )
That's your opinion. Doesn't mean it's right.

---

### Post by harun on 2007-06-14
Do:
```

using namespace std;

```
instead of:
```

using std::cout;
using std::cin;
using std::endl;

```
I see now Mathiasdm already suggested this.

Do consider using prefixes on your variable names to set them off from the C++ key words and other control structure words. You will notice right away the added readability. So instead of this:
```

int first;
int second;
int multiple;
int cont = 1;	// 1 Means to Continue, 0 means end program

```
Somthing like this:
```

    int l_iFirst;
    int l_iSecond;
    int l_iMultiple;
    int l_iCont = 1;	// 1 Means to Continue, 0 means end program

```

The lower case "L" telling you the variables are *local* to main and not member variables or global, and the lower case "I" telling you they are ints.

You are doing very well for just starting out. You are already concentrating on something the vast majority of programmers overlook and that is readability.

---

### Post by Jessehk on 2007-06-14
> **harun said:**
> Do:
```

using namespace std;

```
instead of:
```

using std::cout;
using std::cin;
using std::endl;

```


Why is one preferable to the other? AFAIK, it is a matter of personal preference, so I don't think you should be representing yours as fact.


> 
Do consider using prefixes on your variable names to set them off from the C++ key words and other control structure words. You will notice right away the added readability. So instead of this:
```

int first;
int second;
int multiple;
int cont = 1;	// 1 Means to Continue, 0 means end program

```
Something like this:
```

    int l_iFirst;
    int l_iSecond;
    int l_iMultiple;
    int l_iCont = 1;	// 1 Means to Continue, 0 means end program

```

The lower case "L" telling you the variables are *local* to main and not member variables or global, and the lower case "I" telling you they are ints.


In my experience (which is admittedly very little), Hungarian notation actually decreases readability. Oh, well. Once again, this is a matter of personal preference.

---

### Post by hod139 on 2007-06-14
> **harun said:**
> Do:
```

using namespace std;

```instead of:
```

using std::cout;
using std::cin;
using std::endl;

```I see now Mathiasdm already suggested this.

This is very bad advice.  The entire point of namespaces are to prevent naming collisions, and the using directives dumps multiple namespaces together, defeating the goal of the namespaces.  You should get into the habit of using the std:: prefix or, if you must, only bring in what you need with the using-declartion (e.g.  using std::cout).   Again, you should **never** use the using namespace std directive. For more reasons, you can read the [c++ faq on using namespace std]("http://www.parashift.com/c++-faq-lite/coding-standards.html#faq-27.5")

> 
Do consider using prefixes on your variable names to set them off from the C++ key words and other control structure words. You will notice right away the added readability. <snip>I"m not sure coding standards like this actually help.  More important issues exist, like  software design, than pretty printing your code.


Edit: I should add, to the OP, except for some strange indentation your first coding example looks pretty good.  Make sure you watch our for a mod by zero which isn't possible.

---

### Post by Mathiasdm on 2007-06-15
Just mentioning: I only mentioned the 'using namespace std', because it was another possibility ;)

---

### Post by harun on 2007-06-15
> **hod139 said:**
> This is very bad advice.  The entire point of namespaces are to prevent naming collisions, and the using directives dumps multiple namespaces together, defeating the goal of the namespaces.  You should get into the habit of using the std:: prefix or, if you must, only bring in what you need with the using-declartion (e.g.  using std::cout).   Again, you should **never** use the using namespace std directive. For more reasons, you can read the [c++ faq on using namespace std]("http://www.parashift.com/c++-faq-lite/coding-standards.html#faq-27.5")


I am glad you posted that link to the FAQ. At the end of that section it states:

*Just remember that you are part of a team, so make sure you use an approach that is consistent with the rest of your organization.*

If you are coding for yourself you can take the practical approach or the purist approach (if one considers the C++ FAQ Lite an authority, which the previous poster I guess does and I do not). If working professionally in an organization you would use the convention used previously and continue to go with it.

I do disagree that you say this is "*very bad advice*" and think you are wasting peoples time and confusing beginners by saying such. The poster asked for **opinion's** on their code. Not for people to give their opinions on other peoples **opinion's**. 

Bjarne Stroustrup, the creator of C++ gives the example the other way, right out of the box to new students:

[http://www.research.att.com/~bs/bs_faq2.html#simple-program](http://www.research.att.com/~bs/bs_faq2.html#simple-program)

If it was *really bad advice* the creator of the language would not start off new students doing things that way. It is simply another way to do things and there are **many**.

---

### Post by hod139 on 2007-06-15
> **harun said:**
> 
I do disagree that you say this is "*very bad advice*" and think you are wasting peoples time and confusing beginners by saying such. The poster asked for **opinion's** on their code. Not for people to give their opinions on other peoples **opinion's**. 

The problem I had with your post, and my reason for responding sharply, is that your "opinion" came across as an authoritative fact.  The using directive was created to allow backwards compatibility with older C++ code and to ease the transition into namespaces.  However, it also allows for lazier programming, since you can bring in the entire namespace.  For smaller programs, such as the OP or Stroustrup's examples on his website, the using directive is probably okay; but (and this is my opinion) one should get into the habit of not using the using directive.  As stated in my first post, the using directive defeats the original design goals of namespaces, and (in my opinion, and many others) shouldn't be used.  This is especially true in larger projects.   Also, you should never put a using directive into a header file.

---

### Post by nomats on 2007-06-15
It's not a good idea to read user input directly to int. You should read it to a string first and then parse to the form you need it to be. char arrays are also bad idea because they have a maximum length. Otherwise good job. Keep it up.

---

### Post by slavik on 2007-06-15
may I suggest using a bool variable for continuing, instead of an int? (an int is used in C, C++ has boolean variables) :)

as it stands, your code is readable, but I would've done things differently (and added more error checking :))

---

### Post by hod139 on 2007-06-15
> **nomats said:**
> It's not a good idea to read user input directly to int. You should read it to a string first and then parse to the form you need it to be. 
cin is type safe, there is nothing wrong with reading it directly into an int.  For example, if I run the OP's code and give bad input
```

Enter the greater integer: r

Enter number to find if it is multiple of the first: 134519592 is NOT a multiple of -1210139940
Enter 1 to find multiple of another number, any other key to exit

```

As other's have mentioned, what the OP should be doing is checking that the read was successful, along with many other missing checks.  But it is perfectly fine to use cin to read to an int.

---

### Post by nomats on 2007-06-15
> **hod139 said:**
> cin is type safe, there is nothing wrong with reading it directly into an int.  For example, if I run the OP's code and give bad input
```

Enter the greater integer: r

Enter number to find if it is multiple of the first: 134519592 is NOT a multiple of -1210139940
Enter 1 to find multiple of another number, any other key to exit

```

As other's have mentioned, what the OP should be doing is checking that the read was successful, along with many other missing checks.  But it is perfectly fine to use cin to read to an int.

but what's the point in checking whether r is a multiple of some number? just because it doesn't make the program crash doesn't mean that it makes sense.

---

### Post by hod139 on 2007-06-15
> **nomats said:**
> but what's the point in checking whether r is a multiple of some number? just because it doesn't make the program crash doesn't mean that it makes sense.

I don't understand what you are saying here.  cin will notify you if the input read is not of the correct type, and let you the programmer decide what to do.  Let me post some code to clarify why reading directly into an int with cin is fine.  I'm going to rewrite the beginning of the OP code, such that error checking is now performed on the input to make sure it is an int.  
```

#include <iostream>

int main()
{
    int first;
    int second;

    while ((std::cout << "Enter the greater integer: ")
          && (!(std::cin >> first))) {
         std::cout << "That's not an int; ";
         std::cin.clear();
         std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n');
    }

    while ((std::cout << "Enter number to find if it is multiple of the first: ")
          && (!(std::cin >> second) || second > first)) {
         std::cout << "That's not an int less than the first number; ";
         std::cin.clear();
         std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n');
    }
 
    // Rest of code

    return 0;
}

```Now a sample run
```

Enter the greater integer: r
That's not an int; Enter the greater integer: t
That's not an int; Enter the greater integer: 4
Enter number to find if it is multiple of the first: g
That's not an int less than the first number; Enter number to find if it is multiple of the first: 9
That's not an int less than the first number; Enter number to find if it is multiple of the first: 3

```This technique is not a new idea and can be found in many books.  The c++ faq also has a section devoted to [input/output]("http://www.parashift.com/c++-faq-lite/input-output.html") and covers this topic exactly.

---

### Post by nomats on 2007-06-16
> **hod139 said:**
> I don't understand what you are saying here. 
i was referring to that example you gave earlier. where r go got transformed into an int.

---

### Post by hod139 on 2007-06-16
> **nomats said:**
> i was referring to that example you gave earlier. where r go got transformed into an int.
Then you misunderstood the example, because 'r' was **never** transformed into an int.  This is what I mean when I say cin is type safe, it won't auto cast anything.  The reason for the strange output in the first example after entering 'r', is because the cin error was never cleared.  But again, r was never read and cast into the int.  What happened was:
1) cin read r, noticed it was not an int, and returned an error.  It did not set the int first.
2  The int second was not read into because the cin error was not cleared
3) The code performed a mod operation on two uninitialized variables (134519592 and -1210139940)

In my second example, I handle the cin errors to demonstrate more clearly the type safety.  Now, if a non int is read, I clear the error and ignore the rest of the input, and repeat until an int is read.  I never have to check the type of the input, cin is doing that for me.

---

### Post by TreeFinger on 2007-06-21
Well here I am again, wondering how readable my code is. Here is an example of a program I just wrote. Please inform me if anything that looks wrong.

```

// Find if 5 digit number is Palindrome
#include <iostream>
using std::cout;
using std::cin;
using std::endl;

int main()
{
int digit;
int first, second, third, fourth, fifth;

cout << "Enter a 5 digit number and I will tell you if it is a palindrome." << endl << "A palindrome is a number that reads the same forward as backward." << endl;

// Identifying original digits
cin >> digit;

fifth = digit / 10000;
fourth = ( digit % 10000 ) / 1000;
third = ( digit % 1000 ) / 100;
second = ( digit % 100 ) / 10;
first = ( digit % 10 );

// Printing individual digits
cout << "1st: " << first << "\t2nd: " << second << "\t3rd: " << third << "\t4th: " << fourth << "\t5th: " << fifth << endl;


if ( first == fifth ) { // Comparing 1st and 5th digit
	if ( second == fourth ) { // Comparing 2nd and 4th digit
	cout << "Your number is a palindrome" << endl;
	}
	else {
	cout << "Your number is NOT a palindrome" << endl;
	}
}
else {
cout << "Your number is NOT a palindrome" << endl;
}
return 0;
}

```

I know I get a little brace happy, but I am just trying to figure out how I will have my braces set up when they are really needed.

---

### Post by Mathiasdm on 2007-06-21
It looks just fine ;)
Now, a question from my side: try to expand your program, so it can check any number (1 digit, 2 digits, 3 digits,...).

---

### Post by hod139 on 2007-06-21
Your indentation is still inconsistent.  I ran your code through the AStyle source code formatter, and it produced:

```

// Find if 5 digit number is Palindrome
#include <iostream>
using std::cout;
using std::cin;
using std::endl;

int main()
{
    int digit;
    int first, second, third, fourth, fifth;

    cout << "Enter a 5 digit number and I will tell you if it is a palindrome." << endl << "A palindrome is a number that reads the same forward as backward." << endl;

// Identifying original digits
    cin >> digit;

    fifth = digit / 10000;
    fourth = ( digit % 10000 ) / 1000;
    third = ( digit % 1000 ) / 100;
    second = ( digit % 100 ) / 10;
    first = ( digit % 10 );

// Printing individual digits
    cout << "1st: " << first << "\t2nd: " << second << "\t3rd: " << third << "\t4th: " << fourth << "\t5th: " << fifth << endl;


    if ( first == fifth )
    { // Comparing 1st and 5th digit
        if ( second == fourth )
        { // Comparing 2nd and 4th digit
            cout << "Your number is a palindrome" << endl;
        }
        else
        {
            cout << "Your number is NOT a palindrome" << endl;
        }
    }
    else
    {
        cout << "Your number is NOT a palindrome" << endl;
    }
    return 0;
}

```
Here the indentation is consistent.  

You never check if the user actually inputs a number.  In a previous post I showed the code to do exactly that.

Why do you want the input to be a number?  Consider reading the input as a string and comparing the characters.

As noted by Mathiasdm, as written your code is not general.  It only works for input of length 5.   I also suggest trying to generalize your algorithm.  Hint, do not use nested if statements.

---

### Post by harun on 2007-06-21
> **hod139 said:**
> The problem I had with your post, and my reason for responding sharply, is that your "opinion" came across as an authoritative fact.  The using directive was created to allow backwards compatibility with older C++ code and to ease the transition into namespaces.  However, it also allows for lazier programming, since you can bring in the entire namespace.  For smaller programs, such as the OP or Stroustrup's examples on his website, the using directive is probably okay; but (and this is my opinion) one should get into the habit of not using the using directive.  As stated in my first post, the using directive defeats the original design goals of namespaces, and (in my opinion, and many others) shouldn't be used.  This is especially true in larger projects.   Also, you should never put a using directive into a header file.

After some research I feel you are correct in your harshness of my post. Thanks for the tip. I didn't think that brought in the **entire** C++ standard library namespace, which it does. Hence I agree with you that doing that is actually a quite bad example to show beginners. I am surpised Stroustrup doesn't just prefix the items with std:: in the beginning examples to get them off on the right foot. I can see the ease of use and readability but a mention of it would certainly be worth while.

---

### Post by TreeFinger on 2007-06-21
I just wrote this simple program as an exercise. The question was just to read a 5 digit number so thats what I did. I could make it so if user inputs something other than a 5 digit number it would ask again but it is not that important to me. I just want to complete these exercises at the end of this chapter so I can move on to functions :)

---

