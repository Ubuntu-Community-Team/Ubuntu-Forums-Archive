---
title: "gluUnProject trouble (python)"
date: 2011-01-14
forum: Programming Talk
---

### Post by oedipuss on 2011-01-14
I'm having some trouble with gluUnProject, used to get world coordinates from window coordinates in an orthographic projection. 

I've set up a simple test gtk glext window, with just the following:
Used to initialize opengl in the gkt.glext widget's expose event:
```

        glDisable( GL_TEXTURE_2D )

        w,h= self.allocation.width, self.allocation.height

        glViewport(0, 0, w, h)
        glMatrixMode( GL_PROJECTION )
        glLoadIdentity()    
        glOrtho( -w/2.0, w/2.0, h/2.0, -h/2.0, -1, 1 )
        glMatrixMode( GL_MODELVIEW )
        glLoadIdentity()
        glTranslatef(20,20,0)
        glRotatef(10,0,0,1)


```

and expose event :
```

        glClearColor(1,1,1,1)
        glClear(GL_COLOR_BUFFER_BIT)
        glColor4f(1,0,0,1)        
        glBegin(GL_QUADS)
        glVertex2f(-100,-100)
        glVertex2f(100,-100)
        glVertex2f(100,100)
        glVertex2f(-100,100)
        glEnd()

```

This shows a red rectangle, slightly rotated, and moved a bit off-center.

Now for gluUnProject, in a button-press event : 
```

        cx,cy = event.x, event.y

        x,y,z = gluUnProject( cx, cy, 0 )

        print cx,cy,":",x,y

```

When I click at the rectangle's corners, the output should be 
whatever, whatever : ~ +- 100, ~ +- 100 
( +- depending on which corner ) but it's very different.. 

If I rotate without translating at all, it seems as if gluUnproject uses the rotation angle in the opposite direction. The +-100,+-100 points it returns form a rectangle rotated the other way. With translation I can't figure out exactly what's going wrong, but it seems only the vertical axis is off.

I hope I'm describing it ok...

There's nothing else gl related in this test case, just the code above. Oh, and another glViewport in the configure event, same as above, but I'm not resizing the window anyway.

Is this not the correct way of using gluUnproject? If so what am I doing wrong ?

---

