---
title: "String Copy issues"
date: 2008-09-16
forum: Programming Talk
---

### Post by MiroMage on 2008-09-16
Hey,

I'm supposed to write a program that will read in vehicle information from the user and sort and store the information in a linked list in sorted order by the license number. Whenever I use the strcpy function, my program always crashes and I'm not sure what else to do at this point. Here is the code I have so far:

```
[COLOR="SeaGreen]#include <stdio.h>
#include <string.h>[/COLOR]

struct vehicle
{
    int year;
    char* license;
    char* model;
    char* color;
    char* make;
    struct vehicle* next;
};


void insert(struct vehicle** head, char* make, char* model, int year, char* color, char* license);

int main (void)
{
    int choice;
    char license[15];
    char make[15]; 
    char model[15];
    char color[15];
    int year;
    struct vehicle* head = NULL;
    
    printf("Welcome to the Skyweb's Automobile Management Subsystem.\n");
    
    do
    {
       printf("Here are your options.\n");
       printf("1) Insert a vehicle.\n");
       printf("2) Delete a vehicle.\n");
       printf("3) Print all vehicles.\n");
       printf("4) Save to a file.\n");
       printf("5) Load from a file.\n");
       printf("0) Quit.\n");
       printf("Please make a choice.\n");
       
       scanf("%d", &choice);
       
       if (choice == 1)
       {
            printf("What is the make of the vehicle?\n");
            scanf("%s", &make);
            printf("What is the model?\n");
            scanf("%s", &model);
            printf("What is the year?\n");
            scanf("%d", &year);
            printf("What is the color?\n");
            scanf("%s", &color);
            printf("What is the license plate number?\n");
            scanf("%s", &license);
            
            insert(&head, make, model, year, color, license);
            
            printf("Vehicle Added!\n");
        }
            
    }
    while (choice != 0); 
    
    
    system("PAUSE");
    return 0;
}


void insert(struct vehicle** head, char* make, char* model, int year, char* color, char* license)
{
    struct vehicle* newvehicle;
    struct vehicle* crnt = (*head);
    
    newvehicle = malloc(sizeof(struct vehicle));
    newvehicle->make = make;
    newvehicle->model = model;
    newvehicle->year = year;
    newvehicle->color = color;
    newvehicle->license = license;
    
    
    
    
    if ((*head) == NULL || (*head)->license > license)
    {
        strcpy((*head),newvehicle->next);
        strcpy(newvehicle,(*head));
        return;
    }
    
    while(crnt->next != NULL && crnt->next->license < license)
    {
        strcpy(crnt->next, crnt);
    }
    
    strcpy(crnt->next,newvehicle->next);
    strcpy(newvehicle,crnt->next);
}
```

---

### Post by LaRoza on 2008-09-16
> **MiroMage said:**
> Hey,

I'm supposed to write a program that will read in vehicle information from the user and sort and store the information in a linked list in sorted order by the license number. Whenever I use the strcpy function, my program always crashes and I'm not sure what else to do at this point. Here is the code I have so far:


I'll give you a hint, it has to do with pointers and their relationships to arrays.

Read this thread for the solution: [http://ubuntuforums.org/showthread.php?t=717011](http://ubuntuforums.org/showthread.php?t=717011)

---

