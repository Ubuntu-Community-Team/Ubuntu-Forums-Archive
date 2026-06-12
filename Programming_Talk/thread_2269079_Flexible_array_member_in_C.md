---
title: "Flexible array member in C"
date: 2015-03-13
forum: Programming Talk
---

### Post by achuthpnr on 2015-03-13
Im trying to learn the concept of flexible arrays in C.  I have a struct containging an array, the length of which is unknown at the time of compilation or is an input parameter. 
 Everything goes well so far, until I run the program. 
It appears that the extra memory allocated to store the array info gets added to the end of the struct. Hence the ouput reads the contents of other members instead of the intended value. 

Is there any way to make the array elements added as if it is a predefined structure with a fixed array size, so that it coule be correctly printed?

Here is the program I have

```

#include<stdio.h>
#include<stdlib.h>

struct table_type
{
    unsigned int a;
    unsigned int b;
    unsigned int c;
    unsigned int d;
    unsigned int e[];
};

struct table_type *table;


int main()
{
    unsigned int i,j;
    unsigned int N=6; // Intended to be read from input

    table=(struct table_type *)calloc(N,(sizeof(struct table_type)+N*sizeof(unsigned int)));

    for(i=0;i<N;i++)
    {
        table[i].a=i;
        table[i].b=i+10;
        table[i].c=i+100;
        table[i].d=i+1000;
        for(j=0;j<N;j++)
            {
                table[i].e[j]=i+j;
            }
    }

    for(i=0;i<N;i++)
    {
        printf("\n");
        for(j=0;j<N;j++)
            printf("i=%u j=%u k=%u\n",i,j,table[i].e[j]);
    }

    return 0;
}



```

The question is how do I properly access table[i].[j]?

---

### Post by spjackson on 2015-03-13
> **achuthpnr said:**
> Is there any way to make the array elements added as if it is a predefined structure with a fixed array size, so that it coule be correctly printed?

No there isn't. You cannot have an array of table_type (syntax error); you can calloc whatever you like and cast it to struct table_type *, but you can't do meaningful pointer arithmetic with the result. &(table[1]) is the same value as &(table[0].e) - ignoring possible alignment issues.

You could declare e as a pointer and calloc (and free) each e, but that's not using a flexible array.

See also [http://stackoverflow.com/questions/3875523/lookup-table-in-c](http://stackoverflow.com/questions/3875523/lookup-table-in-c)

---

### Post by ofnuts on 2015-03-14
In other words an array assumes that all elements have the same size.... So you have two solutions:
1) use an array of  pointers to table_type elements (then you malloc() individual tabe_type items and add their pointer to the array)
2) have table_type not use a flexible array (spjackson's suggestion)

---

### Post by achuthpnr on 2015-03-17
Thanks for the replies.

If I have to keep an array of pointers to each and every element, it seems like double effort when the number of elements is large. 
When and where is this concept of flexible array actually used? Is it designed to be used only with smaller number of elements?

---

### Post by ofnuts on 2015-03-17
Not much difference in programming. Either you use an array of pointers to the whole structure cum flexible array, or you use an array of structures with a pointer to that auxiliary array (same total memory footprint) or you use an array of structures with a fixed array at the maximum size you expect. So it all depends on the size difference between the average array and the maximum array. If this is smaller than the size of a pointer then it would be a more memory-efficient solution.

---

