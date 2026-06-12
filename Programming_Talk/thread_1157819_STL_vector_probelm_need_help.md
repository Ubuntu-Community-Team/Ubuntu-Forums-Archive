---
title: "STL vector probelm need help"
date: 2009-05-13
forum: Programming Talk
---

### Post by abraxas334 on 2009-05-13
Hi guys, I have started using the STL recently but I am still a little confused about some things, tho I am sure that with the problem i have at the moment an iterator is the best solution.

My starting point is this: I have a list contained in a vector like this:
```

vector < vector < int > > vList;
vector <int > v(2);
//do something in a for loop 
vList.push_back(v);

```
so in the end i have a vList of say size 1000 (will differ) each with entries like this:
vList[i][0] = small value;
vList[i][1] = bigger value;
//the zero entry is always smaller than the 1 entry and vList is sorted in accending order according to the vList[i][0] entry.

Here comes my problem:
say between i = 0 and i = 20 vList[i][0] and vList[i][1] the respective entries are identical ([i][0] and [i][1] will be different for same i)
e.g 
1 4
1 4
1 4 etc...

what I want to do is count the number of identical entries (doesn't matter if there is just one or 100) and replace the list entry with of say 20 identical entries with 1 single entries. i.e. something like this.
```

v[0] = vList[i][0]; v[1] = vList[i][1]; 
vList.erase(startIterator, endOfIdenticalEntriesIterator);
v.push_back(NumberOfIdenticalEntries) //making v[2] the number of identical entries
vList.insert(v) // insert new v instead of the 20 identical entries at the point in vector.

```
so we end up with instead of
vList [i=1...20][0] = 1 and vList[i=1...20][1] = 4
I get something like vList[i][0]=1 vList[1][1] = 4 vList[1][2] = 20 // or how many ever elements have been erased from the vector.

So basically by the end of it I would like to get rid of all the duplicates in the vector, making it smaller but retaining the information on how many of the same elements where in it originally. Hope this made some kind of sense. I think my main problem is that I don't quite understand how i could get a 2 d iterator to work, as the iterator obviously must be the same as the vector it is iterating over. Any help would be greatly appreciated :) (BTW i can solve it copying vector elements and stuff but I'd really like to get the hang of iterators)
Thanks

---

### Post by dwhitney67 on 2009-05-13
Personally, I would have employed the use of a multimap instead of the vector within a vector approach.

The multimap sorts the entries based on the key, so that meets one of your criteria.  As for removing duplicates, whether it be from a multimap or a vector, one needs to understand that to do it in a loop requires care.  This is because if you are looping on the premise of using the iterator as your marker to determine when to end the loop, this iterator becomes useless should you remove an entry.

Here's some code using a multimap that mimics your task scope.  It probably could be made more efficient with some fancy algorithm embedded in the bowels of the C++ STL documentation, so bear with my "verbose" way of doing things:

EDIT:  There is a bug in the code; I will try to sort it out, and post the corrected solution later.

```

#include <map>
#include <iostream>
#include <algorithm>


void displayValue(const std::pair<int, int>& v)
{
  std::cout << v.first << ", " << v.second << std::endl;
}

int main()
{
  std::multimap<int, int> mm;

  mm.insert(std::make_pair(1,2));
  mm.insert(std::make_pair(1,2));
  mm.insert(std::make_pair(1,2));
  mm.insert(std::make_pair(2,4));
  mm.insert(std::make_pair(2,4));
  mm.insert(std::make_pair(2,4));
  mm.insert(std::make_pair(2,4));
  mm.insert(std::make_pair(2,4));
  mm.insert(std::make_pair(3,6));

  std::cout << "original set:\n";
  std::for_each(mm.begin(), mm.end(), displayValue);


  while (true)
  {
    std::multimap<int, int>::iterator it1;
    std::multimap<int, int>::iterator it2;
    std::pair<std::multimap<int, int>::iterator, std::multimap<int, int>::iterator> ret;

    for (it1 = mm.begin(); it1 != mm.end(); ++it1)
    {
      bool dupeFound = false;

      ret = mm.equal_range(it1->first);

      for (it2 = ret.first; it2 != ret.second; ++it2)
      {
        if (it2 == ret.first) continue;  // keep the first found

        dupeFound = true;

        mm.erase(it2);   // delete the duplicates
      }

      if (dupeFound) break;
    }

    if (it1 == mm.end()) break;
  }

  std::cout << "condensed set:\n";
  std::for_each(mm.begin(), mm.end(), displayValue);
}

```

