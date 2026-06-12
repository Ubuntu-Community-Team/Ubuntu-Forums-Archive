---
title: "OO Design"
date: 2009-02-12
forum: Programming Talk
---

### Post by garusher on 2009-02-12
Hi,

I need some suggestions for the following.

I and designing a system which has components and compositeComponents, Will use the composite design pattern i think.

Anyway, I want to apply rules to the construction of a Component or compositeComponent. And potentially there could be an unlimited number of Component, CompositeComponent Combinations.

how can i achieve this?

Thanks
Gary Rusher

---

### Post by CptPicard on 2009-02-12
You really should be a bit more exact about what you're trying to achieve but sounds like you have some sort of Component interface that both CompositeComponents and "normal" Components implement, and the "rules for building" could be implemented as some sort of Factory pattern... that is, you have, say, a method that takes in some kinds of rules as parameters and then builds the Component hierarchy(?) you want.

---

### Post by garusher on 2009-02-12
Hi CptPicard,

Well this is what i am trying to model.

I'm making Custom Cabinets. these cabinets are made up of components like sides, top, etc. However they are also made of compositeComponents like Drawers and Doors.

Now, I believe the Composite Pattern will model the above, however when building (Maybe a factory pattern or Builder) I want to apply rules. Rules like if cabinet opening is 30" high a maximum of two drawers could be added, or 3 fixed shelves or 1 fixed shelf and two adjustable shelves.

Keep in mind that not all compositeComponents are 30" cabinets, they could be 36" or custom height.

Thanks
Gary Rusher

---

### Post by CptPicard on 2009-02-12
This is actually very close to how GUI libraries do their nested components/containers, and the layout manager is the ruleset.

I'm not quite sure I understand the distinction between component and compositecomponent...

---

### Post by garusher on 2009-02-12
Hi,

Well Component is at the atomic level. In my app it could be any of the following things.

Right Rail
Left Rail
Bottom Rail
Top Rail
Center Stile
End Panel
Back Panel
Drawer Side
Drawer Bottom
Drawer Front
Drawer Back
etc.......

WhereAs a CompositeComponent could be
1)    17x30" Drawer, it's made of Drawer side,bottom,front,back.
2)    30x36" Cabinet, it's made of a CompositeComponent(Drawer) 
      and left,right,bottom,top rails,end panel,back panel

Now any of these could have a construction rule applied to it.

Thanks
Gary Rusher

---

### Post by CptPicard on 2009-02-12
Yeah, ok. Yep, looks like you're looking for a tree of components in general, with the distinction that a compositecomponent can have composite parts (is an internal node), while the "components" are always at the leaves.

You just need to define some sort of nice common interface for all of these and then build the tree with some sort of tree-builder that maintains the rules that are in force. Another possibility is to enforce rules inside the components, but I would probably try to figure out some kind of compromise... components know their size etc, rules about what is actually allowed is maintained in the Builder.

---

### Post by nvteighen on 2009-02-12
Hm... I'd make this: a Component super-class which stores common attributes and methods for all components. Then, create children classes that inherit Component for each type of "component": Rails, Doors, Drawer sides, etc. and there you override what you need accordingly.

But what I really don't see is why you need a CompositeComponent class... which would be pretty much a Furniture class (this name seems better to me, actually). Each "composite component" should be a class on its own, IMO, where each component is a kept in an attribute as a reference to a certain Component-derivative class. So, for example, class Drawer would have references to the DrawerSide instances that are needed... And if then you need a Drawer in the Cabinet, you just pass a reference to a Drawer and store it as an attribute. But a CompositeComponent may render itself as useless... as I don't see anything in common among the possible "composites" other than a dimensions attribute... but then you can use the very same Component class... a CompositeComponent is a Component in its own, right?

---

### Post by garusher on 2009-02-12
Hi,

It's really the gang of four (Composite pattern)

Thanks
Gary Rusher

---

### Post by nvteighen on 2009-02-12
> **garusher said:**
> Hi,

It's really the gang of four (Composite pattern)

Thanks
Gary Rusher
[The Sign of Four]("http://en.wikipedia.org/wiki/The_Sign_of_Four")? (The very best of all Sherlock Holmes's adventures, IMO)

---

### Post by garusher on 2009-02-12
Hey CptPicard,

You've given me an idea,

An interface on the component class that takes a rule.
then a method to execute all rules on the component class.

Gary Rusher

---

### Post by CptPicard on 2009-02-12
Yeah, and then recurse down the tree with to enforce the rules downwards...

---

