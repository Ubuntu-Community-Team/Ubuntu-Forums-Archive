---
title: "[JAVA]find array inside an array"
date: 2009-01-09
forum: Programming Talk
---

### Post by babacan on 2009-01-09
Hello
I am trying to make a function that consumes 2 arrays, checks if the second one exists in first and gives true, if not false.

ie: A= {1,2,3,4,5,6} B= {4,5,6} C ={8,9}
sArray(A,B) -> true
sArray(A,C) -> false

here is my own java program and algorithm, I couldnt find why it goes to an eternal loop and not works.
```

static boolean sArray(int a[], int[] b){

	for(int i=0;i<a.length;i++){

		int c=0;
		int d= i;
		while(c < b.length  && i< a.length){
			if(a[d] == b[c]){
				c++;
				d++;
			}
		}
		if (c == (b.length - 1))
			return true;
	}
	return false;
}
```

---

### Post by shadylookin on 2009-01-09
[PHP]
while(c < b.length  && i< a.length){
			if(a[d] == b[c]){
				c++;
				d++;
			}
		}

[/PHP]

here is the infite loop. a[0] != b[0] so it cannot go into that if statement therefore it never gets incremented so you're endlessly checking to see if a[0] == b[0]  you need to increment d outside of your if statement

---

### Post by babacan on 2009-01-09
> **shadylookin said:**
> [PHP]
while(c < b.length  && i< a.length){
			if(a[d] == b[c]){
				c++;
				d++;
			}
		}

[/PHP]

here is the infite loop. a[0] != b[0] so it cannot go into that if statement therefore it never gets incremented so you're endlessly checking to see if a[0] == b[0]  you need to increment d outside of your if statement

Thanks alot for your asistance, now my code looks like this:
[PHP]static boolean sArray(int a[], int[] b){

	for(int i=0;i<a.length;i++){

		int c=0;
		int d= i;
		while(c < b.length  && i< a.length){
			if(a[d] == b[c]){
				c++;
			}
		        d++;
		}
		if (c == (b.length - 1))
			return true;
	}
	return false;
}[/PHP]

But when checking for some B that is inside A , I get out of boundaries error. I fail to see what part of my algorithm fails.

---

### Post by shadylookin on 2009-01-09
> **babacan said:**
> Thanks alot for your asistance, now my code looks like this:
[PHP]static boolean sArray(int a[], int[] b){

	for(int i=0;i<a.length;i++){

		int c=0;
		int d= i;
		while(c < b.length  && i< a.length){
			if(a[d] == b[c]){
				c++;
			}
		        d++;
		}
		if (c == (b.length - 1))
			return true;
	}
	return false;
}[/PHP]

But when checking for some B that is inside A , I get out of boundaries error. I fail to see what part of my algorithm fails.

well first off the for loop should be gotten rid of since it doesn't do anything just initialize int d = 0; and it will accomplish the same thing.

in the while loop you have i < a.length it should be d < a.length

if (c == (b.length - 1)) if you'll look closely at your algorithm you'll notice that if **array b** is a sub array of **array a** then c will be equal to b.length not one less than.

---

### Post by Reiger on 2009-01-09
Interesting, for a similar problem I once implemented a 'cyclic' array which wraps around itself. That way you never ought to get any out-of-bounds errors:

