---
title: "WINE like program for source code?"
date: 2007-12-31
forum: Programming Talk
---

### Post by lingnoi on 2007-12-31
Converting your windows programs to work on other platforms such as Linux takes quite a bit of effort by developers if they have used the windows APIs.

There are programs such as wine that translate the windows APIs at run time, but I was wondering why there aren't any programs that translate the windows APIs in the program's source code so that a developer can just parse their windows program's source code and it is converted into an SDL / openGL combo?

Surely this would be a better solution to get third party developers, such as game companies to supply a Linux / Mac binary?

---

### Post by revanthedarth on 2007-12-31
If there was a way, every game would have a linux-port :)

It isn't that simple. For example, glEnable(GL_LIGHTING) is the same as (ID3DDEV) Device->SetRenderState(D3DRS_LIGHTING, true), but it's not the way to do for every code.

I don't think there is a way. There cannot be. It's like converting from C to another language. They (OpenGL and DirectX, or any two APIs) have something in common, yes. But they are different.

But thinking that, i wish there was a way.

---

### Post by pogenwurst on 2007-12-31
The closest thing to that out there is [Winelib]("http://www.winehq.org/site/winelib"). It allows you to build against Wine's implementation of the Win32 API.

---

### Post by Auria on 2007-12-31
> **lingnoi said:**
> Converting your windows programs to work on other platforms such as Linux takes quite a bit of effort by developers if they have used the windows APIs.

There are programs such as wine that translate the windows APIs at run time, but I was wondering why there aren't any programs that translate the windows APIs in the program's source code so that a developer can just parse their windows program's source code and it is converted into an SDL / openGL combo?

Surely this would be a better solution to get third party developers, such as game companies to supply a Linux / Mac binary?

If you manage to do that properly you will become rich :lolflag:

no seriously, automatising port from an APi to another is nearly impossible unless they were designed to be compatible from the ground up (and if they were then you don't have a protability problem, right?)

---

