---
title: "sorted linked list...why seg faults!"
date: 2008-03-24
forum: Programming Talk
---

### Post by S15_88 on 2008-03-24
i have a program that adds a name and an age to a structure then that structure is added to a list that's sorted by name and age.

when i add a struct then go to remove it, seg fault!

when i add a struct it's all good but when i go to add another struct, seg fault!

i'm using -g when compiling and  valgrind --show-reachable=yes to see the problems with memory.

i can't figure this out for the life of me, can someone shed some light on as to why i'm getting these seg faults.

Thanks, ALain

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_LEN 250

typedef struct node 
{
    char *name;
    int  age;
    struct node *nextName;
    struct node *nextAge;
}NODE;

int drain_stdin()
{
    int c;

    while((c = getchar()) != '\n' && c != EOF);

    return c;
}

NODE * listInput(NODE *new)
{

    new = malloc(sizeof(NODE));
	new->name = malloc(sizeof(char)*MAX_LEN + 1);    
    
    if (drain_stdin() != EOF)
    {
        printf("Enter name: ");
        fgets(new->name, MAX_LEN + 1, stdin);

        printf("Enter age: ");
        scanf("%d", &new->age);
    }
    else
    {
        printf("An Error Has Occured\n");
    }
    return new;
}

NODE * insertNameNode(NODE *new, NODE *head1)
{
    NODE *temp;
    NODE *prev;

    new->nextName = NULL;
    
    if (head1 == NULL)
    {
        return new;     
    }

    temp = head1;
    prev = NULL; 
    
    while(1) 
    {
	    if (strcmp(temp->name, new->name) < 0) 
        {
		    prev = temp; 
		    temp = temp->nextName;      
		    continue; 
	    }
        else/* if(strcmp(temp->name, new->name) >= 0) */
        {
	        new->nextName = temp;   	
            
	        if (prev != NULL)
            {
                prev->nextName = new;  
            }
	        else
            {
                head1 = new;  
	            /*break;*/
            }
        }
    }
    return (head1);    
}

NODE * insertAgeNode(NODE *new, NODE *head2)
{
    NODE *temp;
    NODE *prev;

    new->nextAge = NULL;

    if (head2 == NULL)
    {
        return new;     
    }

    temp = head2;
    prev = NULL; 
    
    while(1) 
    {

	    if (temp->age < new->age) 
        {
		    prev = temp; 
		    temp = temp->nextAge;      
		    continue; 
	    }
        else/* if(temp->age >= new->age) */
        {
	        new->nextAge = temp;   	
            
	        if (prev != NULL)
            {
                prev->nextAge = new;  
            }
	        else
            {
                head2 = new;  
	           /* break;*/ 
            }
        }
    }
    return(head2);
}


NODE * removeNameStruct(NODE *head1, char *nameRemove)
{
    NODE *prev;
    NODE *root;    

    prev = NULL;
    root = head1;    
   
    if (drain_stdin() != EOF )
    {
        printf("Enter Name Of Desired Record To Be Removed: ");
        fgets(nameRemove, MAX_LEN + 1, stdin);

        while (root != NULL) 
        { 
            if(strcmp(nameRemove, root->name) == 0)
            {
                printf("Found The Record\n");

                if (prev != NULL)
                {
                    prev->nextName = root->nextName;
                }
                else
                {
                    head1 = root->nextName;
                }
                root = root->nextName; 
                /*free(head1);*/
                break;
            } 
            else 
            {
                printf("Record NOT Found\n");
     		    prev = root; 
			    root = root->nextName;
		    }
        }
    }
    else
    {
        printf("An Error Has Occured\n");
    } 
    return (head1);
}

NODE * removeAgeStruct(NODE *head2, char *nameRemove)
{

    NODE *prev;
    NODE *root;

    prev = NULL;   
    root = head2;    

    while (root != NULL) 
    { 
        if(strcmp(nameRemove, root->name) == 0)
        {
            printf("Found The Record\n");

            if (prev != NULL)
            {
                prev->nextAge = root->nextAge;
            }
            else
            {
                head2 = root->nextAge;
            }
            root = root->nextAge;
            free(head2->name);
            free(head2);
            break;
        } 
        else 
        {
            printf("Record NOT Found\n");
            prev = root;
            root = root->nextAge;
	    }
    }
    return (head2);
}

void printName(NODE *head1, NODE *head2)
{
    if (head1 == NULL) 
    { 
		printf("List is empty.\n") ; 
		return; 
	}
    else
    {    
        while (head1 != NULL) 
        {
            printf("%s %d\n", head1->name, head1->age);
            head1 = head1->nextName;
        }
    }
}

void printAge(NODE *head1, NODE *head2)
{
    if (head2 == NULL) 
    { 
		printf("List is empty.\n") ; 
		return ; 
	}
    else
    {    
        while (head2 != NULL) 
        {
            printf("%s %d\n", head2->name, head2->age);
            head2 = head2->nextAge;
        }
    }
}


