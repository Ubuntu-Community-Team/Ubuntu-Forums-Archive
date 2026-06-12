---
title: "CUDA: questions about 3D textures"
date: 2011-03-24
forum: Programming Talk
---

### Post by jeannotlapin on 2011-03-24
Hello, 
I'm new to CUDA, and i'm currently (i try at least :p) developing 3D filers for image analysis, using 3D textures CUDA. 

Is there a specific function to go through the neighboring texels around a position a tex3D? 
more precisely, what is the fastest way to go through the _volume_ and the _surface_ of a 3D sphere around a texels using tex3D, taking in account the calibration (the z size > xy size)

Another question, I'm not used to these synchronization stuff: is it possible to have an array modified by different threads at the same time? (like incrementing...) how could i do that?

Thanks
jeannot

---

