---
title: "Simple calculator &quot;( )&quot; priority needed!"
date: 2011-05-09
forum: Programming Talk
---

### Post by heatblazer on 2011-05-09
Hello. I am programming in C for 4 months / no previous experience/ and I am trying to make a simple calculator using a stack ADT. My problem is that I can`t seem to make the priority of the braces...
like: 10+10+(2*2) to equals to 24 instead of 48... :( Here is my code:
Any advice will be appreciated :) 

#include <stdio.h>
#define SIZE 100
int stack[SIZE];
int *sp = stack; /*pointer to the stack*/

/********PROTOTYPES*****************/

void push(int a);
int pop(void);

/******************MAIN*************/
int main(void) {

    int i, j;
    char ch;
    do {
        scanf("%d", &i);
        push(i);
       if ( ch == '+' ) {
           push(pop()+pop());
       }
        if ( ch == '*' ) {
            push(pop()*pop());
        }
        if ( ch == '-' ) {
            int temp = pop();
            push(pop()-temp);
        }
        if ( ch == '/' ) {
            int temp = pop();
            push(pop()/temp);
        }
        printf("ch is %c \n", ch);

    } while( (ch=getchar()) != '=' );

    printf("%d is stack\n", stack[0]);
}
/****************************************/

void push(int a) {

    *(sp++) =  a;
}

int pop(void) {

    return *(--sp);
}

---

### Post by simeon87 on 2011-05-09
The problem is that you're immediately popping when you encounter a '*' symbol. Let's say we're evaluating 2*(3*4) then you have to process the whole equation first before you can compute the value of the first multiplication. Same for (2*3)*4. You can build a stack-based calculator this way but then you have to use Reverse Polish notation: [http://en.wikipedia.org/wiki/Reverse_Polish_notation](http://en.wikipedia.org/wiki/Reverse_Polish_notation) The proper way of evaluating expressions like these is by building a parse tree, like this one

[IMG]http://images.immateriel.fr/baw/9780596155971/tagoreillycom20090804oreillyimages316024.png.jpg[/IMG]

and then evaluating each of the nodes to compute the final result.

---

### Post by heatblazer on 2011-05-09
> **simeon87 said:**
> The problem is that you're immediately popping when you encounter a '*' symbol. Let's say we're evaluating 2*(3*4) then you have to process the whole equation first before you can compute the value of the first multiplication. Same for (2*3)*4. You can build a stack-based calculator this way but then you have to use Reverse Polish notation: [http://en.wikipedia.org/wiki/Reverse_Polish_notation](http://en.wikipedia.org/wiki/Reverse_Polish_notation) The proper way of evaluating expressions like these is by building a parse tree, like this one

[IMG]http://images.immateriel.fr/baw/9780596155971/tagoreillycom20090804oreillyimages316024.png.jpg[/IMG]

and then evaluating each of the nodes to compute the final result.


Nice chart, btw. Well I tested the following:
10+++ it equals to 10+10+10+10... each '+' pushesh s sum of the original pop()... So you propose a linked list for doing this... I`m a newbie yet so a little pseudocode will help :)

---

### Post by simeon87 on 2011-05-09
> **heatblazer said:**
> Nice chart, btw. Well I tested the following:
10+++ it equals to 10+10+10+10... each '+' pushesh s sum of the original pop()... So you propose a linked list for doing this... I`m a newbie yet so a little pseudocode will help :)

That's not correct notation because you now have more plus symbols than numbers. But the following examples are in Reverse Polish Notation:

10 10 +
2 3 4 * *

The first is equal to 10 + 10, the second is equal to 2 * (3 * 4). The way it works is:

- Process symbol.
- If it's a number, push it on the stack.
- If it's a + - / *, then pop as needed and compute result. Push that back on the stack.
- Keep going until you're done.

So the above examples would be:

Push(10)
Push(10)
Pop() (gives 10)
Pop() (gives 10)
Push(10 + 10)

and:

2 3 4 * *
Push(2)
Push(3)
Push(4)
Pop() (gives 4)
Pop() (gives 3)
Push(3 * 4)
Pop (gives 12)
Push(2 * 12)

---

### Post by heatblazer on 2011-05-09
> **simeon87 said:**
> That's not correct notation because you now have more plus symbols than numbers. But the following examples are in Reverse Polish Notation:

10 10 +
2 3 4 * *

The first is equal to 10 + 10, the second is equal to 2 * (3 * 4). The way it works is:

- Process symbol.
- If it's a number, push it on the stack.
- If it's a + - / *, then pop as needed and compute result. Push that back on the stack.
- Keep going until you're done.

So the above examples would be:

Push(10)
Push(10)
Pop() (gives 10)
Pop() (gives 10)
Push(10 + 10)

and:

2 3 4 * *
Push(2)
Push(3)
Push(4)
Pop() (gives 4)
Pop() (gives 3)
Push(3 * 4)
Pop (gives 12)
Push(2 * 12)

I was thinking of a string separation usign atoi to check if it is a number then push it to the stack and after encountering a symbol like +,-,* or / to pop then push back dependantly of the next atoi string... 
 Or... I can have 2 stacks - integer and symbol in the int I`ll store numbers, in symbol I`ll store operators then pop as it follows:

intstaack 1, 2, 3

symbolstack +, *, -;

then I can add () to make a fake priority by pushing later symbols... :confused: too nerdy

---

### Post by simeon87 on 2011-05-09
> **heatblazer said:**
> I was thinking of a string separation usign atoi to check if it is a number then push it to the stack and after encountering a symbol like +,-,* or / to pop then push back dependantly of the next atoi string... 
 Or... I can have 2 stacks - integer and symbol in the int I`ll store numbers, in symbol I`ll store operators then pop as it follows:

intstaack 1, 2, 3

symbolstack +, *, -;

then I can add () to make a fake priority by pushing later symbols... :confused: too nerdy

There are many ways to implement a parser. If you wish to use two stacks that's fine, it's just that Reverse Polish Notation doesn't require more than one stack.

---

### Post by schauerlich on 2011-05-09
One simple thing you could do to both keep your infix notation and still be able to evaluate expressions easily and using a stack is to convert the infix expression to reverse polish notation, and then evaluate the resulting expression. You can use Dijkstra's Shunting Yard Algorithm for this. There's a bunch of information [here](http://ubuntuforums.org/showthread.php?t=1441700), including a lot of examples.

---

