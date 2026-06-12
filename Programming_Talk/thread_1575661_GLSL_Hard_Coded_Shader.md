---
title: "GLSL Hard Coded Shader"
date: 2010-09-16
forum: Programming Talk
---

### Post by ChurroLoco on 2010-09-16
I'm trying to load a GLSL shader with the source code hard coded into the .cpp file.  I normally read it from a file and store in a buffer, but the challenge is a one source file program.  So I store my shader like this as a global.

```
const char* g_VERT_SHADER_SOURCE = "void main()\r\n{\r\n\tgl_Position = gl_ModelViewProjectionMatrix * gl_Vertex * 3.0;\r\n}\0";
```

My question though is how big is this buffer.  When I send this text to OpenGL for shader compilation I need to tell it how big the source is.  Does '\r' and '\n' count as one or two char.  I know at some point they turn into a single char code, but when?

Thanks!

---

### Post by Quikee on 2010-09-16
> **ChurroLoco said:**
> I'm trying to load a GLSL shader with the source code hard coded into the .cpp file.  I normally read it from a file and store in a buffer, but the challenge is a one source file program.  So I store my shader like this as a global.

```
const char* g_VERT_SHADER_SOURCE = "void main()\r\n{\r\n\tgl_Position = gl_ModelViewProjectionMatrix * gl_Vertex * 3.0;\r\n}\0";
```

My question though is how big is this buffer.  When I send this text to OpenGL for shader compilation I need to tell it how big the source is.  Does '\r' and '\n' count as one or two char.  I know at some point they turn into a single char code, but when?

Thanks!

\r\n (or CRLF) are always 2 separate chars. However in Unix systems \n is enough to mark a new line, in Windows both \r\n are needed. Editors in Linux usually handle line end characters depending on what style of text files you save.

In your case however you should use \r\n will never be fixed because you don't edit the source in text editor but hard code the source in a char* (and escape \r\n).

However to count the size of char* you should just use strlen from string.h which counts the number of chars till it hits a \0 character.

---

### Post by ChurroLoco on 2010-09-16
Thanks for your help.

---

