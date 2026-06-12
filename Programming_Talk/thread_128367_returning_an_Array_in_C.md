---
title: "returning an Array in C"
date: 2006-02-11
forum: Programming Talk
---

### Post by diffuser78 on 2006-02-11
Hi all,

I am kinda rusty and was writing some C code where I was trying to return an array from a function.
```

int main(){
    int a[10];
    a = somefunc();
    return 0;
}

int *somefunc(){
    int b[];
// function code
    return b;
}

```

The error I am getting is incompatible types. Could somebody please point out the mistake. I am really rusty and spend good 2 hours but nothing clicked.

Thanks

---

### Post by SavageBeginner on 2006-02-11
I'd recommend sending the address of the array in main to somefunc and manipulating it that way.  The problem with what you're doing is you're trying to change the address of the array in main, but it is not a pointer.  This will cause a compile error, but changing it to a pointer won't work either because it will point to the address of the array in somefunc which won't exist (unless it's static) after somefunc has been called.  


I'd do it like this:```
void somefunc(int *b);

int main(void){
    int a[10];
    somefunc(a);
    return 0;
}

void somefunc(int *b){
// function code
}
```or this would work too, but it's probably not what you want:```
int *somefunc(void);

int main(void){
    int *a;
    a = somefunc();
    return 0;
}

int *somefunc(void){
    static int b[10];
// function code
    return b;
}
```

---

### Post by diffuser78 on 2006-02-11
I think I wanted the second approach but again I got errors.

I want a function to return an array. With or without pointers, it doesn't matter to me. Can you please show how to do it. Forget what I wrote in my previous post. I think I didn't write exactly what I wanted. Apologies for that.

Thanks for your time



> **SavageBeginner]I'd recommend sending the address of the array in main to somefunc and manipulating it that way.  The problem with what you're doing is you're trying to change the address of the array in main, but it is not a pointer.  This will cause a compile error, but changing it to a pointer won't work either because it will point to the address of the array in somefunc which won't exist (unless it's static) after somefunc has been called.  


I'd do it like this:```
void somefunc(int *b) said:**
> ;
    somefunc(a);
    return 0;
}

void somefunc(int *b){
// function code
}
```or this would work too, but it's probably not what you want:```
int *somefunc(void);

int main(void){
    int *a;
    a = somefunc();
    return 0;
}

int *somefunc(void){
    static int b[10];
// function code
    return b;
}
```

---

### Post by Viro on 2006-02-11
It would be helpful if you posted the *actual* errors that you are getting, and what code you've written that generated those errors.

---

### Post by krypto_wizard on 2006-02-11
sorry wrong post

---

### Post by kvorion on 2006-02-11
> **diffuser78]Hi all,

I am kinda rusty and was writing some C code where I was trying to return an array from a function.
```

int main(){
    **int a[10] said:**
> ;
// function code
    return b;
}

```

The error I am getting is incompatible types. 

Thanks


Even though you are trying to assign an int* to an int*, the problem here is that int a[] is not an lvalue. It is an array. Trying to do that will give you an error anywhere.

The problem with an array name like that is that you cannot modify its value like a normal pointer. That is why the error.
[what is an lvalue?]("http://builder.com.com/5100-6370_14-5383417.html")

One more dangerous thing you are doing in your program is that you are returning the address of a variable that is local to somefunc()

You never know what could become of that variable once the control is out of the function. This wont figure as an error but your compiler will flag a warning. So make the variable a static.

It is not really clear to me what you are trying to do here. To return an array simply return the address of the array, and that is what you are doing here. Just dont assign it to a non lvalue like an array name.

---

### Post by Buffalo Soldier on 2006-02-11
This is from my assignment in previous semester. The program function is to pick the maximum and minimum from 5 numbers. Hope this is what you're looking for. I'm not good at C... sorry if its not what u're after.

```
#include <stdio.h>

float *min_max(float []);

int main(void)
{
	int count;
	float *smallest, *largest, values[5];
	
	printf("Enter 5 values separated by whitespace.\n");
	for (count = 0; count < 5; ++count)
		scanf("%f", &(values[count]));
	
	smallest = min_max(values);
	largest = min_max(values)+1;
	
	printf("Minimum = %.2f, Maximum = %.2f\n", *smallest, *largest);
	
	return 0;
}

float *min_max(float values[])
{
	int count;
	float *pa, min, max, array[2];
	
	max = min = values[0];
    	for (count = 0; count < 5; ++count){
    		if (values[count] < min)
    			min = values[count];
    		if (values[count] > max)
        		max = values[count];
	}
	
	array[0] = min;
	array[1] = max;
    
	pa = &array[0];
	
	return pa;
}
```

---

### Post by Vegettex on 2006-02-11
Can't you do it like this? Didn't test it because i am not on a pc with gcc but should work probably (wrote it in notepad in like 5 minutes so errors could be included ;))

```
#include <stdio.h>

