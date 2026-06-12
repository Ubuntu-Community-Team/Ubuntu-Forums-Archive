---
title: "ordered map?"
date: 2008-08-31
forum: Programming Talk
---

### Post by slavik on 2008-08-31
I recently found out that PHP's associative arrays (dunno if this differs from a regular array) are implemented as an ordered map. My question is, what exactly is ordered in an ordered map? are the keys kept in a sorted order?

This is in contract to Perl's hashes (where PHP takes its roots) which uses a hash table with buckets.

---

### Post by Lux Perpetua on 2008-08-31
Yes, the keys are ordered. This allows the use of a treelike data structure. Another example: STL maps in C++ are also ordered maps.

---

### Post by mdawg414 on 2008-08-31
I believe they are ordered in the order you add elements to the array, unless you specifically change it.

---

### Post by slavik on 2008-09-01
that would explain PHP's not so stellar text processing performance ...

---

### Post by hod139 on 2008-09-01
> **Lux Perpetua said:**
> Yes, the keys are ordered. This allows the use of a treelike data structure. Another example: STL maps in C++ are also ordered maps.

I'm not sure if this is true of all implementations of STL map, but it is definitely true for GNU's and Microsoft's implementations.  GNU uses a red-black tree, not sure how Microsoft does it.

There are performance issues with red-black trees in a map, so there is a common (but not standard) hash_map data structure that both GNU and Microsoft implement with very similar API to the std::map.  There is also a standard unordered_map in the upcoming C++0X standard.  GNU already has it implemented in std::tr1::unordered_map and Microsofts latest visual studio also includes support too.

---

### Post by CptPicard on 2008-09-01
I believe the key-ordered tree-style map is what is being talked about, but there is also the possibility of keeping (arbitrary) order in a hashmap by maintaining an additional linked list among the items. Java API has such a class.

---

### Post by Lux Perpetua on 2008-09-01
> **hod139 said:**
> I'm not sure if this is true of all implementations of STL map, but it is definitely true for GNU's and Microsoft's implementations.  GNU uses a red-black tree, not sure how Microsoft does it.It's not only a question of implementation; it's not true that you can switch out an unordered map for an ordered map without the client noticing. An ordered map requires that the keys have an order defined, while an unordered map does not require this but may have other requirements (such as a hash function). So ordered maps and unordered maps have different interfaces. The STL map, as defined by the standard, is an ordered map. If some implementation gives you an unordered map instead, then it isn't implementing the STL correctly.

---

### Post by dribeas on 2008-09-01
> **CptPicard said:**
> I believe the key-ordered tree-style map is what is being talked about, but there is also the possibility of keeping (arbitrary) order in a hashmap by maintaining an additional linked list among the items. Java API has such a class.

Can you point me to the class in Java? I know of HashMap (most often used as a dictionary) and TreeMap. The first one is a hash table (requires only a hash function), and the second one is a red-black tree. What would that class be?

   David

---

### Post by CptPicard on 2008-09-01
[http://java.sun.com/j2se/1.5.0/docs/api/java/util/LinkedHashMap.html](http://java.sun.com/j2se/1.5.0/docs/api/java/util/LinkedHashMap.html)

---

### Post by dribeas on 2008-09-01
> **CptPicard said:**
> [http://java.sun.com/j2se/1.5.0/docs/api/java/util/LinkedHashMap.html](http://java.sun.com/j2se/1.5.0/docs/api/java/util/LinkedHashMap.html)

oh, I see. The ordering (if I did understand it fully) is 'insertion order'. I was wondering what kind of algorithm they could have made as to keep an ordering on the elements in a list (more efficient than an ordered tree, that is).

Thanks for the reference.

	David

---

### Post by mssever on 2008-09-01
> **slavik said:**
> I recently found out that PHP's associative arrays (dunno if this differs from a regular array)
<off-topic>AFAIK, in PHP associative arrays and regular arrays are really the sime thing. If essence, if you supply a key, PHP uses it. If you don't supply a key, PHP simply uses the next highest available integer for the key.

---

### Post by dribeas on 2008-09-01
> **mssever said:**
> <off-topic>AFAIK, in PHP associative arrays and regular arrays are really the sime thing. If essence, if you supply a key, PHP uses it. If you don't supply a key, PHP simply uses the next highest available integer for the key.

In fact quite <on-topic>, but I believe wrong, nonetheless. From [php array]("http://es2.php.net/manual/en/language.types.array.php") documentation:

> An array in PHP is actually an ordered map. A map is a type that associates values to keys

---

### Post by mssever on 2008-09-01
> **dribeas said:**
> In fact quite <on-topic>, but I believe wrong, nonetheless. From [php array]("http://es2.php.net/manual/en/language.types.array.php") documentation:
How is that different from what I said?

---

### Post by hariputtar on 2008-09-01
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by slavik on 2008-09-01
I was actually wondering if PHP would optimize an array if there are no special keys to be used. Guess not. :(

---

### Post by hod139 on 2008-09-02
> **Lux Perpetua said:**
> It's not only a question of implementation; it's not true that you can switch out an unordered map for an ordered map without the client noticing. An ordered map requires that the keys have an order defined, while an unordered map does not require this but may have other requirements (such as a hash function). So ordered maps and unordered maps have different interfaces. The STL map, as defined by the standard, is an ordered map. If some implementation gives you an unordered map instead, then it isn't implementing the STL correctly.

There are two (popular/efficient) ways to represent an map (a.k.a.  associative array), a balanced tree or a hash table.  This is all I was trying to say.  The implementers of GNU chose to use a balanced tree.  

In the upcoming standard, the are now also allowing the user to be able to use a hash table.  The API is very similar, and I'm not sure why you say a client would notice.  With a hash map, if you let the default hash function be the identity, then the programmer can switch between the two representation without any changes (except the associated performance changes).

---