```

import java.util.Iterator;
import java.util.NoSuchElementException;

/**
 * 
 * @param <T>
 */
public class CyclicArray<T>  implements Iterable<T>{
	
	protected T[] array;
	protected int index=0;
	protected int begin=0;
	
	/**
	 * Create a litteral CyclicArray&lt;T&gt; value from the litteral array T [].
	 * @param value
	 */
	public CyclicArray(T [] value) {
		array=value;
		index = value.length -1;
	}
	
	
	/**
	 * Default constructor: create an empty CylicArray&lt;T&gt; with the size specified.
	 * @param size
	 *
	 */
	@SuppressWarnings("unchecked")
	public CyclicArray(int size) {
		array=(T [])(new Object [size]);
	}
	
	/**
	 * Get the size/length/capacity of an CyclicArray object.
	 * @return the size (capacity) of the CylicArray.
	 */
	public int size() {
		return array.length;
	}
	
	/**
	 * 
	 * Pushes an item onto the end of a CyclicArray. 
	 * <div>
	 * @param item : the item to be 'pushed' onto the end of the CyclicArray.
	 * </div>
	 * <hr />
 	 * If the CyclicArray should 'overflow'
	 * (that is, the number of elements should exceed its capacity/size/length) the
	 * CyclicArray will 'rotate' itself 'upwards' and overwrite its original first element 
	 * with the element to be pushed onto the CyclicArray. This means that at any given
	 * time the CyclicArray will hold only the *last* C elements which have been pushed
	 * onto it, with C equal to the capacity/size of the CyclicArray.
	 * @see {@link #set(int, Object)} {@link #pop()}
	 */
	public void push(T item) {
		array[index] = item;
		int i = index+1;
		if(i < array.length)
			index=i;
		else {
			begin = (begin + 1) % array.length;
			index = 0;
		}
	}

	/**
	 * Puts the item passed at the index specified. The 
	 * index is assumed to refer to some (rotated) position relative to 
	 * the start of the CyclicArray and it is mapped to the corresponding 'absolute' 
	 * index within the CyclicArray itself.
	 * This may result in unexpected behaviour, should the index be out 
	 * of bounds (larger than the size of the CyclicArray, or less than 0) as this method
	 * will not signal any such 'overflow' but silently overwrite the element at the 
	 * calculated 'absolute' index instead.
	 * <div>
	 * @param index
	 * @param item
	 * </div>
	 * <hr />
	 * You should only use this method if you must directly manipulate the items at a certain well-known index.
	 * Consider using push() instead.
	 * @see {@link #push(Object)}
	 */
	public void set(int index, T item) {
		array[(begin + index) % array.length] = item;
	}
	
	public T read() {
		return array[index];
	}
	
	public T read(int index) {
		return array[(begin + index) % array.length];
	}
	
	/**
	 * Pops the last item off the end of a CyclicArray.
	 * This method behaves as the opposite of push(T item) both w.r.t. function and rotating the array.
	 * @return the item which was popped off the end of the CyclicArray
	 * @see {@link #push(Object)}
	 */
	public T pop() {
		T item = array[index];
		array[index] = null;
		int i = index -1;
		if(i > -1)
			index = i;
		else {
			begin = (begin - 1 + array.length) % array.length;
			index = array.length - 1;
		}
		return item;
	}
	
	@SuppressWarnings("unchecked")
	public T [] toArray() {
		T [] result = (T []) (new Object [array.length]);
		int i;
		for(i=0;i<array.length;i++)
			result[i] = array[(begin + i) % array.length];
		return result;
	}
	
	public boolean equals(T [] test) {
		boolean result = false;
		if(test.length == array.length) {
			int i;
			result=true;
			for(i=0;result && i<array.length;i++) {
				T t = array[(begin + i) % array.length];
				if(test[i] != null && t !=null)
					result = test[i].equals(t);
				else
					result = test[i] == null && t == null;
			}
		}
		return result;
	}


	@Override
	public Iterator<T> iterator() {
		return new CyclicArrayIterator<T>(this);
	}
}

/**
 * Simple array-based iterator implementation for the benefit of 
 * syntactic sugar. (So you can code: for(T t: CyclicArray<T>)).
 * @param <T>
 */
class CyclicArrayIterator<T> implements Iterator<T> {

	private CyclicArray<T> cat;
	private int post=0;
	public CyclicArrayIterator(CyclicArray<T> cat) {
		this.cat=cat;
	}
	
	@Override
	public boolean hasNext() {
		return post<cat.size() && post>=0;
	}

	@Override
	public T next() {
		if(post<cat.size()) {
			T result=cat.read(post);
			post++;
			return result;
		}
		else
			if(post<0)
				throw new NoSuchElementException("No element at index: "+post+". The Iterator is empty!");
			else
				throw new NoSuchElementException("No element at index: "+post+". You've already reached the end of the Iterator!");
	}

	
	@Override
	public void remove() {
		if(post>=0) {
			cat.pop();
			post--;
		}
		else
			throw new NoSuchElementException("No element at index: "+post+". You've already fully emptied the Iterator!");
	}
}

```

Shouldn't be very hard to make an 
```

/** Check if the T[] contained is really contained inside this CylicArray */
public boolean containsArray(T [] contained) { /* code */ }

```

A possible implementation (which does not take care of possible rotations, should you be interested in such a thing)
```

boolean result = contained.length == this.size();
if(result)
  return this.equals(contained);
if(contained.length > this.size())
  return false;
int i;
result=true;
for(i=0;result && i<contained.length;i++) {
   if(contained[0] != null && this.read(i) != null)
      result = contained[0].equals(this.read(i));
   else
      result = contained[0] == null && this.read(i) == null;
}
return result;

```

---

