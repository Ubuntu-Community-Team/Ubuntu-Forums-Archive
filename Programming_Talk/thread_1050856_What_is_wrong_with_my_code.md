---
title: "What is wrong with my code ?"
date: 2009-01-26
forum: Programming Talk
---

### Post by shindz on 2009-01-26
Hi all, I try to write a code which would allow memory strorage.
but after two step(in windows, when I'am at School) or 4 steps( in Linux, to house) the code crash. I figure not out what is wrong, I only know that the trouble come with the "realloc" line.
here is my code:
```
 /* myalloc. this code should allow space for a array of pointer* 

void allowspace(char ***ptr,int *maxwords)
{
     int i;
     /*for the first time we call malloc*/
     if(firsttime == 1)
        *p = (char **)real(sizeof(char *)*(*maxwords));
     // for the next time we call "realloc"
     else if(firsttime == 0)
         {
            *p = (char **)realloc(*p,sizeof(char *)*(*maxwords));

         }
     else if(firsttime == -1)
      {
          i = 0;
          while(*p[i] != NULL)
           {
                free(*p[i]);
                i++;
           }
      }
      
}

```

I know I could use this line too, but the trouble is the same.
```

void allowspace(char ***ptr, int *maxwords)
{
  *p = (char **)realloc(*p,sizeof(char *)*(*maxwords));
}

```

in the main , I have something like this to call "allowspace"
```

int main(void)
{
   char **ptrs;
   char line[132];
   int maxword = 0;
   int number_of_word = 0;
   while(true)
    {
      if(number_of_word +1 > maxwords)
        allowspace(&ptrs,&maxwords);
        gets(line);
        if(strlen(line)==0)
           break;
        ptrs[number_of_word] = (char *)malloc(sizeof(char)*132);
        strcpy(ptrs[number_of_word],line);
        number_of_word++;
    }
   allowspace(&ptrs,NULL); // freed of storage
   return 0;
}

```
could help me to figure out what is wrong with my code and could you give me any suggestions please ?
Thanks !

---

### Post by geirha on 2009-01-26
This looks like homework, which we can't help you with. I can give you a few hints though.

1. Use fgets instead of gets. gets doesn't check if the destination buffer has enough room, so you may get buffer overflows.

2. Use strncpy instead of strcpy for the same reason as above.

3. In your code above, what is the value of maxwords each time allowspace() is called...?

4. Don't complicate things by using char*** when you only need char**

5. Run your program through valgrind. Install [valgrind](apt:valgrind) from the repositories, then run your program with
```

$ gcc -Wall -o myprog myprog.c
$ valgrind ./myprog

```

It will tell you if your program has memory leaks and overflows.

---

### Post by shindz on 2009-01-26
you are right, this is a home work, but this code was not given. anyone have to write his own. I must obey something: the signature of the "allowspace". I know too that "gets" is dangerous, but as this is just a homework, it doesn't matter. I could have writte the same task another way, but I ought to pay attention about the prototype of : 
allowspace(char ***ptr,int *maxword);

I want to figure out why the code don't run. And you gave me hint:
I forget to write the line where we set the new value of *maxwords.
I don't want to complicate things, trust me, if I had to fix the goal, I would not use char *** where I only need char **.
I update the code with the forgotten line and get you in touch.

---

### Post by shindz on 2009-01-27
hi, i tried to update my code but I'm still having segmentation fault.I have one questions: how could we allocate memory for char **p? where must we pay attention to obtain the good result?

---

### Post by shindz on 2009-01-27
I missed something up: after a call to "realloc" ptrs has Null as adress and here crash my code.below is the place where I use "realloc"
```

ptrs = (char **)realloc(*p,sizeof(char *)*(*maxwords));
if(ptrs!= NULL)
     {
         puts("realloc exits with success.");
        *p = ptrs;
      }

```

---

### Post by dwhitney67 on 2009-01-27
A char** represents a pointer to an array of strings.  In your case, you have not defined the length of the array, much less the length of the strings pointed to by each element of the array.

Thus you have allowSpace(), which seems normal at first, but passing the pointer to maxwords seems quirky.  Consider the following as an alternative:
```

void allocSpace(char*** ptr, int numWords)
{
  ...
}

```

Anyhow, in allowSpace(), you need to carefully think about what is needed.  Your main() function takes a string as input from the user, and then you want to store it.  Obviously you would also like to keep track of the number of strings entered by the user.

Try to think of ptrs and number_of_word to be analogous to argv and argc.  argv is an array of pointers to strings -- exactly what you are looking to achieve.

So use malloc() and realloc() to allocate your array, then consider using strndup() to allocate the space for the string that you want your array element(s) to point to.  In lieu of strndup(), you can also use malloc() followed by a strncpy().

Anyhow, for allowSpace(), consider this:
```

if (numWords == 0)
  use malloc() to allocate ptr
else
  use realloc() to (re)allocate a new memory space for ptr

```
It is that simple; the code in the OP is almost correct.  Like I stated earlier, it would be easier if numWords was not passed as a pointer.  If you insist on passing it as a pointer, then specify the dereference character '*' above when accessing the value of numWords.

P.S.  geirha is correct ---- use fgets() to read in the user's input.  It's better to develop good habits now, rather than later.

---

### Post by mdurham on 2009-01-28
> A char** represents a pointer to an array of strings.

dwhitney67, Isn't a char** a pointer to a char pointer, and nothing to do with arrays or strings necessarily?
Cheers, Mike

---

### Post by Reiger on 2009-01-28
A pointer, almost by definition points to an item inside an array or linked list like structure. That's why pointer calculus is any good: you can, with one simple pointer reference pass an entire list of the actual items -- using calculus based on the underlying data structure to retrieve the others. After all, pointer calculus is just a higher-level abstraction from memory management (heap/stack manipulation) operations required to retrieve values.

A char* therefore (typically) points to a String (an array of chars); a char** points to an array of char*, hence an array of Strings.

---

### Post by mdurham on 2009-01-28
char A = 'a';

char *pA = &A;

char **ppA = &pA;

no string & no array.

---

### Post by dwhitney67 on 2009-01-28
> **mdurham said:**
> dwhitney67, Isn't a char** a pointer to a char pointer, and nothing to do with arrays or strings necessarily?
Cheers, Mike

Yes.  Sorry for the slip.

---

### Post by shindz on 2009-01-28
Anyhow, for allowSpace(), consider this:
```

if (numWords == 0)
  use malloc() to allocate ptr
else
  use realloc() to (re)allocate a new memory space for ptr

```
It is that simple; the code in the OP is almost correct.  Like I stated earlier, it would be easier if numWords was not passed as a pointer.  If you insist on passing it as a pointer, then specify the dereference character '*' above when accessing the value of numWords.

P.S.  geirha is correct ---- use fgets() to read in the user's input.  It's better to develop good habits now, rather than later.[/QUOTE]


I used this line on the top, but the trouble is always the same. I get a Null pointer with realloc

---

### Post by zacktu on 2009-01-28
Who initializes and modifies the value of firsttime?  It should be a static variable in allowspace that is given the initial value of 1 and not known to any other function.

---

### Post by shindz on 2009-01-28
firsttime is a global variable. i have forgotten to writte it here, the update of "firsttime" is done just after i get the line in the while loop, I do the same with maxwords.. so allowspace access the true value of "firsttime".

---

### Post by dwhitney67 on 2009-01-28
The variable 'firsttime' is not needed.  Since it is pointless to beat around the bush, here's the syntax that I would use for allocSpace():

```

void allocSpace(char*** ptr, const int numWords)
{
  if (numWords == 0)
  {
    *ptr = malloc(1 * sizeof(char*));
  }
  else
  {
    *ptr = realloc(*ptr, (numWords + 1) * sizeof(char*));
  }
}

int main()
{
  char** my_argv = 0;
  int    my_argc = 0;
  ...

  while (seekingUserInput)
  {
    // get input string from user
    ...

    // check if the user is done with inputting strings;
    // break from while-loop if so.
    ...

    allocSpace(&my_argv, my_argc);

    my_argv[my_argc] = strndup(...);   // this allocates memory
    ++my_argc;
  }

  ...

  for (int i = 0; i < my_argc; ++i)
  {
    free(my_argv[i]);
  }
  free(my_argv);
}

```

---

### Post by shindz on 2009-01-28
after any suggestions from you and a few try, I get the code run.
dwhitney67, you are right, "firsttime" is not too important, I just use it to allow or free storage. I have to free the strorage befor the end, so I set "firsttime" to "-1" and send it to allowspace. I'll try your code and save your idea. here is what I did and it make my code run.
I update "*mawords" in allowspace befor allowing storage wih realloc. it looks like this:
```

void myalloc(char ***p, int *maxwords)

{
     int i;

     char **ptrs = NULL; /* ptrs useless, I will remove it, unless you have suggestions */

     *maxwords++;

     if(erstemal == 1)

       {

          *p = (char **)malloc(sizeof(char *)*(*maxwords));



        }



     else if(erstemal != 1)

            {

                 ptrs = (char **)realloc(*p,sizeof(char *)*(*maxwords));

                 if(ptrs!= NULL)

                   {

		      puts("realloc exits with success.");
/* dont care   this line*/
		      *p = ptrs;

		    }



            }
    else if(erstemal == -1)
            {
                for(i = (*maxwords); i >= 0;i--)
                    free(*p[i]);
            }

}





```

---

### Post by dwhitney67 on 2009-01-28
A few comments about your function myalloc().

1)  You do not need to declare the 'ptrs' variable; just assign the return value from realloc() directly to the 'p' pointer.

