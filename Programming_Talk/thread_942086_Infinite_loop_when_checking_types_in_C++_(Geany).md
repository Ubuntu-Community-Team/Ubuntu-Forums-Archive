---
title: "Infinite loop when checking types in C++ (Geany)"
date: 2008-10-08
forum: Programming Talk
---

### Post by RobertWaelder on 2008-10-08
I'm writing a program for an introductory course in C++, and the purpose of the program is to take three grades and then find the average and display the total class grade. I have a while loop that checks for errors in the input, e.g. whether the user inputted the correct range of numeric characters. Here is what I came up with (the offending code is in italics):

```

	// prompt for first score...

	cout << "\n\nEnter the first score: ";

	cin >> score;



	/**********************************

	| error checking:                 |

	| this structure ensures an error |

	| will not be inadvertently       |

	| undetected if it is farther     |

	| back in the sequence            |

	**********************************/

	while (score > 50 || typeid(score) != typeid(sum) || score < 0)

	{

		[I]while (typeid(score) != typeid(sum))

		{

			cin.sync();

			cin.clear();

			cout << "\nError! Enter an integer: ";

			cin >> score;

		}
[/I]
		while (score > 50)

		{

			cin.sync();

			cin.clear();

			cout << "\nError! Scores cannot be greater than 50: ";

			cin >> score;

		}

		while (score < 0)

		{

			cin.sync();

			cin.clear();

			cout << "\nError! Enter a positive number: ";

			cin >> score;

		}

	}

	

	// add the first score to the total points

	sum += score;



	// prompt for second score...

	cout << "\nEnter the second score: ";

	cin >> score;


```

When I enter a letter or string, it simply infinitely loops "Error! Enter an integer: ". I also tried using !cin instead of typeid() and I get the same results. Maybe my approach is too complicated? Thanks in advance for your advice! My teacher hasn't been responding to my questions.

---

### Post by Sydius on 2008-10-08
In all my years of C++ programming, I've never come across typeid before.  Funny I missed it.

How is score defined?

---

### Post by RobertWaelder on 2008-10-08
Yea, I was searching for alternate methods of checking for bad input besides !cin and I found typeid. Seems it could be a useful tool.

I defined score as an integer.

---

### Post by dwhitney67 on 2008-10-08
If I recall, typeid comes from the RTTI (Run Time Type Identifier) library that is part of C++.  It is not widely used because it compromises the performance of an application.

There are other ways to determine if the data that has been read in using 'cin' is valid.  One can use cin's fail() function.

For instance:
[PHP]while ( true )
{
  std::cout << "Enter a number: ";
  std::cin  >> number;

  if ( !std::cin.fail() )
    break;

  // error detected
  cin.clear();                // clear the flag(s)
  cin.ignore( 1024, '\n' );   // clear the cin buffer

  std::cout << "Dumb fool, I said enter a number!" << std::endl;
}[/PHP]

RobertWaelder -

Has your class covered arrays yet?  Consider declaring an array to hold 3 unsigned integers.  Then loop around 3 times prompting the user to enter the test grades.  When the loop ends, tally the scores and compute the average.

Finally, output the 3 test scores (optional) and the average.

---

