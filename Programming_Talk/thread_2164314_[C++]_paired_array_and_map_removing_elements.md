---
title: "[C++] paired array and map: removing elements"
date: 2013-07-31
forum: Programming Talk
---

### Post by erotavlas on 2013-07-31
Hi,

I have a problem with array and map. Suppose I have an array of int of fixed size. Each new element is added to array after the last filled element. While if I remove an element from a given position of the array, then I will move all the following elements one position back. As example: an array of M elements filled up to N element and with M-N empty elements.
array a1|a2 ... aN|0|0
add aN+1 -> a1|a2 ... aN|aN+1|0
remove aj -> a1|a2|...aj-1|aj+1..aN|0|0|0
I have also a map in which the key is the address of each element in the array. Now suppose that I want to remove an element from the array, then I have to update the map. I cannot simply erase the element of the map since that after erasing an element from the array also the address need to be changed.
My idea is to remove all the elements in the map that are successive w.r.t. the removed element and then to add again the elements with the correct key i.e. address. This is not efficient.
Do you have a clever idea?
Thank you


An example is this. Suppose that for simplicity each row of the matrix   has only one element and then each element of the array is length one.   Further that the array has 10 elements.
```


array = [36, 128, 16384, 9, 24705, 0, 0, 0, 0, 0]
array_address = [0xfc2840, 0xfc2844, 0xfc2848, 0xfc284c, 0xfc2850,   0xfc2854, 0xfc2858, 0xfc285c, 0xfc2860, 0xfc2864, 0xfc2868] // not   stored used only for this example.

The map  size 5
Key address 0xfc284c 9 value 3
Key address 0xfc2840 36 value 0
Key address 0xfc2844 128 value 1
Key address 0xfc2848 16384 value 2
Key address 0xfc2850 24705 value 4

Then after removal of the third element, the array is

array = [36, 128, 9, 24705, 0, 0, 0, 0, 0, 0]
array_address =  [0xfc2840, 0xfc2844, 0xfc2848, 0xfc284c, 0xfc2850,   0xfc2854, 0xfc2858,  0xfc285c, 0xfc2860, 0xfc2864, 0xfc2868] // not   stored used only for this  example.

The map size 5
Key address 0xfc284c 24705 value 3
Key address 0xfc2840 36 value 0
Key address 0xfc2844 128 value 1
Key address 0xfc2848 9 value 2
Key address 0xfc2850 0 value 4


```

Since that I moved the elements in the array, also the map is updated.    Now if I try to make search inside the map I cannot find the elements.    In fact I would to remove the element with key 0 and value 4, but I    cannot find it using an iterator. So the only way to achieve my purpose    is to remove all the elements that follow the element to remove and   the  to add these elements to map or is it possible to do this in   efficient  manner?
Thank

---

### Post by ofnuts on 2013-07-31
Yes, use a different data structure... Or manage the array differently. The least disruptive would be have the array hold pointers to elements, so that the map points to the ejements themselves. But if you insert & delete things at random, an array isn't the right data structure.

---

### Post by erotavlas on 2013-08-16
Hi,

I'm still having a trouble with this problem. My array is row-wise representation of a matrix. Suppose that I have the following code
```

bool remove_element(int index, int* array, int size, int row_size, std::map<int*, int> myMap)
{
    for(int i = index; i < size - 1; i++)
    {
        for(int j = 0; j < row_size; j++)
        {
            array[i*row_size+j]=array[(i+1)*row_size+j];
        }
    }

    // reset the last element
    for(int j = 0; j < row_size; j++)
    {
        array[(size - 1)*row_size+j]=0;
    }

    return true;
}

```

where the map is defined as

```


 std::map<int*, int, Compare> myMap;

class Compare {
   public:
      Compare(const int size_) : size(size_)  {};
      bool operator()(const unsigned int* x,const unsigned int* y)
      {
          for(int i = 0; i < size; i++)
          {
              if(x[i] < y[i])
              {
                  return true;
              }
              else if(x[i] > y[i])
              {
                  return false;
              }
          }
        return false; // if they are equal
      }
   private:
      int size;
};

```

Each element of the map points to each element of the array while the key is the index of the element in the array. The first element of the map points to the first element of the array, the second element of the map points to the second element of the array and so on. So if I do a modify in the array I need to modify the map. In particular, the code removes correctly the element from the array.

