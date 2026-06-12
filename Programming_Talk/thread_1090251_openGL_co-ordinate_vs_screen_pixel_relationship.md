---
title: "openGL co-ordinate vs screen pixel relationship"
date: 2009-03-08
forum: Programming Talk
---

### Post by tneva82 on 2009-03-08
Just wondering how I could transform point in the screen in specified in pixels to 2d-co-ordinates in openGL(Z value can be forgotten since this will be dealing with 2d objects only). More specifically how I could move the object according to how mouse moved if I know the distance mouse moved(in pixels).

Is there some sort of a fixed relationship or maybe some sort of method that allows to determine it?

Edit: And as a side note if somebody could give pointer to tutorial on how to print text in openGL which preferably works in both linux and windows or atleast works in linux I would appreciate that. So far only guides I have found have used windows specific function :( Not good enough I'm affraid.

---

### Post by Gordon Bennett on 2009-03-08
First of all, base your mouse coordinate system as values from 0.0 -> 1.0 in X and Y axes.  Take your mouse coordinates from any position on screen and convert to it (eg, x = gui.area.width / current.mouse.xpos ; watch out for divide-by-zero!).  This way you can easily scale independent of the resolution.

As for rendering text - one way is to store the bitmaps for every character in the alphabet at a decent resolution (say, 64x64 pixels) - most games do this.

Another way is to use a text renderer such as [FreeType]("http://www.freetype.org/") which will allow you to display at any size.  You can even use it to store pre-computed sizes for any high-speed situations.

---

### Post by cb951303 on 2009-03-08
from gamedev forums

[php]  
void glEnable2D()
{
   int vPort[4];

   glGetIntegerv(GL_VIEWPORT, vPort);

   glMatrixMode(GL_PROJECTION);
   glPushMatrix();
   glLoadIdentity();

   glOrtho(0, vPort[2], 0, vPort[3], -1, 1);
   glMatrixMode(GL_MODELVIEW);
   glPushMatrix();
   glLoadIdentity();
}

void glDisable2D()
{
   glMatrixMode(GL_PROJECTION);
   glPopMatrix();   
   glMatrixMode(GL_MODELVIEW);
   glPopMatrix();	
}
[/php]

this would give you a 2D viewport. (0, 0) is the bottom left corner.

example:
[php]
  
void RenderScene()
{
  glClear(GL_COLOR_BUFFER_BIT| GL_DEPTH_BUFFER_BIT);
  glLoadIdentity();
  
  glEnable2D();
    glBegin(GL_TRIANGLES);
      glColor3ub(255, 0, 0);
        glVertex2d(0, 0);
      glColor3ub(0, 255, 0);
        glVertex2d(100,0);
      glColor3ub(0, 0, 255);
        glVertex2D(50, 50);
    glEnd();
  glDisable2D();
}
[/php]

---

### Post by tneva82 on 2009-03-08
Working with the 2d-drawing I ran into annoying problem. Specifically somehow my texture goes all haywire. Doesn't seem to be code error though since BMP file from NeHe goes fine but maybe I'm incorrect.

Anyway here's screenshot of what happens:

[IMG]http://tneva.net/pics/error.jpg[/IMG]

And the code what does this(in order they are called). Again worth a note that with another texture it works fine but same size texture doesn't when I tried to put(what should come is uniformly green with little bit of text at the very top-left corner).

Oh and I have tried the texture with all 16BPP formats GIMP has. No difference. Also for heck tried 24bit colour though program is set with 16BPP.

```

void start2d() {
  glDisable(GL_DEPTH_TEST);
  int vPort[4];
  
  glGetIntegerv(GL_VIEWPORT, vPort);

  glMatrixMode(GL_PROJECTION);
  glPushMatrix();
  glLoadIdentity();

  glOrtho(0, vPort[2], 0, vPort[3], -1, 1);
  glMatrixMode(GL_MODELVIEW);
  glPushMatrix();
  glLoadIdentity();
}

void GUIObject::draw() {

  glBindTexture( GL_TEXTURE_2D, texture );
  glBegin(GL_POLYGON);
  glTexCoord2f(0.0f, 0.0f);
  glVertex2f(x, y-heigth);
  glTexCoord2f(1.0f, 0.0f);
  glVertex2f(x+width, y-heigth);

  glTexCoord2f(1.0f, 1.0f);
  glVertex2f(x+width, y);

  glTexCoord2f(0.0f, 1.0f);
  glVertex2f(x, y);
    
  glEnd();

}

void disable2d() {
  glMatrixMode(GL_PROJECTION);
  glPopMatrix();   
  glMatrixMode(GL_MODELVIEW);
  glPopMatrix();
  glEnable(GL_DEPTH_TEST);
}
```

Anyway problem with image options(though colour properties seems to be same as is size) or with the code?

---

### Post by cb951303 on 2009-03-08
I think image dimensions should be power of 2.

---

### Post by tneva82 on 2009-03-09
> **cb951303 said:**
> I think image dimensions should be power of 2.

256x256 is power of 2 yes? (unless my math is TOTALLY rusty :D). As said it's of exact same dimensions as texture from NeHe site which works fine.

(though from other thread seeems that limitation has been removed but haven't had reason to try that on my own code).

---

### Post by cb951303 on 2009-03-09
didn't check your code last time.
can you try this.
```

void GUIObject::draw() {

  glBindTexture( GL_TEXTURE_2D, texture );
  **glEnable(GL_TEXTURE_2D);**
  glBegin(GL_POLYGON);
  glTexCoord2f(0.0f, 0.0f);
  glVertex2f(x, y-heigth);
  glTexCoord2f(1.0f, 0.0f);
  glVertex2f(x+width, y-heigth);

  glTexCoord2f(1.0f, 1.0f);
  glVertex2f(x+width, y);

  glTexCoord2f(0.0f, 1.0f);
  glVertex2f(x, y);
    
  glEnd();
  **glDisable(GL_TEXTURE_2D);**

}

```

also why width, height, x, y and texture are out of function draw's scope. shouldn't they be local? (not that it would have an impact on drawing but, if you're using them globally, that's not a good idea and not necessary)

---

### Post by tneva82 on 2009-03-09
> **cb951303 said:**
> didn't check your code last time.
can you try this.

No effect :-/ Starting to feel it's problem with image but what? Same size, 16BPP just like how I set the window...Odd. Very odd. If the other image didn't work I would imagine it to be code error but the NeHe .BMP worked just fine(except they were upside down which I solved by altering texture co-ordinates a bit).

> also why width, height, x, y and texture are out of function draw's scope. shouldn't they be local? (not that it would have an impact on drawing but, if you're using them globally, that's not a good idea and not necessary)

The draw function is member of GUIObject class(which is parent class for every GUI related class I have like GUIWindow I'm now trying to get working) and the variables you mention are members of the same class. Since those aren't changing constantly seemed like best place to store them :D

Need to store them somewhere and rather than having them in main programs side and passed as parameters logical step would IMO be hiding them inside the class.

---

### Post by cb951303 on 2009-03-09
> **tneva82 said:**
> No effect :-/ Starting to feel it's problem with image but what? Same size, 16BPP just like how I set the window...Odd. Very odd. If the other image didn't work I would imagine it to be code error but the NeHe .BMP worked just fine(except they were upside down which I solved by altering texture co-ordinates a bit).


I really don't remember how opengl handles coordinates but here is a code that I tried few days ago and know it works. if  this doesn't work too I'm guessing there is something wrong with the way you setup opengl?
```

void DrawTexture(int x, int y, GLuint textureid, int textw, int texth)
{
    glBindTexture(GL_TEXTURE_2D, textureid);
    glEnable(GL_TEXTURE_2D);

    glBegin(GL_QUADS);
        glTexCoord2i(0, 0);
        glVertex3f(x, y, 0);

        glTexCoord2i(1, 0);
        glVertex3f(x+textw, y, 0);

        glTexCoord2i(1, 1);
        glVertex3f(x+textw, y+texth, 0);

        glTexCoord2i(0, 1);
        glVertex3f(x, y+texth, 0);
    glEnd();

    glDisable(GL_TEXTURE_2D);
}

```

> 
The draw function is member of GUIObject class(which is parent class for every GUI related class I have like GUIWindow I'm now trying to get working) and the variables you mention are members of the same class. Since those aren't changing constantly seemed like best place to store them :D

Need to store them somewhere and rather than having them in main programs side and passed as parameters logical step would IMO be hiding them inside the class.

ah sorry about that, I get blind in the mornings didn't see it was a class member :)

---

### Post by tneva82 on 2009-03-09
> **cb951303 said:**
> ah sorry about that, I get blind in the mornings didn't see it was a class member :)

No probs :D My fault for not making it specific.

Anyway problem solved. Wasn't fault in code. Problem seems to be how GIMP made the BMP. GIMP loaded it right, nothing else did. Made replacement quickly with windows paint(have to find replacement for that!) and works like a charm.

Also got "window" to move around by drag&drop(though seems somewhat sluggish at some times in starting the drag). Have to test wether it works with nested windows(ie window inside a window) and how it tackles when I have multiple non-nested windows but simple GUI is forming up.

Edit: Second window comes nicely and I can move it nicely as well but for some reason or other nested window DOESN'T draw up. Indeed this code:

```

  for(list<GUIObject*>::iterator it=objects.begin();it!=objects.end();it++) {
    printf("hep");
    (*it)->draw(x, y);
  }

```

Never goes through(no "hep" printed and certainly no box drawn). Humhum. I have push_backed new GUIObject* inside there so that shouldn't be issue. Hum hum.

Edit2: That one was easy. The bloody thing calls parent class function rather than overridden one in the inherited class. Okay. Now to figure out how this works. Last time I tried something like this it was with Java :D

---

