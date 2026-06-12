---
title: "Using FTGLPixmapFont breaks other GL textures?"
date: 2008-08-03
forum: Programming Talk
---

### Post by Senesence on 2008-08-03
I'm using FTGL in my small OpenGL application to render some text on screen.

In addition to that text, I am also rendering a simple quad.

It all worked great (or so I thought) until I decided to texture the quad (using glTexCoord2i). For some reason, rendering the FTGLPixelFont seems to prevent the quad from being textured. So instead of some text and a textured quad, I get the text and a plain color quad.

I am fairly certain that this is caused by something FTLGPixelFont does, because if I don't render the FTGL text, the quad is textured just fine.

How can I render the FTGLPixmapFont, and still see the texture on the quad?

---

### Post by Wybiral on 2008-08-03
Can you post the code?

It's possible that the font library is flipping some texture-specific bit that opengl needs, but I would need to see the code to help.

---

### Post by Senesence on 2008-08-03
> **Wybiral said:**
> Can you post the code?

Draw code for my quad:
[PHP]
glEnable(GL_TEXTURE_2D);
glPushMatrix();
	
	glBindTexture(GL_TEXTURE_2D, texture); // Texture
	glTranslatef(posx, posy, 0); // Position
	glRotatef(rotation, 0, 0, 1); // Rotate
	
	float xcoord = width * 0.5;
	float ycoord = height * 0.5;
		
	glBegin(GL_QUADS);
		glTexCoord2i(0, 0); glVertex2f(-xcoord, ycoord);
		glTexCoord2i(1, 0); glVertex2f( xcoord, ycoord);
		glTexCoord2i(1, 1); glVertex2f( xcoord,-ycoord);
		glTexCoord2i(0, 1); glVertex2f(-xcoord,-ycoord);
	glEnd();
		
glPopMatrix();
[/PHP]

As for the text; The whole point of using a "font library" is to abstract rendering details, so I don't have any relevant draw code here, instead I just do:

[PHP]
glColor3f(0,0,0); // Black text
glRasterPos2f(0,0); // Center of the screen
font.Render("Blah"); // Draw it
[/PHP]

> It's possible that the font library is flipping some texture-specific bit that opengl needs, but I would need to see the code to help.

Yea, I thought the same, but being somewhat new to OpenGL, I don't exactly know what "bits" OpenGL needs and when it needs them. Right now I am only aware of GL_TEXTURE_2D as being necessary, so I enable that on each draw with glEnable(GL_TEXTURE_2D); just in case if font.Render() disables it for some reason.

PS:
Is there a way to save those specific bits before font.Render() does whatever it actually does, and then return them to that state when done? You know, something like glPush/PopMatrix() but for those needed bits?

---

### Post by Wybiral on 2008-08-03
Yes, around the call to the font rendering, try this:

```

glPushAttrib(GL_TEXTURE_BIT)

...

glPopAttrib()

```

See if that solves it... But I don't know what the font library is doing, so I can't help much there.

BTW: [http://www.opengl.org/documentation/specs/man_pages/hardcopy/GL/html/gl/pushattrib.html](http://www.opengl.org/documentation/specs/man_pages/hardcopy/GL/html/gl/pushattrib.html)

---

### Post by Senesence on 2008-08-03
I tried it; didn't work.

I actually found the FTGLPixmapFont.cpp through google. You can browse it here:
[http://www.debian-doc.org/packages/f/ftgl-dev/html/FTGLPixmapFont_8cpp-source.html](http://www.debian-doc.org/packages/f/ftgl-dev/html/FTGLPixmapFont_8cpp-source.html)

It looks like FTGLPixmapFont is doing the attribute pushing on it's own, and as suspected it does disable GL_TEXTURE_2D.

Although, I don't think that's causing the problem since I always enable it before drawing the quad. 

Right?

---

### Post by Wybiral on 2008-08-03
It doesn't look like it should be messing anything up... Have you tried running your code with the font render calls disabled/commented out?

---

### Post by Senesence on 2008-08-03
> **Wybiral said:**
> It doesn't look like it should be messing anything up... Have you tried running your code with the font render calls disabled/commented out?

Yes.

As I said in my first post: if I don't render the FTGL text, the quad is textured just fine.

---

### Post by Senesence on 2008-08-07
*Bump

Anyone?

---

### Post by Wybiral on 2008-08-07
I'm confused as to why I keep seeing it as ftgl and gltt (even on the same pages online) but your best bet would be the mailing list (as usual): [http://gltt.sourceforge.net/lists.html](http://gltt.sourceforge.net/lists.html)

---

### Post by Senesence on 2008-08-07
Ok, Wybiral.

Thanks for sticking with me this far.

---

