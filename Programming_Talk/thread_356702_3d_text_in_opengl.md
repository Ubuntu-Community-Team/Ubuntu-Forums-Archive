---
title: "3d text in opengl"
date: 2007-02-08
forum: Programming Talk
---

### Post by Phobia on 2007-02-08
Hi, one of my friends at work is trying to find a way to  code 3d text in opengl that is platform independent. He has tried glut be can't get it working in windows. The only example code he can find is for windows. If there is a way then can y'all post some links to the websites.

--Thanks

---

### Post by Wybiral on 2007-02-08
I don't think GLUT has any 3d text features (that I know of...)

Do you mean text, in general, in OpenGL?

The method I usually use is to make a single image with all the characters in it. You can make the characters whatever size you'd like, but arrange them in a 16x16 grid. Then you can adjust the texture mapping to whichever character you need and render it on a quad... 

My function looks like this:

```

void glPrint(GLuint font, int x, int y, const char text[]){
	float tx, ty;
	float unit = 1.0/16;
	glBindTexture(GL_TEXTURE_2D, font);
	glBegin(GL_QUADS);
	for(int i=0; text[i]!='\0'; i++){
		tx = (int)(text[i]%16  )*unit;
		ty = (int)(text[i]*unit)*unit;

		glTexCoord2f(tx     , ty     ); glVertex2i(x+textSize[0]*i            , y            );
		glTexCoord2f(tx+unit, ty     ); glVertex2i(x+textSize[0]*i+textSize[0], y            );
		glTexCoord2f(tx+unit, ty+unit); glVertex2i(x+textSize[0]*i+textSize[0], y+textSize[1]);
		glTexCoord2f(tx     , ty+unit); glVertex2i(x+textSize[0]*i            , y+textSize[1]);
	}
	glEnd();
}

```

textSize[0] is the font width, textSize[1] is the font height. You can make another function to update those, something like "glFontSize(int, int)"

I've attached a charset made by Tom Mulgrew (it's from Basic4GL)

You can replace those characters with your own to make your own font, or look for some already made ones for download somewhere.

If you do actually mean 3d text... Then you might need a model of each character, then you do a similar routine to the print funtion above, but render the models.

You might also look into OpenGL GUI libraries...
[http://libufo.sourceforge.net/index.html](http://libufo.sourceforge.net/index.html)
[http://www.bramstein.nl/gui/](http://www.bramstein.nl/gui/)

---

### Post by jblebrun on 2007-02-08
I googled "Opengl text" and got this helpful looking link:
[http://www.sjbaker.org/steve/omniv/opengl_text.html](http://www.sjbaker.org/steve/omniv/opengl_text.html)

---

### Post by Phobia on 2007-02-08
thanks, i will try and see if this solves my friends problem. I have email him a link to the post.
and thanks again.

---

