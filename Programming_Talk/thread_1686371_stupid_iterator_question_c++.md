---
title: "stupid iterator question c++"
date: 2011-02-12
forum: Programming Talk
---

### Post by abraxas334 on 2011-02-12
This may be a very silly question about iterators.

I have a vector defined like this:

[PHP]using namespace std;

vector<int> Vertex (30);
//then i fill the vector with some elements
//Vertex is sorted and unique;

//now I need to find the position of an element with a certain value in the vector

vector<int>::iterator it;

it = find(Vertex.begin(), Vertex.end(), 25)[/PHP]

I want to know at which point in the vector 25 appears, i.e. which value of i between 0 and 29, if I was to go over the vector in this style:
[PHP]for (int i = 0; i<Vertex.size(); i++)
{
    cout<<Vertex[i]<<endl;
} [/PHP]
if i do a cout<<iterator<<*it<<endl; it is is the same as cout<<Vertex[i]<<endl; but what I really want to know for which "i" the iterator returns my value of 25. Is there a simple way of doing it, because i need the position as an int value in order to pass it to a function, otherwise I'll have to rewrite the entire function

---

### Post by MadCow108 on 2011-02-12
if the vector is sorted you should use a binary search like *lower_bound*, *upper_bound* or *equal_range* and not *find*. its much faster
for unique entries *lower_bound* returns the result you want.

to get the position you can use *distance* defined in the iterator header
```
distance(Vertex.begin(), it)
```

---

### Post by abraxas334 on 2011-02-12
binary-search, of course! ok I'll use that instead. 
Thanks for the comment :)

---

### Post by worksofcraft on 2011-02-12
> **abraxas334 said:**
> binary-search, of course! ok I'll use that instead. 
Thanks for the comment :)

I thought you can just subtract vector iterators from each other as if they were pointers:

[php]
int i = find(Vertex.begin(), Vertex.end(), 25) - Vertex.begin();
[/php]

---

### Post by MadCow108 on 2011-02-12
this only works with random access iterators.

the distance function does the same, but works with any iterator.
the complexity depends on the iterator type (O(1) for random access, O(N) for forward iterator etc.)

---

