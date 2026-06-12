---
title: "syntax error near unexpected 'newline'"
date: 2015-03-11
forum: New to Ubuntu
---

### Post by Achyuth_Koneti on 2015-03-11
hi all,
im completely new to ubuntu nd openGL
i need to do a graphic based game as my project..
so my professor suggested to use glfw...

when i type
cd <glfw-root-dir>

i'm getting error 
bash:syntax error near unexpected token 'newline'

---

### Post by steeldriver on 2015-03-11
Hello and welcome to the forums

It's a little hard to understand what you're trying to do - can you give us some context? 

It sounds like you're **literally** typing

```

cd <glfw-root-dir>

```

whereas the <glfw-root-dir> is probably meant as a **placeholder** for an actual directory such as /usr/local/glfw

```

cd /usr/local/glfw

```

[You will need to replace /usr/local/glfw with the **actual directory** that your professor is referring to - it's hard to guess what that might be without more information]

---

