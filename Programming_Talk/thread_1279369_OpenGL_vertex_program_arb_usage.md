---
title: "OpenGL vertex_program_arb usage?"
date: 2009-09-30
forum: Programming Talk
---

### Post by MadMan2k on 2009-09-30
basically I am trying to write a OpenGL3 compatible renderer, but since the OSS radeon drivers just support OpenGL1.5 I have to use vp/fp instead of GLSL.

I already managed to write a simple shader and to load it. Now I want to push some external data into it like the Model-View-Matrix, which is the following in OpenGL3:

int loc = glGetUniformLocation(programObject, "name");
glUniformMatrix4fv(loc, 1, GL_FALSE, identity);

I also would like to know whether there is a function closer to glVertexAttribPointer than glVertexPointer?

Generally I am looking for a tutorial which explains a vp/fp based render and also has some documentation for the assembly language.

---

