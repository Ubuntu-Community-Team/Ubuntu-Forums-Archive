---
title: "C simple program, HELP."
date: 2010-10-11
forum: Packaging and Compiling Programs
---

### Post by punkzio on 2010-10-11
Hi I did a simple program but when compiling it says:

make correct_prog0316
cc     correct_prog0316.c   -o correct_prog0316
correct_prog0316.c: In function ‘main’:
correct_prog0316.c:10: error: expected expression before ‘)’ token
make: *** [correct_prog0316] Error 1


But I don't know what's wrong.

Here is the program:

#include <stdio.h>
main () {

   float num1, num2, res=0;  /* What I did was changing int to float  */
   char op;

   printf("Escreva uma expressao mat: ");
   scanf(" %f %c %f ", &num1, &op, &num2);

   switch () {

   case '+' : res = num1+num2; break;
 
   case '-' : res = num1-num2; break;

   case 'x' :
   case '*' : res = num1*num2; break;

   case ':' :
   case '/' : res = num1/num2; break;
   }

   printf(" %f %c %f = %f \n", num1, op, num2, res);
}




Thanks to all.

---

### Post by punkzio on 2010-10-11
I solved the problem I asked, but now it blocks when I run it.

---

### Post by cgroza on 2010-10-11
C++ is tricky at first but you will get it. Does it reports any errors? And I dont think you can use the switch statement with non int values. Try with if and else if.

---

### Post by dethorpe on 2010-10-11
I think you need to put the variable name in the switch statement: switch (op)

---

### Post by Tony Flury on 2010-10-11
You can use switch with characters (not character strings), and ints/longs etc, but nothing else.

also your switch statement is wrong - you have to tell it what character to switch on 

```

switch( op ){
....
}

```
The reason it might be blocking is to do with way scanf works - especially with single characters.

---

### Post by punkzio on 2010-10-11
Thanks cgroza, I changed from "switch" to "if", "else if"
but it continues to do the same thing 

./correct_prog0316
Escreva uma expressao mat: 21/4
                                  <- in this line doesn't appear nothing.

Then I tried to type a letter and it worked but not the way it was supposed to.

./correct_prog0316
Escreva uma expressao mat: 21/4
w
 21.000000 / 4.000000 = 5.250000

---

### Post by punkzio on 2010-10-11
When I say I solved it was refering to " switch () " I have already changed it. That's not the problem now.

---

### Post by cgroza on 2010-10-11
Post the latest code.

---

### Post by punkzio on 2010-10-11
Here you have cgroza :)


#include <stdio.h>
main () {

  float num1, num2, res=0;  /* What I did was changing int to float  */
  char op;

  printf("Escreva uma expressao mat: ");
  scanf("%f %c %f ", &num1, &op, &num2);

  if (op == '+') 

    res = num1+num2;

  else 

    if (op == '-')
      res = num1-num2;

    else 

      if (op == '*')
	res = num1*num2;

      else

	if (op == '/')
	  res = num1/num2;

  printf(" %f %c %f = %f \n", num1, op, num2, res);
}

---

### Post by dethorpe on 2010-10-12
Looks like you have a space at the end of your scanf format string, that might make scanf eat whitespace which would include the CR. then the w causes it to complete as its an unmatched charater. Try removing the space: 
  scanf("%f %c %f",

---

### Post by punkzio on 2010-10-12
You were right dethorpe :)

It was That :D

THANKS TO All of you

---

### Post by cgroza on 2010-10-14
So much trouble for a space. LOL

---

