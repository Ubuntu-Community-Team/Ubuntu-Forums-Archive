---
title: "Maybe someone can spot where I'm going wrong with this code"
date: 2009-02-07
forum: Programming Talk
---

### Post by lswest on 2009-02-07
Okay, well I'm working on my python skills, and I'm trying to take two lists, one containing all the prime factors and their maximum occurrence in a series of numbers (current list is from 1-20), and the other containing just the prime factors (no duplicates), and, using the second list, store the maximum consecutive occurrences of a value in a list called "count" corresponding to the place of the uniqvalue list.  The final two lists should look like:
```
[1, 2, 3, 5, 7, 11, 13, 17, 19] #uniqvalues
[1,4,2,1,1,1,1,1,1]#count
```

The temp_list contains the prime factor, and then the number of consecutive occurrences per value in the range (so from 1-20).  Read: each value of the range is taken and factored into primes, and each consecutive occurrence of a prime factor *for that current value in the range* is stored in a position by itself in the temp_list.

the two lists are:
```
[1, 1, 2, 1, 3, 1, 2, 2, 5, 1, 2, 1, 3, 1, 7, 1, 2, 3, 3, 2, 2, 1, 5, 1, 11, 1, 2, 2, 3, 1, 13, 1, 2, 1, 7, 1, 3, 1, 5, 1, 2, 4, 17, 1, 2, 1, 3, 2, 19, 1, 2, 2, 5, 1]#temp_list
[1, 2, 3, 5, 7, 11, 13, 17, 19] #uniqvalues
```
the code I have written is as follows:
[PHP]for x in uniqvalues: #find maximum consecutive occurrence of a value by iterating through the list of prime factors
    while c < len(temp_list):#iterate through the consecutive occurrences loop
        if x==temp_list[c]:#if the prime factor is equal to x
            temp=temp_list[c+1]#set a temporary count value
            if temp > count[c/2]:#if the temporary count value is greater than the current count value
                count[c/2]=temp#replace them
        c+=2
print count[/PHP]

However, the resulting "count" list is this:
```
[1, 0, 0, 0, 0, 0, 0, 0, 0]
```
(I set the count list to 0, and the same length of the uniqvalue list, in order to simplify my loops)

If anyone needs any more info, has any questions, I will post any more info or code that is needed.

To summarize the problem again in case I lost you above: I would like someone to point out where my mistake is with the python code, since it seems to only iterate through the loop once.

Thanks for any help,
Lswest

*edit* don't know if it matters but I am compiling it using python 2.6

---

### Post by JohnFH on 2009-02-07
It looks like you need to re-initialise c for each x, so:
```

for x in uniqvalues:
    c = 0;
    while c < len( ....

```

---

### Post by lswest on 2009-02-07
That's true, I feel silly for not having noticed, however, I'm running into out of bounds errors.  I should be able to sort that out though.  Thanks for the quick reply!

Thanks, got it sorted and working!

---

