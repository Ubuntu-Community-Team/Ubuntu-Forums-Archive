---
title: "Java programming of linked lists"
date: 2010-12-04
forum: Programming Talk
---

### Post by 404wanderer on 2010-12-04
Hello all,

it's been a long time since I've done any Java programming and I am struggling with linked lists.

I read a set of strings from a file into a linked list and setup a list iterator. I then need to extract items from this list to a second linked list. The way I am currently doing this causes a concurrent modification exception. Can anybody assist at all? Please be gentle....

Snippits of the code -

```


    public static LinkedList llist = new LinkedList();
    private Iterator li=llist.iterator();
    public static LinkedList llist_full = new LinkedList();
    private Iterator li_full=llist_full.iterator();


//So the idea is I have a complete list of words in llist_full.
// I then extract a subset of these to a second linked list 

  public void extract_words (int length)
    {
        String str=null;
        while ((str=read_word())!=null)
        {
            if (str.length()==length)
            {
                llist.add(str);
            }
        }
    }


public String read_word ()
    {
        String word=null;
        if(how_many_words_full()!=0)
        {
            if (li_full.hasNext())
            {
                String tword=(String) li_full.next();
                word=tword;
                li.put(word);
                System.out.println("extracted word - " + word);
            }else
            {
                li_full=llist_full.iterator();
            }
        }
        return word;
    }


```

I can't really understand why the read_word function throws a concurrent modification exception.

Any help would be appreciated.

Cheers,

wanderer

---

### Post by NovaAesa on 2010-12-04
Here's a quote from Oracle's online docs [http://download.oracle.com/javase/6/docs/api/java/util/LinkedList.html:](http://download.oracle.com/javase/6/docs/api/java/util/LinkedList.html:)

> The iterators returned by this class's iterator and listIterator methods are fail-fast: if the list is structurally modified at any time after the iterator is created, in any way except through the Iterator's own remove or add methods, the iterator will throw a ConcurrentModificationException. Thus, in the face of concurrent modification, the iterator fails quickly and cleanly, rather than risking arbitrary, non-deterministic behavior at an undetermined time in the future."

Think about when you are creating the iterator and what you are doing to the lists before iterating through them.

---

### Post by 404wanderer on 2010-12-05
<Thick User>

ok, so when I do -
```

llist.add(word)

```

isn't that adding to the list using the list iterator's own add method?

</Thick User>

---

### Post by NovaAesa on 2010-12-05
When you use llist.add(word), this is adding a word to the list using the llist's add method. llist is an instance of a LinkedList.

First of all I am assuming that the variables declared at the start of your code are meant to be instance variables of a class (the code is incomplete so it's trick to tell if this is the case or not).

It appears that you instantiate your lists, then instantiate your iterators. By the time you want to use the iterators to traverse the list, the list has already been modified and the iterators are no longer "in sync" so to speak.

What you should probably do instead is declare your iterators as local variables, and instantiate them immediately prior to their use.

EDIT: Do you know about generics in Java? It's always a good idea to use generics when using the container classes.

---

### Post by 404wanderer on 2010-12-05
Thank you for that. I rethought my code and changed my list iterators to locals. A bit of restructuring and the code worked.

I've not heard of generics. Is there any text in particular you would recommend?

Cheers, wanderer.

---

