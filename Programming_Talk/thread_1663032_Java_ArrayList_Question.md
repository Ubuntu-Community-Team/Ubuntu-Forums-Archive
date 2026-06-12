---
title: "Java ArrayList Question"
date: 2011-01-09
forum: Programming Talk
---

### Post by SNYP40A1 on 2011-01-09
I have this simple function below which is used for filtering a signal.  It's taking a very long time to run.  xvals and yvals are ArrayLists and I'm adding about 500,000 elements.  If I add an element to the beginning of an arrayList, is that much slower than adding to the end?  I would think they would both be O(1) operations since only the reference to the beginning of the array would need to be changed.  GNU Octave performs the same calculation in under a second.  My Java implementation has been running for about half an hour.

[PHP]
	public void add(double value) {
		double sum = 0;		
		xvals.add(0, value);
		if(xvals.size() >= xcoeffs.length)
		{
			for(int i = 0; i < xcoeffs.length; i++)
			{
				sum += xcoeffs[i] * xvals.get(i);
			}
		}
		if(yvals.size() - 1 >= ycoeffs.length)
		{
			for(int i = 1; i < ycoeffs.length; i++)
			{
				sum -= ycoeffs[i] * yvals.get(i-1);
			}
		}
		yvals.add(0, sum);
	}
[/PHP]

---

### Post by squaregoldfish on 2011-01-09
ArrayLists start out with memory pre-allocated for its potential future size. If you add more elements than the allocated memory can hold, Java will allocate more memory, which can cause delays.

If you know in advance (roughly) how many elements your list will contain, you can specify this in the list's constructor:

[http://download.oracle.com/javase/6/docs/api/java/util/ArrayList.html#ArrayList(int](http://download.oracle.com/javase/6/docs/api/java/util/ArrayList.html#ArrayList(int))

HTH,
Steve.

---

### Post by Some Penguin on 2011-01-09
You're eating the overhead of storing doubles as Doubles, i.e. objects. 

Perhaps start from 
[http://stackoverflow.com/questions/3307622/java-primitive-collections-library]("http://stackoverflow.com/questions/3307622/java-primitive-collections-library")

---

### Post by KdotJ on 2011-01-09
I haven't read up or looked at the source to see how java's ArrayList is implemented. If, it is indeed implemented as an array that expands when needed, the adding an element to the beginning of the list will of course be much less efficient then adding it to the end because all of the existing elements would need to be moved up one place to allow the new elementgo be inserted at index 0. However as I said I don't know how java implements an ArrayList. 

If this is the case, or for whatever case it turns out that adding to the end is much more efficient, then maybe in your method you could add elements to the end of your ArrayLists, and the in your loops work backwards eg

```
for (int i = 0, j = xvals.size() -1; i < xcoeffs.length; i++, j--) {
    // blah blah
}
```

So effectively your ArrayLists are in reverse order, the newest added element at the back. 


Also, is this add method being called from within a loop? Remember that if it is, you in effect have a loop within a loop (depending on the likelihood of the loop in the add method being called is). Any algorithm where you have a loop in a loop will give you O(N^2) already...

Some Penguin also brings up a very good point which is a highly likely cause of the slow execution. You say you are adding around 500,000 elements. All of that "auto boxing" from double to Double (and vice versa) can bog your algorithm down dramatically.

---

### Post by SNYP40A1 on 2011-01-09
GNU Octave should be performing the same operations.  The boxing / unboxing will not change the class of the algorithm as it only adds a constant time delay to each operation.

---

### Post by SNYP40A1 on 2011-01-09
The reason the code ran slowly was because I was appending elements to the front of the ArrayList rather than adding to the end.  I haven't looked at the implementation, but I don't understand why appending to front vs. appending to end would make a difference in execution time.  Appending to front should only cause:

1) Reference to head of list gets updated with new element.
2) Reference from new element to previous first element gets set.  

Should be an O(1) operation, not O(n).

I'm using Sun Java 1.6.0.22

---

### Post by KdotJ on 2011-01-09
> **SNYP40A1 said:**
> The reason the code ran slowly was because I was appending elements to the front of the ArrayList rather than adding to the end.  I haven't looked at the implementation, but I don't understand why appending to front vs. appending to end would make a difference in execution time.  Appending to front should only cause:

1) Reference to head of list gets updated with new element.
2) Reference from new element to previous first element gets set.  

Should be an O(1) operation, not O(n).

I'm using Sun Java 1.6.0.22

You are describing a Linked List style operation here. 

As I said I dont know java's implementation of ArrayLists, but seeing as java also provides a LinkedList collection, I assume the two are not implemented in the same way?? Guessing by the name of the class, ArrayList would be implemented using an array and some sort of ensureCapacity() method. This of course meaning adding new elements to the beginning would cause all over elements to be shifted up one index...

---

### Post by KdotJ on 2011-01-09
Java's ArrayList javadoc - [HERE]("http://www.docjar.com/html/api/java/util/ArrayList.java.html")

It is stored as a simple array. 
If you look at the add(int index, E item) method, you can see that if the index parameter is 0, it calls the private method growAtFront() which can be found on line 371. Here you can see that the method creates a new array and copies elements across into the new array. You are copying your array each time you call you method in post #1, which makes an increasing the number of copies each time you call it with your larger ArrayLists. 

That is why it is slow adding to the front each time...

---

### Post by Lootbox on 2011-01-09
The Java ArrayList is indeed backed by an array (i.e. contiguous in memory) of objects that is re-allocated and increased in capacity every time you run out of space. Since it's an array, it makes for efficient constant-time lookup of any element just by its index.

The downside of that, of course, is any insertion requires all elements beyond that point to be shifted down by one, which as you can imagine is a rather expensive procedure in large lists. If you can re-arrange how the ArrayList is organized so that most insertions are at the back rather than the front, you'll have asymptotically better performance.

If you can't avoid insertions in the middle front of the list, then consider a linked-list implementation. The problem with **that** is that lookup in the middle of the list now becomes O(n) rather than O(1). I'm not sure if Java has a data structure akin to the C++ deque, but if it does, that would be a good balance of efficient insertion and lookup.

---

