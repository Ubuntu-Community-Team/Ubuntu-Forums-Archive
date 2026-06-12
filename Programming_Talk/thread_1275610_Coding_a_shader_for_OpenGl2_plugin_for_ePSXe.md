---
title: "Coding a shader for OpenGl2 plugin for ePSXe"
date: 2009-09-26
forum: Programming Talk
---

### Post by MechWarrior001 on 2009-09-26
Hey, whats up? I've recently been learning C by way of taking a tutorial (C made Easy - Cprogramming.com) and writing down in my own words, so far, I've reached If statements.

Anyways, I was wondering if someone could help me with this. There's a graphical plugin Called "Pete's OpenGL2 Plugin" for the ePSXe Playstation emulator. The plugin supports using external shaders to create various effects (Storybook shaders, color-enhancement shaders, bump-mapping shaders, etc.), and I was wondering if it would be possible to create a shader that allows me to display a 320*240-640*480 sized box that is capable of displaying a txt or a rtf file inside of it, allowing to essentially use guides/faq/walkthroughs without exiting or minimizing the game. And if its possible, how would I bind the scroll function to the Page Up/Page Down keys, and/or bind it to scroll lock or F12 to summon/dismiss it.

---

### Post by Ferrat on 2009-09-26
Shaders don't work that way, shaders are like a filter that can do some amazing stuff but it's still just a filter. 
In a simple term they are like glasses for your 3D, they can be sunglasses and change the way you see light, they can be like normal glasses and give you a sharper / fuzzier image and so on but the can't really create anything of their own.

---

### Post by MechWarrior001 on 2009-09-26
Dang, alright, thanks anyways. But would a "Bloom" shader be possible?

---

### Post by tom66 on 2009-09-26
What you want is a texture of some kind, which maps to a surface which might be drawn by a simple HTML viewer. Or you might write a simple HTML viewer for your own uses.

---

### Post by MechWarrior001 on 2009-09-26
Alright, how much knowledge of C am I going to need to code that? So far, I'm at **If Statements**.

---

### Post by aiwarrior on 2009-09-26
I am guessing you will need know more than just the basics. You will probably need an advanced knowledge in both mathematics and computer science in general. That is my humble opinion (I do not consider i master any of the mentioned).

---

