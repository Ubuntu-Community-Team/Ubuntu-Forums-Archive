---
title: "Mysterious Program"
date: 2012-02-05
forum: Programming Talk
---

### Post by achuth on 2012-02-05
Sir,
Please consider the below C code.
[FONT=Courier New]
[B]#include<stdio.h>
void main()
{
  char c1,c2;
  do
  {
   printf("\nEnter a character");
    scanf("%c",&c1);
     printf("\nDo you want to continue?yes(y),no(n)\n");
    scanf("%c",&c2);
  }while(c2=='y');
} [/B][/FONT]


The second scanf is not working !!!! I don't know why this happens.
The program just exits after the **printf** statement.
Please explain why this happens..
I have used **gcc** for compiling the program

---

### Post by Arndt on 2012-02-05
> **achuth said:**
> Sir,
Please consider the below C code.
[FONT=Courier New]
[B]#include<stdio.h>
void main()
{
  char c1,c2;
  do
  {
   printf("\nEnter a character");
    scanf("%c",&c1);
     printf("\nDo you want to continue?yes(y),no(n)\n");
    scanf("%c",&c2);
  }while(c2=='y');
} [/B][/FONT]


The second scanf is not working !!!! I don't know why this happens.
The program just exits after the **printf** statement.
Please explain why this happens..
I have used **gcc** for compiling the program

Don't use scanf. Read one line with fgets and then parse it with sscanf.

---

### Post by ofnuts on 2012-02-05
> **achuth said:**
> Sir,
Please consider the below C code.
[FONT=Courier New]
[B]#include<stdio.h>
void main()
{
  char c1,c2;
  do
  {
   printf("\nEnter a character");
    scanf("%c",&c1);
     printf("\nDo you want to continue?yes(y),no(n)\n");
    scanf("%c",&c2);
  }while(c2=='y');
} [/B][/FONT]


The second scanf is not working !!!! I don't know why this happens.
The program just exits after the **printf** statement.
Please explain why this happens..
I have used **gcc** for compiling the program
The second scanf() is working... what it gets is the LF you entered at the first prompt (because you had to strike the Enter key... so reallyt entered "a\n", for instance). Your code has to consume that character... as well as anything you enter at the first prompt before hitting Enter ("yyyyyyyyyynnnnn[Enter]")

---

### Post by achuth on 2012-02-07
***ofnuts* **helped me.
Thanks.
Thread ends here.

---

### Post by Arndt on 2012-02-07
> **achuth said:**
> ***ofnuts* **helped me.
Thanks.
Thread ends here.

Then you can mark it "solved".

---

