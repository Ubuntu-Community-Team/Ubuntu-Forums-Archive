---
title: "[SOLVED] C linked list...why am i getting segfault?"
date: 2008-03-19
forum: Programming Talk
---

### Post by S15_88 on 2008-03-19
hi i'm wondering why i'm getting a segfault before the user can input data.  I had the program running fine earlier before i tried to make a list.  Just wondering if i'm doing something wrong with respect to the pointers.  If anyone could give me some tips on how to make a list and stuff that would be great as i'm pretty confused right now.

i'm guessing that it has something to do with setting the pointers to NULL?

Thanks, ALain

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_LEN 250

struct node 
{
    char *name;
    int  age;
    struct node *nextName;
    struct node *nextAge;
};

typedef struct node NODE;

int drain_stdin()
{
    int c;

    while((c = getchar()) != '\n' && c != EOF );

    return c;
}
 
void addStruct(NODE *root, NODE *ptr)
{
    root = NULL;
    ptr = NULL;
 
    if (drain_stdin() != EOF)
    {
        printf("Enter name: ");
        fgets(ptr->name, MAX_LEN + 1, stdin);

        printf("Enter age: ");
        scanf("%d", &ptr->age);

        ptr->nextName = root;
        ptr->nextAge = root;
        root = ptr;
    }
    else
    {
        printf("An Error Has Occured\n");
    }
   
}

void removeStruct(NODE *root, NODE *ptr)
{
    char nameRemove[MAX_LEN + 1];

    root = NULL;
    ptr = NULL;
    
    if (drain_stdin() != EOF )
    {
        printf("Enter Name Of Desired Record To Be Removed: ");
        fgets(nameRemove, MAX_LEN + 1, stdin);

        if(strcmp(nameRemove, ptr->name) == 0)
        {
            printf("Found The Record\n");
        }
        else
        {
            printf("There Is No Record With That Name\n");
        }
        
    }
    else
    {
        printf("An Error Has Occured\n");
    }
}

void printName(NODE *root, NODE *ptr)
{
    root = NULL;
    ptr = NULL;

    printf("%s %d\n", ptr->name, ptr->age);
}

void printAge(NODE *root, NODE *ptr)
{
    root = NULL;
    ptr = NULL;

    printf("%s %d\n", ptr->name, ptr->age);
}


void progExit(NODE *root, NODE *ptr)
{

}


int main() 
{
    int choice;

    NODE *root, *ptr;

    ptr = malloc(sizeof(NODE));
    ptr->name = malloc(sizeof(char)*MAX_LEN);

    do
    {
        printf("1. Add structure\n");
        printf("2. Remove structure\n");
        printf("3. Print names\n");    
        printf("4. Print ages\n");
        printf("5. Exit\n");
        scanf("%d", &choice);

        if(choice == 1)
        {
            addStruct(root, ptr);
        }
        else if(choice == 2)
        {
            removeStruct(root, ptr);
        }

        else if(choice == 3)
        {
            printName(root, ptr);
        }
        else if(choice == 4)
        {
            printAge(root, ptr);
        }
        else if(choice == 5)
        {
            progExit(root, ptr);
        }   
        else
        {
            return 0;
        }
        
    }while(choice != 5);    

    return 0;
}


```

---

### Post by Jessehk on 2008-03-19
EDIT: I skimmed your post the first time, so I didn't realize you suspected the NULL pointers were the problem. Do you actually have a good idea of how pointers work in C? I ask not be critical, but randomly changing things and settings pointers to NULL (ie, trial and error) will likely not get you anywhere. My favorite reference for pointers is [here](http://www.eternallyconfuzzled.com/tuts/languages/jsw_tut_pointers.aspx), but be prepared to learn.
If your looking at writing linked lists, the same site has a great (and lengthy, but in a good way) guide on them [here](http://www.eternallyconfuzzled.com/tuts/datastructures/jsw_tut_linklist.aspx). Good luck, and try to ask better questions in the future. :)

Despite the terrible way in which you asked this question (no line numbers, no indications of expected behavior, etc), I'll tell you that in
**addStruct()**, you set
```

ptr = NULL;

```

and then dereference it when you call **fgets()**. Dereferencing a NULL pointer will usually result in a segfault, but AFAIK is actually undefined behavior. You do the same thing in **removeStruct()**, and **printName()**.

---

### Post by S15_88 on 2008-03-19
sorry about the phrasing of the question, and i figured the problem out, my apologies i didn't look hard enough before i posted.

Thanks, ALain

---

### Post by stevescripts on 2008-03-19
The OP was on the right track to suspect a NULL pointer.

A little levity - for any of you who may never have seen this -

The Ten Commandments for C Programmers : [http://www.lysator.liu.se/c/ten-commandments.html](http://www.lysator.liu.se/c/ten-commandments.html)

Hope somebody gets a smile - I know I certainly did, the first time somebody
pointed me to this link.

Steve

---

### Post by Jessehk on 2008-03-19
> my apologies i didn't look hard enough before i posted.

That's ok. Read the edit. :)

---

