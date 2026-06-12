---
title: "garbage collection ..."
date: 2008-08-28
forum: Programming Talk
---

### Post by slavik on 2008-08-28
this is similar in spirit to my "exceptions ..." thread.

garbage collection library in C? (I am writing this as I am thinking about it, so it might be lower quality than the exceptions post).

The basic way of doing garbage collection is to create wrappers around pointer assignment. You will need one large chunk of heap space and have your own malloc() to allocate chunks of the heap space you get. this means that the large chunk of memory will have to be divided into nodes that will contain the reference count (how many 'things' are pointing to this node) and the location of the next node and a third field that is the actual data (this is where the reference will actually point to). this is basically a linked list.

Every time someone assigns a reference to the node, the node's reference count goes up by one. when the reference is assigned another node, the reference count is decremented. This is much like ext2/3 (when you rm a file, the link count is set to 0, then the file system does the magic to create space at the file's location).

Now you have 2 choices once a reference count reaches 0.
1. this is the less efficient one. you can remove the node (set the previous node's pointer to the next node to the node after the one being removed) and call free() on this node. this is not particularly efficient for two reasons. first, you have the call to free() which is expensive (all syscalls are), the other is that you are fragmenting the memory that you have (you might want to have a bigger node there next time).

2. this is what Java might be using. leave the node alone. then when you call the GC (when there is a set percentage of memory left, or you need space which you don't have), you allocate another hunk of heapspace as big as the one you had and then go through the original and copy out all the node with reference count >0 into the new heap space. then you call free() on the entire original heap hunk. this method (in comparison with #1) has only 1 free() call and it also gets rid of the fragmentation (since there is no free space between nodes now).

you would also need to track all the references that have been assigned in a function (using assignment wrappers) and at the end of every scope call a general cleanup function that would decrement the reference counts as the need might be.

EDIT: forgot to mention. method #2 requires n space overhead (where n is the amount of memory you want your heap size to be), when copying the nodes. (just wanted to make this problem more obvious).

EDIT2: Just realized what the third method is ... simply move the nodes up. this has no free() call and you don't need extra space, except that you will probably have to copy nodes byte by byte (memcpy() might not be usable if you are trying to move a node up by less than the space it takes up. I do not know how memcpy() is implemented, whether it is a byte by byte copy or is it a CPU instruction that doesn't do byte by byte copy).

---

### Post by Npl on 2008-08-28
Maaaaan, youre way off.
First, with C (and to a lesser extend C++) the primary problem is to "dereference" all allocated Blocks/Objects, once you miss a call you get a leak. GC should collect unused objects automatically, what you are doing is merely providing an own heap (with a myfree() function that only deallocates if refcount == 0).

And what do you expect to happen if you compact the heap? All pointers would be invalid after this operation, and I doubt it will be less expense than the alloc/free functions.

You should look at GObject, it does what I think is your intent - to have refcounted Objects.

---

### Post by slavik on 2008-08-28
good point ... completely forgot about that. :( (I knew I should've thought more about this ...)

---

### Post by dribeas on 2008-08-29
> **slavik said:**
> this is similar in spirit to my "exceptions ..." thread.

If the spirit is learning how GC are implemented, just google for it. As with exceptions, it takes a whole amount of thinking (years) to get it right. Note that reference counting is NOT garbage collection.

The basics around GC is that you have a set of references that cannot be lost (stack allocated + statics + ...). You mark the objects as 'reachable' (not garbage) and add the references they hold into your set of 'reachable' nodes. Anything that was not reached is garbage and can be treated as such.

Now the smart ideas come from how you do it, but most importantly, what you do once you know what is garbage and what is alive. Usually use memory is compacted (either moving to the beginning of the block or to a completely different block) and all references to the objects updated. This allows for a really fast allocator.

With compacted memory, memory acquisition just needs a pointer to the first free available byte. Every time new is called, that pointer is returned and then moved by the size of the object. Now, GC may be slow, but while C/C++ memory acquisition is slow, Java new just takes a few instructions to complete (I believe it was 4/5) making allocation reaaaallly fast.

Now there are quite some optimizations. First that comes to mind are generational GC. In GC you keep different chunks of memory for recently allocated objects and long lived ones. The idea is that most objects are just used locally, and thus you will get more memory from GC-ing newly created objects that long lived.  Then you can GC your first generation quite often, after an object has lived through a number of GC passes, it is moved to the second generation. Older generations are GC-ed each so many GC passes.

This is a really interesting field (at least to me), just google for it. There are some really interesting articles on tecniques.

   David

BTW: If you want to do reference counting, read into the insights of any shared_ptr implementation (std::shared_ptr -from C++0x- should already be in g++4.3, boost::shared_ptr can be downloaded from [boost]("http://www.boost.org"). That is a nice exercise, reference counting is just a simple technique, you can provide your own implementation and then learn how it is really done out there, and understand the differences.

---

