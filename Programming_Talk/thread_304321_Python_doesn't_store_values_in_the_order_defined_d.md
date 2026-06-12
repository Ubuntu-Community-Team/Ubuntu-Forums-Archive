---
title: "Python doesn't store values in the order defined does it?"
date: 2006-11-21
forum: Programming Talk
---

### Post by ironfistchamp on 2006-11-21
Hey all

Is it me or does Python not store values in a data dictionary in the order they are assigned. Either that or the for loop doesn't take them out in that order. I have just created a for loop to go through each value in my data dictionary. It has pulled them out in a rather odd order. They are not in the order defined or alphabetical. Is there a particular order that DDs store values or is it random or is it the loop itself?

Thanks for any replies

Ironfistchamp

---

### Post by ohgod on 2006-11-21
Dictionary objects store values based on the hash of the key.  Basically, a hash algorithm is applied to the key you assign to generate an integer.  That integer is then used to decide which 'bucket' the value is placed into.  If you're curious, check out this link for a better explanation of hashtables/dictionaries:  [http://en.wikipedia.org/wiki/Hashtable]("http://en.wikipedia.org/wiki/Hashtable")

The simple answer is that you can't really depend on the values in dictionary objects being in any particular order.

---

### Post by ironfistchamp on 2006-11-21
Oh that is a pain. Thanks for the reply. Guess I am going to have to write something to put it in the order I want :p

---

### Post by dataw0lf on 2006-11-21
You can simulate an 'ordered dictionary' with a set of tuples inside a list:

```

[('key', 'value'), ('key', 'value')]

```

Or, use the odict module.

---

### Post by dwblas on 2006-11-22
As far as I know, if you wanted to say print it out in order, you would have to append each key to a list, then list.sort, and then lookup and print each dictionary entry from the sorted list.

---

### Post by ironfistchamp on 2006-11-23
Thanks for the replies people 

@dwblas: That is exactly what I did. Thanks for echoing it.

Ironfistchamp

---

