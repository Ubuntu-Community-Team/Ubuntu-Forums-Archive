---
title: "c++ sort"
date: 2007-06-13
forum: Programming Talk
---

### Post by LotsOfPhil on 2007-06-13
I have a sequence of numbers. So I know that #0 = x0, #1 = x1, #2 = x2, and so on. 

What I want to do is sort them while preserving the relationship between #0 and x0.

Say I have a[5]=4,9,3,1,7
After sorting I'll have sort[5]=1,3,4,7,9

I want to know that sort[0] was initially a[3], that sort[1] was originally a[2] and so on.

How can I do this?

---

### Post by digitalbenji on 2007-06-13
sort[0] was initially empty.  The purpose of having 2 seperate arrays is so that you don't have to modify the initial array.  Then you can simply print out
for (int i=0;i++;i<a.length()-1){
    cout << "initial value in position[ " << i << "] was" << a[i] << "\nnew value in position[" << i << "] is " << sort[i] << '\n';
}

The point I'm trying to get across here is that by not modifying the unsorted array, you can simply run a 1:1 comparison using the same index to see what is in that position of the array in the sorted and unsorted manners, which is what you are trying to do.  If you don't like this solution, you could create an object or a datatype that contains a record of the information you want.

I'm re-reading your original post, and maybe I misunderstood the question?  Please clarify if my answer was unsatisfactory.

---

### Post by SNYP40A1 on 2007-06-13
What are you using to sort?  As far as I remember from my C days, the built-in sorting functions which are qsort and maybe mergesort, there's no way that they keep track of the original order.  If you want to do this, the information needs to be stored some place.  So I would make an array of structs where each struct holds the value as well as the original index.  Then implement the sort function to use a comparison function which compares only the value, as this is all the sort algorithm needs for sorting.  When done, each element also remembers what its original index was.

struct valstruct {
int value;
int orig_index;
}

---

### Post by LotsOfPhil on 2007-06-13
Hmm, that doesn't quite answer my question.

What I want to know is, after the array is sorted, which element was the biggest, the second biggest, and so on. That way I can go back to the initial array and say "okay, element 14 was the biggest, element 56 was the second biggest..."

---

### Post by LotsOfPhil on 2007-06-13
SNYP40A1,

I was hoping to avoid writing my own algo.

---

### Post by nitro_n2o on 2007-06-13
I don't really know why you don't want to use a struct? but i understand programmer need to have fun sometimes.... 
The way i would do it, is that I'll fill an array of size(a) of integers (indexes) 
so a = [4,9,3,1,7]  indexes = [0, 1, 2, 3, 4] 
Then I'll use some simple sort let's say Insertion sort... and whenever i do the swap portion i don't only swap entries in the array sorted but also swap them in indexes... 
so, by the end of the day you'll get sorted = [1,3,4,7,9] index = [3,2,0,4,1] And the lowest element in the original array is a[indexes[0]] = a[3] = 1 OR the lowest element in the array was element # 3 indexes[0] 

have fun

---

### Post by hod139 on 2007-06-13
I don't really understand what you are looking for, but here is a possible solution.  Instead of using a vector of ints, I use a vector of std::pairs<int, int>, where the first int is the value and the second int is the index.

```

#include <vector>
#include <utility>
#include <algorithm>
#include <iostream>

int main(void){
   static int index = 0;
   std::vector<std::pair<int, int> > myVector;
   myVector.push_back(std::pair<int, int>(4, index++));
   myVector.push_back(std::pair<int, int>(9, index++));
   myVector.push_back(std::pair<int, int>(3, index++));
   myVector.push_back(std::pair<int, int>(1, index++));
   myVector.push_back(std::pair<int, int>(7, index++));

   // copy the vector
   std::vector<std::pair<int, int> > myVectorCopy(myVector.begin(), myVector.end());
   
   // print the original vector
   std::cout << "Original order\n";
   std::vector<std::pair<int, int> >::const_iterator itr;
   for(itr = myVectorCopy.begin(); itr != myVectorCopy.end(); ++itr){
      std::cout << "Value = " << (*itr).first << ", original index = " << (*itr).second << "\n";
   }
   std::cout.flush();

   // sorts by first element of the pair automatically
   std::sort(myVector.begin(), myVector.end());

   // print the sorted vector
   std::cout << "Sorted order\n";
   for(itr = myVector.begin(); itr != myVector.end(); ++itr){
      std::cout << "Value = " << (*itr).first << ", original index = " << (*itr).second << "\n";
   }
   std::cout.flush();
}


```Running the above code produces:
```

Original order
Value = 4, original index = 0
Value = 9, original index = 1
Value = 3, original index = 2
Value = 1, original index = 3
Value = 7, original index = 4
Sorted order
Value = 1, original index = 3
Value = 3, original index = 2
Value = 4, original index = 0
Value = 7, original index = 4
Value = 9, original index = 1

```Again, I don't really understand what you are trying to do and I'm sure there are better solutions.

---

### Post by SNYP40A1 on 2007-06-13
> **LotsOfPhil said:**
> SNYP40A1,

I was hoping to avoid writing my own algo.

You should not have to write your own algorithm.  No matter what you do, you will need to supply some sort of a comparison function so that the built-in sort algorithm knows how to compare the elements in your array.  (Unless there is a built-in specifically for sorting int or doubles from smallest:largest or vice-versa.)  The comparison function approach using structs seems like it would be easiest to implement.

I am thinking of this sort function:

[http://www.cplusplus.com/reference/clibrary/cstdlib/qsort.html](http://www.cplusplus.com/reference/clibrary/cstdlib/qsort.html)

---

### Post by slavik on 2007-06-14
> **nitro_n2o said:**
> I don't really know why you don't want to use a struct? but i understand programmer need to have fun sometimes.... 
The way i would do it, is that I'll fill an array of size(a) of integers (indexes) 
so a = [4,9,3,1,7]  indexes = [0, 1, 2, 3, 4] 
Then I'll use some simple sort let's say Insertion sort... and whenever i do the swap portion i don't only swap entries in the array sorted but also swap them in indexes... 
so, by the end of the day you'll get sorted = [1,3,4,7,9] index = [3,2,0,4,1] And the lowest element in the original array is a[indexes[0]] = a[3] = 1 OR the lowest element in the array was element # 3 indexes[0] 

have fun
this is what databases do. :)

Sort the indeces, not the data itself (since moving data can be expensive when it is a 5MB image file that needs to go over a network and such)

---

