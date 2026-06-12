---
title: "Java Collections - Sets/Maps"
date: 2009-02-17
forum: Programming Talk
---

### Post by DeadRobot on 2009-02-17
So my friend and I were trying to devise an algorithm to sort a HashMap or TreeMap based on its values not its keys.  We were only trying to use Sets and Maps (TreeSets, HashSets, TreeMaps, HashMaps), so no arrays, arraylists, lists, or comparators.  


We gave up after an hour or so. :P  

Any ideas on how to do this?


EXAMPLE:
I have a HashMap: (keys are strings on the left, values are Integers on right)
"today" -> 3
"is"    ->  56
"very"  ->  13
"sunny" ->  32

How do you get it to look like this:
"today" -> 3
"very" -> 13
"sunny" -> 32
"is" -> 52

---

### Post by jespdj on 2009-02-18
The Set and Map types in Java do not have an order. You should view a Set as a bag that contains items - the items are all in the bag, but not in any particular order. Likewise, a HashMap does not store items in any particular order.

You can use LinkedHashMap, which is a HashMap that remembers the items in the order that you inserted them. (Under the covers, LinkedHashMap is a HashMap combined with a list to remember the order of the items). Lookup LinkedHashMap in the Java API documentation.

---

### Post by Zugzwang on 2009-02-18
> **jespdj said:**
> The Set and Map types in Java do not have an order. You should view a Set as a bag that contains items - the items are all in the bag, but not in any particular order. Likewise, a HashMap does not store items in any particular order.


I'm afraid that this is incorrect, as *some* set and map type *do* have an order, in particular TreeSet and TreeMap. In these, objects are ordered according to their intrinsic order (hence the keys for TreeMaps and the values for TreeSets must implement the Comparable interface).

---

### Post by CptPicard on 2009-02-18
> **Zugzwang said:**
> I'm afraid that this is incorrect, as *some* set and map type *do* have an order, in particular TreeSet and TreeMap.

But then you're dealing with a SortedSet... Set in itself does not guarantee order and it would be dangerous to assume the implementation.

The OP may be interested in the LinkedHashMap...

---

### Post by Zugzwang on 2009-02-18
> **CptPicard said:**
> But then you're dealing with a SortedSet... Set in itself does not guarantee order and it would be dangerous to assume the implementation.

Uuh? TreeSets guarantee order according to the Java specification. It's just not called "TreeSortedSet" but "TreeSet". No one said that they are casting anything to the class "Set" in their java program or trying to treat all elements in their list the same way. Then it is *safe* to assume this.

---

### Post by CptPicard on 2009-02-18
Well, if you know you are dealing with TreeSet, you have order. But jespdj is right in saying that the Java interfaces Set and Map do not guarantee order -- the sub-interfaces SortedSet and SortedMap do.

You are refining what he says, but he's not *wrong* (at least not from the way I read it). :)

---

### Post by Reiger on 2009-02-18
There's a simple way: implement your own Comparable CustomEntry<K,V> object. Then the code which re-sorts your data merely need to use a SortedSet<CustomEntry> (which relies on the built-in comparator of CustomEntry so all power to you there). Then for(CustomEntry : SortedSet<CustomEntry>) populate the desired data structure.

---

