---
title: "Generating a Unique set of Items in Java"
date: 2011-10-22
forum: Programming Talk
---

### Post by karlson on 2011-10-22
I have a slight problem with the project I am doing.

I have a set of Double values and I need to generate a subset of unique values.  HashSet, while seemingly best suited for this purpose doesn't work since it doesn't allow for a custom comparator for insertion.

Is there something that would be useful in this case other then a TreeMap?

---

### Post by PaulM1985 on 2011-10-22
I don't quite understand your issue.  Why can't HashSet be used to create a set of Doubles?  Why do you need a custom compare method for a Double? Is standard comparing not what you need?  If not, it doesn't sound like you want unique Doubles.

What exactly are you trying to do?

If I have missed the point, why don't you create your own class and implement the Comparable interface and use this class in the HashSet so you now have your own custom comparison function?

Paul

EDIT: Are you trying to do a fuzzy compare?

---

### Post by ofnuts on 2011-10-22
> **karlson said:**
> I have a slight problem with the project I am doing.

I have a set of Double values and I need to generate a subset of unique values.  HashSet, while seemingly best suited for this purpose doesn't work since it doesn't allow for a custom comparator for insertion.

Is there something that would be useful in this case other then a TreeMap?
I haven't got any argument against the TreeSet in this case. However, there may be a faster method: store all your items in a list, sort the list, and scan the list and remove consecutive duplicates.

---

### Post by karlson on 2011-10-22
> **PaulM1985 said:**
> I don't quite understand your issue.  Why can't HashSet be used to create a set of Doubles?  Why do you need a custom compare method for a Double? Is standard comparing not what you need?  If not, it doesn't sound like you want unique Doubles.

What exactly are you trying to do?


If you work with Doubles, which may have at one point been stored as Float or strings, you could wind up with 14.55 looking like 14.5499999999999999922355, so you need to compare for equality by doing (Math.abs(d1 - d2) < EPSILON).

C++ has __DBL_EPSILON__ defined specifically for that purpose.

> 
If I have missed the point, why don't you create your own class and implement the Comparable interface and use this class in the HashSet so you now have your own custom comparison function?

I was kinda hoping to avoid that.

---

### Post by karlson on 2011-10-22
> **ofnuts said:**
> I haven't got any argument against the TreeSet in this case. However, there may be a faster method: store all your items in a list, sort the list, and scan the list and remove consecutive duplicates.

That actually is O(nlogn) same a the TreeMap and it may actually be slower because of the number of passes you need to make through the list.

---

### Post by ofnuts on 2011-10-22
> **karlson said:**
> That actually is O(nlogn) same a the TreeMap and it may actually be slower because of the number of passes you need to make through the list.NLogN for the list sort and one linear pass (N)(you perform one and only one comparison for every item).

---

### Post by karlson on 2011-10-22
> **ofnuts said:**
> NLogN for the list sort and one linear pass (N)(you perform one and only one comparison for every item).

Requires implementation of something like a STL's lower_bound or upper_bound with a custom comparator.

---

### Post by ofnuts on 2011-10-22
> **karlson said:**
> If you work with Doubles, which may have at one point been stored as Float or strings, you could wind up with 14.55 looking like 14.5499999999999999922355, so you need to compare for equality by doing (Math.abs(d1 - d2) < EPSILON).

C++ has __DBL_EPSILON__ defined specifically for that purpose.


I was kinda hoping to avoid that.
Not that simple, see: 
[http://realtimecollisiondetection.net/blog/?p=89](http://realtimecollisiondetection.net/blog/?p=89)
[http://www.cygnus-software.com/papers/comparingfloats/comparingfloats.htm](http://www.cygnus-software.com/papers/comparingfloats/comparingfloats.htm)

It should also be noted that with the method your mention, if you have x,y,z, slightly less than epsilon apart, you find that x==y, y==z, but x!=z.

In practice, using  a plain equality is very often sufficient (Double.equals() is roughly that, outside of NaN, if the binary representations are the same, the numbers are equal) , inaccuracies being taken care of where they really matter...

---

### Post by karlson on 2011-10-22
> **ofnuts said:**
> 
It should also be noted that with the method your mention, if you have x,y,z, slightly less than epsilon apart, you find that x==y, y==z, but x!=z.

What I actually find is x!=y and y!=z.

> 
In practice, using  a plain equality is very often sufficient (Double.equals() is roughly that, outside of NaN, if the binary representations are the same, the numbers are equal) , inaccuracies being taken care of where they really matter...

Not in my case.  As I mentioned this problem shows up fairly consistently when there is a conversion from float to double.

---

### Post by ofnuts on 2011-10-22
> **karlson said:**
> What I actually find is x!=y and y!=z.



Not in my case.  As I mentioned this problem shows up fairly consistently when there is a conversion from float to double.Does that mean that the same floats where converted to different doubles?

---

### Post by karlson on 2011-10-22
> **ofnuts said:**
> Does that mean that the same floats where converted to different doubles?

Haven't tested that but if I have one straight up as a Double and the other one converted from a Float this happens.

---

### Post by karlson on 2011-10-24
Just to illustrate the point:
```



public class MainClass {

  public static void main(final String args[]) {

	  Float a = 1.44f;
	  Float b = 1.44f;
	  Double mult1 = 1.2;
	  Double mult2 = 1.2;
	  
	  Double ad = a.doubleValue();
	  Double bd = b.doubleValue();
	  
	  System.out.println("A:" + ad.toString() + " B: " + bd.toString() + " Mult: " + mult1*mult2);

  }
}

```

Result:
```

A:1.440000057220459 B: 1.440000057220459 Mult: 1.44

```

---

### Post by 11jmb on 2011-10-24
> **karlson said:**
> Requires implementation of something like a STL's lower_bound or upper_bound with a custom comparator.

It was my understanding that in java a hash set does not use comarators, but rather, the hashCode and equals methods. In order to use a hash set to accept a specific tolerance, you would have to create your own custom class with their own equals and hashCode methods.

This is going to be a bit of a pain because the Double class is final, so you would need to build a custom wrapper class.

If this seems like too much work or unnecessary for your purposes, stick to a TreeSet which accepts custom comparators and take the slight performance hit.

---

### Post by 11jmb on 2011-10-24
> **karlson said:**
> That actually is O(nlogn) same a the TreeMap and it may actually be slower because of the number of passes you need to make through the list.

Actually, a Tree set is O(log[n]) average case for placement and searching, O(n) worst case. Traversal will be O(nlog[n]).

Think of it as maintaining a sorted list contrary to sorting a list

---

### Post by karlson on 2011-10-24
> **11jmb said:**
> It was my understanding that in java a hash set does not use comarators, but rather, the hashCode and equals methods. In order to use a hash set to accept a specific tolerance, you would have to create your own custom class with their own equals and hashCode methods.

This is going to be a bit of a pain because the Double class is final, so you would need to build a custom wrapper class.

If this seems like too much work or unnecessary for your purposes, stick to a TreeSet which accepts custom comparators and take the slight performance hit.

Figured as much.  Thanks everyone...:(

---

