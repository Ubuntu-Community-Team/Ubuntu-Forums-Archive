---
title: "How to implement a file-based binary search tree structure"
date: 2011-12-04
forum: Programming Talk
---

### Post by wirate on 2011-12-04
I am looking to implement a binary search tree with around 10  million nodes. Each node will contain about 32 bytes of data. Making  the tree completely in memory and then dumping it into a file is  dangerous because I'm not yet sure of the number of nodes in the tree. A rough idea on how to do this will be helpful because I'm not  language-specific yet.


The purpose of the tree is to be an inverted index for a list of  related pages against keywords. It is part of a search engine project.  Thank you for your time.


Also any suggestions on how to keep the tree balanced as keywords keep coming randomly? Can I just trust that they will be random enough to keep the tree fairly balanced?

---

### Post by ofnuts on 2011-12-04
> **wirate said:**
> I am looking to implement a binary search tree with around 10  million nodes. Each node will contain about 32 bytes of data. Making  the tree completely in memory and then dumping it into a file is  dangerous because I'm not yet sure of the number of nodes in the tree. A rough idea on how to do this will be helpful because I'm not  language-specific yet.


The purpose of the tree is to be an inverted index for a list of  related pages against keywords. It is part of a search engine project.  Thank you for your time.


Also any suggestions on how to keep the tree balanced as keywords keep coming randomly? Can I just trust that they will be random enough to keep the tree fairly balanced?
There are algorithms to maintain a tree roughly balanced despite worst case insertion order. Look at[ "AVL trees"]("http://en.wikipedia.org/wiki/AVL_tree") for instance.

Maybe you are re-inventing the wheel and should instead look at some light-weight SQL embedded engines such as [SQLite]("http://www.sqlite.org/").

---

### Post by wirate on 2011-12-04
Maybe I am kinda re-inventing the wheel but that still is a huge task for me :D I am a second year computer science student and this is a course project for data structures and algorithms. So I cant use anything that does the DS part for me. Thank you for the answer :)

---

### Post by wirate on 2011-12-06
bump. I need help

---

### Post by gnometorule on 2011-12-06
Similarly to suggesting an AVL tree, you could use a red-black tree. It should be performance effective - eg, it is used to keep track of the memory regions of a processes' address space in the Linux kernel. The routines that you need to code up are a little lengthy, and it takes some thinking when first seeing it, so you can't just copy them in here. I learned it from 

[http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-046j-introduction-to-algorithms-sma-5503-fall-2005/](http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-046j-introduction-to-algorithms-sma-5503-fall-2005/)

which, for a computer science major, I warmly recommend (it's close to being a must-have). However, there are probably online sources you could google. The tree is self-balancing, operates in O(lgn) time, and allows free growth and shrinking as you appear to need.

I don't understand your memory vs file concern. Absent that, you should read up on, understand, then code up (with pseudo-code algorithms from a source like the book above easy) a rb-tree, which in my understanding of your question handles your problem. 

P.S.: The Linux kernel has routines for rb-trees, eg, rb_entry(). In my system, the header file is at

include/linux/tbtree.h

Using those might speed you up, or not: they could be in different directories, you still need to understand them, etc. As those trees are important, it probably will help you more to do it from scratch.

---

### Post by schauerlich on 2011-12-06
Well, if you're looking for a tree structure with good performance when the tree is partially on disk and partially in memory, you might want to look into [some form of B-tree](http://en.wikipedia.org/wiki/B%2B_tree). B-trees can get complicated to implement, though, so if you're not familiar with how they work it might be more worth your time to stick with an AVL tree.

---

### Post by gnometorule on 2011-12-06
Aren't B-trees more a theoretical construct not much used in practice (eg, for the reasons you allude to - complicated)?

---

### Post by gnometorule on 2011-12-06
I don't have my book handy; but also, weren't the theoretical performance increases mostly in limit cases less relevant for practical implementations?

---

### Post by schauerlich on 2011-12-06
> **gnometorule said:**
> Aren't B-trees more a theoretical construct not much used in practice (eg, for the reasons you allude to - complicated)?

No. They're commonly used by filesystems and databases for the reasons I mentioned (minimizing disk IO). Wikipedia lists NTFS, ResierFS, JFS, Microsoft SQL Server, SQLite, etc, all using B+ trees. And that's just that specific variant of B-trees.

---

### Post by gnometorule on 2011-12-06
Ah. I'm confusing them with another tree then that outperformed rb, but mostly in unimportant limit situations. Thanks for clarifying.

---

### Post by schauerlich on 2011-12-06
> **gnometorule said:**
> Ah. I'm confusing them with another tree then that outperformed rb, but mostly in unimportant limit situations. Thanks for clarifying.

B-trees aren't binary search trees. The try to be wider than they are deep in order to minimize the average depth of a piece of data. Since each level you go down is another potential disk access, keeping the tree as flat as possible will greatly speed things up. If one disk access costs the same amount of time as dereferencing 1000 pointers and comparing memory contents, you'd rather have a tree of depth ~10 and process 100 things in memory per node than do 1000 disk accesses with only one comparison each.

---

### Post by wirate on 2011-12-06
Red-black trees look like a good idea. However, AVL and B-trees are way too complex for me and their advantages are not very much required. I am not looking for heavy disk I/O optimization. Completing the project is a big enough challenge here.

Let me be a little more descriptive now. In my search engine project, I will have a list of keywords and their IDs, a list of webpages and their IDs and a tree relating each keyword to a number of pages.

Each node is supposed to be representing a keyword and contain a pointer to a list of webpages that are relevant for that keyword along with their relevance scores. So when the user enters a query in the search engine, the program looks for that keyword in the tree and displays the list of related webpages in decreasing order of their relevance scores. Fairly simple.

Now the problem is that all these lists have to reside on disk and they have to be read in at the time of executing the query. You can see from the above description that I am a newbie :P Please help me out :(

---

### Post by schauerlich on 2011-12-06
Red-Black trees are more complex to implement than AVL trees, IMO. Once you learn the rotations, AVL is pretty simple. Red-Black, not so much.

---

