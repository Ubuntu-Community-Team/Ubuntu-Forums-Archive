---
title: "finding items that occur more than once in a vector"
date: 2011-05-07
forum: Programming Talk
---

### Post by LMHmedchem on 2011-05-07
I have some vectors to evaluate and develop a list of values that occur in more than one element.

This is the simplest case. I have a vector,
```

std::vector<int> vec1;
vec1[0]=5;
vec1[1]=5;

```I need to know that that 5 occurs twice in the vector. If I do a double loop,
```

std::vector<int> occurs_twice;

for (i=0; i<vec1.size(); i++) {
   for (j=0; j<vec1.size(); j++) {
      if(vec1[i] == vec1[j]){
         occurs_twice.push_back(vec1[i]);
      }
   }
}

```The vector occurs_twice contains the value 5 in four elements.
```

occurs_twice[0]=5;
occurs_twice[1]=5;
occurs_twice[2]=5;
occurs_twice[3]=5;

```I have identified the repeat value, but I don't have a unique list. I suppose I could check and see if 5 is already a member of occurs_twice before adding it.
```

for (i=0; i<vec1.size(); i++) {
   for (j=0; j<vec1.size(); j++) {
      if(i != j && vec1[i] == vec1[j]){
         // check if vec1[i] is already on the list
         m = 0;
         for (k=0; k<occurs_twice.size(); k++) {
            if(occurs_twice[k] == vec1[i]){ m++; }
         }
         if(m == 0) { occurs_twice.push_back(vec1[i]); }
      }
   }
}

```This works, and could be cleaned up so it stops checking when m != 0, etc, but I expect there is a more efficient way to do this. Is there a library function to give values that occur more than once in a vector, or a function that would take my occurs_twice vector and return only the unique elements?

Thanks,

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by dwhitney67 on 2011-05-07
Iterate through the vector, and for each value, at it to a multiset.

Here's the brute-force way; beer is on my mind, not working on "silly" problems.  I'm sure there is a better way to do this.
```

#include <vector>
#include <set>
#include <iostream>

int main()
{
   int                data[] = { 10, 20, 30, 30, 30, 40, 50, 50, 60, 60, 60, 70 };
   std::vector<int>   vec(data, data + 12);
   std::multiset<int> mset;

   for (std::vector<int>::const_iterator it = vec.begin(); it != vec.end(); ++it)
   {
      mset.insert(*it);
   }

   for (std::multiset<int>::const_iterator it = mset.begin(); it != mset.end(); ++it)
   {
      std::cout << *it << " occurs " << mset.count(*it) << " times." << std::endl;

      for (size_t i = 1; i < mset.count(*it); ++i, ++it);
   }
}

```

---

### Post by LMHmedchem on 2011-05-07
> **dwhitney67 said:**
> Iterate through the vector, and for each value, at it to a multiset.

Here's the brute-force way; beer is on my mind, not working on "silly" problems.  I'm sure there is a better way to do this.
```

#include <vector>
#include <set>
#include <iostream>

int main()
{
   int                data[] = { 10, 20, 30, 30, 30, 40, 50, 50, 60, 60, 60, 70 };
   std::vector<int>   vec(data, data + 12);
   std::multiset<int> mset;

   for (std::vector<int>::const_iterator it = vec.begin(); it != vec.end(); ++it)
   {
      mset.insert(*it);
   }

   for (std::multiset<int>::const_iterator it = mset.begin(); it != mset.end(); ++it)
   {
      std::cout << *it << " occurs " << mset.count(*it) << " times." << std::endl;

      for (size_t i = 1; i < mset.count(*it); ++i, ++it);
   }
}

```So multiset::count() returns the count of each element? That would be useful when I need to know if there are 2 instances, 3 instances, etc. Is there some advantage to using the iterators over the double looping above? It seems like, one way or another, this has to be done by brute force, even if that happens under the hood in some library function.

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by NovaAesa on 2011-05-07
> **LMHmedchem said:**
> Is there some advantage to using the iterators over the double looping above? It seems like, one way or another, this has to be done by brute force, even if that happens under the hood in some library function.

From quick inspection, it seems like the complexity of double looping is O(n^2) while the complexity of using an mset is O(nlogn). In other words a pretty damn huge complexity difference. I only had a quick look though, so my complexity calculation could be a bit off.

---

### Post by dwhitney67 on 2011-05-07
> **LMHmedchem said:**
>  It seems like, one way or another, this has to be done by brute force, even if that happens under the hood in some library function.

For the scenario you "painted", I would say yes.  Computers are fast at processing algorithms, but bear in mind that it is humans that teach these computers how to perform their tasks.

Carl Lewis would probably run circles around you at the track.  However, if either he or you attempt to solve a trivial task of sorting 52 cards of a traditional deck of cards, then you will either beat him, tie, or lose to him.  A computer on the other hand, will beat you (or him) before you can say "boo hoo hoo".

The same with your problem; a computer is fast... and it can probably be made to act faster.  That is your job... to find the happiest level at which your computer will solve your problem.  Figure it out and, just maybe, you might find yourself sought out by the "Google" and "Amazon" giants out there.

[/eobs]

---

### Post by johnl on 2011-05-08
If the range of your data is small and the amount of data is large, you could consider something like the following:

```

#include <iostream>
#include <vector>


void findminmax(const std::vector<int>& v, int& min, int& max) 
{
    /* assume v.size() != 0 */
    min = v[0];
    max = v[0];
    for(std::vector<int>::const_iterator i = v.begin(); i < v.end(); ++i) {
        if (*i < min) {
            min = *i;
        }
        if (*i > max) {
            max = *i;
        }
    }
    return;
}


int main(int argc, char* argv[]) {
    int data[] = { 1, 2, 3, 3, 3, 4, 5, 5, 6, 6, 6, 7 };
    std::vector<int> vec(data, data + 12);
    int min, max;
    size_t range;

    /* if you already know the range of the data you can skip this set */
    findminmax(vec, min, max);
    range = (max - min) + 1;

    std::vector<int> cnt(range);
    
    for(std::vector<int>::const_iterator i = vec.begin(); i < vec.end(); ++i) {
        ++cnt[*i - min];
    }

    for(size_t i = 0; i < range; ++i){
        if (cnt[i] > 0) {
            std::cout << (i + min) << " occurs " << cnt[i] << " times."
                      << std::endl;
        }
    }
    
    return 0;
}

```

---

