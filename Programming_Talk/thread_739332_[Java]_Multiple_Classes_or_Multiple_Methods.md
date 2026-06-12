---
title: "[Java] Multiple Classes or Multiple Methods?"
date: 2008-03-29
forum: Programming Talk
---

### Post by TreeFinger on 2008-03-29
I am creating the first class of a java program I am planning to create. The plan is that when an object of this class is constructed, the parameters will decide which methods will be available for this certain object. That means many of the methods inside this class will NOT be available for objects.

Should I just be making separate classes?
If I did make separate classes, pretty much each of them would be constructed multiple times.

---

### Post by CptPicard on 2008-03-29
I am not quite sure what you're doing there, but my immediate reaction would be that you do not want some kind of a God Object that has all sorts of unimplemented methods that just throw exceptions or return nulls when called.

You certainly should think of some kind of an inheritance hierarchy in terms of is-a -relationships and return objects of classes that contain only appropriate methods. Then, you might consider making use of some kind of a factory pattern -- use a static "build" method, for example, to examine the parameters you're passing in, construct an appropriate object and return that from your method.

---

### Post by TreeFinger on 2008-03-29
Thanks for the reply, but I have another question now as I was thinking about implementing different Classes.

My program is a card game. There are several Card Types and Each Card Type could have a different value. Each Card Type has a different action.

I want to be able to store each Card Object in the same Collection.

Is this possible if each of my 'cards' is a constructed from a different class? Does a collection have to be filled with objects of the same class?

---

### Post by CptPicard on 2008-03-29
Well, looks like you've got some kind of an abstract base class Card, extended by some CardTypes, that then override some method "action".

Read up on Java's Generics, what you can put into collections and get out of them parametrized in certain ways is somewhat subtle... in this case you'd want a Collection<Card>.

---

