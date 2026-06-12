---
title: "Sorting int variables in ascending order in c"
date: 2005-11-26
forum: Programming Talk
---

### Post by ItsMe1989 on 2005-11-26
[COLOR="Navy"][FONT="Trebuchet MS"]Hi,

I have a selection of variables with random numbers generated and stored in ints. What i want to do is sort these into ascending order.

I'm not sure how to do this in c, and any help would be appreciated.

Many Thanks[/FONT][/COLOR]

---

### Post by gord on 2005-11-26
[http://en.wikipedia.org/wiki/Sorting_Algorithm](http://en.wikipedia.org/wiki/Sorting_Algorithm) has a good few algorithms showing you how to sort data :)

---

### Post by ItsMe1989 on 2005-11-26
Thanks... could use a bit more help if possible!

I have 7 variables, which would you suggest to be the best?

Thanks

---

### Post by gord on 2005-11-26
well im gonna assume that they are in an array n use bubble sorting (the easyest but most inefficient varient.. but for 7 values who cares? ;))

```
 
void sortarray(int* myarray) {
  bool foundsort = True;
  int tmpvalue;
  while (foundsort == True) {
    foundsort = False;
    for (int i = 0; i <= 6; i++) {

      if (myarray[i] <= myarray[i+1]) {
        foundsort = True;
        tmpvalue = myarray[i];
        myarray[i] = myarray[i+1];
        myarray[i+1] = tmpvalue;
      }

    }
  }
}

```

i appologise for any mistakes and bugs and all that junk, its getting late and im a little ill ;) but hey, finding bugs is the greatest part. if you goto the wikipedia article and read up on bubble sorting you should be able to follow whats going on. 

but basically, it itterates through the array if int's, if myarray[i+1] is greater than myarray[i], it swaps the two values around.
it keeps doing this until no values get swapped around. thus the greatest value is at myarray[0] and the largest at myarray[6]

---

### Post by toojays on 2005-11-26
If you don't want to write your own sort function, you can use the qsort() function. Here's a complete example that does what you want:```
#include <stdio.h>
#include <stdlib.h>

int array[] = {5, 4, 3, 2, 1, 6, 0};

int compare_ints(const void *a, const void *b)
{
  const int *ia = (const int *) a;
  const int *ib = (const int *) b;
  
  return (*ia > *ib) - (*ia < *ib);
}

void print_array()
{
  int i;
  printf("  [ ");
  for (i = 0; i < sizeof(array)/sizeof(int); i++) {
    printf("%d ", array[i]);
  }
  printf("]\n");
}

int main()
{
  printf("Initial array:\n");
  print_array();
  qsort(array, sizeof(array)/sizeof(int), sizeof(int), compare_ints);
  printf("After sorting:\n");
  print_array();
  return 0;
}
```

---

### Post by ItsMe1989 on 2005-11-27
Actully they were not in an array, but could be if this was the simpler way of doing it?

---

### Post by baRRacuda on 2005-11-27
It's better to keep them in an array than to keep in different variables like x,y,z... It'll shorten your algorithm and it'll be easier to reach each one. As **gord** says, bubble sort might be the worst algorithm to sort, but it's the easiest to keep in mind.

---

### Post by cactus on 2005-11-27
Linux forums... helping students do their homework since 1998. 
;)

---

### Post by ItsMe1989 on 2005-11-27
How is this homework... its just a stage in me learning C.

---

### Post by cactus on 2005-11-27
was a joke, my apologies.
/me bows and tips hat

---

### Post by otake-tux on 2005-11-27
input the numbers into an array then do a bubble sort.

since you know the # of integers comming, assuming input is comming from the keyboard:

int myarray[6];
for (int i=0;i<6;i++)
{
         scanf(%i,myarray[i]);
}
then just send myarray to a bubble sort function.

---

### Post by zimmergage on 2012-09-27
I need to find sort arry: Sorts an array a of size s in ascending order return 0 if everything goes OK

return -1 if it is not

starts with

int SortArray( int a[], int s);

no bool

---

### Post by overdrank on 2012-09-27
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

