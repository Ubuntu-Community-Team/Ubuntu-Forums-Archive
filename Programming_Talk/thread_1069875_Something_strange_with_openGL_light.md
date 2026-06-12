---
title: "Something strange with openGL light"
date: 2009-02-14
forum: Programming Talk
---

### Post by tneva82 on 2009-02-14
It's working bit of strangely. Basicly if I stand away from wall I see the wall. I go CLOSER to wall and it darkens? What gives? It's not like camera position contains object that would be blocking the light? Any idea am I doing it wrongly or is it something with normals? Maybe they are incorrect or something?

```

GLfloat LightAmbient[]  = { 0.8f, 0.8f, 0.8f, 1.0f };
GLfloat LightDiffuse[]  = { 1.0f, 1.0f, 1.0f, 1.0f };
GLfloat LightPosition[] = { -20.0f, -2.0f, -10.0f, 1.0f };

glLightfv( GL_LIGHT1, GL_AMBIENT, LightAmbient );
glLightfv( GL_LIGHT1, GL_DIFFUSE, LightDiffuse );
glLightfv( GL_LIGHT1, GL_POSITION, LightPosition );
glEnable( GL_LIGHT1 );
glEnable( GL_LIGHTING );

```

That's the code I use to set up lightning. 

So anybody who understands theory of lightning could give me estimates where I am going wrong? I figure it might be normals but changing order of vertexes in polygon(in case they weren't counter-clock afterall) seems to only make it worse so I think I have it now. But why parts of model are darkish especially if I look directly at them? Or go closer?

---