For example, I reported the content of the map
```

Suppose I decide to remove the element 2048 with key 1.
Before removal an element from the array, the map is:
The map: size 11
Key address 0x1f9c840 4 value 0
Key address 0x1f9c854 36 value 5
Key address 0x1f9c844 2048 value 1
Key address 0x1f9c848 4096 value 2
Key address 0x1f9c84c 6145 value 3
Key address 0x1f9c860 65536 value 8
Key address 0x1f9c864 65537 value 9
Key address 0x1f9c850 65824 value 4
Key address 0x1f9c858 131073 value 6
Key address 0x1f9c85c 131136 value 7
Key address 0x1f9c868 270336 value 10

After removal of the element from the array, the elements are correctly shifted and the last element, i.e. with key 10, is put to zero.
Key address 0x1f9c840 4 value 0
Key address 0x1f9c854 131073 value 5
Key address 0x1f9c844 4096 value 1
Key address 0x1f9c848 6145 value 2
Key address 0x1f9c84c 65824 value 3
Key address 0x1f9c860 65537 value 8
Key address 0x1f9c864 270336 value 9
Key address 0x1f9c850 36 value 4
Key address 0x1f9c858 131136 value 6
Key address 0x1f9c85c 65536 value 7
Key address 0x1f9c868 0 value 10


```

Now the last step is to remove the element from the map with this code:

```

    
    int * element[row_size]=0;

    // update the map

    std::map<int*, int>::iterator it = myMap.find(element);
    if(it != myMap.end())
    {
        // erase last element
        myMap.erase(it);
    }
    else
    {
       std::cout << "error" << std::endl;
    }

```

The problem is that the element is not found in the map. Do you have any idea?

Thank you

---

### Post by dwhitney67 on 2013-08-16
I am having trouble understanding what requirement you are attempting to satisfy; this also make my understanding of your solution even vaguer.

As for remove_element(), the variable 'node_index' is not defined within the scope of the code you presented.  I can only assume that this is the index of the entry in the array that will be overwritten (and hence removed) with the next element in the array.

As for why you chose an array for storage of your data also is questionable.  Why did you not chose a different container?  A vector, or even a list, would seem to be better choices.

There are various ways to define a "virtual" matrix in software.  Your approach is one way; another way could be:
```

typedef std::vector<int> Row;

typedef std::vector<Row> Matrix;

...

Row row;
row.push_back( 1 );
row.push_back( 2 );
row.push_back( 3 );

Matrix matrix;
matrix.push_back( row );
...

```

---

### Post by erotavlas on 2013-08-16
The variable node_index is simply index, I'm sorry.
I need to maintain the code efficient as possible and so I use plain C for data structure. I know that this introduce some management problems. I would like to implement something like this, as I have described in the previous post
```

array a1|a2 ... aN|0|0
add aN+1 -> a1|a2 ... aN|aN+1|0
remove aj -> a1|a2|...aj-1|aj+1..aN|0|0|0

```
I have an array and the element are added to the end (as for a vector). When I want to remove an element, I find it and then I shift all the following elements back by a position and I reset the last element. To make efficient the research of the elements inside the array I have paired it with a map. The map has as key the pointer to the element of the array and as value the index of the array. Now the operation of add to the array and to the map works fine. I have the problem with the operation to remove the element from the array and to update the map.
If you have a suggestions I will appreciate it.

---

### Post by erotavlas on 2013-08-16
An example is this. Suppose that for simplicity each row of the matrix  has only one element and then each element of the array is length one.  Further that the array has 10 elements.
```


array = [36, 128, 16384, 9, 24705, 0, 0, 0, 0, 0]
array_address = [0xfc2840, 0xfc2844, 0xfc2848, 0xfc284c, 0xfc2850,  0xfc2854, 0xfc2858, 0xfc285c, 0xfc2860, 0xfc2864, 0xfc2868] // not  stored used only for this example.

The map  size 5
Key address 0xfc284c 9 value 3
Key address 0xfc2840 36 value 0
Key address 0xfc2844 128 value 1
Key address 0xfc2848 16384 value 2
Key address 0xfc2850 24705 value 4

Then after removal of the third element, the array is

array = [36, 128, 9, 24705, 0, 0, 0, 0, 0, 0]
array_address =  [0xfc2840, 0xfc2844, 0xfc2848, 0xfc284c, 0xfc2850,  0xfc2854, 0xfc2858,  0xfc285c, 0xfc2860, 0xfc2864, 0xfc2868] // not  stored used only for this  example.

The map size 5
Key address 0xfc284c 24705 value 3
Key address 0xfc2840 36 value 0
Key address 0xfc2844 128 value 1
Key address 0xfc2848 9 value 2
Key address 0xfc2850 0 value 4


```

Since that I moved the elements in the array, also the map is updated.   Now if I try to make search inside the map I cannot find the elements.   In fact I would to remove the element with key 0 and value 4, but I   cannot find it using an iterator. So the only way to achieve my purpose   is to remove all the elements that follow the element to remove and  the  to add these elements to map or is it possible to do this in  efficient  manner?
Thank

---

