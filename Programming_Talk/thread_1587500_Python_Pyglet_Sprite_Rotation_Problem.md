---
title: "Python Pyglet Sprite Rotation Problem"
date: 2010-10-03
forum: Programming Talk
---

### Post by MiniStephan on 2010-10-03
Okay, so here's the idea.  I want to rotate my sprite in place, or, around the center.  Unfortunately, this doesn't work because the pyglet.sprite.Sprite.rotation moves it around the (x, y) coordinates (the bottom left corner).

Does anyone know how to offset the point that the image is rotated around? I tried changing anchor_x and anchor_y, but it didn't seem to do anything.

---

### Post by MiniStephan on 2010-10-04
Alright, I figured it out.  I was changing the anchor_x and anchor_y wrong; you have to change the variables for the IMAGE not the variable itself  Here is the correct idea:

[PHP]my_sprite = pyglet.sprite.Sprite("image") #create the sprite

# set it so it will rotate around the center
my_sprite.image.anchor_x = my_sprite.image.width / 2
my_sprite.image.anchor_y = my_sprite.image.height / 2

# now you can change the rotation
my_sprite.rotation = 45     # the rotation value is in degrees, with 0 as north[/PHP]
Note: this will set the center of the sprite to the sprite's (x, y) position.

Hopefully this will help someone.

---

### Post by greenmoss on 2011-06-05
> **MiniStephan said:**
> Hopefully this will help someone.

It helped **me**; thanks and +1!

---

