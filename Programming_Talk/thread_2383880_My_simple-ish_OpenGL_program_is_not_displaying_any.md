---
title: "My simple-ish OpenGL program is not displaying anything other than a gray background."
date: 2018-01-30
forum: Programming Talk
---

### Post by s3a on 2018-01-30
I am very new to OpenGL, and I am trying to modify the following file(s) to learn, but I can't even get it/them running properly, in the first place!

My simple-ish OpenGL program is not displaying anything other than a gray background, and there are no errors displayed either! What's wrong?

Here are the files:

TheMainFile.cpp:
[http://dpaste.com/19GJ4ZN](http://dpaste.com/19GJ4ZN)

f.glsl (fragment shader):
[http://dpaste.com/27JCV5F](http://dpaste.com/27JCV5F)

v.glsl (Vertex Shader):
[http://dpaste.com/0657KA2](http://dpaste.com/0657KA2)

What must I do to make the code display the triangles it's supposed to display? Any help in getting me to have them displayed would be greatly appreciated!

---

### Post by norobro on 2018-02-04
[SIZE=2]You need to l[/SIZE]oad, compile and link your shaders: [https://www.khronos.org/registry/OpenGL-Refpages/gl4/html/glUseProgram.xhtml](https://www.khronos.org/registry/OpenGL-Refpages/gl4/html/glUseProgram.xhtml)
```
GLuint loadShaders(std::string vertex_shader_path, std::string fragment_shader_path) {    
    // Create the shaders
}
```

---

