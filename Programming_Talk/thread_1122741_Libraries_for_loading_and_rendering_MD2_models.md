---
title: "Libraries for loading and rendering MD2 models"
date: 2009-04-11
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-04-11
Yeah, I want to use the old MD2 models for a 2D platformer game.

Any libraries which can load the models and render in OpenGL?

And maybe some linux native tools for creating the models?

---

### Post by hessiess on 2009-04-11
The Irrlicht engine can read MD2, maby you can extract the relevent code from that. For creating the models, try Blender.

Why exactilly are you using a 3D mesh format for a 2d game? 3d but movement locked to 2 dimensions? You would be better off using a waited bone format instead, unless you want the obvious vertex jumping that MD2 causes.

---

### Post by bfrosty on 2009-04-11
> **crazyfuturamanoob said:**
> Yeah, I want to use the old MD2 models for a 2D platformer game.

Any libraries which can load the models and render in OpenGL?

And maybe some linux native tools for creating the models?

I'm not sure about libraries. You might find that you have to parse it yourself- I ended up having to do this for 3DS. The MD2 format should have plenty of documentation available or open source engines that use this format so it shouldn't be too difficult. 

As hessiess pointed out, MD2 is a 3D file format- It wouldn't really work in a 2D game unless you translated it. If you are new to game development, [http://www.gamedev.net/](http://www.gamedev.net/) has some very good resources that might give you a better solution.

---

### Post by crazyfuturamanoob on 2009-04-11
I know MD2 is 3D model, I know it is frame-based, I know frame-based animation takes a lot disk space and isn't perfectly accurate, but I absolutely want to have it.

---

