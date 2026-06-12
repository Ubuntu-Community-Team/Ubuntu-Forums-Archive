---
title: "difference between *.a and *.so libs"
date: 2012-07-18
forum: Programming Talk
---

### Post by MikeCyber on 2012-07-18
Hi
what's the difference between *.so and *.a libs? 
Thanks

---

### Post by Bachstelze on 2012-07-18
Very roughly :

*.a libs are called *static*, which means that when you compile a program that uses the library, the library is built into the program. This has the advantage that you do not need to distribute the library along with the program, but the downside is that if you want to use a newer version of the library (e.g. for a bug fix), you need to recompile the entire program. It also makes your program larger.

*.so libraries are called *shared* (so stands for **s**hared **o**bject), and they are basically the opposite of static libraries. When you compile a program against a shared library, the library is accessed at run-time, meaning that the library file must be present on the system when you run the program.

---

### Post by Bachstelze on 2012-07-18
By the way, if you are wondering what the .a stands for, it's for **a**rchive, because a static library is basically an archive of code that you can use in your program (it is created with the [font=monospace]ar[/font] tool).

---

### Post by MikeCyber on 2012-07-19
Thanks. For ex.:
--------
michael@michael-ubuntu:/usr/local/lib$ find . -name "*Bullet*"
./libOgreBulletDyn.a
./libOgreBulletDyn.so.0.0.0
./libOgreBulletDyn.la
./libBulletDynamics.a
./libOgreBulletCol.a
./libBulletSoftBody.so.0
./pkgconfig/OgreBullet.pc
./libOgreBulletCol.so.0.0.0
./libBulletWorldImporter.a
./libBulletDynamics.so.0
./libBulletDynamics.la
./libBulletCollision.la
./libBulletDynamics.so.0.0.0
./libBulletSoftBody.la
./libBulletCollision.so
./libOgreBulletDyn.so.0
./libOgreBulletCol.la
./libBulletSoftBody.so.0.0.0
./libOgreBulletCol.so.0
./libBulletMultiThreaded.a
./libBulletCollision.so.0
./libBulletCollision.a
./libBulletCollision.so.0.0.0
./libBulletSoftBody.a
./libOgreBulletDyn.so
./libBulletSoftBody.so
./libOgreBulletCol.so
./libBulletSoftBodySolvers_OpenCL_Mini.a
./libBulletDynamics.so
./libBulletFileLoader.a
michael@michael-ubuntu:/usr/local/lib$ 

shows even *.la. What are those? Now how to link to a static or what's the difference to link to a shared lib? I've only linked to a shared lib so far, but would link now, as they're there, to static libs.
Many thanks

---

### Post by Barrucadu on 2012-07-19
Unless you have some specific need to (precise version requirements, needing to patch the library, etc), generally you don't link against static libraries as it just increases the size of your binary.

---

