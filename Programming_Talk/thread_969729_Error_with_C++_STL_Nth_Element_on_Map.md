---
title: "Error with C++ STL Nth_Element on Map"
date: 2008-11-03
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-11-03
I am having trouble compiling the line below where curosc is defined as:

map<int, double>* curosc;	

nth_element(curosc->begin(), curosc->begin() + curosc->size()/4, curosc->end());

The code was working when curosc was defined as:

vector<double>* curosc;

Anyone know why the above does not work?  Problem related to adding curosc->begin() + curosc->size().

---

### Post by Npl on 2008-11-03
I think it has to do with nth_element requiring an random-access-iterator, but map not having one (I think... to lazy to search for books).
It`s generally a good idea to post the error-message from the compiler if you need help.

---

### Post by dwhitney67 on 2008-11-03
Well, when I tried to implement a simple program, employing an STL map and the nth_element() function as you provided, the compiler spit out an error indicating that the operator+() method is not available for the STL map.

Is this the problem you have?

[php]
#include <iostream>
#include <algorithm>
#include <map>

void display(const std::pair<int, double>& p)
{
  std::cout << p.first << " " << p.second << std::endl;
}


int main ()
{
  typedef std::map<int, double> MAP;

  MAP mymap;

  for (int i = 1; i < 10; ++i)
  {
    mymap.insert( std::pair<int, double>(i, (i+1) * 10.0) );
  }

  // this won't compile!
  std::nth_element(mymap.begin(), mymap.begin()+5, mymap.end());

  std::cout << "mymap contains:" << std::endl;
  std::for_each(mymap.begin(), mymap.end(), display);

  return 0;
}
[/php]

---

### Post by dribeas on 2008-11-03
> **SNYP40A1 said:**
> I am having trouble compiling the line below where curosc is defined as:

map<int, double>* curosc;	

nth_element(curosc->begin(), curosc->begin() + curosc->size()/4, curosc->end());

The code was working when curosc was defined as:

vector<double>* curosc;

Anyone know why the above does not work?  Problem related to adding curosc->begin() + curosc->size().

Map iterators are bidirectional iterators, while nth_element requires random access iterators. Vector iterators are random access and that is why it does work with vector.

On the other hand, std::map's are already ordered, so that if nth_element could be used in a map, the result after the call would be exactly the same arrangement of elements than before the operation.

---

### Post by SNYP40A1 on 2008-11-03
How do I delete this post?

---

### Post by SNYP40A1 on 2008-11-03
I should have posted the error, here it is:

binary '+' : no operator found which takes left-hand operand of type 'std::_Tree<_Traits>::iterator' (or there is no acceptable conversion)
  with
[
   _Traits=std::_Tmap_traits<int, double,std::less<int>std::allocator<std::pair<const int, double>>, false>
]

dribeas, Nth_element does not actually do any sorting to the collection which it is called on so the elements should have been ordered the same in the case when I was using vector (although I never checked that). 

Is there a work-around for what I am trying to do -- just get the 25, 50, and 75-percentile of values in the map?

---

### Post by Npl on 2008-11-03
As the map is sorted ascending by keys, you could simply iterate size()/4 times and do whatever you like with the iterated key/value pairs (put them in a new vector/map or whatever)

---

### Post by SNYP40A1 on 2008-11-03
> **Npl said:**
> As the map is sorted ascending by keys, you could simply iterate size()/4 times and do whatever you like with the iterated key/value pairs (put them in a new vector/map or whatever)

I might have misunderstood your post, but it sounds like you are suggesting that the values stored in the map get copied to an vector, then call Nth_element on the vector.  Is there a more efficent way?  Some way I can get the Nth element from the map directly?

---

### Post by Lux Perpetua on 2008-11-03
Actually, I think Npl is suggesting that you simply take an iterator to the beginning of the map and increment it n/4 times. A separate "n-th element" algorithm is completely unnecessary, since the map is already ordered.

There is probably a relatively easy modification of the map data structure that allows finding the n-th element in logarithmic time (as opposed to linear time), but I don't think the std map implements this. If you need this operation to be really fast for some reason, then I'd consider such a modification; otherwise, linear time should be acceptable.

---

### Post by dribeas on 2008-11-04
> **SNYP40A1 said:**
> Is there a work-around for what I am trying to do -- just get the 25, 50, and 75-percentile of values in the map?

I got the answer wrong, the contents don't get shifted around. The idea is the same nevertheless: std::map is ordered, if you want the highest element, get the last element in the map. If you want the lowest 25 percentile, just get a map iterator into the beginning and increment it size()/4 times. You will iterate over the map in the order that it is stored, and the (size()/4)th element will be your 25 percentile.

---

### Post by SNYP40A1 on 2008-11-04
I should not have to iterate through the map to pull out the nth element.  There should be some way to use Nth on a map or at least calculate the iterator.  Iterators are just pointers to each map pair, right?  So an iterator would have a pointer to the map element and 2 pointers to the previous iterator and next iterator?

---

### Post by SNYP40A1 on 2008-11-04
> **dribeas said:**
> I got the answer wrong, the contents don't get shifted around. The idea is the same nevertheless: std::map is ordered, if you want the highest element, get the last element in the map. If you want the lowest 25 percentile, just get a map iterator into the beginning and increment it size()/4 times. You will iterate over the map in the order that it is stored, and the (size()/4)th element will be your 25 percentile.

Just to make sure I understand the implementation...I would do something like this to get the median value from the following map:

map<int, double>* curosc;

//do some stuff to map

map<int, double>*::iterator i = curosc->begin();
for(int j = 0; j < curosc->size() / 2; j++)
{
     return j->second;
}

---

### Post by dwhitney67 on 2008-11-04
Can I ask a silly question?  What does your data look like?  I ask because I would expect that you would use an STL **multiset** to store your data, not a **map**.

As for computing the median, there are various ways to do this (see the wiki: [http://en.wikipedia.org/wiki/Median](http://en.wikipedia.org/wiki/Median)).

For computational purposes, from what I understood, you take the middle value for an odd-number of values, and if there are an even-number of values, then you take the average of the two values in the middle.

---

### Post by dribeas on 2008-11-04
> **SNYP40A1 said:**
> Just to make sure I understand the implementation...I would do something like this to get the median value from the following map:

map<int, double>* curosc;

//do some stuff to map

map<int, double>*::iterator i = curosc->begin();
for(int j = 0; j < curosc->size() / 2; j++)
{
     return j->second;
}

To get the median of the keys you would have this code:

```

