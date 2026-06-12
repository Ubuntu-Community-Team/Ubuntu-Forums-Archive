---
title: "N-d array permutation to 1d array index"
date: 2007-07-04
forum: Programming Talk
---

### Post by [h2o] on 2007-07-04
I have a multidimensional vector which contain indices (it is a subset of a larger multidimensional vector).
```

A = [ 
 [1, 3, 5], 
 [4, 6],
 [1, 2, 5, 6]
]

```

I want to use these indices to index a 1-d array of 1/0:
```

B = [ 1 0 0 0 1 1 1 1 0 0 0 ...]

```

The goal is to get the number of 1's in the particular subset.
In this example I want:
```

sum = B[ (1,4,1) ] + B[ (1,4,2) ] + B[ (1,4,5) ] + ... + B[(5,6,5)] + B[ (5,6,6) ]

```

The size for array A is not known at compile time. It can have 1 to 4 rows where each row can have an arbitrarly number of elements.

**How do I go about iterating over A to get the sum of B for my subset A?**

I am using C++ with A being a *std::vector<int> and B a *bool.

---

### Post by Soybean on 2007-07-04
Well... I'm a little confused about a couple of key points here. I'm not really clear on what data type A and B are (is A a pointer to a dynamically allocated array of std::vector<int>s?), and I don't entirely understand what you're trying to do with B.

However, despite the fact that I have almost no idea what's going on,  it seems to me like your main challenge is that you want a nested loop, where the depth of the nesting is the same as the number of vectors in A. Does that sound right? If so, I can think of two ways of doing it.

The first way is ugly and terrible, but easy to understand. Since A has a maximum of 4 vectors, just make 4 nested loops and disable the inner loops if they're not needed. Something like
```

for(int i=0; i < A[0].size(); ++i)
{
      for(int j=0; NUMBER_OF_VECTORS > 1 && j < A[1].size(); ++j)
      {
               ...etc
      }
}

```
where NUMBER_OF_VECTORS is a variable, of course. Oh, and you should probably use a std::vector<int>::iterator instead of an int for the index, but I'm assuming you're good with iterating straight through a single vector.

The other option is much better, and that's a recursive function. The function would loop through all elements in a single vector in A, and in each loop iteration, it would call itself for the next vector. Recursive functions can be difficult to get your head around, but this option is much cleaner and more scalable.

Sorry for being so vague, but like I said, I'm a little confused. ;) Good luck!

---

### Post by [h2o] on 2007-07-05
Yeah, the problem is a bit complex and hard to understand, so sorry for not making it clearer.

I actually solved it with a recursive function. Thanks for the advice :)

---

