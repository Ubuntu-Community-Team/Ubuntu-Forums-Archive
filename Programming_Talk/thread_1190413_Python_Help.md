---
title: "Python Help"
date: 2009-06-17
forum: Programming Talk
---

### Post by rustysynate on 2009-06-17
Hi,

I am new to programming with python. I want to make a image rotate dynamically corresponding to the CPU usage. I searched everywhere but couldnot find any post for it.All i have found is a static rotation with the PIL. If anyone could help me in this it would be of great help to me. I have a great passion to python and want to learn a lot about it. So please give me some links on the topic "How to continuously rotate images with python in a dynamic fashion?"

---

### Post by monraaf on 2009-06-17
Take a look at goocanvas.

---

### Post by rustysynate on 2009-06-18
Thanks for your reply. But what i actually want to know is that can it be done with python.

---

### Post by Bodsda on 2009-06-18
> **rustysynate said:**
> Thanks for your reply. But what i actually want to know is that can it be done with python.

Maybe pygame can help,

@monraaf: nice vivi avatar :)

Regards,

Bodsda

---

### Post by Can+~ on 2009-06-18
A 2d/3d library may help you, pygame as mentioned above, or pygl.

---

### Post by monraaf on 2009-06-18
> **rustysynate said:**
> Thanks for your reply. But what i actually want to know is that can it be done with python.

Sure it can be done with python. Just import goocanvas, create a canvas, add the canvas to your window, add an image to the canvas and call the animate method of the image. It's that simple.

---