2)  'maxwords' does not need to be passed by address; a local copy of the value is all that is needed.

3)  IMHO, myalloc() should only be used for allocating memory, not to free it.  Create a separate function for freeing the memory; for example myfree().

4)  Do not forget to free the memory pointed to by 'p' (the memory provided by malloc/realloc in myalloc()); currently you are only freeing the memory that each element of 'p' is pointing to, which presumably you allocated elsewhere.  Examine the code I posted earlier.

P.S.  Avoid global variables whenever possible.

P.S.S.  Use 'valgrind -v a.out' to see the memory leak in your current version of myalloc().

---

### Post by shindz on 2009-01-28
Hi, I update the code and it run.
here is how I write myfree():
```
void myfree(char **p, int maxwords)
{
    int i;
    for(i = maxwords; i > 0; i--)
        free(p[i]);
    free(p);
}

```

I understand what you about "*maxwords", but the task is to it with a pointer. thank for your advice about the global variable, but I realy don't understand is it a bad idea to work global. I don't mind it, I just want to know why. thanks

---

### Post by mdurham on 2009-01-29
> **shindz said:**
> Hi, I update the code and it run.
here is how I write myfree():
```
void myfree(char **p, int maxwords)
{
    int i;
    for(i = maxwords; i > 0; i--)
        free(p[i]);
    free(p);
}

```

