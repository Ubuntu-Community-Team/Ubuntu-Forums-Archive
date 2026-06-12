---
title: "how to replace line from file."
date: 2007-11-29
forum: Programming Talk
---

### Post by EzarKun on 2007-11-29
Hi,
C++ newb here.

Ok, so this is for an assignment. I am suppose to read a csv file, and also be able to modify it.

the file looks like this

```
54321,123,543.32
12334,543,678945.34
etc...
```

the first field is account number, second is PIN, and the third is amount in account.

Imagine I was to withdraw from the second account - 12334, I read from the second line, and store the amount in a temp. How would I replace that whole amount again?

Thanks for any suggestions in advance.

---

### Post by Modred on 2007-11-29
In general, because a text file stores information as characters and each character takes up (normally) one byte of space, different sized numbers take different amounts of storage space to represent.  Because of this, using random access on the file would almost certainly result in unreliable behavior, so you simply read everything in order and then print out the entire file again with the new values.

---

### Post by slavik on 2007-11-29
> **Modred said:**
> In general, because a text file stores information as characters and each character takes up (normally) one byte of space, different sized numbers take different amounts of storage space to represent.  Because of this, using random access on the file would almost certainly result in unreliable behavior, so you simply read everything in order and then print out the entire file again with the new values.

I will second this advice. :)

---

### Post by EzarKun on 2007-11-29
I will do this cause its just an assignment and the files will be small.
But could you tell me how its done in the real world, cause the part where I will store everything into an arrays seems really inefficient.

Thanks for the suggestion thou.

---

### Post by slavik on 2007-11-29
in the "real world" such data belongs in a database. (that is to say, the current real world) believe it or not, but long ago, databases were nothing more than flat files (hence the reason for creation of AWK).

if it had to be read from a file, it would probably be stored in a linked list. :)

---

### Post by smartbei on 2007-11-29
Well EzarKun, you could read the file line by line, perform the operation on a single line, write it to the output file, and then load the next line into the same buffer. In terms of memory that is more efficient than reading the whole file into RAM (O(1) instead of O(n)).

---

### Post by Modred on 2007-11-29
> **smartbei said:**
> Well EzarKun, you could read the file line by line, perform the operation on a single line, write it to the output file, and then load the next line into the same buffer. In terms of memory that is more efficient than reading the whole file into RAM (O(1) instead of O(n)).

A more common practice would be to read in sizable chunks and then parse the records from a pool of cached data.  You need to add some checks to ensure you get complete records off the end of a block, but in terms of disk I/O it's much more efficient than a line-by-line or record-by-record solution.

---

