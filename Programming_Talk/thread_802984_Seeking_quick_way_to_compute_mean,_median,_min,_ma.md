---
title: "Seeking quick way to compute mean, median, min, max"
date: 2008-05-21
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-05-21
I need to perform some simple statistics (mean, median, max, min) on a set of ordered pairs of numbers where the first element of the ordered pair is an integer and the second number in the pair is a floating-point double.  I will calculate about 4000 ordered pairs and I was thinking of putting them into a map of vectors where the key is the integer and the value is the vector.  This operation will be repeated several times, but I really only need to perform the stats on no more than about 80 elements each time so each vector would be no more than about 80 elements long.  Then after gathering all the data, I would iterate over the map and compute the stats for each vector one at a time.  

Performance is pretty important.

1. Is there a better data structure for what I have described?  I basically compute a stream of ordered pairs and most often the stream is sorted by the first element in the ordered pair, but not always, I can't guarantee that...otherwise, no data structure or only a vector would be needed to compute the stats.

2. I plan on computing the stats by: 
Median - sort vector, take middle element.
Mean - Go over the vector and sum up all values, keep track of how many values have been seen, then divide by that number to get the avg.  
Max, Min - While computing the mean, just keep track of the smallest and largest elements seen.

The above approach is simpler, but is there a better implementation that already does that?  Perhaps a Boost library?  Speed is important.

---

### Post by dwhitney67 on 2008-05-21
You should consider using an std::list.  It is easier to sort.  Or better yet, an std::set.

You shouldn't have to keep track of the number of values "seen"... the std container can tell you that count by referring to the size() function.  For example:  myVector.size(), myList.size(), mySet.size().

The middle of the container may not necessarily provide the mean nor median values... these will have to be determined.

The lowest and highest values, should be at the container's extremities... providing the container's values are sorted.

---

### Post by ZylGadis on 2008-05-22
Sorting seems overkill to me. The fastest sorting algorithms on a binary architecture have O(n*log(n)) complexity (for unlimited ranges, that is). There should be some algorithm to find the median with just a single pass over all values (the median is the only difficulty, the rest are trivial). Perhaps some kind of dynamic programming, or divide and conquer? I have no time to think of a solution now, but hopefully this is a push in a right direction.

---

### Post by SNYP40A1 on 2008-05-22
> **dwhitney67 said:**
> You should consider using an std::list.  It is easier to sort.  Or better yet, an std::set.

You shouldn't have to keep track of the number of values "seen"... the std container can tell you that count by referring to the size() function.  For example:  myVector.size(), myList.size(), mySet.size().

The middle of the container may not necessarily provide the mean nor median values... these will have to be determined.

The lowest and highest values, should be at the container's extremities... providing the container's values are sorted.

That's right, containers keep track of their own size, no need to count.  Sets have no ordering and I don't see how to get the median without sorting.

---

### Post by Lux Perpetua on 2008-05-22
There are much better ways to find a median than sorting the whole list. Look into std::nth_element. Sorting is O(N*log(N)) on a list of length N, but median-finding (and generally n-th-element-finding) is only O(N). 

Easy algorithm to find the n-th element of an array:

- Pick a random element of the array (the "pivot").
- Partition the array on that pivot (as in quicksort).
- Now you know the correct position of the pivot. If it happens to be the n-th element, great. Otherwise, you now know which side of that element the n-th element appears on. Recurse. 

That algorithm runs in expected O(N) time but worst-case O(N^2) time, since you can get unlucky with your pivot if it is near one of the ends of the array. That can be fixed by choosing the pivot more carefully, e. g., via the BFPRT algorithm, which is a deterministic O(N) algorithm. (If you've never heard of it, please do look it up. It's very clever.) However, in practice, I'm pretty sure the algorithm I outlined above will handily outperform BFPRT, and I'm also pretty sure that it's what g++ implements (although I don't think it really picks the pivot randomly).

---

### Post by slavik on 2008-05-22
BFPRT won't always work as it is for kth largest element. When looking for median, you sometimes are looking at 2 numbers (example set: {1,3,7,25}, median is 5).

---

### Post by Lux Perpetua on 2008-05-22
I'm not sure what you mean. To find the median of an array of 100, you could just find the 50th smallest element, then find the smallest element larger than it (just one pass through the array), and average the two. If you use a recursive partitioning algorithm like BFPRT or the one I gave above, then this is especially simple: just find the minimum element of the subarray to the right of the 50th element. Otherwise, you could go through the whole array; you would just need to be careful to do the right thing when there are multiple copies of the 50th element. Either way, it's still O(N).

---

### Post by SNYP40A1 on 2008-05-22
Actually, it does not need to be that precise.  If the array is even, then I could pick either of the "middle" elements, no need for averaging the two.

