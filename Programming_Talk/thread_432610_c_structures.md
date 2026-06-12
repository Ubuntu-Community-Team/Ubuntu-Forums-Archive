---
title: "c structures"
date: 2007-05-04
forum: Programming Talk
---

### Post by jmwalloh on 2007-05-04
**how do you declare and name a structure in c that probably has about 5 elements and how do you declare a pointer to a structure also like in linked lists and double linked lists**:confused:

---

### Post by aquavitae on 2007-05-04
```

typedef struct {
   int element1;
   float element2;
  // etc...
} MyStruct;

MyStruct a_struct;

MyStruct* pointer_to_a_struct = &a_struct;

```

Hope this helps.

---

### Post by phossal on 2007-05-04
I do it a little differently.

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h> /* Includes for good measure : ) */


struct vehicle_struct {
        char name[30];
        int engines;
        int passengers;
};

typedef struct vehicle_struct vehicle;

int main(int argc, char * argv) {
        vehicle car;
        vehicle *car_ptr = &car; /* *car_ptr points to car ? */

		strcpy(car.name, "Ferrari");
		
		printf("Vehicle: %s\n", car.name);
		printf("Vehicle_ptr: %s\n", (*car_ptr).name);
		
        return(0);
};

```

---

### Post by Wybiral on 2007-05-05
Here's a singly linked list. Basically you just need to have a pointer of the structures own type inside itself (so that it can contain a pointer to the next element).

This one uses a simple "push" or "prepend" style append since it's the easiest. Just create a pointer to the top link, create a new link and set it's "next" pointer to the link that used to be on top... Then place the new one on top. The same effect as "pushing" something onto a stack.

Dynamic data like this requires dynamic memory allocation, so there is a "free_list" function to clean up.

```

#include <stdlib.h>
#include <stdio.h>

struct list_t
{
   int data;
   struct list_t *next;
};
typedef struct list_t list;

void push(list **link, int data)
{
   list *temp = (*link);
   (*link) = (list*)malloc(sizeof(list));
   (*link)->data = data;
   (*link)->next = temp;
}

void print_list(list *link)
{
   while(link)
   {
      printf("%i\n", link->data);
      link = link->next;
   }
}

void free_list(list *link)
{
   list *next;
   while(link)
   {
      next = link->next;
      free(link);
      link = next;
   }
}

int main()
{
   list *my_list = NULL;
   push(&my_list, 10);
   push(&my_list, 20);
   push(&my_list, 30);
   print_list(my_list);
   free_list(my_list);
   return 0;
}

```

---

### Post by hod139 on 2007-05-05
> **Wybiral said:**
> 
<snip>
```

void push(list **link, int data)
{
   list *temp = (*link);
   (*link) = (list*)malloc(sizeof(list));
   (*link)->data = data;
   (*link)->next = temp;
}

```
<snip>

To hopefully save future headaches, note that link is passed as a pointer to the list pointer (list **).  This is **very** important.  Even though the code will compile if you pass only a list*, you will be allocating memory for a copy of the list, not the actual list, and you will get a runtime seg fault.

---

### Post by Wybiral on 2007-05-06
Yeah, it's meant to use list pointers, passed by reference...

```

   push(&my_list, 10);
   push(&my_list, 20);
   push(&my_list, 30);

```

Where "my_list" is "list*"

It's because it's "prepend"ing them and the "top" changes. Whereas this wouldn't be a problem if you were appending to the end, where the top remains the same. This is really more of a stack then a list... But it should illustrate the core concepts he was asking about (pointing to it's own kind in a list-like structure)

---

