---
title: "Is this C++ STL set lookup code reasonably efficient?"
date: 2009-09-10
forum: Programming Talk
---

### Post by SNYP40A1 on 2009-09-10
Specifically, can the code below be made more efficient by supplying a comparison function to the set?  What would the function prototype of the comparison function look like (I know how to make the body)?

[PHP]
set<pair<int, int> > coords;

void loadSet(vector<pair<int, int> > coordinates)
{
    for(int i = 0; i < coordinates.size(); i++)
    {
         coords.insert(coordinates[i]);
    }
}

int main()
{
    loadSet(coordinates);
    cout << "Enter x coordinate" << endl;
	cin >> x;
	cout << "Enter y coordinate" << endl;
	cin >> y;
	
	if(coords.find(pair<int, int>(x, y)) != coords.end()) cout << "Set contains (" << x << "," << y << ")" << endl;
	else cout << "Set does not contain (" << x << "," << y << ")" << endl;
	return 0;
}
[/PHP]

---

### Post by MadCow108 on 2009-09-10
your the set uses a standard comparison for pairs of basic types which just sorts first entry before second entry (e.g. 01 02 10 11 12)
> In inequality comparisons (<, >), only the first element is compared, except if both first elements compare equal to each other, in this case only the second element is taken into consideration for the comparison operation.
[http://www.cplusplus.com/reference/std/utility/pair/](http://www.cplusplus.com/reference/std/utility/pair/)

unless you need to sort differently I see no problems with that.
the speed is logarithmic no matter how you sort.

here would be a compare funcion which sorts the other way round:
```
struct cmp {
  bool operator() (const pair<int, int>& lhs, const pair<int, int>& rhs) const
  {
  	if (lhs.second == rhs.second)
  		return (lhs.first > rhs.first);
  	else
  		return (lhs.second > rhs.second);
  }
};
set<pair<int, int>,cmp> coords;

```
you can of course also use function pointers instead of functors (although functors are preferable)



when inserting there are performance differences.
If you give the insert operation the position of the preceding element you have a very fast insertion.
[http://www.cplusplus.com/reference/stl/set/insert/](http://www.cplusplus.com/reference/stl/set/insert/)

---

### Post by dribeas on 2009-09-10
Not a matter of efficiency, as that was already answered by MadCow108, but a little more on style. I'd avoid having global variables, and you can avoid the function (not for efficiency, but for code bloat) by using iterators.

```

int main()
{
   typedef std::pair<int,int> point;

   // construct a vector
   std::vector< point > v();
   // fill in data...

   // construct a std::set from a given set of data (pair of iterators)
   std::set< point > s1( v.begin(), v.end() );

   // or insert values into an already existing set:
   std::set< point > s2;
   // ...
   s2.insert( v.begin(), b.end() );
}

```

---

### Post by Lux Perpetua on 2009-09-10
Consider hash_set (not ISO standard yet, but provided by various implementations including GNU) as well if performance is important. You typically have expected constant-time insertion and lookup, but no guarantee of that...provided, that is, that your keys don't follow a rather strange distribution. (For any given fixed hash function, you can defeat it by engineering your keys appropriately, degrading performance to linear-time.) Hash sets also have some memory overhead (linear in the number of keys).

---

### Post by SNYP40A1 on 2009-09-11
Thanks for all the advice.  I appreciate it.  I will stick with a tree-based set for now.  Hashset in the future if performance really matters (that's why I said reasonably efficient rather than most efficient).  I only expect to store ~100 - 200 points so basic STL set should be fine for that.

---

