---
title: "[SOLVED] [Java] Concerning enumerated data type"
date: 2008-03-28
forum: Programming Talk
---

### Post by TreeFinger on 2008-03-28
I am creating a class that has an attribute that will be an enumerated data type. 

The object containing this enumerated data type will be constructed from a different class. When being constructed the constructor will require this enumerated value as a parameter. 

Where should I create this enumerated data type?

---

### Post by Ramses de Norre on 2008-03-29
In a separate class, an enum. [Example](http://pastebin.com/m774de16e).

---

### Post by alexpwalsh on 2008-03-29
You dont have to make a separate class in order to declare and use Enums ... you can declare them as a static variable as well.

eg: 
Class move has the following enum....

//directions used for movement 
public static enum direction{N, NE, E, SE, S, SW, W, NW}

.... and then use them statically 

eg...
controller.movePiece(_Move.direction.N_);

now how you decide to implement and use them is up to you.
Hope I help....

---

### Post by Ramses de Norre on 2008-03-29
I think you should only do that if the enum is clearly a part of the object your class is representing, if it is an entity of itself (like the direction of my example) your code will be cleaner when the enum is a class of itself. This is, of course, a matter of style and preferences, you're free to use the implementation that suits you best.

---