std::map< int, std::string > curosc;
// fill in
std::map< int, std::string >::const_iterator it = curosc.begin();

// move the iterator to the median position
for ( int i = 0; i < curosc.size()/2; ++i )
{
   ++it;
}

int median_value = it->first;
std::string median_name = it->second;

```

Note that the iterator is std::map<...>::iterator, regardless of whether the map is a local object, a reference or heap allocated and held through a pointer (in the code above I have changed it into a local object for simplicity).

You could pre-compute size()/2 and avoid calculating it in each iteration.

Rereading the code above, I am thinking whether you want the median of the keys or the median of the associated values. In the former case the implementation above is what you want, in the latter I don't think there is an easy solution other than moving the data into another data structure and performing the percentiles there.

The second data structure could be a std::multimap (in case the values can be repeated) and the solution above could directly work, or it could be another data structure (std::vector<  std::pair< int, double > > with a hand made weak ordering predicate).

By the way, I have reread the nth_element algorithm and it does indeed move the data inside the container.

---

### Post by SNYP40A1 on 2008-11-04
> **dribeas said:**
> To get the median of the keys you would have this code:

```

std::map< int, std::string > curosc;
// fill in
std::map< int, std::string >::const_iterator it = curosc.begin();

// move the iterator to the median position
for ( int i = 0; i < curosc.size()/2; ++i )
{
   ++it;
}

int median_value = it->first;
std::string median_name = it->second;