---

### Post by dwhitney67 on 2008-05-22
If it does not need to be precise, then use these definitions:

```
Mean: To compute the mean, add the values of all the entries and then divide by the number of entries.
```

```
Median: The median is the central value of an ordered distribution.
To obtain the median, order the values from the smallest to the largest. Then pick or construct the middle score. If the data set has an even number of entries, add the two middle values and divide by 2.
```

Here's some code using std::set that provides evidence that as data is inserted into the container, it is automatically sorted, thus facilitating the calculations you need to perform:
[PHP]#include <set>
#include <iostream>

using namespace std;

int main()
{
  typedef pair< unsigned int, double > Data;
  typedef std::set< Data >             DataSet;
  typedef DataSet::const_iterator      DataSetCIter;

  DataSet mySet;

  mySet.insert( Data(5, 1.23f) );
  mySet.insert( Data(1, 3.33f) );
  mySet.insert( Data(3, 9.39f) );
  mySet.insert( Data(3, 9.29f) );

  for ( DataSetCIter it = mySet.begin(); it != mySet.end(); ++it )
  {
    cout << "unsigned int = " << it->first  << "\n"
         << "double       = " << it->second << "\n"
         << endl;
  }

  return 0;
}[/PHP]

---

### Post by Lux Perpetua on 2008-05-22
There is no need to use a set data structure. There is no need to sort the data. All of the statistics can be computed easily in O(N) time. Do you understand that std::set will take O(N*log(N)) time just to insert N data points into the structure?

---

### Post by dwhitney67 on 2008-05-22
I'm trying to see this in my mind.... how can one compute the median value if the data is not sorted.  Is there a formula for computing this?

To find the lowest, highest, and the mean values will require an O(N) parse of the container.  That much is obvious.  I still do not get how one tracks what the median is?

For instance, with simple data like:

```
1 500 74 29 677 12 3 123

The lowest is : 1
The highest is: 677
The mean is   : 177     (sum of all values / 8)
The median is : 51      (29 + 74 / 2)
```

Now picture 4000, or even 1 million un-sorted values... how do you determine the median?

I generated a file with 4000 pairs of randomized data pairs.  It took 0.028s to calculate the information required for this assignment.  Is that too slow?  (Bear in mind some of the time was spent accessing the HDD to get the data).

---

### Post by nvteighen on 2008-05-22
> **dwhitney67 said:**
> I'm trying to see this in my mind.... how can one compute the median value if the data is not sorted.  Is there a formula for computing this?

There is a formula for grouped data...

```

Me = L_i + c * (N/2 - n_prev) / n_i

```

Where (I know the names in Spanish... they may be mistranslated):
Me: Median
L_i: Real inferior limit of the median interval
c: median interval width
N: total number of data
n_i: absolute freq. for median interval
n_prev: accumulative freq. for all intervals previous to the median one.

The "median interval" is the one after which the sum of areas (c * freq) gets more than the half.

If we make c (the amplitude) an infinitesimal, could we get the median for continuous data??

---

### Post by Lux Perpetua on 2008-05-22
dwhitney67 - See post #5. It works in expected O(N) time for exactly the same reason that quicksort works in expected O(N*log(N)) time: you can expect that neither of the two subarrays after the partition will be very large. The difference between this and quicksort is that in quicksort, you have to recurse on both subarrays, whereas here, you only have to recurse on one of them, since you know which subarray contains the element you're looking for. 

It's not very hard to turn that into a rigorous analysis of the expected running time, but I think that intuition is pretty convincing myself. 

That has worst-case O(N^2) running time, as I said. To fix that (only if you must guarantee a good worst case, even at the expense of the average case), you have to make sure that you choose a pivot that is at least some constant fraction of the array size away from both ends of the array. Then you're guaranteed to reduce the size of the problem by a constant factor on each recursive call, which guarantees that--not counting the time required to find the pivot--you do O(N) work in total. Of course, you can't afford to spend too much time finding the pivot. The ingenious contribution of BFPRT is finding a good pivot in O(N) time. I won't explain it here; there are many places to read about it, and it's probably covered in most algorithms textbooks.

nvteighen - I'm sorry, I understand 0% of what you just said. Could you perhaps give an example?

---

### Post by thornmastr on 2008-05-22
This rings a bell from a far distant and clouded past; specifically Andrew Koenig...Barbara E. Moo, "Accelerated C++" Chapter 3; the example tracking student grades.

If so, this much high powered help is not helping this person at all.

---

### Post by dwhitney67 on 2008-05-22
Agreed... for 4000 data points, a solution completed today is better than one not understood for days.

