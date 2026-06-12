---
title: "What's the best data structure for this simple problem? Constant time lookup desired"
date: 2009-08-21
forum: Programming Talk
---

### Post by SNYP40A1 on 2009-08-21
I have a problem where I want to store pairs of integers ranging from -20 to +20.  So examples would be (-14, 20) or (3, -2).  I want to scan these pairs in from a file and then simply be able to lookup to see if a given integer pair was in the list.  If this only required one integer, I would simply use a set.  However, if I use a set with 2 integers, not sure if I can have constant time lookup as I would need to supply a comparison function.  Anyone see the best way to solve this?

---

### Post by CptPicard on 2009-08-21
A pair of integers is just as sortable as a single integer... use a lexicographic ordering (first order by first item, then by second item). But you should also be aware that if you're using data structures that use comparisons, you're most likely dealing with log n time trees. A constant-time lookup would be achievable by hashing with an appropriate hash function... hashing a pair of integers is not, again, much different from hashing a single integer.

---

### Post by SNYP40A1 on 2009-08-21
Since my dataset will be less than 300, I think I will just use a linear or log(n) search with comparison function.  No need to figure out a complicated hash function.

---

### Post by dribeas on 2009-08-23
If you use a set you will never get constant time lookup, not with an integer, not with an integer pair.

If memory is not a really tough problem, I would recommend using a bidimensional array of 41 elements with each coordinate representing the first and second element in the set offset so that -20 is stored at position 0. The stored value would be a boolean identifying if the pair is present. Size will be 41*41 = 1681 bytes and you will get constant time lookup.

---

### Post by SOULRiDER on 2009-08-23
> **dribeas said:**
> If you use a set you will never get constant time lookup, not with an integer, not with an integer pair.

If memory is not a really tough problem, I would recommend using a bidimensional array of 41 elements with each coordinate representing the first and second element in the set offset so that -20 is stored at position 0. The stored value would be a boolean identifying if the pair is present. Size will be 41*41 = 1681 bytes and you will get constant time lookup.

I was gonna say that!

Just make a 2d array (or matrix or whatever you wanna call it). Adding a value (it could be a boolean in this case) and seeing if a value is rpesent will both be O(1)

---

### Post by Lux Perpetua on 2009-08-24
Exactly. ```
bool hash[41][41] = {{false}};

// To store pair (i,j):
hash[i+20][j+20] = true;

// To look up pair (i,j):
if (hash[i+20][j+20]) {
    // it was in the list
} else {
    // it wasn't in the list
}
```

---

### Post by CptPicard on 2009-08-24
On the other hand, if this is a static set that can be kept sorted, just binary-searching into such a small data set is actually very fast, too -- unless you have an insanely intensive loop you're doing this in or something.

---

### Post by nvteighen on 2009-08-24
> **dribeas said:**
> If you use a set you will never get constant time lookup, not with an integer, not with an integer pair.

If memory is not a really tough problem, I would recommend using a bidimensional array of 41 elements with each coordinate representing the first and second element in the set offset so that -20 is stored at position 0. The stored value would be a boolean identifying if the pair is present. Size will be 41*41 = 1681 bytes and you will get constant time lookup.

Isn't that called an associative matrix? In other words, you're abstracting a graph in an array... quite a good method sometimes; I myself used it a couple of times (without knowing anything about this) :p

---

### Post by WitchCraft on 2009-08-24
Well, the simplest solution would be a fscanf with a large-enough two dimensional array, and then do a mergesort on them.

Another idea that i'd have is std::map
an associative array, so once you have the first part, you will automatically have the second.

However, that doesn't allow for duplicates.

Since you might want to have a dynamic length, 
you can use std::vector with a struct

typedef struct mytype_s
{
    int iTime = 0 ;
    int iValue =0 ;
} mytype_t

then you fill in the values in a struct and push_back the struct.

Once input is finished, you run std::sort on the vector (you have to give std::sort a callback function for sorting).
If you want only one pair each, you can run std::unique (after you run std::sort) and give a callback for equal comparison.

---

