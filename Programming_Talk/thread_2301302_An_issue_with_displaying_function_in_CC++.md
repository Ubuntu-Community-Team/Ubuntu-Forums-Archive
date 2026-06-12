---
title: "An issue with displaying function in C/C++"
date: 2015-11-01
forum: Programming Talk
---

### Post by NoWeDoR on 2015-11-01
Hello guys.

 I want to create a simply circular linked list that shows the entered names on the screen.

I also created it but I guess there is something wrong in displayList() function. When I run the codes (which are I've shared below), it shows me strange symbols, articles etc. Would you run and help me about the problem?

```
#include <stdio.h>#include <stdlib.h>


struct list
{
    char *data;
    struct list *next;
};


typedef struct list List;
typedef List *ptrList;
ptrList head;


void createALinkedList()
{
    int i, elementNumber; 
    char value[25];
    printf("Express that how many name you'll enter: ");
    scanf_s("%d", &elementNumber);
    for (i = 0; i < elementNumber; i++)
    {
        printf("Enter %d. name of list: ", i + 1);
        scanf("%s", &value);
        if (head == NULL)
        {
            head = (List *)malloc(sizeof(List));
            head->data = value;
            head->next = head;
        }
        else
        {
            ptrList temp1 = head;
            ptrList temp2 = (List *)malloc(sizeof(List));
            while (temp1->next != head)
            {
                temp1 = temp1->next;
            }
            temp1->next = temp2;
            temp2->data = value;
            temp2->next = head;
        }
    }
}


void displayList()
{
    ptrList temp = head;
    do
    {
        printf("%s\n", temp->data);
        temp = temp->next;
    } while (temp != head);
}




int main()
{
    createALinkedList();


    printf("\n*-* First statement of list *-*\n");
    displayList();


    return 0;
}

```

---

### Post by steeldriver on 2015-11-01
Your 

```

head->data = value;

```

just assigns the *value of the local pointer*: you need to allocate explicit storage for each data string within each struct member that you create, and then strcpy or strncpy the respective `value`s to them, I think. Don't forget to `free` the memory at the end.

---

### Post by spjackson on 2015-11-01
You don't allocate any memory for the data. Here's one way to do it
```

    head->data = strdup(value);
    temp2->data = strdup(value);

```

---

