---
title: "Need Help Finding error"
date: 2006-11-12
forum: Programming Talk
---

### Post by stealth75711 on 2006-11-12
```
#include <iostream>
using namespace std;

void main(void)
{
    // constants
    const int SIZE = 10;

    // function prototype(s)
    // return by value is used
    int computeAverage(const int[], const int);
    int countLessThan(const int[], const int, const int);
    void display(const int, const int);

    // local data
    int intAverage = 0;
    int count = 0;
	int average;
	int sum;
	
	
	

    // data declaration(s) & initialization(s)
    // array data: use data from sample output above
    // TODO: declare & initialize array of ten integers

	int numbers[]={20,17,9,29,19,9,19,20,20,19};

    // start the program
    cout << "*** start of 276Arrays_Ex02.cpp program ***" << endl;
    cout << endl;

    // Compute & return integer average of the array
    // TODO: call computeAverage()function,
    //  which returns average of numbers
	intAverage = computeAverage(numbers, average);

    // Compute & return count of array values less than integer average
    // TODO: call countLessThan() function,
    //  which returns the count of numbers less than the average  
//THis is were the ERROR is	count = countLessThan(SIZE);

    // display the required output
    // TODO: call display function,
    //  passing integer average & count of numbers less than average
    display(intAverage, count);

    // terminate the program
    cout << endl;
    cout << endl;
    cout << "*** end of 276Arrays_Ex02.cpp program ***" << endl << endl;
    cin.get();
    return;
}   // end main()

//--------------------------------------------------------------------//
// Function Name: computeAverage(const int numbers[],
//                                     const int size)
// Purpose: to compute the integer average of the values
// Values received:  array, size of array
// Values returned:  the integer average
// Notes:
//--------------------------------------------------------------------//
// TODO: code the display function

void display(const int intAverage, const int count)
{



   // display average label and average
	cout << "Average Interger Score: ";
	cout << intAverage;
	cout << "Count of Integers Less Than Average: ";
	cout << count;





   // display count less than label and count less than average
 
}

// TODO: code the computeAverage function
	
int computeAverage(int intAverage, int size)
{

   // local variables (if needed)
	int sum = 0;
	int average = 0;
	int numbers;
	
		


   // compute sum
	for(int index = 0; index < size; index++)
	sum += numbers;

   // compute integer average
	average = sum / numbers;
		
   // return integer average
   return average;
}

//--------------------------------------------------------------------//
// Function Name: countLessThan(const int numbers[],
//                                  const int size,
//                                  const int average)
// Purpose: to count array items less than the average
// Values received: array, size of array, integer average
// Values returned: count of numbers less than average
// Notes:
//--------------------------------------------------------------------//

// TODO: code the countLessThan function

int countLessThan(int numbers, int count)
{


   // local variables (if needed)
		
		
   // TODO: using a for loop
   // count number of values less than average
	for(count = 1; count < numbers; count++)
	{
		if(numbers > count)
		count = numbers;
	}
   // return count
   return count;
}
```

---

### Post by hod139 on 2006-11-27
Taking a quick look,
First, main should return an int, not void.

Second, the function prototypes should be declared globally, not local to main.

Lastly, the function prototype for 
```
int computeAverage(const int[], const int)
``` does not match the implementation 
```
int computeAverage(int intAverage, int size)
```, which is why you will get a linking error about computeAverage.

Other errors may pop up later, but that is what I see from a quick look.

---

