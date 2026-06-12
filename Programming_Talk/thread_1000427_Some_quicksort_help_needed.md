---
title: "Some quicksort help needed"
date: 2008-12-02
forum: Programming Talk
---

### Post by jjb123 on 2008-12-02
Hello,
I am trying to write a quick sort program in c++ because I am studying sorting algorithms. Below is the code I have managed to come up with so far, but when I run it the final outputted array seems to be just randomly re-arranged with no pattern that I can tell. I have stared at this for hours now and I am stuck. Any suggestions? Thanks. :D

```

#include<iostream>
#include<cstdlib>
using namespace std;

//Defines
#define ArraySize 250
#define RandomCap 1000

//Globals
int numbers[ArraySize];
int numbersRaw[ArraySize];

//Prototypes
void arrayPopulate();
void arrayOutput();
void quickSort(int startPosition, int endPosition);
void swap(int& a, int& b);
int splitArray(int pivot, int startPosition, int endPosition);

int main(){
    //Generate arrays  
    arrayPopulate();
    
    //Sort one of the arrays
    quickSort(0,ArraySize-1);
    
    //Print array
    arrayOutput();
    
    //Wait for return
    system("PAUSE");
    return 0;   
}

void swap(int& a, int& b){
	int temp;
	temp = a;
	a = b;
	b = temp;
}

void quickSort(int startPosition, int endPosition){
	//Assign the pivot point to the far left element
	int pivotPoint = numbers[startPosition];
	int splitPoint;
	
	//Make sure there is at least one element
	if (endPosition>startPosition){
		splitPoint = splitArray(pivotPoint,startPosition,endPosition);
		
		numbers[splitPoint] = pivotPoint;
		quickSort(startPosition,splitPoint-1); //Quick sort the first part
		quickSort(splitPoint+1,endPosition); //Quick sort the second part
	}
}

int splitArray(int pivot, int startPosition, int endPosition){
	int leftSide = startPosition;
	int rightSide = endPosition;
	
	while (leftSide < rightSide){
		while (pivot < numbers[rightSide] && rightSide > leftSide){ //Keep moving  until a smaller number is reached, or until we hit the end
			rightSide--;
		}
		swap(numbers[leftSide],numbers[rightSide]); //Swap so that the pivot is to the right of the small one.
		while (pivot >= numbers[rightSide] && leftSide < rightSide){ //Keep moving until a larger number is reached, or until we hit the end
			leftSide++;
		}
		swap(numbers[leftSide],numbers[rightSide]);
	}
	return leftSide;
}

void arrayPopulate()
{
	int generateCount;
	generateCount = 0;
	int tempRand;
	
	while(generateCount<=ArraySize-1){
		tempRand = (rand() % RandomCap) + 1;
		numbers[generateCount]=tempRand;
		numbersRaw[generateCount]=tempRand;
		generateCount++;
	}
}

void arrayOutput()
{
    int outputCount;
    outputCount = 0;
    
    while(outputCount<=ArraySize-1){
        cout<<outputCount<<":\t"<<numbersRaw[outputCount]<<"\t"<<numbers[outputCount]<<endl;
        outputCount++;                        
    }    
}

```

---

### Post by dwhitney67 on 2008-12-02
I forgot where I found this implementation, but maybe it will help you:
[php]
const int SMALL_ENOUGH = 15;


template <typename T>
void selectionsort(T& array, const int left, const int right)
{
  for (int i = left; i < right; ++i)
  {
    int min = i;

    for (int j = i+1; j <= right; ++j)
    {
      if (array[j] < array[min])
        min = j;
    }
    typename T::value_type temp = array[min];
    array[min] = array[i];
    array[i] = temp;
  }
}

template <typename T>
int partition(T& array, const int left, const int right)
{
  typename T::value_type val = array[left];
  int                    lm  = left-1;
  int                    rm  = right+1;

  for(;;)
  {
    do
    {
      rm--;
    } while (array[rm] > val);

    do
    {
      lm++;
    } while(array[lm] < val);

    if (lm < rm)
    {
      typename T::value_type temp = array[rm];
      array[rm] = array[lm];
      array[lm] = temp;
    }
    else
    {
      return rm;
    }
  }
}

template <typename T>
void quicksort(T& array, const int left, const int right)
{
  if (left < (right - SMALL_ENOUGH))
  {
    int split = partition(array, left, right);
    quicksort(array, left, split);
    quicksort(array, split+1, right);
  }
  else
  {
    selectionsort(array, left, right);
  }
}
[/php]

Btw, why are you using global variables?  Why not just declare your arrays in your main() function, then pass them to the appropriate function(s) to have manipulated.

---

### Post by mdurham on 2008-12-02
At a very quick glance, I noticed
> 		quickSort(startPosition,splitPoint-1); //Quick sort the first part
		quickSort(splitPoint+1,endPosition); //Quick sort the second part
 splitPoint-1 and splitPoint+1, what about the one between them?
Not sure if that is causing your problem though.
Cheers, Mike

---

### Post by jjb123 on 2008-12-03
The one between them is already in its proper place, that is the pivot from the last iteration and doesn't need to be sorted again.

I tried constraining the number of items to 1 to better see whats going on and this is what I got:
> 
0:    42    42
1:    468   170
2:    335   335
3:    501   501
4:    170   359
5:    725   479
6:    479   725
7:    359   465
8:    963   963
9:    465   468


It looks like it manages to get the first few steps right at least, then it just breaks down. I'm so confused.

---

### Post by mdurham on 2008-12-03
jjb123, I think I found your error now that I've has more than 10 secs to look at your prog. See below.
Should be leftSide not rightSide.

> 		while (pivot >= numbers[leftSide/*rightSide*/] && leftSide < rightSide)
		{ //Keep moving until a larger number is reached, or until we hit the end
			leftSide++;
		}


---

### Post by jjb123 on 2008-12-03
Wow, thanks that did the trick. It's always something simple :D Thanks again!

---

### Post by Mr.Macdonald on 2008-12-03
unless you are doing this to learn, use the C version of sort. It combines heap and quick to get the best possible, and will be faster than anything you could make (no offense, but its true).

But if you are doing it to learn then thats just fine, but for any application, use C's

---

### Post by jjb123 on 2008-12-03
Interesting, what is the name of it? Just C sort?

---

