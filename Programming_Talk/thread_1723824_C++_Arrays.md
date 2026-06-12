---
title: "C++ Arrays"
date: 2011-04-07
forum: Programming Talk
---

### Post by CM Xtasy on 2011-04-07
I'm having trouble adding asterisks (*) to the end of my lines.  Here's what it's supposed to look like 

```
Belvidere        **********
Freeport         ********
Byron            ************
Stillman Valley  ***************
Rockford         *********
```

Each * represents a point each city has.  Here is my code:

```
#include <iostream>
#include <iomanip>
using namespace std;

// constants
// Dimensions beyond first must be global
const int CITY_SIZE = 20;

int main(void)
{
    // constants
    const int SIZE = 5;


    // function prototype(s)
    // return by value is used
    void printStars(const int [], const char [][CITY_SIZE], const int);

    // local data (other than arrays)

    // array data declaration(s) & initialization(s)
    // array data: use data from sample output above
    // TODO #1: declare & initialize array of ten integers
	int points[] = {10,
					8,
					12,
					15,
					9};

    // TODO #2: declare & initialize array of five cities

	char cities[][CITY_SIZE] = {"Belvidere",
                                "Freeport",
                                "Byron",
                                "Stillman Valley",
								"Rockford"};

    // start the program
    cout << "*** start of 276Arrays_Ex04.cpp program ***" << endl;
    cout << endl;

    // display the required output
    // TODO #3: call display function, passing count array & size
    printStars(points, cities, SIZE);

    // terminate the program
    cout << endl;
    cout << "*** end of 276Arrays_Ex04.cpp program ***" << endl << endl;
    cin.get();

    return 0;
}   // end main()

//--------------------------------------------------------------------//
// Function Name: printStars(const int[],
//                            const char [][], const int)
// Purpose: to display cities and their points in a graph
// Values received: city points array, citie names array, size
// Values returned: <none>
// Notes:
//               Prints column headings
//               Loop until all cities processed
//                  print row label (name of one city)
//                  Loop until all stars printed for one city
//                     One star is printed
//                  End inner loop
//                  New line
//               End outer loop
//--------------------------------------------------------------------//
// TODO #4: code the display function
void printStars(const int points[],
                const char cities[][CITY_SIZE],
                const int size)
{
   
   // print column headings
   cout << left << setw(15);
   cout << "City";
   cout << setw(2) << " "; // insert 2 spaces between
   cout << left << setw(21);
   cout << "City Points";
   cout << endl;
   cout << endl;
   cout << "---------------";
   cout << setw(2) << " "; // insert 2 spaces between
   cout << "1---5----10---15---20";
   cout << endl;


   // print detail lines
   for (int i = 0; i < size; i++)
   {
      // print city name

	cout << cities[i];
	cout << endl;

      // nested for loop
	for (int stars = 0; stars < points[i]; stars++)
   {
      // print stars for the city

 

	}
   }
}

```

The problem lies at the very bottom in the "print stars for the city"  I've tried everything but I never get the * next to the names like they are supposed to. Any suggestions?

---

### Post by Some Penguin on 2011-04-07
```

        cout << cities[i];
	cout << endl;

```

Ask yourself what this does.

---

### Post by CM Xtasy on 2011-04-07
> **Some Penguin said:**
> ```

        cout << cities[i];
	cout << endl;

```

Ask yourself what this does.

I tried cout << cities[i] << "*" << endl;

but how do get the correct amount of * by each specific city?

---

### Post by smartbei on 2011-04-08
The endl writes a newline to stdout, so you would probably want to write the *s before it. As for writing the correct amount - It looks like you have a for loop that will do nicely :-).

---

### Post by Blackbug on 2011-04-15
yes agree with the previous post..
you are using endl, which will put a new line of the output screen...

---

