---
title: "opengl rotate-translate-rotate problem"
date: 2008-05-01
forum: Programming Talk
---

### Post by paukku92 on 2008-05-01
Im drawing a box and i would like to do the following:

1. rotate the box around its own axis (the angle of the object)
2. move it to position according to the position values and camera position
3. rotate again for the camera angle

I have managed to make following piece of code, but when the model angle changes it rotates around the viewer, not its own axis. 

```

glPushMatrix();
glLoadIdentity();

glRotatef(model.Angle.X,1.0f,0.0f,0.0f); 
glRotatef(model.Angle.Y,0.0f,1.0f,0.0f); 
glRotatef(model.Angle.Z,0.0f,0.0f,1.0f);
glTranslatef(-Position.X+model.Position.X,-Position.Y+model.Position.Y,-Position.Z+model.Position.Z);
glRotatef(Angle.X,1.0f,0.0f,0.0f); 
glRotatef(Angle.Y,0.0f,1.0f,0.0f); 
glRotatef(Angle.Z,0.0f,0.0f,1.0f); 

glBegin(GL_QUADS);
glVertex3f(i->Vertexes[0].X,i->Vertexes[0].Y,i->Vertexes[0].Z);
glVertex3f(i->Vertexes[1].X,i->Vertexes[1].Y,i->Vertexes[1].Z);
glVertex3f(i->Vertexes[2].X,i->Vertexes[2].Y,i->Vertexes[2].Z);
glVertex3f(i->Vertexes[3].X,i->Vertexes[3].Y,i->Vertexes[3].Z);
glEnd();
			
glPopMatrix();
```

---

### Post by Wybiral on 2008-05-01
Do the "camera" first, then the object.

---

### Post by paukku92 on 2008-05-01
Thank you for the tip. It seems to work now.

---

