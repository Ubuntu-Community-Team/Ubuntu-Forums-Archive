---
title: "Suggestions on language and 3D graphics library for engineering simulation"
date: 2012-11-02
forum: Programming Talk
---

### Post by x824 on 2012-11-02
Hi everyone.

**The problem**
I have recently started a two month long project (very short!) where the aim is to simulate the displacement of a 3D body subjected to some external forces (structural mechanics type of problem). The body's geometry will be in some kind of structured sense i.e. a .msh or .obj file. What I will need to do is

1) graphically visualize (in 3D) the body by importing geometrical data (points) from an external file
2) animate the body subjected to some forces

There will be a mass-spring model to "connect" the body and provide some realistic motion.
The languages I have in mind is C/C++, JAVA or MATLAB (I have experience with all).

**Questions**
1) With the time limit (2 months) in mind, what language do you feel would suit this problem?
2) I have though about JAVA and maybe writing a simple wrapper for e.g. JOGL, for anyone with experience with JOGL would this be realistic?

I am not looking for a definite answer, any discussion, comment, question is equally welcome!

Thank in advance!

---

### Post by PaulM1985 on 2012-11-02
Given the very tight timescale that you have I think that it would probably be best to do this in Matlab.

You have all the necessary matrix multiplication and maths functions already built in and you are able to use the mesh rendering that is already provided.

If you haven't used OpenGL before you could end up wasting time trying to get rendering working rather than actually completing the task.

Paul

---

### Post by SuperCamel on 2012-11-02
The Irrlicht engine could take care of rendering, importing of 3d models and animation. All potentially big time savings. 

[http://irrlicht.sourceforge.net/](http://irrlicht.sourceforge.net/)

---

### Post by x824 on 2012-11-03
> **PaulM1985 said:**
> Given the very tight timescale that you have I think that it would probably be best to do this in Matlab.

You have all the necessary matrix multiplication and maths functions already built in and you are able to use the mesh rendering that is already provided.

If you haven't used OpenGL before you could end up wasting time trying to get rendering working rather than actually completing the task.

Paul

The timescale is absolutely the largest constraint. My worries with MATLAB is the lack of 3D plotting alternatives and the geometrical data might be quite large which may result in performance issues. There might also be a need to make the simulation act in realtime with some interactive features (like parameteric change). The complete simulation specifications (along with data) will hopefully arrive next week.

I have thought about using MATLAB for visualization and use MATLAB MEX-files (C written) for the demanding calculations, do you (or anyone else) have any experience with this?

Thank you for your reply.

---

### Post by x824 on 2012-11-03
> **SuperCamel said:**
> The Irrlicht engine could take care of rendering, importing of 3d models and animation. All potentially big time savings. 

[http://irrlicht.sourceforge.net/](http://irrlicht.sourceforge.net/)

Thank you, I will definitely look into it.

**Another question for anyone to answer is**

Do you have any experience with SOFA? A C++ written framework for simulations. I have looked into it and some features are great, but the framework in itself is unstable and segmentation faults are not uncommon.

---

### Post by juancarlospaco on 2012-11-03
Blender BGE

blender.org

---

