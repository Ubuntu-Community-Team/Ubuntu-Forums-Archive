---
title: "Array outside the Main()"
date: 2011-12-05
forum: Programming Talk
---

### Post by jacksonyoyo on 2011-12-05
Programming Language: C

Hi everyone. 
I am trying to create a 2D array outside the main loop, which will then be used in the main loop. 
so the program will run: main -> array function-> create array -> use the array created to do something. 

I know that when you try to pass an array to one function to another, you are actually passing a pointer. However, I know it in words, but not in practice#-o


```

void create_array(int size, int center)
{
int i, j;
float myarray[size][size];

    for(i=0; i<size; i++)
            {
                for(j=0; j<size; j++)
                {
                    if (i==center && j==center)
                    {
                        myarray[i][j] = 0;
                    }
                    else
                    {
                        disarray[i][j] = 1.41 ;
                    }
                }
            }
}


```In main: 

```

main()
{
int size = 7;
int center = 4;

/*call function and create myarray*/
myarray(size, center);

int i, j;
int times;


/*in loop, use the array*/

for(i = 0; i < size; ++i)
{
   for(j = 0; j < size; ++j)
   {
      times = 10*myarray[i][j];
   }
}

}


```So i guess, the major problem here is how to pass the created array to the main.

Thanks for all your time and help in advance.:P

---

### Post by dwhitney67 on 2011-12-05
The only parameters that can be passed to main() are the argc (count of command line parameters), argv (the list of command line args), and envp (environment settings).  Of course, the names of these variables is arbitrarily chosen, and they are not required at all... for example, in your program.

Thus the first thing I want to comment on is that main() should be declared to return an int.
```

**int **main(void)
{
   ...

   **return 0;**   /* or non-zero if error occurs */
}

```
As for the array, since it appears that you require it within two or more functions, you are going to have to declare it at the highest level (e.g. within main() or as a global variable (not recommended).

Consider this code:
```

int* create_array(const int size, const int center)
{
   /* create a linear array that will represent a two-dimensional array */
   int* array = malloc(sizeof(int) * (size * size));

   for (int row = 0; row < size; ++row)
   {
      for (int col = 0; col < size; ++col)
      {
         int value = 1.41;

         if (row == center && col == center)
         {
            value = 0;
         }

         array[row*size + col] = value;
      }
   }

   return array;
}

void destroy_array(int* array)
{
   free(array);
}

void printArray(const int* array, const int size)
{
   for (int row = 0; row < size; ++row)
   {
      for (int col = 0; col < size; ++col)
      {
         printf("array[%d][%d] = %d\n", row, col, array[row*size + col]);
      }
   }
}

int main(void)
{
   int size = 7;
   int center = 4;

   int* array = create_array(size, center);

   printArray(array, size);

   destroy_array(array);

   return 0;
}

```

---

### Post by lisati on 2011-12-05
Your options include:
[LIST]
[*]Create a global array (not a good idea, there's a risk of unintended consequences)
[*]Define the array within main() and pass its details to the function
[*]Create the array within the function, e.g. with malloc, and return its details to the calling function (take care to keep a note of the details so you don't end up with nasty stuff like memory leaks)
[/LIST]

Others more proficient with using C than myself will be able to help with the nuts and bolts of using these and any other methods that the community thinks of.

---

### Post by jacksonyoyo on 2011-12-05
Thank you so much for your help. 

The previously problem has been solved. However, I have came out with a new problem.

the created array, is passed to another function, and then to another where sorting will also take place. Explains below: 
 
In Main: 
```

int size = 7;
int center = 3;

/*var and mean calculated*/
int var = 10;
int mean = 5

/*a 1D array*/
int original[49]={----values----};

int* array = create_array(size, center);
int* second_array = function(array, mean, var);
int* repeat = repeat(second_array, original);

```
In function: calculation done to array, new 1D array is created known as "second_array"
```

int* function(const int* array, const int mean, const int var)
{
    int i, j, block;
    int index=0;
    int* second_array = malloc(sizeof(int) * (size * size));    

    for(i=0; i<size; i++)
       {
        for(j=0l j<size; j++)
        {
            block = (---calculation here---);
        
          if(block<=4)
         {
            second_array[index] = block;
            index++;
          }
         else
             {
                second_array[index] = 0;
                index++;
             }
    }    
    }
return second_array;
}

```
In last part, repeat(). 
A new array known as  "newsort" will be created, the size of array is based on the sum of  elements in "second_array" array created in function(). 
"newsort" stores the elements in array named "original", which is repeated according to the values in "second_array".

```

int* repeat(const int* second_array, const int* original)
{
    int s, total, i, j;

    for(s=0; s<49; s++)
    {    total += second_array[s];    }   //getting sum of elements in "second_array" 


    /* using total to allocate memory for new array "newsort" */

    int* newsort = malloc(sizeof(int) * total);
    int index;

    for(i=0; i<49; i++)                //loop for 49 blocks (7 by 7)
    {
        for(j=0; j<second_array[i]; j++)     
        {
            newsort[index] = original[i];
            index++;
             
             /* repeat values in array "original" , the number of times repeated */
                                /* is the value in "second_array" */
        }
    }

   
    /*qsort the "newsort" array (function not pasted here)*/

    qsort(newsort, index, sizeof(int), intcmp);

    int median = newsort[(index+1)/2];

    return XXXXXXXXXXX;
}


```here, 
what shall my function return to?
this median value will needs to be passed back to the main so for example:
```
int output[4][0] = median
```
I know this is so long....
thanks for reading up to here... 
I hope i explained it fine.... :S 
if not, please let me know.

Thank you so much for helping. :)

---

### Post by dwhitney67 on 2011-12-05
Please define better names other than function() and repeat().  These name do not offer any context as to the purpose for the function.

I would recommend that you refrain from putting too many operations into a single function.  If I had known earlier that you were going to need to create a second array, I would not have placed the code to initialize the array within the create_array() function.

Also, when passing an array to a function, always pass the size of the array as a parameter to that function.  This way, it makes it easier to modify the size of the array without having to worry as to whether you have a hard-coded constant somewhere else in the code.

Lastly, revisit the repeat() function.  You have some poor assumptions in there with respect to the number of elements that will be created for the 'newsort' array.  (Also, 'index' is uninitialized!)

---

### Post by jacksonyoyo on 2011-12-05
> **dwhitney67 said:**
> 
I would recommend that you refrain from putting too many operations into a single function.  If I had known earlier that you were going to need to create a second array, I would not have placed the code to initialize the array within the create_array() function.


thank you for your reply. 
I don't quite get what you mean by not initializing the array withing the create_array() function. 
:confused: so, what is your suggestion in doing a program like this? where creating arrays and keep using the arrays in arrays... 
ARRAYS EVERYWHERE! lol. 

Thanks once again. :)

---

