---
title: "UML, Dependency, Aggregation"
date: 2011-11-07
forum: Programming Talk
---

### Post by cybo on 2011-11-07
i did a little bit of oo programming and decided to learn more. so i thought it would be a good idea to learn UML, and so far it has been fine. i'm even enjoying drawing all those diagrams. however i can't figure out in which cases i need to use dependency (dashed arrow) and aggregation (empty diamond arrow). i would appreciate if someone could show some of the examples and also examples of their implementation. C++, Java and Python are the preferred languages but if you don't know them i bet i can figure out what you are trying to say.

any help is appreciated

---

### Post by muteXe on 2011-11-08
I will have more time later but:

In my experience, dependency is more at the Use Case level, and aggregation and composition (and inheritance) is more at the implementation/design level. 
In other words, I don't think it makes that much sense to compare dependency with aggregation. Unless my OO definitions are screwed up of course :)

---

### Post by cybo on 2011-11-08
hmm... i guess i should clarify my question. 
i just read a UML 2.0 book, and in chapter 5 it talks about relationships between classes. classes can associate with each other and there are 5 types of associations:

1. dependency - dashed line with a regular arrow
2. association - solid line with a regular arrow
3. aggregation - solid line with an empty diamond
4. composition - solid line with a filled diamond
5. inheritance - solid line with an empty arrow

i know when i would use inheritance, association and composition arrows, but i can't figure out in what cases i would use dependency and aggregation. 

it would be nice to see some uml diagrams and their implementation if possible. languages of choice are Java, C++ and Python. however i would not mind if you implement your diagrams in other languages.

---

### Post by satsujinka on 2011-11-08
The answer is don't use aggregation or dependency.
Aggregation doesn't actually mean anything and any case that you might use it composition is better and more meaningful.
Dependency is complicated, but basically amounts to the same thing. Dependency is only useful is you have static classes or singletons (ie. you need to use Java's Math library then you have a dependency there.) For the most part though, you're going to have objects that have other objects in them (association.) So as a rule of thumb use association not dependency.

---

### Post by muteXe on 2011-11-08
> **satsujinka said:**
> The answer is don't use aggregation or dependency.
Aggregation doesn't actually mean anything 
Doesn't mean anything?  I disagree.

These are the differences between association, aggregation and composition: [http://www.go4expert.com/forums/showthread.php?t=17264](http://www.go4expert.com/forums/showthread.php?t=17264) , with c++ examples.  At least the definitions I have been taught (and by the looks of it other people have too).


I agree that mostly you'll be using association, but i can definitely see where you'd want to use aggregation instead.

Again, from an implementation point of view I've never come across dependency.  I have only seen them on things like Use Case OO diagrams.

---

### Post by satsujinka on 2011-11-10
Just repeating what I was told in my Systems Analysis and Design class.

The linked use for aggregation is really just an association with navigability. And there's already a symbol for that, a line with an arrow pointing to the class you want to access.

So yes, as my teacher told me and I said here. Aggregation has no meaning that isn't better represented elsewhere. Has-a is association and is-a-part-of is composition.

Dependency as I said, is also kind of useless. You should only see them in relation to static classes or singletons.

---

### Post by cybo on 2011-11-14
thanks for the help everyone. i think i got it.

---

