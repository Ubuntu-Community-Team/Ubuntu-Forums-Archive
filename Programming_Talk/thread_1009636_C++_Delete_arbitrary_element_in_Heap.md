---
title: "C++ Delete arbitrary element in Heap"
date: 2008-12-12
forum: Programming Talk
---

### Post by kjohansen on 2008-12-12
I am using make_heap and push_heap on a vector of structs.

I am reading in a data file and on some lines I want to add to the vector and then some lines will indicate to delete.

Pseudocode of what I am trying to do:
[php]while(reading)
{
if(add)
{
   v.push_back(item);
   push_heap(v.begin(),v.end());
}
else if(delete)
{
   for(i=0;i<v.size();i++)
   {
      if(v[i]==the item to delete)
      {
          index=i;
          break;
      }
   }
  v.erase(v.begin()+index);
  make_heap(v.begin(),v.end());
}
}[/php]

if I run this with the heap commands at the end V has size of 19, if I run it deleting only the heap commands the final size is 15.

Is there a proper way to delete an arbitrary entry in a heap?

---

### Post by kjohansen on 2008-12-13
so as I was playing around with this I tried to use just the plain sort from the algorithm header and I get similar results. this leads me to believe that the begin and end iterators are somehow constant and are ignoring my erases.  there has to be a way to delete from a sorted list, add more to it and sort, delete and so on ...or do I need to write my own sort?

---

### Post by CptPicard on 2008-12-13
I don't know about the C++ specifics, but you remove arbitrary element from binary heap in array by essentially performing the "remove max" (assuming it's max-heap) operation on the item you want to remove. What you do is you replace the removed item with the last item from the heap array (which you can just lob off without concern) and fix the heap invariant by pushing that down.

---

### Post by kjohansen on 2008-12-14
I have gone away from the heap for now to test the rest of my logic, and just use sorting at the end.

I have a struct that has a "size" element, setting the size to 0 will have the same basic effect later on in my logic as deleting the record but the vector without deletions will get very very big and thus unmanageable to work with.

The vector will have size of a million or more if I do not do deletions.  If I do deletions it will have an average size of 50,000.

Now my logic is as follows:

[php]
while(reading)
{
if(add)
{
   v.push_back();
}
else if(delete)
{
   for(int i=0;i<v.size();i++)
   {
      if(v[i] is the obj to delete)
      {
           set the size to 0 but do not delete
      }
   }
}

if(do_some_processing)
{
   sort(v.begin(),v.end());
   do some processing
}
}  
[/php]

this return the results I expect but if I try to replace the set the size to 0 part to 

[php]
v.erase(v.begin()+i);
[/php]
  
my results are off, suggesting that it is deleting the wrong item.  shouldnt v.erase as above delete the "ith" element, and then when I call the sort this will be reflected in the v.begin() and v.end()? I have also tried using an iterator in the for loop that finds the element and then just saying delete that iterator instead of the begin+offset, and that is still wrong.


thanks.

---

