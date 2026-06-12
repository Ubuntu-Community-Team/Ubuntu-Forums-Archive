---
title: "C++ Dynamic Arrays"
date: 2007-03-27
forum: Programming Talk
---

### Post by DivineOmega on 2007-03-27
Hi guys,

I'm asking for some help. I need to create a dynamic array of objects in C++, and also need to know how to add items to this array after its creation.

I'm currently using the following code to generate a static array. How would I make this a dynamic array? I assume it involves the use of pointers.

```
musicfile listofmusic = new musicfile[100];
```

If someone could provide some relevant example code that would be very useful. As simple as possible to start please.

---

### Post by Jmccaffrey on 2007-03-27
class musicfile {
public:
int a;
};

musicfile *listofmusic = new musicfile[100];
listofmusic[2].a = 1;

---

### Post by hod139 on 2007-03-27
If this is part of a homework assignment you best give more effort and specific questions.  If not, I would suggest you use a vector, which is part of the STL and is the standard dynamic array.

```
std::vector<musicfile> listofmusic(100); // initial size 100
listofmusic.push_back(item); 

```

---

### Post by vuul on 2007-03-27
I am pretty sure that in C++ your line of code means: create an array of musicfile objects named listofmusic.

With the use of the "new" keyword you have dynamically allocated an array of 100 musicfile objects.

To edit one of the musicfile object to your array, in the 4th position in the array you would do something like this:

listofmusic[3].some_class_function(some_formal_parameter);

Or to add/copy a pre-existing musicfile object into your array at the 6th position do this:

listofmusic[5] = name_of_pre-existing_musicfile_object;

Also, at the end of your program don't forget to call the musicfile class' destructor on your dynamic array, or you will have a memory leak. 

Below is an example of what the musicfile class destructor would need to look like to clean up the dynamic array of objects.

musicfile::~musicfile()
{
   delete[] listofmusic;
}

---

### Post by kpatz on 2007-03-27
The simplest way is to use a vector, as mentioned above.

Or for a challenge, code it as a linked list.  Assuming you coded the musicfile class, add a next_musicfile pointer to the class, and have each entry point to the next.  Then you can add entries on the fly, and delete entries pretty easily as well.  Just make sure to handle cleanup in your destructor to avoid memory leaks.

---

### Post by monkeyking on 2007-03-27
you could also make a variabel that keeps track of number of items allready inserted,
and each time you input a new element then check that you array isn´t full.
If full then allocate a new array with the double amount of elements.
And move the old element to the new.

---

### Post by DivineOmega on 2007-03-28
Thanks all. It's not an assignment, however I've done similar things in Java but it different ways and was trying to work out how to apply the knowledge to C++.

The vector solution seems to be the most appropriate. That is all I wanted to know. Thanks again. :)

---

### Post by Tomosaur on 2007-03-28
I much prefer Linked Lists in all honesty. They act pretty much like an array but you can code in new features and stuff very easily. They're much more versatile.

---

### Post by hod139 on 2007-03-28
> **Tomosaur said:**
> I much prefer Linked Lists in all honesty. They act pretty much like an array but you can code in new features and stuff very easily. They're much more versatile.
This is incorrect logic, lists are not "pretty much an array", they do not have random access and the performance guarantees are different.  

If you need random access, use a vector.  With a vector, insertions and removals can be expensive (this is why there is no push_front() with a STL vector) but you can access an element based on an index using the [] operator in constant time.  

With a list, insertions and deletions are constant time (if you know the position), but indexing is not possible.  This is why with the STL list (which is a doubly linked list) you have both push_front and push_back, you can reference the first and last node, but there is no random access, there is no [] operator defined.

The list and vector are the big two sequence style containers, but there are other containers that can also be used in the right situations: associative arrays (map), trees, heaps, etc.  My point is, there is not reason to prefer one type over another.  Use the right container for the right task.

---

### Post by Tomosaur on 2007-03-28
> **hod139 said:**
> This is incorrect logic, lists are not "pretty much an array", they do not have random access and the performance guarantees are different.  

If you need random access, use a vector.  With a vector, insertions and removals can be expensive (this is why there is no push_front() with a STL vector) but you can access an element based on an index using the [] operator in constant time.  

With a list, insertions and deletions are constant time (if you know the position), but indexing is not possible.  This is why with the STL list (which is a doubly linked list) you have both push_front and push_back, you can reference the first and last node, but there is no random access, there is no [] operator defined.

The list and vector are the big two sequence style containers, but there are other containers that can also be used in the right situations: associative arrays (map), trees, heaps, etc.  My point is, there is not reason to prefer one type over another.  Use the right container for the right task.

You're correct, but I didn't say they ARE pretty much an array, I said they ACT pretty much LIKE an array. I prefer the linked list because I can modify how a linked list works. I am not too concerned with being able to use random access unless the situation absolutely demands it. In any case, there are fairly quick workarounds to such problems.

---

### Post by thumper on 2007-03-28
> **Tomosaur said:**
> You're correct, but I didn't say they ARE pretty much an array, I said they ACT pretty much LIKE an array. I prefer the linked list because I can modify how a linked list works. I am not too concerned with being able to use random access unless the situation absolutely demands it. In any case, there are fairly quick workarounds to such problems.

No they don't.

C++ vectors are often used because of the contiguous memory assertion, so the contents of the vector can be used to communicate with C APIs.

Sure you can insert into a list in the same way you can insert into a vector, but they have different performance guarantees.

And what do you mean "I can modify how a linked list works"?  The whole point of programming is to mess with this stuff, and to change how stuff works.

Choose the container that makes the most sense for the work you are doing, and most of the time, the best container is vector.  I can probably count the number of times I've used a list over a vector on one hand.

---

### Post by Tomosaur on 2007-03-29
> **thumper said:**
> No they don't.

C++ vectors are often used because of the contiguous memory assertion, so the contents of the vector can be used to communicate with C APIs.

Sure you can insert into a list in the same way you can insert into a vector, but they have different performance guarantees.

And what do you mean "I can modify how a linked list works"?  The whole point of programming is to mess with this stuff, and to change how stuff works.

Choose the container that makes the most sense for the work you are doing, and most of the time, the best container is vector.  I can probably count the number of times I've used a list over a vector on one hand.

I think you're mixing up my approach to Lists. I'm not saying they should be used in every situation, nor am I trying to convince you (or anybody, for that matter) that a List is a drop in replacement for an array. When I say a List works pretty much like an array, I mean this:

A list can be iterated through.
The values at each node/index can be altered.
A list has the bonus of being extensible beyond its initial allocation bounds.

Whereas you seem to be saying that a List is not the same as an array because you can't type:

int i = my_list[7];

or something like that. I **know** you can't do that, all I'm saying is that when I need a dynamic array, I LIKE to use Lists. It's not like this is deciding the fate of the world here, it's just a preference. For all intents and purposes, a list can be used as a dynamic array. I personally don't particularly care about the performance hit - I don't program professionally and most of what I do write is for me personally, little experiments and such. In the majority of circumstances where I need a dynamic array, a list (doubly linked or not) suits my needs just fine. Yes, perhaps in the professional world you're going to get fired for not using a Vector - but I am not, so what's the problem? I find that I enjoy using / implementing lists more than Vectors.

---

### Post by thumper on 2007-03-29
The only reason why I can think you'd want to implement a list these days is as part of a learning exercise.

std::list would be the standard way to use a list these days.

---

