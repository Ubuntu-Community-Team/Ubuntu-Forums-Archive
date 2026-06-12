---
title: "[Python] Pygame help, what are blend modes?"
date: 2008-10-03
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-10-03
So what are blending modes in pygame? I think they have something to do with alpha values.

I want to draw an image like this (found with google):
[IMG]http://images.gamedev.net/features/programming/2dsoftshadow/02BasicPP.gif[/IMG]


And I already have a grayscale surface, which looks like this:
[[IMG]http://img53.imageshack.us/img53/5223/testjb2.th.png[/IMG]](http://img53.imageshack.us/my.php?image=testjb2.png)[[IMG]http://img53.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

But how can I draw only the black parts of that grayscale surface with pygame blending modes,
so the white part of the image would be transparent??

---

### Post by jamescox84 on 2008-10-03
A simple solution to this would be to create a PNG image with a faded transparent circle in it, and load that. You could then render the background and blit the PNG on top of that.

Just an idea. But it might not be what you need.

Perhaps look at these:
[http://www.pygame.org/docs/ref/surface.html#Surface.blit](http://www.pygame.org/docs/ref/surface.html#Surface.blit)
[http://www.libsdl.org/cgi/docwiki.cgi/SDL_SetAlpha](http://www.libsdl.org/cgi/docwiki.cgi/SDL_SetAlpha)

---

### Post by crazyfuturamanoob on 2008-10-04
But I got an image of that white ball (with alpha values) then I got a black surface,
and I blit the white circle on the black surface.
But how to draw only the black parts of the surface? And all grayshades would have different opacity according it's brightness.

---

### Post by jamescox84 on 2008-10-04
I just tried to implement what you described. I used Surface.blit(source, dest, area=None, special_flags=0) with special_flags set to BLEND_SUB. This option unfortunately was not included in the version of pygame bundled with Ubuntu 8.04. So I downloaded and compiled pygame my self. Any way the code bellow seems to do what you need.

```
import pygame


pygame.init()

screen = pygame.display.set_mode((640, 480))

blob = pygame.image.load('blob.png')
poly = pygame.image.load('poly.png')

running = True
while running:
	for e in pygame.event.get():
		if e.type == pygame.QUIT:
			running = False
	
	screen.fill(0)
	
	screen.blit(blob, (170, 90))
	screen.blit(poly, (170, 90), None, pygame.BLEND_SUB)
	
	pygame.display.flip()
	
pygame.quit()
```

Just a point of interest I tried this code with two different images for the poly image. One with an alpha channel, and one with a black background. The alpha channel image seemed to be converted to a 1-bit alpha image that was then flattened on top of a black background before blitted to the screen! Maybe this will be fixed in a future release!

Hope this helped

---

