---
title: "Why blender slows down when increasing subdivision level in ubuntu?"
date: 2012-08-16
forum: New to Ubuntu
---

### Post by anandharaja on 2012-08-16
hi
i  installed ubuntu 12.04, using blender whenever i increase the subdivision level or more objects have subdivision level means in 3d view port selecting different object will take some time. how can i solve this problem.

Processor: Intel i5 2500
Mother Board: Intel DH67BL
RAM: 8GB

---

### Post by cariboo on 2012-08-17
You failed to mention what graphics adapter your system uses. IF you are using the builtin adapter, is it possible to increase the amount of shared ram in the bios?

---

### Post by anandharaja on 2012-08-19
i don't have GPU. But in windows 7 no problem working well.

---

### Post by Paqman on 2012-08-19
For a 3D graphics application like blender you're going to need a GPU. The Core iX chips do have a reasonable on-board graphics capability, but it's not really designed to do serious 3D work. Increasing any settings in an app like Blender will degrade performance.

A dedicated GPU doesn't need to be expensive, even a budget one should improve your situation somewhat.

---

