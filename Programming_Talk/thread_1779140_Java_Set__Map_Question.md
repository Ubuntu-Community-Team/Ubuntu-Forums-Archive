---
title: "Java Set / Map Question"
date: 2011-06-10
forum: Programming Talk
---

### Post by Kentucky88 on 2011-06-10
I want to store objects in a Set, but I want to be able to look them up using get() similar to map.  This might sound like a stupid question, but I define the equals() to match on only one of the fields of my object and all data needed is contained in that object.  So for my purpose, two objects that are equal according to the equals function are not necessarily the same.  So basically, I have two objects and I want to pull information out of one to put in the other.  A stupid hack is to store the object as the key and the value in a map, but that's a bit wasteful.  Anyone know of a better solution?

---

### Post by PaulM1985 on 2011-06-10
I'm sorry, from the description it isn't exactly clear what you are trying to do.

Can you give a bit more context?
What are your objects?
What are you using them for?
Why are you using a set?  Do they need to be distinct?

Paul

---

### Post by Kentucky88 on 2011-06-10
Basically, I want to do something like this:

public class A {
    private String name;
    private Something something;

    public A(String name)
    {
        this.name = name;
    }
    
    public void setSomething(Something something)
    {
        this.something = something;
    }
    
    @Override
    public boolean equals(Object obj) {
        if (this == obj)
            return true;
        if (obj == null)
            return false;
        if (getClass() != obj.getClass())
            return false;
        A other = (A) obj;
        if (name == null) {
            if (other.name != null)
                return false;
        } else if (!name.equals(other.name))
            return false;
        
        return true;
    }
}

public static void main(String args[])
{
     A a = new A("a");
     A aa = new A("a");
     Something something = new Something();
     a.set(something);
     Something otherthing = new Something();
     b.set(otherthing);

     Set<A> aset = new HashSet<A>();
     aset.add(a);
     A retrieve = aset.get(aa);
}

On the last line, aset.get(aa) returns object 'a' which was inserted into the set on the line above because both a and aa are considered equal according to the equals() function defined above.  Issue here is that Java set does not have a get() method.

---

### Post by Reiger on 2011-06-11
Your get() operation is meaningless. Think about what an unordered set is, think about the consequence of the Set interface being defined in terms of equals() and then think of what your get() operation would do in a proper Set instance.

HashSet requires that the objects you store have hashCode() defined in such a way that it is a substitute for equals(). If not, the Set contract may be broken. So if you redefined equals() you have to make sure you redefine hashCode(), too.

If you want to navigate a set, you need to work with OrderedSets. This leads you to TreeSet, which in turn relies on the objects being Comparable or having a Comparator passed in. Either way, the compareTo() resp. compare() methods must be defined properly w.r.t. equals() because of the Set contract.

EDIT: As you figured out the proper way to do this is to work with a Map of some sort, and indeed it would be wasteful to duplicate objects. So instead of duplicating objects, you might want to redefine how those objects look (or work) so that the keys are not part of the value object (or vice versa: that the values you want are not part of the key object).

---

