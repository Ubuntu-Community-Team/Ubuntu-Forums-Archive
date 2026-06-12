---
title: "How to code this logic in bulletproof way in C"
date: 2009-07-15
forum: Programming Talk
---

### Post by codingfreak on 2009-07-15
Hi,

I am trying out the following code in C

```
#include <stdio.h>
int main(){

    int count = 1;
    int m1, temp;
    while(count)
    {
        printf("\nenter for m1 = ");
        scanf("%d",&m1);

        if (count==10)
        exit(0);

        count++;
    }
    return 0;
}    
```Instead of giving an integer if I try to give a character or any junk value above code simply loops for 10times and exits.

Can anyone help me to fix this issue ???

---

### Post by SledgeHammer_999 on 2009-07-15
while() takes a bool type variable. eg true or false. Count is an integer. If count==0 then while will exit. If count>0 then the loop will continue. The same goes for count as a char.

---

### Post by codingfreak on 2009-07-15
> **SledgeHammer_999 said:**
> while() takes a bool type variable. eg true or false. Count is an integer. If count==0 then while will exit. If count>0 then the loop will continue. The same goes for count as a char.

The problem is not with count value .... but with scanf I guess ...

If I give only numbers whenever scanf() asks me the above code works fine. If I give an alphabet for scanf then it simply keeps on looping ......

---

### Post by Npl on 2009-07-15
have you actually read the docs about scanf ?
it will return the number or characters it correctly parsed, if it expects an integer and it encounters a character instead it will return 0 (and as the input-stream doesnt change it will do the same thing the next time you call it). if it found an integer the return value will be > 0. So you need to do a check for scanf() <= 0 and then handle the error. 

I dont know how you easily and reliably can skip over the unwanted input though

---

### Post by Thesuperchang on 2009-07-15
For when invalid input is entered into a scanf() call.
[PHP]void ClearSTDIN(void) {
	scanf("%*[^\n]");
	scanf("%*1[\n]");
}[/PHP]

---

### Post by MindSz on 2009-07-15
Or you can try getting a char every time and then see if it's of integer value or not (integers range from 0x30 to 0x39 in the ASCII table) and then decide what you want to do with it.

---

### Post by c0mput3r_n3rD on 2009-07-15
> **MindSz said:**
> Or you can try getting a char every time and then see if it's of integer value or not (integers range from 0x30 to 0x39 in the ASCII table) and then decide what you want to do with it.

You should get into habit of making conditional statements to insure the input is correct.  You don't want the user putting in a wrong value and having the program crash.

---

### Post by codingfreak on 2009-07-15
> **MindSz said:**
> Or you can try getting a char every time and then see if it's of integer value or not (integers range from 0x30 to 0x39 in the ASCII table) and then decide what you want to do with it.

If I execute the above C code I get the following result
```
$ ./a.out 

enter for m1 = 1

enter for m1 = 2

enter for m1 = a

enter for m1 = 
enter for m1 = 
enter for m1 = 
enter for m1 = 
enter for m1 = 
enter for m1 = 
enter for m1 = $
```If I give integer values then everything goes fine it loops back and waits for next value. If I give character 'a' it simply don't wait for the input from the user and just loops remaining 7 times. I am maintaining count of 10 if not it simply loops infinitely. 

So can you modify the C code so that it waits for the user input even if I give junk content.

---

### Post by soltanis on 2009-07-15
scanf stops when it hits an unexpected input character, and I think it's left on the buffer. So it keeps looping, looking for a digit, and the 'a' simply sits there in the input, so it stops scanning and continues the loop.

You should try using this:

```

#include <stdlib.h>

char buf[50], *end;

fgets(buf, 50, stdin);
m1 = strtol(buf, &end, 0);
if (**end != '\0') {
        /* you entered something invalid. */
}

```

Instead of your scanf function.

---

### Post by nmccrina on 2009-07-16
```
#include <stdio.h>
int main(){

    int count = 1;
    int m1, temp;
    while(count)
    {
        printf("\nenter for m1 = ");
        if (scanf("%d",&m1))
        {        
            if (count==10)
            exit(0);

            count++;
        }
        else
        {
            getchar();
        }
    }
    return 0;
}
```

This makes sure you get 10 different integer values for m1; that is, it discards non integer inputs like they didn't even happen.

---

### Post by lisati on 2009-07-16
There is often more than one way to solve a problem.

What about this as an alternative?

```

#include <stdio.h>
int main(void)
    {
    int count = 1;
    int m1, temp;
    while(count<10)
        {
        printf("\nenter for m1 = ");
        if (scanf("%d",&m1))
        {        
           count++;
        }
        else
        {
            getchar();
        }
    }
    return 0;
}

```
It has the advantage of being slightly shorter, and anyone reading the condition will have a better idea of what ends the loop.

