---
title: "Pygame help"
date: 2012-06-25
forum: Programming Talk
---

### Post by strsccgms on 2012-06-25
Hi,

Problem.

1. I have a sprite (a) which is a subclass of pygame.sprite.DirtySprite
2. Sprite (a) is a member of pygame.sprite.LayeredDirty group
3. Image is a simple rectangular surface image 

3. I have sprite (b) which is a subclass of pygame.sprite.Sprite
4. Sprite (b) is a member of pygame.sprite.LayeredUpdates group
5  Image is a circle drawn on to a rectangular surface with the colour key set at the (0,0) - produce a circle

Issue:
When Sprite (b) is on the background image is perfect circle
When Sprite (b) is on sprite (a) image shows the rectangular border around the surface. There is a flickering of these borders

How do I show a clean circle when traversing over sprite (a)

Regards

---

### Post by Tony Flury on 2012-06-27
Without looking at your code it is difficult to say - but one cause of flickering could be to do with your screen updates. You might want to look at where/when you updae the screen - and only do it once per main loop, rather than each time you move an object.

---

### Post by wei2912 on 2012-06-27
> **strsccgms said:**
> Hi,

Problem.

1. I have a sprite (a) which is a subclass of pygame.sprite.DirtySprite
2. Sprite (a) is a member of pygame.sprite.LayeredDirty group
3. Image is a simple rectangular surface image 

3. I have sprite (b) which is a subclass of pygame.sprite.Sprite
4. Sprite (b) is a member of pygame.sprite.LayeredUpdates group
5  Image is a circle drawn on to a rectangular surface with the colour key set at the (0,0) - produce a circle

Issue:
When Sprite (b) is on the background image is perfect circle
When Sprite (b) is on sprite (a) image shows the rectangular border around the surface. There is a flickering of these borders

How do I show a clean circle when traversing over sprite (a)

Regards

Have you tried double buffering? Load all images into an image buffer, then paint it. I don't know python well but I do know that is a common problem.

---

