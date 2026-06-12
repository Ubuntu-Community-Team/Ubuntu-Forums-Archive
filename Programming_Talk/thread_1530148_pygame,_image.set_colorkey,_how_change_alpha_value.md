---
title: "pygame, image.set_colorkey, how change alpha value?"
date: 2010-07-13
forum: Programming Talk
---

### Post by Nihu25 on 2010-07-13
Hello,

I would use alpha value to do an image transparent using this
function, set_colorkey. I'm trying to change the alpha value but i cant.
The function get an object Color which is a tupla (r,g,b,a) but i
tried to assign values in a new variable but does not work in set_colorkey.

Maybe if I knew how to get the other value of alpha image or other method.

I have not run the following tests:
color.a = 128
color [3] = 128
color (3) = 128

The code on my .py is:

[I]       color = image.get_at((0,0))  
       #take 255 in alpha value, but i dont know how change it.
       #Take the pixel color (0,0)
       #red color must be semi-transparent
       #~ print color
       #~ color = (255, 0, 0, 255)
       #~ color = (255, 0, 0, 128)
       #~ color = (255, 0, 0, 0)

       image.set_colorkey(color, RLEACCEL)
return image[/I]


Thanks in advance!

Regards.

---

