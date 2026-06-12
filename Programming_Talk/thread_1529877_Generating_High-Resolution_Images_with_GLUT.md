---
title: "Generating High-Resolution Images with GLUT"
date: 2010-07-12
forum: Programming Talk
---

### Post by KoRnholio on 2010-07-12
So, I'm trying to create some algorithmic art for myself, and get it printed on a huge canvas. While I'm sure discussing the algorithm itself might be more interesting to most people, I have a question about saving it to an image.

Right now I'm using GLUT, and I want to save a high resolution image. This is not hard, as there's a function that will save the screen to an image for you. The problem is, it doesn't work for resolutions higher than your screen. This is a problem, because the resolution needed to print clearly on a large canvas (I'm talking 5 feet by 2 feet) is much larger than my screen or even any mass-produced computer screen. Like, 5000-6000 pixels across, at least.

Does anybody know a way around this? In theory I could just generate the pixels using regular C++, save the bitmap directly, and not bother with GLUT, but the immediate visualization without saving a file is quite handy when working on this.

---

