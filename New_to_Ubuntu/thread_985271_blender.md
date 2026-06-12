---
title: "blender"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by djallalnamri on 2008-11-17
*hello all
*recently i have been having a screen resolution problem that i have finally solve today but in the meantime i have downloaded blender 2.48a dbpkg from getdeb.net that would not install because of dependancies not being satisfied;i have tried to install an older version that probably comes with canonical cd:this one also would not install now...;any help as i am totally new to linux...on the whole!!!
*thank in advance

---

### Post by markjensen on 2008-11-17
It sounds like you are fighting your package manager, and doing things the "*Windows Way*".   Don't worry, I did that too, when I first started using Red Hat Linux (and got introduced to RPM hell, that is really just self-inflicted).

You should always try to use the packages in your repositories (online software warehouses) first.   You can fire up "synaptic" which is a nice GUI front-end to apt, and allows you to search for apps and install them after reading a brief description.   Search for "blender" there, and click it to select and install it.

Or, from a terminal, the command would be:
**sudo apt-get install blender**

Let me know how either of those go for you.

---

### Post by djallalnamri on 2008-11-18
*hello and thanks for reply
*i had trouble with blender simpy because i did not activate nvidia driver:i knew it from error messages related to opengl;now it works but stil it is an old version (2.45) and now blender is 2.48a and this is a bit restrictive
*i wonder if downloading and installing dbpkgs from getdeb.net won't cause problem....
*anyway,thanks again

---