int foo(int *);

int main(int argc, char** argv)
{
        int array[10];
        int i, val = 0;
        int* p;
        p = &val;

        for(i = 0; i < 10; i++)
        {
                array[i] = foo(p);
                printf("nr %i is %i\n", i, array[i]);
        }

        return 0;
}

int foo(int* val)
{
        return (*val)++;
}

``` maybe it isn't working but i think you get my idea

---

### Post by Vegettex on 2006-02-11
[QUOTE=Buffalo Soldier]This is from my assignment in previous semester. The program function is to pick the maximum and minimum from 5 numbers. Hope this is what you're looking for. I'm not good at C... sorry if its not what u're after.

```
#include <stdio.h>

float *min_max(float []);
...
```[/QUOTE] Hmm I always used to think that passing an array in a function was really bad... (isn't that the reason they invented pointers, well probably it wasn't the main reason but ... ;) you know what i mean)

---

### Post by orlox on 2006-02-11
I don't trust much my capacity with C but, shouldnt you use malloc or something like that in your function? If my memory doesn't fail me, returning the address of a local variable produced segfaults whenever you tried to access it from outside the function...

---

### Post by engla on 2006-02-11
[QUOTE=orlox]I don't trust much my capacity with C but, shouldnt you use malloc or something like that in your function? If my memory doesn't fail me, returning the address of a local variable produced segfaults whenever you tried to access it from outside the function...[/QUOTE]
This is absolutely right, and sadly this thread is a bit off the track. [No offense, but we have to get this straight now].

When you do
```
int i =5;
```
or
```
int a[5];
```
Memory is allocated on the **stack**. This is not what we want, since when a context ends all the memory on the stack is deallocated. So in an example:
```

int function() {
  int a[5]; // we grab some local memory

  int i;
  for (i = 0; ...   // use the memory

  return result;
}    // the function ends, and all local references are now void!

```

To grab memory from the 'heap', the shared application memory space we have to use malloc. Malloc might seem obscure but it's absolutely vital for a C programmer. You grab memory and get a **pointer** to the memory. And you have to remember to deallocate it yourself!

```

int *function() {
   int *memory_pointer = malloc(5 * sizeof(int));  // Grab memory, 5 pieces of int
   if(memory_pointer != NULL) // Check that we got memory -- malloc can possibly fail
       return NULL;
  // Fill it, use it

  return memory_pointer;
}

int main(void) {
  int *p = function();
  
  // use p
  free(p);   //remember to free p when you are done!
}

```

---

### Post by celloandy on 2006-02-12
Using malloc and free will work, but declaring the array in main, passing a pointer to said array to the function, and manipulating it within the function is the better approach, in my opinion, as then you don't have to worry about remembering to free your array when you're done with it. I think this has already been proposed, above, but just in case:

```

#include <stdio.h>

int function(int *a) {
    a[1] = 2;
}

int main() {
    int b[10];
    function(b);
    printf("%d\n", b[1]);
}

``` 
Andrew

---

### Post by sathish j on 2010-08-26
not for
 
multidimensional 

arrays

---

### Post by sathish j on 2010-08-26
this is ur answer
:KS:KS:KS:KS:KS:KS:KS:KS> **sathish j said:**
> 
const int size=2;
int *input()
{
int a[size][size];
for(int i=0;i<size;i++)
cin>>a[i];
return a;
}
int main()
{
int *b;
b=input();
for(int i=0;i<size;i++)
cout<<*b(0+i);
}

---

### Post by dwhitney67 on 2010-08-26
> **sathish j said:**
> const int size=2;
int *input()
{
int a[size][size];
for(int i=0;i<size;i++)
cin>>a[i];
return a;
}
int main()
{
int *b;
b=input();
for(int i=0;i<size;i++)
cout<<*b(0+i);
}

Your first post, and it's wrong!  You should not be returning the address of a locally declared variable (or array), because upon returning from the function, it is no longer in scope.

This thread is old... very old... and if you had paid attention, it was concerning how to do manipulate an array in C... not C++.

Either case, I hope a mod can close the thread.

---

### Post by schauerlich on 2010-08-26
It burns us!

---

### Post by Pithikos on 2010-10-13
```

int function(int *a) {     a[1] = 2; }
```Just wanted to point out that the "function" is declared as int so there should be a "return" somewhere inside it. Either that or you could declare the function as: 
```
**void** function(int *a) {.. 
```

---

### Post by lisati on 2010-10-13
Time to let this thread rest in peace and sink into obscurity.

---

