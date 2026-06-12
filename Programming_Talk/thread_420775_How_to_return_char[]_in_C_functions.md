---
title: "How to return char[] in C functions?"
date: 2007-04-23
forum: Programming Talk
---

### Post by phossal on 2007-04-23
What is the best way to return a character array from a function using C?

---

### Post by thelinuxguy on 2007-04-23
Do you really want to **return** an array. Since arrays are returned by reference, when you return an array you are only returning a reference to it. If the array was declared within the function then its memory would have been released by the time you use its reference outside the function.

---

### Post by slavik on 2007-04-24
allocate the array on the heap and return a pointer to it. you do lose the size of the array, so what you can do is return a struct with an array pointer and the size of an array.

---

### Post by Tuna-Fish on 2007-04-24
Why do you even need the size of a string anywhere, you can just assume it's null-terminated, right?

---

### Post by phossal on 2007-04-24
> **Tuna-Fish said:**
> Why do you even need the size of a string anywhere, you can just assume it's null-terminated, right?

Can you?

---

### Post by rjack on 2007-04-24
> **slavik said:**
> allocate the array on the heap and return a pointer to it. you do lose the size of the array, so what you can do is return a struct with an array pointer and the size of an array.

A simpler solution is to the pass a size_t argument by reference (i.e. its pointer) so that the function can fill its value with the size of the string.

Example:

```
char*
new_string (&ret_size) {
   size_t *size = do_some_computation();
   char *string = malloc (size * sizeof (char));
   /* omitting malloc check */
   *ret_size = size;
   return string;
}
```

This approach is good if there are no ways to compute the size of the new string outside the functions. Otherwise, just pass the desired size as an argument by value and let the caller decide.

> **phossal said:**
> Can you?

No he can't.

He can write a function that null-terminates the allocated string, but it has to be done explicity.

---

### Post by hod139 on 2007-04-24
I'm not sure what you are trying to do, but you don't need to have a method return the char array.  You can pass a pointer to the char*, and manipulate the parameter.  You can then return an error state.  For a similar example allocating a new char array:

```
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

// Assumes string has not been previously malloced
// important, requires char** not char*
int new_string(char** string, int size)
{
  (*string) = (char *) malloc (size * sizeof (char));
  
  if( (*string) == NULL ) 
    return 0; // malloc failed, return false
  
  return 1; // success, return true
}

// Here it is ok to pass the char array by value
int make_random_string(char* string, int size)
{
  int i;
  for (i=0; i < size; ++i)
     string[i]=rand()%26+'a';
   string[size-1]='\0'; // always null terminate a string

  return 1; //success, return true
}

// Main entry point
int main(void)
{
   int n = 5;  // default size of string to malloc
   char *string; // the string to create
   
   srand ( time(NULL) ); // seed the rng

   // Allocate a new string 
   if( !new_string(&string, n) )
   {
      printf("Failed to allocate the string\n");
      exit(1);
   }

   // Make a random string
   if( !make_random_string(string, n) )
   {
      printf("Failed to make a random string\n");
      exit(1);
   }
   
   // print the string
   printf ("Random string: %s\n",string);
   
   free (string); // memory management

   return 0;
}



```It is very important to pass a pointer to the char* (char **) and not simply the char*.  This is because passing a char* alone is actually passing a copy (pass by value) of the pointer, and you do not want to allocate memory for the copy.

---

