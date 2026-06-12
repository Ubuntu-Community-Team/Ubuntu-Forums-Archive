---
title: "[SOLVED] c++ pointers dynamic arrays  quick question."
date: 2007-09-03
forum: Programming Talk
---

### Post by sillv0r on 2007-09-03
First quick question, is there a difference between these two declarations:

```
char* pOne[];


char** pOne;
```


Second question:

I'm storing a group of strings using an array of pointers:

```
char** temp = new char*[oldSize+1];

for(int i=0;i<oldSize;i++)
{
  temp[i] = new char[30];  // lines of interest
  temp[i] = ptrToAnArray[i]; 
}
```

The two lines marked as 'lines of interest,' are these going to do what I think?

As in will the array that is pointed to by 'ptrToAnArray[i]' be copied into the memory block that temp[i] is pointing to?  

Or is the address pointed to by temp[i] going to now be pointing to the address that ptrToAnArray[i] was pointing to?


(I could probably just as easily type up a program to answer my second question, but I figured if someone knows off the top of their head there's no harm in asking.)

I tried to be complete in my question, but if something doesn't make sense let me know.

---

### Post by thumper on 2007-09-03
> **sillv0r said:**
> First quick question, is there a difference between these two declarations:

```
char* pOne[];


char** pOne;
```

Not really.

> **sillv0r said:**
> Second question:

I'm storing a group of strings using an array of pointers:


Don't do that.  Since you are using C++, use std::string and std::vector.

> **sillv0r said:**
> 
```
char** temp = new char*[oldSize+1];

for(int i=0;i<oldSize;i++)
{
  temp[i] = new char[30];  // lines of interest
  temp[i] = ptrToAnArray[i]; 
}
```

The two lines marked as 'lines of interest,' are these going to do what I think?

As in will the array that is pointed to by 'ptrToAnArray[i]' be copied into the memory block that temp[i] is pointing to?  

Or is the address pointed to by temp[i] going to now be pointing to the address that ptrToAnArray[i] was pointing to?

(I could probably just as easily type up a program to answer my second question, but I figured if someone knows off the top of their head there's no harm in asking.)

I tried to be complete in my question, but if something doesn't make sense let me know.

None of the contents of a pointer are copied when assigning pointers.  What you are doing is allocating memory and then overwriting the only pointer you have to that allocated memory with something else.

Unless you really like pain, use the standard library.

---

### Post by sillv0r on 2007-09-03
Thanks,  I was kind of shying away from the std library.  Don't know why.  

Perhaps I needed speed, but maybe there isn't much of a performance difference.  -- heck perhaps the std library is simply doing what I'm doing...  Heh, I guess when I initially worked with c++ , we wrote our own linkedlists/hashtables/vector/string classes.   So when I started again, it was only natural for me to go that route. 

*cough*  sorry for the tangent.

I'll look into the std library again.

Much appreciation!  :KS

---