void freeProg(NODE *head1, NODE *head2)
{
/*
    while(head1 != NULL && head2 != NULL)
    {
        free(head2->name);    
        free(head2);
    }    
*/ 
}


int main(void) 
{
    int choice, count;
    char nameRemove[MAX_LEN + 1];

    choice = 0;
    count = 0;

    NODE *new;
    NODE *head1;
    NODE *head2;
    
    new = NULL;
    head1 = NULL;
    head2 = NULL;

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
            new = listInput(new);
            head1 = insertNameNode(new, head1);
            head2 = insertAgeNode(new, head2);
        }
        else if(choice == 2)
        {
            head1 = removeNameStruct(head1, nameRemove);
            head2 = removeAgeStruct(head2, nameRemove);
        }

        else if(choice == 3)
        {
            printName(head1, head2);
        }
        else if(choice == 4)
        {
            printAge(head1, head2);
        }
        else if(choice == 5)
        {
            freeProg(head1, head2);
        }   
        else
        {
            return 0;
        }
        
    }while(choice != 5);    

    return 0;
}

/*
NODE * removeStruct(NODE *head1, NODE *head2)
{
    NODE *prev;
    NODE *root;

    prev = NULL;
    root = head1;

    char nameRemove[MAX_LEN + 1];
   
    if (drain_stdin() != EOF )
    {
        printf("Enter Name Of Desired Record To Be Removed: ");
        fgets(nameRemove, MAX_LEN + 1, stdin);

        while (head1 != NULL) 
        { 
            if(strcmp(nameRemove, root->name) == 0)
            {
                printf("Found The Record\n");
                if (prev != NULL)
                {
                    prev->nextName = head1->nextName;
                   
                }
                else
                {
                    root = head1->nextName; 
                    
                }
                free(head1);
                break;
            } 
            else 
            {
     		    prev = head1; 
			    head1 = head1->nextName;
		    }
        }
    }
    else
    {
        printf("An Error Has Occured\n");
    } 
    return head1;
}
*/

```

---

### Post by kknd on 2008-03-24
Try debugging it with gdb.

---

### Post by Jessehk on 2008-03-24
A linked list node, regardless of how many pieces of data it has, only contains **one** link to the next node.

Your code,
```

typedef struct node 
{
    char *name;
    int  age;
    struct node *nextName;
    struct node *nextAge;
}NODE;

```

is nonsensical.

You didn't look at the linked list guide I gave you last time this happened, did you?

---

### Post by themusicwave on 2008-03-24
> **Jessehk said:**
> A linked list node, regardless of how many pieces of data it has, only contains **one** link to the next node.

Your code,
```

typedef struct node 
{
    char *name;
    int  age;
    struct node *nextName;
    struct node *nextAge;
}NODE;

```

is nonsensical.

You didn't look at the linked list guide I gave you last time this happended, did you?

The only time you need more than one link is perhaps for a doubly linked list where you can traverse forwards and backwards.  For starters, I would only worry about going through the list forwards unless you need to go backwards.

Either way though, you need to link to nodes not to the data they contain.

---

### Post by Jessehk on 2008-03-24
[quote=me]
only contains one link to the **next** node.
[/quote]

:)

---

### Post by WW on 2008-03-24
> **Jessehk said:**
> A linked list node, regardless of how many pieces of data it has, only contains **one** link to the next node.

Your code,
```

typedef struct node 
{
    char *name;
    int  age;
    struct node *nextName;
    struct node *nextAge;
}NODE;

```

is nonsensical.

I beg to differ. There is no reason this can't work.  S15_88 is implementing two linked lists, that happen to hold the same data.  I'm not saying that this implementation is great, but it is not "nonsensical".

S15_88: Your "insert" functions are more complicated than necessary.  Check out these versions:
```

NODE * insertNameNode(NODE *new, NODE *head1)
{
    NODE *temp;
    NODE *prev;

    temp = head1;
    prev = NULL;
    while ((temp != NULL) && (strcmp(temp->name,new->name) < 0)) 
    {
        prev = temp; 
        temp = temp->nextName; 
    }
    new->nextName = temp;
    if (prev == NULL)
    {
        // Special case: new becomes the first element in the list.
        return new;
    }
    else
    {
        prev->nextName = new;
        return head1;
    }
}

NODE * insertAgeNode(NODE *new, NODE *head2)
{
    NODE *temp;
    NODE *prev;

    temp = head2;
    prev = NULL;
    while ((temp != NULL) && (temp->age < new->age)) 
    {
        prev = temp; 
        temp = temp->nextAge; 
    }
    new->nextAge = temp;
    if (prev == NULL)
    {
        // Special case: new becomes the first element in the list.
        return new;
    }
    else
    {
        prev->nextAge = new;
        return head2;
    }
}

```

---

