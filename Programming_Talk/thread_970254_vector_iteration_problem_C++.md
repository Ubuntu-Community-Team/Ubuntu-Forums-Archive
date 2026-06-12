---
title: "vector iteration problem C++"
date: 2008-11-04
forum: Programming Talk
---

### Post by diamantis13 on 2008-11-04
I would like to iterate through all the elements of a vector of objects excluding the last one. With an array it would be really simple, but I cannot figure a nice way to do it with a vector.
Any suggestions?

---

### Post by dribeas on 2008-11-04
> **diamantis13 said:**
> I would like to iterate through all the elements of a vector of objects excluding the last one. With an array it would be really simple, but I cannot figure a nice way to do it with a vector.
Any suggestions?

```

std::vector<int> v;
// fill in v
std::vector<int>::const_iterator end = v.end()-1; // [1]
// else get end to point to v.end() and then decrement end:
// std::vector<int>::const_iterator end = v.end(); --end; // [2]
for ( std::vector<int>::const_iterator it = v.begin();
      it != end; ++it )
{
   // loop
}

```

Vector iterators are RandomAccessIterators, not only they can be incremented and decremented (BidirectionalIterator) but they can also be displaced by a constant factor [1]. In containers with Bidirectional (not Random) iterators, you can decrement the iterator as in [2].

Beware of the arithmetic operations, you may end up outside of the original container (if vector has size()==0, then end above will be one before the beginning of the container and iterating with != will get you into trouble).

---

### Post by alternatealias on 2008-11-04
> **dribeas said:**
> [CODE]
Beware of the arithmetic operations, you may end up outside of the original container (if vector has size()==0, then end above will be one before the beginning of the container and iterating with != will get you into trouble).

You don't need to decrement the end() iter.

for (std::vector<int>::const_iterator iter = v.begin(); iter != v.end (); iter++) {
    // loop
}

that's the proper way to do things.

Your loop would never use the last item in the vector, which is a perfectly valid item.

---

### Post by dribeas on 2008-11-04
> **alternatealias said:**
> 
for (std::vector<int>::const_iterator iter = v.begin(); iter != v.end (); iter++) {
    // loop
}

that's the proper way to do things.


No, it is not, it is the proper way of iterating over all elements in the vector as end() is defined as an iterator 'one past the end of the container'. The OP requested how to iterate over all but the last element. Your loop will iterate over all elements in the vector including the last one.

---

### Post by alternatealias on 2008-11-04
> **dribeas said:**
> No, it is not, it is the proper way of iterating over all elements in the vector as end() is defined as an iterator 'one past the end of the container'. The OP requested how to iterate over all but the last element. Your loop will iterate over all elements in the vector including the last one.

ah, apologies. I missed that he didn't want the last element.

---

