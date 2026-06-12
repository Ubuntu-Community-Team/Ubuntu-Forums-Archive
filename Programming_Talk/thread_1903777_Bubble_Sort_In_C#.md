---
title: "Bubble Sort In C#"
date: 2012-01-03
forum: Programming Talk
---

### Post by Tarast on 2012-01-03
Hi guys i am writing a program, well trying to, i am just learning to program. I am writing a console application that allows the user to input 10 numbers, and what i want is to sort them and use bubble sort.
 
here is my code:
 
[FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]using[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] System;
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]using[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] System.Collections.Generic;
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]using[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] System.Linq;
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]using[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] System.Text;
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]namespace[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] Task2
{
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]class[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Task2
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]{
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]static[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]void[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] Main([/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]string[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][] args)
{
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][] numbers = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][10];
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] index = 0;
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]string[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] enteredNumber = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]""[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// Read the numbers entered by the user
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]for[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] (index = 0; index < 10; index++)
{
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Console[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].Write([/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Enter Number:"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]);
enteredNumber = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Console[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].ReadLine();
numbers[index] = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].Parse(enteredNumber);
}
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// Sort the numbers
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]BubbleSort(numbers);
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// Display the sorted numbers
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Console[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].WriteLine([/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"The sorted numbers are:"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]);
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]foreach[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] ([/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] num [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]in[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] numbers)
{
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Console[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].Write(num + [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]" "[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]);
}
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Console[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].ReadLine(); [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// Pause
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]}
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// BubbleSort function
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]static[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]void[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] BubbleSort([/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][] numbers)
{
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]bool[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] swapped = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]true[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] count = 1;
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// Write the bubble sort code from the flowchart here!!
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]}
}
}
 
i cant figure out how to start, can anyone give me a suggestion please or a start up code or something? 
[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by KdotJ on 2012-01-03
Seems like homework? What is the flowchart it refers to?

---

### Post by PaulM1985 on 2012-01-03
> **KdotJ said:**
> Seems like homework? What is the flowchart it refers to?
+1

Also, as a tip for some of the code you have already written, look into the function TryParse.

Paul

---

### Post by Petrolea on 2012-01-03
If you have no idea what you're doing then this link is for you: [http://bit.ly/A1AzoR](http://bit.ly/A1AzoR)

But I recommend that you first learn how bubble sort works and then I think writing a bubble sort function shouldn't be a problem. It is actually really simple once you think about it.

---

### Post by KdotJ on 2012-01-03
Even a quick Google search gives you a huge amount of information. Wikipedia gives great explanation [here]("http://en.m.wikipedia.org/wiki/Bubble_sort"). However I suggest you seriously try to understand how it works before pasting in a bunch of code.

---

### Post by Barrucadu on 2012-01-03
You have the algorithm, you have the Internet available to address your C# queries, what more do you need? If you have specific questions after trying to implement it yourself, come back and ask.

---

### Post by mörgæs on 2012-01-03
> **Barrucadu said:**
> If you want to ask about something I posted, send a PM, as I don't watch many threads

Using 'advanced search' you can search for your own username. This will give you a date-sorted list of all threads where you have posted.

I can't tell whether the list is made with bubblesort, but I doubt it.

---

### Post by highspider on 2012-01-03
I had this working in c++ so I converted it C.

complied with 
gcc (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5

```

#define MAX 10       [COLOR=DarkGreen]//max numbers to input[/COLOR]
#include <stdio.h>  [COLOR=DarkGreen] //std input-output[/COLOR]

[COLOR=DarkGreen]//declare func[/COLOR]
void bubble_sort(int *thearray, int num_records);

[COLOR=DarkGreen]//MAIN[/COLOR]
int main(void) {
   int numbers[MAX]; [COLOR=DarkGreen]//array of numbers[/COLOR]
   int i = 0;        [COLOR=DarkGreen]//int i for loop[/COLOR]

  [COLOR=DarkGreen] //loop throught and get are numbers[/COLOR]
   for (i = 0; i < MAX; i++) {
      printf("%d) Give me a number: ", i+1);
      scanf ("%d", &numbers[i]);
   }

 [COLOR=DarkGreen]  //display unsorted numbers[/COLOR]
   for (i = 0; i < MAX; i++){
     printf("\n%d) unsorted: %d", i+1,numbers[i] );
   }
  [COLOR=DarkGreen] //cleaner display newlines[/COLOR]
   puts("\n\n");

  [COLOR=DarkGreen] //call bubble sort and sort numbers[/COLOR]
   bubble_sort(numbers, MAX);

   [COLOR=DarkGreen]//display sorted numbers[/COLOR]
   for (i = 0; i < MAX; i++){
      printf("\n%d) sorted: %d", i+1,numbers[i] );
   }
   [COLOR=DarkGreen] //cleaner display newlines[/COLOR]
   puts("\n\n");

   return 0;
}[COLOR=DarkGreen]//END MAIN[/COLOR]

[COLOR=DarkGreen]/************************************************************************
*NAME:    bubble_sort()
*PARAM:   (array) *thearray by ref and changes values,
*          passed num_record by value and doesn't change its value
*PURPOSE: Resort the array using a bubble sort algorithm
*RETURN:  n/a
*************************************************************************/[/COLOR]
void bubble_sort(int *thearray, int num_records){

    int i, l; [COLOR=DarkGreen]//for loop[/COLOR]
    int temp; [COLOR=DarkGreen]//temp place holder for 3-way swap
[/COLOR]
[COLOR=DarkGreen]    //begin bubble sort[/COLOR]
    for (l = 0; l < num_records; l++)
    {
        for (i = 0; i < num_records - 1; i++)
     [COLOR=DarkGreen]       //if thearray[i] is grater than next array sort it[/COLOR]
            if (thearray[i] > thearray[i + 1]) {
                 [COLOR=DarkGreen]//sort for numbers[/COLOR]
                 temp = thearray[i];
                 thearray[i] = thearray[i + 1];
                 thearray[i + 1] = temp;

             }[COLOR=DarkGreen]//end if swap[/COLOR]
    }[COLOR=DarkGreen]//end bubble sort[/COLOR]
}[COLOR=DarkGreen]//end func[/COLOR]

```

---