Anyhow, the program I wrote looks for a data file (called 'data.txt') that has pairs of values on each line.  The first value is an unsigned integer, the second value a double.  For example:
```

15874   1.82181e+08
95625   1.63806e+08
4518    4.14998e+08
21233   3.85084e+08
76905   4.29928e+08
71029   4.18077e+07
44643   4.38208e+08
25612   1.11735e+08
82495   5.1242e+08
58215   1.5561e+08
...
```

The program uses an std::multiset to allow for the collection of duplicate values.

Enjoy!
---------------------
[PHP]#include <fstream>
#include <sstream>
#include <set>
#include <stdexcept>
#include <iostream>

using namespace std;

typedef pair< unsigned int, double > Data;
typedef std::multiset< Data >        DataSet;
typedef DataSet::const_iterator      DataSetCIter;



void calcMedianAndMean( const DataSet &data, Data &median, Data &mean )
{
  // if no Data, throw error
  //
  if ( data.size() == 0 )
  {
    throw runtime_error( "Error:  DataSet is empty!" );
  }

  // check if Data set only has one data pair; if so, return it.
  //
  else if ( data.size() == 1 )
  {
    median = Data( data.begin()->first, data.begin()->second );
    mean   = Data( data.begin()->first, data.begin()->second );
  }

  // more than one data pair present within Data set
  else
  {
    unsigned int medFirst   = 0;
    double       medSecond  = 0.0f;
    unsigned int meanFirst  = 0;
    double       meanSecond = 0.0f;

    // Determine the mid-point of the data set.  Add one to this value if the data
    // set contains an odd-number of data values.
    const unsigned int midPoint = data.size()/2 + (data.size()%2 == 0 ? 0 : 1);

    // Determine the divisor to use when computing the median value
    // (2 if even-number of data values; 1 otherwise).
    const unsigned int medDiv = (data.size() % 2 == 0 ? 2 : 1);

    register unsigned int i = 1;

    for ( DataSetCIter it = data.begin(); it != data.end(); ++i, ++it )
    {
      meanFirst  += it->first;
      meanSecond += it->second;

      if ( i == midPoint )
      {
        medFirst  += it->first;
        medSecond += it->second;

        if ( data.size() % 2 == 0 )
        {
          ++it;

          meanFirst  += it->first;
          meanSecond += it->second;

          medFirst   += it->first;
          medSecond  += it->second;
        }
      }
    }

    median = Data( medFirst / medDiv, medSecond / medDiv );
    mean   = Data( meanFirst / data.size(), meanSecond / data.size() );
  }
}


int main()
{
  fstream fs( "./data.txt", ios::in );

  if ( fs )
  {
    DataSet mySet;

    char buf[80];

    while ( fs.getline( buf, sizeof buf ) )
    {
      unsigned int first  = 0;
      double       second = 0.0f;

      istringstream istr( buf );

      istr >> first >> second;

      mySet.insert( Data( first, second ) );
    }

    Data low  = *(mySet.begin());
    Data high = *(--mySet.end());

    Data med, mean;

    calcMedianAndMean( mySet, med, mean );

    cout << "Lowest data pair : ( " << low.first  << ", " << low.second  << " )" << endl;
    cout << "Highest data pair: ( " << high.first << ", " << high.second << " )" << endl;
    cout << "Mean data        : ( " << mean.first << ", " << mean.second << " )" << endl;
    cout << "Median data      : ( " << med.first  << ", " << med.second  << " )" << endl;
  }
  else
  {
    cout << "Error:  Could not open file './data.txt'" << endl;
  }

  return 0;
}[/PHP]

---

### Post by Lux Perpetua on 2008-05-22
The only thing not to understand is why someone would use an inefficient, complicated solution when C++ gives you an efficient one for free (see std::nth_element, as I have already pointed out). Even if you don't know how it works, you should be aware that it exists and that this is when you should use it. My posts were a bit terse and it's possible that I didn't explain it very well, but there are other sources from which you can learn about it if you care.

---

### Post by dwhitney67 on 2008-05-22
In my copious spare time, I will study/memorize each of the std:: containers, algorithms, iterators, and whatever else.

Here's a list of them:  [http://www2.roguewave.com/support/docs/sourcepro/edition9/html/stdlibref/booktoc.html](http://www2.roguewave.com/support/docs/sourcepro/edition9/html/stdlibref/booktoc.html)

When I get to nth-element, I will let you know.

---

### Post by utUtu on 2008-05-22
> **SNYP40A1 said:**
> I need to perform some simple statistics (mean, median, max, min) on a set of ordered pairs of numbers where the first element of the ordered pair is an integer and the second number in the pair is a floating-point double.  I will calculate about 4000 ordered pairs and I was thinking of putting them into a map of vectors where the key is the integer and the value is the vector.  This operation will be repeated several times, but I really only need to perform the stats on no more than about 80 elements each time so each vector would be no more than about 80 elements long.  Then after gathering all the data, I would iterate over the map and compute the stats for each vector one at a time.  

