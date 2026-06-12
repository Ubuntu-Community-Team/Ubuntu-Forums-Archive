---
title: "arraysort ascenting order"
date: 2012-09-27
forum: Programming Talk
---

### Post by zimmergage on 2012-09-27
I need it to sort an array a of size s in ascending order that return o if it is right and returns -1  if it is wrong starts with

int SortArray (int a[], int s);

---

### Post by nothingspecial on 2012-09-27
*Thread moved to **Programming Talk**.*

---

### Post by spjackson on 2012-09-27
Is this a homework assignment?

---

### Post by PaulM1985 on 2012-09-27
If this is not homework, you probably want qsort:

[http://www.cplusplus.com/reference/clibrary/cstdlib/qsort/](http://www.cplusplus.com/reference/clibrary/cstdlib/qsort/)

If it is, you need to think about this more yourself.

Paul

---

### Post by zimmergage on 2012-09-27
yes it is

---

### Post by spjackson on 2012-09-27
> **zimmergage said:**
> yes it is
See [Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")
> 
7. While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.

What have you done so far? What are you stuck with?

---

### Post by nothingspecial on 2012-09-27
> **zimmergage said:**
> yes it is

you'll only get hints then.

---

### Post by zimmergage on 2012-09-28
It compiles but it doesn't sort


int main(void){
int v;
int r;



int array[ SIZE ];
 

srand (time (NULL));
init_array(array,SIZE);

print_array(array, SIZE);

printf ("Enter value");
scanf ("%d",&v);
r=search_array(array, v, SIZE);
if(r==0)
    printf ("Value is found\n");
else
    printf("Value is not found\n");

r=sort_array(array, SIZE);
if(r==0)
    
    printf ("There are no errors\n");
else
    printf ("There are errors\n");
    
return 0;
}
int init_array( int a[], int s ){
    int i;
    for(i=0; i< s; i++){
        a[i] = RANDOM_NUM(1,100);
    }
    return 0;
    }

int print_array(int a[], int s){
int i;

       printf( "%s%13s\n", "Element", "Value" );
       for ( i = 0; i < s ;  i++ ) {
              printf( "%7d%13d\n", i, a[ i ] );
       } 
    return 0;
}

int search_array(int a[], int k, int s){

    int i;

    for(i=0; i < s; i++){
        if (a[i] == k)
            return 0;
    }
    
    return -1;
}
int sort_array(int a[], int s){
 int i;    
 int swp;
int n=i;
    do{
        swp = 0;
        for(i=0; i<s; i++)
            if(a[i-1]>a[i]){
                swap(a+i-1,a+i);
                swp=1;
        }
        s=s-1;
        } while
            (swp);
}


void Swap(int *a, int *b){
    int t;
    t = *a;
    *a = *b;
    *b = t;
}

---

### Post by Tony Flury on 2012-09-29
can you repost your code using code tags - so it preserves the formatting and makes it easier to read.

If your code is not working - have you tried printing out the array after each iteration of your sort ? You might get a clue what is going wrong ? Try printing out some of the other variables too.

Also I am surprised you aren't including "stdio" as a minimum - it is good practice since you are using printf and scanf

---

### Post by spjackson on 2012-09-29
I guess you are not allowed to use qsort. If you are allowed, then use it.

Perhaps it is a requirement to use random values, but while debugging, it makes sense to
use known values. Once it is working with known values, then use random ones.

How do you know it isn't working? What is happening? What isn't happening?

In sort_array,  look carefully at your for loop and the array indices. Do you spot anything amiss?

As a general rule, you will probably get better help if you post complete compilable code. e.g. What is SIZE, RANDOM_NUM?

---

### Post by zimmergage on 2012-09-29
I checked every time I written a new section the only thing that doesn't work is the sort_array, though it compiles.

#include<stdlib.h>
#include <stdio.h>
#include <time.h>

#define RANDOM_NUM( min, max ) ( min + (int)( (double)max * rand() / ( RAND_MAX + 1.0 ) ) )
#define SIZE 100
#define swap

void Init_Array( int a[], int s);
void PrintArray( int a[], int s);
int SearchArray( int a[], int k, int s);
int SortArray(int a[], int s);



int main(void){
int v;
int r;



int array[ SIZE ];
 

srand (time (NULL));
init_array(array,SIZE);

print_array(array, SIZE);

printf ("Enter value");
scanf ("%d",&v);
r=search_array(array, v, SIZE);
if(r==0)
    printf ("Value is found\n");
else
    printf("Value is not found\n");

r=sort_array(array, SIZE);
if(r==0)
    
    printf ("There are no errors\n");
else
    printf ("There are errors\n");
    
return 0;
}
/*
 *InitArray Inititialize n array a of size s with random
 *number form 1-100 inclusive
 */
int init_array( int a[], int s ){

    int i;
    for(i=0; i< s; i++){
        a[i] = RANDOM_NUM(1,100);
    }
    return 0;
}
/*
 *PrintArray: Prints an array a of size a to the screen
 */
int print_array(int a[], int s){
    int i;

       printf( "%s%13s\n", "Element", "Value" );
       for ( i = 0; i < s ;  i++ ) {
              printf( "%7d%13d\n", i, a[ i ] );
       } 
    return 0;
}
/*
 *SearchArray: Searches a key k in an array a of size s,
 *returns 0 if everything goes OK -1 if error
 */
int search_array(int a[], int k, int s){
 

    int i;

    for(i=0; i < s; i++){
        if (a[i] == k)
            return 0;
    }
    
    return -1;
}
/*
 *SortArray: Sorts an array a of ize  in ascending order
 *return 0 if everything goes OK-1 if error 
 */
int sort_array(int a[], int s){
    int i;    
     int swp;
     int n=i;
    do{
        swp = 0;
        for(i=0; i<s; i++)
            if(a[i-1]>a[i]){
                swap(a+i-1,a+i);
                swp=1;
        }
        s=s-1;
        } while
            (swp);
}


void Swap(int *a, int *b){
    int t;
    t = *a;
    *a = *b;
    *b = t;
}

---

### Post by spjackson on 2012-09-29
Here are some hints.

swap_array is supposed to return an int. How do you think it does that?

I wrote
> 
In sort_array,  look carefully at your for loop and the array indices. Do you spot anything amiss?
 I suggest that you do this.

Put a printf in your Swap function. When does it get called? Why is that?

---

