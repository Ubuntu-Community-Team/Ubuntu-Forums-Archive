---
title: "Some confusion about Queues(python)"
date: 2007-09-11
forum: Programming Talk
---

### Post by triptoe on 2007-09-11
I am doing this link here: [http://www.greenteapress.com/thinkpython/thinkCSpy/html/chap19.html](http://www.greenteapress.com/thinkpython/thinkCSpy/html/chap19.html)

THe problem is i am at the very last exercise. It says to do this: > As an exercise, write an implementation of the Priority Queue ADT using a linked list. You should keep the list sorted so that removal is a constant time operation. Compare the performance of this implementation with the Python list implementation.

Here is what I don't understand... in order to make removal a constant time function you have to keep the list sorted. in order to make the list sorted... you have to make the insert function a Linear function.. as opposed to constant time. isn't that correct? And is a linked list a better option than just a plain list if you want to keep it sorted?

How do you go through a linked list and keep it sorted? For instance to print every node in a linked list

while node:

    print node
    node = node.next

the reason that works is because it creates a copy of the real node you pass to that function... and so its printing a copy. Otherwise you would be starting with the head.. and the head would be changing each pass through the loop. If you want to keep the list sorted, how can you do that without actually modifying the nodes??

---

### Post by pmasiar on 2007-09-11
you have linked list: to change it, you just modify the links, no?

IMHO you need some background in data structures - see wiki in my sig

---

### Post by Lux Perpetua on 2007-09-11
triptoe - you are correct that inserting an arbitrary value into a sorted linked list is a linear-time affair.

---

### Post by steve.horsley on 2007-09-12
Can't you do a binary search to find the insert point? That wouldn't be linear time then, I think.

---

### Post by Lux Perpetua on 2007-09-12
To binary search, you need random access. With a linked list, you don't have random access. Well, you do, but it isn't constant-time. It's linear-time, and that destroys any advantage binary search might have.

---

### Post by slavik on 2007-09-12
hashes are so much better than lists for priority queues :P

constant time insertion and constant time removal :)

here's a sample in perl:
[php]
sub enqueue {
	push @{$_{"$_[0]"}}, $_[1];
}

sub dequeue {
	foreach(sort { $a <=> $b } keys %_) { return shift @{ $_{$_} } if ($#{ $_{$_} } > -1); }
}
[/php]

EDIT: in perl, the arrays are actually doubly linked circular lists, so adding and removing is literally constant time :)

---

### Post by Lux Perpetua on 2007-09-12
> **slavik said:**
> hashes are so much better than lists for priority queues :P

constant time insertion and constant time removal :)

here's a sample in perl:
[php]
sub enqueue {
	push @{$_{"$_[0]"}}, $_[1];
}

sub dequeue {
	foreach(sort { $a <=> $b } keys %_) { return shift @{ $_{$_} } if ($#{ $_{$_} } > -1); }
}
[/php]

EDIT: in perl, the arrays are actually doubly linked circular lists, so adding and removing is literally constant time :)Would you mind explaining this algorithm? Chances are, there's a hidden cost somewhere. I hope your 'sort' in the second function isn't literally a sort of the keys of the hash.

---

### Post by slavik on 2007-09-13
good thing you reminded me of the sort, it's nlogn, I stand corrected. also, keep in mind that the code allows for any numerical priority (sorting has to change to be able to check strings). but the sort does happen once (or it should, since the foreach should be taking a list not an expression)

but in any case ...

ENQUEUE
1. start with an empty hash.
2. dereference the hash element as an array with the given priority (in perl, if it doesn't exist when accessing it, it gets created).
3. push the value onto the array (in perl, there is on list and no stack, there is only the array, beat that python :-P)

DEQUEUE
1. sort the keys in accending order
2. pick the lowest key and shift the element out, and return it.
*3. if the array in #2 is empty, go to the next one.

---

### Post by steve.horsley on 2007-09-13
> **Lux Perpetua said:**
> To binary search, you need random access. With a linked list, you don't have random access. Well, you do, but it isn't constant-time. It's linear-time, and that destroys any advantage binary search might have.

Doh!

---

### Post by dwblas on 2007-09-15
> Here is what I don't understand... in order to make removal a constant time function you have to keep the list sortedIf we are all using linked list to mean the same thing, then the list is not sorted, the keys are sorted.  If the list is sorted, then you don't really need a linked list because you can just search the sorted list with the len/2 method.  Also, removing something usually just means removing the key/link.  The actual records are removed all at once, once per day or at some time interval, because all of the keys have to be generated again because some of the records have now moved.  In any case, I'm not sure that I understand exactly what you are asking, but this is a learning exercise, so it is best to take it step by step.  Post the code you have, even if it is only creating a list of test data and the related indexes, and I'm sure someone will help with the next step.

---

### Post by lisati on 2007-09-15
Suggestion: keep a "master" pointer to the head, and use a COPY when doing a search.

---

