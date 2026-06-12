---
title: "[C] Problem with Linked Lists"
date: 2008-08-15
forum: Programming Talk
---

### Post by British0zzy on 2008-08-15
I'm trying to write my first program to use linked lists and I'm having pointer troubles. I want to use the list as a stack (first in, last out).
When I run the program, the 'head' of the list seems to point NULL. I'm not sure why this is. Here is my test code to get them up and running.

```
#import <stdio.h>
#import <stdlib.h>

typedef struct node { 
    int data; 
    struct node* next; 
} LList;

void push(LList* head, int n);
int pop(LList* head);

int main (int argc, char *argv[])
{
    LList* stack1 = NULL;
    LList* stack2 = NULL;
    int a[] = {1, 2, 3, 4};
    size_t i;
    
    for (i = 0; i < 4; ++i) {
        push(stack1, a[i]);
    }
    for (i = 0; i < 4; ++i) {
        push(stack2, a[3 - i]);
    }
    printf("Stack1:\n");
    for (i = 0; i < 4; ++i) {
        printf("%i\n", pop(stack1));
    }
    printf("Stack2:\n");
    for (i = 0; i < 4; ++i) {
        printf("%i\n", pop(stack2));
    }
    return 0;
}

void push(LList* head, int n)
{
    if (head == NULL) {
        LList* newNode = malloc(sizeof(LList));
        if((head = newNode) == NULL) {
            printf("Error: Memory allocation failed.\n");
            return;
        }
        newNode->next = NULL;
        newNode->data = n;
    }
    else {
        LList* newNode = malloc(sizeof(LList));
        if(newNode == NULL) {
            printf("Error: Memory allocation failed.\n");
            return;
        }
        newNode->next = head;
        head = newNode;
        newNode->data = n;
    }
    return;
}

int pop(LList* head)
{
    if (head != NULL) {
        LList* temp;
        int n;
        n = head->data;
        temp = head->next;
        free(head);
        head = temp;
        return n;
    }
    else {
        printf("Error: Stack is empty.\n");
        return 0;
    }
        
}
```

When I run the program, I receive the 'Error: Stack is empty' message for each call of pop.
I'm pretty sure the problem is the function push. I've looked over it a bunch of times and can't tell where I made a mistake. I'm a beginner so its probably some obscure rule I forgot.

---

### Post by WW on 2008-08-15
Your push() function can not change the value of the stack pointer, at least not the way you have written it.  None of the calls "push(stack1,a[i])" change the value of stack1, so stack1 is still NULL after each call.  C is "call by value"; to change stack1 when push() is called, you would have to pass its address (and adjust the push function accordingly).

---

### Post by mike_g on 2008-08-15
To show what WW means in code:
```

int main()
{
    ...
    for (i = 0; i < 4; ++i) {
        push([COLOR="DarkRed"]&[/COLOR]stack1, a[i]);
    }
    ...
}

void push(LList*[COLOR="DarkRed"]*[/COLOR] head, int n)
{
    ...

    [COLOR="DarkRed"](*newNode)[/COLOR]->next = head;
    head = [COLOR="DarkRed"]*newNode[/COLOR];
    [COLOR="DarkRed"](*newNode)[/COLOR]->data = n;
 
    ...
}
```

Using pointers was one of the things I found most difficult in learning C. I could understand what I needed to do when it was explained to me - I just dident get the syntax. and I'm still not completely sure about it, lol

---

### Post by dwhitney67 on 2008-08-15
mike_g, you are correct.  The same concept also needs to be applied to the pop() function.

BritishOzzy, you should refrain from using "#import" and use the more portable "#include" syntax for including header files.

Also, for the push() and pop() functions, try to simplify it like:
[PHP]void push(LList** head, int n)
{
    LList* newNode = malloc(sizeof(LList));

    if(newNode == NULL) {
        printf("Error: Memory allocation failed.\n");
        return;
    }

    if (*head == NULL) {
        *head = newNode;
        newNode->next = NULL;
        newNode->data = n;
    }
    else {
        newNode->next = *head;
        *head = newNode;
        newNode->data = n;
    }
}

int pop(LList** head)
{
    if (*head == NULL) {
        printf("Error: Stack is empty.\n");
        return 0;
    }

    int n = (*head)->data;
    LList *temp = (*head)->next;
    free(*head);
    *head = temp;
    return n;
}
[/PHP]

---

### Post by WW on 2008-08-15
I didn't have time earlier to suggest actual changes in the code, and now mike_g and dwhitney76 have done it well.  Take a close look at dwhitney76's code, especially the push() function.

---

### Post by British0zzy on 2008-08-16
Thanks for the tips. I was confused, thinking that call by value only applies when you give a function an number (not a pointer or a list). 
So in my code I was sending the value of the pointer to the function. The only time I can change data, not created by the function, I have to dereference a pointer? I think that makes a lot more sense to me now.
And (*newNode).data is equivalent to newNode->data?

Sorry, about the import command, I'm going to end up using the linked list in an objective-c program :).

I like the look of unrolled linked lists. I can think of some ways to implement them, but I don't know how efficient my method is. Do you know of any websites that describe the specifics to unrolled linked lists?

---