---

### Post by dwhitney67 on 2009-07-16
I think the main issue that the OP was attempting to resolve was how to handle unwanted (and hence, erroneous) input.

The "count" he used was merely to stop a runaway program from indefinitely prompting him for input.  As it has been discussed, scanf() can be used to determine if a valid value has been read.

Here's a simple program that ensures that an integer is read from the user...
```

#include <stdio.h>

int main()
{
  int value = 0;

  while (1)
  {
     printf("\nEnter a value: ");

     if (scanf("%d", &value)) break;

     // error if here
     printf("Error!  Try again...\n");
     while (getchar() != '\n');
  }

  printf("\nThe value entered is: %d\n", value);
  return 0;
}

```

The program above will handle situations when the user enters a single character, or even a string of characters.  If the user happens to enter "10 bottles of beer", well, then the number 10 is used.

---

### Post by lisati on 2009-07-16
> **dwhitney67 said:**
> I think the main issue that the OP was attempting to resolve was how to handle unwanted (and hence, erroneous) input.

The "count" he used was merely to stop a runaway program from indefinitely prompting him for input.  As it has been discussed, scanf() can be used to determine if a valid value has been read.

Here's a simple program that ensures that an integer is read from the user...


True!
I put in my contribution more for stylistic reasons than helping with the input of numbers......

---

### Post by codingfreak on 2009-07-17
> **nmccrina said:**
> ```
#include <stdio.h>
int main(){

    int count = 1;
    int m1, temp;
    while(count)
    {
        printf("\nenter for m1 = ");
        if (scanf("%d",&m1))
        {        
            if (count==10)
            exit(0);

            count++;
        }
        else
        {
            getchar();
        }
    }
    return 0;
}
```This makes sure you get 10 different integer values for m1; that is, it discards non integer inputs like they didn't even happen.

If I execute the above code snippet giving junk inputs then it will behave as shown below.

```
$ ./a.out 

enter for m1 = asdf

enter for m1 = 
enter for m1 = 
enter for m1 = 
enter for m1 = a

enter for m1 = asdfghjk

enter for m1 = 
enter for m1 = 
enter for m1 = 
enter for m1 = 
enter for m1 = 
enter for m1 = 
enter for m1 = 
enter for m1 = 
```

---

### Post by Mirge on 2009-07-17
> **soltanis said:**
> scanf stops when it hits an unexpected input character, and I think it's left on the buffer. So it keeps looping, looking for a digit, and the 'a' simply sits there in the input, so it stops scanning and continues the loop.

You should try using this:

```

#include <stdlib.h>

char **buf[50]**, *end;

**fgets(buf, 50, stdin)**;
m1 = strtol(buf, &end, 0);
if (**end != '\0') {
        /* you entered something invalid. */
}

```Instead of your scanf function.

Should be char buf[51] shouldn't it? or I guess fgets(buf, 49, stdin); ?

---

### Post by dwhitney67 on 2009-07-17
> **Mirge said:**
> Should be char buf[51] shouldn't it? or I guess fgets(buf, 49, stdin); ?

It should be fgets(buf, sizeof(buf), stdin).  Avoid hard-coding numbers whenever possible.

Anyhow, has the OP tried my solution (posted earlier)?  It seems he picked up a buggy solution from someone else, then just gave up.

---

### Post by Mirge on 2009-07-17
> **dwhitney67 said:**
> It should be fgets(buf, sizeof(buf), stdin).  Avoid hard-coding numbers whenever possible.

Anyhow, has the OP tried my solution (posted earlier)?  It seems he picked up a buggy solution from someone else, then just gave up.

lol @ second part.

It's been a while since I've used C... but wouldn't you need maybe sizeof(buf)+1 to store the terminating NULL?

---

### Post by stevescripts on 2009-07-17
My $.02 germaine to the thread - Validating user input is important to learn, and not always simple, after all, users *WILL* be users ... ;)

Steve
(who also wonders if the OP tried dwhitey67's solution? ...)

---

### Post by dwhitney67 on 2009-07-17
> **Mirge said:**
> lol @ second part.

It's been a while since I've used C... but wouldn't you need maybe sizeof(buf)+1 to store the terminating NULL?

No, the man-page for fgets() indicates that at most one less than the number of bytes specified is read.  So if you specify 50, only 49 bytes are read, unless an EOF is encountered before that.  Finally, a terminating null is placed at the end of the buffer.

---

### Post by Mirge on 2009-07-17
> **dwhitney67 said:**
> No, the man-page for fgets() indicates that at most one less than the number of bytes specified is read.  So if you specify 50, only 49 bytes are read, unless an EOF is encountered before that.  Finally, a terminating null is placed at the end of the buffer.

Ahh ok :)

---