### Post by dwhitney67 on 2013-08-16
> **erotavlas said:**
> 
Since that I moved the elements in the array, also the map is updated.   Now if I try to make search inside the map I cannot find the elements.   In fact I would to remove the element with key 0 and value 4, but I   cannot find it using an iterator. So the only way to achieve my purpose   is to remove all the elements that follow the element to remove and  the  to add these elements to map or is it possible to do this in  efficient  manner?
Thank
Please tell me WHAT is it that you are trying to achieve, not HOW you are trying to achieve it.

In other words, what *requirement *are you attempting to implement in your system/application?  Perhaps you are approaching the solution to the problem in the wrong manner, but it is impossible to comment further on this because I don't have a clue as to what you are attempting to do?

Indicating that you must store data in an array, use a map for a lookup, etc is NOT a requirement.  Typically requirements are something along the line of:  "The system shall do <blah>..."

---

### Post by trent.josephsen on 2013-08-16
> **erotavlas said:**
> I need to maintain the code efficient as possible and so I use plain C for data structure.
That's possible. But then you're adding to this "efficiency" requirement a std::map that has to be maintained in parallel with the array, most likely negating the efficiency gains (if there were any in the first place, which is dubious).

I think the crux here is "what's the map for?"

> To make efficient the research of the elements inside the array I have paired it with a map. The map has as key the pointer to the element of the array and as value the index of the array.

Using a map to speed up searching an array may sometimes make sense, but the way you're going about it just doesn't. How do you know the address of the thing you want to search for without knowing already where it is in the array? In your example, the pointers you're using are literally just the addresses of the array elements, which is pointless -- if you know the element's address, you know where it is in the array.

I would guess that on some level you probably want to search by value, e.g. determine the index of the array element containing 2048. Is that correct? If not, what kind of search are you trying to make faster by using a map? (And do you do it often enough that speeding it up is worth slowing down every other operation on the array?)

---

### Post by erotavlas on 2013-08-17
My requirement is to store the a matrix in array that is preallocated in one contiguous block at the beginning of the program. This is done for efficiency. Then I have to speed up the search inside the array that is O(n). For this is use a map O(log n). Each element of the array (row of the matrix) is associated with one element in the map.

Now I'm able to do efficient the addition operation while I'm not able to make efficient the removal.
That's all :)

---

### Post by erotavlas on 2013-08-17
> **trent.josephsen said:**
> That's possible. But then you're adding to this "efficiency" requirement a std::map that has to be maintained in parallel with the array, most likely negating the efficiency gains (if there were any in the first place, which is dubious).

I think the crux here is "what's the map for?"



Using a map to speed up searching an array may sometimes make sense, but the way you're going about it just doesn't. How do you know the address of the thing you want to search for without knowing already where it is in the array? In your example, the pointers you're using are literally just the addresses of the array elements, which is pointless -- if you know the element's address, you know where it is in the array.

I would guess that on some level you probably want to search by value, e.g. determine the index of the array element containing 2048. Is that correct? If not, what kind of search are you trying to make faster by using a map? (And do you do it often enough that speeding it up is worth slowing down every other operation on the array?)


Yes I search inside the map by value not by address. This is the reason for which I redefine the compare operator. I need to implement a faster way to remove the element from the array and the to update the map. I would like to avoid something like this

```

    myMap.erase(myMap.begin(), myMap.end());

    // update the map
    for(int i=0; i < size-1; i++)
    {
        myMap.insert(std::pair<int *,int>(&array[i*row_size],i));
    }

```

since that it requires for each removal to delete and rebuild the while map.

Thank you

---

### Post by dwhitney67 on 2013-08-17
> **erotavlas said:**
> My requirement is to store the a matrix in array that is preallocated in one contiguous block at the beginning of the program.

I'm sorry, but I have to question your ability to define a requirement.  What you have stated above is not a requirement.  It is a preconception of how you have decided to implement something.  However, your assertion may be incorrect.

> **erotavlas said:**
> This is done for efficiency. Then I have to speed up the search inside the array that is O(n). For this is use a map O(log n).

Ideally, an application should be efficient, but again, what you have stated is also not a requirement.  How do you gauge whether your application is efficient enough?  Do you have a benchmark that you are trying to achieve?  O(n) and O(log n)... whatever... What is the purpose of your data, how will it be used, etc.

> **erotavlas said:**
> Each element of the array (row of the matrix) is associated with one element in the map.
Ok.  Why do you need this?  You have not clarified why you need this functionality, much less how it will solve your goal to making your program more efficient.

Why not spend a little time stepping back from the implementation of your application, and spend a little more time discussing the lofty goal that you are trying to achieve.  That way, you actually may get some real help than just drifting in circles pondering whether you have an efficient application or not.

P.S.  I assume that your are working on an important application; if you are merely writing software as a hobbyist, then please forgive my intrusion into this thread.

---

