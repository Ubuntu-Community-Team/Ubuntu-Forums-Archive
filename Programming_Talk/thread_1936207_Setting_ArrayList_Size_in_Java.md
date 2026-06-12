---
title: "Setting ArrayList Size in Java"
date: 2012-03-05
forum: Programming Talk
---

### Post by Gannin on 2012-03-05
According to the Java docs, you should be able to do this:

```
ArrayList list = new ArrayList(10);
```

That should create a new ArrayList with an initial capacity of 10.

However, if I then try something like this:

```
list.add(5, object);
```

Or

```
list.set(5, object);
```

Either line gives me an index out of bounds exception.  Why is that, when I initialized the ArrayList to start with a size of 10?

---

### Post by r-senior on 2012-03-05
That's just the underlying capacity of the array that is used to store the list.

It means that it doesn't need to extend itself until you put the (n+1)th element in there. It doesn't mean the List has n elements, even though internally it has an array of n elements behind it. If you use size() on the list, you'll see that it is zero.

If you look at the JavaDoc for any List implementation, you'll see that the set() method throws:

```
IndexOutOfBoundsException - if the index is out of range (index < 0 || [COLOR="Red"]index >= size()[/COLOR])
```

Maybe you want a plain old array rather than an ArrayList? That works more like the array structure you are expecting.

---

### Post by Gannin on 2012-03-05
I still want an ArrayList for its dynamic capabilities.  Thanks for the explanation :).  I guess I just need to build the ArrayList with a number of dummy objects ahead of time, which I can then go in and replace later as need be.

---

### Post by stchman on 2012-03-05
With ArrayList you really don't need to dimansion them first.  Simply adding Objects adds to their size.

Just remember, that all items in the ArrayList are of the same type.

---

### Post by muteXe on 2012-03-06
So why didn't the OP's initial add() call work?

---

### Post by r-senior on 2012-03-06
In terms of the OP's question, using add() with an index is the same issue as with set():

*java.util.List*
```
void add(int index,
         E element)

    Inserts the specified element[COLOR="Red"] at the specified position[/COLOR] in this list (optional operation). Shifts the element currently at that position (if any) and any subsequent elements to the right (adds one to their indices).

    Parameters:
        index - index at which the specified element is to be inserted
        element - element to be inserted 
    Throws:
        UnsupportedOperationException - if the add operation is not supported by this list 
        ClassCastException - if the class of the specified element prevents it from being added to this list 
        NullPointerException - if the specified element is null and this list does not permit null elements 
        IllegalArgumentException - if some property of the specified element prevents it from being added to this list 
        [COLOR="Red"]IndexOutOfBoundsException - if the index is out of range (index < 0 || index > size()[/COLOR])


```

---

### Post by muteXe on 2012-03-06
Thank you. so post number 4:

> 
With ArrayList you really don't need to dimansion them first. Simply adding Objects adds to their size.


is incorrect? Or does OP's initialisation of his/her list to 10 elements somehow confusing the compiler?

---

### Post by r-senior on 2012-03-06
No, it's correct.

The ArrayList in Java is a sequence, a list of objects. It cannot be sparse, there can be no gaps. You can't have an element 3 if elements 2, 1 and 0 don't exist.

ArrayList is backed by an array but that doesn't affect the semantics of the ArrayList as a continuous sequence. It has a constructor that sets the initial capacity of the backing array but that's for performance reasons. When new elements are added to the ArrayList it uses the existing storage until that storage is exceeded, then it has to reallocate a new array. If you know you are going to be adding 10000 elements to an ArrayList, you set the initial capacity to 10000 so that the reallocation doesn't have to happen repeatedly.

If you later want to optimise storage because you believe the backing array is excessively large, you can save memory by using trimToSize(). This reduces the backing array so that it is the same size as the list.

The size() of an ArrayList is the number of elements that have been added, not the capacity of the array in which it is stored. You can't access unused elements of the backing array. You can only work with elements through the List API.

---

### Post by r-senior on 2012-03-06
> **stchman said:**
> Just remember, that all items in the ArrayList are of the same type.
This, on the other hand, is not correct. Lists can contain objects of different types, e.g. List<Object> could contain String, Integer, Customer, Fruit, etc., etc..

From Java 1.5, generics (the things in angle brackets) allow lists (and other collections) to be constrained by type. Polymorphism applies, so a List<Person> could contain Person, Customer, Employee, etc.. (Where Customer and Employee are subclasses of Person). But a List<Employee> must only contain Employee.

---

### Post by muteXe on 2012-03-06
I see. Thanks for the explanation.

---

### Post by Damascushead on 2012-03-17
r-senior is right about the ArrayList being dynamic. You can just simply add elements to an ArrayList with the .add() method. 

But for simplicity's sake, if you know that the array is going to be of size 10 always, you should just use a regular array of wanted objects.

```
 object[] objectArray = new object[10];
```hope this helps, although r-seniors answers are probably better:p

---

### Post by Gannin on 2012-03-17
My particular use case is a bit unique.  The array starts off with a known size, but then through the course of the program objects can be removed from the array and added back in later so I need the dynamic capabilities as well.

What I settled on doing was starting by specifying the size of the ArrayList during object creation for memory optimization, then I have a loop to fill each slot of the ArrayList with a place holder to initialize it and make each slot accessible for adding objects later.

---

