---
title: "Differance between Hash Table and Array"
date: 2009-04-06
forum: Programming Talk
---

### Post by Pyro.699 on 2009-04-06
Hello,

Im helping a friend out with a entrance level java course and hes come to the final assignment and we are both stumped on one of the questions and thought that i would ask here. The question is asking for the difference between an Array and a Hash Table and what Java Class uses it. Normally asking for answered to an assignment is a last resort, but I've looked through all my textbookx, reviewed his notes and searched the internet. Any help would be greatly appreaiated

The question again is:

[LIST=1]
[*]What is a Hash Table and what Java Class uses it
[*]What is the differance between a Hash Table and an Array
[/LIST]
The assignment is due tuesday.

Thanks
~Cody Woolaver

---

### Post by col48 on 2009-04-06
Hash table (I can't help with Java)

Suppose you are a big company and want to store a database table (which is really an an array in another form) which has millions of rows on disk.  It will be accessed frequently by many users simultaneously online

You want to optimise disk access. This is achieved in part to spreading the table rows as evenly as possible across the allocated disk space.

One way to do this is to take the key data in each row (say an insurance policy number) and apply a HASHING ALGORITHM (which amounts to enciphering it) to decide where to store the row.  When you want to retrieve the data you use the same algorithm to find it.

In the real world there are more bells and whistles needed but I hope that explains the principle.

---

### Post by Tony Flury on 2009-04-06
The idea of a Hash algorithm is to create a enCoded version of your key value, to speed up retrieval.

The Hash encoding is normally one-way - you can take a key and produce a Hash value, but for most Hash algorithms you can't take the hash value and get the unique Key. However even with a large data set, the intention should be that your Hash algorithm results in only a small number of "collisions" (a collision being where two Keys produce the same Hash value).

As col48 said Hash value are often used to help optimise data retrieval, as you can store the data in Hash value order, making it very easy to take a key value, translate to its hash, and find the Hash value in your data.

A hash table is normally designed to be sparsely populated (if you wrote down a list of all possible Hash values, and marked which ones actually get used there would be significant gaps in the list between Hashes that actually get used). In fact in your program only Hash values that are actually used get allocated into storage, unused Hash values simply don't exist).

An array on the other hand are generally designed to be sequentially accessed (one item after another), or accessed in a direct index based way), and normally arrays are designed to densely populated - i.e. most if not all of the Array has data in it. In most Array implementations, all possible Array "cells" are allocated in storage, meaning they can be massively in-efficient if you only need a smaller numbers of cells from a big range.

---

### Post by kpatz on 2009-04-06
Long story short, a hash table uses a key to access the elements within.  An array uses a subscript (numeric index).

So, a hashtable may have values stored with various values as keys.  For example, say you have an array of employee job descriptions.

```

  employeename[0] = 'Harry';
  employeedesc[0] = 'Manager';

  employeename[1] = 'Sally';
  employeedesc[1] = 'Cashier';
  (and so forth)

```

If you wanted to look up Sally's description, you would have to search through the employeename array to find the correct index for her description (1).

A hashtable lets you store the description by the name, so that employeedesc['Sally'] would return 'Cashier' instead of having to use a numeric index.

---

### Post by simeon87 on 2009-04-06
> **kpatz said:**
> Long story short, a hash table uses a key to access the elements within.  An array uses a subscript (numeric index).

So, a hashtable may have values stored with various values as keys.  For example, say you have an array of employee job descriptions.

```

  employeename[0] = 'Harry';
  employeedesc[0] = 'Manager';

  employeename[1] = 'Sally';
  employeedesc[1] = 'Cashier';
  (and so forth)

```

If you wanted to look up Sally's description, you would have to search through the employeename array to find the correct index for her description (1).

A hashtable lets you store the description by the name, so that employeedesc['Sally'] would return 'Cashier' instead of having to use a numeric index.

This is not what defines a hash table: what you're describing can also be an associative array (which can be implemented without hashing). It's only a hash table when a hash function is used on the key that's used to look something up. It doesn't matter whether this key is an integer, a string or an arbitrary object, as long as it is hashed to a value (which is then used to look it up in the internal datastructure of the hashtable, usually an array).

---

