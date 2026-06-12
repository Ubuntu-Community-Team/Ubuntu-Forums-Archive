---
title: "Passing a linked list to a function"
date: 2010-06-08
forum: Programming Talk
---

### Post by esmeco on 2010-06-08
I am trying to pass a pointer to a linked list to a function.  I want the function to modify the linked list.
In the function, If I print out a member of the structure,it works,but if I try to print in main the program breaks,which leads me to think it has something to do with bad pointers.
Here's the code:

```

typedef struct 
{
    int total;
    int paid;
    Item *items_ordered; 

}Meal;

``````

typedef struct group Group,*Pgroup;

struct group
{
    int n_elements;
    int served;
    Meal *request_meal;
    Pgroup next;

};


``````

void main()
{
    ...
    Pgroup list_group=NULL;
    int n_groups=0;
    Table *table=NULL;
    Group *group=NULL;
    int n_tables=12;

                            n_groups=register_group(&group,&table,n_tables,n_groups,&list_group);
                            printf("%d\n",list_group->n_elements);//breaks
                            ...

    free(group);
 
}

``````

int register_group(Group **group,Table **table,int capacity,int n_groups,Pgroup *list)
{
    int i,num_p;

  

    printf("Type the number of epople in the group:\n");
    scanf("%d",&num_p);
    

    for(i=0;i<capacity;i++)
    {
        printf("%d %d\n",(*table)[i].free,(*table)[i].capacity);
        if((*table)[i].livre && (*table)[i].capacity==num_p)
        {
              n_groups++;
             *group=(Group *) realloc(*group,n_groups*sizeof(Group));
            (*table)[i].suc_groups=group[n_groups-1];
            (*table)[i].free=FALSE;
            (*group)[n_groups-1].n_elements=num_p;
            (*group)[n_grups-1].served=FALSE;
            (*group)[n_groups-1].next=NULL;
            (*group)[n_groups-1].request_meal=NULL;
            return n_groups;
        }
        
    }
        printf("No tables available for that number of people!\n");
        printf("Adding to the queue...\n");
        add_group_list(list,num_p);
                
        
    return n_groups;
}

``````


void add_group_list(Pgroup *ptr_list,int n_people)
{
    Pgroup new1,aux;

    new1=(Group*)malloc(sizeof(Group));

    if(new1 == NULL)
    {
        printf("Error alocating memory\n");
        exit(1);
    }

    if((*ptr_list)==NULL)
    {
        new1->n_elements=n_people;
        new1->served=FALSE;
        new1->request_meal=NULL;
        new1->next=*(ptr_list);
        (*ptr_list)=new1;
    }
    else
    {
        aux=(*ptr_list);
        while(aux->next!=NULL)
            aux=aux->next;
        aux->next=new1;
    }
  

}

```

---

### Post by gmargo on 2010-06-08
**n_groups** is uninitialized. (And never actually gets incremented since it is passed by value not reference.)

What is "Pgroupo" in add_group_list() function?

---

### Post by esmeco on 2010-06-08
Sorry,it was just a mistyping and really forgot to initialize n_groups as 0.But n_groups is incrementing inside the function and is the value returned...

---

### Post by Some Penguin on 2010-06-08
*ignore*

Misread code, my bad.

---

### Post by esmeco on 2010-06-08
I know that n_groups is passed by value instead of reference, but since it's value is incremented in the function **register_group** and returned from the function,which in turn updates the n_groups variable in main,only to be sent again each time the function is called,I thought it worked...

```

**n_groups**=register_group(&group,&table,n_tables,n_groups,&list_group);


```

I've put a printf line on main to check the n_groups variable and is indeed incrementing it's value...

---

### Post by Some Penguin on 2010-06-08
In the following code, the contents of the structure pointed to by new1 are uninitialized (in particular, new1->next can be pointing anywhere), and therefore the behavior of your program upon subsequent list traversals is undefined.

        aux=(*ptr_list);
        while(aux->next!=NULL)
            aux=aux->next;
        aux->next=new1;

---

### Post by esmeco on 2010-06-09
Thanks for the help!It's solved now!

---

### Post by trent.josephsen on 2010-06-09
> **esmeco said:**
> ```
typedef struct group Group,*Pgroup;
```

Please, *please* don't do that.  Hiding a pointer behind a typedef is bad for documentation.  (I'd also advise you to use "struct group" instead of defining a new typedef, but I think I'm the only one who feels that way.)

---

