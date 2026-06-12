---
title: "[C++] STL searching: most efficient"
date: 2010-11-24
forum: Programming Talk
---

### Post by erotavlas on 2010-11-24
Hi,

I have to store many informations from text file. The informations are string type and I have to take a decision about how I can store them. I would like to know what is the most efficient way to store them If have to search within them.

I have thought about map std::map<std::string, unsigned int> where the second element is empty or initialized to a dummy value. O(logn) complexity.

I have discard the vector container because it has O(n) complexity.

Is there an efficient way to store the two strings in the same structure/container?

Thank you

---

### Post by worksofcraft on 2010-11-24
HUm... I tried to explain on t[hread about indexing]("http://ubuntuforums.org/showthread.php?p=10155361#post10155361") that the keyvalue of an stl container is not searched for like that. In vector there would be no complexity indexing with a number and on a map it uses a balanced binary tree... are you guys doing some kind of assignment on this? IDK the academic terminology, but you can't make the key searches anymore efficient unless you use quantum computers :P

---

### Post by erotavlas on 2010-11-24
> **worksofcraft said:**
> HUm... I tried to explain on t[hread about indexing]("http://ubuntuforums.org/showthread.php?p=10155361#post10155361") that the keyvalue of an stl container is not searched for like that. In vector there would be no complexity indexing with a number and on a map it uses a balanced binary tree... are you guys doing some kind of assignment on this? IDK the academic terminology, but you can't make the key searches anymore efficient unless you use quantum computers :P

I'm developing a project where I have to search in best efficient way. I can have many thousands of words (sometimes a few millions) and the complexity is fundamental.

What is IDK?

---

### Post by worksofcraft on 2010-11-24
> **erotavlas said:**
> I'm developing a project where I have to search in best efficient way. I can have many thousands of words (sometimes a few millions) and the complexity is fundamental.

What is IDK?

IDK = I Don't Know.

AFIK (As Far As I Know) You cannot make it anymore efficient than balanced tree. You can use hash maps to reduce clustering but if the tree is balanced then clustering should not matter.

---

### Post by Zugzwang on 2010-11-24
Actually, to tell you which approach is most efficient, we have to know what you are actually trying to do. "Store some stuff from a text file" is very generic. It's a little bit like saying to someone "Go to the supermarket and buy some stuff I need" - information is missing.

Apart from that, I'll try making some guesses:
[LIST=1]
[*]There's no need for dummy values or the like. A set of strings, i.e., "std::set<std::string>" is likely to do the same.
[*]It you only want to track which words occurred in a file, a Trie (see the [Wikipedia article]("http://en.wikipedia.org/wiki/Trie")) might do the trick.
[/LIST]

---

### Post by erotavlas on 2010-11-24
> **Zugzwang said:**
> Actually, to tell you which approach is most efficient, we have to know what you are actually trying to do. "Store some stuff from a text file" is very generic. It's a little bit like saying to someone "Go to the supermarket and buy some stuff I need" - information is missing.

Apart from that, I'll try making some guesses:
[LIST=1]
[*]There's no need for dummy values or the like. A set of strings, i.e., "std::set<std::string>" is likely to do the same.
[*]It you only want to track which words occurred in a file, a Trie (see the [Wikipedia article]("http://en.wikipedia.org/wiki/Trie")) might do the trick.
[/LIST]


I have found this [http://www.nedprod.com/programs/portable/nedtries/](http://www.nedprod.com/programs/portable/nedtries/). And what do you think about unordered_map not in C++ standard but implemented by some compiler?

---

### Post by MadCow108 on 2010-11-24
depends on your needs and the data.
unordered maps have worst case complexity O(N) (depending on data and hash function), so it may not be the right choice.
trie's are often a good choice when dealing with text lookup. But without your exact requirements it is just guessing...

why not use a (non-relational) database and save yourself the trouble of implementing it yourself?

---

### Post by C0derBear on 2010-11-24
If you have a lot of plain-text that you need to search through, a dedicated full text search system is better than any of the actual Standard C++ containers that I am familiar with.

I haven't looked into the state of this in a number of years, but this wikipedia link looks like a good starting point: [http://en.wikipedia.org/wiki/Full_text_search](http://en.wikipedia.org/wiki/Full_text_search)

Some full text search algorithms work "out of core" - meaning that they can work with text databases clearly beyond the size of available virtual memory. If you're going to be dealing with truly large data sets then you need to consider something like that.

If you're determined to use a standard C++ container for holding your dictionary then maybe consider using a hash_map<key,value> where key is a numeric (32-bit or 64-bit) value generated from the value content. This plus a tuned hash function for your purposes would probably work well up to some limit of memory use. Note that it would be really obvious when you fell off physical memory limits for your process as there is no guarantee of "locality" in-memory of different nodes in the hash_map<> - your application would thrash the VM system/swap-file and searches into the map would go from ms in execution to seconds- or minutes- to return values.

Best of luck,
-t

---

