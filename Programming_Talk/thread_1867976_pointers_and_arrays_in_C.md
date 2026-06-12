---
title: "pointers and arrays in C"
date: 2011-10-23
forum: Programming Talk
---

### Post by polaris90 on 2011-10-23
I need some help with pointers and arrays in C. I'm trying to make a function like follows

```

 void matrix_new(int **matrices, int *rows, int *cols){  //function to enter arrays
 20 
 21    *rows = &matrices[0][1];  //this will check the number of rows
 22    *cols = &matrices[0][2];  //this will check the number or columns
 23    int i, j;
 24     
 26    for(i = 0; i < *rows; i++){
 27       for(j = 0; j < *cols; j++){
 28         if(i==0 && j==0){
 29            scanf("%c", matrices[i][j]);
 30           }
 31         if(i==0 && j==1){
 32            scanf("%c", matrices[i][j]);
 33           }
 34         for(i=4; i<*rows; i++){
 35           scanf("%d", matrices[i][j]);
 36         /*now what*/
 37         
 38        }
 39      }

```
after i start scanning the items I want to check if the user enters another character using the isalpha() function. If user enters a character I want to scanf() that element as a character type and then just keep entering all elements as integers. Can anybody help me with this?

---

### Post by lisati on 2011-10-23
*Thread moved to **Programming Talk**.*

---

### Post by karlson on 2011-10-23
> **polaris90 said:**
> I need some help with pointers and arrays in C. I'm trying to make a function like follows

```

 void matrix_new(int **matrices, int *rows, int *cols){  //function to enter arrays
 20 
 21    *rows = &matrices[0][1];  //this will check the number of rows
 22    *cols = &matrices[0][2];  //this will check the number or columns
 23    int i, j;
 24     
 26    for(i = 0; i < *rows; i++){
 27       for(j = 0; j < *cols; j++){
 28         if(i==0 && j==0){
 29            scanf("%c", matrices[i][j]);
 30           }
 31         if(i==0 && j==1){
 32            scanf("%c", matrices[i][j]);
 33           }
 34         for(i=4; i<*rows; i++){
 35           scanf("%d", matrices[i][j]);
 36         /*now what*/
 37         
 38        }
 39      }

```
after i start scanning the items I want to check if the user enters another character using the isalpha() function. If user enters a character I want to scanf() that element as a character type and then just keep entering all elements as integers. Can anybody help me with this?

I am not sure I can follow what you're trying to do but there are a few things wrong
> 
```

 21    *rows = &matrices[0][1];  //this will check the number of rows
 22    *cols = &matrices[0][2];  //this will check the number or columns

```

This is wrong you are assigning an address of matrices[0][1] to the integer stored in address of pointed to by rows.  It should be
```

rows = &(matrices[0][1]);

```
or
```

*rows = matrices[0][1];

```
Also
```

scanf("%c", matrices[i][j]);

```
should be
```

scanf("%c", &(matrices[i][j]));

```

But in general why would you want to store char as integer in the same matrix as the data?

---

### Post by polaris90 on 2011-10-23
> 
But in general why would you want to store char as integer in the same matrix as the data?

Thanks for the reply and suggestions. The program is supposed supposed to ask for data(matrix or matrices) and do operations with it, like adding or multiplying. The problem is that I have to enter everything at once. Order to enter data is action(add or multiply), name of array, dimensions, and then elements in it, then second matrix(if it applies).

For example I want to add matrices A and B with dimensions 2x2, I have to enter them like this, +A221234B225678.
Yes, it's homework if you want to know. I just need help working with pointers since my professor barely explained on what they do and never went into pointer matrices. I read a book and got some information about it but never got anything on double pointer arrays. I googled it but couldn't find anything. 

I'm planing on having a variable to store the value of i+j when a character is encountered so I know where the next array starts. 
Then when I want let's say add, I can add the first matrix[i][j](in a for loop) plus matrix[i+variable][j+variable].
I'm no very experienced on programming so this the only thing I can think of right now. If anybody has a better suggestion, it's welcome.

---

### Post by gsmanners on 2011-10-23
I don't suppose the prof would let you hand in a C++ example. This stuff all reeks of needless complication (that you can just replace with standard libs or something).

---

### Post by polaris90 on 2011-10-23
> **gsmanners said:**
> I don't suppose the prof would let you hand in a C++ example. This stuff all reeks of needless complication (that you can just replace with standard libs or something).

I might be able to do it if I didn't have to enter the data all at once and I didn't have to use pointers. Of course it would be a lot of work and it would take more lines but it would be easier. C++, I haven't got into it but I know there are libraries that basically do stuff for you. This is a reason why I don't like C. 
My professor expects us to know everything. He teaches us how to solve for 'x' in x^x + 2x + 1, and he expects us to know how to integrate. 
Going back to my problem, can anybody tell me whether I'm going in the right direction concerning my code, if not can you give me some suggestions?
thanks

---

### Post by karlson on 2011-10-23
> **gsmanners said:**
> I don't suppose the prof would let you hand in a C++ example. This stuff all reeks of needless complication (that you can just replace with standard libs or something).


You're right but I think writing it yourself was sort of the point here.

---

### Post by karlson on 2011-10-23
> **polaris90 said:**
> I might be able to do it if I didn't have to enter the data all at once and I didn't have to use pointers. Of course it would be a lot of work and it would take more lines but it would be easier. C++, I haven't got into it but I know there are libraries that basically do stuff for you. This is a reason why I don't like C. 
My professor expects us to know everything. He teaches us how to solve for 'x' in x^x + 2x + 1, and he expects us to know how to integrate. 
Going back to my problem, can anybody tell me whether I'm going in the right direction concerning my code, if not can you give me some suggestions?
thanks

Have you considered entering op, matrix name, rows, columns, then allocate the matrix?  Then once you get all data enter matrix name, rows, columns, allocate memory and then perform the operation.

I think the point of this exercise was not only the use of pointers but also the understanding that memory is contiguous even for an N dimensional array.

---

### Post by lisati on 2011-10-23
> **karlson said:**
> You're right but I think writing it yourself was sort of the point here.

Agreed that writing it yourself can have some merit. The thing about homework assignments is that even though it's not always easy to see the point, what you learn by doing them isn't limited to the specifics of the particular problem.

---

### Post by polaris90 on 2011-10-23
> 
Have you considered entering op, matrix name, rows, columns, then allocate the matrix? Then once you get all data enter matrix name, rows, columns, allocate memory and then perform the operation.
if you mean like: asking for rows and columns > store them and then allocate the memory for the items to be entered.
yes I have, it would be a lot easier but that's not the point of the of the assignment. I have to be able to enter all the data at once. By the way I previously asked if my idea is right or not on how I'm trying to approach this problem and asked for ideas.
> 
after i start scanning the items I want to check if the user enters another character using the isalpha() function. If user enters a character I want to scanf() that element as a character type and then just keep entering all elements as integers. Can anybody help me with this?

---

### Post by gsmanners on 2011-10-24
> **polaris90 said:**
> By the way I previously asked if my idea is right or not on how I'm trying to approach this problem and asked for ideas.

Here's an idea: break down the assignment into parts. Think of it as three or four assignments in one. Code each, then merge them together. I think that'll go faster.

1) Use pointers
2) Pass pointers to a function
3) Make an input function
4) Store variables into an array
5) Store variables into a multidimensional array

You see? :D

---