### Post by RobertWaelder on 2008-10-09
Hmm, I changed the code as you suggested, to cin.fail() (i didn't include the std:: parts though, what is that?). I also used a counter-controlled loop to simplify the code a bit. I still get the infinite loop issue though. Do I need to add the break in this part?  

[PHP]
if ( !std::cin.fail() )
    break;
[/PHP]

The current code looks like:

[PHP]
// Robert Waelder

// COP1000.02

// This project accepts grades as input,

// and calculates the total grade.



#include <iostream>

using namespace std;



int main()

{

	// declare variables...

	int score;

	int sum = 0;

	int totalAvg = 0;

	

	// set a counter for the main loop

	int count = 0;

	

	// these variables will later be used to

	// determine the letter grade

	const int gradeA = 90;

	const int gradeB = 80;

	const int gradeC = 70;

	const int gradeD = 60;

	const int gradeF = 50;



	// greet user...

	cout << "Welcome to the grade calculator!\n"

		 << "This program will take three\n"

		 << "scores as input, and output the\n"

		 << "average of the grades.";

	while (count < 3)

	{

		// prompt for a score...

		cout << "\n\nEnter a score: ";

		cin >> score;



		/**********************************

		| error checking:                 |

		| this structure ensures an error |

		| will not be inadvertently       |

		| undetected if it is farther     |

		| back in the sequence            |

		**********************************/

		while (score > 50 || cin.fail() || score < 0)

		{

			while (cin.fail())

			{

				cin.sync();

				cin.clear();

				cout << "\nError! Enter an integer: ";

				cin >> score;

			}

			while (score > 50)

			{

				cin.sync();

				cin.clear();

				cout << "\nError! Scores cannot be greater than 50: ";

				cin >> score;

			}

			while (score < 0)

			{

				cin.sync();

				cin.clear();

				cout << "\nError! Enter a positive number: ";

				cin >> score;

			}

		}

		

		// add the third score to the total points

		sum += score;

		count++;

	}

	// calculate grades...

	totalAvg = 2*(sum/3);

	

	// output grades...

	cout << "\nYour total average for the class is " << totalAvg << ".\n";

	

	// this section displays custom messages

	// that depend on the grade earned.

	if (totalAvg >= gradeA)

	{

		cout << "\nCongratulations! You received an A!"

			 << "\nNow go grab a beer, you deserve it.";

	}

	else if (totalAvg >= gradeB)

	{

		cout << "\nGood job! You received a B!";

	}

	else if (totalAvg >= gradeC)

	{

		cout << "\nNot bad. You received a C.";

	}

	else if (totalAvg >= gradeD)

	{

		cout << "\nStudy harder. You received a D.";

	}

	else if (totalAvg >= gradeF)

	{

		cout << "\nYou fail. You received an F.";

	}

	else if (totalAvg == 0)

	{

		cout << "\nWow. You received a ZERO."

			 << "\nYou suck at life.";

	}



	// say goodbye...

	cout << "\n\nThank you for using the grade calculator."

		 << "\nWritten by Robert Waelder, 2008.\n";



	// terminate successfully

	return 0;

}

[/PHP]

It's a little more elegant now, but still produces the same error. I am beginning to think it may be an issue with Geany, because the program seems to work fine on the school computers....

Thanks for your replies! Ya'll are one in a million.

---

### Post by Sydius on 2008-10-09
I think the key might be this part:

```
cin.ignore( 1024, '\n' );
```

I think, unless you have that, it keeps the invalid value in the input buffer forever (because you never actually get it out).  This command tells it to ignore what's there, which effectively resets it.

Other than that, you seem to be using while loops where you should use if statements (a single while loop with several if statements inside would probably be best).

---

### Post by dribeas on 2008-10-09
> **RobertWaelder said:**
> 

The current code looks like:

[PHP]
int main()
{
//...
	while (count < 3) 
	{
		cin >> score; 
		while (score > 50 || cin.fail() || score < 0) 
		{
			while (cin.fail())
			{
				cin.clear();
				cin >> score;
			}

			while (score > 50) 
			{
				cin.clear();
				cin >> score;
			}

			while (score < 0) 
			{
				cin.clear();
				cin >> score;
			}
		}
		sum += score;

		count++;
	}
	// ...
}
[/PHP]


Your code seems overly complex for the task at hand. Try to explain in plain words what it is mean to do and then translate to C++. Or in general any other programming language, programming is having a clear idea of what you want and then telling the computer in the appropriate programming language.

If I were to read (in plain english) what your code does I don't think I could do it in plain words... too many nested whiles there. Consider wheter they are necessary.

My approach to the algorithm would be:

```

- repeat until 3 correct grades have been read
--- repeat while failed to read or grade is invalid
-----  try read one grade
--- add the (correct now) grade to the sum
- calculate average of grades
- output result

```

then translate into your programming language:

```

// Translating to C++
// repeat until 3 correct grades have been read
int count = 0; // so that we know how many grades were read
while ( count < 3 ) // or: for ( int count = 0; count < 3; ++count )
{
   // repeat while failed or grade was invalid
   {
      // try reading
   }
   // add the readed grade to the sum
}
// Calculate average
// Output result

```

During that translation phase, you will need to add variable, express formally conditions (what is an invalid grade? how do you know that input failed? how do you restore the input stream if it has failed?)

But from the algorithm you should get an idea of the shape of your code (in this case, basically two nested loops one for the number of grades and one to insist on reading until a valid input was found)

---

### Post by dwhitney67 on 2008-10-09
Using a sum in lieu of the array I had suggested earlier is an easier solution, however you lose the context of the data.  Thus if you wanted to generate a report-card, you could not.  But for now, this is a small issue.  For now, I will go along with summing the scores as you did

See below for changes/comments:

[php]
// Robert Waelder
// COP1000.02
// This project accepts grades as input,
// and calculates the total grade.


#include <iostream>

using namespace std;    // this is where the std namespace is included


int main()
{
  const unsigned int gradeA = 90;
  const unsigned int gradeB = 80;
  const unsigned int gradeC = 70;
  const unsigned int gradeD = 60;
  const unsigned int gradeF = 50;

  cout << "Welcome to the grade calculator!\n"
       << "This program will take three\n"
       << "scores as input, and output the\n"
       << "average of the grades.\n\n";

  unsigned int sum = 0;

  // collect 3 scores...
  for ( unsigned int count = 0; count < 3; ++count )
  {
    unsigned int score = 0;   // declare and initialize;
                              // unsigned int so that it cannot
                              // be a negative number

    // loop until the input data is correct
    while ( true )
    {
      cout << "Enter score #" << (count+1) << " (0-50): ";
      cin  >> score;

      if ( !cin.fail() )
      {
        if ( score > 50 )
        {
          cout << "Error! Scores must be between 0 and 50.\n\n";
          continue;   // go to beginning of while-loop
        }

        // data input was successful; break out of the while-loop
        break;
      }

      // data input was not numeric; clear cin input stream
      // and issue error message.
      cin.clear();
      cin.ignore( 1024, '\n' );
      cout << "Error! Input must be a number...\n\n";
    }

    // add the score to the total points
    sum += score;
  }

  // calculate grades...
  unsigned int totalAvg = 2*(sum/3);

  // output grades...
  cout << "\nYour total average for the class is " << totalAvg << ".\n";

  // Output grade results that depend on the grade earned.
  if (totalAvg >= gradeA)
  {
    cout << "\nCongratulations! You received an A!"
         << "\nNow go grab a beer, you deserve it.";
  }
  else if (totalAvg >= gradeB)
  {
    cout << "\nGood job! You received a B!";
  }
  else if (totalAvg >= gradeC)
  {
    cout << "\nNot bad. You received a C.";
  }
  else if (totalAvg >= gradeD)
  {
    cout << "\nStudy harder. You received a D.";
  }
  else if (totalAvg >= gradeF)
  {
    cout << "\nYou fail. You received an F.";
  }
  else if (totalAvg == 0)
  {
    cout << "\nWow. You received a ZERO."
         << "\nYou suck at life.";
  }

  cout << "\n\nThank you for using the grade calculator."
       << "\nWritten by Robert Waelder, 2008.\n";

  return 0;
}
[/php]

---

### Post by RobertWaelder on 2008-10-09
Woohoo! It runs beautifully now! I added the cin.ignore line, and that stopped it from looping infinitely, and using ifs instead of whiles allowed the correct error messages to show through. Also, using a for loop for the outer loop seemed much more elegant (as per dwhitney's suggestion).

[PHP]
// Robert Waelder

// COP1000.02

// This project accepts grades as input,

// and calculates the total grade.



#include <iostream>

using namespace std;



int main()

{

	// declare variables...

	int score;

	int sum = 0;

	int totalAvg = 0;

	

	// these variables will later be used to

	// determine the letter grade

	const int gradeA = 90;

	const int gradeB = 80;

	const int gradeC = 70;

	const int gradeD = 60;

	const int gradeF = 50;



	// greet user...

	cout << "Welcome to the grade calculator!\n"

		 << "This program will take three\n"

		 << "scores as input, and output the\n"

		 << "average of the grades.";

	for (int count = 0; count < 3; ++count)

	{

		// prompt for a score...

		cout << "\n\nEnter a score: ";

		cin >> score;



		/**********************************

		| error checking:                 |

		| this structure ensures an error |

		| will not be inadvertently       |

		| undetected if it is farther     |

		| back in the sequence            |

		**********************************/

		while (score > 50 || cin.fail() || score < 0)

		{

			if (cin.fail())

			{

				cin.sync();

				cin.clear();

				cin.ignore( 1024, '\n' );

				cout << "\nError! Enter an integer: ";

				cin >> score;

			}

			else if (score > 50)

			{

				cin.sync();

				cin.clear();

				cin.ignore( 1024, '\n' );

				cout << "\nError! Scores cannot be greater than 50: ";

				cin >> score;

			}

			else if (score < 0)

			{

				cin.sync();

				cin.clear();

				cin.ignore( 1024, '\n' );

				cout << "\nError! Enter a positive number: ";

				cin >> score;

			}

		}

		

		// add the third score to the total points

		sum += score;

	}

	// calculate grades...

	totalAvg = 2*(sum/3);

	

	// output grades...

	cout << "\nYour total average for the class is " << totalAvg << ".\n";

	

	// this section displays custom messages

	// that depend on the grade earned.

	if (totalAvg >= gradeA)

	{

		cout << "\nCongratulations! You received an A!"

			 << "\nNow go grab a beer, you deserve it.";

	}

	else if (totalAvg >= gradeB)

	{

		cout << "\nGood job! You received a B!";

	}

	else if (totalAvg >= gradeC)

	{

		cout << "\nNot bad. You received a C.";

	}

	else if (totalAvg >= gradeD)

	{

		cout << "\nStudy harder. You received a D.";

	}

	else if (totalAvg >= gradeF)

	{

		cout << "\nYou fail. You received an F.";

	}

	else if (totalAvg == 0)

	{

		cout << "\nWow. You received a ZERO."

			 << "\nYou suck at life.";

	}

	return 0;

}

[/PHP]

Ahhh! So much better! Alot cleaner and more readable. Thanks for all the advice, Sydius and dwhitney.

---

### Post by dwhitney67 on 2008-10-09
Now if you can get rid of the excessive vertical white-space in the code, that would be a big plus.  :)

P.S.  I just looked at your last code posting... it can still be made much "cleaner".  See my previous post.

---

### Post by RobertWaelder on 2008-10-09
Oh wow. There's is so much interesting material in your last post, dwhitney. I'll need to pore over that for awhile... I especially find the unsigned ints interesting. Is it really necessary to make the grades unsigned though, since they are constants?

And I have no clue what's going on with that whitespace.... my code in geany doesn't have it. It doesn't even look like that when I paste it into the message box. Wierd.

EDIT: Nevermind. I ran my code and quickly figured out why I need to make them all unsigned ints.

---

### Post by dwhitney67 on 2008-10-09
You should define your variables (constants or other) to fit the data you expect.  If you declare data to be one type (say int) and compare it to an unsigned int, you will get a warning... if you compile using the -Wall compiler flag.

I recommend that you insert the following alias into your ~/.bashrc file:
```
alias g++='g++ -Wall -pedantic'
```
It will make you into an "honest" programmer!  If you try to cut corners, g++ will warn you.

---

### Post by RobertWaelder on 2008-10-09
Ah, I see! Interesting. Added that line to my bashrc. I think I was already getting those error messages, but I'm not entirely sure.

The instructor for our class taught us to use cin.sync() clear the buffer. What is the difference between it and cin.ignore()?

Anyway, hopefully the code is up to snuff.

[php]
// Robert Waelder 
// COP1000.02 
// This project accepts grades as input, 
// and calculates the total grade. 
 
#include <iostream> 
using namespace std; 
 
int main() 
{ 
    // declare variables... 
    unsigned int sum = 0; 
     
    // these variables will later be used to 
    // determine the letter grade 
    const unsigned int gradeA = 90; 
    const unsigned int gradeB = 80; 
    const unsigned int gradeC = 70; 
    const unsigned int gradeD = 60; 
    const unsigned int gradeF = 50; 
 
    // greet user... 
    cout << "Welcome to the grade calculator!\n" 
         << "This program will take three\n" 
         << "scores as input, and output the\n" 
         << "average of the grades.\n"; 
    for (unsigned int count = 0; count < 3; ++count) 
    { 
        unsigned int score; 
        /********************************** 
        | error checking:                 | 
        | this structure ensures an error | 
        | will not be inadvertently       | 
        | undetected if it is farther     | 
        | back in the sequence            | 
        **********************************/ 
        while (true) 
        { 
            // prompt for a score... 
            cout << "\nEnter score #" << (count+1) << " (0-50): "; 
            cin >> score; 
            if (!cin.fail()) 
            { 
                if (score > 50) 
                { 
                    cout << "Error! Scores must be from 0-50.\n"; 
                    continue; 
                } 
                break; 
            } 
            cin.clear(); 
              cin.ignore( 1024, '\n' ); 
              cout << "Error! Input must be a positive number.\n"; 
        } 
         
        // add score to the total points 
        sum += score; 
    } 
    // calculate grades... 
    unsigned int totalAvg = 2*(sum/3); 
     
    // output grades... 
    cout << "\nYour total average for the class is " << totalAvg << ".\n"; 
     
    // this section displays custom messages 
    // that depend on the grade earned. 
    if (totalAvg >= gradeA) 
    { 
        cout << "\nCongratulations! You received an A!" 
             << "\nNow go grab a beer, you deserve it."; 
    } 
    else if (totalAvg >= gradeB) 
    { 
        cout << "\nGood job! You received a B!"; 
    } 
    else if (totalAvg >= gradeC) 
    { 
        cout << "\nNot bad. You received a C."; 
    } 
    else if (totalAvg >= gradeD) 
    { 
        cout << "\nStudy harder. You received a D."; 
    } 
    else if (totalAvg >= gradeF) 
    { 
        cout << "\nYou fail. You received an F."; 
    } 
    else if (totalAvg == 0) 
    { 
        cout << "\nWow. You received a ZERO." 
             << "\nYou suck at life."; 
    } 
    return 0; 
} 
[/php]Very nice! I definitely learned a lot tonight. Phew, it's getting late. Good night!

(And as a side note... I finally got rid of that pesky white space! w00t.)

---

### Post by dwhitney67 on 2008-10-09
> **RobertWaelder said:**
> 
...
The instructor for our class taught us to use cin.sync() clear the buffer. What is the difference between it and cin.ignore()?
...

I'm not sure what sync() is supposed to do.  I tried following an [example]("http://www.cplusplus.com/reference/iostream/istream/sync.html"), but it did not work as "advertised".  Hence the reason why I use ignore()... it works!  :-)

Btw, your code looks much better.

---

### Post by RobertWaelder on 2008-10-09
I wonder if it has anything to do with our using Visual C++ at school. I'll compile my program at school and see if both sync() and ignore() work. I have to wonder, because my program ran fine at school using sync(), with no infinite looping issues. Perhaps it's just not well supported.

Now, the only part of your code I didn't quite understand was that while (true) part. While what is true?

---

### Post by dwhitney67 on 2008-10-09
[PHP]while (true) { ... }[/PHP]
or
[PHP]while (1) { ... }[/PHP]
or
[PHP]for (;;) { ... }[/PHP]
are all equivalent infinite-loop constructs.  Most times (but not always), it is desirable to exit the infinite loop, thus when a condition is met, the loop can be exited using the "break" statement.

---

### Post by RobertWaelder on 2008-10-09
Ah! I see now. Now that all makes perfect sense. I feel like I should cite you in my code :)

---

