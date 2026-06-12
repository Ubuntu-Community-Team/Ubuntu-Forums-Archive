---
title: "Simple Java TreeMap question"
date: 2009-06-23
forum: Programming Talk
---

### Post by cdiem on 2009-06-23
Hello,

I was trying to solve the following problem: [http://javabat.com/prob/p196640](http://javabat.com/prob/p196640) using a TreeMap (now, I know it's a matter of several lines of code making comparisons to the elements of the array, but I thought this would be a nice chance to learn more about red-black-trees and the Java Collections). I have googled for several hours, and I still understand them as much as I did in the beginning though... 

As I understand it, once the values from the array are put in the TreeMap, they should be automatically sorted - and finding the highest and the lowest value is just a matter of asking for the first and last element of the TreeMap. However, they are not sorted (or at least I cannot see it...). Or maybe I got it completely wrong?

Here's my sample code - except that it takes the first and last element of the array. In order to solve this with a TreeMap, should I use firstly the Collection.sort (or even simpler, Array.sort) and then retrieve the first and last elements? Aren't the first and last element in the TreeMap supposed to be the ones with the lowest/highest value? 

Here's my code (which doesn't work as expected):

[PHP]public int bigDiff(int[] nums) {
  int smallestValue = 0;
  int largestValue = 0;
  java.util.TreeMap<Integer, Integer> sMap = new java.util.TreeMap();
  for (int i = 0; i < nums.length; i++) {
    sMap.put (i, nums[i]);
  }    
  smallestValue = sMap.get(sMap.firstKey());
  largestValue = sMap.get(sMap.lastKey());
  return (largestValue - smallestValue);   
   
}[/PHP]

bigDiff({10, 3, 5, 6}) &#8594; 7	(I get -4)
bigDiff({7, 2, 10, 9}) &#8594; 8	(I get 2)
etc.

---

### Post by Zugzwang on 2009-06-23
> **cdiem said:**
> Aren't the first and last element in the TreeMap supposed to be the ones with the lowest/highest value? 


Erm, no! The first and last elements of a TreeMap are the elements with the lowest/highest *keys*, not the values. In order to do what you want to do, put all the values into a TreeSet and then take the first and last element.

However, if you only need to sort your data a single time, sorting an Array is usually faster. Also note that the classical way of iterating over the array is also much faster than everything that creates some (total) ordering among the elements (like using a TreeMap, TreeSet or sorting the array). Speaking in terms of complexity, your approach is **O(n log n)** for n elements instead of **O(n)**.

---

### Post by cdiem on 2009-06-23
Yes, I think I have tried to use the wrong data structure; thank you Zugzwang. You're absolutely right about the increased Big(O) complexity (time), as well as the increase of the memory consumption. However, I think this is a risk I'm willing to take in order to learn better the data structures in the Java Collections ;]

P.S.: with TreeSet it was a breeze:

[PHP]public int bigDiff(int[] nums) {
  int smallestValue = 0;
  int largestValue = 0;
  java.util.TreeSet<Integer> intSet = new java.util.TreeSet();
  for (int i = 0; i < nums.length; i++) {
    intSet.add (nums[i]);
  }    
  smallestValue = intSet.first();
  largestValue = intSet.last();
  return (largestValue - smallestValue);   
   
}
[/PHP]

Thanks again!

---