```

Note that the iterator is std::map<...>::iterator, regardless of whether the map is a local object, a reference or heap allocated and held through a pointer (in the code above I have changed it into a local object for simplicity).

You could pre-compute size()/2 and avoid calculating it in each iteration.

Rereading the code above, I am thinking whether you want the median of the keys or the median of the associated values. In the former case the implementation above is what you want, in the latter I don't think there is an easy solution other than moving the data into another data structure and performing the percentiles there.

The second data structure could be a std::multimap (in case the values can be repeated) and the solution above could directly work, or it could be another data structure (std::vector<  std::pair< int, double > > with a hand made weak ordering predicate).

By the way, I have reread the nth_element algorithm and it does indeed move the data inside the container.

Actually, I think the map sorts by keys, and not by values.  So the above probably would not work for me, as I want the median value, not the median key.  


I am using a map of maps, but the map that contains the actual values will have about around 40-60 values.  The "outer map" will have around 30-60 maps.  Here's what I am trying to do.  I have about 1000-2000 results of the form:

<key 1> <key 2> <value>

One type of calculation that I want to do is take all values with <key 1> = x, find the 25, 50, and 75-percentile.  That's easy and I was previously doing that with a map of vectors.  Where each vector has a common key.  

Second calculation is more difficult.  And hard to explain, but basically, I want to subtract two values corresponding to two different <key 2> indexes under the same <key 1> index, take that result and put it in a set or vector, then make that calculation across all <key 1>'s.  So the data structure that I thought to use is a map of maps.  Example, assume that I have:

<key 1> <key 2> <value>
1        1       13.3
1        2       14.3
1        3       7.5
2        1       15.5
2        2       10.2
2        3       8.9

For my this calculation, I want to take <key 2> = 3 and <key 2> = 2, subtract the corresponding values for <key 1> = 1, which in the case above would be this:

(7.5 - 14.3)

Take the result above and put it in a vector.  Then repeat that same calculation (with <key 2> = 3, and <key 2> = 2, same as above) for all other indexes of <key 1>.  

So to do this, I have a map that maps <key 1> to a map <key 2>.  Is there a better way?

---

### Post by dwhitney67 on 2008-11-04
Because it appears that you have non-unique keys, you will require a multimap.

Using lower_bound and upper_bound should help you isolate the key (and the range in which it occurs).

---

### Post by SNYP40A1 on 2008-11-04
> **dwhitney67 said:**
> Because it appears that you have non-unique keys, you will require a multimap.

Using lower_bound and upper_bound should help you isolate the key (and the range in which it occurs).

Actually, the keys are unique.  My data structure would look like this:

map<int, map<int, double> > 

//and read the above as: map<(key1), map<(key2), (value)> >

There will be only one occurrence of the key (k1, k2) where k1 is some <key 1> and k2 is some <key 2>.

---

### Post by dribeas on 2008-11-04
> **SNYP40A1 said:**
> Actually, the keys are unique.  My data structure would look like this:

map<int, map<int, double> > 


I cannot think of a better data structure. At the end you do need to access the data structure indexing by different methods. You will need to build a different data structure to calculate the percentiles. There are different ways of doing it, the easier one being iterating over the map extracting the values:

```

typedef std::map< int, double > InternalMap; // just to type less
std::vector<double> extract_second( InternalMap const & m )
{
   std::vector<double> result;
   for ( InternalMap::const_iterator it = m.begin(); it!= m.end(); ++it )
   {
      result.push_back( it->second ); // store just values
   }
   return result;
}

std::vector<double> percentiles( InternalMap const & m )
{
   std::vector<double> values = extract_second( m );
   std::vector<double> percentiles;
   const int size = values.size();

   // calculate percentiles here
   std::sort( values.begin(), values.end() ); 

   percentiles.push_back( values[ size/4 ] );
   percentiles.push_back( values[ size/2 ] );
   percentiles.push_back( values[ 3*size / 4 ] );

   return percentiles; 
}

```

If you need to keep back references to the indexes, then you can store std:: pair's in the vector and provide a specialized comparison predicate to sort (or nth_element which ever you want to use):

```

typedef std::pair< int, double > Pair;
bool precedes2nd( Pair const & a, Pair const & b )
{
   return a.second < b.second;
}

std::vector<double> percentiles( InternalMap const & m )
{
//...
   std::sort( values.begin(), values.end(), precedes2nd ); 
//...
}

```

---

