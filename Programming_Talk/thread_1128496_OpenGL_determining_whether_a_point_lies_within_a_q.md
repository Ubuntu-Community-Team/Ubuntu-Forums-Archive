---
title: "OpenGL: determining whether a point lies within a quad"
date: 2009-04-17
forum: Programming Talk
---

### Post by Bulletbeast on 2009-04-17
I know this is more of a mathemathical question than a programming one, yet what's the easiest way to determine whether a point in 3D space lies within a quad?

EDIT: Let's be more detailed. I have a bunch of random quads spread in 3D space, and I want them to react to mouse clicks in order to select them. I have found some code that uses gluUnProject to convert window coordinates to 3D coordinates, but analytic geometry fails me, and so does Google.

---

### Post by c174 on 2009-04-17
I'm not sure I get what you mean by "a point in 3D in a quad"? I Suppose you want to check if a point is inside a 2D polygon (with four edges)? If that is the case you can use the following.

Any line in 2D can be described by an equation like: Ax + By = C. Here ( A, B ) is also a vector perpendicular to the line. Now define a function

f = Ax + By - C

If you insert a point ( x0, y0 ) the result will be either a positive or a negative number depending on which half-space the point is in, with respect to the line (i.e. to the "left" or the the "right" of the line).

So if you perform four tests (one for each line segment) and the sign is the same for all, you know that the point is either inside or outside the polygon -- depending on your sign convention; Note that the normal vectors [ the ( A, B )'s ] must be defined consistently, for example all pointing outward.

Also this procedure might fail if the polygon is not convex.

This is one way to go - there are probably other ways to do it also..

---

### Post by hessiess on 2009-04-17
Assuming you are using perspective, you need to find a way to create a new mesh with the perspective applied, then treet this as a 2D mesh and do a point-in-polygon test on each quad.

---

### Post by DougB1958 on 2009-04-17
> **Bulletbeast said:**
> ... I have a bunch of random quads spread in 3D space, and I want them to react to mouse clicks in order to select them. I have found some code that uses gluUnProject to convert window coordinates to 3D coordinates, but analytic geometry fails me, and so does Google.

Figuring out which object in your world is under a mouse click sounds like exactly what OpenGL "picking" is for. I haven't used it myself, but I remember a fairly good discussion in the OpenGL Programming Guide (Red Book), and I just found a tutorial at [http://www.lighthouse3d.com/opengl/picking/](http://www.lighthouse3d.com/opengl/picking/). You might see if either of these solves your problem...

---

### Post by tneva82 on 2009-04-18
> **DougB1958 said:**
> Figuring out which object in your world is under a mouse click sounds like exactly what OpenGL "picking" is for. I haven't used it myself, but I remember a fairly good discussion in the OpenGL Programming Guide (Red Book), and I just found a tutorial at [http://www.lighthouse3d.com/opengl/picking/](http://www.lighthouse3d.com/opengl/picking/). You might see if either of these solves your problem...

Out of curiosity I read somewhere(can't remember where alas) that picking should be avoided and instead draw all objects with unique colour and use that to determine which object was clicked.

Any truth to that and if so why? Picking sounded more useful for me as I could use objects own ID to name it. With different colours I would need either add colour data to objects(or use colour instead of ID) or figure way to link ID to colours.

Dunno. Haven't got around for picking yet.

---

### Post by Bulletbeast on 2009-04-18
On the topic of picking, I can't seem to get any hits with it. Here's my code (based on [this](http://opengl.czweb.org/ch19/591-593.html) and the pages that follow):

```

int DrawSelectionScene(GLvoid)
{ 
  glTranslatef(0.0f,0.0f,zoom-26.0f);

  glRotatef(tilt,0.1f,0.0f,0.0f);
  glRotatef(spin,0.0f,0.0f,0.1f);
  
  glTranslatef(-galaxies[selected_galaxy].x*travelled,-galaxies[selected_galaxy].y*travelled,-galaxies[selected_galaxy].z*travelled);
  
  glColor4f(0.5f,0.5f,0.5f,0.5f);
  
  glInitNames();
  glPushName(0);
  
  // A circle to represent the Supergalactic Plane
  
  glLoadName(PLANE);
  glBegin(GL_TRIANGLE_FAN);
    glVertex2f(0,0);
    for(int i=0;i<52;i++){
       double angle = i*2*M_PI/52;
       glVertex2f(cos(angle)*(PLANE_START_SIZE+PLANE_INC_SIZE*(PLANE_NUM_CIRCLES-1)),sin(angle)*(PLANE_START_SIZE+PLANE_INC_SIZE*(PLANE_NUM_CIRCLES-1)));
    }
    glVertex2f(cos(0)*(PLANE_START_SIZE+PLANE_INC_SIZE*(PLANE_NUM_CIRCLES-1)),sin(0)*(PLANE_START_SIZE+PLANE_INC_SIZE*(PLANE_NUM_CIRCLES-1)));
  glEnd();
  
  // And quads for the galaxies
  
  for (int i=0; i<num_galaxies; i++)
	{
    glLoadName(i);
    
    glTranslatef(galaxies[i].x,galaxies[i].y,galaxies[i].z);

    glRotatef(-spin,0.0f,0.0f,0.1f);
    glRotatef(-tilt,1.0f,0.0f,0.0f);

	  glBegin(GL_QUADS);
    glTexCoord2f(0.0f,0.0f); glVertex3f(-0.8f, 0.8f, 0.0f);
    glTexCoord2f(0.0f,1.0f); glVertex3f( 0.8f, 0.8f, 0.0f);
	    glTexCoord2f(1.0f,1.0f); glVertex3f( 0.8f,-0.8f, 0.0f);
		  glTexCoord2f(1.0f,0.0f); glVertex3f(-0.8f,-0.8f, 0.0f);
    glEnd();

	  glRotatef(tilt,1.0f,0.0f,0.0f);
	  glRotatef(spin,0.0f,0.0f,0.1f);

	  glTranslatef(-galaxies[i].x,-galaxies[i].y,-galaxies[i].z);
  }  
  return TRUE;
}

void ProcessSelection(int X, int Y)
{ 
  GLuint select[SELECT_BUFFER_LENGTH];
  GLint hits, viewport[4];

  glSelectBuffer(SELECT_BUFFER_LENGTH, select);
  glGetIntegerv(GL_VIEWPORT, viewport);

  glMatrixMode(GL_PROJECTION);
  glPushMatrix();
  glLoadIdentity();
  glRenderMode(GL_SELECT);
  
  gluPickMatrix(X, Y, 2, 2, viewport);
  gluPerspective(45.0f,(GLfloat)window_width/(GLfloat)window_height,0.1f,100.0f);

  DrawSelectionScene();

  hits = glRenderMode(GL_RENDER);

  glMatrixMode(GL_PROJECTION);
  glPopMatrix();
  glMatrixMode(GL_MODELVIEW);

  return;
}

```

Wherever I click, the variable *hits* always turns out to be -1. What have I copypasted wrong?

---

### Post by Bulletbeast on 2009-04-19
Bump?

---

### Post by DougB1958 on 2009-04-19
> **tneva82 said:**
> Out of curiosity I read somewhere(can't remember where alas) that picking should be avoided and instead draw all objects with unique colour and use that to determine which object was clicked.

Any truth to that and if so why? Picking sounded more useful for me as I could use objects own ID to name it. With different colours I would need either add colour data to objects(or use colour instead of ID) or figure way to link ID to colours.

Dunno. Haven't got around for picking yet.

I seem to remember reading something like this somewhere too, but also don't remember where, or even if it said "avoid picking and use color instead" or just "using color is an alternative to picking." I suppose I could see color being a bit simpler than picking: draw your scene into an off-screen buffer, using exactly the code you always use, except that each object has a unique color. Then get the window coordinates of your mouse click, read back the color at that point in the off-screen buffer, and presto, you've got your obect ID. Also notice that since no-one ever sees these colors, you can encode object IDs in color bits -- for example, object 0 can have a red (or whatever your favorite color channel is) value of 0, object 1 a red value of 1, and so forth; if you have lots of objects, use one channel for the low-order bits of the ID and other channels for higher-order bits, etc.

But all of the above comes from someone who has never actually dealt with this problem in real code, it's all just my vague memories of things I think I've read somewhere. Maybe there's an expert following this who cares to improve on my thoughts...?

---

### Post by Tuna-Fish on 2009-04-19
> **tneva82 said:**
> Out of curiosity I read somewhere(can't remember where alas) that picking should be avoided and instead draw all objects with unique colour and use that to determine which object was clicked.

Any truth to that and if so why? Picking sounded more useful for me as I could use objects own ID to name it. With different colours I would need either add colour data to objects(or use colour instead of ID) or figure way to link ID to colours.

Dunno. Haven't got around for picking yet.

The color solution is probably significantly less computationally intensive. If you are developing for an iphone or something, it might make sense. Other than that, just use the simple way.

---

### Post by Bulletbeast on 2009-04-20
On the contrary, I believe picking would be more optimized, or at least as fast as colours, with the upside of being able to retrieve all object sunder the cursor and not only the topmost.

By the way, it turned out that there's nothing wrong with the above code, my problem was elsewhere.

---

### Post by mirna on 2009-05-29
Hi,

You are missing a call to

glMatrixMode(GL_MODELVIEW);

before you redraw the objects in the GL_SELECT mode. Take a look here:

[http://gpwiki.org/index.php/OpenGL:Tutorials:Picking]("http://gpwiki.org/index.php/OpenGL:Tutorials:Picking")

You can also take a look at lighthouse3D website.

What I don't understand is the coordinates returned by gluUnProject. They make no sense. Where could I find that code that uses gluUnProject?

mirna


> **Bulletbeast said:**
> On the topic of picking, I can't seem to get any hits with it. Here's my code (based on [this](http://opengl.czweb.org/ch19/591-593.html) and the pages that follow):

```

int DrawSelectionScene(GLvoid)
{ 
  glTranslatef(0.0f,0.0f,zoom-26.0f);

  glRotatef(tilt,0.1f,0.0f,0.0f);
  glRotatef(spin,0.0f,0.0f,0.1f);
  
  glTranslatef(-galaxies[selected_galaxy].x*travelled,-galaxies[selected_galaxy].y*travelled,-galaxies[selected_galaxy].z*travelled);
  
  glColor4f(0.5f,0.5f,0.5f,0.5f);
  
  glInitNames();
  glPushName(0);
  
  // A circle to represent the Supergalactic Plane
  
  glLoadName(PLANE);
  glBegin(GL_TRIANGLE_FAN);
    glVertex2f(0,0);
    for(int i=0;i<52;i++){
       double angle = i*2*M_PI/52;
       glVertex2f(cos(angle)*(PLANE_START_SIZE+PLANE_INC_SIZE*(PLANE_NUM_CIRCLES-1)),sin(angle)*(PLANE_START_SIZE+PLANE_INC_SIZE*(PLANE_NUM_CIRCLES-1)));
    }
    glVertex2f(cos(0)*(PLANE_START_SIZE+PLANE_INC_SIZE*(PLANE_NUM_CIRCLES-1)),sin(0)*(PLANE_START_SIZE+PLANE_INC_SIZE*(PLANE_NUM_CIRCLES-1)));
  glEnd();
  
  // And quads for the galaxies
  
  for (int i=0; i<num_galaxies; i++)
	{
    glLoadName(i);
    
    glTranslatef(galaxies[i].x,galaxies[i].y,galaxies[i].z);

    glRotatef(-spin,0.0f,0.0f,0.1f);
    glRotatef(-tilt,1.0f,0.0f,0.0f);

	  glBegin(GL_QUADS);
    glTexCoord2f(0.0f,0.0f); glVertex3f(-0.8f, 0.8f, 0.0f);
    glTexCoord2f(0.0f,1.0f); glVertex3f( 0.8f, 0.8f, 0.0f);
	    glTexCoord2f(1.0f,1.0f); glVertex3f( 0.8f,-0.8f, 0.0f);
		  glTexCoord2f(1.0f,0.0f); glVertex3f(-0.8f,-0.8f, 0.0f);
    glEnd();

	  glRotatef(tilt,1.0f,0.0f,0.0f);
	  glRotatef(spin,0.0f,0.0f,0.1f);

	  glTranslatef(-galaxies[i].x,-galaxies[i].y,-galaxies[i].z);
  }  
  return TRUE;
}

void ProcessSelection(int X, int Y)
{ 
  GLuint select[SELECT_BUFFER_LENGTH];
  GLint hits, viewport[4];

  glSelectBuffer(SELECT_BUFFER_LENGTH, select);
  glGetIntegerv(GL_VIEWPORT, viewport);

  glMatrixMode(GL_PROJECTION);
  glPushMatrix();
  glLoadIdentity();
  glRenderMode(GL_SELECT);
  
  gluPickMatrix(X, Y, 2, 2, viewport);
  gluPerspective(45.0f,(GLfloat)window_width/(GLfloat)window_height,0.1f,100.0f);

  DrawSelectionScene();

  hits = glRenderMode(GL_RENDER);

  glMatrixMode(GL_PROJECTION);
  glPopMatrix();
  glMatrixMode(GL_MODELVIEW);

  return;
}

```

Wherever I click, the variable *hits* always turns out to be -1. What have I copypasted wrong?

---

