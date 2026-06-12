---
title: "C++ Bubble sort / Selection Sort Help"
date: 2008-12-02
forum: Programming Talk
---

### Post by agiles2303 on 2008-12-02
I'll start off by saying I'm new to the forums and new to C++.  And to be honest the question I am asking is related to a homework problem.  I have a program that does the job it is supposed to however my professor added a twist to it, and no matter where I put my print statements I can't get the right answer.

The prompt is as follows:
"Use two identical 20 integer arrays, call a function that uses a bubble sort algorithm in ascending order and count the number exchanges and print that value.Do the same for the selection sort algorithm"

Like I said I was able to get both sorts to function properly, my issue is I don't know how to display the number of exchanges are made before the sort is complete.  Here is my code, I greatly appreciate any advice:

```

//Chapter 8 Problem 9
//Sorting Benchmark

//Use two identical 20 integer arrays
//Call a function that uses a bubble sort algorithm in ascending order
//Count the number exchanges
//Do the same for the selection sort algorithm

#include <iostream>
using namespace std;

//Function Prototypes
int bubbleSort(int [], int);
void showBubble(int [], int);
void selectionSort(int [], int);
void showSelection(int [], int);

int main()
{
    //Array of 20 unsorted values
    int bubble[20] = {2, 11, 15, 13, 55, 16, 22, 78, 19, 31, 45, 49, 38, 25, 3, 5, 17, 24, 61, 82};
    int selection[20] = {2, 11, 15, 13, 55, 16, 22, 78, 19, 31, 45, 49, 38, 25, 3, 5, 17, 24, 61, 82};
    int results;
    
    //Display Bubble Array    
    cout << "***Bubble Sort***" << endl;
    cout << "Original Unsorted Array:" << endl;
    showBubble(bubble, 20);
    cout << endl;
    
    //Call Bubble Sort Algorithm
    bubbleSort(bubble, 20);
    
    //Display Bubble Sorted Array
    cout << "Sorted Array:" << endl; 
    showBubble(bubble, 20);
    
    //Display Selection Array
    cout << "***Selection Sort***" << endl;
    cout << "Original Unsorted Array:" << endl;
    showSelection(selection, 20);
    cout << endl;
    
    //Call Select Sort Algorithm
    selectionSort(selection, 20);
    
    //Display Selection Sorted Array
    cout << "Sorted Array" << endl;
    showSelection(selection, 20);
    cout << endl;
   

    system("PAUSE");
    return 0;
}

int bubbleSort(int array[], int size)
{
     bool swap;
     int num;
     
     do
     {
         swap = false;
         for(int count = 0; count < (size - 1); count++)
         {
             if (array[count] > array [count + 1])
             {
                              num = array[count];
                              array[count] = array[count + 1];
                              array[count + 1] = num;
                              swap = true;
                              count++;
                                                           
             }
             return count++;
         }
     } while (swap);  
}

void showBubble(int array[], int size)
{
     for(int count = 0; count < size; count++)
     cout << array[count] << " ";
     cout << endl;
}

void selectionSort(int array[], int size)
{
     int startScan, minIndex, minValue;
     
     for (startScan = 0; startScan < (size - 1); startScan++)
     {
         minIndex = startScan;
         minValue = array[startScan];
         for(int index = startScan + 1; index < size; index++)
         {
                 if(array[index] < minValue)
                 {
                                 minValue = array[index];
                                 minIndex = index;
                 }
         }
         array[minIndex] = array[startScan];
         array[startScan] = minValue;
     }
}

void showSelection(int array[], int size)
{
     for (int count = 0; count < size; count++)
     cout << array[count] << " ";
     cout << endl;
}

```

---

### Post by agiles2303 on 2008-12-02
Since I failed to do this before the code should be easier to read with some tags, sorry.

```


//Chapter 8 Problem 9
//Sorting Benchmark

//Use two identical 20 integer arrays
//Call a function that uses a bubble sort algorithm in ascending order
//Count the number exchanges
//Do the same for the selection sort algorithm

#include <iostream>
using namespace std;

//Function Prototypes
int bubbleSort(int [], int);
void showBubble(int [], int);
void selectionSort(int [], int);
void showSelection(int [], int);

int main()
{
    //Array of 20 unsorted values
    int bubble[20] = {2, 11, 15, 13, 55, 16, 22, 78, 19, 31, 45, 49, 38, 25, 3, 5, 17, 24, 61, 82};
    int selection[20] = {2, 11, 15, 13, 55, 16, 22, 78, 19, 31, 45, 49, 38, 25, 3, 5, 17, 24, 61, 82};
    int results;
    
    //Display Bubble Array    
    cout << "***Bubble Sort***" << endl;
    cout << "Original Unsorted Array:" << endl;
    showBubble(bubble, 20);
    cout << endl;
    
    //Call Bubble Sort Algorithm
    bubbleSort(bubble, 20);
    
    //Display Bubble Sorted Array
    cout << "Sorted Array:" << endl; 
    showBubble(bubble, 20);
    
    //Display Selection Array
    cout << "***Selection Sort***" << endl;
    cout << "Original Unsorted Array:" << endl;
    showSelection(selection, 20);
    cout << endl;
    
    //Call Select Sort Algorithm
    selectionSort(selection, 20);
    
    //Display Selection Sorted Array
    cout << "Sorted Array" << endl;
    showSelection(selection, 20);
    cout << endl;
   

    system("PAUSE");
    return 0;
}

int bubbleSort(int array[], int size)
{
     bool swap;
     int num;
     
     do
     {
         swap = false;
         for(int count = 0; count < (size - 1); count++)
         {
             if (array[count] > array [count + 1])
             {
                              num = array[count];
                              array[count] = array[count + 1];
                              array[count + 1] = num;
                              swap = true;
                              count++;
                                                           
             }
             return count++;
         }
     } while (swap);  
}

void showBubble(int array[], int size)
{
     for(int count = 0; count < size; count++)
     cout << array[count] << " ";
     cout << endl;
}

void selectionSort(int array[], int size)
{
     int startScan, minIndex, minValue;
     
     for (startScan = 0; startScan < (size - 1); startScan++)
     {
         minIndex = startScan;
         minValue = array[startScan];
         for(int index = startScan + 1; index < size; index++)
         {
                 if(array[index] < minValue)
                 {
                                 minValue = array[index];
                                 minIndex = index;
                 }
         }
         array[minIndex] = array[startScan];
         array[startScan] = minValue;
     }
}

void showSelection(int array[], int size)
{
     for (int count = 0; count < size; count++)
     cout << array[count] << " ";
     cout << endl;
}



```

---

### Post by Paul Miller on 2008-12-02
What you need to do is modify your sort functions to increment a counter every time they actually swap a value.  Then, have them return that value when finished.

---

### Post by agiles2303 on 2008-12-02
The thing is I thought I did that, by adding the count++, and return count++, but it doesn't return a value.

---

### Post by dwhitney67 on 2008-12-02
For now I would forget about the number of swaps.  Your BubbleSort() algorithm is incorrect, thus you should focus your attention there.
-----------
Edit:  Actually, your algorithm does look correct; initially I was thrown off by the do-while; normally I see a while-do.  Anyhow, you are returning the count in the incorrect place.  It should be returned after the do-while ends.
-----------

I've also seen a different implementation of the SelectionSort() than you have, yet yours seems close enough, thus I'll assume it is correct.  The only thing that I question is your setting of the minValue when one value is less than the other.
[php]
                 if (array[index] < minValue)
                 {
                   minValue = array[index];   // <--- Is this right??  It probably is, since it makes sense.
                   minIndex = index;
                 }
[/php]

---

