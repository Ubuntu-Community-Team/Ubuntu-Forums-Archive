---
title: "help with a maze-like data structure"
date: 2009-07-30
forum: Programming Talk
---

### Post by manualqr on 2009-07-30
Suppose you want to store a massive amount of strings in a data structure. You also want to check if a given string has been stored very quickly. I can think of 2 ways to do this: with hashmaps, or .. this 'other' way.

I'm working on an implementation of this 'other' way, but first I want to find out what it's called and where I can find a reference implementation (or pseudo-code). Here's my description of it...

edit:
This is a trie.

The 'other' data structure contains a datum, a list of peers, and a list of children. The idea is that you could make "branches" every time your input data diverges from what's already present. I think if it's implemented correctly, it would have 3 large advantages over hashmaps (even very efficient ones):
1. Insert operations could be done in less time than it takes to compute the hash of the input.
2. There would be no re-hashing overhead, which is substantial in hashmaps.
3. It would be more memory efficient (assuming that the hashmap uses open-addressing). Unless the hashmap uses chained-hashing, 20 - 30% of the memory occupied by the hashmap is unused. As the load increases, insert/lookup performance decreases radically (but if chained-addressing is used, performance degrades gracefully).

Here is a visual for the strings; "hello", "here", "are", "some", "sample", "strings"
```

>--> h - e - l - l - o
|    .       .
^    .       r - e
|    .
*    a - r - e
     .
     s - o - m - e
         .
         a - m - p - l - e
         .
         t - r - i - n - g - s

```

If you know what this is called, I'd love to hear from you. If you know a more efficient way to do the same thing, I'd like to hear about it.

thanks

(I'll be attaching my implementation soon if you want to look at it.)

edit:
If you're interested in this implementation, sorry! I've learned about a better data structure and it's taking me a while to grok it. I'll post the code for that when I get it done, but it won't be done anytime soon.

---

### Post by unknownPoster on 2009-07-30
I know there are a quite a few more knowledgeable people here than me, but I'll give it a shot.

You probably want to look into some sort of directed graph. Some sort of tree would make sense to me.

---

### Post by lisati on 2009-07-30
Looks like some kind of [tree structure]("http://en.wikipedia.org/wiki/Tree_(data_structure)") to me too.

---

### Post by unknownPoster on 2009-07-30
Implementing the tree seems fairly straight forward to me. I'm just not sure what type(s) of traversal would be best for this scenario.

---

### Post by CptPicard on 2009-07-30
[http://en.wikipedia.org/wiki/Trie](http://en.wikipedia.org/wiki/Trie)

(There are many variations on the theme in the field of string algorithms, both trees and graphs)

---

### Post by manualqr on 2009-07-30
Thank you so much!
The wikipedia link on Tries was awesome!

> 
unknownPoster:
You probably want to look into some sort of directed graph.


You're right. For what I'm trying to do, a [directed acyclic word graph]("http://en.wikipedia.org/wiki/Directed_acyclic_word_graph") is much more efficient.

Wikipedia rocks! .. I didn't even know what a graph in computer science was until I read those articles.

---

### Post by lisati on 2009-07-30
> **CptPicard said:**
> [http://en.wikipedia.org/wiki/Trie](http://en.wikipedia.org/wiki/Trie)

(There are many variations on the theme in the field of string algorithms, both trees and graphs)

Thanks - I'd spotted that link earlier today in connection with another thread, but my mental processes didn't make the connection in time to suggest it here.

---

### Post by unknownPoster on 2009-07-30
> **manualqr said:**
> Thank you so much!
The wikipedia link on Tries was awesome!



You're right. For what I'm trying to do, a [directed acyclic word graph]("http://en.wikipedia.org/wiki/Directed_acyclic_word_graph") is much more efficient.

Wikipedia rocks! .. I didn't even know what a graph in computer science was until I read those articles.

Graphs are one of the most abstract data structures in Computer Science that I have encountered. We spent several months in my Data Structures and Algorithms class studying Graph Theory. It's a fairly complex topic which led us to all sorts of other interesting things such as graph traversals, especially Dijkstra's and Prim's Algorithms, NP-Completeness, etc. I could talk about these types of things forever... :)

I enjoy the abstraction and theory of Computer Science much more than I enjoy coding.

---

### Post by CptPicard on 2009-07-30
Well, uhm... graphs are one of the "fundamental" simple data structures really. Arrays, stacks, lists, trees, graphs, hashes. Graphs are just the most general form of "what you can do with things that have links to other items". Of course as such they can model a lot of things, therefore graph theory is applicable in a lot of directions...

---

### Post by manualqr on 2009-07-31
I suppose it's as complicated as you make it..

At any rate, I've been reading up and I found a very interesting paper on DAWGS. Check it out!:

[http://www-igm.univ-mlv.fr/~mac/REC/97-CSA.html](http://www-igm.univ-mlv.fr/~mac/REC/97-CSA.html)

edit:
More resources:
[http://www-igm.univ-mlv.fr/~mac/REC/97-CPM.html](http://www-igm.univ-mlv.fr/~mac/REC/97-CPM.html)

Eek! This same paper costs money from the LNCS site ([http://www.springerlink.com/content/9163t73465k23mj3/](http://www.springerlink.com/content/9163t73465k23mj3/))! that's odd..

---

### Post by Tony Flury on 2009-07-31
From what i can see the structure is great for checking if a particular string has been stored, and realtively simple for insertion/deleting and pretty quick to sort as well,  but it is tough to use it to retrieve an actual string, as you don't have a single reference that uniquely defines that string. It all depends what you need to do with it.

---

### Post by chiisu on 2009-07-31
This thread and those links are scarily fascinating, those goes my weekend  :)

---

### Post by chiisu on 2009-07-31
> **unknownPoster said:**
> 
I enjoy the abstraction and theory of Computer Science much more than I enjoy coding.

I do as well, unfortunately a deficiency in math lead me to switching majors, still trying to fix that...

---

### Post by manualqr on 2009-07-31
> 
it is tough to use it to retrieve an actual string, as you don't have a single reference that uniquely defines that string


It's like a hashmap in this sense - you can't get a value out of it unless you have a key.

Hmm.. ooh! Cool idea!
Any graph/trie structure needs EOW (End-Of-Word) flags.. So if you find an EOW node, designate a void* in it to point to a value. If all your nodes have an isEOW bool, make them isEOW void*'s (if it's NULL, it's not an EOW and if it's not NULL, it's an EOW and the address points to a value).

The value could be a string (e.g if it's a dictionary) or a number (e.g if it's a counter).

I'm going to have a chance to work on an implementation of that CSA paper I posted about earlier. I'll see if I can make EOWs more useful by making them value-references..

---

