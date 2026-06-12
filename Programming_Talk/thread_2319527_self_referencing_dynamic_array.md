---
title: "self referencing dynamic array"
date: 2016-04-05
forum: Programming Talk
---

### Post by achuthpnr on 2016-04-05
A structure is having a self seferencing node, which is an array of  pointers. Since the pointer array needs to have the same number of  elements as in the structure, it is not possible to expilcitly define  the number of elements. So, the dynamic array needs to be used. So far, I  have made the following

```

struct list
{
    unsigned long int a,b,c;
    struct list **ptr_my_list; 
    ......
};

struct list *my_list;

my_list=calloc(N,sizeof(struct list)); //unsigned long int N is read from the input

for(i=0;i<N;i++)
    my_list[i].ptr_my_list=calloc(N,sizeof(struct list *));
    
if((my_list+i)->ptr_my_list[j]=my_list+k)
{
    //do something
    ....
}

```

It is giving expected correct results. Being self learned, I just need to verify this is the correct way of doing this. Thanks

---

### Post by Chuck_McManis on 2016-04-06
Not really. Not sure what you are trying to achieve. You have allocated N structures, and then you have allocated another array of N pointers to structures, and then you've put pointers in the second array which point to structures in your first array. Why the second array? Why not just 

struct list {
    uint32_t a, b, c;  /* really recommend standard int types for portability */
    struct list *another_node;
}  *my_list;

my_list = callloc(N, sizeof (struct list)); /* now you have 'n' structures */
for (i = 0; i < N; i++) {
    (my_list + i)->another_node = (my_list +i); /* points it back at self */
}

There are a whole bunch of interesting data structures you can build, linked lists, doubly linked lists, b-trees, etc. What are you trying to actually build? And why?

---

### Post by achuthpnr on 2016-04-07
The idea is to have N subgroups, each could contain maximum of N elements and the odering matters. OR Imagine it as N shuffling process and each pointer array describes the oder of their arrangement. Basically
```

struct list
{
    unsigned long int a,b,c;
    struct list *ptr_my_list[N]; 
    ......
};

```
would be sufficient. However, since N is an input this is not possible to compile the code. The first post is the way I could think of to squeeze everything together to a single structure.

 Of course it could be done in two parts without directly linking the array of pointers to the structure, which I am not interested in for the moment.

---

