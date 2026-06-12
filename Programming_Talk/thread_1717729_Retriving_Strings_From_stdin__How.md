---
title: "Retriving Strings From stdin : How?"
date: 2011-03-30
forum: Programming Talk
---

### Post by ChipOManiac on 2011-03-30
This question popped up when I was doing «Thinking In C» by Chuck Allison, in Chapter 5 we're asked to create a program as an exercise... one of the main aspects of the progam includes retreiving a string and putting it into one of the members of a struct....

The struct is understood well by me, but the problem comes with reading the string

«gets» seems to be dangerous, and the manual's description convinced me...
«fgets» seemed to be the answer... but there's a small problem... we're expected to enter the number of characters we expect to be input...

This seems a little restricted, and even though «fgets» is supposed to stop after an endline or EOF it does'nt do so and keeps reading the rest of the entry until size number of characters is entered.

So my question is this... how can I read a line from stdin without these hassles...?

Any help and rudeness for being an idiot gracefully accepted...

Thanks for trying to help. :)

---

### Post by MadCow108 on 2011-03-30
> **ChipOManiac said:**
> 
This seems a little restricted, and even though «fgets» is supposed to stop after an endline or EOF it does'nt do so and keeps reading the rest of the entry until size number of characters is entered.




I don't believe this.
[quote=man fgets]
fgets() reads in **at most** one less than size characters from stream and stores them into the buffer pointed  to by  s.   Reading **stops** after an EOF or a newline[/quote]

can you please show your code?

for very easy reading from streams have a look at getline.
it saves you the manual buffer management, but it is not part of the C standard and thus less portable!

---

### Post by ChipOManiac on 2011-03-30
Thanks For Reading «MadCow108»!

Here's the code:
```

/* arbemprecorder.c Arbitary Employee Recorder */
#include <stdio.h>
#include <strings.h>

#define MAXEMPENTRIES 4

struct Employee
{
  char last[19];
  char first[19];
  char title[5];
  int salary;
};

int main()
{
  struct Employee AstructEmployeeList[MAXEMPENTRIES];
  int intEmployeeCount;

  printf("Please Enter The\nLast Name\nFirst Name\nTitle\nSalary\n");

  for (intEmployeeCount=0; intEmployeeCount < MAXEMPENTRIES; intEmployeeCount++)
  {
    fgets(AstructEmployeeList[intEmployeeCount].last, 19, stdin);

    if ((AstructEmployeeList[intEmployeeCount].last) == "")
    {
      printf("No Characters Entered... Terminating");
      break;
    }

    fgets(AstructEmployeeList[intEmployeeCount].first, 19, stdin);
    fgets(AstructEmployeeList[intEmployeeCount].title, 5, stdin);
    scanf("%d", &AstructEmployeeList[intEmployeeCount].salary);
  }

  while (intEmployeeCount >= 0)
  {
    printf("Last Name: %s, First Name: %s, Title: %s, Salary: %d\n",
       AstructEmployeeList[intEmployeeCount].last,
       AstructEmployeeList[intEmployeeCount].first,
       AstructEmployeeList[intEmployeeCount].title,
       AstructEmployeeList[intEmployeeCount].salary);
    intEmployeeCount--;
  }
}

```

And Here's The Output:

```

Please Enter The
Last Name
First Name
Title
Salary
Arun
Varma
Mr.
90
Vipul
Rao
Mr.
100
Vikaas
Swarp
Mr.
200
Last Name: , First Name: , Title: , Salary: -1076716276
Last Name: as
, First Name: Swarp
, Title: Mr.
, Salary: 200
Last Name: Mr.
, First Name: 100
, Title: Vika, Salary: -1076716520
Last Name: 
, First Name: Vipul
, Title: Rao
, Salary: 134513176
Last Name: Arun
, First Name: Varma
, Title: Mr.
, Salary: 90

```

Did I Do Something Stupid? :confused:???

---

### Post by MadCow108 on 2011-03-30
there are a few problems:
1. fgets also reads the new line into the buffer, so you need to remove it if you don't need it (e.g. if (buffer[strlen(buffer) == '\n') buffer[strlen(buffer)] = '\0')

2. if the string entered is too long for the buffer the newline will remain in the string and the next fgets will return on it.
check for newline at the end of the buffer and handle it (e.g. increase the buffer and repeat fgets or error out).

3. (AstructEmployeeList[intEmployeeCount].last) == "" is usually undefined.
if you want to check if the string is empty first initialize the buffer to zero and check if the first character is a newline after the fgets
compile with -Wall and the compiler will warn you about this.

4. scanf("%d", &AstructEmployeeList[intEmployeeCount].salary); will not remove the trailing newline
use "%d%*c" to remove all following characters from the stream

5. while (intEmployeeCount >= 0) ..., here youre employee count is one to large. use a for loop, reduce it by one or use a do while loop and put the decrement to the top.

6. in this case you should use sizeof to get the buffer size: fgets(AstructEmployeeList[intEmployeeCount].first, sizeof(AstructEmployeeList[intEmployeeCount].first), stdin)
this saves some typing when changing the struct
but beware only use sizeof for information known at compile time e.g. arrays in the same stack frame or global.
When used on pointers to dynamic memory it will always return the size of the pointer regardless to how large the memory pointed to is.

---

### Post by ChipOManiac on 2011-04-12
Hey <<MadCow108>>... I'm very sorry for not replying to your posts, I was constantly distracted when I was going to reply and never got ot it... Thank You very much for your informative post, it helped clear out the problems I had and more, It's really appreciated.

Once again. Sorry for not replying and thank you very much for your help. :D

---

