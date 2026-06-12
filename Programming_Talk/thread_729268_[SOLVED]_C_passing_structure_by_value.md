---
title: "[SOLVED] C passing structure by value"
date: 2008-03-19
forum: Programming Talk
---

### Post by S15_88 on 2008-03-19
I was wondering if this makes sense.  I need to pass a structure to some functions that perform their respective tasks as the memory cannot be free'ed until the user ends the program.  is that the most logical thing to do is to keep feeding information into the structure and passing it to the functions?

I'm not 100% sure on whether my code is ok, with respect to passing the structure:

```

struct node 
{
    char *name;
    int  age;
    struct node *nextName;
    struct node *nextAge;
};

typedef struct node NODE;

void addStruct(NODE *info)
{

    if (drain_stdin() != EOF )
    {
        printf("Enter name: ");
        fgets(info->name, MAX_LEN + 1, stdin);
    }
    else
    {
        printf("An Error Has Occured\n");
    }
    printf("Enter age: ");
    scanf("%d", &info->age);
}

int main(void)
{
    NODE *info;
    info = malloc(sizeof(NODE));
    info->name = malloc(sizeof(char)*MAX_LEN);

    addStruct(&info);
}


```

I only included the code that i felt neccessary.

i'm getting:
 warning: passing argument 1 of ‘exit’ from incompatible pointer type

for all the function calls.
.

Thanks, ALain

---

### Post by mike_g on 2008-03-19
I think you might want to leave out the & when calling addStruct. IE:
```
addStruct(info);
```

Edit:
The content of your struct looks as if its going to form a node on a list. Since each node holds both name and age you should only require one pointer linking to the next node.

---

### Post by S15_88 on 2008-03-19
that did the trick thanks, and the reason i have two pointers is because i need it to be sorted by name and age in one list, so the name pointer will sort the list by name then the number pointer will sort the list by age.

Thanks for the help with passing the structure!

ALain

---

### Post by mike_g on 2008-03-19
Fair enough, although I think it may be to simpler to code by having one link pointing to the next node. Then re-sort the list when you want to change how its sorted by. Just an idea.

---

### Post by S15_88 on 2008-03-19
ya it would be a good idea to do it that way, but unfortunately this is a school assignment and the prof gave us this structure to work with:
> 
struct node {
   char *name;
   int  age;
   struct node *nextName;
   struct node *nextAge;
};


---

