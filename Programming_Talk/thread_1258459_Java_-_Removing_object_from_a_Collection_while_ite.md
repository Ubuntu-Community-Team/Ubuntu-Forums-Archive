---
title: "Java - Removing object from a Collection while iterating"
date: 2009-09-05
forum: Programming Talk
---

### Post by PaulM1985 on 2009-09-05
Hi

I recently completed a coursework where I had a Collection, myCollection, and an object that I thought was an Attribute of a thing in the collection, myObject.

Things in the Collection where distinct, so only one of each thing in the collection existed.

I wanted to iterate over the collection and remove the first thing that had an attribute of myObject.  If no things had an attribute of myObject I had to throw an exception.

I used the following code:

```

        for (MyObjects things : myCollection)
        {
            if (things.hasAttribute() == myObject)
            {
                myCollection.remove(things);
                return;
            }
        }
        
        throw new AnException();

```

but was told that I can't remove things from a Collection I was iterating over.  I have done some tests and they seem to work ok.

The question I have is should I contest the marks I lost for this, since it appears to work.

Thanks for any input on this.

Paul

(Since this question is relating to coursework I have really simplified it as I have noticed there is alot of discussion regarding courseworks and the like at the moment.  Additionally, this has already been submitted.)

---

### Post by baizon on 2009-09-05
Java don't allow to remove elements while you are iterating it.
The simplest solution is that you copy your collection and then remove the element, because you're not iterating thru it.

Example:
```

for (MyObjects things : myCollection)
        {
            if (things.hasAttribute() == myObject)
            {
                Map<> tempThings = new HashMap<>(myCollection); // Copys your collection.
                tempThings.remove(things);
                return tempThings;
            }
        }
        
        throw new AnException();

```

---

### Post by nvteighen on 2009-09-05
Hm... Using a while loop should work and is something that should work in any language.

Think about this: when iterating, what you usually do is to increment a counter which is also used as the accessing index in each iteration. Ok, if you remove something, you're reducing the collection's length by 1, therefore already advancing 1 place towards the end of that collection. Implement that idea with a while loop that stop on all end cases and that increments the counter selectively only when needed.

I've done this in C++ with a vector and worked flawlessly (with manual memory management and all)

---

### Post by Ruhe on 2009-09-05
If you want to remove items while iterating, you should use Iterator.

```

Iterator<Integer> it = list.iterator();
while (it.hasNext()) {
  int i = it.next();
  if (i % 2 == 0) {
    it.remove();
  }
}

```

This is the only safe way.

---

### Post by PaulM1985 on 2009-09-06
> **baizon said:**
> Java don't allow to remove elements while you are iterating it.

When you say it doesn't allow you to, do you mean it won't work, or won't compile?

I have run the program and it will both compile and seems to provide the correct results when testing it in JUnit in Netbeans.

I agree, using the remove() method of the Iterator would be a neater solution, which I should have considered, but this seems to work... so is it "correct"?

Paul

---

### Post by Arndt on 2009-09-06
> **PaulM1985 said:**
> Hi

I recently completed a coursework where I had a Collection, myCollection, and an object that I thought was an Attribute of a thing in the collection, myObject.

Things in the Collection where distinct, so only one of each thing in the collection existed.

I wanted to iterate over the collection and remove the first thing that had an attribute of myObject.  If no things had an attribute of myObject I had to throw an exception.

I used the following code:

```

        for (MyObjects things : myCollection)
        {
            if (things.hasAttribute() == myObject)
            {
                myCollection.remove(things);
                return;
            }
        }
        
        throw new AnException();

```

but was told that I can't remove things from a Collection I was iterating over.  I have done some tests and they seem to work ok.

The question I have is should I contest the marks I lost for this, since it appears to work.

Thanks for any input on this.

Paul

(Since this question is relating to coursework I have really simplified it as I have noticed there is alot of discussion regarding courseworks and the like at the moment.  Additionally, this has already been submitted.)

It's generally good to be cautious when changing a structure at the same time you are traversing it. Some constructs in some languages explicitly allow this, some explicitly disallow it (meaning the effect is undefined, rather than giving an error).

I'm not an expert in Java, but in your particular case, it looks like you don't change the structure _while_ you're traversing it, but _after_ you're done traversing it, since you only look for one element, remove it and then quit. I would need very specific reasons to believe that you can't do it that way.

Doing tests for finding out whether something works is fine, but in those cases where the language says the effect is undefined, obtaining the wanted result does not prove anything.

---

### Post by NovaAesa on 2009-09-06
Echoing what Ruhe said, user the iterator() method of the collection and use a while loop with hasNext() as the condition to iterate over the collection. The iterator's remove() method will removed the last acessed item in the collection.

---

### Post by spupy on 2009-09-06
Java allows to remove items from a collection that you are iterating over. There is no compile time exception. However, you can get a runtime exception - ConcurrentModificationException, if you remove and element and that messes the iteration up.
The solution, as already mentioned, is to use an Iterator.

---

### Post by baizon on 2009-09-06
> **PaulM1985 said:**
> When you say it doesn't allow you to, do you mean it won't work, or won't compile?

I have run the program and it will both compile and seems to provide the correct results when testing it in JUnit in Netbeans.

I agree, using the remove() method of the Iterator would be a neater solution, which I should have considered, but this seems to work... so is it "correct"?

Paul

Before compiling I'm getting a error message (Eclipse).

```

Can only iterate over an array or an instance of java.lang.Iterable

```

---

