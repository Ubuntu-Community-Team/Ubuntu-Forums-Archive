---
title: "python how do i make a sprite jump using parabola"
date: 2013-03-28
forum: Programming Talk
---

### Post by snowlizard31 on 2013-03-28
How do I make a sprite jump using a parabola using python. where do I put the variables for speed, current position etc. in the parabola so I can modify the speed or something. Is there a more efficient way of making a sprite jump?

---

### Post by Tony Flury on 2013-04-01
What do you mean - where do they go ?

you will have a main loop where you calculate the new position of the sprite in each iteration - that position will depend on things like it's current position, velocity etc.

it does sort of depend how far you expect your sprint to jump - it might be more effective to animate the parabola, by changing the sprite image on each iteration, rather than calculate the exact curve.

---

### Post by snowlizard31 on 2013-04-01
I mean where would I put each variable in the equation ( y = a(x-h)2 + k ). In that formula where would I put my players current position velocity ect.

---

### Post by Tony Flury on 2013-04-02
Where did you get the formula from  - surely that would tell you what the terms mean, but it looks like that formula simply calculates the height (y) given the vertical distance (x). If you have a known horizontal velocity then you need to use that to calculate your horizontal distance at each step -> distance = velocity * time, and then use the formula to calculate your new y (assuming you know what a, h & k mean).

I don't think (but I am not an expert) that the formula you gave is a generic formula for a parabola that you can use in all cases - such as starting velocity, height above ground etc. The formula though is similar to (but not the same as) the formula defining a parabola where the "top" is at point h,k - as given here [http://en.wikipedia.org/wiki/Parabola](http://en.wikipedia.org/wiki/Parabola), but i think it is not similar enough to be close to being correct.

If I was doing this -I would write a loop which work it out as follows :

```

#Positions : 
# where vvo is the vertical velocity at the stat of the jump time slice, and a is the acceleration (normally due to gravity), and t is the amount of time since the last iteration.
x1 = x0 + hv * t # x0 is the horizontal position at the stat of the jump, and hv is the horizontal velocity - it never changes.
y1 = y0 + vv + 0.5 * a * t * t  # y0 is the vertical position at the start of the jump, vv is the vertical velocity at the start of the jump, a is the accleration (gravity)

# Draw and swap
move sprite to x1,y1
Increment t
Loop to the top

```

---

### Post by trent.josephsen on 2013-04-02
vv * t in line 4

---

### Post by Tony Flury on 2013-04-02
Well spotted :-). Basic calculus failed me.

---

### Post by Nytram on 2013-04-03
> **snowlizard31 said:**
> How do I make a sprite jump using a parabola using python. where do I put the variables for speed, current position etc. in the parabola so I can modify the speed or something. Is there a more efficient way of making a sprite jump?

Another way of doing something similar, and that's used a lot in games, is simply increase and decrease the sprite's vertical position, while at the same time moving in a horizontal direction. I'm not sure if that makes an exact parabola, maybe it's more of a sawtooth, but it looks like one.

---

### Post by trent.josephsen on 2013-04-03
> **Tony Flury said:**
> Well spotted :-). Basic calculus failed me.

I have found it to be generally true that the more math you learn, the harder it is to remember the basics. I, for instance, can factor quadratic equations in my head, but subtraction? I'll need pencil and paper. And I've long since forgotten how to find the volume or area of anything without using calculus... :)

---

### Post by snowlizard31 on 2013-04-03
Thanks guys!

---

