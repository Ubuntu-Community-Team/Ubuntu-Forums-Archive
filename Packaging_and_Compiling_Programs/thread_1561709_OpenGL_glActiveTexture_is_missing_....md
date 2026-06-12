---
title: "OpenGL glActiveTexture is missing ..."
date: 2010-08-26
forum: Packaging and Compiling Programs
---

### Post by abominable on 2010-08-26
Hello everyone.

I am trying an OpenGL application. And far to now I had no problem. But today, while trying multitexturing, in the compilation procedure, I faced the following error ::

```
error: %glActivceTexture% was not declared in this [CODE]
```scope.[/CODE]

I have included the GL/gl.h, and have found the following declaration in the GL/gl.h file :: ```
 GLAPI void GLAPIENTRY glActiveTexture( GLenum texture );
GLAPI void GLAPIENTRY glActiveTextureARB(GLenum texture); 
```

But I don't know how to solve it. I found a site proposing to reinstall the mesa-common-dev package, but didn't solve the problem.

If you have any idea, would be really helpfull !!

---

### Post by SevenMachines on 2010-08-27
if thats actually the error then havent you just spelt the function name wrong?
glActivceTexture isnt glActiveTexture

---

### Post by abominable on 2010-08-27
Sory about that. I couldn't copy paste the error from my ssh-konsole, and wrote it myself. The spelling mistake was made here, not in my code.

---

### Post by SevenMachines on 2010-08-27
i do that all the time :)
can you post the code? makefile, that sort of thing. easier to see if it can be tested

---

### Post by abominable on 2010-08-27
Well I could post a part of my code ::
```
void renderTheTexture(GLubyte* texture, GLuint textureID, int textureSize)
{
  glBindTexture(GL_TEXTURE_2D, textureID);

  glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR);
  glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR);
  glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_REPEAT);
  glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_REPEAT);
  
  glTexImage2D(GL_TEXTURE_2D, 0, GL_RGBA, textureSize, textureSize, 0, GL_RGBA, GL_UNSIGNED_BYTE, texture);
  glActiveTexture(GL_TEXTURE0);
  glPushMatrix();
    glColor3f(1.0f, 1.0f, 1.0f);
    glInterleavedArrays(GL_T2F_V3F, 0, cloudVertices);	      		// Set our Array of elements to be drawn.
    glDrawElements(GL_QUADS, 4, GL_UNSIGNED_INT, texIndices);	// Draws it.
  glPopMatrix();
}
```

The thing is that I use kDevelop. And I don't know how, when typing something, it presents various choices I can type (variable names, function names, etc). When typing "glAc", doesn't bring on the "glActiveTexture". And when compiling says that can't find it.

---

### Post by abominable on 2010-08-27
For the makefile I don't use my own, because of CUDA programming. So I just set my files in a previous CUDA-OpenGL project and compile it.

---

### Post by SevenMachines on 2010-08-27
hmm, works fine here, dont know about kdevelop and its project settings and things that could cause a problem. if you've
* got mesa-common-dev installed
* got #include <GL/gl.h>
then glActiveTexture and the other gl stuff should compile fine.

have you tried opening a new project in kdevelop and testing a simple example in that, maybe some project settings have gone wrong, would seem strange but....

---

### Post by abominable on 2010-08-27
Dude thanx for your help. I found it !!

CUDA makefile doesn't read the /usr/include/GL/<files>. CUDA comes with its own inc/GL/<files>. I checked it on a CUDA project and found out that I had to use GL/glew.h instead of GL/gl.h for compiling my project.

---

### Post by SevenMachines on 2010-08-27
ah, its all flooding back now! I remember something confusing like that when trying to use the cuda headers that come with the proprietary nvidia driver, with much head bashing on keyboard at the time :)

---

