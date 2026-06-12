---
title: "Simple math/opengl question.."
date: 2010-05-17
forum: Programming Talk
---

### Post by kahootbot on 2010-05-17
This is very specific to my application, and should be pretty basic, but I can't seem to figure it out. I'm hoping someone can at least point me in the right direction.

I'm applying a rotation to an image with glRotatef, which can take all 360 degrees for an angle (although I think it uses Radians). I'm confused though about how to make in move in the direction of the angle. How do I increment/decrement X and Y in such a way as to move in the direction of the rotation? I'm sure the same formula would apply to the bullet of a ship firing in any direction like the old arcade games. 

I think it has to do with Trigonometry, which I admit I didn't have much of in school. I'm hoping someone could at least point me in the right direction of what to look for? Thanks. :)

---

### Post by JwB Zoofware on 2010-05-17
Hi, I'm not too familiar with graphic programming, but this might help (apologies if its way out :P):

[http://www.delphiforfun.com/programs/math_topics/polar-cartesian.htm](http://www.delphiforfun.com/programs/math_topics/polar-cartesian.htm)

i.e. if your pointing at 30 degrees and want to move 10 forward then:

x = 10 * cos(30 d)
y = 10 * sin(30 d)

---

### Post by kahootbot on 2010-05-17
You hit the nail on the head - Thanks! Just what I was looking for! :popcorn:

---

### Post by oedipuss on 2010-05-18
I think depending on the order of the transforms, you could do that without involving sine / cosine calculations.
For instance, to move 10 units in a 30 deg. from horizontal direction you could first translate to +10,0 (the 0 deg. direction) and then rotate the entire thing 30 degrees. 
I think opengl generally works like that. Look up opengl transformation order for more details.

---