Performance is pretty important.

1. Is there a better data structure for what I have described?  I basically compute a stream of ordered pairs and most often the stream is sorted by the first element in the ordered pair, but not always, I can't guarantee that...otherwise, no data structure or only a vector would be needed to compute the stats.

2. I plan on computing the stats by: 
Median - sort vector, take middle element.
Mean - Go over the vector and sum up all values, keep track of how many values have been seen, then divide by that number to get the avg.  
Max, Min - While computing the mean, just keep track of the smallest and largest elements seen.

The above approach is simpler, but is there a better implementation that already does that?  Perhaps a Boost library?  Speed is important.


The fastest way is use a spreadsheet.

:guitar:

---

### Post by CptPicard on 2008-05-23
IMO this discussion really drives home the point why algorithmics are important. As LP is pointing out, it is an interesting fact that nth-element can be found in linear expected time, and doing something as (comparatively) heavy as sorting really is not worth it. There are numerous examples like this where a little algorithmic understanding makes a big difference in the solution you end up getting, and sometimes, especially with large enough inputs, the difference can either make or break your code.

The nth-element algorithm is really really simple though, shouldn't be hard to understand. If you understand what quicksort does, this is essentially just a simplification of the same thing -- the speed comes from the fact that once you have the two parts of the array/list where first part is smaller than pivot, and second part is bigger than pivot, you *know which half you can just throw away*. 

In a very crude mathematical analysis of the situation you can expect the size of the half of the array to be 1/2n, and when you go down that half, you get something of expected size 1/4n and so on, and the series (1 + 1/2 + 1/4 + 1/8...)n converges to O(n).

Maybe some code helps:

```

def kth(li, k):
    if k > len(li):
      return None
    else:
      pivot = li[0]
      smaller = [x for x in li[1:] if x <= li[0]]
      bigger = [x for x in li[1:] if x > li[0]]
      if len(smaller) == k-1: #Ok, there are exactly k-1 smaller elements, found it
	return pivot
      elif len(smaller) >= k:  # Here's the trick, you can just ignore an expected one half of the list
	return kth(smaller, k)
      else:
	return kth(bigger, k - len(smaller) - 1)

```

---

### Post by nvteighen on 2008-05-23
> **Lux Perpetua said:**
> 
nvteighen - I'm sorry, I understand 0% of what you just said. Could you perhaps give an example?
:)

I'm fixing the variables names to something perhaps more familiar.
i: the interval
f_i: absolute freq. of interval i
F_i: cummulative freq. of interval i. This is, SUM(f_(i-1)) + f_i.
RIL: Real Inferior Limit (Mean between i-th's Inferior Limit and (i-1)-th's Superior... i.e. where rounding makes a non-integer data be included in interval i)

A very simple example:
```

i        RIL        f_i        F_i
[0-1]    -0.5*      12         12 (0+12)
[2-3]    1.5        1          1 (+1)
[4-5]    3.5        9          24 (+9)... This is N, total sum. of elements

```
*RIL for i=1 is always extrapolated.

First, we calculate the total "area", assuming that there are rectangles with width c (all intervals have amplitude 2, you must take the difference between RLIs) and height f_i. So, in this case, Areas will respectively be 24 (12*2), 2 (1*2), 18 (9*2). Total area, 50.

Then we calculate areas cummulatively, until we get a result higher than 50/2 = 25. The first interval has an area of 24. Adding interval 2, we get 26... Ok, the median is somewhere in interval 2 ("the median interval")

There comes the formula's job:
```

Me = RIL_i + c*(N/2 - F_(i-1))/f_i
Me = 1.5 + 2*(24/2 - 12)/1
Me = 1.5

```The median is 1.5. That's where areas to both sides get 25, the half. It's pretty logical, because we needed it a little less than 2.

Has this been more clear now?

---

### Post by SNYP40A1 on 2008-05-25
Hello everyone, I have been away from my computer for a few days, but I really want to thank everyone who posted for their input.  I do need to learn more about the C++ standard library.  I am familiar with the basics: string, set, array, vector, map, but it seems like learning the rest can really improve my programming efficiency.  Fortunately, I do know when a better way probably exists.  I will learn the STD::nth library and figure out how to use it in my program.  Actually, for what I am doing, even 0.02 seconds full sort is fine.  If performance did not matter, I never would have asked the question, but 0.02 is tolerable.  I appreciate all the input.

---

### Post by SNYP40A1 on 2008-06-28
I found this useful:

[http://www.devx.com/cplus/10MinuteSolution/30115/1954](http://www.devx.com/cplus/10MinuteSolution/30115/1954)

---

