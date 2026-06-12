---
title: "(c++) Generic Heapsort - iterator errors"
date: 2008-10-15
forum: Programming Talk
---

### Post by lian1238 on 2008-10-15
Hi guys,

I'm writing a generic heapsort after successfully writing a heapsort array for ints. I'm using vector<int> as the container.

Here's the code.
[php]
#include <cstdlib>
#include <iterator>

using namespace std;

// void heapsort(int array[], int size);
// void shiftdown (int array[], int from, int to);

template <typename T>
class LessThan
{
public:
    bool operator()(const T& a, const T& b) const
        {    return (a < b ? true : false); }
};

template <typename RAITR, typename CB>
void heapsort (RAITR begin, RAITR end, CB cmp);

template <typename RAITR>
void heapsort (RAITR begin, RAITR end);

template <typename RAITR, typename CB>
void shiftdown (RAITR from, 
    typename iterator_traits<RAITR>::difference_type offset,
    RAITR to, CB cmp);
    
void swap (int & a, int & b);

template <typename RAITR, typename CB>
void heapsort (RAITR begin, RAITR end, CB cmp)
{
    typename iterator_traits<RAITR>::difference_type counter = end - begin;
    
    if (counter < 2)
        return; // nothing to sort
    
    typename iterator_traits<RAITR>::difference_type nonleaf = counter/2 - 1;
    
    typename iterator_traits<RAITR>::difference_type childoffset = nonleaf + 1;
    
    for (RAITR i = begin + nonleaf; childoffset > 0; --i, --childoffset)
    {
        shiftdown(i, end - 1, childoffset, cmp);
    }
        
    for (RAITR j = end - 1; j > begin;)
    {
        swap (*begin, *j);
        shiftdown (begin, --j, 1, cmp);
    }
}

template <typename RAITR>
void heapsort (RAITR begin, RAITR end)
{
    heapsort (begin, end,
        LessThan<typename iterator_traits<RAITR>::value_type>() );
}

/*
void heapsort(int array[], int size)
{
    int noleafOffset = size/2 - 1;
    for (int i = noleafOffset; i >= 0; --i)
        shiftdown (array, i , size - 1);
    
    for (int j = size - 1; j > 0; --j)
    {
        swap (array[0], array[j]);
        shiftdown (array, 0, j-1);
    }
}
*/


template <typename RAITR, typename CB>
void shiftdown (RAITR from, 
    typename iterator_traits<RAITR>::difference_type offset,
    RAITR to, CB cmp)
{
    typename iterator_traits<RAITR>::value_type temp = *from;
    
    RAITR child = from + offset;
    
    while (child <= to)
    {
        offset *= 2;
        if (child < to && ! cmp(*(child+1), *child))
        {
            ++child;
            ++offset;
        }
        if (!cmp(*child, temp))
        {
            *from = *child;
            from = child;
            child = from + offset;
        }
        else
            break;
    }
    *from = temp;
}
/*
void shiftdown (int array[], int from, int to)
{
    int temp = array[from];
    int child = from*2 + 1;
    
    while (child <= to)
    {
        if (child < to && array[child+1] < array[child])
            ++child;
        if (array[child] < temp)
        {
            array[from] = array[child];
            from = child;
            child = from * 2 + 1;
        }
        else
            break;
    }
    array[from] = temp;
}*/

void swap (int & a, int & b)
{
    //modified to count swaps
    ++swapCount;
    int temp = a;
    a = b;
    b = temp;
}
[/php]The commented out code is the heapsort for array of ints.

Here's the test driver but wouldn't compile.
[php]
#include <iostream>
#include <vector>
#include "HeapSort/heapsort.hpp"
#include <ctime>

using namespace std;

class Less
{
public:
template <typename T>
    bool operator()(const T& a, const T& b)
    { return (a<b ? true:false);}
};

int main()
{
    srand( time(NULL) );
    vector<int> x(10);
    
    for (int i = 0; i < 10; i++)
    {
        x.at(i) = rand()%100;
        cout << x.at(i) << ' ';
    }
    cout << endl;
    
    heapsort(x.begin(), x.end(), Less());
    
    for (int i = 0; i < 10; i++)
        cout << x.at(i) << ' ';
    cout << endl;
    
    return 0;
}
[/php]Here's the error:
```

HeapSort/heapsort.hpp: In function ‘void heapsort(RAITR, RAITR, CB) [with RAITR = __gnu_cxx::__normal_iterator<int*, std::vector<int, std::allocator<int> > >, CB = Less]’:
heapsorttestdriver.cpp:28:   instantiated from here
HeapSort/heapsort.hpp:46: error: no matching function for call to ‘shiftdown(__gnu_cxx::__normal_iterator<int*, std::vector<int, std::allocator<int> > >&, __gnu_cxx::__normal_iterator<int*, std::vector<int, std::allocator<int> > >, ptrdiff_t&, Less&)’
heapsorttestdriver.cpp:28:   instantiated from here
HeapSort/heapsort.hpp:52: error: no matching function for call to ‘shiftdown(__gnu_cxx::__normal_iterator<int*, std::vector<int, std::allocator<int> > >&, __gnu_cxx::__normal_iterator<int*, std::vector<int, std::allocator<int> > >&, int, Less&)’

```
Thanks for any help.

---

### Post by dribeas on 2008-10-15
> **lian1238 said:**
> 
```

//...
template <typename RAITR, typename CB>
void shiftdown (RAITR [COLOR="Red"]from,[/COLOR] 
    typename iterator_traits<RAITR>::difference_type [COLOR="Red"]offset,[/COLOR]
    RAITR [COLOR="Red"]to,[/COLOR] CB cmp);
//...    
        shiftdown([COLOR="Red"]i[/COLOR], [COLOR="Red"]end - 1[/COLOR], [COLOR="Red"]childoffset[/COLOR], cmp);
//...
        shiftdown ([COLOR="Red"]begin[/COLOR], [COLOR="Red"]--j[/COLOR], [COLOR="Red"]1[/COLOR], cmp);

```

```

HeapSort/heapsort.hpp:46: error: no matching function for call to ‘shiftdown(__gnu_cxx::[COLOR="Red"]__normal_iterator[/COLOR]<int*, std::vector<int, std::allocator<int> > >&, __gnu_cxx::[COLOR="Red"]__normal_iterator[/COLOR]<int*, std::vector<int, std::allocator<int> > >, [COLOR="Red"]ptrdiff_t[/COLOR]&, [COLOR="Red"]Less&[/COLOR])’

```


Did you change the order or your parameters?

Function is defined as ( iterator, difference, iterator, cmp ), but call is (iterator, iterator, difference, cmp )

---

### Post by lian1238 on 2008-10-15
> **dribeas said:**
> Did you change the order or your parameters?

Function is defined as ( iterator, difference, iterator, cmp ), but call is (iterator, iterator, difference, cmp )

Wow, that's it! I overlooked it. Thanks so much!

---

