---
title: "Why this output?"
date: 2012-09-05
forum: Programming Talk
---

### Post by DiegoTc on 2012-09-05
Hi
I have the fallowing c code

```

int *s(int c);

void main()
{
	int y = 10;
	int *p = s(y);
        printf("%d\n",*p); //Why it prints 10?
        
	int temp = 11;
	int *lol = 12;

	printf("%d\n",*p);//Why it prints 10?
}

int *s(int c)
{
   int a = c;
   printf("%d\n",&a);//Here it prints the memory address of a
   return &a;  //Here it returns 10. Why?
}


```

I will like to know why it prints 10 on the main, but not in the funcion?

---

### Post by GeneralZod on 2012-09-05
Hint - compile your code with -Wall (as you should be doing, anyway ;))

---

### Post by MG&amp;TL on 2012-09-05
```

//Function returning a pointer to an int. (Memory address).
int *s(int c);

void main()
{
    int y = 10;
    //pointer to an int (memory address), which has a value of ten.
    int *p = s(y);
    //print the data the pointer points to, in this case a value of 10.
    //If you used "p" rather than "*p", you'd get a memory address
        printf("%d\n",*p); //Why it prints 10?
        
    //irrelevant?
    int temp = 11;
    int *lol = 12;
    //Memory address hasn't changed, still points to an int with a value of 10.
    printf("%d\n",*p);//Why it prints 10?
}

//Function returning a pointer to an int.
int *s(int c)
{
   int a = c;
   //You're finding the memory address of a. What did you expect it to print?
   printf("%d\n",&a);//Here it prints the memory address of a

   //It doesn't. It returns a pointer to an int of value 10.
  //This is a bad idea, btw. See: http://stackoverflow.com/questions/8184315/why-does-gcc-throw-a-warning-when-returning-a-pointer-to-a-local-variable-and-no
   return &a;  //Here it returns 10. Why?
}


```


I've commented your code. I think you probably need to read up on pointers a little more.

No doubt the REAL programmers here will correct me further, but oh well. :)

---

### Post by DiegoTc on 2012-09-05
I know it was going to print some strange number in the function s 

But my question is wy it returns 10.
I know it related how c puts the values in the data segment,but still don't know why it returns 10.

---

### Post by Tony Flury on 2012-09-05
> **DiegoTc said:**
> I know it was going to print some strange number in the function s 

But my question is wy it returns 10.
I know it related how c puts the values in the data segment,but still don't know why it returns 10.

It doesn't return 10, it returns the address of where a was stored when function s was executing (which MG&TL has already pointed out is technically invalid address the moment the function s exits - i.e. immediately after the return statement).

Your main code then stores the return value in p (which is a pointer to int), and then prints the contents of what p points to - your code prints "*p" which means - use the value stored in p as an address and use the value stored there.

Since (luckily for you) the value you stored in p still points to the value 10 on the stack (mainly because you haven't called anything else in the mean time, your printf outputs that value.

if you did this : 
```

int *p = s(y);
printf("%d\n",p); 
printf("%d\n", *p);

```
Then your first printf would output the same "strange number" you got from inside s, and the 2nd printf may print 10, or some other value as the first call to printf has probably stomped over the stack frame, or the world could end (the behaviour is undefined after all - I would bet on the 2nd option though) which actually would be a good lesson as to why you should never return the address of a local variable.

---

### Post by DiegoTc on 2012-09-05
> **Tony Flury said:**
>  it returns the address of where a was stored when function s was executing (which MG&TL has already pointed out is technically invalid address the moment the function s exits - i.e. immediately after the return statement).



Thanks that's the explanation I was looking it has sense. How the values are put in the data segment(Event make the drawing :P)

---