---

### Post by dwhitney67 on 2009-05-13
Below is the corrected code.  It seems in my first attempt, I did not heed my own advice to be careful about reusing the iterator once I deleted an entry from the multimap.  I discovered the bug when I inserted a duplicate record at the end of the map.  Anyhow, the code below works, albeit it is by no means efficient.

```

#include <map>
#include <iostream>
#include <algorithm>

void displayValue(const std::pair<int, int>& v)
{
  std::cout << v.first << ", " << v.second << std::endl;
}

int main()
{
  std::multimap<int, int> mm;

  mm.insert(std::make_pair(1,2));
  mm.insert(std::make_pair(1,2));
  mm.insert(std::make_pair(1,2));
  mm.insert(std::make_pair(2,4));
  mm.insert(std::make_pair(2,4));
  mm.insert(std::make_pair(2,4));
  mm.insert(std::make_pair(2,4));
  mm.insert(std::make_pair(2,4));
  mm.insert(std::make_pair(3,6));
  mm.insert(std::make_pair(3,6));
  mm.insert(std::make_pair(3,6));

  std::cout << "original set:\n";
  std::for_each(mm.begin(), mm.end(), displayValue);


  while (true)
  {
    std::multimap<int, int>::iterator it1;
    std::multimap<int, int>::iterator it2;
    std::pair<std::multimap<int, int>::iterator, std::multimap<int, int>::iterator> ret;

    for (it1 = mm.begin(); it1 != mm.end(); ++it1)
    {
      ret = mm.equal_range(it1->first);

      it2 = ret.first;

      ++it2;  // skip the original that we want to preserve

      if (it2 != ret.second)
      {
        mm.erase(it2);   // erase the duplicate
        break;
      }
    }

    if (it1 == mm.end()) break;
  }

  std::cout << "condensed set:\n";
  std::for_each(mm.begin(), mm.end(), displayValue);
}

```

---

### Post by abraxas334 on 2009-05-13
> **dwhitney67 said:**
> Below is the corrected code.  It seems in my first attempt, I did not heed my own advice to be careful about reusing the iterator once I deleted an entry from the multimap.  I discovered the bug when I inserted a duplicate record at the end of the map.  Anyhow, the code below works, albeit it is by no means efficient.




Thank you, that is exactly what i was looking for. Must say I have never used Multimaps but they seem rather useful, my C++ book somehow decided to omit these (That's what you get from learning stuff from just one book).
Efficiency is a different story I guess. I am still at the stage of things where I want stuff to work and worry about efficiency later.
Thanks a lot :)

---

### Post by stevescripts on 2009-05-13
> **abraxas334 said:**
> ...
Efficiency is a different story I guess. I am still at the stage of things where I want stuff to work and worry about efficiency later.
Thanks a lot :)

In general, getting it to work first is a good plan.

Premature optimization is ... evil ... ;)

Steve

---

### Post by kknd on 2009-05-13
You are reinventing the wheel. You can use the unique() function from <algorithm>:

[PHP]
unique(start_iter, end_iter [, custom_compare_func]);
[/PHP]

If I remember well, the container must be sorted before calling unique.

---

### Post by dwhitney67 on 2009-05-13
> **kknd said:**
> You are reinventing the wheel. You can use the unique() function from <algorithm>:

[PHP]
unique(start_iter, end_iter [, custom_compare_func]);
[/PHP]

If I remember well, the container must be sorted before calling unique.

Please show how to use this with a multimap.

---

### Post by abraxas334 on 2009-05-14
> **kknd said:**
> You are reinventing the wheel. You can use the unique() function from <algorithm>:

[PHP]
unique(start_iter, end_iter [, custom_compare_func]);
[/PHP]

If I remember well, the container must be sorted before calling unique.

yeah have used unique before but i need to know how many of each duplicate element i get rid of, so Ill still have to do some sort of awkward counting. 
If unique worked with multimaps that would be great! Does it?

---

### Post by kknd on 2009-05-14
> **abraxas334 said:**
> yeah have used unique before but i need to know how many of each duplicate element i get rid of, so Ill still have to do some sort of awkward counting. 
If unique worked with multimaps that would be great! Does it?

Ah, I answered this based on the first post. I didn't saw the new requirements.

---

