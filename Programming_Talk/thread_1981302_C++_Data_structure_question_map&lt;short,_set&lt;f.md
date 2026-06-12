---
title: "C++ Data structure question: map&lt;short, set&lt;foo*&gt; &gt; vs. ?"
date: 2012-05-16
forum: Programming Talk
---

### Post by Kentucky88 on 2012-05-16
**Background:**
I have on average 2000 records that I need to store in a structure.  Each record contains up to 32 pointers to other structures.  (The 32 structures are constant, each foo* will only point to 1 of 32 possible foo objects.  A record may have anywhere from 0 to 32 pointers.  I may need to store anywhere from 0 to 2000 records.  Currently, I am storing this data in a map<short, set<foo*> >.  I use map because I do not load each record in serial...that will eventually change so I will be able to use a vector instead of a map.  I want to make this data structure more efficient at least in terms of speed.  

So instead of using a map or vector, I am thinking of creating an array of constant size to hold the records where the record struct would look as follows:

struct record {
   boolean isset;
   boolean[] foospresent;
}; 

I would then create a foo **fooptrs; array to map between the fooenabled boolean and the actual foo object (foospresent boolean shares same index with fooptrs).  That way, for each record, I only have to store whether a foo object is present or not.  And since I only have 32 different foo objects to keep track of, I would only need the boolean array to be about 32 in size.  

**Question: **
I thought about using bitset:

[http://www.cplusplus.com/reference/stl/bitset/](http://www.cplusplus.com/reference/stl/bitset/)

But if I am only allocating an array of about 32 booleans, that should only be 32 bytes of space.  Would bitset be worth the overhead?  Seems like it would need at least 4 bytes of data and I would have to stamp out one bitset object for each record...does not seem very space-efficient.  How much more efficient would it be to read the boolean directly from a boolean array vs. reading / storing the value in bitset?  Would it be twice as slow (assume modern processor, Core2Duo) or more?

Anyone see a better approach?  I want to improve performance by removing the memory allocation / deallocation associated with using a map of sets.  Does anyone know approximately how much memory an empty map and empty set consume (base overhead of those templates)? I know it varies by implementation and system.  But would it be in bytes, tens of bytes, etc?

---

### Post by ofnuts on 2012-05-16
> **Kentucky88 said:**
> **Background:**
I have on average 2000 records that I need to store in a structure.  Each record contains up to 32 pointers to other structures.  (The 32 structures are constant, each foo* will only point to 1 of 32 possible foo objects.  A record may have anywhere from 0 to 32 pointers.  I may need to store anywhere from 0 to 2000 records.  Currently, I am storing this data in a map<short, set<foo*> >.  I use map because I do not load each record in serial...that will eventually change so I will be able to use a vector instead of a map.  I want to make this data structure more efficient at least in terms of speed.  

So instead of using a map or vector, I am thinking of creating an array of constant size to hold the records where the record struct would look as follows:

struct record {
   boolean isset;
   boolean[] foospresent;
}; 

I would then create a foo **fooptrs; array to map between the fooenabled boolean and the actual foo object (foospresent boolean shares same index with fooptrs).  That way, for each record, I only have to store whether a foo object is present or not.  And since I only have 32 different foo objects to keep track of, I would only need the boolean array to be about 32 in size.  

**Question: **
I thought about using bitset:

[http://www.cplusplus.com/reference/stl/bitset/](http://www.cplusplus.com/reference/stl/bitset/)

But if I am only allocating an array of about 32 booleans, that should only be 32 bytes of space.  Would bitset be worth the overhead?  Seems like it would need at least 4 bytes of data and I would have to stamp out one bitset object for each record...does not seem very space-efficient.  How much more efficient would it be to read the boolean directly from a boolean array vs. reading / storing the value in bitset?  Would it be twice as slow (assume modern processor, Core2Duo) or more?

Anyone see a better approach?  I want to improve performance by removing the memory allocation / deallocation associated with using a map of sets.  Does anyone know approximately how much memory an empty map and empty set consume (base overhead of those templates)? I know it varies by implementation and system.  But would it be in bytes, tens of bytes, etc?What makes you think the bitset would be inefficient? I'm pretty sure most of it is implemented using inline functions...

---

### Post by kingtaurus on 2012-05-16
> **Kentucky88 said:**
> **Background:**
I have on average 2000 records that I need to store in a structure.  Each record contains up to 32 pointers to other structures.  (The 32 structures are constant, each foo* will only point to 1 of 32 possible foo objects.  A record may have anywhere from 0 to 32 pointers.  I may need to store anywhere from 0 to 2000 records.  Currently, I am storing this data in a map<short, set<foo*> >.  I use map because I do not load each record in serial...that will eventually change so I will be able to use a vector instead of a map.  I want to make this data structure more efficient at least in terms of speed.  

So instead of using a map or vector, I am thinking of creating an array of constant size to hold the records where the record struct would look as follows:

struct record {
   boolean isset;
   boolean[] foospresent;
}; 

I would then create a foo **fooptrs; array to map between the fooenabled boolean and the actual foo object (foospresent boolean shares same index with fooptrs).  That way, for each record, I only have to store whether a foo object is present or not.  And since I only have 32 different foo objects to keep track of, I would only need the boolean array to be about 32 in size.  

**Question: **
I thought about using bitset:

[http://www.cplusplus.com/reference/stl/bitset/](http://www.cplusplus.com/reference/stl/bitset/)

But if I am only allocating an array of about 32 booleans, that should only be 32 bytes of space.  Would bitset be worth the overhead?  Seems like it would need at least 4 bytes of data and I would have to stamp out one bitset object for each record...does not seem very space-efficient.  How much more efficient would it be to read the boolean directly from a boolean array vs. reading / storing the value in bitset?  Would it be twice as slow (assume modern processor, Core2Duo) or more?

Anyone see a better approach?  I want to improve performance by removing the memory allocation / deallocation associated with using a map of sets.  Does anyone know approximately how much memory an empty map and empty set consume (base overhead of those templates)? I know it varies by implementation and system.  But would it be in bytes, tens of bytes, etc?

Honestly: there is probably a better way to design this; but without more details of the problem domain I can't give you any better solutions. It sounds like you are wanting to use the flyweight design pattern. 

Please note that even just storing 32 pointers in a vector (and having 2000 of them) will probably take up just a little more than:
4 bytes * 32 * 2000 = 250 kB
On any modern computers this is a tiny amount of space.

Next point, why don't you just use a vector to store everything and call reserve or alternate constructor ([http://www.cplusplus.com/reference/stl/vector/reserve/]("http://www.cplusplus.com/reference/stl/vector/reserve/")).

Finally why are you using set? It might be better to use a vector which been sized to 32 and has the value is 0 (or just reserve 32 places of storage and then. Then when creating the record:
```

std::vector<std::vector<int *> > record(2000, std::vector<int*>(32));

//When you want to have an element in a specific record (<record_id>):
(record[<record_id>])[<object_id_number>] = <ptr_to_object>;
//Please note that this will require constant checks to make sure that you don't deference 0.

```

or

```

std::vector<std::vector<int *> > record(2000);
for (int i = 0; i < record.size(); ++i)
{
  record[i].reserve(32);
}

//When you want to add an element to a specific record:
record[<record_id>].push_back(<ptr_to_object>);
//please note there will be duplicates in records if you do multiple push_backs with the same <ptr_to_object>;

```


If you are looking to minimize the amount of data stored:
(1) You could do a couple of things. Noting that you only have 32 objects you could just use an unsigned int as a simple bit holder. The idea is as follows: 
```

//give each object a number (from 0-31)
//so then
const unsigned int object_zero = 0;
const unsigned int object_one  = 1;
//...
//...
//...

unsigned int bit_map = 0;
//to setup the bit_map, use bitwise operations
// (so this bit_map would tell us that object_zero and
//  object_one are available);
bit_map |= (1 << object_zero);
bit_map |= (1 << object_one);
//...

//after that, to determine if you have a particular bit object associated with a record:
if (bit_map & (1 << object_zero))
{
//do something with 'foo pointer corresponding to object_zero'
}

```

The difficulty with any of these solutions is that they may introduce a large amount of complexity to the code base and make the actual implementation more difficult to extend or understand.

Cheers

---

### Post by Kentucky88 on 2012-05-16
> Next point, why don't you just use a vector to store everything and call reserve or alternate constructor ([http://www.cplusplus.com/reference/stl/vector/reserve/](http://www.cplusplus.com/reference/stl/vector/reserve/)).

Previously, I was not processing records in order, but I can make another change so that I can and will switch to vector.

> Finally why are you using set?

I did not need indexing so I thought set would be more efficient.  I can switch to vector.  I don't have to worry about duplicate entries.

> It might be better to use a vector which been sized to 32 and has the value is 0 (or just reserve 32 places of storage and then. Then when creating the record:
```

std::vector<std::vector<int *> > record(2000, std::vector<int*>(32));

//When you want to have an element in a specific record (<record_id>):
(record[<record_id>])[<object_id_number>] = <ptr_to_object>;
//Please note that this will require constant checks to make sure that you don't deference 0.

```

That works.  Actually, if I just store the pointer, then the index does not matter.  I can just use push_back to add new entries.  If I run low on memory I can try the bit packing approach, but I don't think I'll need to do that.

> What makes you think the bitset would be inefficient? I'm pretty sure most of it is implemented using inline functions... 	

I was thinking that bit shifting and masking operations would be slower than dereferencing a pointer and comparing to zero.

---

### Post by kingtaurus on 2012-05-16
> **Kentucky88 said:**
> Previously, I was not processing records in order, but I can make another change so that I can and will switch to vector.



I did not need indexing so I thought set would be more efficient.  I can switch to vector.  I don't have to worry about duplicate entries.



That works.  Actually, if I just store the pointer, then the index does not matter.  I can just use push_back to add new entries.  If I run low on memory I can try the bit packing approach, but I don't think I'll need to do that.



I was thinking that bit shifting and masking operations would be slower than dereferencing a pointer and comparing to zero.

Bit shifting and masking can be incredible quick (it depends on the platform). For example, a bit shift on some platforms can take less time than an addition. Further, you can remove the |= for += (if you only do the operation once) and try some timing tests to determine which is faster. Speed of pointer operations can take more time depending on whether the calls that can be resolved statically or inlined. Premature optimization often leads to more trouble than its worth.

Cheers,

---

### Post by Kentucky88 on 2012-05-17
Ok, thanks King, I'll mark this thread as closed.

---

