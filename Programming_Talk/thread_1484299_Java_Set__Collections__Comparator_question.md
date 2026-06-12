---
title: "Java Set / Collections / Comparator question"
date: 2010-05-15
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-05-15
Say I have a very long array of objects of type Person that look like this:

[PHP]public class Person
{
	public enum Gender {MALE, FEMALE};
	public enum HairColor {BROWN, BLACK, BLONDE, GREY};
	
        private String name;
	private int age;
	private Gender gender;
	private HairColor haircolor;
	
	public Person(String name, int age, Gender gender, HairColor haircolor)
	{
		this.age = age;
		this.gender = gender;
		this.haircolor = haircolor;
                this.name = name;
	}
}[/PHP]

What I want to do is traverse the array and add each person into a Set.  But here's the catch, at any given time while traversing the list, I will want to look at my set and see only the most recent entries for a given age in the set.  For example, assume my list only contains people of age 20 to 29.  After going through the first 50,000 entires, my set should only contain 10 people.  These 10 people would be the most recently seen people in the list of age 20,21,22...29.  Basically, upon each insertion, if there is a person of the same age already in the set, that person gets deleted and the person to be added into the set who has the same age is added.  I would also like to do the same with gender and hair color.  I think I can do this by creating a Comparator for each characteristic that I want to filter.  The problem is that I don't see a way to pass this comparator to the Set at construction.  Anyone know how to do this?

---

### Post by Reiger on 2010-05-15
Well you do so at the constructor. But, what you want to do is actually opposite of how a Set works: read the Javadoc on the add() operation to see what I mean.

So for this kind of work you'd probably have to work with a Map type collection.

---

### Post by HotCupOfJava on 2010-05-15
You could also have your Person(s) implement the Comparable interface. If you are comparing on the age, you will need a getter method for age, since your instance variables are private. If  you do something like this, it may be as simple as 

```
if(person1.compareTo(person2) == 0){
  //add your replacing code here
}
```

---

### Post by SNYP40A1 on 2010-05-15
> **Reiger said:**
> Well you do so at the constructor. But, what you want to do is actually opposite of how a Set works: read the Javadoc on the add() operation to see what I mean.

So for this kind of work you'd probably have to work with a Map type collection.

Yes, it is the opposite of how the add function works (preserves current objects instead of replacing).  However, it's only 2 additional lines to check for an object in the set and then remove it before adding the one to replace it.  I also don't see any constructor which takes a comparator, at least for a HashSet:

[http://java.sun.com/javase/6/docs/api/java/util/HashSet.html](http://java.sun.com/javase/6/docs/api/java/util/HashSet.html)

Also, I don't think a map is necessary as I don't want to map objects.  I could see how a map could be used -- use age as key and then keep updating the values to be most current, but I'd rather just have the set do that for me...but for now, I'll use a map unless someone knows a better solution.

---

### Post by Reiger on 2010-05-15
Sorry, the Set I referred to (with the constructor) is actually a TreeSet. That implements SortedSet; which is why a Comparator is actually useful there: navigating the set can be easily implemented using Comparator & tree lookup.

If you insist on a Set you will have to override the add() method to provide the behaviour you want. But now I think about it some more, a Map is not quite as useful for it either: managing the size constraint isn't as straightforward.

---

### Post by Some Penguin on 2010-05-15
It's not entirely clear what you intend for, say, the following case:

insert *Bob, 26, male, brown-haired*
insert *Mothra, millions, female, brown-haired*

Do you remove Bob, because Mothra's also brown-haired, or do you keep Bob, because he's the most recent male and the most recent 26-year-old?

---

### Post by SNYP40A1 on 2010-05-15
> **Some Penguin said:**
> It's not entirely clear what you intend for, say, the following case:

insert *Bob, 26, male, brown-haired*
insert *Mothra, millions, female, brown-haired*

Do you remove Bob, because Mothra's also brown-haired, or do you keep Bob, because he's the most recent male and the most recent 26-year-old?

I just want to store the Person object seen most recently for a given characteristic.  So if I am looking at hair color, then Mothra would be the only brown-haired person in the set.  Bob would have been in the set earlier, but he would have been replaced by Mothra since she was a more recent occurrence.  If instead of filtering by hair, I could filter by age where there would only be one person in the set of each age and that person would be the most recently seen occurrence of that age.

---

### Post by SNYP40A1 on 2010-05-15
> **HotCupOfJava said:**
> You could also have your Person(s) implement the Comparable interface. If you are comparing on the age, you will need a getter method for age, since your instance variables are private. If  you do something like this, it may be as simple as 

```
if(person1.compareTo(person2) == 0){
  //add your replacing code here
}
```

Could do that, but then I'd have to change it for every characteristic I want to sort / filter by...I want to supply the Comparable to the set separately.

---

### Post by SNYP40A1 on 2010-05-15
> **Reiger said:**
> Sorry, the Set I referred to (with the constructor) is actually a TreeSet. That implements SortedSet; which is why a Comparator is actually useful there: navigating the set can be easily implemented using Comparator & tree lookup.

If you insist on a Set you will have to override the add() method to provide the behaviour you want. But now I think about it some more, a Map is not quite as useful for it either: managing the size constraint isn't as straightforward.

The map is not too bad actually because when you insert a pair into the map, it will replace what was there before.  So only trick is the sorting.

---

### Post by Some Penguin on 2010-05-15
Sorting?  I'm not sure where you need it.

If you want to preserve insertion order, a LinkedHashMap works.  You'll want to write classes which wrap the Person structure to provide criteria-specific hashCode() and equals() functions.

---

### Post by SNYP40A1 on 2010-05-16
Sorry Penguin, by sorting, I meant comparison.  I used a TreeSet and that seems to be doing the job pretty well...

---

