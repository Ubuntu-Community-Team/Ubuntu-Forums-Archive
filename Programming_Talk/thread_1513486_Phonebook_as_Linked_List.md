---
title: "Phonebook as Linked List"
date: 2010-06-19
forum: Programming Talk
---

### Post by esmeco on 2010-06-19
I'm having some problems here with a phonebook linked list.
I need to search through the linked list in order to determine which 1st letter of a name is the most common.

I have a function which takes a pointer to a linked list as an argument and returns the most common character.
I'm not sure this is the "right" way to do this or if,somehow,there's an easier way to accomplish what I've did.
Here's the code:

```


typedef struct person data, *pdata;

struct person{
char name[100];
char phone[15];
pdata next;
};


``````

char most_common_letter(pdata list)
{

char c=NULL;
pdata actual,previous=NULL;
int counter=0,int largest=0;

actual=list;
previous=actual;

    if(actual==NULL)
       return c;



     while(actual!=NULL)
      {
         counter++;

             if(actual->name[0]!=prev->name[0])
             {
                   if(counter>largest)
                  {
                       largest=counter;
                       c=previous->name[0];
                  }
                  counter=0;
             }
          previous=actual;
         actual=actual->next;
       }

      if(counter>largest)
        c=previous->name[0];

     return c;
  }


```

---

### Post by gmargo on 2010-06-19
Did you have a question?

Three things I notice off the top of my head:
1) Fix your indentation and spacing; it's difficult to read.
2) "actual" is not initialized, so loop will never work.
3) "counter" needs to be maintained on a per-character basis; you obviously can't have only one instance if you plan on making only one pass through the data.  I.E. you need an array of counters.

---

### Post by esmeco on 2010-06-19
Fixed the actual part not being initialized...Why will I need an array of counters?Can't I just go through the whole list counting how many times the 1st letter of a certain name appears an then,when the next letter appears compare the largest number value with the counter's value,to check which is the actual letter with more names in the phonebook?
I'm not sure If my code is supposed to perform what I intend to, or if there is a simplified way to do that,so I wanted you opinions on how to achieve the desired result.

---

### Post by dwhitney67 on 2010-06-20
> **esmeco said:**
> ?Can't I just go through the whole list counting how many times the 1st letter of a certain name appears an then,when the next letter appears compare the largest number value with the counter's value,to check which is the actual letter with more names in the phonebook?

EDIT: Never mind.  Keeping the array of counters would almost certainly be more efficient.

---

### Post by esmeco on 2010-06-20
So,the code is actually correct as it is?

---

### Post by lisati on 2010-06-20
There are multiple answers.

I'd suggest an array of counters. That way you only need to scan the phone list once, which could take a long time if it's a large list. You'd then scan the counter list and return the entry with the highest count.

Another way, which would only work if the list you're scanning is sorted, is to keep a running tally of how many times the "current" character occurs and which is the most common so far. Then when you reach the next letter or the end of the list, you update your "most frequent" tally. When you've reached the end of the list, you can return the "most frequent."

---

### Post by Can+~ on 2010-06-20
This algorithm is flawed, simply because, it depends on a consecutive set of characters to work:

First case:
```
aaabbbb (a:3, b:4)
```

The algorithm will read the first 3 chracters, define a as the most common character as soon as it goes to b, count b, and then set b as the most common character (which is right)

Second case:
```
aaabbbbaa (a:5, b:4)
```

Same as before, b has a count of 4, now it will count two a's, and dismiss them.

This will only work if the list is alphabetically sorted (as lisati pointed out). In fact, the algorithm, per se, is counting the longest continuous sequence of characters.

---

### Post by trent.josephsen on 2010-06-20
The "right" way is not to store a phonebook as a linked list.  That beside the point, please don't hide pointers behind typedef's, and (if you must use typedef) use more descriptive tags than "data" and "pdata".  The purpose of a typedef is to make code *easier* to read.

---

### Post by esmeco on 2010-06-20
The list is ineed alphabetically sorted

---

