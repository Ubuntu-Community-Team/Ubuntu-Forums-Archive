---
title: "C++ Calendar"
date: 2008-11-12
forum: Programming Talk
---

### Post by Neon612 on 2008-11-12
I'm working on a C++ printed calendar. The user enters the number of days in the month and the day it starts on (1 for Sun, 2 for Mon ...), but at the moment I've left those variables set when initialized for ease of use. It is a project for school but I have everything working except the day it starts on. No matter what number is entered it still places the first day on Sunday.

And also on a side note, I need to try to refrain from using the same typed code over and over, and it needs to be easy to change the size of the boxes.

Any and all help will be appreciated. Thank you.

[php]#include <iostream>

using namespace std;

void PrintEmptyLine(int Width)

{
	for (int i=0; i<=((Width+1)*7)-6; i++)
	{
		if (i%Width == 0)
		{
			cout << "*";
		}
		else
		{
			cout << " ";
		}
	}
	cout << endl;
}

void PrintLine(int Width)
{
	for (int i=1; i<=((Width+1)*7)-6; i++)
	{
		cout << "*";
	}
	cout << endl;
}

int main()
{
    // Declare constants (first day of the month, number of days)

	int firstday = 2, numdays = 30;
	const int ColWidth  = 8;
	const int ColHeight = 4;

	/*cout << "Enter number of days in month: ";
	cin  >> numdays;
	cout << "Enter day month starts on (1=Sunday, 2=Monday): ";
	cin  >> firstday;*/

    // Display first line with the name of each day
	cout << "   Sun     Mon     Tue     Wed     Thu     Fri     Sat   " << endl;

    

    // Display line of stars
	for (int x = 1; x <= ColWidth*7+1; x++)
	{
		cout << "*";
	}
	cout << endl;



    // Declare counter for days, starts at 0

	int daycount = 0;



    // We loop for each week

    for (int i = 0; i < 6; i++)
    {
    	if (i >= 1)
    	{
    		cout << "*";
    	}
    	
    	// We loop for each day

        for (int j = 0; j < 7; j++)
        {
        	// If we already displayed all days of the month, break out

		if (daycount > numdays)
		{
		for (int z=0; z<=ColWidth-2; z++)
	   		{
	   			cout << " ";
	   		}
			cout << "*";
			continue;
		}

            	// If we already started counting, display the date

            	if (daycount != 0)

	   	{
	   		if (daycount < 10)
	   		{
	   			for (int z=0; z<=ColWidth-3; z++)
	   			{
	   				cout << " ";
	   			}
	   			cout << daycount << "*";
	   		}
	   		else if (daycount >= 10)
	   		{
	   			for (int z=0; z<=ColWidth-4; z++)
	   			{
	   				cout << " ";
	   			}
	   			cout << daycount << "*";
	   		}



                	// Increment counter

                	daycount++;

            	}

            	// If we didn't start counting yet

           	 else if (daycount == 0)
           	 {

                	// display white space where the date would be


                	//cout << "    ";

                	// Start counting on the day before the starting day

                	if (j < firstday)
                	{
                		daycount++;
                		//cout << "       *";
                		//continue;
                		break;

                    		cout << daycount;

                	}

            	}



        }

        // Each week is displayed on a separate line
        if (i < 1)
        {
        	continue;
        }
        

        cout << endl;
        for (int a = 0; a <= ColHeight-3; a++)
        {
        	PrintEmptyLine(ColWidth);
        }
        PrintLine(ColWidth);

    }



    return 0;

}[/php]

---

### Post by dwhitney67 on 2008-11-12
I rewrote your program, but unfortunately I cannot provide you with it since you stated that you are working on a class assignment.

One thing that I noticed as I was developing the program was that I was too focused, as it appears you are, on making the output look pretty.

If I were you, I would comment out (or just remove) all of the code in the for-loop dealing with the days of the week, and concentrate more on the logic in there... from scratch.

The first thing your code needs to determine is whether it will display the 'daycounter', or merely display white-space for the day of the week.  Your 'firstday' will be used in determining this.

Once you have finished displaying the first week, the 'firstday' is no longer relevant.

The other thing you need to do is to check if the 'daycount' is greater than or equal to the 'numdays'.  If so you are done.  You may want to check this in both loops, but it is not necessarily required.

One other thing I recommend is that you refrain from using single-character variables for your for-loops.  Choosing words like 'week' and 'weekday' may help you understand your code better.

I also recommend that you study the I/O manipulators (e.g. setw() and setfill()) to make your code a bit cleaner.

If you do not have a requirement to display the calendar with a border, then I would recommend that you display in a similar fashion as used by the "cal" command.

---

### Post by Neon612 on 2008-11-13
I do need the border, the book I'm using has it displayed exactly like this (except for a working startday setting)

Where would I need to put the firstday selector in? I know it goes inside the "day" loop but where inside that?

---

### Post by dwhitney67 on 2008-11-13
Here's a hint:
[php]
if (week == 0 && weekday < firstday)
{
  ...
}
else
{
   ...
}
[/php]

---

