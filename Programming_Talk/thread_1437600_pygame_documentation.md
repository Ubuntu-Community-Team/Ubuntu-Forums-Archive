---
title: "pygame documentation ??"
date: 2010-03-24
forum: Programming Talk
---

### Post by Tony Flury on 2010-03-24
I am trying to get to grips with pygame and using the "reference" documention : [http://www.pygame.org/news.html](http://www.pygame.org/news.html) - which to me seems to the be official documentation.

However I am noticing significant gaps in the documentation, such that using the docs alone it is impossible to actually write useful working code.

On the classes I have looked at, while the methods are documented, none of the attributes are listed at all (or if they are the documentation is pretty sparse) - for instance from the documentation alone what attribute or method do i use to set or change an image on a sprite - I can guess, but it is not actually documented.

Is there an exhaustive list of classes, attributes, methods etc.

As an example the pyGTK documentation is excellent, it documents all of the classes, attributes, methods, as well as documenting the Base class, so you can drill down and identify lower level attributes and methods that might also be used (or have been extended, overriden etc).

---

### Post by lavinog on 2010-03-24
> **Tony Flury said:**
> 
for instance from the documentation alone what attribute or method do i use to set or change an image on a sprite - I can guess, but it is not actually documented.


Are you wanting to modify an image or change the image.
changing the image should just require reassigning it.
You can't modify the sprite in place, I think you need to modify a surface, then assign that surface to a sprite.

Also keep in mind that there are significant changes between the version documented on the website, and the version of pygame in karmic.

---

### Post by Tony Flury on 2010-03-25
as I say - I can guess that the sprite class has an image attribute, I have seen it used in a number of examples - but no mention in the actual documentation.

I have also seen implications (although no actual code) that suggest that you can assign a sprite in such a way that it displays only part of an image, and you can thereofre create animations by displaying differing slices in turn of one image file (rather than loading up different images) - i can't find a code example of this though - so have no idea of what attribute i might use to acheive this.

Finally I would assume that you can move a sprite by changing the top and left (or center) - can you move an entire sprite group in the same way - or do you have to loop round each sprite and move it ?

Again none of this is covered in the documentation. 

ty for the hint about karmic - I am still on 8.04 - Hardy Heron - so at least that wrinkle wont impact me.

---

### Post by lavinog on 2010-03-25
> **Tony Flury said:**
> as I say - I can guess that the sprite class has an image attribute, I have seen it used in a number of examples - but no mention in the actual documentation.

I have also seen implications (although no actual code) that suggest that you can assign a sprite in such a way that it displays only part of an image, and you can thereofre create animations by displaying differing slices in turn of one image file (rather than loading up different images) - i can't find a code example of this though - so have no idea of what attribute i might use to acheive this.

The sprite is a base class, you can give it whatever attributes you want.
I think loading tilesets involve subsurfaces.
then you control the subsurfaces with the sprite.

> 
Finally I would assume that you can move a sprite by changing the top and left (or center) - can you move an entire sprite group in the same way - or do you have to loop round each sprite and move it ?

You create an update method for each sprite class.  The update method can be used to move the sprite.  Then when you call the group.update...it will pass the arguments to each sprite.update in the group.




> 
Again none of this is covered in the documentation. 


I think you are expecting a lot out of sprites...They are meant to be subclassed, not used directly:
> 
The classes are fairly lightweight and only provide a starting place for the code that is common to most games.

The Sprite class is intended to be used as a base class for the different types of objects in the game. 


Many things are covered in tutorials
Use the search on the internet button on the documentation page.

> 
ty for the hint about karmic - I am still on 8.04 - Hardy Heron - so at least that wrinkle wont impact me.

The version of pygame in hardy is even older.

---

### Post by Tony Flury on 2010-03-25
I appreciate the point about Sprites being a base class which can be extended - but without knowledge of the properties and methods of the base class(es) it is impossible (or at least very difficult) to extend the functionality.

Reading code only helps so far to be honest (most of the code I have found is not commented at all, or only sparesley - so it does not really explain what the actual code does) - and Search on the internet button only works from the reference website for those methods that are already documented - so will never show usage for the attributes - as they are not documented.

for instance I know (or can at least guess) that a atrribute named "image" exists - but it is not actually mentioned and so it is impossible to search for uses of it.

and I think (given some code snippets I have seen), that it is possible to get a sprite to display a section of an image given the full image and a rect (which defines a part of the image) - I have seen some code whch will create a set of rects given the number of frames per row, padding etc - but the code that showed how those rects are then used to actually set the sprite up is nowhere to be found.

What i Have in mind is as follows : 

A helper class which will take an image and create a set of "frames" - these maybe implemented as rects or something else see above, which are based on a regular layout of the base image. This class will also enable the creation of one or more sub sets - so you can have more than one animation sequence in a single file.

An extended sprite class which will can take either a static image, or a set of frames (as above). The sprite will also be extended to support a state value (with an associated animation set if neccessary), and support various animation types - timed (so many fps) or animated per move - looping vs stop reverse etc.

but until I know how to tell a sprite how to display just a sub part of an image instead of the whole image, then the whole thing is dead.
I will investigate manipulating the surface of a sprite - but again it is guess work that the attribute is ".surface" as that is not documented.

---

### Post by lavinog on 2010-03-25
I am pretty sure all of the methods of sprites are documented.

The image attribute is just added to the class...it isn't part of the original sprite class.

for example:
[http://www.google.com/codesearch/p?hl=en#nz84cPv7_9c/~jantz/pythonkurs/material/tag4/pacman.tar.gz|Y0Y9q1zA8ec/pacman.py&q=file:\.py$%20pygame.sprite.Sprite&d=5](http://www.google.com/codesearch/p?hl=en#nz84cPv7_9c/~jantz/pythonkurs/material/tag4/pacman.tar.gz|Y0Y9q1zA8ec/pacman.py&q=file:\.py$%20pygame.sprite.Sprite&d=5)

```

class PacMan(AnimatedSprite):
    speed=TILESIZE

    def __init__(self, x, y):
        frame1=GRAPHICS.subsurface(Rect(TILESIZE*4,0,TILESIZE,TILESIZE))
        frame1.convert()
        frame2=GRAPHICS.subsurface(Rect(TILESIZE*4,TILESIZE,TILESIZE,TILESIZE))
        frame2.convert()
        AnimatedSprite.__init__(self,[frame1,frame2])
        self.image=frame1
        self.rect=Rect(TILESIZE*x,TILESIZE*y,TILESIZE,TILESIZE)
        self._xdir=0
        self._ydir=0
        self._homex=x
        self._homey=y



```
GRAPHICS is a global that contains a single gif with all of the graphics on one image.
the author uses subsuface to load each frame for the sprite.

---

### Post by Tony Flury on 2010-03-25
I think you are wrong - the image attribute used by the code is inherited from the sprite classs - it must be - I have seen code that just uses the base sprite class and nothing else which sets the "image" attribute - and code examples definitely display the image as expected.

In the code snippet on that web page there is no manipulation of the Suface of the sprite object (no mention of surface at all), so in theory (if image is an entirely constructed attribute of the extended class), then this sprite would not display anything as at no point is the image applied to the screen or anything else - as it would be simply stored in an attribute which is local only to the Animated sprite class 

Perversley though - even though I think your analysis is wrong, you have given me enough to start with, as your posted code below does allow me to create a slice of a single image file - so thank you.

---

### Post by lavinog on 2010-03-25
> **Tony Flury said:**
> I think you are wrong - the image attribute used by the code is inherited from the sprite classs - it must be - I have seen code that just uses the base sprite class and nothing else which sets the "image" attribute - and code examples definitely display the image as expected.

In the code snippet on that web page there is no manipulation of the Suface of the sprite object (no mention of surface at all), so in theory (if image is an entirely constructed attribute of the extended class), then this sprite would not display anything as at no point is the image applied to the screen or anything else - as it would be simply stored in an attribute which is local only to the Animated sprite class 

Perversley though - even though I think your analysis is wrong, you have given me enough to start with, as your posted code below does allow me to create a slice of a single image file - so thank you.

from the docs:
> 
Group.draw

      blit the Sprite images
      Group.draw(Surface): return None

      Draws the contained Sprites to the Surface argument. This uses the Sprite.image attribute for the source surface, and Sprite.rect for the position. 

so use it uses .image to get the image...but that doesn't exist in the base sprite...that is why it must be assigned.

The example code was probably not the best to use due to its complexity.
What it does is assigns each sprite to a renderupdates() variable like ACTORS, then calls pygame.display.update(ACTORS.draw(screen)) to blit the whole group to the screen.

If you have a different example. I might have an easier time explaining it.

I am sure pygame could be better documented, but I don't think they are leaving many details out.

---

### Post by Tony Flury on 2010-03-25
I will have a go at writing some code - i think that is best.

---

