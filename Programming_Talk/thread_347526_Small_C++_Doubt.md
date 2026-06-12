---
title: "Small C++ Doubt"
date: 2007-01-27
forum: Programming Talk
---

### Post by studiesrule on 2007-01-27
I've been brushing up my C++ skills, and I'm confused at a particular point, and I was hoping some of you would help clear it up. 

Basically, I want to define an interface called Entity. This is a entity that I hope to use in a game, and has some basic functions. However, it has certain pure virtual functions, for example GetDimension, which gets the metric of the entity (for example a rectangle has width and height, or a circle has just a radius). Now this GetDimension must be implementation specific, so I thought the virtual keyword is appropriate. So I've written it as:
```

virtual Dimension GetDimension() = 0; // function that gets dimension.

```

However, as an interface, I'd like to pass Entity into functions, which use the functions of the Entity. Anyhow, I can't declare an Entity variable, and must derive. So, whatever I pass into this function must have the definitions of the virtual function (getDimension). However, when I pass it into another function as:
```

bool hasCollided (Entity other); // Function to determine if these two shapes have collided

```

I get a complier warning:
> 
entity.h:49: error: cannot declare parameter ‘other’ to be of abstract type ‘Entity’
entity.h:37: note:   because the following virtual functions are pure within ‘Entity’:
entity.h:49: note:      virtual bool Entity::hasCollided(Entity)


Where have I gone wrong? How should I correctly implement it? I've gone through my reference book, (Bjourne Straustop's Guide), and I can't seem to find any relevant details, so I thought I would ask here.

Thanks a bunch in advance

---

### Post by LordHunter317 on 2007-01-27
Your issue is that you're trying to pass-by-value an abstract type.  You cannot do that.

You should never, ever pass a member of class hieharchy by value anyway.  Look at the C++ FAQ on the slicing problem.  

You must pass by pointer or reference, depending on what is appropriate.

BTW, I think you may be approaching this problem wrong.  If you're not representing everything as a series of polygons, you're like to run in to trouble handling dimensions.  You probably want to use generics.

---

### Post by studiesrule on 2007-01-27
Thanks a lot! I just added the reference tag, and looking at it, actually wanted to reference, and not pass-by-value. I don't think I'm looking for generics. Different shapes would collide differently, so the hasCollided function would be entirely different for two shapes. Again a big thanks to you.

---

### Post by LordHunter317 on 2007-01-27
The determiniation for the need for generics isn't if the actual implementation of an algorithm is different.

The general rule is: if you have different behaviors and same data, you can use inheritance.  If you have the same behavior and different data, you use templates.  You can use templates with different implementations of the same behavior and different data, but it's not always the best approach.

My concern is hte data part: I really doubt you'll want to do collision detection using the same data if you're colliding between a circle and a rectangle.

---

