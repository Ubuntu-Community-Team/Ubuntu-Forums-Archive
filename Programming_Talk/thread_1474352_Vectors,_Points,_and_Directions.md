---
title: "Vectors, Points, and Directions"
date: 2010-05-06
forum: Programming Talk
---

### Post by kiplingw on 2010-05-06
I have a C++ class for representing 3D coordinates called, say, **Vector3**. It has four components: X, Y, Z, and W. The fourth component W is always present to make working with homogeneous coordinates possible.

I would also like to represent 3D points and directions, perhaps as typedef aliases or through inheritance, I don't know. They are related to each other, but not identical.

They relate to each other as such:
[list]direction + direction = direction[/list]
[list]direction - direction = direction[/list]
[list]point + direction = point[/list]
[list]point - point = direction[/list]
[list]point + point = *N/A*[/list]

Moreover, **Point3** have their W coordinate set to 1 and **Direction3**'s to 0. This is to ensure directions are not translated, but points are.

What is a good approach to enforcing this policy safely and efficiently? If you have a design pattern you'd recommend, I've got the Gang of Four right beside me. I've thought about it for a while and different approaches of templates, inheritance, and access modifiers come to mind but without clarity in this context.

Assume I have a **Vector3** class with a four parameter constructor and **Point3** / **Direction3** need only three parameters.

Thanks  :)

---

### Post by gnometorule on 2010-05-06
I'm not sure this is the best solution (I'm still learning all this myself, so take it with a grain of salt), but it seems one way of doing this would to declare direction and point states in a stripped finite state machine (stripped of actions and output, just transitioning between states). The basic idea would be about as follows:

```

class BaseState{
public:
virtual ~BaseState();
};

class Point: public BaseState{
(code to make this a singleton)
};

class Direction: public BaseState{
(code to make this a singleton)
};


```You then use for all 3 objects (vector, point, direction) the vector object and give that object a private pointer to BaseState, aka,

```

class Vector3{
private:
BaseState* v_State;
(etc.)
public:
void ChangeState(State* v_new_state);
(etc.)
};

```That's the basic outline. You said you have a design book next to you; check that for 'singleton' and 'finite state machine' and decide if you like the idea. You probably also find plenty of hits for these two on gamedev.net as well as they are core game design. If you want to follow this direction, really only read the most basic ways of doing this as what you'd need is as stripped as it'd get (the singleton is just to safe memory; not necessarily needed, so you could do w/o that too if you prefer)

---

### Post by MadCow108 on 2010-05-06
template metaprogramming is perhaps a good solution for this:
your problem is pretty similar to compile time dimensional analysis which has a very nice tutorial in the boost mpl:
[http://www.boost.org/doc/libs/1_42_0/libs/mpl/doc/tutorial/dimensional-analysis.html](http://www.boost.org/doc/libs/1_42_0/libs/mpl/doc/tutorial/dimensional-analysis.html)

another way would be to do it at runtime over polymorphism

---

### Post by kiplingw on 2010-05-07
Hey gnometorule. Thanks for your help. I think the singleton pattern might not be the best approach in this case in the event that I'd like to use more than one point / direction.

MadCow108, I am taking a look at that link now. Thanks both of you.

---

