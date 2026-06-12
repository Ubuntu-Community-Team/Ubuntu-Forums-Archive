---
title: "C Programming - Idea for improvement"
date: 2015-01-25
forum: Programming Talk
---

### Post by flaymond on 2015-01-25
Hello, I just wanna ask for an opinion or idea to improve this simple code in C. I wanna it loop to the main again and again after the user got the answer.

```
  1 /* adds.c -- Calculated integers (addition)
  2  * Copyright 2015
  3                                             */
  4 
  5 
  6 #include <stdio.h>
  7 
  8 // Declaring prototype functions
  9 
 10 int add1(int, int);
 11 int add2(int, int, int);
 12 int add3(int, int, int, int);
 13 int add4(int, int, int, int, int);
 14 
 15 int main()
 16 {
 17     int response;
 18     int first;
 19     int second;
 20     int third;
 21     int fourth;
 22     int fifth;
 23    
 24 
 25 
 26     printf("\n\tAddition Program\n");
 27     printf("Please enter your selection: \n");
 28     printf("\n1\tAdd 1 number\n");
 29     printf("2\tAdd 2 numbers\n");
 30     printf("3\tAdd 3 numbers\n");
 31     printf("4\tAdd 4 numbers\n");
 32     printf("\n\nType 'q' to exit\n\n");
 33     scanf("%d", &response);
 34 
 35     switch (response) {
 36         case 1:
 37             printf("The answer is: %d \n",  add1(first, second));               // Use function add1 if user choose 1
 38             break;
 39         case 2:                                                                 // Use function add2 if user choose 2
 40             printf("The answer is: %d\n", add2(first, second, third));
 41             break;
 42         case 3:
 43             printf("The answer is: %d\n", add3(first, second, third, fourth));   // Use this function if user choose 3
 44             break;
 45         case 4:
 46             printf("The answer is: %d\n", add4(first, second, third, fourth, fifth));  // Use this function if user choose 4
 47             break;
 48         default:
 49             printf("Thanks for using our service! :)\n");                       // I don't know how to make this go to welcoming
 50                                                                                     // prompt or the top main function
 51 
 52          }
 53 
 54 }
 55 
 56 // Function definition
 57 int add1(int first, int second)
 58 {
 59 
 60     printf("Enter your first number\n");
 61     scanf("%d", &first);
 62 
 63     printf("Enter your second number\n");
 64     scanf("%d", &second);
 65 
 66     return first + second;
 67 }
 68 
 69 // Function definition
 70 int add2(int first, int second, int third)
 71 {
 72 
 73     printf("Enter your first number\n");
 74     scanf("%d", &first);
 75     printf("Enter your second number\n");
 76     scanf("%d", &third);
 77 
 78     return first + (second + third);
 79 }
 80 
 81 // Function Definition
 82 int add3(int first, int second, int third, int fourth)
 83 {
 84 
 85     printf("Please enter your first number\n");
 86     scanf("%d", &first);
 87     printf("Please enter your second number\n");
 88     scanf("%d", &second);
 89     printf("Please enter your third number\n");
 90     scanf("%d", &third);
 91     printf("Please enter your fourth number\n");
 92     scanf("%d", &fourth);
 93 
 94    return first + second + (third + fourth);
 95 }
 96 
 97 // Function definition
 98 
 99 int add4(int first, int second, int third, int fourth, int fifth)
100 {
101 
102     printf("Please enter your first number\n");
103     scanf("%d", &first);
104     printf("Please enter your second number\n");
105     scanf("%d", &second);
106     printf("Please enter your third number\n");
107     scanf("%d", &third);
108     printf("Please enter your fourth number\n");
109     scanf("%d", &fourth);
110     printf("Please enter your fifth number\n");
111     scanf("%d", &fifth);
112 
113     return first + (second + third) + (third + fourth);
114 }
115 






```

Thanks for your help! 

* I'm a beginner that passionate to learn and ask question :)

---

### Post by ofnuts on 2015-01-25
[LIST]
[*]The first..fifth variables defined in main shouldn't be there. They serve absolutely no purpose in main. As written your add..() functions don't need any parameters since they obtain the values directly from the user.
[*]So these variables should be declared as local variables in the add..() functions.
[*]And instead of having 5 distinct variables, use an array of 5 items
[*]Then you could really have one single add() function that takes the number of expected numbers as a parameter (basically, the code of add5() that skips the numbers above the passed limit).
[*]Then you can make that a loop instead if a linear execution
[*]And finally you find you don't need to ask the user first how many numbers he wants to add. You start with a sufficiently big array and keep looping getting numbers to add until the user answers with an empty line. Then you compute the sum.
[/LIST]

---

### Post by flaymond on 2015-01-27
Thanks! :D

---