I understand what you about "*maxwords", but the task is to it with a pointer. thank for your advice about the global variable, but I realy don't understand is it a bad idea to work global. I don't mind it, I just want to know why. thanks
shindz, without seeing the rest of the code it's a bit difficult to tell but... What about free(p[0]), it doesn't get freed because your for loop only works while i > 0, that should be i >= 0 (I think!) and maybe it should be for(i = maxwords - 1;...
Cheers, Mike

---

### Post by dwhitney67 on 2009-01-29
> **mdurham said:**
> shindz, without seeing the rest of the code it's a bit difficult to tell but... What about free(p[0]), it doesn't get freed because your for loop only works while i > 0, that should be i >= 0 (I think!) and maybe it should be for(i = maxwords - 1;...
Cheers, Mike

+1

```

for (i = maxwords - 1; i >= 0; --i)

```
or the more pleasant to read:
```

for (i = 0; i < maxwords; ++i)

```

---

### Post by dwhitney67 on 2009-01-29
> **shindz said:**
> Hi, I update the code and it run.
here is how I write myfree():
```
void myfree(char **p, int maxwords)
{
    int i;
    for(i = maxwords; i > 0; i--)
        free(p[i]);
    free(p);
}

```

I understand what you about "*maxwords", but the task is to it with a pointer. thank for your advice about the global variable, but I realy don't understand is it a bad idea to work global. I don't mind it, I just want to know why. thanks
Global variables are not necessarily "evil", but their use tends to be frowned upon by the today's s/w industry.

For small applications, less than 200-300 lines of code, I suppose a global variable or two doesn't matter.  But when the code starts creeping up in size and spans multiple modules, then it becomes a maintenance nightmare to determine which function is operating on the global value at any given time.  Usage of global variables can also lead to a poor design.

In your small application, the use of the global variable was simply unnecessary.  You had at your disposal two other alternatives, which IMO you chose the better of the two, and that is to define/implement the myfree() function.

The other option, which is not that terrific, yet still better than using a global variable, would be to augment myalloc() to accept a third parameter to indicate whether allocation should take place, or if de-allocation should be performed.

Employing the latter choice would make myalloc() perform two distinct operations, which strays away from the concept of keeping things simple, modularized and decoupled.

Anyhow, good luck with your programming class.  I hope you understand the exercise that you developed and understand some of the concepts presented.

---

### Post by Branimir on 2009-01-29
Global variables are ok. They just have to be accessed through
functions, not directly. This new naming for global variables
is called singleton pattern.

Greets, Branimir.

---

### Post by dwhitney67 on 2009-01-29
> **Branimir said:**
> Global variables are ok. They just have to be accessed through
functions, not directly. This new naming for global variables
is called singleton pattern.

Greets, Branimir.

The practice of "hiding" a global variable within a .c module, and providing accessor functions (which are defined in a header file, implemented in a .c file) to either set or get the value has been around for as long as I can remember.  It is nice to know that a name has been associated with the practice.

IMO the name "singleton" is appropriate, and the concept of such resembles the singleton design pattern often implemented in OOP applications.

---

### Post by shindz on 2009-01-29
> **dwhitney67 said:**
> +1

```

for (i = maxwords - 1; i >= 0; --i)

```
or the more pleasant to read:
```

for (i = 0; i < maxwords; ++i)

```

I thought that  p[0] and p were the same, that is why I decided to free from the end to the start ( p[maxwords -1] ---> p[1]). As I have just said, I thought p[0] and p were the same, so after freeing p[maxwords -1] ---> p[1] I free then p. But I was wrong, it seems like p # p[0].

now I see that I can  free from any direction without trouble, I mean from start ( p[0]) to end (p[maxwords -1]) oder in the reverse direction.

1 question: what is IMO and IMHO?

---

### Post by dwhitney67 on 2009-01-29
> **shindz said:**
> ...

1 question: what is IMO and IMHO?

IMO  = In My Opinion
IMHO = In My Honest (or Humble) Opinion

See other "internet slang" words/acronyms [here]("http://en.wiktionary.org/wiki/Appendix:Internet_slang").

---

### Post by nvteighen on 2009-01-30
> **dwhitney67 said:**
> A few comments about your function myalloc().

1)  You do not need to declare the 'ptrs' variable; just assign the return value from realloc() directly to the 'p' pointer.


Isn't that a bit risky? What if realloc() fails for some reason and returns NULL or a random pointer (which can happen, look at the man page)? Then you get a memory leak, don't you?

---

### Post by shindz on 2009-01-30
> **nvteighen said:**
> Isn't that a bit risky? What if realloc() fails for some reason and returns NULL or a random pointer (which can happen, look at the man page)? Then you get a memory leak, don't you?

I thougth so too. i saw that "realloc" may return a NULL pointer so I'd better try with **ptrs and then after checking if the pointer return by realloc is valid, I put his adress  in p.

---

### Post by dwhitney67 on 2009-01-30
You guys are optimists, in the sense that you think your system will move along just nicely if it is out of memory.  I on the other hand, feel that if the system cannot honor a request for memory, then there's no point attempting to recover, and of course, a memory leak, if any, will be cleared up when the application terminates.

---

### Post by nvteighen on 2009-01-31
> **dwhitney67 said:**
> You guys are optimists, in the sense that you think your system will move along just nicely if it is out of memory.  I on the other hand, feel that if the system cannot honor a request for memory, then there's no point attempting to recover, and of course, a memory leak, if any, will be cleared up when the application terminates.
OK, I see your point... But you never know what will happen when the system runs out of memory. For example, in GNU/Linux, you don't know if the OOM-killer will kill your application or another one.

Or am I mistaken?

---

